---
title: "1080 playback is not smooth"
date: 2009-10-05
forum: Mythbuntu
---

### Post by tjbron on 2009-10-05
Hi everyone! First post, so take it easy on me :) This is my first Linux project and I feel like I've gotten pretty far with the forums and wikis, but I seem to have hit a wall. Appreciate any help you can give me! Also please let me know if I can provide any more information or logs, etc.
 
First, the key issues. Then I'll give you all the details I have.
The key problems are:
 
1) Video gets choppy with 1080, and vertical lines look like zippers during fast panning. That's the best way I can describe it. (up to 720 video is fine). I have so far assumed it is a playback issue, but perhaps I could send a brief recording to someone who's system is working well to find out if the recording is bad.
 
2) In trying to troubleshoot the above, I found out I can't take a screenshot of mythtv. See attached: the black behind the terminal was actually a paused shot of a football game.
 
3) Also would like to run SPDIF (coaxial) audio. Thought that might help the CPU, but following the wiki hasn't gotten me anywhere, except more confused. They say PulseAudio is the devil (which is what I'm apparently using by default for analog), but then they start discussing how to use it. I guess I need someone to hold my hand on this one. I can't get spdif to work outside Mythtv either.
 
Ok, the details.
I started with a former HP Pavilion a1210n, (laughably sold as a "Media Center" PC). 
Due to limited slots, a Hauppauge hvr-2250 went in the one PCIexpress slot and I had to get a PCI video card for TV-out.
 
Athlon 64 3500+ 2.2 GHz 
Chipset: ATI Radeon XPress 200
Mobo:ASUS A8AE-LE
184 pin, DDR SDRAM = 512 MB (2 x 256)
HDD: 200 GB SATA, 7200 rpm
TV Card: Hauppauge hvr-2250
Graphics: NVIDIA GeForce FX 5200 256MB PCI
OS: Mythbuntu Jaunty, mythtv= 0.21.0+fixes 19961-0ubuntu8
 
Signal: Over the air only (digital).
TV: The ol' tube TV. 480i is all it needs, but I think I am forced to record the HD content as it is broadcast.
Playback setup: No deinterlacer (I want 480i). I think I am using XVMC, but I'm not positive that it's working. Never got the monochrome OSD, but they said that would be with softblend... an option I am not given under "Standard XVMC". Also, whether I select xv-blit or opengl, I curiously get this in the frontend log:
```
VideoOutputXv: Desired video renderer '' not available.
   codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
```
 
CPU runs about as shown in the screenshot on 1080 content. 50% xorg, 50% myth frontend, with a load around 2.0 to 2.6.
Here is a snippet of the frontend log I get when I play a brief 1080 recording I made for troubleshooting purposes:
```
2009-10-04 10:57:34.370 TV: Attempting to change from None to WatchingPreRecorded
2009-10-04 10:57:34.672 DPMS Deactivated 
2009-10-04 10:57:37.001 AFD: Opened codec 0x93183c0, id(MPEG2VIDEO) type(Video)
2009-10-04 10:57:37.001 AFD: codec AC3 has 6 channels
2009-10-04 10:57:37.002 AFD: Opened codec 0x95d41c0, id(AC3) type(Audio)
2009-10-04 10:57:37.002 AFD: codec AC3 has 2 channels
2009-10-04 10:57:37.003 AFD: Opened codec 0x9440340, id(AC3) type(Audio)
2009-10-04 10:57:37.005 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-04 10:57:37.005 Opening ALSA audio device 'default'.
2009-10-04 10:57:37.073 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-10-04 10:57:37.134 Mixer unable to find control PCM
2009-10-04 10:57:37.134 Mixer unable to find control PCM
2009-10-04 10:57:37.157 VideoOutputXv: Desired video renderer '' not available.
   codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-10-04 10:57:37.161 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Overlay'
2009-10-04 10:57:37.518 OSD Theme Dimensions W: 640 H: 480
2009-10-04 10:57:38.311 TV: Changing from None to WatchingPreRecorded
2009-10-04 10:57:38.314 Couldn't load deinterlace filter 
2009-10-04 10:57:38.315 The realtime priority setting is not enabled.
2009-10-04 10:57:38.415 OpenGLVideoSync()
2009-10-04 10:57:38.462 Video timing method: SGI OpenGL
2009-10-04 10:58:25.215 DPMS Reactivated.
2009-10-04 10:58:25.624 WriteAudio: buffer underrun
2009-10-04 10:58:45.659 TV: Attempting to change from WatchingPreRecorded to None
2009-10-04 10:58:45.708 ~OpenGLVideoSync() -- begin
2009-10-04 10:58:45.708 ~OpenGLVideoSync() -- middle
2009-10-04 10:58:45.709 ~OpenGLVideoSync() -- end
2009-10-04 10:58:45.922 TV: Changing from WatchingPreRecorded to None
```
 
