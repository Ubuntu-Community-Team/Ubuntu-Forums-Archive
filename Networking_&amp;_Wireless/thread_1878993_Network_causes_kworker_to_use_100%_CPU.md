---
title: "Network causes kworker to use 100% CPU"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by mizery on 2011-11-10
Hi everyone,

Not sure if I'm posting this in the right forum, but I'm in desperate need of help right now.

My Lenovo T61 has been running with Ubuntu 11.04 for a while, and everything has been absolutely perfect till now. 
Whenever I connect to a wireless network or plug in a network cable, a kworker thread (0:0 or 0:3) suddenly jumps up to using 100% of one core of my CPU in periodic ticks. For the short while its doing this (like half a second every 2-3 seconds), my mouse will freeze and the computer won't respond to input via the keyboard.

See the screenshot below:
[IMG]https://lh4.googleusercontent.com/-zGbiQDFSnjg/Trxaab8ihnI/AAAAAAAAAtM/n2wnHWQ8xgc/s720/cpu-network.png[/IMG]

I didn't make any changes of the network setup or configuration, however I did install the Wolfram CDF Player ([http://www.wolfram.com/cdf-player/]("http://www.wolfram.com/cdf-player/")) approximately at the same time, though I don't see how that could be related. 

Inspired by Googling and powertop, the following line of code seems to temporarily fix the issue for the wifi part, though the cabled issue remains:
```
find /sys/devices/pci* -path "*power/control" -exec bash -c "echo auto > '{}'" \;
```

I've attached ps.txt which should show all processes currently running. The problem persists when running in safe mode.

Any help would be **much** appreciated - for now, this is rendering my main work PC nearly unusable.

Thanks in advance!

---

### Post by mizery on 2011-11-10
As suggested in #ubuntu, I tried disabling ACPI. This did not fix the issue.
I disabled it using the guide found [here]("http://ubuntuforums.org/showthread.php?t=1839408").

---

### Post by DouglasAWh on 2011-11-15
you probably already saw this, but there is some discussion about kworker here: [http://ubuntuforums.org/showthread.php?t=1630347](http://ubuntuforums.org/showthread.php?t=1630347)

---

### Post by mizery on 2011-11-15
Thanks - I think I scrolled over it once or twice while trying to figure out how to fix the problem.

I haven't had the issue for a few days now, though. I tried fixing the problem by booting the 2.6.38-8 kernel instead of the 2.6.38-12 one I'm using - and the issue was not present when using that kernel version. After switching back to 2.6.38-12, however, the issue didn't return...
Was just shooting in the dark, in other posts around the forum it looked like a kernel issue - but what do I know? :P

So I'm happy I'm not seeing the issue anymore, but its probably not gonna help the ubuntu developers fix the problem.
I'll return if the problem ever comes back.

---

### Post by highfructosecorn on 2011-11-22
I wanted to add, I also experienced this behavior with 11.04. Without doing a more thorough search I upgraded to 11.10 (which uses kernel 3.0.0.13-generic) and can replicate the behavior from the first post exactly.

---

### Post by sabreur on 2012-05-25
I am having the same problem, with the same period of oscillation. (I have xubuntu 11.10 on a Lenovo X61 Tablet) This morning, I installed updates and everything seemed fine. Everything was still fine before dinner, but when I returned from dinner, the problem had begun. Additionally, both my Ethernet and power manager are no longer working. From many google searches (there appear to be related problems) I tried the following

Creating file /etc/modprobe.d/local.conf with the line "options drm_kms_helper poll=N" (no quotes). After restarting, this had no effect.

Changing file /sys/module/drm_kms_helper/parameters/poll content to "N" (no quotes). This had no effect.

Unplugging my battery charger. This worked in the beginning, but for some reason it no longer works.

Running "sudo ifconfig eth0 down" (no quotes). This stops the oscillation, but I still have no working Ethernet or power manager.

Help!

---

### Post by mizery on 2012-05-25
Although this is of course not a viable solution, I'm now running Ubuntu 10.04 where everything seems to be working fine. I wonder if 12.04 has the issue... I can't be of much help, though - hope you get it working! (and please, let us know if you do)

---

