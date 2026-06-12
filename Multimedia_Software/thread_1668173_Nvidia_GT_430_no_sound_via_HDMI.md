---
title: "Nvidia GT 430 no sound via HDMI"
date: 2011-01-16
forum: Multimedia Software
---

### Post by slimb on 2011-01-16
Hey all,

I've been trying to get my new nvidia GT 430 to push sound via HDMI.  it's pushing video no problem.

aplay -l shows nothing but my onboard soundcard

```
tmyoungjr@alpha:/var/log$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

While lspci -v shows that both exist (the onboard and the NVIDIA as a sound device)

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 836d
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=128M]
        Memory at de000000 (64-bit, prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at d8000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 836d
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

If i'm in alsamixer I see both as options, however I can't do anything with the NVIDIA (i get no controls to modify).  When im in system - preferences - sound my hardware only shows the internal onboard sound.  

The OS knows the NVIDIA exists for sound output but I'm lost as to where to go.  Running 10.10 and running the 260 drivers for the nvidia.  

Any thoughts or direction would be great!

---

### Post by BicyclerBoy on 2011-01-16
[http://www.nvnews.net/vbulletin/showthread.php?t=154755](http://www.nvnews.net/vbulletin/showthread.php?t=154755)

AFAIK Your kernel modules do not recognise the device.

Check the above nvidia post thread, Stephjen Warren explains what is needed for each nvidia device type.

uname -r
shows you your kernel version.

The easiest thing to do is find updated alsa kernel modules or a later kernel.
Hardest thing to do is build the alsa kernel modules.

There is an alsa upgrade script that does everything...

---

### Post by lidex on 2011-01-16
As far as alsa modules, with the patch that enables hdmi sense, this installs with a minimum of fuss. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
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

### Post by slimb on 2011-01-16
> **lidex said:**
> As far as alsa modules, with the patch that enables hdmi sense, this installs with a minimum of fuss. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanks gents, my box now recognizes the card thanks to adding the audio dev PPA and I can use it for output, but I get no sound from it yet.  Close but I have more work and research to do!  Any other suggestions would be great!  I'm going to keep doing more reading!

---

### Post by efflandt on 2011-01-17
Which Ubuntu version are you running (are you really still running 6.06)?

Your sound devices should have shown up in aplay -l in Maverick (but probably not Lucid) if you had most recent kernel updates.  The audio ppa may make your startup sounds not work when you do update your kernel.  Although, sounds should still work after X starts.

Now you just need to unmute the S/PDIF devices for HDA NVidia in alsamixer by pressing m for any that show MM so they end up as 00, figure out which one works, and add a line to a file.  Try the following and substitute 1,3 with 1,7 1,8 or 1,9 until you find which works:

```
aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav
```Mine is 1,9 so I added a line to /etc/pulse/default.pa after alsa-sink line:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Reboot.  The only odd thing it that in the **Output** tab of **Sound Preferences** you will need to select the HDA NVidia device that does NOT say HDMI to get HDMI sound.  The speaker test in Sound Preferences will not work, but if you play Rythmbox, etc. you should be able to switch sound output on the fly.

---

### Post by slimb on 2011-01-17
> **efflandt said:**
> Which Ubuntu version are you running (are you really still running 6.06)?

Your sound devices should have shown up in aplay -l in Maverick (but probably not Lucid) if you had most recent kernel updates.  The audio ppa may make your startup sounds not work when you do update your kernel.  Although, sounds should still work after X starts.

Now you just need to unmute the S/PDIF devices for HDA NVidia in alsamixer by pressing m for any that show MM so they end up as 00, figure out which one works, and add a line to a file.  Try the following and substitute 1,3 with 1,7 1,8 or 1,9 until you find which works:

```
aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav
```Mine is 1,9 so I added a line to /etc/pulse/default.pa after alsa-sink line:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Reboot.  The only odd thing it that in the **Output** tab of **Sound Preferences** you will need to select the HDA NVidia device that does NOT say HDMI to get HDMI sound.  The speaker test in Sound Preferences will not work, but if you play Rythmbox, etc. you should be able to switch sound output on the fly.

Nah running 10.10 - sorry apparently I omitted it from my first post (and hadn't updated my profile in ages!!)

Once I'm home later I'll give that a try.  My device(s) show up properly with aplay -l now (which is much improved).  However in the output tab of sound preferences i only have one device listed for the Nvidia card (the other is the onboard soundcard).

I did go through and unmute all of the lines in alsamixer already.  I'll try that config change suggestion.  Thanks!

---

### Post by slimb on 2011-01-18
Thanks all!!  The last bit of advice was what finished it up.  I get sound now :)

I even get *some* sound in XBMC - but I have further troubleshooting to do there!

Thanks again!

---

### Post by kinmad on 2011-01-28
Thanks guys,

you also sorted out my sound problems perfectly following the instructions.

I'm a Linux newbie, but couldn't get

"
aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav
to work (issue with plughw:1,3) part, but by trial and error updating the default.pa file and finding the right combination, lo and behold sound !

Thanks again from a happy camper

---

### Post by kinmad on 2011-02-02
Hi again,

After loading up all my media, I'm also having trouble with XBMC (Ubuntu 10xx) playing sound on some media.

Did you find a fix for the same issue you mentioned?

Cheers

---

### Post by kinmad on 2011-02-02
All sorted......trial and error time, but got there:p

---

### Post by kinmad on 2011-02-15
Still not 100% :cry:

Is anyone else having the issue where upon start-up the sound sometimes works, sometimes not.

I'd guess it seems to work around 50% of the time.

As I'm trying to auto-boot into XBMC to get WAF approval, obviously this is not ideal!

Cheers in advance for anyone in the same boat who has some suggestions

---

### Post by kaicrr77 on 2011-04-17
> **kinmad said:**
> Still not 100% :cry:

Is anyone else having the issue where upon start-up the sound sometimes works, sometimes not.

I'd guess it seems to work around 50% of the time.

As I'm trying to auto-boot into XBMC to get WAF approval, obviously this is not ideal!

Cheers in advance for anyone in the same boat who has some suggestions

Make sure you do post #3 and #5. Was searching hi and low for a solution and that did the trick. This fix cleans up the distortion AND adds sound over HDMI.

---

### Post by aps_brar on 2011-05-22
I followed post #3 & #5 and got sound over HDMI :), but it is only stereo and not 5.1, any idea how I can get LPCM over HDMI with GT 430

---

### Post by lidex on 2011-05-22
What profile is selected in 'Sound Preferences'?

---

### Post by aps_brar on 2011-05-23
I have disabled my MotherBoard's onboard sound card and now I have only one item under Hardware > Choose a device to configure > Hdmi  (can not remember exact wording as I am not in front of Ubuntu machine)
at the bottom this screen in the profile dropdown there are only 2 option Off and Digital Stereo

HDMI output is going to an ONKYO Reciever (HDMI 1.1) which is connected to Samsung plasma (HDMI 1.3)

---

### Post by lidex on 2011-05-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by alldunn on 2011-09-28
I was able to get sound out of my TV doing the aplay test, but I do not have a /etc/pulse/default.pa file or a /etc/asound.conf.  I created these files manually, but I am still unable to get sound out using any application other than aplay.  This particular box is running Mythbuntu 11.04 with a NVidia GT 430.  I only performed step 5 here in addition to unmuting the spdif channels in alsamixer, as I was able to get sound without doing step 3.

Here is the alsa info script if it helps:
[http://www.alsa-project.org/db/?f=1007ae085091149c22fcfe71c48507040cc02892](http://www.alsa-project.org/db/?f=1007ae085091149c22fcfe71c48507040cc02892)

Ultimately I want to get 5.1 out of this card with Mythtv, but the TV I am testing with only has 2 built-in speakers.  Your suggestions are appreciated.

---

### Post by cacycleworks on 2011-12-09
YESSSHH!! 

Thank you guys so much!! My gal Friday's Win 7 install got a virus so she asked me to put ubuntu on it for her. I've been kinda bitter about how Ubuntu keeps changing everything from one install to the next, so I'm sticking with 10.04 LTS for the time being.

This office computer is a "crappy old Dell" C521 3 GHz Athlon X2 with lots of RAM, a nVidia GT430 video card, and a Gateway 23" HDMI monitor.

I tried my usual trick of ubuntu 10.04 minimal then add stuff, but it wouldn't find and load video drivers. So I got the 10.04.3 Desktop x64 ISO and things started looking up!

> **lidex said:**
> As far as alsa modules, with the patch that enables hdmi sense, this installs with a minimum of fuss. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. **[COLOR="Red"]<M> to mute/unmute.[/COLOR]**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

The bit about pressing M is crucial. You must unmute the 2nd through 4th audio instances.

But still no "sound"...

> **efflandt said:**
> 
Your sound devices should have shown up in **aplay -l** in Maverick (but probably not Lucid) if you had most recent kernel updates.  The audio ppa may make your startup sounds not work when you do update your kernel.  Although, sounds should still work after X starts.

Now you just need to unmute the S/PDIF devices for HDA NVidia in alsamixer by pressing m for any that show MM so they end up as 00, figure out which one works, and add a line to a file.  Try the following and substitute 1,3 with 1,7 1,8 or 1,9 until you find which works:

```
aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav
```Mine is 1,9 so I added a line to /etc/pulse/default.pa after alsa-sink line:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Reboot.  The only odd thing it that in the **Output** tab of **Sound Preferences** you will need to select the HDA NVidia device that does NOT say HDMI to get HDMI sound.  The speaker test in Sound Preferences will not work, but if you play Rythmbox, etc. you should be able to switch sound output on the fly.

I did all this and now it's perfect. 

Thank you guys SO MUCH!! :D
Chris

---

### Post by cacycleworks on 2011-12-11
OH no... I let ubuntu update, which loaded a new kernel... 

As expected, it broke the video and audio, so I ran the NVIDIA driver installer and then came here to repeat these steps:

```

