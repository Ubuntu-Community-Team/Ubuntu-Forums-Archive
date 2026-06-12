---
title: "No sound ANYWHERE Linux Mint 10"
date: 2011-02-02
forum: Multimedia Software
---

### Post by Hip-Hopapotamus on 2011-02-02
I successfully installed Linux Mint 10 but there is no sound whatsoever from any application. I tried adjusting the volume sliders with no luck.

Dummy audio output was the only option for audio in my sound panel.

I tried installing alsamixer and now Simultaneous output is the only option, with no change in performance.

When I shut down, a command screen appears for a split second before the Mint log off screen. There is a command that says " pulseaudio configured for per user sessions". I'm not sure if this is the root of the problem, or how to reconfigure.

Any advice at all would be appreciated. If I've left out any important information, please excuse me, as I am new to Linux.



lspci shows this:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by lidex on 2011-02-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Hip-Hopapotamus on 2011-02-03
[http://www.alsa-project.org/db/?f=c704ad9afd7c94f9bd5abb3e5ed69ae50b25d285](http://www.alsa-project.org/db/?f=c704ad9afd7c94f9bd5abb3e5ed69ae50b25d285)

Also, lspci -v shows:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 13f3
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d5400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

---

### Post by lidex on 2011-02-03
Wow, not surprised, your alsa install is borked. Try a re-install. ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**
You may need to install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by Hip-Hopapotamus on 2011-02-04
I entered both commands. The first one went smoothly, but when I tried to install aptitutde it said I already had the newest version. I also re-installed pulseaudio, but the result is the same.

---

### Post by lidex on 2011-02-04
What is your aplay result now:
```
aplay -l
```

---

### Post by hutch1 on 2011-02-04
I don't mean to hijack this thread but I'm having the same problem. I've literally been online all day trying to get sound on my laptop. 
_[http://www.alsa-project.org/db/?f=cf24484397355819a9df095979d807b305ee814b](http://www.alsa-project.org/db/?f=cf24484397355819a9df095979d807b305ee814b)_[]("http://www.alsa-project.org/db/?f=43739d6c5d4172bac38865c6176e2d6184dbe35d")

---

### Post by lidex on 2011-02-04
> **hutch1 said:**
> I don't mean to hijack this thread but I'm having the same problem. I've literally been online all day trying to get sound on my laptop. 

[http://www.alsa-project.org/db/?f=43739d6c5d4172bac38865c6176e2d6184dbe35d](http://www.alsa-project.org/db/?f=43739d6c5d4172bac38865c6176e2d6184dbe35d)
Try adding a model quirk to alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-6ch-dig 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Try these if no joy:
```
options snd-hda-intel model=3stack-6ch
options snd-hda-intel model=lenovo-101e

```
One at a time please.

---

### Post by hutch1 on 2011-02-04
Thank you so much lidex! 

Worked on the first try! :popcorn:

---

### Post by Hip-Hopapotamus on 2011-02-05
aplay: device_list:235: no soundcards found...

---

### Post by Hip-Hopapotamus on 2011-02-07
Any new thoughts?

---

### Post by Hip-Hopapotamus on 2011-02-08
I followed the instructions in the 'Comprehensive Sound' thread with no success. I think I've been wasting my time since my driver is not listed on the alsa website. 

If anyone can help me figure out why my soundcard is recognized but not working I would seriously appreciate it. Otherwise I feel like I've exhausted my search for a solution.

---

### Post by tjones00 on 2011-02-08
I know this is a longshot but have you checked user groups and ensured that your user is part of the audio group? I'm not on an ubuntu 10.10 system right now so I can't tell you what all the required groups are. I believe pulseaudio is also a group under the name pulse.

If it is a groups error a simple indicator would be.

```
aplay -l
```

won't work but

```
sudo aplay -l
``` 

will work since the root user should be part of all the groups on the system.

To check the groups your user belongs to do the following:

```
groups yourusername
```

To add a user to a group eg. audio

```
sudo usermod -a -G audio yourusername
```

You can add multiple groups at once with the following format.

```
sudo usermod -a -G group1,group2,group3 yourusername
```

---

### Post by Hip-Hopapotamus on 2011-02-08
Thanks for the reply, yea both aplay -l and sudo aplay -l tell me "no soundcards found". 

I did add my username to the audio group earlier in this trial and error process, and the groups username command does indeed list audio as one of the groups.

---

### Post by gordintoronto on 2011-02-08
> **Hip-Hopapotamus said:**
> Any new thoughts?

Have you ever installed system updates? For example, your kernel is three versions out-of-date. You have 35-22, I'm running 35-25.

---

### Post by Hip-Hopapotamus on 2011-02-08
> **gordintoronto said:**
> Have you ever installed system updates? For example, your kernel is three versions out-of-date. You have 35-22, I'm running 35-25.

Yea I update my system whenever it shows updates are available. How can I go about updating the kernel?

---

### Post by gordintoronto on 2011-02-09
Kernel updates arrive along with all the other updates. If you have been applying updates, perhaps this will bring you up to date. Open Accessories/Terminal and enter the command:
sudo update-grub

Then you have to reboot for it to take effect.

---

### Post by Hip-Hopapotamus on 2011-02-09
> **gordintoronto said:**
> Kernel updates arrive along with all the other updates. If you have been applying updates, perhaps this will bring you up to date. Open Accessories/Terminal and enter the command:
sudo update-grub

Then you have to reboot for it to take effect.

I entered sudo update-grub, did not receive any error messages. 

I rebooted my computer. But it still shows 2.6.35-22

 [http://www.alsa-project.org/db/?f=1de7de5b4702ed2d8f56842f620ffd680de4c7ed](http://www.alsa-project.org/db/?f=1de7de5b4702ed2d8f56842f620ffd680de4c7ed)

---

### Post by Perfect Storm on 2011-02-10
Thread closed. Please use the mint forum, thanks.

---