Whew! Sorry for the long and scattered post. I spent all weekend messing with it and I am on the verge of ripping out my luxurious hair. :(
Thanks!

---

### Post by ian dobson on 2009-10-05
Hi,

I've got the feeling that you graphic card (FX 5200) just isn't enough for 1080i. The linux drivers aren't as good as the windows ones, so you may be out of luck.

If you can change the hardware about abit, try getting a NVIDIA card that supports VDPAU. VDPAU allows mythtv to use the graphic card to decode the video rather than using the main CPU.

My frontend is an underclocked C2D 5200 that runs at 1.2GHz most of the time (Even when displaying 1080i h264 videos) with only 10-20% load. I'm using a 9300 passive cooled graphic card.

Have a look here [http://ubuntuforums.org/showthread.php?t=1052130](http://ubuntuforums.org/showthread.php?t=1052130) for a discussion about PCI/VDPAU graphic cards.

Regards
Ian Dobson

---

### Post by tjbron on 2009-10-05
Ian,
Thanks for the reply.  I will start studying VDPAU now!
The discussions I've seen indicate some instability.  Have you noticed any?

---

### Post by ian dobson on 2009-10-05
> **tjbron said:**
> Ian,
Thanks for the reply.  I will start studying VDPAU now!
The discussions I've seen indicate some instability.  Have you noticed any?

For me VDPAU using the backports from jya is quite stable. I've only found one HD recording which crashes mythfrontend (it also crashes mediaplayer under windows).

Note: I only use VDPAU for HD recordings and 'xv-blit' for standard mpeg recordings as the video looks nicer to me.


Regards
Ian Dobson

---

### Post by jcmiguel on 2009-10-06
This might help for your audio quests. The ASUS A8AE-LE is actually a special board manufactured to HP, namely AmberineM-GL6E. The audio chip seems to be integrated to the ATI SB400 southbridge, according to [this site]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c00496280"). Looking at the [alsa site]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI") , it seems that you should have no problem making it work. You may find useful to have a look at what [aplay -l and aplay -L commands]("http://alsa.opensrc.org/index.php/Aplay") return. Digital pass through is a bit confusing in my opinion but if alsa is working is just a matter to set it up on the setup of Mythtv itself.
I noticed that your board has some limitations regarding Disk I/O such as support only for sata I(150). It might be worthy considering replacing this mobo into something more uptodate for 1080i or 1080p playback. Mythtv as well as any media center, will record what you are looking at and doing playback at the same time wich requires a lot of disk performance. I had tried VDPAU with both an 9300SE and the 9600GT and I assure you will enjoy having a good Nvidia card on the background for BBC HD. I didn't try the 9500 which might be enought but certainly the 9300 will not be able to use the advanced methods for VDPAU. I tried with both the patched 0.21 and the 0.22 trunk from avenard and both worked without problems with Nvidia 185.18.36.

---

### Post by tjbron on 2009-10-06
Thanks for all the great info.
 
> **jcmiguel said:**
> You may find useful to have a look at what [aplay -l and aplay -L commands]("http://alsa.opensrc.org/index.php/Aplay") return. Digital pass through is a bit confusing in my opinion but if alsa is working is just a matter to set it up on the setup of Mythtv itself.
 
I forgot to get the aplay -L output (machine is not online), but here is what it says for -l:
 
```
bronson@bronson-myth:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bronson@bronson-myth:~$ aplay -L
front:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    Front speakers
surround40:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.0 Surround output to Front and Rear speakers
surround41:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=IXP,DEV=0
    ATI IXP, ATI IXP IEC958 (AC97)
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
 

```
 
Maybe I am just doing things in the wrong order or missing a step. My receiver does sometimes show me that it is getting the handshake from the computer, but I just never get any sound. I have tried the speaker-test command, etc. with no luck even outside of myth. And yes, I have tried un-muting everything! One question - would it matter if the outer conductor on my RCA plug is being grounded by the opening in the back of the computer case? It seems like very a close clearance there.
 
> **jcmiguel said:**
> I noticed that your board has some limitations regarding Disk I/O such as support only for sata I(150). It might be worthy considering replacing this mobo into something more uptodate for 1080i or 1080p playback. Mythtv as well as any media center, will record what you are looking at and doing playback at the same time wich requires a lot of disk performance. 
 
It seems to do ok-ish to record and play at the same time except for when it starts or ends a recording while I'm watching something else. I'm sure that is one of my bottlenecks. Other good reasons to get a new mobo: 
1) I can't wake on RTC
2) It would open up the world of PCI-express graphics cards!
3) Multiple core processors
4) Better SATA
 
