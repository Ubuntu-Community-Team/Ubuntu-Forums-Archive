---
title: "[Solved] Hauppage Nova T 500 - Not detected in new backend"
date: 2014-02-26
forum: Mythbuntu
---

### Post by philip7 on 2014-02-26
Hi all, I've been working on migrating my mythbuntu setup to a new PC, everything was going well until I noticed an issue with the capture cards.

Basically, I've pulled the old tv card from my old backend and added to the new backend, I then did a fresh Mythbuntu install on the new backend.

There seems to be an issue with the capture cards, when I try and add a new card I get an error (Will post the exact error when I get back home).
I'll also run a fresh install tonight and post the relevant logs.

I've found a few posts stating that the tv card is difficult to setup, but when I installed on my old backend the cards worked straight out of the box so was hoping I wouldn't have any problems.

Does anyone have any initial ideas?

Thanks in advance

---

### Post by roburk on 2014-02-26
Hi Philip,
 
I have one of these as well, and it was not always straightforward.
 
I suppose you would have checked the device permissions already?
The user that is running mythtv setup must be able to access these devices.
 
I also found this of use a while back ([https://code.mythtv.org/trac/ticket/10830](https://code.mythtv.org/trac/ticket/10830)) although I think the condition that causes this is now fixed in the release I am using.
 
There was time when I would not have been able to detect the card were femon not running in the background.

Rob

---

### Post by khPWXxF on 2014-02-26
As a long term T500 user you are probably well aware of this but I'll mention it anyway as it's so illogical and puzzling.

The T500 has on-board storage holding the firmware and parameters which only gets re-written by a reboot following a power cycle.

I have found that if I change anything associated with the T500 or with other hardware then I need to closedown, remove power at wall socket, press 'start' a few times to discharge psu capacitors then power up and reboot.  Without that, the card retains previous code (or rubbish!) and settings.

I do not have an exhaustive list but installing new Hauppauge drivers, installing Mythbuntu afresh, changing HDMI to VGA, VGA to HDMI or changing Hauppauge parameters such as turning low noise amp on are all events I am wary of.    I'm suspicious too of even connecting USB devices.   The board will just play dead or not accept the changes without the power cycle and reload.

hope this helps.

Phil

---

### Post by blm-ubunet on 2014-02-26
Check if the device is found & firmware is loaded.
From terminal:
dmesg | grep -i dvb

IIRC The firmware is contained in linux-firmware package..

The suggested means to achieve stability include:
- disable RC IR
- disable active EIT scanning on at least one of the tuners.

Complete list of kernel module options & explanations:
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

The f/w is not necessarily uploaded (into tuner) on a warm start only cold start..this is potential problem with USB tuners that are powered in standby.

---

### Post by philip7 on 2014-02-26
Thanks for the help guys, I've posted results below

Checked the permissions below:
```

/dev/dvb/adapter0:total 0
crw-rw----+ 1 root root 212, 0 Feb 26 23:11 demux0
crw-rw----+ 1 root root 212, 1 Feb 26 23:11 dvr0
crw-rw----+ 1 root root 212, 3 Feb 26 23:11 frontend0
crw-rw----+ 1 root root 212, 2 Feb 26 23:11 net0


/dev/dvb/adapter1:
total 0
crw-rw----+ 1 root video 212, 4 Feb 26 23:11 demux0
crw-rw----+ 1 root video 212, 5 Feb 26 23:11 dvr0
crw-rw----+ 1 root video 212, 7 Feb 26 23:11 frontend0
crw-rw----+ 1 root video 212, 6 Feb 26 23:11 net0

```

I thought I was getting somewhere running [COLOR=#000000]femon, when I did this I get see the cards in setup and there were no errors, but when I followed the link to the patch and tried to implement it couldn't find the files. It does say the patch has been superseded but no other details.

[/COLOR]results are below for dmesg | grep -i dvb [COLOR=#000000]

[/COLOR]```

[    6.640453] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[    6.675331] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.384178] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[    7.384269] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    7.384424] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    7.496055] usb 3-1: DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[    8.295180] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.295284] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    8.301271] usb 3-1: DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[    8.936156] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:09.2/usb3/3-1/rc/rc0/input14
[    8.936225] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:09.2/usb3/3-1/rc/rc0
[    8.936471] dvb-usb: schedule remote query interval to 50 msecs.
[    8.936478] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[    8.936653] usbcore: registered new interface driver dvb_usb_dib0700

```[COLOR=#000000]
[/COLOR]
I'm going to make the recommended changes in the options.conf file and then leave it unplugged overnight to see what happens.

Just one other thing I'm sure the first time it booted after a fresh reinstall there was a message abou[FONT=Calibri, sans-serif]t [/FONT]dib0700 but the mythbuntu splash screen came on and I couldn't see what it said.

I might try and reinstall the driver tomorrow night

---

### Post by roburk on 2014-02-27
Hi Philip,
   
  Group ownership on adapter0 is still off by the looks of it, but adapter1 not for some reason!
  You can &#8220;quick and dirty&#8221; fix it by:
   
  sudo chgrp video /dev/dvb/adapter0/*
   
  to get you going, but that will likely disappear on the next reboot.
   
  It should be permanent if properly defined in the udev rules.
  On my box this is in the file:
  /lib/udev/rules.d/50-udev-default.rules
   
  Look for &#8220;SUBSYSTEM=="dvb"&#8221;, mine looks like this:
   
  # DVB (video)
  SUBSYSTEM=="dvb", GROUP="video"
   
  (Yours might also already, this doesn&#8217;t seem to always work as expected, hence you have one adapter with correct ownership, and the other not)
   
  On the femon thing:
   
  I found that once I got through capture card setup I was good to go.
  So, I would fire up two terminals and in each one kick off femon for one of the adapters, having both running simultaneously, so keeping both adapters &#8220;open&#8221;.
  Then start mythtv setup and define the cards as normal, then anything else needed like linking up the video sources etc.
  Then quit setup, and in the terminals stop the two femon processes.
  After that my system functioned normally.
   
  When I was having problems I just used the femon workaround whenever I had to redefine the card. 
  I never attempted to download the patch so can&#8217;t help you there. All I can say is that now I am using 0.28 I don&#8217;t seem to have the problem, although I cannot confirm exactly where and when this was fixed, only that mine appears to be!
   
  Good luck
   

  Rob

---

### Post by philip7 on 2014-02-27
Ignore my last post, I did a quick search and found this post: [https://bbs.archlinux.org/viewtopic.php?id=158027](https://bbs.archlinux.org/viewtopic.php?id=158027)

Read the 4th post and then checked my kernel version I'm on 3.8 not 3.9.

I updated the kernel, rebooted and the cards were found first time.

I'm going to do a clean reinstall and start from scratch, remembering to update the kernel.

---

### Post by roburk on 2014-02-27
Glad you got it sorted, and even better to not have to rely on workarounds.
Interestingly I am still on 3.8 with everything working fine.

Rob

---

### Post by philip7 on 2014-02-27
Thanks Rob

I assumed that running femon would be required everytime I wanted to use the cards, not just during setup.

Will keep you posted how I get on.

---

