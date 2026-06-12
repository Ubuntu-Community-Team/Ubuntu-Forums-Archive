---
title: "Toshiba Satellite laptop - no sound - everything unmuted"
date: 2011-09-10
forum: Multimedia Software
---

### Post by JDacapo on 2011-09-10
I have a toshiba satellite that is duel booted with windows and Ubutnu 11.04. Ubuntu works great, but windows is sluggish. Until today, the sound worked perfectly, but then it just stopped. I had installed Open Modplug Tracker with WINE and tried to play it. It made no sound, and I thought it was just the program. Then I watched a youtube video, and it had no sound. I even tried using the GNOME audio mixer and unmuted a bunch of things, but there still was no sound. I then tried the instructions on this page here:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

but it didn work and it said there were some problems installing the packages. When I rebooted, the sound-controller icon had dashes in front of it instead of waves, and when I selected it, it said there was no audio device available. So I tried this command:

sudo apt-get update && sudo apt-get -y --reinstall install alsa-base alsa-utils; killall pulseaudio; rm -r ~/.pulse*

from this page: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/167312](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/167312)

and even then I had some problems, something about some generic headers missing.


So I went into the terminal and typed in sudo lspci and got this:


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)


I now have the sound controls, but the computer won't play any sound. Is there anything wrong with the sound card?

---

### Post by sdowney717 on 2011-09-10
read here someone with that controller had no sound and solved it
[http://ubuntuforums.org/showthread.php?t=161193&page=2](http://ubuntuforums.org/showthread.php?t=161193&page=2)

Double-click the sound icon from the top panel
Go to Edit->Preferences from the menu bar
Scroll down to the bottom and check the External Amplifier (you do want this selected; this just lets us change its settings)
Hit Close
You should now have a tab called Switches that you can now click on
External Amplifier should be here, and you can now uncheck it to disable it
Your sound should now work!

---

### Post by JDacapo on 2011-09-10
THANK YOU! IT WORKS! Just tested it out with the "Bate o Pé" cockatiel video and didn't even expect any sound but it WORKS! And man I was just tying myself in knots trying to make this darn computer do what I wanted. Even was fighting with windows, which was pretty sluggish. Someday I might just wipe the drive on this lovely computer and put Ubuntu Studio on it.

Right now everything is groovy, though I do still need some help with making ZynAddSubFX actually make sound, as well as how to work with JACK. Anyone here have experience with that area?

---

