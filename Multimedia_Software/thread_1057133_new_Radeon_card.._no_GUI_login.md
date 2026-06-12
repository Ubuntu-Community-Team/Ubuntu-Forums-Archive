---
title: "new Radeon card.. no GUI login?"
date: 2009-02-01
forum: Multimedia Software
---

### Post by zim2dive on 2009-02-01
Facing a bug (being worked on by nvidia with no ETA) with my onboard nvidia 8200 IGP, I bought a bottom-end ATI 3450 to get me thru the short-term ($20 after rebate... hard to argue with that)...

so I installed the card, booted my machine, and connected my HDMI connection to the new ATI connector.

EDIT: ok, some progress... following some ideas from [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910) I did > sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv and as part of this I copied my xorg.conf back in place (aticonfig seemd to want something to start from). so now I have a GUI, and the screen resolution claims it is 1920x1080, but I have a 2inch black border around everything, whereas I had full-screen with nvidia... is there an ATI config panel similar to the Nvidia X config panel?

---

### Post by markbuntu on 2009-02-01
There is the Catalyst Control Center which is the configuration gui for fglrx. Many displays use overscan which is why you have the border. try aticonfig --help to see the options for tv output.

---

### Post by zim2dive on 2009-02-01
> **markbuntu said:**
> There is the Catalyst Control Center which is the configuration gui for fglrx. Many displays use overscan which is why you have the border. try aticonfig --help to see the options for tv output.

Thanks! I don't seem to have that in my GUI menus anywhere... maybe b/c I did my install from the command line.. so in Synaptic I just did a reinstall of fglrx-amdcccle and looked thru the file list and see it at /usr/bin/amdcccle. .which does launch... still not automagically inserted to GUI menus (the nvidia config panel was), so no biggee, I can do that.

**_remaining Issue #1_**
at the command-line I did > aticonfig --tv-geometry=100x100+0+0 and rebooted but I still have the (overscan) border.. so then I tried > aticonfig --tv-overscan=off and rebooted.. still no dice (I am connected to the HDMI output)

> aticonfig --tv-info says "The TV is not connected" ??

I also tried> aticonfig --lcd-mode=full... still no luck.

[U]
**remaining Issue #2**[/U]
On the audio front, during the reboot, I also went in to BIOS and disabled onboard HD audio and HDMI audio. My Volume control in the top panel disappeared, so I re-added it... apparently I cannot adjust the volume or it crashes.. shrug.

When I go to Sound preferences, the sound tests work.  With the onboard disabled, aplay -l now lists my ATI card as card #0 (instead of card #1).  I can point VLC to it, and Songbird (for music). speaker-test -c 2 works, but I can't get sound from Firefox/Flash (ie. Youtube).. I did have this working when the nvidia was my card #0.  Re-ran alsaconf... any suggestions?

---

### Post by markbuntu on 2009-02-01
For the sound problem with flash try switching your System/Preferences/Sound to alsa. You may need to get the packages

libasound2
libasound2-plugins
alsa-oss

HDMI audio is IEC958/Spdif digital only so you cannot control the volume from the computer.

Which driver from ati are you using?
Control for tvs and HDMI has been incrementally improved with each driver.

---

### Post by zim2dive on 2009-02-01
> **markbuntu said:**
> For the sound problem with flash try switching your System/Preferences/Sound to alsa. You may need to get the packages

libasound2
libasound2-plugins
alsa-oss

HDMI audio is IEC958/Spdif digital only so you cannot control the volume from the computer.

Which driver from ati are you using?
Control for tvs and HDMI has been incrementally improved with each driver.

already installed.. I was on Alsa 1.0.19 (I had to upgrade to 18a at a minimum for the nvidia HDMI sound)... so I had this all working with nvidia HDMI audio previous to installing this new ATI card.

For ATI, I am using whatever I got by default with apt-get under Intrepid (which if the nvidia side is any guide, is woefully outdated, but I have not investigated the by-hand ATI process yet.. it was perilous under the nvidia drivers after 180.11).. Synaptic suggests xserver-xorg-ati-* at 1.69, and the hardware drivers panel, unhelpfully gives no driver version (unlike nvidia which does) for the active driver.. fglrx is 8.552 (via Synaptic).

I wonder if my xorg is messy b/c it had the nvidia config in it?  I tried removing it completely, but aticonfig would not run the initial without a "template"?

---

### Post by zim2dive on 2009-02-01
It gets mildly more interesting.. my screen is not compressed... ie. part of my screen are unviewable.

The top left of the GNOME dessktop appears at maybe 100,100 on my LCD... with parts of the right side and bottom missing, out of view.  But I have a uniform black border on all sides of the dfekstop that I can see.. so its not JUST being sifted down/right, else I'd expect to see no border on bottom/right sides...

I did confirm that my driver in xorg is flgrx.

EDIT: it appears that I am getting 1776x1000 as the max area I can view.. if I set resolution to 1920x1080, I seem to "get" 1920x1080, but I can only see the left/upper 1776x1000 of it (right/bottom is cut off).  I have upgraded to Catalyst 9.1, 8.57.2 driver), but still the same.  I have also tried using DVI instead of HDMI.  Still back at square 1.

---

### Post by markbuntu on 2009-02-01
Hmmmm... have you tried the autodetect monitor function in CCC?

---

### Post by zim2dive on 2009-02-01
> **markbuntu said:**
> Hmmmm... have you tried the autodetect monitor function in CCC?

I'm not seeing that option?

