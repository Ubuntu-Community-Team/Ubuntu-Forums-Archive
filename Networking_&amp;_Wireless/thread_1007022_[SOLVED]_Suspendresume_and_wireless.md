---
title: "[SOLVED] Suspend/resume and wireless"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by quip on 2008-12-10
Hello all...it's been a long time since I've been here.  I think Dapper Drake was the last Ubuntu release I had tried before Intrepid Ibex.  Not that it matters...

Anyway, recently I did a fresh install of 8.10 to get the 2.6.27 kernel for my wireless card, which needs the ath9k kernel module.  Everything went well, and I _think_ suspend/resume was all good out of the box.  However, I have updated since.

What I can say is that now I have a problem with suspend/resume and wireless.  After a fresh boot, wireless comes right up.  The first time I try to suspend, everything seems to unload (/var/log/pm-suspend.log looks fine), and the screen blanks, only to come back immediately.  My wireless card also comes back, and the NetworkManager applet bring it up, and it works.

However, if I try to suspend again, things go all the way down (into a proper suspend to RAM), and they stay that way.  Upon the resume, nm-applet will "sit and spin"; it continually tries unsuccessfully to connect.  To get it to connect, I have to remove the module, kill the applet, re-insert the module, restart NetworkManager, and then restart the applet, and, it seems, I need to use a certain order.  Additionally, the applet seems to "block" most everything else--windows don't want to close, I can't sudo, and sometimes the entire thing becomes unresponsive.  This makes it not only inconvenient but also a major problem, as I am on the laptop for hours every day (CS student).

I have tried hacking around some of the pm-utils scripts to no avail.  I have tried to re-set everything back to normal, including going back from the ATI drivers (installed through restricted drivers manager) to the open source MESA drivers.  Right now what I need is some help, or at least some fresh ideas to try.  Anybody, please?

TIA,

Wayne

---

### Post by quip on 2008-12-10
Well, I am marking it as "solved", since the wireless card is no longer the main problem.  While I thought I had reverted all changed scripts that I messed with the their original states, I found that I had marked the ath9k module as one that needed to be unloaded upon suspend and reloaded upon resume.  (BTW, I thought I read in one of the files in /etc/default/acpi-support, or one of the ones in /usr/lib/pm-utils that all network interfaces were taken down and modules unloaded automatically and by default?  Don't know, can't recall.)

Anyway, I removed ath9k from the modules to unload/reload list, and now the wireless does fine.  Every so many resumes I have to unload and reload the module by hand after coming back up, but at least I can do it, and the system doesn't become unresponsive.  Also, this is pretty normal for wireless cards across the board and in other OS's, too, in my experience.

I do still have the problem where the first suspend after a reboot immediately resumes, but all the suspend/resume cycles after that are good, and that's not a wireless issue.

BTW, to all who have had a hand in the development of Ubuntu and its "siblings"--great job!

---

### Post by psycovic23 on 2008-12-17
Hey,

I'm having this problem right now, though I haven't changed anything at all. Could you give more specifics on how you fixed it? I'm using the ath_pci module.

---

### Post by quip on 2008-12-17
> **psycovic23 said:**
> Hey,

I'm having this problem right now, though I haven't changed anything at all. Could you give more specifics on how you fixed it? I'm using the ath_pci module.

Well, in case I didn't explain it well, enough, I did nothing, in effect.  I reverted all the changes I made to the defaults.  Basically, I just removed my screw-ups.

I did write a short script to reload the wireless module for times that it doesn't come back up properly.  All I did was create a launcher for the panel, and tell it to execute the script in my home directory.  The script is just a text file with the line ```
#!/bin/bash
``` at the top.  Then, underneath it, the commands:```
/sbin/rmmod ath9k
sleep 2
/sbin/modprobe ath9k
```

The sleep just pauses execution of the script to make sure that rmmod has time to finish.  Then the applet takes over and connects.  I have to launch it w/sudo, of course, and there is a program that will pop up a window and prompt you for it:  gksudo.  So, I guess the launcher actually runs```
gksudo reset_wireless_script
```

Hope that helps.  I had to do the same thing in openSUSE on my old laptop with the ath_pci module.

---

