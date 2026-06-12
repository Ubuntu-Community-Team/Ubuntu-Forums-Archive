---
title: "sound issues"
date: 2010-08-01
forum: Multimedia Software
---

### Post by mossrunner on 2010-08-01
i came back from vacation to find that the sound on my computer isn't working properly.   

 my speakers are working fine and the drivers appear to be installed correctly.  when i play music files everything appears to be working properly except there is no sound.   

 i've been muting and un-muting everything i can think of, tweaking alsamixer, gnome-volume-control and working through every tutorial i can find, including the comprehensive sound solutions guide on this website.  i also booted up the live CD to attempt a reinstall, however the same no-sound issue appears there. 

 any and all ideas are greatly appreciated. 

   $ uname -r
2.6.32-24-generic

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).


$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 

$ grep 'audio' /etc/group 
audio:x:29:matt,pulse 

$ cat /proc/asound/card*/codec#* | grep Codec 
Codec: Realtek ALC888 
Codec: ATI RS690/780 HDMI

---

### Post by lidex on 2010-08-01
Interesting, but I don't think sound just magically disappeared. More likely something changed that required a reboot to take effect and on your return is now evident. Think what you did prior to shutting it down. System upgrade, new kernel? I see you have an alsa upgrade from the 6th, why did you need that? Previous sound problems? Any bios changes? If a dual-boot, did you install chipset/audio driver updates in windows?

Try toggling the profile in sound preferences and make sure the correct device is selected as well as the correct connector on output tab.

More info is always a good thing. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by mossrunner on 2010-08-01
I did authorize a pile of upgrades through the ubuntu automatic update utility, but i didn't really pay attention to what was being upgraded.  I was under the impression that those upgrades are for routine stuff and didn't think they required much consideration.

As for the alsa upgrade, that was one of my failed attempts at fixing the issue this morning.  

