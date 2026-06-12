---
title: "Nvidia 4xx fermi series &amp; HDMI sound"
date: 2010-11-12
forum: Multimedia Software
---

### Post by ARTO222 on 2010-11-12
I'm using Ubuntu Maverick (64bit) on a core i5 750 with nvidia gtx 460 1GB graphics card setup.
The card along with the drivers obtained from the &quot;additional hardware support&quot; app (nvidia-current) works the best I've experienced so far. 
There's no tearing or other artifacts on video playback even with full compiz effects on. However, there's no HDMI audio.

Googling the problem only brings up a few sites. One of them is the following forum post:
[HTML]http://ubuntuforums.org/showthread.php?t=1560288[/HTML]Most of them point to the following link:
[HTML]http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio[/HTML]On the last link the focus is on post #7.
Anyone who has any idea how to get and apply the patches mentioned in  post #7, via GIT, should feel free to post step by step instructions.

Are only 10 -20 people using ubuntu with nvidia 4XX cards currently around the world?

Aside from the GIT patches, several other simpler tweeks surfaced while researching the issue from people claiming that it solved the problem.
I tried some and they failed. Some are mentioned [COLOR=Blue][here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611810")[/COLOR].

1) Tried adding various lines to the sound configuration files. After deleting the relevant lines when there were no positive results (and rebooting each time) I started experiencing problems with desktop rendering. 
Windows appearing with no frames which cannot be moved and total loss of theme sometimes. I Have to log out and back in to get a normal desktop.

2)Upgraded to the most recent mainline kernel version ( 2.6.37-999-generic) from [COLOR=Blue][here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")[/COLOR].
That solved the issue of the card not being recognised. 
lspci -v now outputs:

```
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 2322
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fa080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel
```After this I went into sound preferences from the speaker icon and the nvidia audio device was already there and activated. I then used alsamixer and unmutted the spdif settings as many proposed. Despite all this, there still was no sound. 

3) Next suggestion was to reinstall ALSA. I used the method outlined [COLOR=Blue][here]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")[/COLOR].
This didn't work because the repository does not have a version for the most current mainline kernel.

4) Following this was alsa compilation from source. Compilation terminated with no error messages but alsa is not installed at all. I tried installing the current snapshot from [COLOR=Blue][here]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/")[/COLOR].

I forgot to read the &quot;kernels supported&quot; file which states:

```
The alsa-drivers in this package are designed for the following kernels:

 - Vanilla 2.6.29 or earlier
 - Vanilla 2.4.31 or earlier
 - Vanilla 2.2.26 or earlier

It's not guaranteed that they work with any newer version than above
or modified kernels by distributors.
```Apparently, the bleeding edge alsa source version does not even support the stock maverick kernel.

5) I updated the nvidia-current drivers to the latest version from ubuntu-x-swat ppa while running the latest mainline kernel (2.6.37-999-generic). 

This updated the drivers but now when I switch to the older kernel version (2.6.35-22-generic) via the grub menu X wont start because the kernel module for the updated drivers was not installed. 

When I tried installing from the command line while using 2.6.35-22 I got a &quot;drivers are already in the most current version&quot; and so I still can't start X with the old kernel (where ALSA works).

So now I can boot with 2 kernels.
With 2.6.35-22 I cannot start X. Alsa works, but it can't see the nvidia sound device.
With 2.6.37-999 I can start X but I have no ALSA and the system doesn't recognize ANY sound device.

Is there a way for me to roll back or install the updated drivers with the 2.6.35-22 kernel short of reinstalling the entire system?
How can I locate and remove all files installed after compiling ALSA?

Generally in my experience with Linux drivers, alot of trouble can be caused when people suggest right away installation/re-installation from packages or source
without first specifying what software/configuration files/libraries need to be removed and how. I'm saying this because previously I've been using ATI
graphics cards, both with the open source and proprietary drivers and the standard commands do not properly remove everything so re-installation
can proceed without conflicts.

