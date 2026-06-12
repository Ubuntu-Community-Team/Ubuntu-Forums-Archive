---
title: "Just installed Lucid and no surround sound"
date: 2010-07-22
forum: Multimedia Software
---

### Post by Dukenukemx on 2010-07-22
I just installed Lucid X64 on my PhenomX4 machine and I can't get my 5.1 speakers working.  Only works in stereo.  

Sound Preferences have only stereo options, how can I get surround 5.1?  If it helps, I have Realtek for sound.

---

### Post by lidex on 2010-07-23
This should help:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Hmm. Something screwy about that site. If it doesn't come up as it should click the 'start' breadcrumb link, then hardware>Configuring Surround Sound with Pulseaudio

---

### Post by Dukenukemx on 2010-07-23
Thanks, I did that and rebooted but I still only get Stereo.  I tested it with this. 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

I still only hear from left or right.  Just wanted to add that I have the Realtek ALC883 sound chip.

---

### Post by lidex on 2010-07-23
Can you post the output of these terminal commands for me please:
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

### Post by 71GA on 2010-09-08
```
ziga@ziga-PC:~$ uname -a
Linux ziga-PC 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux


ziga@ziga-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ziga@ziga-PC:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA


ziga@ziga-PC:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```Ok so here are the outputs you wanted. I am not the same person but i have a SAME problem :).

---

### Post by lidex on 2010-09-14
> **71GA said:**
> ```
ziga@ziga-PC:~$ uname -a
Linux ziga-PC 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux


ziga@ziga-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ziga@ziga-PC:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA


ziga@ziga-PC:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```Ok so here are the outputs you wanted. I am not the same person but i have a SAME problem :).

First I would update your alsa install following the link in my sig.

---

### Post by Dukenukemx on 2010-10-07
Yes I'm bringing back this thread.  I still haven't solved the problem, but I think I have an idea of what the cause is.

My Radeon 4670 can output sound through HDMI, and it's shown in my sound preferences.  The sound ouput from it is only capable of Stereo, where as my on board Realtek can do 5.1.

So I'm thinking that it's using the ATI video card for sound, and routing it through my on board realtek chipset?  :confused:  No matter where I look, it always shows the ATI HDMI sound, and nothing for the on board realtek.  

I also wanna try installing the realtek HD audio drivers from their website.  They do have audio drivers, but I have no idea how to install them.  

I'm trying the ALSA upgrade now.

**EDIT**
Nope, the upgrade didn't fix it.  The drop down menu doesn't have a 5.1 option for sound.

---

### Post by lidex on 2010-10-07
> **Dukenukemx said:**
> Yes I'm bringing back this thread.  I still haven't solved the problem, but I think I have an idea of what the cause is.

My Radeon 4670 can output sound through HDMI, and it's shown in my sound preferences.  The sound ouput from it is only capable of Stereo, where as my on board Realtek can do 5.1.

So I'm thinking that it's using the ATI video card for sound, and routing it through my on board realtek chipset?  :confused:  No matter where I look, it always shows the ATI HDMI sound, and nothing for the on board realtek.  

I also wanna try installing the realtek HD audio drivers from their website.  They do have audio drivers, but I have no idea how to install them.  

I'm trying the ALSA upgrade now.

**EDIT**
Nope, the upgrade didn't fix it.  The drop down menu doesn't have a 5.1 option for sound.

Need your info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Dukenukemx on 2010-10-08
Ok, here's the link to the report.

[http://www.alsa-project.org/db/?f=58ee2f5be1d54a6dcc90f5bec45aff7da57deea5](http://www.alsa-project.org/db/?f=58ee2f5be1d54a6dcc90f5bec45aff7da57deea5)

---

### Post by lidex on 2010-10-08
> **Dukenukemx said:**
> Ok, here's the link to the report.

[http://www.alsa-project.org/db/?f=58ee2f5be1d54a6dcc90f5bec45aff7da57deea5](http://www.alsa-project.org/db/?f=58ee2f5be1d54a6dcc90f5bec45aff7da57deea5)

Some motherboard info please. 
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Dukenukemx on 2010-10-08
Here's the info.  

```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: ASUS M2A-VM ACPI BIOS Revision 2302
    Release Date: 02/05/2009
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x002D, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        r|CA|iso8859-1
        a|JP|unicode
    Currently Installed Language: n|US|iso8859-1

```

```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M2A-VM
    Version: 1.XX    
    Serial Number: 123456789000

```

---

### Post by lidex on 2010-10-08
Hmm. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=alc883-6stack-dig 
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

---

### Post by Dukenukemx on 2010-10-08
I booted up with no sound, and with alsamixer I get "cannot open mixer: No such file or directory".  

Just an idea, but should I be using something with the word "Intel" in it?  I have an AMD machine.  

Under "System ->Preferences ->Sound", I have nothing listed.  This is after entering "options snd-hda-intel model=alc883-6stack-dig".

---

### Post by lidex on 2010-10-08
> **Dukenukemx said:**
> I booted up with no sound, and with alsamixer I get "cannot open mixer: No such file or directory".  

Just an idea, but should I be using something with the word "Intel" in it?  I have an AMD machine.  

Under "System ->Preferences ->Sound", I have nothing listed.  This is after entering "options snd-hda-intel model=alc883-6stack-dig".

The snd-hda-intel is a generic driver. You should try some of the other models. How many audio jacks on the motherboard, including spdif? Is this a 6 or 8 channel board?

---

### Post by lidex on 2010-10-08
OK, so you have 3 jacks, 6 channel audio. Try these models instead:
```
3stack-6ch
3stack-6ch-dig
```
Only one at a time and reboot to initialize.

---

### Post by Dukenukemx on 2010-10-08
> **lidex said:**
> The snd-hda-intel is a generic driver. You should try some of the other models. How many audio jacks on the motherboard, including spdif? Is this a 6 or 8 channel board?

It has 3 audio jacks, and that's it.  It does 6 channel through it.  

When I entered that into the alsa-base.conf, I didn't just lose sound.  I couldn't restart the machine.  Restart or shutdown would bring me to the login screen.  I had to reset the machine to restart it.  When I removed it, everything was working again.  Besides the 5.1 sound.  

Is there anyway to install the Realtek drivers?  Would it help to use Realteks drivers?

---

### Post by Dukenukemx on 2010-10-08
Ok, I got it working as 5.1.  I did the Alsamixer thing that you said, but with the " options snd-hda-intel model=alc883-6stack-dig" removed.  When I had Alsamixer open, I could see the other channels if I hit the right arrow key.  I raised the volume for them.

Now, when I go to sound preferences, I see 5.1 is now selected.  So 5.1 is certainly working now.

---

### Post by lidex on 2010-10-09
That's great *Dukenukemx*. I was starting to get worried ;)

---

