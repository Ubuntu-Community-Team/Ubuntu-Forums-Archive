---
title: "No sound with OSS"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by disk11 on 2008-01-06
I lost sound last night when installing my TV card, so I switched from ALSA to OSS v4 per Temüjin's instructions [here.]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60")  Installing the .deb worked fine, but I still have no sound.

ossinfo output:
```
Version info: OSS 4.0 (b1012/200801022350) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (server)

Number of audio devices:        1
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH5 (24D5) interrupts=27510 (27510)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (ALC658) (Mixer 0 of device object 1)

Audio devices
Intel ICH5 (24D5)                 /dev/oss/ich0/pcm0  (device index 0)

```

Here's the lspci output:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
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
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a3)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:06.0 Mass storage controller: Promise Technology, Inc. PDC20267 (FastTrak100/Ultra100) (rev 02)
02:07.0 Ethernet controller: Altima (nee Broadcom) AC9100 Gigabit Ethernet (rev 15)

```

And here's dmesg|grep oss:
```
[   39.875642] Adding 2000052k swap on /dev/sda1.  Priority:-1 extents:1 across:2000052k
**[  140.768807] ich: no version for "oss_register_device" found: kernel tainted.**
[  140.832483] usbcore: registered new interface driver ossusb
[ 1829.956214] usbcore: deregistering interface driver ossusb
[ 1911.138187] usbcore: registered new interface driver ossusb
[ 1994.290582] usbcore: deregistering interface driver ossusb
[ 1998.098980] usbcore: registered new interface driver ossusb

```

The bolded part worries me, and I couldn't find anything that helps me though google.

osstest shows all tests completed OK.

I am using Klipsch ProMedia 2.1s and Sony MDR-V600 headphones to no avail.

---

### Post by Yellow Pasque on 2008-01-06
Hi. Sorry to hear you're having issues. Have you run ossxmix to make sure nothing's muted?
Don't worry about the kernel tainted issue

Also, it looks like you're having issues with the ossusb driver, which you probably don't need. So:
```
sudo gedit /usr/lib/oss/etc/installed_drivers
```
Remove the ossusb line and save.

Log out and log back in with a Failsafe Terminal session. Then:
```
sudo soundoff
sudo soundon
exit
```

Log back in with the normal "Xclient script" session and see if sound works now.

---

### Post by disk11 on 2008-01-06
First, I should mention I did a reinstall of 7.10.  But I did redo the OSS install instructions you posted.

When I go do the "sudo soundoff" in fail-safe terminal, I get this:
```
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
SNDCTL_MIX_READ: No such device or address
FATAL: Module osscore is in use.
Cannot unload the OSS driver modules

```

osstest fails now, and I can't open ossxmix with any flag.  Here is the output of ossinfo:
```
Version info: OSS 4.0 (b1012/200801022350) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 (server)

Number of audio devices:        1
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH5 (24D5) interrupts=14360 (14360)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: (ICH AC97 Mixer (ALC658) )(Mixer 0 of device object 1)

Audio devices
(Intel ICH5 (24D5)                 /dev/oss/ich0/pcm0 ) (device index 0)

```

---

### Post by Yellow Pasque on 2008-01-06
Well, now you have to reboot. Before you do, make sure the /usr/lib/oss/etc/installed_drivers file still does not contain the line to load the usb driver.

---

### Post by disk11 on 2008-01-06
No usb line in that file and rebooted.  Ossxmix comes up now, but still no sound.  When I fire up audacious and play a song, vmix0-out has some colored bars show up.  Does this mean I have something muted?

---

### Post by Yellow Pasque on 2008-01-06
In ossxmix, do you have the front audio routed correctly (to DMA)?
Also, have you chosen the OSS output plugin in the Audacious preferences?

---

### Post by disk11 on 2008-01-06
I have audacious set properly, and I don't see what you are talking about in ossxmix.

---

### Post by Yellow Pasque on 2008-01-06
Ok, I think I understand now. Post the output of:
```
ossinfo -e
```

I just logged on to AIM, so you can click the AIM icon in my post header and hit me up there if you have it.

---

### Post by Insomnia777 on 2008-01-06
Still no sound, here's the output of ```
ossinfo -e
```

```
abner@R2D2:~$ ossinfo -e