So before suggesting software installation one should specify what if any software needs to be removed and how, or state simply that a new install
will overwrite any existing files without problems.

Has anyone got HDMI sound working with fermi cards?
Anybody know how to apply kernel & alsa patches from GIT?
Could someone from the community or preferably NVIDIA simply patch ALSA so we can install and use it with some mainline kernel version?

Thanks

---

### Post by ARTO222 on 2010-11-13
Any GIT gurus out there that can help?  
How to do what's in post #7  from the following link: 
[HTML]http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio  [/HTML]

Thanks.

---

### Post by CMDR:ZOD on 2010-11-15
Hey ARTO222,

Ive got 3 480 gtx's in sli and the audio one them worked right from first boot of maverick. Are you using the hdmi adaptor or are you using the mini hdmi out? I use the mini hdmi out and when I am not fighting with other audio problems (other cards) it works pretty well, and with obvious delay when first used after boot or a while since audio has played.

---

### Post by ARTO222 on 2010-11-16
Thanks for the reply CMDR:ZOD.

I was offline due to unrelated hardware problems.

HDMI sound is now working, but I'm not sure I can reproduce this on a fresh install, so
I can't mark this thread SOLVED just yet.

As previously mentioned after initial ubuntu and propriatery nvidia driver installation, the
audio devices of the gtx 460 where not [FONT=Verdana]recognized[/FONT]. They only appeared after installing the latest mainline kernel.

I have the following two driver related PPAs enabled on my system:
1) _[ppa:ubuntu-audio-dev/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")_ (alsa, sound)
2) _[ppa:ubuntu-x-swat/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")_ (graphics drivers)

I can't vouch for the exact order in which I performed the following, but as I recall:
1) booted into 2.6.37-999-generic
2) ```
sudo apt-get remove --purge nvidia-current nvidia-setttings
```3) After enabling the PPAs:
```
sudo apt-get dist-upgrade
``` because the simple install commands did not work.