$ sudo apt-get update
...
$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[sudo] password : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-36-generic

```

Would someone please confirm that this is a matter of the alsa driver module making people just needing to keep up with the kernels?? And maybe soon there will be a package for me? I tried booting back to the previous kernel in grub (2.6.32-33-generic), but it totally broke X. :( 

This computer cannot live long without sound... I'll check in again on Monday and if no replies or thoughts added, I'll start a new thread that isn't SOLVED. 

Thanks,
Chris

PS - Lesson? If you can read this, **go into the Update Manager and turn off automatic updates** unless you're ok with booting to low graphics mode and no audio one day.

---

### Post by Philippo.co on 2011-12-20
> **cacycleworks said:**
> OH no... I let ubuntu update, which loaded a new kernel... 

PS - Lesson? If you can read this, **go into the Update Manager and turn off automatic updates** unless you're ok with booting to low graphics mode and no audio one day.

Hi

This topic will help You for nv driver kernel update problems.
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Regards

---

### Post by Cincinnatux on 2012-04-17
[QUOTE=lidex;10363314]As far as alsa modules, with the patch that enables hdmi sense, this installs with a minimum of fuss. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```

Safe to assume that if my NVidia audio via HDMI is currently working, there's nothing to gain by adding this repository and installing the patch?

---

