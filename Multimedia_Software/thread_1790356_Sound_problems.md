---
title: "Sound problems"
date: 2011-06-24
forum: Multimedia Software
---

### Post by Veritas_08 on 2011-06-24
It was suggested to me to post my problem here for a better chance of help, so here we go... I'm going to be as detailed as possible.

I am test driving Ubuntu 11.04 with Wubi which I obtained from the Ubuntu website. I did not burn it to a CD or USB because when I tried it told there wasn't enough room on the blank CD I had put in the tray. I had been able to download the last LTS (which I didn't use because it wouldn't recognize my internet connection and I just didn't have the time to mess with it) with no problems. So I downloaded straight to my hard drive. 

I restarted and booted into Ubuntu instead of Win7 (64 bit btw). And it immediately recognized my internet connection so I started to use it. I do like it a lot. Firefox alone sold me on it, pretty much. The first problem was no flash which with a little googling I fixed. Next was Banshee/Rhythmbox not recognizing my Droid X as a music player. I fixed that on my own. Once my music showed up on Rhythmbox and I started to play it there was no sound. That was 4 or 5 days ago. I've been pecking at this problem on my own for a week. It's the only thing keeping me from fully switching to Ubuntu. I like everything else and while I'm a complete newb to Linux I can see it's way more customizable and fun to use than Win7. 

I"m running my computer with my 40" Sony Bravia as the monitor through an HDMI cable, I don't know if this may be a factor. I went through the Sticky about sound problems here and I can see that Ubuntu does read the sound card on my system but for some reason it's not being used. I purged and reinstalled sound programs. Downloaded the Ubuntu extras. The only thing I didn't try was finding my card on the alsa project website because I can't tell what name my card has. Like I said, I'm a complete newb lol 

Below is the info I got from running the commands suggested in the sticky...

[SIZE=2]aplay -l
[/SIZE] **** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I think here is where it's showing that my card is there just not being used, Subdevices:1/1, Subdevice #0: subdevice #0. I've seen other posts where users paste something like this and at least one of the subdevices will read subdevice #1. But when I go to System Settings-Sound and check the available card, I don't see a way to enable it. I assume it is enabled as it is the only card in the system. I also tried the alsa mixer suggestion and none of the sliders are muted. I ran alsa mixer on the Terminal and saved the settings. I then restarted and the sliders remained turned up. So I don't think that's the problem. But this is just my guess. 

