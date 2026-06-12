---
title: "Shutdown problem"
date: 2012-06-09
forum: Mythbuntu
---

### Post by Leechpool on 2012-06-09
Hi,
I'm using Mythbuntu 12.04 (although I had the same issue with 11.10 which is why I did a fresh install of 12.04 with db export/import). I have set it up with mythwelcome to shutdown when idle and start up for recordings according to:

[http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup")


For the most part it all works well. However, occassionally the system hangs when shutting down. The purple mythbuntu and animated red dots are displayed indefinitely. I've tried just leaving it but it doesn't shutdown.
The shutdown command used is sudo shutdown -Ph now.
As I said auto shutdown/wakeup works fine apart from about once a week it hangs during shutdown. When its hung I can ctrl alt F1 and terminal displays but when I type nothing appears.... alt F7 takes me back to splash screen.
I've only just discovered that if I press esc the splash screen swaps to the console where the last line displays "checking for running unattended upgrades" with a cursor flashing on the (blank) next line.
The system is set to check daily for updates and display them immediately (not install them automatically).
I've tried googling and with my limited knowledge have not been able to find a solution.  Many references to similar issues don't seem to fit but this one interested me because it refers to similar symptoms including terminals being unresponsive:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=637995]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=637995")

Anyway I did wonder if a workaround could be as simple as uninstalling the unattended-upgrade package?

edit: I've just realised the package autofs5 referred to in the bug report is not even installed on my machine but it does sound like similar symptoms....

Any help would be greatly appreciated.

---

### Post by Leechpool on 2012-07-02
Hi all,
Ok I think its been long enough to say I've found the problem:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/824369](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/824369)

I don't fully understand this but its something to do with lirc in kernel support, so it might only affect people with an Imon LCD module "15c2:0038 SoundGraph Inc. GD01 MX VFD Display/IR Receiver".  I modified the init script with a # to disable lirc in kernel support when the service is stopped as per the posts in hte bug report and I haven't had a problem since........

Thanks

---

