---
title: "[SOLVED] No sound: Toshiba Satellite a135-s2386"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by theooftheoretic on 2007-05-23
Just to let everyone know that I have solved my audio problems on my Toshiba Satellite a135-s2386 with an SB450

I made the following change after a fresh install (no other changes to the system made), as per a post I found somewhere in this site.

At the bottom of /etc/modules.d/alsa-base:
```

options snd-hda-intel probe_mask=8 model=3stack

```

Before this change, the output of "aplay -l" was this:
```
adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

After a couple of reboots, the output now reads:
```
adamtheo@laptop-a135:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So it seems the problem was that Linux was thinking my dial-up modem was the soundcard, and therefore couldn't use it to produce sound. It had to be told to ignore the modem and go on to another device (I'm guessing?). And although I had tried a similar fix that didn't work, the key part of this fix seemed to be the "probe_mask=8" part of the alsa-base line.

Now sound works perfectly, although perhaps a little low (in Vista the sound was excellent, even the volume at 20% was enough to clearly hear from the next room over, now I have to crank it up to 80%).

---

### Post by kuripot on 2007-06-03
Awesome!! I've been waiting for a fix for this, now I'm back to using ubuntu again. 

also, the correct location of alsa-base is 

/etc/modprobe.d/alsa-base

not

/etc/modules.d/alsa-base

Other than that, easy as pie to follow.

---

### Post by volkswagner on 2007-06-04
Still no sound for me.  I have tried several fixes on the forum.  I think we need an organized post.  We need to know what version of alsamixer people are having success with.  See my post

[http://ubuntuforums.org/showthread.php?t=443512]("http://ubuntuforums.org/showthread.php?t=443512")

I am using latest alsamixer.  I see some have alsa-base in different locations.  See prior post on this thread.  For me it is /etc/modprobe.d/alsa-base

Is this due to different version of alsamixer?
Here is what my file looks like

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

I have in the past added this "options snd-hda-intel probe_mask=8 model=3stack" and saved but now i see it is not there.  

The only switches i see are for headphones what do others see with this card?

---

### Post by volkswagner on 2007-06-04
Ok maybe when i saved it did not take.  Sound now works when adding 

options snd-hda-intel probe_mask=8 model=3stack        

for me alsa-base is in  /etc/modprobe.d/alsa-base

saved, reboot, sound works

Before the change aplay -l   listed sb40 and modem now just sb450

spread the word.  Please note i am using latest alsamixer

---

### Post by jms830 on 2007-06-04
options snd-hda-intel position_fix=1 model=3stack

Adding that line made sound work on my toshiba satellite A135-S4527. However, when headphones are plugged in, sound comes out of them, BUT sound still comes out of the speakers also. Anyone fix that issue?

---

### Post by intricate on 2007-06-05
Forgive me for being an ignoramus, but I am new to Ubuntu and would like to know where to paste the code you've shown. Exactly, how do I go to the area I need to paste the code and where would I paste the code? (My aplay shows the same output Ubuntu thinking my sound chip is the modem, or vice versa). Thank you to those with far more experience than I.

---

### Post by intricate on 2007-06-05
Here is what aplay -l shows now on my TOSHIBA laptop: 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It shows BOTH modem and sound!  What the...?? How do i get rid of the modem portion?

Thanks guys!



to let everyone know that I have solved my audio problems on my Toshiba Satellite a135-s2386 with an SB450

I made the following change after a fresh install (no other changes to the system made), as per a post I found somewhere in this site.

At the bottom of /etc/modules.d/alsa-base:
```

options snd-hda-intel probe_mask=8 model=3stack

```

Before this change, the output of "aplay -l" was this:
```
adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

After a couple of reboots, the output now reads:
```
adamtheo@laptop-a135:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So it seems the problem was that Linux was thinking my dial-up modem was the soundcard, and therefore couldn't use it to produce sound. It had to be told to ignore the modem and go on to another device (I'm guessing?). And although I had tried a similar fix that didn't work, the key part of this fix seemed to be the "probe_mask=8" part of the alsa-base line.

Now sound works perfectly, although perhaps a little low (in Vista the sound was excellent, even the volume at 20% was enough to clearly hear from the next room over, now I have to crank it up to 80%).[/QUOTE]

---

### Post by volkswagner on 2007-06-05
intricate,

i had the same output via aplay -l as you !

after adding the line options snd-hda-intel probe_mask=8 model=3stack to 
/etc/modprobe.d/alsa-base   my aplay -l output only shows the sound card and sound now works.  I still have audio out on headphones and speakers but it doesn't impact me at this time.

when i perform gedit in a terminal the file opens in another window where the line is to be added
at the end.  

Good luck!

---

### Post by LightPhoenix on 2007-06-11
I have a Toshiba Satellite a135-s4467, and I had the same message when I typed in aplay -l.  However, typing in the options line above caused ALSA to stop recognizing my card.  I left out the "probe_mask=3" parameter and my sound started working after a reboot.

Thanks to everyone else for putting me on the road.