I was hoping to do this HTPC on the cheap using an old PC, but the 1080 broadcasts have broken my dreams. :-k
 
> I had tried VDPAU with both an 9300SE and the 9600GT and I assure you will enjoy having a good Nvidia card on the background for BBC HD. I didn't try the 9500 which might be enought but certainly the 9300 will not be able to use the advanced methods for VDPAU. I tried with both the patched 0.21 and the 0.22 trunk from avenard and both worked without problems with Nvidia 185.18.36.
 
**@Ian** - Since you have had such good luck with VDPAU, what is your graphics card setup?
 
Thanks again!

---

### Post by tjbron on 2009-10-06
I am not going to get to really work on this machine any time soon and funds are short.  As a band-aid of sorts, is there some way I could convert the 1080 mpg files down to something more palatable before watching them?  Is that what transcoding is for?  How do I do it?
 
Thanks!

---

### Post by bsntech on 2009-10-06
In regards to SPDIF output, you might check out my page here.  You need to get the PulseAudio Device Chooser and setup the default sink.  After I did all of this, I was able to get sound out of Totem and Firefox normally.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

It is also worth noting that digital setup in Karmic 9.10 is MUCH easier.  The volume control itself has an option to choose which hardware to use - analog, digital, or both analog+digital.  I changed mine to just Digital and heck - even the volume control even works as well!

So far what I've seen with Ubuntu 9.10, I'm impressed that several items that I had trouble with before are fixed - especially the digital audio thing right off the bat.  I also have  microsoft Elite for Bluetooth keyboard/mouse and it seems like it works with the new Bluetooth stack - although I do have a bug open on LaunchPad right now - where the keyboard/mouse work during the splash screen startup but quits working once the desktop loads after a reboot.  But, if you search for new Bluetooth devices and move the mouse/hit keys on the keyboard, it seems it is re=found and fixed.

---

### Post by Shibblet on 2009-10-06
I think it's your video card.  The FX5200 cannot handle the 1080 source.  Get an 8000 series (at the very least), and one that can handle "vdpau".  They won't be too expensive.

---

### Post by tjbron on 2009-10-07
> **bsntech said:**
> In regards to SPDIF output, you might check out my page here. You need to get the PulseAudio Device Chooser and setup the default sink. After I did all of this, I was able to get sound out of Totem and Firefox normally.
 
Thanks for the good info. This seems like it will be a pretty straight forward howto for the SPDIF. 
 
I also gleaned some lirc info from your blog :). One thing I've never understood about the lircrc config file (copied yours for inspiration) is how do you know what "button" names are what for your remote, and what "config" names are what for any given application? At this point, I would just be making things up and hoping they worked! BTW, I have a mceusb remote which worked great out of the box with Mythbuntu Control Center.
 
