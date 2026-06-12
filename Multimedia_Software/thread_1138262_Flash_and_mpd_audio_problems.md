---
title: "Flash and mpd audio problems"
date: 2009-04-26
forum: Multimedia Software
---

### Post by zorblek on 2009-04-26
Sometimes flash audio stops working for no apparent reason in Firefox. I'm wondering if this is somehow connected to mpd. I use mpd with Sonata for music, and it, too occasionally stops working for no apparent reason. Switching to a virtual terminal and back fixes the problem with mpd/Sonata, but not with flash, which only starts working again when I restart Firefox. They don't necessarily stop working at the same time (I am often able to play audio with Sonata but not flash), but they often seem to quit when I have both running simultaneously, which is why I wonder if there is a connection.

This is on Jaunty with the latest versions of all programs involved. Please let me know if there's some useful log I can provide. I don't know a whole lot about Linux sound.

Thanks!

---

### Post by NJLash on 2009-07-26
I'm having similar problems.  Currently i am unable to get flash working and sometimes mpd cuts out and i have to restart.  I'm using pulseaudio for mpd and alsa for everything else....

---

### Post by martinbaselier on 2009-07-26
What kind of audiocard do you have? Does flash suddenly stop playing sounds or do you have other symptoms?

---

### Post by NJLash on 2009-07-26
I have a Macbook 2,1 (i tried to look up audio card, can't find it, i'm a noob).  Flash originally was working fine, but after installing mpd, I don't have sound from flash or even rhythmbox.  When I stop mpd and open firefox, there still isn't sound.  then, I restart mpd, and now there is no sound for that either!

---

### Post by igorzwx on 2009-07-26
OK.
no problem
type on terminal:

aplay -l

---

### Post by NJLash on 2009-07-26
aplay: device_list:217: no soundcards found...

ummm I know thats not true...

---

### Post by igorzwx on 2009-07-26
aplay means alsa play

do you have OSS4?

---

### Post by NJLash on 2009-07-26
no oss. alsa.

---

### Post by igorzwx on 2009-07-26
lspci > hardwareinfo.txt
gedit hardwareinfo.txt

---

### Post by NJLash on 2009-07-26
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by igorzwx on 2009-07-26
Let us check.
If you have not OSS4, this command should not work:

osstest

---

### Post by NJLash on 2009-07-26
also, while mpd is playing, I tested of the options under gstreamer-properties, and there were no sounds.

---

### Post by NJLash on 2009-07-26
yep, command not found.  I don't have oss.

---

### Post by igorzwx on 2009-07-26
Does this command work or not?

osstest

---

### Post by NJLash on 2009-07-26
it does not work

---

### Post by igorzwx on 2009-07-26
OK

Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by martinbaselier on 2009-07-26
What does 
**sudo lspci -v 00:1b.0**
show? 

You can select text on a terminal and then use the right mousebutton to copy (or ctrl+shift+C, which will probably be apple+shift+c in your case)

---

### Post by NJLash on 2009-07-26
Thanks for your patience!

Heres what i got:
njlash@njlash-laptop:~$ sudo lspci -v 00:1b.0
[sudo] password for njlash: 
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
njlash@njlash-laptop:~$ sudo lspci -v 00:1b.0
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file

---

### Post by NJLash on 2009-07-26
looks like oss supports my card... would you recommend moving forward with that?

---

### Post by igorzwx on 2009-07-26
Can you install another Ubuntu 9.04 in dual boot (for experiments)?

read this howto several times and try it:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by martinbaselier on 2009-07-26
I made a mistake in the syntax. It should be:
sudo lspci -s 00:1b.0 -v

I would definitely recommend oss. I've created a guide on how to install it. See my signature.

---

### Post by NJLash on 2009-07-26
martin, your instructions look very good.  i'm gonna try it.  i have osx on my other partition, so i got nothing to lose. :)

---

### Post by igorzwx on 2009-07-26
for High Definition Audio (HDA)
you may need this info

[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")

[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

read it in any case

---

### Post by NJLash on 2009-07-26
So i've fooled around with oss for a while, moving stuff around the middle panel of ossxmix, but no sound at all...

---

### Post by igorzwx on 2009-07-26
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Troubleshooting**

 If you run into problems, follow these steps first: 
 
**Recovering From a Failed .deb Install**

 If you use the .deb package and it fails to install completely, [use this procedure]("http://ubuntuforums.org/showpost.php?p=5055305&postcount=105") to remove it. 
 
**Consult the OSS wiki**

 The wiki's [Troubleshooting page]("http://www.opensound.com/wiki/index.php/Troubleshooting") may already have an answer to the problems you have. 
 
**Additional Support**

 If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 
ossmix
ossinfo -v3Also, you'll want to note if the osstest command works and plays sound. 
 
**Forums**

 You can make a thread on [the OpenSound user forums]("http://www.4front-tech.com/forum/index.php").  
 
**IRC**

 [Freenode]("http://freenode.net/irc_servers.shtml") hosts the OSS support channel (#oss). You can paste your support information from the aforementioned commands [here]("http://oss.pastebin.com/") 
 
**Reverting to ALSA**

 NOTE: I've tested this procedure (on an Intrepid install) and was successful, but some people are complaining that it does not work. If you see any errors, please respond to the forum post. Some users wish to revert back to ALSA to try Creative's X-fi drivers or maintain complete Ubuntu compatibility. [Click here]("http://ubuntuforums.org/showpost.php?p=5539687&postcount=331") for the procedure.

---

### Post by PeterDarkness on 2010-11-09
I apologize for resurrecting the thread. However, I've been having the same conflict with mpd and flash. The solution for me (Karmic) was to change the mpd audio config. Found this piece of info on the arch forums...

The base config being

```
    audio_output {
        type        "alsa"
        name        "My ALSA Device"
        device        **"hw:0,0"**    # optional
        format        "44100:16:2"    # optional
        mixer_device    "default"    # optional
        mixer_control    "PCM"        # optional
        mixer_index    "0"        # optional

    }
```

Changing the bolded bit to "default" solved the issue. Much simpler than installing OSS imho. 

Source: [[Solved] mpd + flash(?) = CRASH]("https://bbs.archlinux.org/viewtopic.php?id=83192")

---

