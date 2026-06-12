---
title: "HP-DV7 w/ Beats Audio speakers not working"
date: 2012-05-01
forum: Multimedia Software
---

### Post by Sxynerd on 2012-05-01
I recently upgraded with a fresh install Ubuntu 12.04 on my HP DV7-6135dx w/ Beats Audio.

The DV7 has 4 speaker and one Sub-woofer.  Currently only two speakers are working.  

Previously with 11.10 I fixed the problem by adding the line "options snd-hda-intel model=ref" to this file, "/etc/modprobe.d/alsa-base.conf" and then I would restart the PC.

When I attempted to use this fix with 12.04 I get no sound at all.

Please advise.  :)

---

### Post by Sxynerd on 2012-05-01
There was no change after doing this.


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0870, uzi, G36, USP9 Tactical, PS90, FN57, HiPower, FMAS



sudo apt-get install --reinstall libasound2
[sudo] password for wolvee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 427 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libasound2 amd64 1.0.25-1ubuntu10 [427 kB]
Fetched 427 kB in 1s (250 kB/s)      
(Reading database ... 168192 files and directories currently installed.)
Preparing to replace libasound2 1.0.25-1ubuntu10 (using .../libasound2_1.0.25-1ubuntu10_amd64.deb) ...
Unpacking replacement libasound2 ...
Setting up libasound2 (1.0.25-1ubuntu10) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by Sxynerd on 2012-05-02
Anyone?

---

### Post by Sxynerd on 2012-05-03
Anyone?

---

### Post by Sxynerd on 2012-05-04
Is there something I'm missing?  Why aren't there any replies to my threads?  Do I smell? :)

---

### Post by Sxynerd on 2012-05-05
alsa-info-script 

[http://www.alsa-project.org/db/?f=233c8c44df66fd6deb7cfcacb2a32e4881bb3c68](http://www.alsa-project.org/db/?f=233c8c44df66fd6deb7cfcacb2a32e4881bb3c68)

---

### Post by Sxynerd on 2012-05-05
More outputs

> wolvee@wolvee-dv7:~$ wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
--2012-05-05 10:34:43--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org](www.alsa-project.org))... 77.48.224.243
Connecting to [www.alsa-project.org](www.alsa-project.org) ([www.alsa-project.org)|77.48.224.243|:80](www.alsa-project.org)|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2012-05-05 10:34:44--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [    <=>                                ] 27,247      38.4K/s   in 0.7s    