[SIZE=2]lspci -v[/SIZE]
I think this is my soundcard info...
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0492
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe520000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Here is where I'm supposed to be able to see the name and find it on the alsa project website. I did find a HDA Intel link there but I got lost in the jargon about working it into the kernel. Apparently once I find it I'm supposed to download the driver somehow (I didn't see a link for that) and the go on with the following command...

[SIZE=2]sudo modprobe snd-[/SIZE]
...where snd- would be followed by my card's name.

This is where I'm stuck. Any help any of you can give would be greatly appreciated. Trying to figure stuff like this on my own can be fun but I'd rather get help and get on with exploring Ubuntu fully instead of being stuck with the sound. I really wanna stick with Ubuntu as I'm enjoying its other features :) Here's hoping!

(For other newbs, run this script on the Terminal...)

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
My particular alsa diagnostic link... 

[http://www.alsa-project.org/db/?f=42088c201fae3f141e8ed47de33fcb6c2bed4900](http://www.alsa-project.org/db/?f=42088c201fae3f141e8ed47de33fcb6c2bed4900)

---

### Post by HeadHunter00 on 2011-06-24
i only see one driver for intel hd audio. must be universal for all intel sound cards. anyways, its called "snd-hda-intel" try that. sudo modprobe snd-hda-intel. but, i don't think that will do anything to fix the sound cuz i just noticed that the driver is already loaded. type in the command "alsamixer -c0" in terminal and turn everything all the way up. tell me if you get any sound then.

---

### Post by Veritas_08 on 2011-06-24
Hi and thanks for your reply...

Ran the command and this is what happened...

:~$ sudo modprobe snd-hda-intel 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.confoptions, it will be ignored in a future release.

Whatever that means.

---

### Post by Veritas_08 on 2011-06-24
Sorry, I didn't read the second part of your suggestion til now...

Pulled up alsamixer and the sliders are all up to the red. Tested by playing a video on youtube. Video plays perfectly, no buffering (as a former IE user, this no buffering has me sold lol) but no sound.

---

### Post by BicyclerBoy on 2011-06-25
install
pavucontrol

& use it to see what your sound output device is..

I'm not familiar with intel HDMI but..
It looks to me that the chipset audio device handles HDMI audio as well. 
This may complicate HDMI audio setup..

Could try
speaker-test -c 2 -r 48000 -D hw0:0
speaker-test -c 2 -r 48000 -F S32_LE -D hw0:0
speaker-test -c 2 -r 48000 -D hw0:3
speaker-test -c 2 -r 48000 -D hw0:7

Each time you stop speaker-test, close the terminal & re-open.

The last (2) cmds could make sound thru' your HDMI device (if you have speakers)

HDMI audio will depend on the graphics driver you are running..
If you are running the IGP sandybridge you may need to use xorg-edgers ppa

---

### Post by Veritas_08 on 2011-06-26
Thank you for your suggestion... tried it and this is what I get...

$ speaker-test -c 2 -r 48000 -D hw0:3

speaker-test 1.0.24.2

Playback device is hw0:3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM hw0:3
Playback open error: -2,No such file or directory

No sound still. Same for the other three commands, restarting Terminal for each. I'm running Windows and messing with Ubuntu when I get time. While in Windows, sound runs fine, well, as fine as HDMI sound runs. 

How do I know if I've Sandybridge and how would I go about getting that xorg deal?

Sorry, total newb here. Thanks again for your help.

---

### Post by BicyclerBoy on 2011-06-26
I think/guess you are running i5 or i7 

Need to go digging in the video driver & find out if HDMI audio is supported at all.

lspci -qnn
lspci -k -nn

Should see i915 for the VGA driver ?

---

### Post by lidex on 2011-06-26
You have one soundcard comprised of three devices - analog, digital, and hdmi. All are controlled by snd-hda-intel module. It looks like alsa is having some issues with your codec:
```
[   16.559154] hda_codec: ALC662 rev1: SKU not ready 0x411111f0
[   16.559319] hda_codec: ALC662 rev1: BIOS auto-probing.
```

Try a couple of model switches in alsa-base.conf. To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot.
Models:
```
3stack-6ch
auto
```
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute. Make sure dig/spdif elements are unmuted. MM signifies muting.

---

### Post by Veritas_08 on 2011-06-28
Thank you all for your help. Sorry it's taken a while to check on this. I mostly work on it on my free time. I'm going to try what's on the post above now. 

Desktop info:

Gateway SX2860
Win 7 64-bit.
Intel Core i3 2100. 
6GB RAM.
DVD-Super MultiDrive.
1TB Hard Drive.
intel HD graphics.
BIOS P01-A0

Not mighty impressive but it is my first desktop :)

---

### Post by Veritas_08 on 2011-06-28
Solved!!!!!!!!!!!!!!

Thank you so much, Lidex. You're a freaking genius!

I edited the file you suggested (see the post above by Lidex,) adding after "model=" I added "3stack-6ch", then saving and rebooting. I got no sound at first so I went to alsamixer, upped all the levels and checked that they weren't muted. 

After, I went to System Settings-Sound-Hardware and verified the card was being read and switched from Analog Audio to HDMI output + Analog input. And there was sound! 

Thank you again, Lidex. 

So long Windows.

-Ubuntu Convert

---

### Post by lidex on 2011-06-29
Nice. Glad to help.

---