Audio engines
00: Intel ICH5 (24D5) (device file /dev/oss/ich0/pcm0)
01: Intel ICH5 (24D5) (device file audio_engine1)
02: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
03: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
04: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
05: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
06: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
07: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
08: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)
09: Intel ICH5 (24D5) (VMIX0) (device file /dev/oss/ich0/pcm0)

```

---

### Post by Yellow Pasque on 2008-01-06
We tried a few different things and had no success, so we're taking it to the experts on the OSS forum. Follow this thread: [http://4front-tech.com/forum/viewtopic.php?t=2414](http://4front-tech.com/forum/viewtopic.php?t=2414)

---

### Post by Insomnia777 on 2008-01-06
seawright wrote:

Does any sound play in response to osstest and are any error messages displayed?
No, this is what osstest shows on shell:
```
abner@R2D2:~$ osstest
Sound subsystem and version: OSS 4.0 (b1012/200801022350) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007

*** Scanning sound adapter #-1 ***
/dev/oss/ich0/pcm0 (audio engine 0): Intel ICH5 (24D5)
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47975.00 Hz (-0.05%)> 

*** All tests completed OK ***
```

How are loudspeakers connected? "Through a cable? :P the socket is out so I presume it is internal?"

If internal is there a headphone socket? "Yes"
If yes, does it work? "No"

---

### Post by Insomnia777 on 2008-01-07
:/ no help here? I found something on how to fix it with alsa but I don't have it anymore :( ...

---

### Post by disk11 on 2008-01-07
I posted in the 4front thread, and no action over there either.

I'm half tempted to format and install Windows on the box in question just to see if it even works, since when I reinstalled alsa didn't work either.

---

### Post by Insomnia777 on 2008-01-08
Disk11 try this, if it works tell me how to reinstall Alsa and unninstall the OSS one

Go in as root (or sudo) : **/etc/modprobe.d/alsa-base**

It will probably appear these 2 lines
[b]# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/b]

Add this
**options snd-hda-intel model=3stack**

It will look like this
[b]# Ubuntu #62691, enable MPU for snd-cmipci
#options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack[/b]

Save and Restart...

---

### Post by Yellow Pasque on 2008-01-08
Insomnia, I'm sorry that my solution didn't work for you. If you'd like to continue trying to get ALSA to work, just boot into recovery mode and do the following and you should be back to where you were.
```
sudo soundoff
sudo apt-get -P oss-linux
sudo apt-get install alsa-base
```

---

### Post by Insomnia777 on 2008-01-08
I did sudo soundoff

and when I do ```
sudo apt-get -P oss-linux
```

I get
```
 E:command line option 'p' [from -p] is not known.
```

I think I have to reinstall 7.10 :/ :(

---

### Post by disk11 on 2008-01-08
To me, it seems like he wants you to do
```
sudo apt-get remove --purge oss-linux
```

Which will remove the install and config files.

I guess I'll give ALSA another shot with that edit you suggested.  Be back shortly to post results.

---

### Post by disk11 on 2008-01-08
Man, still no sound.  I think I fried the output jack:(  I wonder if I can get the front panel to work...

Holy confusion batman!  Everything works again.  It seems my system didn't like me unplugging the front panel connector.  I don't understand how or why it makes a difference but it works now!

---

### Post by Yellow Pasque on 2008-01-09
> **Insomnia777 said:**
> I did sudo soundoff and when I do ```
sudo apt-get -P oss-linux
```
I get
```
 E:command line option 'p' [from -p] is not known.
```

I think I have to reinstall 7.10 :/ :(

Sorry, my mistake. I meant sudo dpkg -P oss-linux

---