2012-05-05 10:34:46 (38.4 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

grep: /tmp/alsa-info.rErDaC68SC/wget.tmp: No such file or directory
Your ALSA information is located at 
Please inform the person helping you.

---

### Post by Sxynerd on 2012-05-06
I still really need help please.

---

### Post by Simplicius on 2012-05-22
I have the same issue. I hope someone will be kind enough to give some advice.

---

### Post by compunaut on 2012-05-25
I do not really know what I am doing, but I had the same problem with my HP dv7 computer, no sound in speakers or earphones.  Someone else posted this fix for a different system, and it gave me sound through the speakers.  It is not a good solution because earphones still do not work, but perhaps this will give someone with more knowledge than me a clue to the proper solution.


To make sound work after updating to Ubuntu 12.4 in my HP dv7, I added this line at the end of /etc/modprobe.d/alsa-base.conf

          options snd-hda-intel model=generic

---

### Post by loboes41 on 2012-05-30
I have the same issue. On upgrade, I had no sound at all, so I changed that last line in alsa-base.conf to:

```
options snd-hda-intel model=auto
```

I have sound in the two main speakers, but NOT the subwoofer.

Anyone find an answer for this?

---

### Post by jgamboa on 2012-06-06
I have the same case, have audio on both speakers but not as loud as compared before when I use Win7.

---

### Post by m7esain on 2012-06-08
Same here too, i have the HP DV6-6145dx

only the front two speakers are working

any suggestions

---

### Post by trulynon on 2012-06-30
And me as well. The sound is gone last night (perhaps?) since I don't know if I have the sound before or not. Anyway I have the same card.

```
mariusz@mariusz-HP-ProBook-4530s:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have modified > /etc/modprobe.d/alsa-base.conf by adding > options snd-hda-intel model=generic and still no results. 

I also get back to previous kernel and still no luck...Pretty annoying. I don't know if this is a hardware issue whether not. I also noticed that when I plug and unplug headphones the sound from speakers i coming, but only for a second or so and then is gone again. I noticed this problem on Windows as well and other members suggesting that this might be a hardware problem, but some says that drivers for IDT HDA Audio card are messed. Any solution? Thanks

---

### Post by nicepants on 2012-07-03
i have an Envy 15 with Beats Audio and a similar problem. i use this in my alsa-base.conf:

> 
options snd-hda-intel model=ref


this has given me the audio from the subwoofer and at least two of the front speakers, but nothing from the top speakers. it's better, but i'm still looking for a solution for all six speakers.


you may want to try some of the models in [HD-Audio-Models.txt]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD") as there are specific entries for some laptops like the DV7-4000 and DV5.

---

### Post by Selim873 on 2012-07-04
> **nicepants said:**
> i have an Envy 15 with Beats Audio and a similar problem. i use this in my alsa-base.conf:



this has given me the audio from the subwoofer and at least two of the front speakers, but nothing from the top speakers. it's better, but i'm still looking for a solution for all six speakers.


you may want to try some of the models in [HD-Audio-Models.txt]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD") as there are specific entries for some laptops like the DV7-4000 and DV5.

How could I find my model?  I'm using an HP Pavilion dv7-6c90us, I just don't wanna start shooting in the dark.

---

### Post by StardustLuna on 2012-07-16
I'm not very knowledgeable in coding or anything, but I have the same laptop and on win7 it seemed as if there was a driver or program that utilized the speakers to their fullest. Whatever the solution is, I need it as well. My sound is horrid. 

~Stardust:KS

---

### Post by StardustLuna on 2012-07-17
Update:

I now have sound from all 4 of my speakers, still no subwoofer, but the quality has vastly increased. 

I just installed the gnome alsa mixer and within it the mixer window showed two spots for 'speakers' and one of them was muted. So yeah, fixed that. Messing around with some of the controls helped with the quality. 

Still want my subwoofer, but I think we'll have to wait for a driver for it. I looked on HP's website, and this brand of laptop originally came with an HD sound driver, I looked around for an HD driver for ubuntu and the only lead I found was one from Realtek, but I can't seem to find anywhere to download and install it. 

~Stardust:KS

---

### Post by Sxynerd on 2012-08-15
I just thought I would update this thread.  there has been no fix that I have found for it.

It's odd that 11.10 had such a simple fix but 12.04 has nothing.

---

### Post by wegah on 2012-09-15
wish this turn everything well. ;-)


/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=hp-dv7-4000

---

### Post by brentini on 2012-09-17
Are you wishing or confirming? Please be more specific my friend.

---

### Post by Sxynerd on 2012-09-21
> **wegah said:**
> wish this turn everything well. ;-)


/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=hp-dv7-4000


This does not work.

---

### Post by stevesmith1987 on 2012-10-08
> **wegah said:**
> wish this turn everything well. ;-)


/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=hp-dv7-4000

I just wanted to confirm that I just tried this with my HP dv7 and it worked for me.

---

### Post by Sxynerd on 2012-10-09
> **stevesmith1987 said:**
> I just wanted to confirm that I just tried this with my HP dv7 and it worked for me.

Is your problem exactly as mine?  Only two of the 5 speakers work? 

There's a common confusion with these Beats audio threads where people start talking about their Mic and Headphones jacks don't work but That's not my DV7's issue.

---

### Post by stevesmith1987 on 2012-10-09
> **Sxynerd said:**
> Is your problem exactly as mine?  Only two of the 5 speakers work? 

There's a common confusion with these Beats audio threads where people start talking about their Mic and Headphones jacks don't work but That's not my DV7's issue.

I have a different dv7 model apparently. I only have 2 speakers and a subwoofer.  The above command worked with mine.

---

### Post by CalcProgrammer1 on 2012-11-09
Anyone have any luck with 12.10?  I have a dv6z-7000 (AMD Trinity) and put Kubuntu 12.10 on it.  I previously had 12.04 and the model=ref got me subwoofer and broke headphones.  Now I get nothing from model=ref at all, just 2 speakers with working headphones (headphones switches off 2 main speakers when plugged in).

Here is my alsa-info:

[http://www.alsa-project.org/db/?f=3c89e273beb52ac4ca57389050662841ab2b29c0](http://www.alsa-project.org/db/?f=3c89e273beb52ac4ca57389050662841ab2b29c0)

---

### Post by lunerceli on 2013-01-10
I also have a dv-7 w/ beats audio. With Ubuntu 12.10 I have gotten the 4.0 surround sound to work, but no subwoofer. I was on the other hand playing with /etc/pulse/system.pa and default.pa by adding lines to remap the speakers. Got a little bit of luck with it, but couldn't get the mapping correct. I am still trying though. If you would like to test what speaker channel is what, then open terminal and type
```
speaker-test -c5 -l1 -twav
```It will play once through all of your channels as a 5 channel audio setup. If you would like to keep it playing more than once so you can hear exactly what is what, then type this into terminal
```
speaker-test -t wav -c 5
```In order to stop the playback, just hit Control + C. Here is the code that I am working with within the pulseaudio wrapper:
```
                                   # Definition of standard sink
load-module module-alsa-sink sink_name=standard device=hw:0 channels=5 channel_map=front-left,front-center,front-right,rear-left,rear-right,
 # Remapping Function
load-module module-remap-sink sink_name=remapped_sound master=standard channels=5 master_channel_map=front-left,front-center,front-right,rear-left,rear-right channel_map=front-left,rear-left,front-right,front-center,rear-right
 # Setting Default to your new re-mapped sink
# (should match the "sink_name" in line 2)
set-default-sink remapped_sound
  
```Basically what I am trying to do is to get the pusleaudio-sink to remap to the alsa-base-sink. Hopefully I can get this working and post a working config file for all with beats audio. Don't worry though, I am working hard on it and trying to get it configured. There are a few other steps that I have taken like muting out a couple of lines within the system.pa and default.pa files that allows this remapping to be done. 

One thing though is that if you have upgraded to the latest Alsa Audio for your distrobution, or even by compiling it yourself, then you should already have the surround sound 4.0 listed in sound properties under the hardware tab.

Hope this helps someone and I will post back with more results. Just hope that Conical gets with the times since it has been over 3 years since the stac92xx chipset came about and still nothing has been implemented for it.

---

### Post by CalcProgrammer1 on 2013-02-03
I figured it out, and have posted in my other thread on this topic.

See here:
[http://ubuntuforums.org/showpost.php?p=12489414&postcount=2](http://ubuntuforums.org/showpost.php?p=12489414&postcount=2)

You need to install hda-jack-retask and retask some of the jacks for PulseAudio.  It's pretty easy, and it holds across reboots.  Should work regardless of what Ubuntu release you're on, I'm on 12.10.  This worked for my dv6z-7000 but if it doesn't work for other models play around with the configurations a bit and figure out which channels are which speakers, then post it.  I started by setting all of them to "Internal Speakers" and turning them off to pinpoint each channel, then setting them to the correct values.

---

### Post by Jammyjamjamman on 2013-02-03
> **CalcProgrammer1 said:**
> I figured it out, and have posted in my other thread on this topic.

See here:
[http://ubuntuforums.org/showpost.php?p=12489414&postcount=2](http://ubuntuforums.org/showpost.php?p=12489414&postcount=2)

You need to install hda-jack-retask and retask some of the jacks for PulseAudio.  It's pretty easy, and it holds across reboots.  Should work regardless of what Ubuntu release you're on, I'm on 12.10.  This worked for my dv6z-7000 but if it doesn't work for other models play around with the configurations a bit and figure out which channels are which speakers, then post it.  I started by setting all of them to "Internal Speakers" and turning them off to pinpoint each channel, then setting them to the correct values.

I have a HP dv7-7102ea and my system is Linux Mint 14 (Ubuntu 12.10). It has the exact same sound card as your computer and your fix worked brilliantly with all speakers working (except for the 0x0f pin which had to be labeled internal speaker (back) so not a big problem), so firstly thanks for your fix! :)

Secondly, after using this fix all my sound settings went completely wrong. If I go into the normal sound settings (not alsa) I can select the 4.1 surround but I can't test any of the speakers and I can only treat them as stereo with the subwoofer considered as part of the left channel. The story is similar with alsamixer. I'm not overly worried about the lack of surround since all the speakers are placed at the front so it makes little/no difference treating them as surround. What I am unsure about is not being able to test the speakers. Any ideas?

Thanks

---

### Post by CalcProgrammer1 on 2013-02-03
I think the speaker wiring is the same but the actual placement varies.  On my laptop, the main speakers are above the keyboard, the secondary speakers are in the center below the screen, and the sub is on the bottom.  They're not really "surround" in this case.  I tried setting them to "Internal speakers (back)" and the main speakers to "Internal speakers" but for some reason the subwoofer wouldn't work with this configuration.

---

### Post by Jammyjamjamman on 2013-02-03
Yes it looks like the speaker placement on my computer is the same, with the subwoofer on the bottom right of the computer ( your right when facing the screen), and the pins are definitely the same as far as I can see. well, to be honest I'm happy enough with a stereo setup as long as all 4 speakers + subwoofer are active (which they are), in fact the most enhancement to the sound occurs when you have at least 2 speakers and the subwoofer active.

---