---

### Post by johntkucz on 2007-06-21
> **theooftheoretic said:**
> Just to let everyone know that I have solved my audio problems on my Toshiba Satellite a135-s2386 with an SB450

I made the following change after a fresh install (no other changes to the system made), as per a post I found somewhere in this site.

At the bottom of /etc/modules.d/alsa-base:
```

options snd-hda-intel probe_mask=8 model=3stack

```

Before this change, the output of "aplay -l" was this:
```
adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

After a couple of reboots, the output now reads:
```
adamtheo@laptop-a135:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So it seems the problem was that Linux was thinking my dial-up modem was the soundcard, and therefore couldn't use it to produce sound. It had to be told to ignore the modem and go on to another device (I'm guessing?). And although I had tried a similar fix that didn't work, the key part of this fix seemed to be the "probe_mask=8" part of the alsa-base line.

Now sound works perfectly, although perhaps a little low (in Vista the sound was excellent, even the volume at 20% was enough to clearly hear from the next room over, now I have to crank it up to 80%).

I tried this "fix" with the HDA-Intel sound card, with the same modem "ambiguity"

card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but upon reboot ended up with aplay -l
222: no devices found error

so I undid that and am still stuck! Help
Have a mx3701 gateway laptop

---

### Post by redcharlie on 2007-06-26
My wife's in grad school and I just bought her a Toshiba A135-2386.
We've got a triple boot (Wista, Xp, Xubuntu) and thanx to this forum, sound.

Other than doing an upgrade after the install (no idea if that had any affect on the sound issue) all I needed to do was 
1) add the one line to the bottom of /etc/modprobe.d/alsa-base as described above.
and
2) open a termnial and type in "alsamixer" and run up the pcm and front speaker to the max.
(see [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide))

Voila! sound!

---

### Post by intricate on 2007-06-26
Forgive me for asking but WHERE do I find :

At the bottom of "/etc/modules.d/alsa-base":

so that I can paste the code I need to make the sound work on my Toshiba laptop?

Thanks kindly.

---

### Post by big67 on 2007-07-07
BUMP!  
Same question as the person above!
Thanks

---

### Post by marc_c on 2007-07-07
In a terminal window enter the following:

sudo gedit /etc/modules.d/alsa-base

---

### Post by calplants on 2007-07-07
Just one typo in your resolution: directory path should be /etc/modprobe.d not /etc/modules.d. Otherwise implementing this solution on my Toshiba Satellite worked like a charm.:D
Thanks,
Calplants

---

### Post by big67 on 2007-07-07
It works! 
I've got sound now!
Thanks everyone.

---

### Post by kpagan on 2007-07-08
Well I have a **Toshiba Tecra A8-103** laptop and I installed the Ubuntu Feisty Fawn 64-bit Linux.
I couldn't hear sound from the integrated speakers too.
I tried options 
```
snd-hda-intel model=3stack
``` 
and 
```
options snd-hda-intel probe_mask=8 model=3stack
``` 
that was referring to Toshiba laptops with no effects.
When I type 
```
lspci | grep Audio
``` the output it produces is ```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

When I typed 
```
aplay -l
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
or something like that. Anyway the important part is **[ALC262 Analog]**
Then I read the solution that **eggdeng** posted at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")
I searched for [ALC262 Analog] in **/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt**
and the portion of the text was 
```
	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  benq		Benq ED8
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)
```

It seems here that I should set my model as **fujitsu**
So I edited **/etc/modprobe.d/alsa-base** and entered
```
options snd-hda-intel model=fujitsu
```
and now I can hear sound from the integrated speakers as well.

---

### Post by GFC2 on 2007-07-08
Problem solved.  See below.

---

### Post by GFC2 on 2007-07-08
Success, sweet success!

Per kpagan's post I navigated to and opened: /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz.  and found the listing for my particular soundcard ID'd under aplay -l.  Under that heading: 
ALC861/660 (under snd-hda-intel module)
   (model name)-----------(description)
	  3stack----------------3-jack<(mine)
	  3stack-dig-----------3-jack with SPDIF I/O
	  6stack-dig---------- 6-jack with SPDIF I/O
	  3stack-660----------3-jack (for ALC660)
	  uniwill-m31---------Uniwill M31 laptop
	  auto-------------------auto-config reading BIOS (default)

