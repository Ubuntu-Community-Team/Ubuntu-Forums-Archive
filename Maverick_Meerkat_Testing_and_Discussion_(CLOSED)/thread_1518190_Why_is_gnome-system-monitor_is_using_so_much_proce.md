---
title: "Why is gnome-system-monitor is using so much processor power?"
date: 2010-06-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-26
I have two gnome-system-monitor on the bottom panel one for memory one for processor and there usually 
show normal results but when i open gnome-system-monitor the processor spikes to 51% and when i close it 
the processor goes to +-0% so something is wrong here now i tried to open gnome-system-monitor via terminal 
and got this:

** (gnome-system-monitor:1710): WARNING **: SELinux was found but is not enabled.

Could it be the cause of the problem?

Thanks in advance.

---

### Post by gnomeuser on 2010-06-26
A good guess would be the rendering of the graphs is taking a lot of power, but you are right it does tend to use a bit more than it's fair share.

I think it is worthy of a bug report.

---

### Post by Reiger on 2010-06-26
Another thing to note is that this kind of app will always use a fair amount of CPU (disproportionate to what you would expect) because it polls the system (sensors) which is by definition a wasteful activity.

You might be able to alleviate this CPU usage problem somewhat by adjusting the time interval at which it updates the sensor data (polls the system).

---

### Post by ronacc on 2010-06-26
if you simply want to monitor your CPU and RAM use the pannel system monitor or screenlets or conky not gnome-system-monitor which is much more than a simple monitor .

---

### Post by philinux on 2010-06-26
With 3 second interval.

---

### Post by aviramof on 2010-06-26
By default it's one second interval so perhaps a bug report is in order anyone care to do that?it would probably better then what i would do.
And what you see in the picture is still good it can go higher.

---

### Post by philinux on 2010-06-26
> **aviramof said:**
> By default it's one second interval so perhaps a bug report is in order anyone care to do that?it would probably better then what i would do.
And what you see in the picture is still good it can go higher.

It doesn't cause me a problem on a 1 second interval. Top seems to report it slightly different due to the time delay
I use the system monitor applet most of the time and top.

---

### Post by donniezazen on 2010-06-26
> **aviramof said:**
> I have two gnome-system-monitor on the bottom panel one for memory one for processor and there usually 
show normal results but when i open gnome-system-monitor the processor spikes to 51% and when i close it 
the processor goes to +-0% so something is wrong here now i tried to open gnome-system-monitor via terminal 
and got this:

** (gnome-system-monitor:1710): WARNING **: SELinux was found but is not enabled.

Could it be the cause of the problem?

Thanks in advance.

I too have exactly same problem.

---

### Post by philinux on 2010-06-27
> **soham_1207 said:**
> I too have exactly same problem.

It's not a maverick problem plus the software works and it is only a warning. It means package selinux is not installed. It is not installed by default in ubuntu.

