---
title: "NO sound , NO device , Dummy output stereo"
date: 2010-05-06
forum: Multimedia Software
---

### Post by amanjjain on 2010-05-06
Hey, 
I have updated my Ubuntu to Lucid 10.04 from 9.10.

Although my sound disappeared in 9.10 only, I thought maybe upgrading might help, but there is no change.

I guess everything is installed fine. 
But still 
aplay -l command shows "NO sound cards.. "
Moreover the sound preferences shows no hardware, no input and a dummy stereo output.

I have banged my head a lot trying various things written in forums and all but no success.
Can please somebody help me, it would be very thankful.

One more thing : When I test "osstest" , I get sound in both the earphones , but altogether there is no sound. I am very much confused.

Early reply is highly appreciable.

Regards,
Aman

---

### Post by xzero1 on 2010-05-06
Start by using the sticky topic(s) in this sub forum.
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by amanjjain on 2010-05-06
Hey,
I went through the link given on the page 
i.e. "http://www.alsa-project.org/alsa-doc/"
it says there you will find your sound card ( chipset ) manufacturer in "drop down" box.

I couldn't find any drop down box over there .. so couldn't proceed forward.

any suggestions??

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Try working through this page as some of it will apply and karmic is where your issues began:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Next do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by morph_89 on 2010-05-06
i think i know what your problem is... u installed oss v4, after that the sound preferences, that i think they are an alsa component, dont detect ur sound card... it happened to me when i install it for the first time, u have to configure some programs to be able to make sound threw oss, but first try to write in the terminal: sudo soundon
 
or...
sudo alsa unload
sudo soundon
 
if that is so run ossxmix (u will only be able to run it if u installed oss...)and u will be able to control the volume from there; i think that ur sound card should be under /dev/dsp now
 
the problem that u are not getting sound is that u have now installed pulseaudio, alsa and oss drivers at the same time, try running vlc and in preferences audio select oss as output to see if u got sound there.

pd: you can also try to put oss off and reloading alsa as well by :

soundoff
alsa unload
alsa reload

---

### Post by Goatrancer on 2010-05-08
I did a fresh instal 0f 10.4 and am also having the dummy output issue. 
Unfortunately I cant use the instuctions in the sticky because I cant find the dropdown.
I am using netbook remix  on an acer AspireOne 1410 btw

here are the outputs of the that lidex requested

```
uname -a
2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21
```

```
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#1 <==
Codec: Intel G45 DEVCTG

```



Regarding Morph's suggestions:
sudo alsa unload gave this:
```
sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1738(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).

```

sudo soundon gave:
```
sudo soundon
sudo: soundon: command not found

```

sudo soundoff:
```
sudo soundoff
sudo: soundoff: command not found

```


