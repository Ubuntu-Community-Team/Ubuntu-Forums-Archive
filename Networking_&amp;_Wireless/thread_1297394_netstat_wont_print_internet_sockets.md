---
title: "netstat wont print internet sockets"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by ThomasDenmark on 2009-10-21
If I do 'netstat' without any parameters I get (after waiting 5 seconds, I think this is for the host name resolution) something like:

```

foo@foo-laptop:~$ netstat | head -n15
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 foo-laptop.loca:35348 ey-in-f19.1e100.net:www ESTABLISHED
tcp        0      0 foo-laptop.loca:51375 ew-in-f113.1e100.ne:www ESTABLISHED
tcp        0      0 foo-laptop.loca:46828 134.102.60.236:47622    ESTABLISHED
tcp        0      0 foo-laptop.loca:35347 ey-in-f19.1e100.net:www ESTABLISHED
tcp        0      0 foo-laptop.loca:39010 ey-in-f17.1e100.net:www ESTABLISHED
tcp        0      0 foo-laptop.loca:35125 host111-8-dynamic:50646 ESTABLISHED
tcp        0      0 foo-laptop.loca:35125 host123-142-dynam:50189 ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    2842     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    3034     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    6272     @/org/freedesktop/hal/udev_event
unix  11     [ ]         DGRAM                    5523     /dev/log

```But if I call netstat with the -w (parameter which means only the internet sockets), it finishes instantly, and only prints:

```

foo@foo-laptop:~$ netstat -w
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
foo@foo-laptop:~$ 

```I.e. looking at the column headers Proto, Recv-Q, etc. it "wants" to print exactly what i am looking for, but it prints no lines at all. Even though the first mentioned command printed 7 lines of internet sockets.

Thomas

---

