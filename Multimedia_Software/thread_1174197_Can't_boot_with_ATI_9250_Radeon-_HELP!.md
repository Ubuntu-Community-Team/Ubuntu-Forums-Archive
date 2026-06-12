---
title: "Can't boot with ATI 9250 Radeon- HELP!"
date: 2009-05-30
forum: Multimedia Software
---

### Post by solder4Christ on 2009-05-30
Hello,
I recently came into possession of a ATI 9250 256 MB video card for my desktop.

I installed the card in my computer, and attempted to load Ubuntu (I'm running 8.04 LTS). This was several weeks ago, but if I remember correctly, it loaded alright, and worked noticeably better than my onboard graphics card that I had been using. However, it didn't work as well as I expected a 256 MB graphics card to work, so I went in search of a reason for this. I found a tutorial on how to install better drivers for the card (I'm sorry, I don't remember where the tutorial was). Anyways, I followed the instructions and typed all the commands as they said to. But, when I went to re-boot, it didn't work properly. 
I don't remember what happened, but I couldn't boot. 

Long story short, I reinstalled with Ubuntu 9.04, and that didn't fix the problem. I was having trouble with Ubuntu 9.04, so I downgraded back to 8.04 (installing from the CD both times). 

Now, onto to the point of my problem: I don't know why, but where I'm at right now, I can't properly boot if I have the ATI card enabled. However I try to boot (whether with LiveCD (either 9.04 or 8.04) or from hard disk) I get an error. Generally, the error resembles the following:
```
rc-default main process (2824) terminated with status 127
```

Then, after a few seconds, a large amount of text scrolls by very quickly, and then ends with a message stating the system is out of memory or something like that.

I don't really know what to do, so if somebody could help me, that would be greatly appreciated! 
I don't know what other information would be needed for a diagnosis, but if you ask, I can post it.

Thanks in advance for the help!

---

### Post by solder4Christ on 2009-08-23
bump

---

### Post by pedro3005 on 2009-08-23
Try following these solutions: [https://answers.launchpad.net/ubuntu/+question/77032](https://answers.launchpad.net/ubuntu/+question/77032)

---

### Post by solder4Christ on 2009-08-24
Ok... So here's where I'm at now:

Somehow, I was able to boot to an Ubuntu 9.04 LiveCD, and I reinstalled it onto the harddisk.
I rebooted, and the loading bar got about an eighth of the way to the end, and stopped, and stayed stopped.

Eventually, I shut it down, and booted into recovery mode to see what was happening under the splash screen.

instead of the rc-default error I got last time, now I'm getting

```
udevd-event[1235]: 'bin/mkdir /var/run/network' abnormal exit
```

It stopped there for about a minute, then scrolls by a bunch of text, stops for another minute or so, gives another udevd-event error, and after about 2 or 3 minutes, it came up with ```
rcS-sulogin main process (1360) terminated with status 127
```

I haven't tried booting into the LiveCD again yet... but I don't know what I would do once I get there...

Thanks Pedro3005... that looks like the exact problem I was having before... but now I have a different problem :S :P :)

---

### Post by solder4Christ on 2009-08-24
Ok... I think it's fixed!! YAY!

Ok, here's what I did for anybody that has this problem in the future:

In the link that pedro3005 gave, *Michael* suggested adding "intel_agp.blacklist=yes" to the boot options. By doing this, I was able to boot into a live CD, and reinstall my system. I still couldn't boot from there though. I booted into a live CD again, but without the "intel_agp.blacklist=yes" in the boot options I couldn't. That's when a little light turned on. 

"If I added 'intel_agp.blacklist=yes' to the harddisk boot options, maybe I can boot from the harddrive"

I tried it, and booted successfully into Ubuntu.

Compiz didn't work at first, but I used Forlong's compiz-check script to see what the problem was. For some reason, the pci ATI card was blacklisted. That was a little strange, but the script un-blacklisted it. So it's working mostly ok now. I've had a couple bugs (like, when I was typing this, the screen went black. I brought it back by switching to a tty, and then back to GNOME.)

Thanks for the help to everybody that helped! Especially to starcraftman and Buuntu on the #ubuntu-beginers-help IRC channel

---