And I had just gotten everything working in Karmic when an update screwed everything up and I just decided to do a clean reinstall :(

---

### Post by Goatrancer on 2010-05-08
OK update.. I checked to see if I even had oss isnstalled in synaptic, turns out I didnt, so I installed it and restarted. now the output of aplay -l is:
```
aplay -l
aplay: device_list:223: no soundcards found...

```

removing oss resotres finding the devices listed in my above post. Do I need oss for audio to work properly?

---

### Post by lidex on 2010-05-08
> **Goatrancer said:**
> OK update.. I checked to see if I even had oss isnstalled in synaptic, turns out I didnt, so I installed it and restarted. now the output of aplay -l is:
```
aplay -l
aplay: device_list:223: no soundcards found...

```

removing oss resotres finding the devices listed in my above post. Do I need oss for audio to work properly?

No. Only if you can't get pulse/alsa working properly.

---

### Post by Goatrancer on 2010-05-08
> **lidex said:**
> No. Only if you can't get pulse/alsa working properly.

OK thanks.. so do the outputs I pasted into my first post in this thread give you any clues as to what might be wrong? 


Is it not possible to use pulseaudio and alsa at the same time? Most of the advice I see on the forums involves asla but googling about pulseaudio gives me the impression that it is what newer versions of ubuntu use for sound.

I suspect that this error might be important:
```
sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1738(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
```

I tried killing the process that is supposedly using pulseaudio and then unloading alsa, but every time I do a new process using pulseaudio stops me.
```
james@james-laptop:~$ sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3445(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
james@james-laptop:~$ kill 3445
james@james-laptop:~$ sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3482(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
james@james-laptop:~$ kill 3482
james@james-laptop:~$ sudo alsa unload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/james/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3519(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).

```

---

### Post by lidex on 2010-05-08
Alsa is your base sound system, pulse is the audio server that sits on top of it, so they work together. What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by Goatrancer on 2010-05-08
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  james      3519 F.... pulseaudio

```

---

### Post by lidex on 2010-05-08
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by Goatrancer on 2010-05-08
Yes! That did it!! 
Thanks for the help!!

---

### Post by Hnilica3 on 2010-05-16
I have an Asus N10J, recently started having the same issue.

Tried replacing the line with 
options snd-hda-intel model=asus
did not help. 

After trying a few things, the sound icon no longer shows up. Can't remember everything I have attempted to get my sound working again.

Any help you can give me would be greatly appreciated.



this is code I have entered that was requested previously in this thread.

ran : uname -a
```

Linux stephen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

ran : aplay -l
```

aplay: device_list:223: no soundcards found...

```

ran : cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

```

ran : head -n 1 /proc/asound/card*/codec#*
```

head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

```
stephen@stephen:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.

```

Once again, I appreciate any assistance you can give to me.

---

### Post by lidex on 2010-05-16
Hnilica3,
Remove any custom entries from alsa-base.conf. Run this command:
```
sudo apt-get install --reinstall ubuntu-desktop
```
Reboot.
Now what does aplay -l say?

---

### Post by Hnilica3 on 2010-05-16
ran : aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Got my sound back :)
Icon still doesn't show up.

woot, after this all i got left is fixing my graphics driver, and figuring out how to remove a panel I accidental created.**Update: Fixed both those issues**

Thanks so much mate, and if you know how to get the icon back that would be greatly appreciated.

---

### Post by lidex on 2010-05-16
Right-click on panel, select 'Add to Panel>Indicator Applet'

---

### Post by Hnilica3 on 2010-05-18
brought my battery, chat and bluetooth back, but not my wireless.

---

### Post by lidex on 2010-05-18
> **Hnilica3 said:**
> brought my battery, chat and bluetooth back, but not my wireless.

Network Monitor?

---

