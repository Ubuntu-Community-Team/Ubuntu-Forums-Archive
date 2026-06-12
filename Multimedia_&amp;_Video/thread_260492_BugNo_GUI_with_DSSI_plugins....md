---
title: "Bug:No GUI with DSSI plugins..."
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by Patrice Brousseau on 2006-09-18
Hi there,

I just installed Ubuntu with a low latency kernel I compiled following the instructions.

So far, everything runs fine apart that I cannot see any DSSI GUI when I load  a synth. It happens in Rosegarden, Ghostess or jack-dssi-host. I verified that all the dependencies are met and it seems it is ok...

Just a weird thing, it happens also with a distro called "Musix" (on the HDD install and on the Live CD) and not only on this computer (old Celeron 533 on Abit board and SiS video card) but also on my main Windows machine (AMD 1600+ with Matrox dual-head).

More than that, I also tried a Mandriva distro and the same thing happens...

For the record, here is a cut and paste of my terminal windows when running  jack-dssi-host (no GUI after the last line):

------------------------------------------

patrice@ubuntu:~$ jack-dssi-host hexter.so

jack-dssi-host: Warning: DSSI path not set
jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/patrice/.dssi"


jack-dssi-host: OSC URL is:
osc.udp://gustave:18365/dssi/hexter/hexter/chan00

host: Ready
hexter_gtk starting (pid 19930)...

------------------------------------------

Is anyone having a clue about it...?


Thanks a lot.

---

### Post by Patrice Brousseau on 2006-09-20
Hi,

Just looking at my previous post, I observed something in the terminal commands: [B]jack-dssi-host: OSC URL is:
osc.udp://gustave:18365/dssi/hexter/hexter/chan00
[/B]

"gustave" is not the Ubuntu computer but my Windows machine on the same network...

So, is it possible that jack-dssi-host is trying to open the GUI on the networked machine, thus making the window unavailable on the Ubuntu computer? It is just  a supposition, maybe the DSSI protocol doesn't handle the GUI this way.

I looked at the file /etc/hosts and "localhost" is clearly written in the text so I do not know where DSSI goes to pick the Windows machine:confused:

If the problem is located elsewhere, is it possible that this bug could be related to GTK??

Thanks a lot again...

---

### Post by dolson on 2006-09-20
That is very weird... Unfortunately I don't know enough to help you. Maybe report a bug in Launchpad or ask on the Linux Audio Users mailing list, where a lot more people hang out and might be able to help.

---

### Post by Patrice Brousseau on 2006-09-20
Thanks Dana,

I will try a couple of things: 

1- disable the network interface to see if DSSI osc udp will be allocated on the Linux computer.

2- try the latest version of Musix (0.59) and see if the bug remains...

3- if all fails, look at the mailing list you suggested...

---

### Post by Patrice Brousseau on 2006-09-20
> **Patrice Brousseau said:**
> Thanks Dana,

I will try a couple of things:

1- disable the network interface to see if DSSI osc udp will be allocated on the Linux computer.

2- try the latest version of Musix (0.59) and see if the bug remains...

3- if all fails, look at the mailing list you suggested...

About 2: Musix latest version behaves the same...

...and 3: Linux Audio Mailing is unavailable today...

I didn't tried number one yet but will do in the next minutes...

---

### Post by Patrice Brousseau on 2006-09-20
> **Patrice Brousseau said:**
> About 2: Musix latest version behaves the same...

...and 3: Linux Audio Mailing is unavailable today...

I didn't tried number one yet but will do in the next minutes...

Yes... The network interface was the culprit.

To work with DSSI plugins, I'll have to disable the NIC each time or close the Win machine.

---

### Post by dolson on 2006-09-20
That makes no sense at all. I would ask the author of dssi about this... And maybe report a bug. Networking should in no way, shape, or form interfere with audio. This issue wins Weird Award of the Day.

---

### Post by Patrice Brousseau on 2006-09-21
> **dolson said:**
> That makes no sense at all. I would ask the author of dssi about this... And maybe report a bug. Networking should in no way, shape, or form interfere with audio. This issue wins Weird Award of the Day.

I agree that it makes no sense but maybe the cause resides elsewhere (brand of NIC, the way I'm networked with Windows, etc...). I'm certainly not the only one to have a WinXP machine and a Linux one networked. 

Is anyone else having a similar setup sharing this DSSI bug???

---

### Post by HanZo on 2006-09-21
Have the same issue here on a fresh edgy install... will try to see if disabling the nic will help in my case too.

---

