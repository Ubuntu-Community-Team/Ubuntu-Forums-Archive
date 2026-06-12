---
title: "Wireless suddenly not working"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by whead33 on 2011-03-13
Hi

I had issues with getting my wireless to work when I first bought my msi 620, clean installed Ubuntu for the first time, and this was sorted out here: [http://ubuntuforums.org/showthread.php?t=1650507](http://ubuntuforums.org/showthread.php?t=1650507)

It's broken again and I can't figure out how to get it going, even though I followed the previous fixed thread's instructions.

Not sure if it has any relevance but I did two things differently to normal when it broke:
1) I was in a different country (just got home today)
2) I plugged in a cable to connect my laptop to my brother's TV, and since then my wireless card has been turned off and I'm unable to turn it back on.

When I run 'sudo lshw -C network' it tells me that the network is disabled, when I hit 'rfkill list' it tells me that wireless lan is hard blocked.

Ideas?

Thanks


[]("http://ubuntuforums.org/showthread.php?t=1650507")

---

### Post by dunp on 2011-03-13
Check your firewall if you have one loaded that may have turn off your wireless connection

---

### Post by wojox on 2011-03-13
What if you run:

```
sudo rfkill unblock wifi
```

```
sudo rfkill list all
```

---

### Post by Shriner on 2011-03-13
Found another thread, that reports that if you are using a kernel before  2.6.34 this problem occurs. It is reported that manually updating your  kernel to 2.6.34 will cure the drops with all wireless cards. I'm not  willing to verify this at this time because my ISP has oversold their  DSL capablities and my connection sucks at this time. I guess I'm  fortunate that I have a WET-11 to use in the interim.

Instructions for manually updating your kernel can be found @
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("http://ubuntuforums.org/view-source:https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

You can determine your current kernel with uname -a

Edit: I need to update this.....it may not solve this particualr problem or have anything to do with it. I was reading different things on my problem, which was similar. I had left this tab open and posted the info I found, but since this isn't quite the same, it may or may not help.

---

### Post by whead33 on 2011-03-13
Hi

Thanks for suggestions so far

Dunp...no firewall.

Wojox... ran those, no change, still hardblocked.

Shriner.... that looks complicated, will do that when I'm less tired so I don't balls it up.

Thanks again....

---

### Post by Shriner on 2011-03-13
Another thing I had found is that sometimes the wireless card is put into a sleep mode by the power saving feature. You can check this with "iwconfig"

If power saving is on you turn it off with "sudo iwconfig wlan0 power off" - assuming that you are using wlan0.

Maybe this will help.......

---

### Post by whead33 on 2011-03-17
No power management issues. I'm losing hair with this one...would consider ditching for apple if it wasn't so expensive...

---

### Post by whead33 on 2011-03-17
Oh, and my kernel is 2.6.35...

---