Here is the link to the Alsa info script (very cool, btw) 
[http://www.alsa-project.org/db/?f=3bc915bb4fe9e46d8682aa05060bf95a8a998f61](http://www.alsa-project.org/db/?f=3bc915bb4fe9e46d8682aa05060bf95a8a998f61)

I have been toggling my audio device, but I don't know for certain which device and/or setting to use.

   Thanks for the help.  

matt

---

### Post by lidex on 2010-08-01
OK. If you have alsa backports installed, remove them.
Update your system:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**
Now follow the alsa-upgrade link in my sig and use the script there. When that completes with no errors and after rebooting, rerun the info script. We want to see all of these at v 1.0.23:
```
!!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22

```

Before you do any of that, please post these outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by mossrunner on 2010-08-01
the initial dmidecode bios and baseboard outputs are below.  

 I removed the installed alsa backports, and performed the updates and upgrades you recomended, followed by running the alsa-upgrade script.  I now have the alsa driver, library and utilities at version 1.0.23, but still don't have sound.  

I am confused as to how to configure my sound card with gnome-volume-control.  I have a choice between a Digital Sterio HDMI output (RS780 Azalia controller) and the internal output which has 16 different setting options including analog sterio output and Digital sterio.

 here is the alsa-info script output after following the procedure you described.
[http://www.alsa-project.org/db/?f=d43717bcd32e02528a7444f081be771a30ac3c4b](http://www.alsa-project.org/db/?f=d43717bcd32e02528a7444f081be771a30ac3c4b) 

Thanks again and please let me know if you have any more ideas. 

=============================

  Before you do any of that, please post these outputs:
```

$ sudo dmidecode -t bios 
# dmidecode 2.9 
SMBIOS 2.5 present. 

Handle 0x0000, DMI type 0, 24 bytes 
BIOS Information 
    Vendor: American Megatrends Inc. 
    Version: 080014  
    Release Date: 06/24/2008 
    Address: 0xF0000 
    Runtime Size: 64 kB 
    ROM Size: 1024 kB 
    Characteristics: 
        ISA is supported 
        PCI is supported 
        PNP is supported 
        APM is supported 
        BIOS is upgradeable 
        BIOS shadowing is allowed 
        ESCD support is available 
        Boot from CD is supported 
        Selectable boot is supported 
        BIOS ROM is socketed 
        EDD is supported 
        5.25&quot;/1.2 MB floppy services are supported (int 13h) 
        3.5&quot;/720 KB floppy services are supported (int 13h) 
        3.5&quot;/2.88 MB floppy services are supported (int 13h) 
        Print screen service is supported (int 5h) 
        8042 keyboard services are supported (int 9h) 
        Serial services are supported (int 14h) 
        Printer services are supported (int 17h) 
        CGA/mono video services are supported (int 10h) 
        ACPI is supported 
        USB legacy is supported 
        LS-120 boot is supported 
        ATAPI Zip drive boot is supported 
        BIOS boot specification is supported 
        Targeted content distribution is supported 
    BIOS Revision: 8.14 

Handle 0x0035, DMI type 13, 22 bytes 
BIOS Language Information 
    Installable Languages: 1 
        en|US|iso8859-1 
    Currently Installed Language: en|US|iso8859-1 




$ sudo dmidecode -t baseboard 
# dmidecode 2.9 
SMBIOS 2.5 present. 

Handle 0x0002, DMI type 2, 15 bytes 
Base Board Information 
    Manufacturer: FOXCONN 
    Product Name: A7GM-S 
    Version: 1.0 
    Serial Number:    
    Asset Tag: To Be Filled By O.E.M. 
    Features: 
        Board is a hosting board 
        Board is replaceable 
    Location In Chassis: To Be Filled By O.E.M. 
    Chassis Handle: 0x0003 
    Type: Motherboard 
    Contained Object Handles: 0 

Handle 0x0033, DMI type 10, 6 bytes 
On Board Device Information 
    Type: Video 
    Status: Enabled 
    Description:   To Be Filled By O.E.M. 

Handle 0x0034, DMI type 10, 6 bytes 
On Board Device Information 
    Type: SCSI Controller 
    Status: Disabled 
    Description:  To Be Filled By O.E.M. 

```[/QUOTE]

---

### Post by mossrunner on 2010-08-02
still no luck with this issue.  with my monitor speakers at 50% volume i get some white noise that i can eliminate by muting the 'Front' setting in alsamixer, and totem appears to be playing an mp3 file without difficulty, however i still have no luck getting the music from my computer to my speakers.  any ideas?

---

### Post by lidex on 2010-08-02
You mentioned some confusion with profiles. Try using analog stereo out or duplex, not the digital options. Remove the asound.conf file:
```
!!ALSA configuration files
!!------------------------
!!System wide config file (/etc/asound.conf)
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```
Reset pulse config:
```
rm -r ~/.pulse 
```

Now this. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Lawrence Talbot on 2010-08-02
You might open up the Pulse Audio Volume Control application and see if everything is set up the way it should be.

---

### Post by mossrunner on 2010-08-02
thanks for the suggestion, i've been tweaking the pulse audio settings as well.  

 i just reinstalled my root partition, figuring that might reset whatever i did wrong in the first place but that doesn't seem to be working either.  

is it possible that my integrated sound card is broken?  or is it more likely that some arcane setting is awry?  i've had this motherboard for almost two years now and i wouldn't mind having an excuse to upgrade.

---

### Post by mossrunner on 2010-08-02
hello lidex, thanks for all your help. 

 i also just made the changes you suggested in your most recent post with no apparent change. 



EDIT: i just realized that i already mentioned this bit below about the white noise.  disregard. 

of curious interest:  when i unmute all the mic inputs i get a white noise coming out of my speakers.  i can silence this by muting the 'Front' output in alsamixer.  is it possible that my computer is sending the music file sound somewhere else?

---

### Post by lidex on 2010-08-02
According to pulse audio website no users should belong to the audio group.
> grep 'audio' /etc/group
audio:x:29:matt,pulse 
Here's mine:
```
grep 'audio' /etc/group
audio:x:29:pulse

```

---

### Post by mossrunner on 2010-08-02
thanks again for all the help.  i finally figured out the settings, and i have no idea how they got tweaked in the first place.

 from gnome-volume-control > hardware tab, I selected the analog stereo output for the internal audio device.  then under the output tab i could select the 'internal audio analog stereo'.  this seemed like one of those riddles that are impossible until you know the embarrassingly simple answer.  

cheers

---