I have a Philips 7403 1080p LCD.. and the CCC shows [Philips] ATI RAdeon Hd 340 nuder the Display Manager  It shows DTV(1) with all the info I'd expect.. Philips, HDMI, 1920x1080 60Hz

EDIT: I see references in various threads around the net to there being overscan controls in CCC.. I dont see them anywhere.. could my CCC be old somehow? It says 2.3 when I do -version...

Edits 2: under Vista I also saw the same thing, BUT CCC 3.x under Vista has an overscan adjustment.. I have CCC 2.3 under linux and see no such adjustment.

---

### Post by zim2dive on 2009-02-02
Partial fix for issue #1> sudo aticonfig --set-dispattrib=tmds2,sizeX:1920
sudo aticonfig --set-dispattrib=tmds2,sizeY:1080
sudo aticonfig --set-dispattrib=tmds2,positionX:+0
sudo aticonfig --set-dispattrib=tmds2,positionY:+0

how do I get this in to my xorg.conf or to happen automtically?

Issue #2 is still there..

Why can't I get sound from Flash... all my other sound works (amarok, vlc, songbird, speaker-test, etc... everything else I've tried worked as expected) ??

---

### Post by markbuntu on 2009-02-02
Try this with flash. Open the pulseaudio volume control and play a flash. see if it shows up in the playback tab.

---

### Post by zim2dive on 2009-02-02
> **markbuntu said:**
> Try this with flash. Open the pulseaudio volume control and play a flash. see if it shows up in the playback tab.

Sorry to be obtuse.. which volume control is that?  

(I find the multiple volume controls confusing.. I have 1 via System Prefs, and another in the top panel, and I'm sure there are more lurking around, like alsmixer and who knows what else)

thanks,
Mike

---

### Post by markbuntu on 2009-02-03
Go here, read this, it will shed a little light on how the sound scheme works

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by zim2dive on 2009-02-03
> **markbuntu said:**
> Go here, read this, it will shed a little light on how the sound scheme works

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I am 99% sure I do not have pulse.  Other than upgrading to alsa 1.0.19, I have pretty much what comes with Intrepid. My un-learned impression is that means I got the not-quite pulse setup (based upon how I read the pulse how-to)

What I have works for all other audio sources, and also worked for Flash when I was using my nvidia IGP.

can we not work with that?

I'm trying to dodge the pulse vs. non-pulse arguments... simpyl saying what I have and what works (ie. everything but Flash audio), and that Flash audio worked with the same setup other than switching from nvidia to ati drivers.

---

### Post by markbuntu on 2009-02-03
OK then, how are your sound preferences set up?

---

### Post by zim2dive on 2009-02-03
> **markbuntu said:**
> OK then, how are your sound preferences set up?

In the System/Pref/Volume ?  I have tried pointing everything at both ALSA and ATI-HDMI.. both work for all other types of audio.

My .asoundrc is > pcm.!default {
type hw
card 0
device 3
}  I saw a reference to change that to hdmi, and will try that tonite (again tho, it seems odd that all other audio is happy)

Via other debug suggestions, I also tried the gstreamer panel and pointed everything there. (some refs made it sound like FF would send audio to gstreamer... rhtythmbox works fine for me)

And some (seemingly out of date) env var for FIREFOX_DSP.. but it fails also in Opera.

---

### Post by markbuntu on 2009-02-03
Do you know where flash is trying to send the sound?
You can try changing your System/Preferences/Sound to the ati hdmi device instead of ALSA, that might work.

---

### Post by zim2dive on 2009-02-03
> **markbuntu said:**
> Do you know where flash is trying to send the sound?
You can try changing your System/Preferences/Sound to the ati hdmi device instead of ALSA, that might work.

I don't know how to "steer" the Flash audio. (I have the impression pulse lets me do that explicitly.. not sure how to do it in the absence of pulse?)  Is there a way for me to know where Flash is trying to send the sound?

I've tried both settings in the Volume prefs.. ie. ALSA, and ATI HDMI, both settings have the same effect for me (sound from everything except Flash).

---

### Post by zim2dive on 2009-02-03
Hmm... here might be the steering wheel.... FLASH_FORCE_(foo)

[https://forja.rediris.es/plugins/scmsvn/viewcvs.php/*checkout*/trunk/libflashsupport/README?root=cls-tcos](https://forja.rediris.es/plugins/scmsvn/viewcvs.php/*checkout*/trunk/libflashsupport/README?root=cls-tcos)

---

### Post by markbuntu on 2009-02-03
Where did you get this flash from?

Did you uninstall pulseaudio or disable it?
If not, it is entirely probable that pulseaudio is running and flash is using it. You can check that with the system monitor, pulseaudio will be sleeping.

---

### Post by zim2dive on 2009-02-03
> **markbuntu said:**
> Where did you get this flash from?

Did you uninstall pulseaudio or disable it?
If not, it is entirely probable that pulseaudio is running and flash is using it. You can check that with the system monitor, pulseaudio will be sleeping.

padevchooser is sleeping, but no other (obvious) parts of pull.

I did> setenv FLASH_DEBUGAUDIO 1 and see this error in my term> ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave

But the FLASH_FORCE_ALSA didn't seem to do the trick (I need to unset it and see if the error vanishes)

---

### Post by zim2dive on 2009-02-03
SUCCESS!

changing my .asoundrc to [QUOTE]defaults.pcm.device 3[QUOTE] somehow made everything happy.

Thanks for sticking with me on this!

Miller time...

EDIT: env vars FLASH_AUDIODEBUG and FLASH_FORCE_ALSA were also in the mix.

---

