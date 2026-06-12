---
title: "Alsa stops working after an update"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by flakeparadigm on 2008-03-06
I installed an update yesterday ( 03/04/08 ) and now my sound doesn't work, except for the line-in on my computer. Could anyone help me?

---

### Post by {BzF}~JOKesTER on 2008-03-06
Possible That By Going To The "Sound" Setting In "Control Center"

That You Can Set The Sounds Defualt Driver Back To ALSA??

And Than Click "Test" And See If It Works?

If It Gives An Error Code Please Give It

Hope This Helps

---

### Post by flakeparadigm on 2008-03-06
That didn't help. no sound still. I tried amarok and it said that the device is busy ("Audio Output; device is busy. xine parameters: ), and Kmix reports that there is no device. ("Mixer cannot be found")

---

### Post by {BzF}~JOKesTER on 2008-03-06
In The Sounds Dialog In Control Center

Under The Default Mixer Tracks Drop-Down Box What Mixers Are There??

---

### Post by flakeparadigm on 2008-03-06
I don't see anything about Mixer Tracks anywhere. Control Center, where exactally whould that be? Sorry if i sound kinda stupid, but i kinda am. (Still trying to learn this stuff)

---

### Post by {BzF}~JOKesTER on 2008-03-07
That Is Ok - You Don't Sound Stupid. {Everyone Needs Help:)}

Ok Heres How To Get To Control Center.

First In Your Tray {Most Likely At The Bottom Of Your Screen - Unless You Moved It}

Click The "System" Tab - It Will Expand.

Now Click The "Preferences" Tab - It Will Also Expand.

Finally, Click The "Control Center" Button.

This Will Open The Control Center....

Now In Control Center Find The Icon Titled "Sound" And Click It...

Seeing As Your Having Trouble With ALSA - In Each Of The Drop Down Boxes - Go Through Them And Set Them To Different Settings - And Hit "Test" Until You Get Sound From Each Of Them - {Except- Sound Capture}

Now,

The Last Drop-Down Box Gives You Your Default Mixer Tracks.
Which Of These Do You Have - Also If You Couldn't Get Sound To Work Before This Point,
Try Selecting A Different Mixer Track And - Going Trough Hitting "Test" On Every Selection Again.

If The Problem Is Still Not Solved Let Me Know!!!

Glad To Help!:):popcorn:

---

### Post by flakeparadigm on 2008-03-07
I found the control center. I realized I couldn't find it because I was using KDE and your were explaining it in GNOME, so I pulled it up and tested all the different setting and none of them worked. I wish I could figure out the problem.

---

### Post by Bubba64 on 2008-03-07
This is a description of stuff you need probably even in KDE you can find alot of it already in synaptic or you can use the terminal.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by flakeparadigm on 2008-03-07
Ok, thanks. I might greatrly benifit from that softwarer, but one problem...
Still no sound. Well, if anyone else has any other suggestions I will be glad to try them.

---

### Post by {BzF}~JOKesTER on 2008-03-08
In The Terminal Type:

apt-get remove alsa-base --purge

And

apt-get remove alsa-oss --purge

now type

apt-get install alsa-base

And

apt-get install alsa-oss

Now Restart You Computer...

Hope This Helps:)

---

### Post by flakeparadigm on 2008-03-09
No success that time either. This is very odd.

---

