---
title: "Nova-T 500 issues since Lucid"
date: 2010-07-21
forum: Mythbuntu
---

### Post by can2002 on 2010-07-21
[FONT="Century Gothic"][SIZE="3"]I've been running a dedicated Mythtv backend since Jaunty without major issues.  I initially had just a Nova-T 500 card, but I added a HVR-4000 back in December (after upgrading to Karmic).  

After the release of Lucid I did a fresh install and imported my recordings database from the previous install.  Things were fine to start with, but in the last month or so I've encountered an irritating problem where recordings spontaneously stop working on the Nova-T card.  I can see the recordings initiated in the backend logs and there's a corresponding record in the 'recorded' table (with a filesize of 0).

After such a failure all subsequent recordings on the Nova-T card fail in the same way and I'm also unable to watch live TV.  The first couple of times it happened I'd been doing other work on the backend server and so just rebooted the box, which fixed it.  As time has gone on I've been able to confirm that when the problem occurs, the HVR-4000 card (which I'm only using for DVB-S) works fine.  I've also confirmed that I can fix it by unloading and reloading the 'dvb_usb_dib0700' module and I've set a cron job to do this in the early hours of the morning.  This has mostly removed the problem, but I still get the odd day where the failure still occurs.

There's nothing obvious in the backend logs to indicate what's happening and I wondered if anyone could recommend any optional logging or debugging I could enable to understand the root cause.  

Cheers in advance for any help!

Cheers,
Chris
[/SIZE][/FONT]

---

### Post by AlecJ on 2010-07-22
I have had similar problems with my Nova T 500.
Stopped using it now as have gone over to 4 Satellite cards, instead.

I got very fed up with each upgrade making my tuners non functional, I have a pile of USB tuners that worked fine under 9.04, not a peep after that, even with auto builds on.
 

 The Nova T 500 is treated as a USB device and in 10.04 there is no Hal.  Not sure what took it's place but I would guess it's turning off the USB support as a sleep power function?

---

### Post by nik. on 2010-08-01
I'm having exactly the same problems, it seems to have become a problem over the last month or two, seemingly getting worse.

Any chance you could post your cron script Chris, as 'mostly' removing the problem is better than the current situation of resorting to standard TV...

Thanks,

Nik

---

### Post by ldobson on 2010-08-13
Yes, a well known problem with this card, and I problem I know very well.  Theres a few things you can do

Add the following to: /etc/modprobe.d/options.conf
options dvb-usb-dib0700 force_lna_activation=1
options usbcore autosuspend=-1
options dvb_usb disable_rc_polling=1
options dvb-usb-dib0700 debug=1
options mt2060 debug=1
options dibx000_common debug=1
options dvb_core debug=1
options dvb_core dvbdev_debug=1
options dvb_core frontend_debug=1
options dvb_usb debug=1
options dib3000mc debug=1

Add a crontab such as:
0 0 * * * /bin/sh /data/sources/scripts/mythrestart.sh

The script should look like:
#!/bin/sh
/etc/init.d/mythtv-backend stop
sleep 1
/sbin/modprobe -r dvb_usb_dib0700
sleep 1
/sbin/modprobe dvb_usb_dib0700
sleep 3
/etc/init.d/mythtv-backend start

My guess is you are probably seeing the mt2060 I2C write failed (len=2) and mt2060 I2C read failed in your dmesg logs.

---

### Post by mymythtv on 2010-08-17
Well - this might be a long shot, but...

Have a FE/BE - running rock solid with 9.10. Two tuner cards - T-500 and Nova S2 ( HVR4000 ).
Upgraded to Lucid and after that problems started ( around beginning of july )
First problem notied was playback froze. Focused on heat on my nivia card ( warm summer ) or even driver issue, but problem got worse.
Also noticed that T-500 recordings got garbeled - normally start my recordings 2 min ahead, and the first minutes were fine, but then recordings went bad.
Once a while a scheduled recording were ok, but...

Found another thread about kernel 2.6.32-XX having problems, so ended up with a full upgraded Lucid, but with a kernel downgraded to 2.6.31-21.

So far it has been rock solid again !

---

