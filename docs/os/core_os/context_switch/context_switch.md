# Scheduler/Context Switching


Scheduler's job is to maintain the list of tasks and decide which one should be running next.

## Description

Task states can be *running*, *ready to run* or *sleeping*.

When task is *running*, CPU is executing in that task's context. The program counter (PC) is pointing to instructions task wants to execute and stack pointer (SP) is pointing to task's stack.

Task which is *ready to run* wants to get on the CPU to do its work.

Task which is *sleeping* has no more work to do. It's waiting for someone else to wake it up.

Scheduler algorithm is simple: from among the tasks which are ready to run, pick the the one with highest priority (lowest numeric value in task's t_prio field), and make its state *running*.

Tasks which are either *running* or *ready to run* are kept in linked list `g_os_run_list`. This list is ordered by priority.

Tasks which are *sleeping* are kept in linked list `g_os_sleep_list`.

Scheduler has a CPU architecture specific component; this code is responsible for swapping in the task which should be *running*. This process is called context switch. During context switching the state of the CPU (e.g. registers) for the currently *running* task is stored and the new task is swapped in.


## List of Functions


The functions available in context_switch are:

* [os_sched](os_sched.md)
* [os_arch_ctx_sw](os_arch_ctx_sw.md)
* [os_sched_ctx_sw_hook](os_sched_ctx_sw_hook.md)
* [os_sched_get_current_task](os_sched_get_current_task.md)
* [os_sched_insert](os_sched_insert.md)
* [os_sched_next_task](os_sched_next_task.md)
* [os_sched_os_timer_exp](os_sched_os_timer_exp.md)
* [os_sched_resort](os_sched_resort.md)
* [os_sched_set_current_task](os_sched_set_current_task.md)
* [os_sched_sleep](os_sched_sleep.md)
* [os_sched_wakeup](os_sched_wakeup.md)
