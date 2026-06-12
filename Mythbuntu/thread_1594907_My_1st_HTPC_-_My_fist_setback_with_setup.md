---
title: "My 1st HTPC - My fist setback with setup"
date: 2010-10-12
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-10-12
So I built the hardware as shown in [COLOR="Blue"]["Going to build my 1st HTPC"]("http://ubuntuforums.org/showthread.php?t=1587584")[/COLOR].

I installed Mythubuntu from a CD, notes are [COLOR="blue"][here]("https://docs.google.com/document/pub?id=19TYASadZmtd3NqH2PMUYV_Ild9u9ELlcIpEpE6nBuWQ")[/COLOR].

After finishing LowSky's [COLOR="blue"][tutorial]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212")[/COLOR] on the Hauppauge HVR-2250, I could watch but not hear TV and schedule recordings. 

Then I installed alsa 1.0.23 from this guide, made suggested changes as shown on the last page of my notes.  I using [COLOR="blue"][this]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")[/COLOR] and [COLOR="blue"][this]("http://ubuntuforums.org/showthread.php?p=6589810")[/COLOR] as guides.  The actual changes I made can be seen on the last page of my [COLOR="blue"][notes]("https://docs.google.com/document/pub?id=19TYASadZmtd3NqH2PMUYV_Ild9u9ELlcIpEpE6nBuWQ")[/COLOR].

Now when I start the HTPC and try to Watch TV (and test the sound) I get a message box that says there are no active recordings, &c.  If I stop and restart the backgound using the MythTV Background Setup, I can then watch TV, but alas no sound.

I could use a little help here :confused:

Thanks

---

### Post by keepitsimpleengr on 2010-10-12
I tried this...

```
me@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
me@htpc:~$ aplay -D plughw:1,3 aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
aplay: main:654: audio open error: No such file or directory
...
root@htpc:~# aplay -D plughw:1,3 aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid v[CODE]alue for card
aplay: main:654: audio open error: No such file or directory
...
me@htpc::/usr/share/sounds/alsa$ ls -slat | grep Noise
136 -rw-r--r-- 1 root root 135202 2010-10-12 13:37 Noise.wav
```

:confused:

---

### Post by scudderwagg on 2010-10-12
By the looks of this from your notes:
> :~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]

 Subdevices: 1/1

 Subdevice #0: subdevice #0

card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]

 Subdevices: 1/1

 Subdevice #0: subdevice #0

card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]

 Subdevices: 1/1

 Subdevice #0: subdevice #0

card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]

 Subdevices: 1/1

 Subdevice #0: subdevice #0
It appears you may need to use a different probe_mask setting.  I had to fiddle with a couple different settings to get it right.  When it's right you should only have one device show up (assuming you have one sound card installed).  Good luck!

---

### Post by David Grigor on 2010-10-13
Shouldn't you be testing with plughw 0,3 instead of 1,3 ?

---

### Post by novellahub on 2010-10-13
I have a GT240.  Use card 0 device 7 for your selection.  If you create a asound.conf file, you can use default as your sound selection in Mythtv.  You can see my notes here:

