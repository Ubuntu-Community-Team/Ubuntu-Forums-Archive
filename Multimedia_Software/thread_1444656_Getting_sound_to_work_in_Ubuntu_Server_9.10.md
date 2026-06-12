---
title: "Getting sound to work in Ubuntu Server 9.10"
date: 2010-04-01
forum: Multimedia Software
---

### Post by ClintSwiney on 2010-04-01
I have an Ubuntu Server 9.10 setup as a LAMP server using the Perfect Server setup over at howtoforge. 

It's working quite nicely. The system has a sound card in it that I'd like to make active, my goal is to run a script or other app from the BASH that will play a set of MP3 files randomly. I have found several ways to accomplish this task already. It's going to be used as a Music on Hold Server. I want to replace a Windows Server that keeps on breaking the Music on hold for various stupid reasons.

I have gone through the installation of pulseausio here: 

[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

I also ran through this procedure, even recompiled ALSA from source.

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

I tried everything but did not find a solution to my issue, basically there is no sound....

In > pacmd if I do a list-cards it says 0 cards available.

This is my lspci output:

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
02:04.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
02:07.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


The Audio Card is onboard audio, The driver works and apparently is installed.

If I run > aplay -l I get no card detected

If I run > sudo aplay -l It detects a card

If I do > speaker-test it looks like it's working but no audio comes out, I changed plug the speaker is plugged into to all of the available outlets and still nothing.

If I run > sudo speaker-test it gives an access denied message.


Does anyone know if there is a way to get the audio working on an Ubuntu 9.10 Server?

Please don't say that Servers should not have audio, I know that! This is a special situation.

---

### Post by uMany on 2010-04-01
Hi,

Take a look to:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

I don't know if this work in the server version. It works awesome in generic.

Hope you solve your issue

---

### Post by GeoffBee on 2011-07-16
First you need a command line mixer. 

  sudo apt-get aumix

Next add yourself to the audio group.

  sudo addgroup YOURUSERNAME audio

logout then log back in again. You may need to reboot if your name doesn't appear in the audio group.

  groups

Your name should show up as a member member of the audio group.

  aumix

opens the commandline mixer use your left / right arrows to turn up Vol to about 3/4

Arrow down and turn Pcm up to a similar level. Hit s to save your settings then q to quit.

Do your speaker-test again and you should get sound :)

---

