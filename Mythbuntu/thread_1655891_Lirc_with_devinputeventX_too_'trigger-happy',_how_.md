---
title: "Lirc with dev/input/eventX too 'trigger-happy', how can I reduce this?"
date: 2010-12-30
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-12-30
Hi guys, i have a problem with lirc in Mythbuntu 10.10 x64 with Mythtv 0.24 selected via the autobuilds: i've finally managed to get it configured correctly via /dev/input/eventX, but its too 'trigger-happy'. in irw and everything else that uses the remote, at the very least if i press the button once, it comes through as two key-presses, and if i press it for longer, it registers more. is there anyway I can inhibit/reduce this?

---

### Post by thatguruguy on 2010-12-30
> **bergqvistjl said:**
> Hi guys, i have a problem with lirc in Mythbuntu 10.10 x64 with Mythtv 0.24 selected via the autobuilds: i've finally managed to get it configured correctly via /dev/input/eventX, but its too 'trigger-happy'. in irw and everything else that uses the remote, at the very least if i press the button once, it comes through as two key-presses, and if i press it for longer, it registers more. is there anyway I can inhibit/reduce this?

You may want to read [this]("http://www.lirc.org/html/configure.html"). In particular, you may want to read about setting up an appropriate .lircrc, including appropriate values for delay and repeat.

---

### Post by Jay2k1 on 2011-02-12
I have the same problem. Then I stopped lirc (/etc/init.d/lirc stop) and this behaviour was gone - a single button press triggered only a single action. But how can the remote work if lirc is not running? I guess there's some kind of daemon that is responsible for the remote to work, and if I additionally start lirc, there are two daemons sending my button presses, so every press is recognized twice.
On mythbuntu 0.23 32-bit it worked fine, now I made a fresh 0.24 install, restored the DB and tried to get my remote work as supposed.

---

### Post by Superdude_123 on 2011-12-29
Try this:

sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

Read [http://ubuntuforums.org/showthread.php?p=11525835](http://ubuntuforums.org/showthread.php?p=11525835) (bottom)

Solved my problem.

---