### Post by Yellow Pasque on 2008-03-09
What kind of sound card do you have? (lspci if you don't know)
Also, I don't want to insult your intelligence, but many smart folk have been burned by the "ALSA likes to mute itself for no apparent reason, especially after an update" bug. Go into alsamixer and mute/unmute everything a few times.

---

### Post by flakeparadigm on 2008-03-09
Ok, my card is VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller. I have checked alsamixer several times to see if it is muted, and again it isn't muted.

---

### Post by Yellow Pasque on 2008-03-09
Maybe try the latest version of ALSA? See this post I just made for someone else. The script is already configured for the via82xx drivers
[http://ubuntuforums.org/showpost.php?p=4480877&postcount=2](http://ubuntuforums.org/showpost.php?p=4480877&postcount=2)

---

### Post by flakeparadigm on 2008-03-09
The script was working up until it required libasound. The error says
"checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found."

---

### Post by xeth_delta on 2008-03-09
That means that you need to install the alsa headers. Try installing the package alsa-source via apt-get.
Alternarively, you can follow the instructions I gave to another user in [http://ubuntuforums.org/showthread.php?t=672290](http://ubuntuforums.org/showthread.php?t=672290), post #18. In the driver compilation section change
```
./configure --with cards=hda-intel --with-oss=yes --with-sequencer=yes
```
with
```
./configure --with cards=via82xx --with-oss=yes --with-sequencer=yes
```

---

### Post by flakeparadigm on 2008-03-09
Well, that didn't work either. GRR. Here is a pastebin of 'lsmod | grep -i snd'.
[http://pastebin.com/maae87bc]("http://pastebin.com/maae87bc")

---

### Post by Josh C on 2008-03-09
Same thing with me.  No sound after this weekends update.

---

### Post by danielcc on 2008-03-09
the terminal alsa mixer wont work?  type alsamixer into the oll terminal and see what it does, then make sure all of your volumes are cranked up

---

### Post by xeth_delta on 2008-03-09
> **flakeparadigm said:**
> Well, that didn't work either. GRR. Here is a pastebin of 'lsmod | grep -i snd'.
[http://pastebin.com/maae87bc]("http://pastebin.com/maae87bc")

What did not work? Did yot try the method I suggested in the link?

---

### Post by flakeparadigm on 2008-03-09
the method you suggested by the link didn't work. Whats is odd though is that all the volume controls are the same and haven't changed. No errors or anything. Its odd.

---

### Post by flakeparadigm on 2008-03-09
> **danielcc said:**
> the terminal alsa mixer wont work?  type alsamixer into the oll terminal and see what it does, then make sure all of your volumes are cranked up

Alsamixer in the terminal comes up and shows all of the channels as usual.

---

### Post by Josh C on 2008-03-09
My alsa mixer is working.  The middle option IEC958 is at 0 and cannot be changed.  I don't remember if this option was available before.  I have already uninstalled and reinstalled alsamixer has shown above.  Still no system sounds, no sound from the web, no sound from saved media files.  Please help.

---

### Post by flakeparadigm on 2008-03-09
> **Josh C said:**
> My alsa mixer is working.  The middle option IEC958 is at 0 and cannot be changed.  I don't remember if this option was available before.  I have already uninstalled and reinstalled alsamixer has shown above.  Still no system sounds, no sound from the web, no sound from saved media files.  Please help.

What card do you have?

---

### Post by xeth_delta on 2008-03-09
> **flakeparadigm said:**
> the method you suggested by the link didn't work. Whats is odd though is that all the volume controls are the same and haven't changed. No errors or anything. Its odd.

Can you please be more explicit on what did not work? That way we can help you better. Please copy the error messages and paste them here, between CODE tags (use the # button in the post page).

Let me see if I understand. You can use the mixer but have no sound? Run the following and paste the output here

```
sudo lshw -C sound
dmesg | grep -i via
lsmod | grep -i snd
```

---

### Post by flakeparadigm on 2008-03-09
'sudo lshw -C sound' outputs:
>   *-multimedia
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

'dmesg | grep -i via' outputs:
> [   18.690750] CPU0: Centaur VIA Esther processor 1500MHz stepping 09
[   20.534013] PCI: VIA PCI bridge detected. Disabling DAC.
[   28.526599] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   31.694395] sata_via 0000:00:0f.0: version 2.2
[   31.694939] sata_via 0000:00:0f.0: routed to hard irq line 11
[   31.695076] scsi0 : sata_via
[   31.695159] scsi1 : sata_via
[   32.134132] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   44.774834] agpgart: Detected VIA VT3314 chipset

'lsmod | grep -i snd' outputs:
> snd_via82xx            29848  2
gameport               16776  1 snd_via82xx
snd_ac97_codec        101924  1 snd_via82xx
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            42784  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11656  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9984  1 snd_via82xx
snd_seq_oss            35456  0
snd_seq_midi            9632  0
snd_rawmidi            25888  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
snd_seq                54352  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9740  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56740  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

By the way, i don't know much about this problem because there are no error messages of any sort.

---

### Post by xeth_delta on 2008-03-09
From the ouput I can deduce that the modules/drivers are loaded,  the card is claimed by them.

What brand and model is your system? You could try reconfiguring alsa:
```
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils
```
Then reboot.

---

### Post by flakeparadigm on 2008-03-09
I have reconfigured alsa before, but I will try again. MY system is an Everex gPC

**reconfiguration didn't work**

---

### Post by xeth_delta on 2008-03-09
ok, try the following
```
sudo /etc/init.d/alsa-utils restart
```
or
```
sudo /etc/init.d/alsasound restart
```
then
```
dmesg | grep -i snd
```
```
dmesg | grep -i 82
```
```
dmesg | grep -i codec
```

I am looking for a line similar to
```
hda_codec: STAC922x, Apple subsys_id=106b2200
```
which is for my laptop. STAC922x is the codec used in the sound card. Once we find out what codec your card uses we can pass module arguments for load time, which might correct your problem.

---

### Post by flakeparadigm on 2008-03-09
The only command that had any kind of output was 'dmesg | grep -i 82'.
The only line (i believe) that has anything about the sound card is line 14
Here are the results:
```
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bee0000 (usable)
[    0.000000]  BIOS-e820: 000000001bee0000 - 000000001bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bee3000 - 000000001bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001bf00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[   18.167829] Freeing SMP alternatives: 11k freed
[   19.514482] Time:  1:20:04  Date: 02/10/108
[   19.546825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.204989] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   29.620753] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.620865] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.621321] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.843921] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   32.994185] FDC 0 is a post-1991 82077
[   35.654782] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   35.812827] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   54.589182] Adding 5245212k swap on /dev/hda3.  Priority:-1 extents:1 across:5245212k
```

---

### Post by Josh C on 2008-03-10
> **flakeparadigm said:**
> What card do you have?

josh@josh-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, fast devsel, latency 0, IRQ 20
Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
I/O ports at 1800 [size=8]
Memory at c0000000 (32-bit, prefetchable) [size=256M]
Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, fast devsel, latency 0
Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
Memory behind bridge: 30000000-300fffff
Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
I/O behind bridge: 00002000-00002fff
Memory behind bridge: d0100000-d01fffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) (prog-if 01 [AHCI 1.0])
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
I/O ports at 18b0 [size=8]
I/O ports at 18a4 [size=4]
I/O ports at 18a8 [size=8]
I/O ports at 18a0 [size=4]
I/O ports at 1890 [size=16]
Memory at d0544400 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: medium devsel, IRQ 10
I/O ports at 18c0 [size=32]

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 1363
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Hewlett-Packard Company Unknown device 30a5
Flags: bus master, medium devsel, latency 32, IRQ 20
I/O ports at 2000 [size=256]
Memory at d0100000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

---

### Post by xeth_delta on 2008-03-11
Josh, You have the same chipset I do. Try the instructions I gave in [http://ubuntuforums.org/showthread.php?t=672290](http://ubuntuforums.org/showthread.php?t=672290), post #18. Let me know if you need any help.

---

### Post by Josh C on 2008-03-11
Maybe a stupid question, but I don't want to mess anything up.  I downloaded those 3 files in step 1.  When I go to extract them where should I be saving them?  I'm guessing not to my desktop which is coming up by default.  Sorry for the simple question, but I am very new to Linux and no nothing about programming.  Thanks

---

### Post by xeth_delta on 2008-03-12
> **Josh C said:**
> Maybe a stupid question, but I don't want to mess anything up.  I downloaded those 3 files in step 1.  When I go to extract them where should I be saving them?  I'm guessing not to my desktop which is coming up by default.  Sorry for the simple question, but I am very new to Linux and no nothing about programming.  Thanks

Don't worry, there are almost no silly questions. Following the commands I provided, the files will be extracted in the same directory you had the tr.bz2 archives. If you want to avoid having them on the desktop, just create a new directory in your home directory cand copy the archives in there and uncompress them.

---

### Post by flakeparadigm on 2008-03-12
I still haven't gotten my sound to work. If anyone has any other ideas, please tell me.

---

### Post by xeth_delta on 2008-03-12
Flakeparadigm, what I can suggest to you know is to recompile the alsa modules. Please tell me what exactly did not work from the indications I posted in the other thread.
What was the error? Did it stop at compilation or configuration time?

---

### Post by flakeparadigm on 2008-03-12
I was looking around at some other posts and tried the command 'aplay -l'. Should there be two entries for my one card?

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by xeth_delta on 2008-03-12
> **flakeparadigm said:**
> I was looking around at some other posts and tried the command 'aplay -l'. Should there be two entries for my one card?

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Do you have an extra card on your computer besides the on-board one?
Post the output of the following:
```
sudo lshw -C sound
```
[EDIT] Any success with the compilation?

---

### Post by Josh C on 2008-03-12
I extracted the files to my desktop.  I did the next step also.  
When I went to 
cd alsa-lib-1.0.16
./configure
make
sudo make install

I get error...
josh@josh-laptop:~$ cd alsa-lib-1.0.16
bash: cd: alsa-lib-1.0.16: No such file or directory
josh@josh-laptop:~$ ./configure
bash: ./configure: No such file or directory
josh@josh-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
josh@josh-laptop:~$ sudo make install


How do I make it find the files on the desktop?



Actually, nevermind...I guess.  I just tried Youtube and sound is working again.  Also working through Amarok.  Perhaps this  sudo aptitude install libncurses5 libncurses5-dev   fixed it.  I deleted the downloaded files from my desktop and I still have sound.  Thank you.

---

### Post by bobkat60 on 2008-03-12
> **{BzF}~JOKesTER said:**
> In The Terminal Type:

apt-get remove alsa-base --purge

And

apt-get remove alsa-oss --purge

now type

apt-get install alsa-base

And

apt-get install alsa-oss

Now Restart You Computer...

Hope This Helps:)

Hi I wonder if you could help me .
 this worked as far as getting the sound going in the session I was in BUT as soon as I tried to reboot I lost it all again. what next,  it appears that something kicks in before I start session again and resets the sound off my proper settings. got suspicions about Nvidia gforce 3d legacy new drivers ?
 Bobkat60

---

### Post by bobkat60 on 2008-03-12
Hi again  First I uninstalled my Nvidia driver in restricted drivers , I went on  following XSeth-Delta's advice :Quote:
In terminal
 sudo dpkg-reconfigure alsa-base
sudo dppkg-reconfigure alsa-utils
Then reboot.
I did this, then after trying sound, (OK)
 I reinstalled my Nvidia gforce  restricted driver (legacy new)
retried  sound (OK again ) 
rebooted to see if all remained OK ...... It has ,Hope this helps you
With Thanks to Xeth-Delta as well
 Bobkat60

---

### Post by xeth_delta on 2008-03-13
> **Josh C said:**
> I extracted the files to my desktop.  I did the next step also.  
When I went to 
cd alsa-lib-1.0.16
./configure
make
sudo make install

I get error...
josh@josh-laptop:~$ cd alsa-lib-1.0.16
bash: cd: alsa-lib-1.0.16: No such file or directory
josh@josh-laptop:~$ ./configure
bash: ./configure: No such file or directory
josh@josh-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
josh@josh-laptop:~$ sudo make install


How do I make it find the files on the desktop?



Actually, nevermind...I guess.  I just tried Youtube and sound is working again.  Also working through Amarok.  Perhaps this  sudo aptitude install libncurses5 libncurses5-dev   fixed it.  I deleted the downloaded files from my desktop and I still have sound.  Thank you.

Glad your sound is back again.
For what it's worth, the errors you got meant that the directory alsa-lib-1.0.16 does not exist in the place you were looking in.
I really doubt installing the ncurses libraries fixed your sound, they don't relate to sound system, but to terminal graphics. It was probably something else you tried.

---

### Post by xeth_delta on 2008-03-13
> **bobkat60 said:**
> Hi again  First I uninstalled my Nvidia driver in restricted drivers , I went on  following XSeth-Delta's advice :Quote:
In terminal
 sudo dpkg-reconfigure alsa-base
sudo dppkg-reconfigure alsa-utils
Then reboot.
I did this, then after trying sound, (OK)
 I reinstalled my Nvidia gforce  restricted driver (legacy new)
retried  sound (OK again ) 
rebooted to see if all remained OK ...... It has ,Hope this helps you
With Thanks to Xeth-Delta as well
 Bobkat60

Good to know sound is working again for you, too.

---

### Post by flakeparadigm on 2008-03-13
> **xeth_delta said:**
> Do you have an extra card on your computer besides the on-board one?
Post the output of the following:
```
sudo lshw -C sound
```
[EDIT] Any success with the compilation?

I only have the on-board sound.

'sudo lshw -C sound':
```
  *-multimedia
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

```

---

### Post by xeth_delta on 2008-03-13
> **flakeparadigm said:**
> I only have the on-board sound.

'sudo lshw -C sound':
```
  *-multimedia
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

```

Good. Sorry for asking once again. Can you tell me what was the error when trying to compile?

---

### Post by flakeparadigm on 2008-03-13
There were no errors when compiling.

---

### Post by flakeparadigm on 2008-03-13
I was looking at [http://ubuntuforums.org/showpost.php?p=4444297&postcount=18]("http://ubuntuforums.org/showpost.php?p=4444297&postcount=18") again and did it over, but it didn't help.

---

### Post by xeth_delta on 2008-03-14
> **flakeparadigm said:**
> I was looking at [http://ubuntuforums.org/showpost.php?p=4444297&postcount=18]("http://ubuntuforums.org/showpost.php?p=4444297&postcount=18") again and did it over, but it didn't help.

Since you compiled and installed the three packages, now you should have a script called alsasound, call it:
```
sudo /etc/init.d/alsasound restart
```
Then
```
dmesg
```
Hopefully this time there will be information on your sound card in its output.

---

### Post by flakeparadigm on 2008-03-16
I was getting frusterated, and installed a new sound card. it works fine. Sorry I haven't replied, but atlease my sound works now. I will continue though to see if i can get my other sond card working anyway.

---

### Post by xeth_delta on 2008-03-16
> **flakeparadigm said:**
> I was getting frusterated, and installed a new sound card. it works fine. Sorry I haven't replied, but atlease my sound works now. I will continue though to see if i can get my other sond card working anyway.

Good to know you have sound now. Keep us updated, please.

---

### Post by flakeparadigm on 2008-03-17
I booted it up on live CDs of several other linux distros including Kubuntu, but the sound didn't work through that card either, so as far as I can tell, something messed up the card physically. But there's no telling.

---

### Post by flakeparadigm on 2008-06-06
After all that trouble I ended up using a different sound card but now I'm running on a totally new system so everything is ok now.

---

### Post by wandalalakers on 2008-06-08
This didn't work for me.  I had sound in kubuntu 7.10 but don't have sound with kubuntu 8.04.

> **{BzF}~JOKesTER said:**
> In The Terminal Type:

apt-get remove alsa-base --purge

And

apt-get remove alsa-oss --purge

now type

apt-get install alsa-base

And

apt-get install alsa-oss

Now Restart You Computer...

Hope This Helps:)

---

### Post by xeth_delta on 2008-06-08
> **pcdoctor said:**
> This didn't work for me.  I had sound in kubuntu 7.10 but don't have sound with kubuntu 8.04.

Have you tried the method suggested in post #16?

---

### Post by wandalalakers on 2008-06-12
I'll try this when I get home.  Thx.

---

### Post by wandalalakers on 2008-06-13
This is what I'm going to try:

Follow from post #16 in this thread.
Follow from post #18 in this thread.
[http://ubuntuforums.org/showthread.php?t=672290](http://ubuntuforums.org/showthread.php?t=672290), post #18

I got an error at this part:
./configure --with cards=hda-intel --with-oss=yes --with-sequencer=yes
configure: error: unrecognized option: --with
I modified the line and just did a ./configure instead of a ./configure --with cards=hda-intel --with-oss=yes --with-sequencer=yes

---

### Post by wandalalakers on 2008-06-13
xeth_delta

[SIZE="7"][COLOR="Red"]XOXOXO[/COLOR][/SIZE]
You've made me a very happy girl!
I have sound now.
I have these instructions in an email account for future reference
On another note, I was using wine with kubuntu 7.10 but I want to try qemu with 8.04 so I can get my Macromedia apps working.

---

### Post by xeth_delta on 2008-06-13
pcdoctor, you are most welcome! I'm glad I could help!

The instructions you used can be used also whenever you update the kernel and don't have sound working, or if simply you want to recompile a new alsa version.

On the Macromedia applications note, You could always use VirtualBox running Windows inside. From there you can run the applications you need. I believe it is also possible to actually have the windows nicely integrated seamlessly into the Linux desktop.

Have you considered giving Quanta Plus a try to write html code?

---

### Post by wandalalakers on 2008-06-13
I've never heard of Quanta Plus but I'll look into it if I get some web design work.  Thx.  I wish someone would come out with open source software to compete with flash.

---

### Post by xeth_delta on 2008-06-14
> **pcdoctor said:**
> I've never heard of Quanta Plus but I'll look into it if I get some web design work.  Thx.  I wish someone would come out with open source software to compete with flash.

Have a look at the following two projects: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/) and [http://www.asual.com/enlarge/](http://www.asual.com/enlarge/)

You can always look for more open source software in the repositories and in [www.sourceforge.net](www.sourceforge.net)

---