[http://ubuntuforums.org/showthread.php?t=631569](http://ubuntuforums.org/showthread.php?t=631569)

---

### Post by aviramof on 2010-06-27
So why does the messege is "SELinux was found but is not enabled" and i found two packages libselinux1 and libsepol1 that i did not installed.

---

### Post by yelo3 on 2010-06-27
I have default options, but the cpu usage of gnome-system-monitor is always 3%.
What increases the cpu usage is to switch to the "process" tab (10%).

---

### Post by aviramof on 2010-06-27
For me it's the tab  with the graphs  that cause the problem.

---

### Post by andrewabc on 2010-06-27
This problem occurred I think for 9.04 (or 9.10) dev testing, but it eventually got fixed. I know I was affected by it.

Maybe the same problem has appeared again?

---

### Post by ranch hand on 2010-06-27
The resources tab sucks the cpu power.  Don't notice it on this box but we have an old box and the only way to use it is to set it at 5.00 (or higher) and then it isn't a problem.

That box has 8.10 on it.

---

### Post by 23meg on 2010-06-27
The current excessive CPU usage is almost certainly the remnant of an earlier bug ([bug #187383]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383") in Ubuntu, [bug #507797]("https://bugzilla.gnome.org/show_bug.cgi?id=507797") upstream), which was considered fixed due to performance impact being reduced with an update, despite not being optimal with lots of configurations.

Cairo acceleration still seems to be tricky with many drivers, and you can expect to have no issues with certain drivers, and very high impact with others.

---

### Post by VMC on 2010-06-27
> **ranch hand said:**
> The resources tab sucks the cpu power.  Don't notice it on this box but we have an old box and the only way to use it is to set it at 5.00 (or higher) and then it isn't a problem.

That box has 8.10 on it.

I never thought of looking at the preferences and changing the value. Its set at 1, and changing it to a 5 is an improvement. 

then again, I rarely use system-monitor. I normally use *top*.

---

### Post by aviramof on 2010-06-28
In any case maybe it would be a good idea to change the default from 1 second to 3 seconds that might prevent future problems,
and with all do respect to *top* and etc the gnome-system-monitor is more comfortable and more accessible to people who wants
to see what happen in there computer in a more graphics way and possibly with more details.

And by the way i really don't understand the process tab i mean why does all the process 
there including the Firefox i am currently using are in sleep status and supposedly are using
0% of the process in all this this tab does not update itself in real time or in any time unless you open a new software and that it, 
it doesn't change the amount of memory or status or anything so what is the point here?

It does not similer at all to windows task manager that is constantly changing which makes this tab very useless so someone should check this and fix it.
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/599233](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/599233)

---

### Post by philinux on 2010-06-28
> **aviramof said:**
> 
And by the way i really don't understand the process tab i mean why does all the process 
there including the Firefox i am currently using are in sleep status and supposedly are using
0% of the process in all this this tab does not update itself in real time or in any time unless you open a new software and that it, 
it doesn't change the amount of memory or status or anything so what is the point here?

It does not similer at all to windows task manager that is constantly changing which makes this tab very useless so someone should check this and fix it.
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/599233](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/599233)

Try opening and closing a firefox tab it updates system monitor.

---

### Post by aviramof on 2010-06-28
It working now but it doesn't understand why the status stays the same all the time and i'm sure the memory and cpu are not as stable as it show all the time.

---

### Post by philinux on 2010-06-28
> **aviramof said:**
> It working now but it doesn't understand why the status stays the smae all the time and i'm sure the memory and cpu are not as stable as it show all the time.

When, I occasionally do, run vista on my GF's laptop it's always doing something in the background. Disk drive getting hit all the time, it's real pain. This is when you are just looking at the screen doing nothing.

Enjoy ubuntu's calmness!!

---

### Post by andrewabc on 2010-06-30
Running June 30 dailylive on liveusb. When no programs are running or anything (idle), with system monitor open, I do not experience any high CPU usage in graphs. CPU anywheres between 0-6% (not the 20% bug that happened a year or two ago).

Hmm, on processes tab, system monitor is shown as using 6% CPU.

default update interval in seconds is 3.
Was that number changed recently? I thought others here was saying it was 1 second (which would cause more CPU).

I notice maverick is using firefox 3.6.6. Wonder when the update will be sent out to older ubuntu versions?

---

### Post by aviramof on 2010-07-01
The number was 1 in the preference of the resources tab the one with the grafhs and for me even with 3 it still take too much cpu.

---

### Post by dinamic1 on 2010-07-01
> **andrewabc said:**
> Running June 30 dailylive on liveusb. When no programs are running or anything (idle), with system monitor open, I do not experience any high CPU usage in graphs. CPU anywheres between 0-6% (not the 20% bug that happened a year or two ago).

Hmm, on processes tab, system monitor is shown as using 6% CPU.

default update interval in seconds is 3.
Was that number changed recently? I thought others here was saying it was 1 second (which would cause more CPU).

I notice maverick is using firefox 3.6.6. Wonder when the update will be sent out to older ubuntu versions?

10.04 has already firefox 3.6.6

---

### Post by andrewabc on 2010-07-01
> **dinamic1 said:**
> 10.04 has already firefox 3.6.6

When are they upgrading 9.10 to 3.6.6?

I used PPA a month ago to upgrade to 3.6.3, and stopped using the ppa because I wanted to see ubuntu normally upgrade to 3.6.6.

hmm, according to packages.ubuntu.com they havn't made the upgrade yet.

Oh well, I think I'll be formatting and upgrading to 10.10 anyways.

---

### Post by andrewabc on 2010-07-01
..

---

### Post by andrewabc on 2010-07-01
EDIT:
Forum error, feel free to delete this post and post above this.

---

