---
title: "No sound in Ubuntu 10.04"
date: 2010-07-26
forum: Multimedia Software
---

### Post by anup.techonly on 2010-07-26
Using Ubuntu 10.04 (64-bit) on a Core-2-Duo machine and having difficulty with sound. There is no sound.. done some search with google but of no avail till now. Below, I am giving some common questions people ask to troubleshoot.

aplay -l gives
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


alsamixer output is attached..

sound preferences look ok to me...

lspci -v gives
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Device 2009
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e0220000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

You are welcome to ask for any new information about my machine and other settings.

Thanks in advance...

---

### Post by anup.techonly on 2010-07-26
any help from anyone, still stuck with it....

---

### Post by lidex on 2010-07-26
Do you have volume icon in your panel? Should be a little speaker. Click on that to make sure it's not muted. You can also access sound preferences from there. On the hardware tab, make sure the correct device is selected and try choosing a different profile for it below. No help? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by anup.techonly on 2010-07-27
Thanks for replying..

```
anup@anup-desktop:~$ uname -a
Linux anup-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```


```
anup@anup-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```



```
anup@anup-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-21-generic    2.6.32-21.201005040600                          Ubuntu-supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.
```


```
anup@anup-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: SigmaTel STAC9227
```




Please help.....

---

### Post by lidex on 2010-07-27
Please also include the make/model of your PC/Laptop.

---

### Post by anup.techonly on 2010-07-27
Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz, (GenuineIntel) desktop machine...

---

### Post by sundays211 on 2010-07-27
not much help, but I have exactly the same problem. the sound was working perfactly fine in an earlier version of ubuntu (5.04 i think), then it hasn't worked on 10.04. VIA built-in audio I think.

---

### Post by lidex on 2010-07-27
> **anup.techonly said:**
> Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz, (GenuineIntel) desktop machine...
Did you assemble it yourself? If not is it a dell, hp, etc? And the model number. If so, what motherboard maker?

---

### Post by lidex on 2010-07-27
> **sundays211 said:**
> not much help, but I have exactly the same problem. the sound was working perfactly fine in an earlier version of ubuntu (5.04 i think), then it hasn't worked on 10.04. VIA built-in audio I think.

That's a heck of an upgrade 5.04 -> 10.04 ;)

---

### Post by anup.techonly on 2010-07-27
Can you please suggest a command by which I can find the Motherboard specification. I ran lspci, cat /proc/cpuinfo, but they don't provide the details...

thanks

---

### Post by sundays211 on 2010-07-27
yup, had an old 5.04 disk lying around and decided to install it, upgraded all the way to 10.04. had so many problems, i decided to re-install

If you want you're motherboard specs, you could always try opening up your pc and looking at the lable on the motherboard.

---

### Post by Yellow Pasque on 2010-07-27
> **anup.techonly said:**
> Can you please suggest a command by which I can find the Motherboard specification. I ran lspci, cat /proc/cpuinfo, but they don't provide the details...

thanks
dmidecode..

---

### Post by anup.techonly on 2010-07-27
Running dmidecode gives the following... I mention only the relevant information...


```
BIOS Information
    Vendor: Intel Corp.
    Version: CO96510J.86A.5882.2007.0413.0100
    Release Date: 04/13/2007
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 0.0
    Firmware Revision: 0.0

Handle 0x0006, DMI type 1, 27 bytes
System Information
    Manufacturer:                                 
    Product Name:                                 
    Version:                         
    Serial Number:                                 
    UUID: 508EB8EE-52C1-11DC-9129-00E018BFD7DC
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family: Not Specified

Handle 0x0007, DMI type 2, 20 bytes
Base Board Information
    Manufacturer: Intel Corporation
    Product Name: DQ965GF
    Version: AAD41019-600
    Serial Number: BQGF7340049V
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0008
    Type: Unknown

```

Please help how can I make sound work in my system...

---

### Post by lidex on 2010-07-27
Intel 965 series looks like. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Right after the = (no space) in the options line, you'll want to add a model name. Try these, one-at-a-time, rebooting each time:
```

  3stack	
  5stack	
  5stack-no-fp
```

---

### Post by anup.techonly on 2010-07-27
I did not understand the part with select correct sound card with alsamixer. Other than that, I made the necessary changes in alsa-base.conf, ad rebooted.. but there is no sound...

---

### Post by anup.techonly on 2010-07-27
Still no sound...

I searched net...found some people say to follow these

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio

these things went fine, then when I did 

sudo alsa force-reload

```
anup@anup-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
Terminating processes: 2272lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
 2409lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
 2422lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
 2435lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2435lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2458(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/anup/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2458(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.




```

please help...

---

### Post by hudsonl on 2010-07-27
I had the same problem after the upgrade to 10.04 from 9.10.

It DID work for quite a while ... and just noticed it stopped working after one of the recent updates.

Tried numerous things ... but I kept noticing that when I would reboot or log off, I would get a message that a program was still running and did I want to reboot anyway, cancel, etc. type of message.  (it was pulse-audio).

So I assumed there was some conflicts with pulse and alsa ...  nothing to lose, so **I removed the PulseAudio Sound Server and rebooted and it works now.**

Go into Synaptic Package Manager ...
  Select "**pulseaudio**"  (PulseAudio sound server)  - **Mark for Complete Removal**
     - Select OK for all the dependencies
     - Select Apply

  - Reboot after removal is completed.

If it doesn't work ... re-install using  Synaptic Package Manager

One thing that I did (saw on the forums) that help sound work consistently for me on 9.10 was disabling the sound on the BIOS.  If you have a sound card and integrated sound on your motherboard ... multiple "cards" seemed to make it "flaky"

Good luck.

---

