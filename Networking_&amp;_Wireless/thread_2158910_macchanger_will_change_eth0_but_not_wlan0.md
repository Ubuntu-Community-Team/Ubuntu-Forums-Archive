---
title: "macchanger will change eth0 but not wlan0"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by buntubox on 2013-07-01
I installed macchanger and am able to change eth0 but not wlan0

when I change eth0 I type
ifconfig eth0 down
macchanger -r eth0
ifconfig eth0 up

Everything works.  When I do exactly the same thing with wlan0 I get a message saying

ifconfig wlan0 down
macchanger -r wlan0
ERROR: Can't change MAC: interface up or not permission: Invalid argument


Am I doing something incorrectly?

---

### Post by dargaud on 2013-07-02
No need for machchanger. Try:
> sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 01:23:45:67:89:01
sudo ifconfig wlan0 up

---

### Post by dvdhudson33 on 2013-09-04
Thanks Dargaud.   Buntubox didn't come back to say if it worked, but I've had exactly the same problem, and this was the result:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]thisPC:~$ sudo ifconfig wlan0 down
thisPC:~$ sudo ifconfig wlan0 hw ether 01:23:45:67:89:01
SIOCSIFHWADDR: Invalid argument
[/TD]
[/TR]
[/TABLE]

My PC has one wired and two wireless Ethernet adapters.  I can change the mac-address for the wired, but for *neither* of the wireless, whether using the above method or Macchanger.  It seems to be a wider problem, as it's also appeared in other threads such as* ubuntuforums.org/showthread.php?t=2145828*.

---

### Post by dvdhudson33 on 2013-09-04
[bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1220973]("http://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1220973")

---

