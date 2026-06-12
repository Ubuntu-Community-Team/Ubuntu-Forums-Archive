---
title: "No sound, lspci sees sound card, alsa+pulseaudio don't, was fine recently. ???"
date: 2018-07-12
forum: Multimedia Software
---

### Post by eggplant2718 on 2018-07-12
[FONT=arial]I'm running Ubuntu 16.04 LTS on a Dell XPS 13 (pre-installed). Everything was fine a week or two ago. Then the sound got glitchy (changing the volume through audio settings sometimes wouldn't change anything) and then disappeared altogether. I went through applicable portions of [/FONT][https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)[FONT=arial]: 1, 2, applicable parts of 3, 4. [/FONT]

[FONT=arial]What I'm seeing: [/FONT]
[FONT=arial]- There is no drumming sound on startup (there used to be)[/FONT]
[FONT=arial]- There is no sound playing from any other application (aplay, chrome, etc)[/FONT]
[FONT=arial]- Nothing is muted[/FONT]
[FONT=arial]- Neither laptop speakers nor headphones produce any sound[/FONT]
[FONT=arial]- Previously when I plugged in headphones, there would be a dialogue asking if I plugged in headphones or a headset. Now when I plug in headphones, no dialogue pops up. The rest of the diagnostics are for when there aren't headphones plugged in. [/FONT]
[FONT=arial]- A sound card shows up in lspci:[/FONT]
[FONT=arial]00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21) (prog-if 80)[/FONT]
[FONT=arial]        Subsystem: Dell Device 075b[/FONT]
[FONT=arial]        Flags: bus master, fast devsel, latency 32, IRQ 134[/FONT]
[FONT=arial]        Memory at dc428000 (64-bit, non-prefetchable) [size=16K][/FONT]
[FONT=arial]        Memory at dc400000 (64-bit, non-prefetchable) [size=64K][/FONT]
[FONT=arial]        Capabilities: <access denied>[/FONT]
[FONT=arial]        Kernel driver in use: snd_hda_intel[/FONT]
[FONT=arial]        Kernel modules: snd_hda_intel[/FONT]
[FONT=arial]- "cat /proc/asound/cards" outputs "--- no soundcards ---"
[/FONT]- "aplay -l" outputs "aplay: device_list:268: no soundcards found..."
[FONT=arial]- output from alsa-info.sh from step 3 of troubleshooting guide: [/FONT]
[FONT=arial]ALSA information is located at [/FONT][http://www.alsa-project.org/db/?f=2a117dedc8ef7794add952d4deb879694f2e8702](http://www.alsa-project.org/db/?f=2a117dedc8ef7794add952d4deb879694f2e8702)
- pavucontrol only displays one output device, "Dummy Output"
[FONT=arial]
[/FONT][FONT=arial]Please help! What can I do? Is there other information I could provide that would be helpful? [/FONT]

[FONT=arial]Thank you![/FONT]

---

### Post by mIk3_08 on 2018-07-12
How about in setting --> sound... ?

[ATTACH=CONFIG]280366[/ATTACH]

---

### Post by Yellow Pasque on 2018-07-12
```
[    4.325917] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[    4.327443] snd_hda_intel 0000:00:1f.3: no codecs found!
```

That's bad. I suggest this first when I see that error (assuming you have the appropriate option in your BIOS):
1. Start with the system turned off. 
2. Power on and enter the BIOS/EFI (or system setup or whatever Dell calls it). Disable the audio codec. Save changes and exit the BIOS. The system will reboot.
3. After system is fully booted, shut down.
4. Boot into BIOS again and re-enable the codec. Save/exit and boot into OS.

---

### Post by Yellow Pasque on 2018-07-12
Other notes:
It looks like you're running an older BIOS (1.3.5). You may want to consider updating.

```
[    4.208087] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.201708030416~ubuntu16.04.1
```
It looks like you installed ALSA dkms last year. You may want to consider purging that and getting a newer version: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201806070316~ubuntu16.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201806070316~ubuntu16.04.1_all.deb)

Or maybe if you get the sound working again, you don't want to touch anything. *shrug*

---

### Post by eggplant2718 on 2018-07-15
Hi! Sorry for the delay.

mlk3_08, the sound settings are fine.

Temujin, I attempted to purge alsa dkms but accidentally did sudo apt-get purge dkms, which was a mistake and isn't stopping ... please help :/

---

### Post by eggplant2718 on 2018-07-15
Temujin, how do you purge alsa dkms? Could you provide more detailed instructions? Thanks!

---

### Post by mIk3_08 on 2018-07-15
ah, so you completely remove the package, 

install the package, try this command;

```
sudo apt-get install dkms
```

---

### Post by mIk3_08 on 2018-07-15
> **Temüjin said:**
> Other notes:
It looks like you're running an older BIOS (1.3.5). You may want to consider updating.