> Get an 8000 series (at the very least)
I am looking at this one since it is on sale and has a rebate and free shipping. Will this be good enough?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133245](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133245)
 
 
Thanks again for all your help!

---

### Post by larsolav on 2009-10-07
> **tjbron said:**
>  One thing I've never understood about the lircrc config file (copied yours for inspiration) is how do you know what "button" names are what for your remote, and what "config" names are what for any given application? At this point, I would just be making things up and hoping they worked! BTW, I have a mceusb remote which worked great out of the box with Mythbuntu Control Center.
 

lircd.conf is the file you are looking for. It is the file that associates a "button name" with the signals from the remote. I think it is at /etc/lirc/lircd.conf (I may be wrong).

---

### Post by tjbron on 2009-10-07
Well, I clicked the button.  A new 8400GS card is on its way.

---

### Post by Shibblet on 2009-10-08
> **tjbron said:**
> Well, I clicked the button.  A new 8400GS card is on its way.

Nice.  Once it's here, you can go to [www.launchpad.net](www.launchpad.net) to find out how to install a vdpau enabled media player.  

Or... This is what I have learned from launchpad to install the PPA in Jaunty.

Add mplayer to your software sources.
```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu jaunty main
```
then in terminal type:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 03E02400
```

If you want to add Smplayer (Which I use, and is a much better interface.)
Add Smplayer to your software sources.
```
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
```
then in terminal type:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
```

Then open up Synaptic and install them.

---

### Post by tjbron on 2009-10-14
> **bsntech said:**
> In regards to SPDIF output, you might check out my page here. You need to get the PulseAudio Device Chooser and setup the default sink. After I did all of this, I was able to get sound out of Totem and Firefox normally.
 
