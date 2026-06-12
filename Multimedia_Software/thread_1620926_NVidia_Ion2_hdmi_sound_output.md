---
title: "NVidia Ion2 hdmi sound output"
date: 2010-11-13
forum: Multimedia Software
---

### Post by zAPPzAPP on 2010-11-13
I am running a fresh install of ubuntu 10.10 on a zotac zbox with an nvidia ion2. It is connected to a tv over hdmi.  
I have installed the latest Nvidia drivers from their homepage.

Currently I am trying to get audio output working over hmdi.  

Following this thread ([http://ubuntuforums.org/showthread.php?t=1552250)  ]("http://ubuntuforums.org/showthread.php?t=1552250")I have determined that my audio output is in fact working (in theory).

The correct output device for me is card 1, device 1 which equals hw:1,7 .

I can can output sound by doing
```
aplay -Dplughw:1,7 /path/to/file.wav
```I can also for example watch a movie with sound if I start mplayer from the command line and give an explicit order to use that sound device, like described here: [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
```
mplayer -ao alsa:device=hw=1.7 moviefile.mkv
```[B][SIZE=2]So, I do know what my device is and it does work. This is where I'm stuck. How do I set Ubuntu to use this device as standard output?
[/SIZE][/B] 
I have also read the sticky thread in this subforum, where it says:
> [LEFT]_**[SIZE=3]Configuring default soundcards / stopping multiple soundcards from switching[/SIZE]**_[/LEFT]
      
[LEFT][SIZE=2]**Note: This section assumes that you have installed each soundcard properly.** [/SIZE][/LEFT]

[LIST]
[*][LEFT][SIZE=2]In a shell, type      
     [/SIZE]```
cat /proc/asound/modules 
```[/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]This will give the the  name and index of each soundcard you have currently. Make a note of the  names, and decide which one you want to be the default card.[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]Now type 
    [/SIZE]```
 sudo nano /etc/modprobe.d/alsa-base 
```[/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]At the very end of the  file, add the following (assuming you have 3 cards with module names A, B  and C and you want to have them in the order CAB)[/SIZE][/LEFT]
[/LIST]
    
 ```
options snd-C index=0[LEFT]options snd-A index=1
options snd-B index=2[/LEFT]
 

```Doing this
```
[SIZE=2]cat /proc/asound/modules[/SIZE]
```returns 2 entries for the Intel soundcard (thats the internal soundcard for analog audio, the wrong one), but NVidia does not show up.

Any ideas?

---

### Post by M.a.d on 2010-11-15
Perhaps this thread holds the solution to your problem?:

[http://ubuntuforums.org/showthread.php?t=1592944](http://ubuntuforums.org/showthread.php?t=1592944)

---

### Post by zAPPzAPP on 2010-11-15
I have solved this in the meantime, although it might not be the optimal solution.
If anyone has ideas for improvement, feel free to post. ;)

**Anyway first off here's what I did:**
- On a fresh install of Ubuntu 10.10
- install the newest NVidia driver from the NVidia homepage. This is done by creating a blacklist for all unwanted drivers first, removing the old drivers (anything with nvidia in name), stopping X server, then running the install skript. There are plenty of guides on this step out there, for example here: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html) 
- reboot
- figure out which card/device combination is giving out hdmi sound (described in the thread I linked in my first post)
- using this information, create a .asoundrc file in your home folder ```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm dmixer
}
```(Source: [https://bbs.archlinux.org/viewtopic.php?id=100759](https://bbs.archlinux.org/viewtopic.php?id=100759))
  pcm "hw:1,7" is where you put your working hdmi card/device combo. 1,7 for me.

Now to make it work I had to reboot again.
At this point hdmi output was only kind of working. 

```
aplay some_sound.wav
```This would play the file over hdmi. Crystal clear sound, no problems.

All other applications I tested also gave out sound BUT it was in a really low quality. Sounded kind of like if you choose a very low sample rate in a voice com program.
But the sample rate was ok.

For example, when using mplayer to play an mkv file:
If I stated alsa as audio out (hw:1,7 being my hdmi device)
```
 mplayer -ao alsa:device=hw=1.7 some_file.mkv

```No problems, crystal clear sound.

```
mplayer some_file.mkv
```Low quality, screechy sound.

Now mplayer gives out some information in the console while playing the file. It shows that in both cases, codecs, sample rate etc.. everything was exactly the same. 
The only difference: the good quality stated alsa as sound output, while the bad one stated pulseaudio!

So: Somewhere in between alsa (where my sound was still perfect) and pulseaudio my soundstream got hit with a 1900s gramophone filter. Because every Ubuntu app accesses the sound over pulseaudio the sound was horrible all over the place.
I dont understand the whole mess with alsa<->pulseaudio, so I can't even begin to guess why and where that happens...

**My solution and the final step:**
- uninstall pulse audio
```
sudo apt-get remove --purge pulseaudio
```(maybe you shouldn't purge it, but I was a bit annoyed after 3 days of trying so..)
- reboot

Done. 
With this, I have now audio working systemwide for me, I have set up XBMC on top of Ubuntu and it works there as well.
With dmix in my .asoundrc I can also play multiple sound files at once (I had no dmix first, but then one app would grab the audio device at some point, crash/close down ungracefully block it forever, leaving me without sound once again...).


There is one minor audio bug still, concerning XBMC:
If I choose to go into suspend mode (the save to RAM mode) from XBMC and then come back, I dont have sound within XBMC. I need to go back into Ubuntu and play a sound with some random app first. After this, my sound in XBMC is back.
This is really not important though, I just close down XBMC and use ubuntus suspend instead.

---

### Post by TombstoneX on 2010-11-21
zAPPzAPP

Your post is great, and i do have single sound working on Ubuntu for whichever device grabs it first. Example : XBMC playing a movie, however if at the same time i go to youtube and try to play a video, i have no sound. I take it this is where the dmix comes into play, i have been reading the [Dmix wiki]("http://www.alsa-project.org/main/index.php/Asoundrc#dmix") but am very confused. Would you be able to share your ~/.asoundrc file with us?

---

### Post by zAPPzAPP on 2010-11-22
I have added the contents of my .asoundrc.
If you want this to work systemwide and not user specific, then put it into asound.conf.
But this being a htpc I didnt neeed that.
--------------
Not related to hdmi:
To make the system really work as a htpc with xbmc here are some additional things that may come in handy
- remove tearing: I had some tearing when playing videos. To get rid of it
      install nVIDIA VDPAU ```

sudo apt-get install libvdpau1 nvidia-185-libvdpau
```reboot and activate VDPAUin xbmc ([http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide))
   and disable all desktop effects
-disable passwort protection when coming back from power save modes and make he box wake up on USB signals ([http://type.appstairs.net/?p=99](http://type.appstairs.net/?p=99))

---

### Post by tjones00 on 2010-12-13
Awesome work zAPPzAPP

I hope you don't mind but I added links to this post to my original Ion2 post. The whole dmix hw/slave thing was the can of worms I didn't want to get into since I only used plughw for my needs.

Did you make any headway on changing or testing the Nvidia hdmi pcm alias so you could just select hdmi:NVidia vs hw:1,7 for audio needs?

I imagine your dmixer setup with the /usr/share/alsa/alsa.conf NVidia redefinition would fix this.

/usr/share/alsa/alsa.conf for hw:1,7

> 
change this:

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

to this:

defaults.ctl.card NVidia
defaults.pcm.card Nvidia
defaults.pcm.device 7Note to anybody setting up this type of dmixer if you don't know what rates etc to use for your hardware just look at the eld data.

---

### Post by lamprakisa on 2011-04-03
Your solution works fine with Nvidia GTS 450 also.

I had to install audiohacks ([https://launchpad.net/~dtl131/+archive/ppa]("https://launchpad.net/%7Edtl131/+archive/ppa")) to restore volume control.

---

### Post by zAPPzAPP on 2011-07-28
The obvious flaw in this solution is, that pulseaudio is "the future".
Now that the pulseaudio is in ubuntu as a default, i fear applications will start to depend on it and soon not offer alsa support as an alternative. Because pulseaudio has streams and programmers love streams. ;)

I didn't risk any updates of ubuntu or xbmc because of this. Never touch a running system and all that.

But I hope there will be a time and ubuntu release, that gets this working out of the box without modifications with pulseaudio. When that is the case, please write me a reminder. Until then, no upgrades for me.

---

### Post by waxbell on 2011-11-13
I found another solution on the XBMC forums when you have bad sound over the HDMI. I am using Ubuntu 10.04 LTS 64-bit on an ASUS AT5IONT-I.

I had to install nVidia drivers and upgrade the ALSA. I also created the .asoundrc in my home folder which made the sound work system wide, but the sound sounded really bad. So instead of deleting pulse audio I added "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2" to /etc/modprobe.d/sound.conf

This worked for me and I read it at: 
[http://wiki.xbmc.org/index.php?title=HOW-TO:Set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO:Set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

My setup is specific to the ASUS AT5IONT-I and there are setups for other kinds of systems. 

Hope this helps someone.

---

