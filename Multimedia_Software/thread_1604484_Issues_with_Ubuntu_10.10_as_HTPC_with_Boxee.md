---
title: "Issues with Ubuntu 10.10 as HTPC with Boxee"
date: 2010-10-24
forum: Multimedia Software
---

### Post by natanel on 2010-10-24
Hi

I have been tring to build my own HTPC
using foxxconn NetBox-nT330i [[COLOR="Blue"]link[/COLOR]]("http://www.foxconnchannel.com/product/Barebones/NT330i/index.html") using the HDMI output

LG scarlet 37 inch (connected with HDMI to the computer)

installed Ubuntu 10.10 32-bit (as from first reading understood the Ubuntu have better driver for the Nvidia ION display card
and Boxee the windows)

also updated to the newest Nvidia drive 260.19.12

some problem I have:
1)I can't output the sound through the HDMI cable.
in GUI sound setting, if setting to internal speaker I can get sound from the internal computer speaker.
changing it to any combination it have of HDMI analog or digital give me no sound. I read there is an issue with sound from HDMI using Ubuntu but can not really find a solution

2)Still after update and using ION hardware acceleration I get a movie (720p) with a annoying small jump in frames (every few seconds).
I can see that the ION have no problem and CPUs are very low load (below 20%).
not really an expert but from reading it may be connected to some V Scan (black or something?)
and maybe to Compiz configuration
any help will be great

3) some forums mention Ubuntu is poor in HTPC as it need many configuration.
so if moving to win7 (as some suggested), does it all work? 
does win7 support ION hardware acceleration

4) any one out there using setting like this?

those are some issues I solved.

first issue was:
trying several output resolution, the one that was suitable (and good looking) for the TV was a little bit big, so the border of the desktop where cut.
after some reading, understood that this is scanning problem of the TV so changed the TV scanning from 16:9 to "just scan"
this work great but needed every time the computer re-start

Second issue: when running 720p in Boxee I got a very bad jumping movie.
I checked the Boxee debug option and found out that the XBMC-CPU is over loaded (170%).
so even though the drive is updated (using Ubuntu GUI hardware update) the Ubuntu is not using the ION hardware acceleration.
this took me some time but after reading that there is a problem with Nvidia driver in full screen. I downloaded and install the latest driver 260.19.12 
now the XBMC-CPU load is down to 30%

still have the problems
can any one help?

---

### Post by P4man on 2010-10-24
> **natanel said:**
> 
some problem I have:
1)I can't output the sound through the HDMI cable.
in GUI sound setting, if setting to internal speaker I can get sound from the internal computer speaker.
changing it to any combination it have of HDMI analog or digital give me no sound. I read there is an issue with sound from HDMI using Ubuntu but can not really find a solution

Well, is this a problem with ubuntu (/pulse) or the app you are using (boxee and/or XBMC)? If you click the sound preferences in the top right panel, go to  hardware  and you select the hdmi output and click "test speakers", do you get sound over HDMI?

> 2)Still after update and using ION hardware acceleration I get a movie (720p) with a annoying small jump in frames (every few seconds).

Thats sort of hard to say :S. Does it happen in all media players, or just some? Have you tried disabling desktop effects (no point in a HTPC anwyay) and experiment with vsynch setting in nvidia-settings ?

> 3) some forums mention Ubuntu is poor in HTPC as it need many configuration.
so if moving to win7 (as some suggested), does it all work? 
does win7 support ION hardware acceleration

Yes win7 also supports purevideo with ion. Is it better for HTPC than ubuntu? Well, if you have 15 years experience with windows and zero with linux, you may  have it set up faster since both boxee and xbmc are available for either platform. 

OTOH, with ubuntu you also get options like mythtv and endless options that you cant do with windows (to name just one, like I have,  XBMC running in one X session on the TV controlled by remote and another independant session on a regular monitor with keyboard and mouse in the other room where the kids can play games).

> 4) any one out there using setting like this?

Yep, sort of. Not based on ion though, just a regular PC tucked away in the playing room :)

---

### Post by natanel on 2010-10-24
> **P4man said:**
> Well, is this a problem with ubuntu (/pulse) or the app you are using (boxee and/or XBMC)? If you click the sound preferences in the top right panel, go to  hardware  and you select the hdmi output and click "test speakers", do you get sound over HDMI?

this is a problem with Ubunut no sound as you describe
sound preferences->hardware->hdmi output->"test speakers" = np sound at all.