[http://www.bsntech.com/content/view/591/281/](http://www.bsntech.com/content/view/591/281/)

 
bsn - I started making my way thru your howto on SPDIF, but still not having any sound thru SPDIF. (The receiver does say PCM 48kHz). There are a couple of spots where I haven't been able to figure out the Mythbuntu Jaunty equivalent of your steps. For example, I can't find this on my system:
 
>  
Go to System - Preferences - Sound. In there, make sure you choose your IEC958 device for each of the items (except sound capture). Mine shows up as "NVidia CK8S with ALC655 NVidia CK8S - IEC958 (ALSA)". For the Default Mixer Tracks, change the drop-down box to your Alsa-mixer (mine shows as "NVidia CK8S (Alsa MIxer)") In the list of items, ensure "Master" is selected and close the window.

 
Also, your howto uses "load-module module-alsa-sink device=hw:0,2" and "alsa_output.hw_0_2". 
In my aplay output, it shows this:
 
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958
 
 
Should I be using 0,1 instead of 0,2?
 
Thanks for your help! :confused:

---

### Post by jyavenard on 2009-10-14
Choppy playback isn't due to the video card, but a CPU that isn't fast enough.

For the kind of content your are playing and with your 5200 you can already get hardware acceleration: set your TV playback profile to use XvMC for the decoder.

This should fix your issue.

Too bad you got a 8400gs, it isn't fast enough for the nice VDPAU deinterlacers... a fanless 9500GT is the best IMO

Re: digital audio, do not set a mixer in mythtv, uncheck that part in the GENERAL settings. Volume control for digital audio will not work that way (at least not yet, 0.23 will let you do that).

---

### Post by jyavenard on 2009-10-14
> **tjbron said:**
> bsn - I started making my way thru your howto on SPDIF, but still not having any sound thru SPDIF. (The receiver does say PCM 48kHz). There are a couple of spots where I haven't been able to figure out the Mythbuntu Jaunty equivalent of your steps. For example, I can't find this on my system:


that howto sounds very complicated to me, and certainly unecessary with a recent ubuntu distribution.

Check this guide, it's regularly updated 
[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

---

### Post by tjbron on 2009-10-14
jyavenard - thanks for the replies.  I decided to save the cash and get the 8400 because I am not using deinterlacers (480i CRT).  Hopefully that was a good assumption.  I will find out this weekend.
 
I have tried XvMC but it did not resolve the problem.  If it is my processor, then VDPAU should help even more than XvMC, right?
 
In addition to being choppy, I am seeing horizontal bars during fast panning, which I'm hoping goes away with the new card.  
 
I will check out the digital audio link from your post.
 
Thanks!

---

### Post by jyavenard on 2009-10-14
> **tjbron said:**
> 
I have tried XvMC but it did not resolve the problem.  If it is my processor, then VDPAU should help even more than XvMC, right?


your card can do full mpeg2 decoding , so in theory, vdpau shouldn't be much better for mpeg2 than what your 5200 card is already capable of

You could have spent a bit more time resolving the issue there...
But with a 480i TV, why bother trying to watch HD?

> 
In addition to being choppy, I am seeing horizontal bars during fast panning, which I'm hoping goes away with the new card.  


Make sure Xv Vsync is enabled (use nvidia-settings) , try also with OpenGL vsync (in Setup->TV->Playback), that should fix the tearing your are seeing.

---

### Post by jyavenard on 2009-10-14
> **tjbron said:**
> select xv-blit or opengl, I curiously get this in the frontend log:
```
VideoOutputXv: Desired video renderer '' not available.
   codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
```
 


hum, I should have looked closer, this is probably where your issues come from.

You have obviously a corrupted playback profile.
Go and edit it, or better, delete your playback profile and re-create one to use XvMC

---

### Post by tjbron on 2009-10-14
> **jyavenard said:**
> 
You could have spent a bit more time resolving the issue there...
But with a 480i TV, why bother trying to watch HD?

 
I pull my signal in as digital OTA.  As far as I can tell, the only way to record it with my Hauppauge hvr-2250, is in the format in which it was broadcast, which is 1080 on several channels.  Unless there is a way for me to translate my recordings down to 480, I have to play them as HD.
 
I will definately redo the bad playback profile and see where that gets me.
 
I appreciate your suggestions!

---

### Post by tjbron on 2009-10-15
> **jyavenard said:**
>  
You have obviously a corrupted playback profile.
Go and edit it, or better, delete your playback profile and re-create one to use XvMC
 
 
AHAH! Thanks to jyavenard, I made a new playback profile for XvMC and viola! The choppy playback is gone, as is the "video renderer '' not available" log entry. It stutters now and then (prebuffering pause and write audio buffer underruns, mostly during closed captioning). But the playback is generally smooth. I am confident that XvMC is now actually working because the xorg CPU usage is down from 50% to about 5%.
 
Now that the playback settings are working, I can focus on the next problem, which is still the gazillion horizontal lines during fast panning (tearing, I suppose it is called). I can capture the tearing by pausing, but any attempt to take a screenshot results in black wherever the video would have been.
 
I am pretty sure OpenGL video sync is working, as it is enabled and shows up in the log. As for jya's other suggestion (Xv vsync in nvidia-settings) I looked in the settings, but wasn't sure to what you were referring. BTW, I am using the "legacy" nvidia driver for my 5200 card.
 
I tried the opengl option in the XvMC playback profile, but it defaulted back to xvmc-blit with this message: 
>* VideoOutputXv: Desired video renderer 'xvmc-opengl' not available. *
>* codec 'MPEG2 IDCT' makes 'xvmc-blit,' available, using 'xvmc-blit' *
>* instead.*
Searching online, it looks like the apparent availability of opengl with xvmc may be a bug?
 
Again, any suggestions would be wonderful.

---

### Post by tjbron on 2009-10-15
I think my issue sounds almost like the "combing" they describe here:
[http://www.mythtv.org/wiki/Deinterlacing](http://www.mythtv.org/wiki/Deinterlacing)
 
It may not be rational to deinterlace for a 480i tube, but heck it's worth a shot.  Of course I probably don't have enough CPU to do anything fancy deinterlacing-wise on 1080.

---

### Post by tjbron on 2009-10-19
Thanks for all your help, everyone.  I guess I can mark the "1080 playback" problem as pretty much solved.  
 
In summary, I got XvMC really working by getting rid of a corrupt playback profile.  Then, I had to deinterlace before playing on my interlaced display (go fig).  Once I turned on Bob2x deinterlacing for all 1080 broadcasts, the combing/tearing was taken care of.  
 
I will probably open a new thread on my continuing digital audio conquests, etc.

---

### Post by bsntech on 2009-10-19
tjbron and all -

The HOWTO I have on SPDIF audio is more advanced than the mythtv site.  That is because I read through that HOWTO originally when setting up the digital audio, and it didn't work for me.  Getting the digital audio to work took days to finally fix.  Most of the stuff in my HOWTO is to setup digital audio so that it also works to play the Ubuntu startup sound and sounds outside of mythtv.  If you just need the digital audio to work in mythtv, ensure that in the Setup - General location, you set the audio device as "alsa:SPDIF" and the pass-through device as the "IEC958".  Then check the boxes to allow pass-through for DTS and AC3 audio.

For a note for one of tjbron's previous post which I just read, you will change that line to:

load-module module-alsa-sink device=hw:0,1
alsa_output.hw_0_1

Just exactly as you said since the device number is 1 and not 2 as it was in my case.

While my HOWTO is very long and detailed, the section on the SPDIF/digital audio is fairly short and only requires a few changes.  I compiled all of this information and put it on the blog so I can easily look back to it when changing to a PC (which I've now done and most of it is useless with Ubuntu 9.10 now and a new GeForce 8200 IGP!).

---

### Post by tjbron on 2009-10-19
Thanks bsntech - 
I started making my way thru your howto on SPDIF, but still not having any sound thru SPDIF. (The receiver does say PCM 48kHz). 
 
I can't find System/Preferences/Sound on my system, where you choose IEC958 device for each of the items. Could this be my problem?
 
 
 
I also went through the AllensDigitalAudioHowto on mythtv.org wiki with no success. For example, when I try to troubleshoot with 
```
mplayer -ac hwac3 -ao also:device=iec958=0 -vo xv -fs /myfile.mpg
```
it freezes on the first video frame and no sound is heard.
 
 
 
 
Thanks

---

### Post by bsntech on 2009-10-19
Try this line for mplayer:

mplayer -ac hwac3 -ao=alsa:device=spdif -vo -xv -fs /myfile.mpg

Do you have Ubuntu or Mythbuntu?  In Ubuntu, there should be a Places menu at the top and then to the System menu, then to Preferences and then to Sound.

Also - do you have MythTV setup with a recording in there?  If you have all of your settings in MythTV correct (with the sound output, passthrough device, etc), then it should work in there independently of the settings that I have in my blog.

You did install the Pulse Audio Device Chooser and then put this following line under the Default Sink menu and choose Other:

alsa_output.hw_0_1

---

### Post by tjbron on 2009-10-19
Thanks, I'll give it a shot.  I am using Mythbuntu, although every step of the way I have wondered why I didn't use full Ubuntu.  It seems like I've had to find or get lots of the Ubuntu pieces anyway.
 
Yes, I have been using Mythtv with analog audio for awhile.  But when I couldn't get digital audio to work, I thought I would try both with and without Mythtv.

---

### Post by jyavenard on 2009-10-19
> **tjbron said:**
>  I can capture the tearing by pausing, but any attempt to take a screenshot results in black wherever the video would have been.


It's normal that you can't do a screen capture with XvMC, would be the same with VDPAU... The video image is only on the graphic card (using colorkey)

Make sure the Xv-sync is active (in nvidia-settings) ; try also with OpenGL v-sync in the TV->Playback configuration screen

---

### Post by jyavenard on 2009-10-19
> **tjbron said:**
> 
I tried the opengl option in the XvMC playback profile, but it defaulted back to xvmc-blit with this message: 
>* VideoOutputXv: Desired video renderer 'xvmc-opengl' not available. *


It needs to have been compiled in... not sure how the mythbuntu package includes it or not

---

