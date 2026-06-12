---
title: "Modprobe killed on a cold boot"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by kammce on 2009-11-26
[FONT=Courier New][SIZE=2]My problem is that on a **cold boot** (booting up my computer after a long time of not being on), I run a shell script that I created that runs `modprobe` and inserts `ndiswrapper` into the kernel which turns on my wifi card. Most of the time, on a cold boot, I get the 'killed' output message.  I understand that, that means that `modprobe` was killed the instant I tried to run it. Then when I attempt to run it again it stalls out and I get no output. Why is that? 

I have previously removed the ndiswrapper module from the boot log, because it stalled out my computers boot every other time I booted up my computer. KDE would exit out of it's loading screen to show me the process working and I would see "Configuring Network Interfaces." I would have to kill that process in order to boot up all the way. 

In order for me to run `modprobe` I am required to restart my computer then hope that my computer is warm enough to run `modprobe` without issue. Almost every time I restart my computer, after a failed first attempt, this works.

I am just wondering what I should do after I get the "killed" message after I run `modprobe` the first time. I would also like to know if I should fix my shell script so that it removes then inserts `ndiswrapper`, and if `insmod` and `rmmod` are better ways to insert and remove kernel modules.

And another thing... if ndiswrapper is already loaded into the kernel, why is my wifi card not turned on?
[B]
Computer Info:[/B]
agriculture  : x86_64
kernel       : 2.6.24-25-server
Ubuntu ver.  : Hardy[/SIZE][/FONT]

---

### Post by kammce on 2010-02-04
still need help with this

---