> **P4man said:**
> Thats sort of hard to say :S. Does it happen in all media players, or just some? Have you tried disabling desktop effects (no point in a HTPC anwyay) and experiment with vsynch setting in nvidia-settings ?

this happen in all media players.
can you please tell me how can I disable all the desktop effect in one place?
I will re-check it with all desktop effect disabled

> **P4man said:**
> Yes win7 also supports purevideo with ion. Is it better for HTPC than ubuntu? Well, if you have 15 years experience with windows and zero with linux, you may  have it set up faster since both boxee and xbmc are available for either platform. 

did not gave up yet

---

### Post by P4man on 2010-10-24
> **natanel said:**
> this is a problem with Ubunut no sound as you describe
sound preferences->hardware->hdmi output->"test speakers" = np sound at all.

To be clear, your motherboard does have HDMI out, and not DVI out with a DVI to HDMI adapter? Because those dont support sound.

If you have HDMI outm perhaps have a look here:
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)

I would strongly recommend first trying the drivers proposed by "additional drivers" in system > administrion > additional drivers rather than downloading from nvidia.

```
this happen in all media players.
can you please tell me how can I disable all the desktop effect in one place?
I will re-check it with all desktop effect disabled

```

System > preferences > appearance > desktop effects. Set it to none. But more likely its a vsync issue you can cure in system > administration > nvidia xsettings.

---

### Post by xbmcoholic on 2010-10-24
I have no sound either on my Aspire Revo R3610 after a recent update in Karmic.  I spent all last night trying to fix it with no success.  Today I've done a fresh install of 10.10 and still can't get sound to work.  All the threads about ION + HDMI sound I've found so far, haven't helped.  I've got the new nvidia 260.19.06 driver installed and I've checked alsa-mixer and the pulse-audio sound preferences - everything checks out the same as when it was working - Hardware is set to "Digital Stereo (HDMI) Output + Analog Stereo Input".  Speaker tests fail.

I've tried messing around with aplay but I get "aplay: main:654: audio open error: Device or resource busy"

---

### Post by natanel on 2010-10-25
P4man thanks

closing desktop effect helped with the movie small jumps
I did not investigated way but I think it involoe vscan of both the X setting and the compiz setting

solving no sound from HDMI was solved using this link
[[COLOR="RoyalBlue"]http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240 [/COLOR]]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
doing PulseAudio Configuration part

any way the updating of the nvidia driver was must to solve the xbmc-cpu overhead. the official drive version just did not do it.

thanks

---

### Post by JeffPH on 2010-11-01
hi natanel,

I cant seem to output my video via hdmi,  i will see linux post but when it reaches desktop i have no signal already in my hdmi according to my tv.  I also use the 37" lg lcd and same nettop box by foxconn. when i use the vga input of the tv it works.

Can you tell me how u did it. i mean can u paste me your xorg.conf here.  i really am lost on this.

Thanks for your help.

PS can you try using both dvi and hdmi out at the same time too? i cant  seem to do that too.

---

### Post by dregsd on 2010-12-07
This is what I did to make boxee work on Ubuntu 10.10 Maverick:

[Drivers]
* Install the nvidia drivers from restricted drivers option on ubuntu.

[Library]
* Install libvdpau and nvidia-185-vdpau using apt-get.

```
sudo apt-get install libvdpau1 nvidia-185-libvdpau
```

[HDMI Sound]
* Select HDMI Output on Sound Preferences. 

* Unmute S/PDIF 1
  - In terminal, run "alsamixer"
  - Go to the right to you find the "S/PDIF", hit "M" to mute it. If you have more then one of the S/PDIF's, mute them all.

[Boxee Settings]
* UNCHECK Enable hardware acceleration if possible.
* Select VDPAU
* Always enable Sync to vblank.

---

### Post by dregsd on 2010-12-07
> **JeffPH said:**
> hi natanel,

I cant seem to output my video via hdmi,  i will see linux post but when it reaches desktop i have no signal already in my hdmi according to my tv.  I also use the 37" lg lcd and same nettop box by foxconn. when i use the vga input of the tv it works.

Can you tell me how u did it. i mean can u paste me your xorg.conf here.  i really am lost on this.

Thanks for your help.

PS can you try using both dvi and hdmi out at the same time too? i cant  seem to do that too.

I got mine to work on my Panasonic LCD. Are you using Ubuntu maverick for the OS?

---

