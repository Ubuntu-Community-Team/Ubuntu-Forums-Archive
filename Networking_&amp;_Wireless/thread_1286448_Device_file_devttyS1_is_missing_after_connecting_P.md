---
title: "Device file /dev/ttyS1 is missing after connecting PCMCIA card"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by chris14679 on 2009-10-09
Up until last week this was working perfectly, now I'm suddenly unable to use my PCMCIA 3G modem.

On plugging in the modem, everything looks fine in /var/log/messages:

```

Oct  9 17:32:19 chris-laptop kernel: [ 1255.238104] pccard: card ejected from slot 0
Oct  9 17:32:27 chris-laptop kernel: [ 1255.554648] pccard: PCMCIA card inserted into slot 0
Oct  9 17:32:27 chris-laptop kernel: [ 1255.554942] pcmcia: registering new device pcmcia0.0
Oct  9 17:32:27 chris-laptop kernel: [ 1255.598870] 0.0: ttyS1 at I/O 0x3f8 (irq = 3) is a 16550A

```

However I'm unable to use the device. I have found that /dev/ttyS1 doesn't exist despite being reported above, maybe that is the problem?

```

chris@chris-laptop:/$ ls -la /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2009-10-09 16:12 /dev/ttyS0
crw-rw---- 1 root dialout 4, 66 2009-10-10 04:46 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-10-10 04:46 /dev/ttyS3

```

I normally connect to the modem using /dev/umts. This device does exist but doesn't seem to do anything.

connecting using 'pon ac850' now either locks up completely or gives 'Connect script failed' without successfully talking to the modem at all (not even 'AT').

Try to connect using GPRSEC gives the error 'Port not found' on both /dev/umts and /dev/ttyS1.

The modem is fine and the lights indicate it has a GPRS connection. I'm sure the problem is something to do with initialising the serial device for it.

All this was working last week and I did not make any changes so I assume this problem must be related to a recent (automatic) ubuntu update. I'm running Hardy 8.04.

Very occasionally it works OK after a reboot, about 1 boot in 20 it just works, I'm not doing anything different on those boots! Otherwise no matter how many times I try pon it doesn't work, and sometimes also leaves a lock file for the umts device hanging about which I have to delete manually. It either works fine every time after a reboot, until the next reboot, or it doesn;t work at all.

I've wasted a whole day trying to fix this, please please can anyone help urgently as I can't work without 3G internet access!

---

### Post by chris14679 on 2009-10-09
A bit more investigation shows that /dev/tts/umts is being created by a udev rules file which is then redirected to /dev/umts. This seems to all happen OK when the modem is plugged in, still can't talk to it though!

I found the following stuff in syslog - note the two lines with NetworkManager doing something. Maybe whatever NetworkManager is doing is causing a conflict or locking up the device? Is this likely to be the problem and, if so, how can I stop NetworkManager playing with the modem without also losing NetworkManager for my WLAN and LAN connections when I need them?

```

Oct  9 18:25:43 chris-laptop kernel: [ 1946.278719] pccard: PCMCIA card inserted into slot 0
Oct  9 18:25:43 chris-laptop kernel: [ 1946.279015] pcmcia: registering new device pcmcia0.0
Oct  9 18:25:43 chris-laptop kernel: [ 1946.323104] 0.0: ttyS1 at I/O 0x3f8 (irq = 3) is a 16550A
Oct  9 18:25:43 chris-laptop NetworkManager: <debug> [1255065943.665136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_2'). 
Oct  9 18:25:43 chris-laptop NetworkManager: <debug> [1255065943.672701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_2_serial_platform_1'). 

```

---

### Post by chris14679 on 2009-10-09
I wish I could change the title of this thread - the missing ttyS1 device was a red herring. If I disable the rules file then the connection comes up as ttyS1, otherwise as umts.

I tried using minicom connecting direct to /dev/umts (and to ttyS0 with the rules file disabled). No response to AT commands. Nothing even echoed back. Dead.

I also tried removing Network Manager using Synaptic and then installed Wicd instead. Wicd seems much better, but unfortunately didn't fix this problem.

I'm really stuck here, anyone have any suggestions how to wake up the serial connection to the PCMCIA 3G modem (sierra aircard 850). Everything was working fine until a few days ago!

---

### Post by chris14679 on 2009-10-10
bump

---

### Post by chris14679 on 2009-10-11
bump^2

---

### Post by achim_59 on 2009-11-23
I had a lot of problems with this card on an HP nx6325. I tried to get some help from this forumm but from 844 views got precisely one response.

What I can tell you is that your settings *appear* to be correct. After you try pon, what comes up if you give the **demsg** command? What about **tail -50 /var/log/syslog**?

That's where I find the most useful information... immediately after a failure there is usually something useful in those places.

I will try to get back to you, but I confess I actually gave up until recently. It's only in the last week that tried to get the thing working under Linux again. This time on an IBM T43. I've got completely different problems now. Well, I guess that's progress.

Good luck and please post anything that you find out. If I discover more, I will let you know.

Achim

---

