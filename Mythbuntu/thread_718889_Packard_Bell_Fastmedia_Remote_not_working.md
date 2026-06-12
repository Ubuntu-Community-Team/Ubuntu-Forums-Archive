---
title: "Packard Bell Fastmedia Remote not working"
date: 2008-03-08
forum: Mythbuntu
---

### Post by rgb1701 on 2008-03-08
I did a fresh install of Mythbuntu 7.10 on good hardware.

I need to use a Packard Bell Fastmedia remote, which uses a simple COM port serial IR receiver.  This remote is well known for ages among Myth and LIRC users.

I verified my COM1 port is active in the PC BIOS, set to 3F8/IRQ4.

I booted with the serial port receiver connected.

There are good batteries in the remote, and I verified the remote is sending out IR signals, based on an X10 IR repeater indicator.

I chose "Packard Bell receiver" as the remote during the Mythbuntu setup, and also verified the setting in the Mythbuntu Control Center.

I've rebooted several times, and nothing responds to the remote in the Myth GUI frontend.

How can I verify the remote is working?  How do I configure and activate the Packard Bell Fastmedia remote?  There doesn't appear to be anything obvious to try, but I could be missing something.

Thanks.

---

### Post by sjrice on 2008-05-30
You need to disable the kernel serial support. 

See the writeup at [URL="https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29"]https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29
[/URL]
It's under Serial IR Transmitter section (also applied to a serial receiver).

---