```
[    4.208087] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.201708030416~ubuntu16.04.1
```
It looks like you installed ALSA dkms last year. You may want to consider purging that and getting a newer version: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201806070316~ubuntu16.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201806070316~ubuntu16.04.1_all.deb)

Or maybe if you get the sound working again, you don't want to touch anything. *shrug*


Just download the package under the link given by Temüjin;
I think this will help you eggplant2718.

---

### Post by eggplant2718 on 2018-07-15
mlk3_08, my concern regarding purging dkms was because the process was going on for more than a couple minutes which seemed unusual to me. I ended up killing the purge, (re-)installing dkms, and sudo apt-get update / upgrade, which I hope is fine. 

I've updated alsa dkms and rebooted, but still no sound. 

Temujin, could you point me to more detailed instructions regarding upgrading bios or disabling/enabling the audio codec? 

What are the risks of either option if the situation is not as expected or I make a mistake, and how likely is either option to fix the sound problem? 

Thanks!

---

### Post by Yellow Pasque on 2018-07-15
The package name is oem-audio-hda-daily-dkms.

> could you point me to more detailed instructions regarding or disabling/enabling the audio codec?

I can't get any more detailed than the instructions I gave you without having the exact same laptop sitting in front of me. Just changing the option to disable/enable your onboard audio isn't risky.
If you're uncomfortable doing BIOS updates, don't do it. There's a lot more potential to screw things up with that.

---

### Post by mIk3_08 on 2018-07-15
> **eggplant2718 said:**
> mlk3_08, my concern regarding purging dkms was because the process was going on for more than a couple minutes which seemed unusual to me. I ended up killing the purge, (re-)installing dkms, and sudo apt-get update / upgrade, which I hope is fine. 

I've updated alsa dkms and rebooted, but still no sound. 

Temujin, could you point me to more detailed instructions regarding upgrading bios or disabling/enabling the audio codec? 

What are the risks of either option if the situation is not as expected or I make a mistake, and how likely is either option to fix the sound problem? 

Thanks!

eggplant2718 try checking the status of your dkms 


```
dkms status
```

---

### Post by mIk3_08 on 2018-07-15
eggplant2718 You can check some DKMS here;

Dynamic Kernel Module Support Framework (dkms for bionic (18.04))
[Click Here]("https://www.ubuntuupdates.org/package/core/bionic/main/updates/dkms")
Dynamic Kernel Module Support Framework (dkms for xenial (16.04LTS))
[Click Here]("https://packages.ubuntu.com/xenial/admin/dkms")

---

### Post by mIk3_08 on 2018-07-17
I think after the code;
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
You forgot to update the system;
```
sudo apt-get update
```
or you may use this code;
```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```
Then reboot the machine

---

### Post by wildmanne39 on 2018-07-17
@mIk3_08```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

Please explain to the OP what that command does.

Thanks

---

### Post by Yellow Pasque on 2018-07-17
> **wildmanne39 said:**
> Please explain to the OP what that command does.

It reinstalls packages in case they got removed and adds user back to pulse group in case the user screwed those up. It's probably nothing that's going to fix "CORB reset timeout... no codecs found!" though.
Oh, and the command is outdated since it's using ~/.pulse instead of ~/.config/pulse and lightdm instead of gdm. It also reinstalls ubuntu-desktop which may add back a bunch of packages the user doesn't want. Not recommended by me.

---

### Post by QIII on 2018-07-17
I have removed a number of posts due to rambling attempts at help and due to a hijack.  I'm not going to pick it over further to restore better continuity because that would probably make the thread entirely useless.

Please:  

1.  Don't attempt to provide assistance by posting old, outdated information.

2.  Don't hijack the threads of others because it causes just the sort of confusion that this thread devolved to.

3.  Please report hijacks rather than drawing the hijacker into the discussion.  We can move the hijack to its own thread to allow everyone to get coherent help individually.

Thanks all for your assistance to the OP.

---

### Post by nik.charles on 2018-08-26
Part of command in post#12 appears to be outdated

Pulseaudio no longer uses folder ~/.pulse/

to remove contents of new folder

```
rm -r ~/.config/pulse/*
```

reboot pc to ensure Pulseaudio rebuilds new configuration files

---

### Post by nik.charles on 2018-08-26
Wondering if OP is dual-booting with Windows?

Audio device may be set to a power state by hybrid hibernation/shutdown in windows that causes it to not be detected by Linux

---

### Post by Yellow Pasque on 2018-08-26
> **nik.charles said:**
> Part of command in post#12 appears to be outdated

I already pointed that out in a previous post. OP has not responded in 6 weeks.

---

### Post by Yellow Pasque on 2018-08-26
> **nik.charles said:**
> Wondering if OP is dual-booting with Windows? Audio device may be set to a power state by hybrid hibernation/shutdown in windows that causes it to not be detected by Linux

That's part of what I was getting at by telling OP to disable/enable codec in BIOS, but apparently OP couldn't figure out how to get in BIOS. I guess Dell uses F2 key on these models, but I'm not sure.

---