[http://mythtvmadness.blogspot.com/2010/05/alsa-1023-upgrade.html](http://mythtvmadness.blogspot.com/2010/05/alsa-1023-upgrade.html)

Here is what is in my /etc/modprobe.d/sound.conf file:

```

options snd-hda-intel enable_msi=0 index=1

```

---

### Post by keepitsimpleengr on 2010-10-13
> **scudderwagg said:**
> By the looks of this from your notes:

It appears you may need to use a different probe_mask setting.  I had to fiddle with a couple different settings to get it right.  When it's right you should only have one device show up (assuming you have one sound card installed).  Good luck!

I added the sound.conf file as follows:

```
root@htpc:/etc/modprobe.d# cat sound.conf
#
# ***me***101013***>
# [https://bbs.archlinux.org/viewtopic.php?id=90350](https://bbs.archlinux.org/viewtopic.php?id=90350)
options snd-hda-intel enable_msi=0
options snd-hda-intel probe_mask=0xfff2
# <***me***101013***


root@htpc:/etc/modprobe.d# ls -slat
total 52
12 drwxr-xr-x 139 root root 12288 2010-10-13 08:21 ..
 4 drwxr-xr-x   2 root root  4096 2010-10-12 16:23 .
 4 -rw-r--r--   1 root root   170 2010-10-12 16:23 sound.conf
 4 -rw-r--r--   1 root root  2617 2010-10-12 16:21 alsa-base.conf
 0 lrwxrwxrwx   1 root root    32 2010-10-11 14:48 nvidia-graphics-drivers.conf -> /etc/alternatives/nvidia_modconf
 0 lrwxrwxrwx   1 root root    41 2010-10-11 14:42 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
 0 lrwxrwxrwx   1 root root    21 2010-10-11 14:42 oss-compat.conf -> /lib/oss-compat/linux
 4 -rw-r--r--   1 root root   325 2010-04-13 21:26 blacklist-ath_pci.conf
 4 -rw-r--r--   1 root root  1603 2010-04-13 21:26 blacklist.conf
 4 -rw-r--r--   1 root root   213 2010-04-13 21:26 blacklist-firewire.conf
 4 -rw-r--r--   1 root root   660 2010-04-13 21:26 blacklist-framebuffer.conf
 4 -rw-r--r--   1 root root  1077 2010-04-13 21:26 blacklist-watchdog.conf
 4 -rw-r--r--   1 root root   156 2010-01-28 16:01 blacklist-modem.conf
 4 -rw-r--r--   1 root root    16 2010-01-06 00:12 libpisock9.conf

Now I get this:

root@htpc:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@htpc:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```


I think it'll probably help?

---

### Post by keepitsimpleengr on 2010-10-13
> **David Grigor said:**
> Shouldn't you be testing with plughw 0,3 instead of 1,3 ?

Right!

```
...
root@htpc:~# aplay -D plughw:1,3 aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
aplay: main:654: audio open error: No such file or directory
...
root@htpc:~# aplay -D plughw:0,3 aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
aplay: main:654: audio open error: Device or resource busy
```

I think we might be getting closer

---

### Post by keepitsimpleengr on 2010-10-13
> **novellahub said:**
> I have a GT240.  Use card 0 device 7 for your selection.  
...
Here is what is in my /etc/modprobe.d/sound.conf file:

```

options snd-hda-intel enable_msi=0 index=1

```

I changed the sound.conf thus:
```
#
# ***me***101013***>
# [https://bbs.archlinux.org/viewtopic.php?id=90350](https://bbs.archlinux.org/viewtopic.php?id=90350)
options snd-hda-intel enable_msi=0 index=1
#options snd-hda-intel probe_mask=0xfff2
# <***me***101013***
```rebooted

now:
```
root@htpc:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
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
root@htpc:~# aplay -D plughw:1,7 aplay -D plughw:1,7 /usr/share/sounds/alsa/Noise.wav
aplay: No such file or directory
root@htpc:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
root@htpc:~# ls -slat /usr/share/sounds/alsa | grep Noise.wav
136 -rw-r--r-- 1 root root 135202 2010-10-12 13:37 Noise.wav
root@htpc:~# alsamixer
cannot open mixer: No such file or directory
```
Uffda! Still confused...
I'm gonna study novellahub's notes.

---

### Post by keepitsimpleengr on 2010-10-13
I ran "[alsa-info.sh.txt]("http://www.alsa-project.org/alsa-info.sh")" from this [web page]("http://www.kernel.org/pub/linux/kernel/people/tiwai/docs/HD-Audio.html#_codec_probing_problem").

The results are attached.

I am going to study on this.

---

### Post by LowSky on 2010-10-13
as for having to stop and restart the backend to get mythtv to work with livetv...

did you install the  1.3.3 firmware and did you skip step 3a? if yes to either please try using those parts of my tutorial.

as for sound over HDMI, it can be tricky... my tutorial does cover some of that as well, step 11a

[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

---

### Post by PhilWig on 2010-10-15
Don't know if you've fixed your sound to HDMI problem – I found it a real challenge, and whilst it is now working it's still black magic!

My setup:  Mythbuntu 9.04, Asus M3N78-EM mobo with onboard Nvidia 8300 graphics.  DVB-T received via Hauppauge T500 in the UK, TV connected via HDMI.

Steps were:

1.   Ensure that Bios advanced > chipset > southbridge > azalia audio has internal codec enabled (or both).  Set HDMI rather than SPDF output.
  
2.  See:   ubuntuforums.org/archive/index.php/t-1140776.html
Create  /etc/asound.conf  as suggested by DrJohn999 on 2 May 2009.

3.  Set alsamixer as per 29 April 09  ie enable all three 958 channels; set master and front volumes to max.

4.  Myth frontend  Setup > setup > general >> audio settings:

        Audio output device = ALSA:default
        Passthrough output device:  default
        Max audio channels:  stereo
        Upmix:  passive
        Enable AC3 to SPDF     no
        Enable DTS to SPDF     no
        Aggressive sound card buffering:  no
        Use internal volume controls;   Yes
        Mixer device:  ALSA:default
        Mixer controls:  PCM
        Two Volume sliders:   100
        Independent muting:  no

Note  In the thread you will see references to adding the line  options snd-hda-intel model=6stack-dig   
to file /etc/modprobe.d/alsa-base.conf.
Other contributors have suggested creating or modifying different files in /etc/modprobe.d
I found these un-necessary.

Don't know if the above really helps with your setup, but good luck!
Phil

---

### Post by keepitsimpleengr on 2010-10-15
> **LowSky said:**
> as for having to stop and restart the backend to get mythtv to work with livetv...

did you install the  1.3.3 firmware and did you skip step 3a? if yes to either please try using those parts of my tutorial.

as for sound over HDMI, it can be tricky... my tutorial does cover some of that as well, step 11a

[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

Well, I think some progress has been made.

I reinstalled mythbuntu from scratch.  This time I enabled the motherboard's onboard HD (ATI) sound.  

I followed LowSky's complete tutorial with the goal of HDMI audio to the TV for passing on to the 5.1 system.

After this, to only sound card recognized was the one (ATI) on the motherboard.

So I installed alsa 1.0.23 as before.

Now both the ATI and nvidia sound cards cards are identified, and testing the sound output of the nvidia card produces appropiate sounds on the 5.1 speakers and the TV speakers through the HDMI cable.

[INDENT]speaker-test -Dplughw:1,3 -c2[/INDENT]

[CENTER]***HOORAY!***[/CENTER]

But still no sound while watching MythTV. :( Frontend setup options?  Hauppauge tuners dropping audio? Straw&#8943;grabbing time!


[CENTER]**_OTHER PROBLEMS_**[/CENTER]

1)  With dual x screens, I can find no way to get the frontend to run on screen 1 without using the application menu on screen 1.  Reading LowSky's tutorial this capability was available previously  

2) When the frontend starts, it refuses to allow watch tv until the backend is killed and allowed to restart.

---

### Post by LowSky on 2010-10-15
1) Where did I write that in my tutorial? Are you trying to setup so that the frontend loads at boot on a certain screen?

2) Install the newer drivers from kernellabs and it will work without requiring a restart.