### Post by Cincinnatux on 2012-04-17
> **cacycleworks said:**
> OH no... I let ubuntu update, which loaded a new kernel... 

As expected, it broke the video and audio...

PS - Lesson? If you can read this, **go into the Update Manager and turn off automatic updates** unless you're ok with booting to low graphics mode and no audio one day.

I feel your pain.  Every once in a while, doing the apt-get upgrade command borks some critical bit of my system - most often my HDMI audio - and this drives me crazy.  I went with Ubuntu over other distros because Shuttleworth has insisted that his goal is for everything to 'just work.'  I applaud that goal.  But it is frustrating how far Ubuntu is from achieving it.  Then again, I've been using Ubuntu as my primary computing environment since Feisty Fawn, and I'm still just a barely competent user, so I haven't taken the time to figure out how to be part of the solution.  I believe in open source, but have yet to really put my money where my mouth is, I guess.

---

### Post by BicyclerBoy on 2012-04-17
I not sure all of the posters (here) needed to use the ubuntu-audio-dev ppa. That ppa updates the alsa kernel modules.
Kernels needed for presence detect fix.
- linux 2.6.36-rc1
- linux 2.6.35
- linux 2.6.34.2 or later ...

To check the nVidia HDMI audio issues with kernel versions & diff GPU h/w, see the nVidia HDMI audio readme.
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