### Post by Hnilica3 on 2010-05-18
yes, the network monitor icon does not appear. (my sound icon doesn't as well, but it is not a big deal because I have controls for it on my keyboard)

---

### Post by narcisgarcia on 2010-06-28
I lost the sound output when I was working with Ubuntu 9.10 (the volume applet showed "Dummy Output"), and I thought upgrading to Ubuntu 10.04 might help, but today I've done the upgrade and no instant result about audio matter.

Running aplay -l in a terminal this is my result:
> **** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And then I've clicked on the volume indicator, selected Sound Preferences, and gone to the Hardware tab. Where I see "Internal audio" in the devices list, I've selected the first "Internal audio" and choosen "Analog Stereo Output" in the dropdown, and then I've choosen the second "Internal audio" and choosen "Analog Stereo Input".

Since this moment the volume applet indicates the output level, and all the programs reproduce audio again.

---

### Post by mmort on 2010-09-19
I installed Ubuntu 10.04 on a new Dell Inspiron N4010 laptop. From the beginning, my output sound worked perfectly, as did my built-in webcam. However, input sound did not work. I made a few changes and eventually got the built-in mic working as well. I used it with Skype. Now, after installing a number of recommended and security updates, neither the input nor the output sound is working. The icon shows no volume, although the sound preferences show full unmuted volume. The strangest part is that, when trying to Skype with friends this morning, they could hear the music that should have been playing on my computer! What is going on??

Here are the results of the requested tests:

michelle@michelle-laptop:~$ uname -a
Linux michelle-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
michelle@michelle-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
michelle@michelle-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep  3 2010 for kernel 2.6.32-24-generic (SMP).
michelle@michelle-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

---

### Post by lidex on 2010-09-19
> **mmort said:**
> I installed Ubuntu 10.04 on a new Dell Inspiron N4010 laptop. From the beginning, my output sound worked perfectly, as did my built-in webcam. However, input sound did not work. I made a few changes and eventually got the built-in mic working as well. I used it with Skype. Now, after installing a number of recommended and security updates, neither the input nor the output sound is working. The icon shows no volume, although the sound preferences show full unmuted volume. The strangest part is that, when trying to Skype with friends this morning, they could hear the music that should have been playing on my computer! What is going on??

Here are the results of the requested tests:

michelle@michelle-laptop:~$ uname -a
Linux michelle-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
michelle@michelle-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
michelle@michelle-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep  3 2010 for kernel 2.6.32-24-generic (SMP).
michelle@michelle-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

Try this. First remove pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by mmort on 2010-09-19
Thanks a lot! I tried the first step, but got the response "no such file or directory."

I search in file system for files containing "asound" or "pulseaudio" and got many results. I'm not sure which ones to delete. (In particular, there are two asound.conf files, _jack and _oss.) There are pulseaudio files in a number of folders, including /etc, /usr, and /var/lib. The first two also contain asound files.

---

### Post by lidex on 2010-09-19
> **mmort said:**
> Thanks a lot! I tried the first step, but got the response "no such file or directory."

I search in file system for files containing "asound" or "pulseaudio" and got many results. I'm not sure which ones to delete. (In particular, there are two asound.conf files, _jack and _oss.) There are pulseaudio files in a number of folders, including /etc, /usr, and /var/lib. The first two also contain asound files.

No, don't remove anything else. That first command did the necessary removal. "no such file or directory." means you don't have those files - and most don't. Did you re-install alsa?

---

### Post by mmort on 2010-09-20
> **lidex said:**
> No, don't remove anything else. That first command did the necessary removal. "no such file or directory." means you don't have those files - and most don't. Did you re-install alsa?

I just did, and nothing changed. There is still no sound, no input listed, and only dummy stereo output. :(

---

### Post by narcisgarcia on 2010-09-21
mmort, could you copy and show the result of:
```
lspci
```
in a terminal?

---

### Post by mmort on 2010-09-21
> **narcisgarcia said:**
> mmort, could you copy and show the result of:
```
lspci
```in a terminal?

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by lidex on 2010-09-21
> **mmort said:**
> I just did, and nothing changed. There is still no sound, no input listed, and only dummy stereo output. :(
You rebooted, correct?
Try removing pulse-cookie:
```
rm -r ~/.pulse-cookie
```

---

### Post by narcisgarcia on 2010-09-22
Are you hearing sound if you boot from Live-CD (Ubuntu 10.04) ?

---

### Post by mmort on 2010-09-22
Removing pulse-cookie did not do anything. When I boot from the CD, the sound does work. It only stopped working a couple days ago...must have been one of the updates.

---

### Post by narcisgarcia on 2010-09-23
To verify the updates cause, you can make a Live-USB with the usb-creator tool (selecting to store documments and settings in extra space).
Then boot the Live-USB and apply updates.

---

### Post by lkjoel on 2010-09-24
> **amanjjain said:**
> Hey, 
I have updated my Ubuntu to Lucid 10.04 from 9.10.

Although my sound disappeared in 9.10 only, I thought maybe upgrading might help, but there is no change.

I guess everything is installed fine. 
But still 
aplay -l command shows "NO sound cards.. "
Moreover the sound preferences shows no hardware, no input and a dummy stereo output.

I have banged my head a lot trying various things written in forums and all but no success.
Can please somebody help me, it would be very thankful.

One more thing : When I test "osstest" , I get sound in both the earphones , but altogether there is no sound. I am very much confused.

Early reply is highly appreciable.

Regards,
Aman
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.
That will update OSS, and it will make your sound work.

---

### Post by zmanian on 2010-10-24
I'm having a similar problem in my Dell R14(N4010) running Maverick(10.10).

Any updates on this issue?

---

### Post by lidex on 2010-10-25
> **zmanian said:**
> I'm having a similar problem in my Dell R14(N4010) running Maverick(10.10).

Any updates on this issue?

Is this an upgrade? Try removing old audio config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by awechris on 2010-11-02
i had this exact problem, with "NO SOUNDCARD" found etc. I tried virtualy everything... recompiling alsa , reinstalling alsa etc. What recovered my sound was a newer kernel (daily build). As of today, it's 2 days old kernel build. However, ubuntu daily build kernel was taken from [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-31-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-31-maverick/)

i don't reply much in forums, but in this case this problem took me several days to find solution, so i thought of sharing to save some other people's time.

---

### Post by sloopjohnbutler on 2010-11-06
Lidex,
 
A big "Thank You" to you for getting me out of a hole when I was away in Dallas, upgraded Ubuntu and got this issue (right in the middle of a load of video travel presentations)
 
If I did shutdown, (which I could only do using sudo shutdown -h now) then I had to run this lot from the terminal every time afterwards.
 
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
 
sudo apt-get update
sudo apt-get upgrade
 
sudo apt-get purge linux-sound-base alsa-base alsa-utils
 
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
 
**Reboot.**
 
That was all very well, but I was stuffed if wi-fi internet wasn't available at the location.
 
After much experimentation, and lots of lost sleep in an unfamiliar time zone, my only way to have sound available for my video travel presentations was never to shutdown my netbook, as the only way to preserve the sound capability was to hibernate it every time. 
 
 
When I got home, my son Chris (a part-time Debian developer) finally sussed out that it would be best if he removed pulseaudio, re-installed alsamixer and added my username to the audio group. Here are the commands he used .......
 
# remove pulseaudio
sudo apt-get remove pulseaudio
 
# add your user to the "audio" group to allow direct access to the sound device
sudo adduser jbutler audio
 
where "jbutler" is my username on the netbook
 
If that helps anyone, my trials and tribulations will have been worth it. I'm off to Cyprus this week, so it will make it so much easier if Ubuntu & VLC retains full capability this time.
 
John

---

### Post by necrosymbiont on 2010-12-15
I got this problem when I installed the "randomsound" package (for harvesting entropy from the sound card). Uninstalling "randomsound" and restarting the computer was a quick and easy fix.

---

### Post by xubuntu84 on 2010-12-27
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Try working through this page as some of it will apply and karmic is where your issues began:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Next do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

I've done these things, hope any of you will be able to assist.  I have an Intel DP55KG with built-in optical audio out... so far I have purged alsa and pulse, reinstalled, and verified nothing is muted.  Can't figure out what is going on:

```
benmctee@ubuntu-server:~$ uname -a
Linux ubuntu-server 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

```
benmctee@ubuntu-server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
benmctee@ubuntu-server:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

```
benmctee@ubuntu-server:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC889

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GPU 11 HDMI/DP

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GPU 11 HDMI/DP

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GPU 11 HDMI/DP

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GPU 11 HDMI/DP
```

Make/Model: Integrated optical audio in/out on an Intel DP55KG motherboard.

When I run: 
```
alsamixer -Dhw
```
I am able to set all volumes except the SPDIF (which I believe IS the optical audio)... just something I thought was strange, and possibly a pointer to the problem.

---

### Post by sites on 2011-03-23
Just thought I'd tag along with this thread instead of starting a new one.

I created a guest account for others to use & when it's logged on there's no sound.  The device output is listed as "dummy output stereo".  "Internal Audio" is not listed as a device.  Everything works fine in my admin account & I made sure the guest account has access to sound devices.

Anyone seen this before?

---

### Post by lidex on 2011-03-24
> **sites said:**
> Just thought I'd tag along with this thread instead of starting a new one.

I created a guest account for others to use & when it's logged on there's no sound.  The device output is listed as "dummy output stereo".  "Internal Audio" is not listed as a device.  Everything works fine in my admin account & I made sure the guest account has access to sound devices.

Anyone seen this before?
Nope, heard of it though.
[http://ubuntuforums.org/showthread.php?p=10597924#post10597924](http://ubuntuforums.org/showthread.php?p=10597924#post10597924)

---