4) followed the steps from the**_[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")_ **[FONT=Verdana]to uninstall & reinstall alsa:[/FONT]
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```5) tried compiling ALSA  from source because the previous step didn't solve the problem.

Several reboots and a few days later:

6) booted into 2.6.35-22-generic
 from the command line I gave:
```
sudo apt-get remove --purge nvidia-current nvidia-settings
sudo apt-get dist-upgrade
```7) checked sound preferences and saw the nvidia audio device listed and activated. I then checked for sound on a video played by VLC. Sound came on only after I activated "ALSA" from VLC preferences.

Today I booted into 2.6.35-22-generic (the speaker icon is grayed out and alsa is not installed in 2.6.37-999-generic) but I had to go into sound preference and manually
activate GF 104 High Definition Controller because the settings from yesterday were not
made persistent for some reason.

I used both DVI to HDMI & the mini HDMI connector previously, but since I got sound on
the DVI to HDMI I've kept it on and haven't retried the mini HDMI. But I expect it should work.

I don't know which step exactly got sound working. I also noticed a new ALSA build posted on the PPA. Maybe that did the trick.

What I'd like to do (and many others I reckon) is to reinstall ubuntu, update, enable the PPAs for the latest drivers, install them and have HDMI audio working.

If anyone can untangle the mess and write up a guide it would be much appreciated.
I'll experiment when I have time and maybe hit upon the exact commands to get all this working from scratch.

---

### Post by my92agsr on 2010-11-16
I am going through the same problem.  Gtx 470 on AMD x4 phenom 955.

I tried downloading the new kernel headers and I couldn't start X under the newest one.  I got it working at some point without the nvidia drivers, but it defeated the purpose as 1080p was no longer an option.  

I'm back to the main distro 10.10 kernel headers, and now Ubuntu will not recognize my HDMI out for sound, as in it doesn't even appear under the output options.  When I got it working temporarily under the new kernel headers, there was a completely different tab for my nvidia card in Alsa; that tab only says Nvidia ID10 in this current, but stable not working kernel.  

Any help?

---

### Post by my92agsr on 2010-11-17
Ok. I figured it out!

This is what I did:

I'm in kernel 2.6.35-22.  I added the Repository for Alsa dev updates and updated Alsa, outlined [here.]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

Rebooted.
Came back in and the sound out option finally recognized my Gtx 470's HDMI out. I selected it, nothing happened.

I ran VLC.  Selected Audio option in preferences.  Selected Alsa output.  Then, instead of Device: Auto, I selected "HDA NVidia:HDMI 0 (hw:1,7).  Now there is audio via HDMI in VLC only.

I'm very happy with the progress.  Alsa mixer however does not seem to fully recognize my video card HDMI output.  In alsa mixer, the two tabs are: VIA VT1828S (my onboard sound) and Nvidia GPU 10 HDMI/DP.  On the Nvidia Tab there are no sliders or anything.  Just in the bottom box four things to check or uncheck, all labeled IEC958.

I would like to get audio streaming via Hulu and other streaming sources in Chrome or firefox.  Anyone know how to get that working from here?  Thanks in advance.

Is there a way to specify in Alsa which HDMI audio device to use like you can in VLC? the (hw:1,7) device.  All boxes in alsa are unmuted, too.  So close...

---

### Post by my92agsr on 2010-11-17
So, basically, does anyone know how to set the output to card 1, device 7?

Edit:  Figured it out. Edit Alsa conf as explained here:[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Set_the_default_sound_card](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Set_the_default_sound_card)

Now it all works over HDMI.  If I want to use my computer speakers I just have to edit the CONF back.  Perfect for an HTPC, perhaps I'll hook PC speakers up to different comp.  Thanks for starting this thread, it got it all going for me.


So, for anyone struggling to figure out how to get HDMI out audio in FERMI cards, this is what I did:

Updated Alsa files using PPA above.  Then updated Alsa-lib using synaptic to dev library. I used VLC to find out which card AND device is the true HDMI audio out, then edited the Alsa conf as explained in the above link.  Hours of work, but not it will only take 2 minutes to do it now that we know.

---

### Post by Tavis on 2010-11-19
I still have the same problem I was having a couple of months ago.  I've installed all of the updates mentioned above, and dmesg shows a lot of HDMI audio messages, and alsamixer shows my card.  But alsa player just hangs:

tavis@baru:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

[and then nothing happens....]

Also, VLC freezes when I click on Tools->Preferences->Audio

Any ideas?

Thanks,
Tavis

---

### Post by CMDR:ZOD on 2010-11-20
Tavis, I have the same problem as you do. When I have my supreme fx x-fi soundcard enabled all my audio is broken. Have tried many,many, things to fix it but no luck yet. The closest I have come is with the 2.6.35-22 kernel with the audio PPA's enabled. It will still freeze audacious whenever that program tries to play audio.

If you do have an onboard soundcard, try disabling it. Thats what worked for me. I believe this issue has something to do with multiple cards (the supreme fx card and nvidia sound) using snd-hda-intel as the driver. 

You should have snd-hda-codec-nvhdmi loaded as a kernel module for the audio to work. With my other soundcard enabled, snd-hda-codec-nvhdmi will not load, although snd-hda-codec-hdmi will. I have not had any success trying to manually load this module either. I would really like to have this other soundcard enabled so I can use txppm to connect my walkera rc model heli controller to fly rc sims on the computer for the winter.  Any help would be greatly appreciated.

---

### Post by efflandt on 2010-11-21
I just got a GT 430 which is at the bottom of the 4xx series, but wasn't sure if I had enough power for a hotter one (I think my OEM psu is 375 watts).  It is so new that **lspci** does not even show its model, but video works fine with nvidia 260.19.21 that I had already installed from x-swat.

However, no NVidia HDMI devices showed up in **aplay -l**, and **alsamixer** said no controls for it.  So I followed the link my92agsr provided to install alsa modules from the ppa.

After reboot 4 NVidia HDMI devices showed up, and I unmuted them all in alsamixer, but only one of them worked:```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav
```So with the regular Maverick 64-bit kernel, the only thing I needed to do besides the nvidia and alsa ppa's was this in /etc/pulse/default.pa:

```
load-module module-alsa-sink device=hw:1,9
```The only thing strange is that the speaker test in Sound Preferences does not work for HDA Nvidia in "Hardware" tab, and in "Output" tab I have an extra device (**HDA NVidia** works on HDMI, **NDA NVidia Digital Stereo (HDMI)** does not).

So for Rythmbox or flash, I can select **Internal Audio Analog Stereo** for that or **HDA NVidia** for HDMI from "Sound Preferences" and either one works.

---

### Post by CMDR:ZOD on 2010-11-21
efflandt, thank you so much!! I ended up breaking audio so i did a fresh install of maverick, and did exactly as you said in your post and finally I got my x-fi and nvidia hdmi audio working!!  ;) I did notice the new device in the sound menu, which is the one I need to use for audio. Anyways now I gotta reinstall Sid Meiers Alpha Centauri and Ut 2004 and the rc heli programs that work on the mic in of the x-fi card. Wish Me Luck!

---

### Post by RaZoR1394 on 2010-11-22
I've tried some tricks to get sound to work on both my computers running Zotac GTX460 with 1 HDMI, 1 DP and 2 DVI-I.

I've tried many mainline kernels and also ubuntu audio dev ppa.

On the second computer I get very garbled sound when playing a mp3 track with aplay. It sounds like some kind of com radio having interference.

On the second computer I also get noise when entering:

```

speaker-test -D plughw:0,7 -r 44100

```

So I added

```

pcm.!default {
      type plug
      slave.pcm {
              type hw
              card 0
              device 7
      }
 }

```

to /etc/asound.conf just like according to the Arch Linux guide but it does still not give me sound.

```

aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav

```

This outputs "CENTER" out of the center speaker so I guess I'm close.

I've also disabled the inbuilt ALC chipset.

edit:

I got sound of the second computer using Grooveshark in Google chrome and an Enigma track. Now I need to see why the login sound isn't working and why I don't get any sound at all with the first computer.

---

### Post by jester13rok on 2011-01-20
To get HDMI to work with my Nvidia GTX460 card and ubuntu 10.10:

-I installed the latest drivers for NVidia
NOTE: next step make sure you reinstall the ubuntu-desktop or xubuntu-desktop
-Removed the ALSA Drivers per the link [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 
-Reinstalled ALSA Drivers ...and ubuntu-desktop
-Rebooted
-Ran alsamixer, had to enable 7, 3 didn't work.

good to go, thanks for the other posts really helped

After getting my hdmi working, I noticed the sound was poor and twangy  I did some research and after some trial and error I edited my /etc/pulse/default.pa and forced static call to the alsa drivers:
load-module module-alsa-sink device=hw:0,7

Also in my bios I disabled the mobo intel sound chipset.  Then I had to go back to system-preferences->sound and set my output to the non-HDMI one (I know counterintuitive)

w00t!
J

---

### Post by lidex on 2011-01-21
What are you guys getting in pulse audio volume control (pavucontrol) as far as controlling your levels?

---

### Post by tweakt on 2011-01-23
I'm generally not a fan of "remove and reinstall xyz" as that isn't really a solution. I'm posting what I've found to work here in the hopes that it might help someone else in my position and lead to a more complete fix.

Mainboard w/Intel HDA audio
Nvidia GTX 470 with HDMI and DisplayPort outputs

Connections
-----------
HDMI->HDTV->Receiver (via TOSLINK)
DisplayPort->LCD Monitor
HDA Intel SPDIF Out -> Desktop Speakers


Ubuntu 10.10
kernel: 2.6.35-24-generic x86_64

amixer info:

```
Card hw:0 'Intel'/'HDA Intel at 0xf7ef8000 irq 76'
  Mixer name	: 'Realtek ALC889'
  Components	: 'HDA:10ec0889,104383c0,00100004'
  Controls      : 36
  Simple ctrls  : 21

Card hw:1 'NVidia'/'HDA NVidia at 0xfbbfc000 irq 34'
  Mixer name	: 'Nvidia GPU 10 HDMI/DP'
  Components	: 'HDA:10de0010,10de0101,00100100'
  Controls      : 16
  Simple ctrls  : 4
```
 
In Pulseaudio sound preferences, under 'Hardware' tab, i have:

```
GF100 High Definition Audio Controller
1 Output
Digital Stereo (HDMI) Output

Internal Audio
1 Output
Digital Stereo Duplex (IEC958)

```


Initially, selecting the HDMI out gave no sound. I fiddled with it for a while but couldn't get any output. Then I took a look at alsamixer. If I run alsamixer on the HDMI device (on my system, card 1):

```

alsamixer -c 1

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                  F1:  Help               &#9474;
&#9474; Chip: Nvidia GPU 10 HDMI/DP       F2:  System information &#9474;
&#9474; View: Playback                    F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF 1                    Esc: Exit               &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;              &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9474;
&#9474;              &#9474;MM&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;              &#9474;
&#9474;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9474;
&#9474;             S/PDIF <S/PDIF 1>S/PDIF 2 S/PDIF 3            &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9474;                                                           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

And it turns out, if I turn on "S/PDIF 1", then I can get clear sound output to my TV by  running the following:

```
pasuspender -- aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
```

Now, once I turn on "S/PDIF 1" on the HDMI card, I also get sound through PulseAudio when I select the HDMI output, but it's horribly distorted (it sounds like a Signed/Unsigned sample mismatch).

I would love to make PulseAudio play nicely (pun intentended) with my HDMI out via Alsa. Major kudos to anyone who figures out what tweaks are needed to fix the audio format issue.

---

### Post by fooman on 2011-03-16
> **my92agsr said:**
> Ok. I figured it out!

This is what I did:

I'm in kernel 2.6.35-22.  I added the Repository for Alsa dev updates and updated Alsa, outlined [here.]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

Rebooted.
Came back in and the sound out option finally recognized my Gtx 470's HDMI out. I selected it, nothing happened.

I ran VLC.  Selected Audio option in preferences.  Selected Alsa output.  Then, instead of Device: Auto, I selected "HDA NVidia:HDMI 0 (hw:1,7).  Now there is audio via HDMI in VLC only.

I'm very happy with the progress.  Alsa mixer however does not seem to fully recognize my video card HDMI output.  In alsa mixer, the two tabs are: VIA VT1828S (my onboard sound) and Nvidia GPU 10 HDMI/DP.  On the Nvidia Tab there are no sliders or anything.  Just in the bottom box four things to check or uncheck, all labeled IEC958.

I would like to get audio streaming via Hulu and other streaming sources in Chrome or firefox.  Anyone know how to get that working from here?  Thanks in advance.

Is there a way to specify in Alsa which HDMI audio device to use like you can in VLC? the (hw:1,7) device.  All boxes in alsa are unmuted, too.  So close...

hey,  i know this is an old thread,  but just wanted to say that adding the alsa repo, then re-installing/updating alsa fixed my problem of audio out to my 50" plasma tv from my gtx480.  :P

i now get audio output via the gtx480's min-hdmi to the hdmi of the tv.  i am using smplayer and had to change the audio output driver to: *alsa (1.7 - HDA Nvidia)*

all that i had to do was:  add alsa repo, update sources, update alsa, and change the output driver in smplayer.  i did not have to edit or create any configuration files whatsoever.  just ran 3 commands in a terminal (per the link provided by my92agsr in the post i quoted above):

```
Adding the ppa: 

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa

update sources:

sudo apt-get update

Install the linux-alsa-driver-modules package:

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```then in smplayer, i changed the output driver by going in the toolbar to: options > preferences > general > audio tab 

change the "output driver" to: *alsa (1.7 - HDA Nvidia)*, click "apply", then ok and BAM....it was working!! \\:D/ 

thanks to my92agsr for that very helpful post!

---