It is a given that nVidia proprietary video driver must be installed.

If you have alsa kernel >=1.0.23 (lucid) you should be okay with GT430.
What is required is alsa user-space (libraries) >=1.0.24. This is available for lucid, but not maverick, from iQuik ppa.

The ubuntu audio-dev ppa is not compatible with iQuik.
Could be better to try a backported kernel, note the nVidia video driver needs the matching kernel headers package.

Reading the nVidia HDMI audio doc you see there have been some bug fixes & regressions that affects different h/w.

---

### Post by cacycleworks on 2012-04-18
Thanks for your very informative reply! I just tried out 12.04 LTS Beta on a couple non-nvidia computers and it works perfectly. Then tried it on a legacy nvidia box and got it to eventually work (should have written down the kernel param voodoo). So I might give this one box another go...

---

### Post by zimmort on 2012-04-19
I've had the same problem with GT440, solved it as follows :
 
open a terminal (ctrl-alt-t), do the following sound tests :
 
For GPUs, which are typically ALSA card 1:
 
[COLOR=#000080]speaker-test -c 2 -r 48000 -D hw:1,3[/COLOR]
[COLOR=#000080]speaker-test -c 2 -r 48000 -D hw:1,7[/COLOR]
[COLOR=#000080]speaker-test -c 2 -r 48000 -D hw:1,8[/COLOR]
[COLOR=#000080]speaker-test -c 2 -r 48000 -D hw:1,9[/COLOR]
 
[COLOR=#000080]write down which one works, the bit that you need to use is the last 2 [/COLOR][COLOR=#000080]numbers,[/COLOR][COLOR=#000080]in my case it's hw:1,7.[/COLOR]
 
[COLOR=#000080]now edit the default.pa file, as follows :[/COLOR]
 
[COLOR=#000080]cd /etc/pulse[/COLOR]
 
[COLOR=#000080]sudo chmod 666 default.pa[/COLOR]

[COLOR=#000080]sudo [/COLOR][COLOR=#000080]gedit default.pa[/COLOR]
 
[COLOR=#000080]find the commented out line :[/COLOR]
 
[COLOR=#000080]#load-module module-alsa-sink[/COLOR]
 
[COLOR=#000080]change it to the hw noted earlier, [/COLOR][COLOR=#000080]in my case its hw:1,7,[/COLOR][COLOR=#000080]so the new line in the file is :[/COLOR]
 
[COLOR=#000080]load-module module-alsa-sink device=hw:1,7 [/COLOR]
 
[COLOR=#000080]save the file.[/COLOR]
 
[COLOR=#000080]now goto system settings menu and select sound,[/COLOR]
[COLOR=#000080]change your "output device" to the nvidia HDMI one.[/COLOR]
 
[COLOR=#000080]thats it sorted.[/COLOR]
 
[COLOR=#000080]the above has worked for me on various versions of linux that I've tried.[/COLOR]
 
[COLOR=#000080]the information i've used is from the nvidia web site support section, [/COLOR]
 
[COLOR=#000080]as follows :[/COLOR]
 
[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
 
I've tested the above fix with VLC, youtube, etc, everything works fine.

---

### Post by BicyclerBoy on 2012-04-20
Depending on your alsa/pulse audio versions you do not need to do this.

I would expect 12.04 pulse audio to enumerate all (4) HDMI audio sub-devices **or** just the one that has an valid ELD.

In your case the ELD can be found
/proc/asound/card1/eld#1.0

& should be event info in kernel logs
dmesg | grep HDA

---