As for sound check your sound settings from the setup, general menu on the frontend you must have the wrong ```
ALSA:plughw:x,y
``` under Audio System (x,y being the output from terminal command aplay -l)

yours should be ```
ALSA:plughw:1,3
```

also 10.10 includes alsa version 1.0.23 already, so adding the PPA is just going to update very few packages at this moment, and nothing that should be giving you a headache.

---

### Post by keepitsimpleengr on 2010-10-16
> **LowSky said:**
> 1) Where did I write that in my tutorial? Are you trying to setup so that the frontend loads at boot on a certain screen?


Actually I was going to but have abandoned the idea.  From your tutorial…

> 9. Now go to Applications >Multimedia > MythTV Frontend.

The next part is from my setup, but for many it might be required (I would love feedback).

First go to Utilities / Setup, its the last option. Choose Setup, then Appearance.

The first page is to choose your theme (A little about me: my choice is MythCenter-wide).
Next page is important: If you have more than one monitor, pick the one you want to display the GUI on. The second is the Monitor Aspect Ratio, be sure to set it to your TV or monitor's correct display size, Mine is 16:9 your's may be 16:10 or 4:3. A good rule of thumb I follow is most HDTV's are 16:9, most PC monitors are 16:10, SDTV is 4:3. Failure to set this might result in a horrible picture. Also on this page is to hide the mouse cursor. If you want to use a mouse over a keyboard or remote, then uncheck the box.
&#8943;

On my mythtv there is no display choice or monitor aspect ration choice, I don't know why that is.

---

### Post by keepitsimpleengr on 2010-10-16
> **LowSky said:**
> &#8943;2) Install the newer drivers from kernellabs and it will work without requiring a restart.&#8943;

I did install the kernellabs drivers.

