---
title: "Leadtek DTV2000DS half works"
date: 2010-07-09
forum: Mythbuntu
---

### Post by itmarshall on 2010-07-09
I am running Mythbuntu 10.04 with a split frontend/backend setup. I have a Leadtek DTV2000DS PCI dual DVB-T tuner card, which I managed to get working correctly with MythTV.

After a kernel update to 2.6.32-23, both of my tuners stopped working, so I installed the latest V4L drivers, retrieved via Mercurial. This has gotten the system to the point where my dual tuner card how has 1 working and 1 not working tuner.

The primary tuner, an af9013 is working fine, while the secondary, an af9015 does not work any more. I have tried booting to the old (2.6.32-22) kernel and even installing 2.6.33 to no avail.

An excerpt from my dmesg is:

> $dmesg | egrep -i "(af901|tda18271|dvb)"
[   12.023806] dvb-usb: found a 'Leadtek WinFast DTV2000DS' in warm state.
[   12.023858] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.024206] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   12.075315] af9013: firmware version:4.95.0
[   12.079321] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   12.089859] tda18271 0-00c0: creating new instance
[   12.092822] TDA18271HD/C2 detected @ 0-00c0
[   12.433633] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.434030] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   12.650941] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   12.653576] af9013: firmware version:4.95.0
[   12.664957] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   12.665102] tda18271 1-00c0: creating new instance
[   12.667175] af9015: command failed:2
[   12.668706] tda18271_read_regs: [1-00c0|M] ERROR: i2c_transfer returned: -1
[   12.670801] af9015: command failed:2
[   12.672331] tda18271_read_regs: [1-00c0|M] ERROR: i2c_transfer returned: -1
[   12.672337] tda18271_attach: [1-00c0|M] error -22 on line 1272
[   12.672339] tda18271 1-00c0: destroying instance
[   12.672471] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-1/input/input7
[   12.672518] dvb-usb: schedule remote query interval to 150 msecs.
[   12.672520] dvb-usb: Leadtek WinFast DTV2000DS successfully initialized and connected.
[   12.776738] usbcore: registered new interface driver dvb_usb_af9015
[   19.498777] tda18271: performing RF tracking filter calibration
[   22.837988] tda18271: RF tracking filter calibration complete

I do not know what is causing this to suddenly fail, and am tearing my hair out trying to fix it. It is even more frustrating as it was working previously, but even going back to the old kernel is not restoring the functionality. Is this a known issue?

Thanks,

Ian

---

### Post by nickrout on 2010-07-09
do you need to turn it off for 5 minutes to make sure the firmware is loaded properly?

---

### Post by itmarshall on 2010-07-09
Holy cow, that fixed it! I performed numerous warm reboots, but no cold boots...

Thanks for the help! :D

---

### Post by nickrout on 2010-07-09
Great: the clue was > dvb-usb: found a 'Leadtek WinFast DTV2000DS' in warm state

---

### Post by shieldsduncan on 2010-10-01
Is there any chance you could post how you got this far?

I have the same TV card, on a Dell Optiplex 755 - used to run the TV on XP but saw that you'd got the card running in Myth so did the following... 

installed Mythbuntu 10.04
added mercurial
used mercurial do get latest V4l drivers
installed drivers

Unfortunately, the card is still not showing up in dmesg - I don't get any DVB lines in there at all.

Bit fresh to Ubuntu but can't really see what I'm missing.

Any help would be gratefully received.

Ta.

---

### Post by itmarshall on 2010-10-04
It looks to me like all you need to do is download and install the firmware for the card.

I downloaded them from [http://otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/) but that link isn't currently working for me when I tried it just now. Elsewhere, I saw it mentioned that you can use Synaptic/apt-get to install the "linux-firmware-nonfree" package, but I haven't tried that myself.

If you still can't find the firmware, you could try searches for firmware for the "af9015" chip that is used on the DTV2000DS and install it to "/lib/firmware/dvb-usb-af9015.fw"

The following thread helped me set up initially: [http://ubuntuforums.org/showthread.php?t=606487](http://ubuntuforums.org/showthread.php?t=606487)

Good luck!

---

### Post by nickrout on 2010-10-04
> **itmarshall said:**
> It looks to me like all you need to do is download and install the firmware for the card.

I downloaded them from [http://otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/) but that link isn't currently working for me when I tried it just now. Elsewhere, I saw it mentioned that you can use Synaptic/apt-get to install the "linux-firmware-nonfree" package, but I haven't tried that myself.

If you still can't find the firmware, you could try searches for firmware for the "af9015" chip that is used on the DTV2000DS and install it to "/lib/firmware/dvb-usb-af9015.fw"

The following thread helped me set up initially: [http://ubuntuforums.org/showthread.php?t=606487](http://ubuntuforums.org/showthread.php?t=606487)

Good luck!

The file you seem to be referring to is certainly in the linux-firmware-nonfree package:

[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist)

---