Note that the model name is simply "3stack," there is no reference to "probe_mask=8."  From what I can tell (and please correct me if I'm wrong), "mask" is some global thingie that is specific to some custom hardware addressing schemes.    Anyway, the lesson is to search for your specific ALSA configuration module and enter the code in the form of:

options (module name, e.g. snd-hda-intel) model=(your model name, e.g. 3stack) 

as the very last line of /etc/modprobe.d/alsa-base.

Those login cungas sounded pretty good!

---

### Post by intricate on 2007-07-20
> **marc_c said:**
> In a terminal window enter the following:

sudo gedit /etc/modules.d/alsa-base

when i type that EXACLY as shown, and then type snd-hda-intel model=3stack,
I get:

bobo@bobo-laptop:~$ sudo gedit /etc/modules.d/alsa-base
Password:

** (gedit:6281): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.


What in the hell does that mean?
I can play a DVD now but NO SOUND HEARD!!


Could not save the file /etc/modules.d/alsa-base. FILE NOT FOUND   

CAN ANYONE LOAN ME 50 IQ POINTS?

Cripes sakes.

---

### Post by mytwobears on 2007-07-20
The OP made a typo.  In the terminal, you should type:

sudo gedit /etc/modprobe.d/alsa-base

When the Password prompt appears, type in your password and then gedit (which is a text editor) will open up the modprobe.d/alsa-base configuration file in a separate application window.  Make whatever changes you need to make, save the file and close gedit.


HTH :).

---

### Post by intricate on 2007-07-21
Thanks mytwobears...now I have sound playing a DVD as long as I keep the volume levels maximized using the alsamixer console.

It proves that syntax disables grammar.

One last mission:

at this web site, video.dot.co.gov I cant see/get any video stream on ubuntu. Id like to use VLC to view but dont know how to call VLC and when I click on a video stream source, I get "error opening or cant open". So far, this is the last web stream application that I cant watch. Same with you tube etc. What can I do to troubleshoot this problem?

Thanks again for you help--I thought Id never be able to watch a  DVD with sound in Ubuntu. I used to watch the DVD wirh gxine but prefer to watch with VLC media player.  I stand by to implement your suggestions

You guys are the greatest and Ill never go back to using Megasloth OS or appz..

---

### Post by PeterWalgreens on 2007-08-28
bump

---

### Post by PeterWalgreens on 2007-08-28
Ok, I figured out how to open up that file, And I added the extra line of text, but now the computer doesnt even think it has a sound card.... WHY?


walgreens@Skynet-Tuxbox:~$  aplay -l
aplay: device_list:222: no soundcards found...

---

### Post by PeterWalgreens on 2007-08-28
> **jms830 said:**
> options snd-hda-intel position_fix=1 model=3stack

Adding that line made sound work on my toshiba satellite A135-S4527. However, when headphones are plugged in, sound comes out of them, BUT sound still comes out of the speakers also. Anyone fix that issue?

Mine too! thanks! AWSOME!

---

### Post by JaceMan on 2007-10-23
What's the deal with Ubuntu/Kubuntu/Xubuntu 7.10?  I have a Toshiba laptop (A105-S2081) as well, with the same soundcard.  It has always been problematic with Ubuntu, but I was always able to get it to work in Ubuntu 7.04 and Linux Mint.  With 7.10 I have no luck at all.

I've tried the simple stuff listed here, and even recompiled my kernel headers to include the latest (brand new) Alsa... still a no go.

Anyone have sound on these stubborn Toshiba machines with the latest release?

Should I break this up into an "unsolved" thread?

---

### Post by stuoolong on 2007-11-08
> **GFC2 said:**
> Success, sweet success!

Per kpagan's post I navigated to and opened: /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz.  and found the listing for my particular soundcard ID'd under aplay -l.  


Yay! This clinched it for me. Thanks to you and everyone else in this thread, I now have sound! :)
Perusing the above-mentioned file, I discovered that there is a model called "lenovo", so I substituted that phrase instead of "3stack". While it says it's specifically for a Lenovo 3000 c200 series, it works on my 3000 N200. I didn't use the probe mask option.

---

### Post by iheartubuntu on 2008-03-05
I have installed Ubuntu on my sisters new laptop, a Toshiba Satellite Pro with all sorts of fun problems.

I followed the steps outlined in this thread and still have no sound. I have the latest ALSA drivers and I do get the volume control to work, but no sound.

I added "options snd-hda-intel probe_mask=8 model=3stack" to the end of the alsa-base.

Here is the output of "aplay -l"

> 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Please help! Thanks!

PS. I also tried "options snd-hda-intel position_fix=1 model=3stack" with no luck as well (I couldnt get the sound control to even work with that)

---

### Post by iheartubuntu on 2008-03-05
Reading another persons post, they noticed some changes when they rebooted a few times. I also notice some stuff going on. In the sound preferences I notice under the Devices is listed:

HDA ATI SB (Alsa mixer)

and then is listed under that...

-Master
-PCM
-Digital

When I first rebooted it only said "master", but now after several reboots It lists PCM and Digital as well.

I also notice I can now switch devices from "HDA ATI SB (Alsa Mixer)" to "Realtek ID 268 (OSS Mixer)" (which lists volume underneath it)

Under further examination of the "aplay -l" command, 
> 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I notice the "subdevices" has changed from 1/1 to 0/1. Either way, now or a few reboots ago, I never have gotten sound.

---

### Post by Sergeant_Pony on 2008-03-18
I have a Toshiba Satellite A105-S2131 and my aplay -l is this:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 I have added several lines that I read in these forums and still no sound....
Any ideas?
Please help.. I've been trying for 2 weeks to get this working.

Thanks

---