> &#8943;yours should be ```
ALSA:plughw:1,3
```&#8943;

When I used the test sound, it was plughw:1,3 and it worked, that it it produced a tone on both TV speakers and the 5.1 speakers, but when I run Mythtv front end, no sound comes through.

Thanks for being patient&#8213;I know I have overlooked some small thing but I am determined to get this working.

I'm going to download 10·10 and try that.

---

### Post by keepitsimpleengr on 2010-10-16
> **keepitsimpleengr said:**
> &#8943;I'm going to download 10·10 and try that&#8943;

amd64 install failed.  Goes to mild screen garbage after splash.  

[Bug filed]("https://bugs.launchpad.net/mythbuntu/+bug/661863")

:(

---

### Post by winewood on 2010-10-17
I too have a 2250 and my backend has to be restarted every reboot before it works. I was understanding that the card is starting up and the backend is started before the card is ready. I blame my hardware and OS being much faster than the Hauppage 2250 cards init. I have tried getting it to delay, but that didn't help. The positive point is that once I restart the backend, I am working perfect until the next reboot that only happens every month or more. Having my HDHomerun on beforehand allows me to watch live TV, but 2 of my 4 feeds are not availiable.
 
> by Lowsky 2) Install the newer drivers from kernellabs and it will work without requiring a restart.

 
Lowsky, I followed your installation instructions and I thank you for getting my card to work initially, however that was 3 months ago. Has a new driver come out since that fixes this? 
 
If restarting the backend after auto boot to mythfrontend presentation is the worst problem I have, I can deal with it. I'm saving $77 each month. :guitar:
 
keepitsimpleengr ->  [http://ubuntuforums.org/showthread.php?t=1471137](http://ubuntuforums.org/showthread.php?t=1471137)  I used this to get past my install that wasnt working.  It may help you.

---

### Post by keepitsimpleengr on 2010-10-17
[CENTER]**_[size="5"]success ! ! ![/size]_**[/CENTER]

My hardware is [here]("http://ubuntuforums.org/showthread.php?t=1587584&page=3").

Step (1)

New install of mythbuntu 10.04 LTS amd64 from CD

Step (2)

Update to current 10.04 using Update Manager

Step (3)

Used [LowSky's tutorial]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") Steps 1,2,3a, 3b, 4

Step (4)

Distribution Update online using Update Manager to 10.10

Step (5)

Copied mythdvd and mythtv folders from /var/lib/ to /dvr, set owner and updated mythtvbackend to those changes.  Note: will tell you it won't work but it does work.  /dvr is the large 2TB disk for mythtv storage

Step (6)

 Used [LowSky's tutorial]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") Steps 6, 7, 8, 9, 10, 11a

Hint: At 11a, Choose the Sound card: HDA Nvidia (Alsa Mixer) then under Select Controls, select all IEC958 controls, then close the select controls window and select the switch IEC958 only, more later...

Step (7)

At this point the sound (for me) didn't work.  So this is what I did:

Step (7a)

At LowSky's step 11a, the [FONT="Courier New"][SIZE="2"][SIZE="1"]aplay -l[/SIZE][/SIZE][/FONT] list four HDA Nvidia devices for card 1, they were 3, 7, 8 & 9.

So I guessed one of the others might work.  

***7 did!*** 

I also had to go back to the Mixer and select IEC958 1 and unselect IEC958.  

Then I restarted MythTV frontend. Went into Utilities / Setup > General. Hit next until I got to the page title is: Audio System.  I changed ALSA:plughw:1,3 to ALSA:plughw:1,7.

Screen shots are [here]("https://docs.google.com/document/pub?id=13fdcRs-fzkMg4hYKkdUvlHxCW2bu6tA0p8SkpUiCLIQ").

Many, many thanks to [LowSky]("http://ubuntuforums.org/member.php?u=330216") for all his work and his help!

And thanks to all the others on this forum without whose help I would have never finished this job.

---

### Post by LowSky on 2010-10-17
I'm glad you got it working. 

Just to mention In the frontend setup there is a few folders that will need to be pointed to your /dvr folder.

---

### Post by keepitsimpleengr on 2010-10-17
> **LowSky said:**
> Just to mention In the frontend setup there is a few folders that will need to be pointed to your /dvr folder.

I copied the mythdvd and mythtv folders and all sub-folders.  Then I changed owner to "mythtv" for all sub-folders.  This matched the owners of the original folders.  I left the original folders in place.

Then I changed directories in backend setup "directories" from "/var/lib..." to "/dvr..." for all in the list.

Did I miss one?

Thanks  :guitar:

---

### Post by keepitsimpleengr on 2010-10-18
> **winewood said:**
> I too have a 2250 and my backend has to be restarted every reboot before it works. I was understanding that the card is starting up and the backend is started before the card is ready. 

Doing what I did (which worked!!!) the restart backend after reboot does not seem to be happening.

I do not have a clue why.

Thanks for your help.

---

### Post by LowSky on 2010-10-18
> **keepitsimpleengr said:**
> I copied the mythdvd and mythtv folders and all sub-folders.  Then I changed owner to "mythtv" for all sub-folders.  This matched the owners of the original folders.  I left the original folders in place.

Then I changed directories in backend setup "directories" from "/var/lib..." to "/dvr..." for all in the list.

Did I miss one?

Thanks  :guitar:

Under the frontend, go into setup and then go into media. Make sure the folders line up with the new one your created in the backend. Basically the frontend looks for pointers for music and fanart and such. Remember that a Myhtv setup can be just a frontend and some things are done directly from there like metadata and fanart, local media directories like music and video that are not recordings.

---

