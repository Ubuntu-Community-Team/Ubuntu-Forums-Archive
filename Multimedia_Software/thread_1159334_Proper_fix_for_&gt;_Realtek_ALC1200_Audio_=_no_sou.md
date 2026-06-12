---
title: "Proper fix for &gt; Realtek ALC1200 Audio = no sound"
date: 2009-05-14
forum: Multimedia Software
---

### Post by djamu on 2009-05-14
Proper fix for Realtek ALC1200 

took me a while to figure this one out > thanks to the guys at the Fedora forums.

solution is simple. just create an option config file in /etc/modprobe.d/

```

sudo gedit /etc/modprobe.d/hda_intel.conf

```

and paste this in it.

```
options snd-hda-intel model=auto probe_mask=1

```

save this 
reboot ( or restart your services etc ... )

check your volume is up...

have fun...
):P

---

### Post by sojyujai on 2009-05-16
Cheers for this.  
I'm using an Asus M3N-H/HDMI mb with ALC1200 sound.  Previous versions of ubuntu used the driver for the ALC883 I think it was - but in Jaunty I noticed it started to use the ALC1200.  I was pulling my hair out trying to get sound out of it until I tried your above fix and that solved it.

After the reboot I still had to go into the volume control, on the switches tab and deselect Headphone and select both IEC958 and 'IEC958 Default PCM' to get it to work.  But now it's working with both standard pcm and with ac3 and dts passthrough.  Sweet.

---

### Post by djamu on 2009-05-18
> **sojyujai said:**
> .....
After the reboot I still had to go into the volume control, on the switches tab and deselect Headphone and select both IEC958 and 'IEC958 Default PCM' to get it to work.  But now it's working with both standard pcm and with ac3 and dts passthrough.  Sweet.

I ha(d)ve them all enabled...

---

### Post by Cyborgoat on 2009-05-27
What needs to be done up to this point before executing this command?

I am getting a Gstreamer or volume control is not installed

---

### Post by SnowPunk98 on 2009-07-09
Thanks this and "fter the reboot I still had to go into the volume control, on the switches tab and deselect Headphone and select both IEC958 and 'IEC958 Default PCM' to get it to work. But now it's working with both standard pcm and with ac3 and dts passthrough. Sweet."

resolved my problem, one of the two, either way I have sound, thanks!

---

### Post by bunorama on 2009-10-03
Thanks.
After reboot, sound works.  Easy fix.

---

### Post by 2GooD on 2009-11-20
> **djamu said:**
> Proper fix for Realtek ALC1200 

took me a while to figure this one out > thanks to the guys at the Fedora forums.

solution is simple. just create an option config file in /etc/modprobe.d/

```

sudo gedit /etc/modprobe.d/hda_intel.conf

```

and paste this in it.

```
options snd-hda-intel model=auto probe_mask=1

```

save this 
reboot ( or restart your services etc ... )

check your volume is up...

have fun...
):P


Thanks a lot! This made sound work on my HP machine.

\David, [http://www.divideandconquer.se/](http://www.divideandconquer.se/)

---

### Post by EnfanTerrible on 2009-12-22
Thank you!
It works here on Asus P5Q (ALC1200) with Karmic Koala 64 bit!

Thank you and Merry Christmas to all :KS

---

### Post by miros84 on 2010-01-03
Does the microphone work with Realtek ALC1200???

---

### Post by djamu on 2010-01-03
> **miros84 said:**
> Does the microphone work with Realtek ALC1200???

mmm, didn't test it but I guess so ( this mobo is now in use as a fileserver for my cluster )..
I also found another fix ( didn't have time to test this yet, but please post any results here.
here > [http://ubuntuforums.org/showpost.php?p=7758827&postcount=19]("http://ubuntuforums.org/showpost.php?p=7758827&postcount=19")

happy NY to all

---

### Post by Rusna on 2010-01-13
Just to confirm, this fixes coaxial S/PDIF as well? Digital output fully working?

---

### Post by djamu on 2010-01-15
> **Rusna said:**
> Just to confirm, this fixes coaxial S/PDIF as well? Digital output fully working?

I guess so, didn't notice 

fix is non-destructive and  done in less then a minute, why don't you try and report here ?

also notice I found a 2nd solution, but this involves compiling your own driver > [http://ubuntuforums.org/showpost.php?p=7758827&postcount=19]("http://ubuntuforums.org/showpost.php?p=7758827&postcount=19")

---

### Post by JoyousDeath on 2010-01-16
This works for me,

I have the ALC888
Ubuntu 9.10

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by djamu on 2010-01-16
> **JoyousDeath said:**
> This works for me,

I have the ALC888
Ubuntu 9.10



:confused:

Good for you.
But enlighten me > what does the ALC888 have in common with with the ALC1200 ?
Nothing I'm afraid. 
Reply is off-topic and polluting the thread, please delete > post in own thread, for example > **Proper fix for > Realtek ALC888 Audio = no sound**
:|

---

### Post by mutha88 on 2010-02-07
Hi! I have a question... I have an ASUS P5Q motherboard with the ingloriuos :popcorn: Realtek ALC1200 audio chipset.

I can't have more than 2 channels in Ubuntu 9.10 Karmic. I use analog audio (6 channels, 5.1 surround, 3 analog cables - 1 for the 2x fronts, 1 for the 2x surround and 1 for the center and subwoofer). 

Where is the problem?

One more question... Which solution is better?:
[B]
Solition 1:[/B]

> **djamu said:**
> Proper fix for Realtek ALC1200 

took me a while to figure this one out > thanks to the guys at the Fedora forums.

solution is simple. just create an option config file in /etc/modprobe.d/

```

sudo gedit /etc/modprobe.d/hda_intel.conf

```and paste this in it.

```
options snd-hda-intel model=auto probe_mask=1

```save this 
reboot ( or restart your services etc ... )

check your volume is up...

have fun...
):P

or:

[B]Solution 2:

[/B]> 

I have an ASUS P5QL Pro motherboard with the ALC1200 HD Audio chipset too.

However I managed to fix this with another method.

RealTek has a Linux driver which works perfectly in Ubuntu _**even though the notes don't specifically list the ALC1200 HD Audio chipset.**_

[http://www.realtek.com.tw/downloads/...3&DownTypeID=3]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3")

Download the linux driver from this page and follow the instructions in the Readme for the for the "Azalia controller" chipset. This driver even enables the SPDIF output on the P5QL motherboard. Then follow this wiki to enable the Pulseaudio ALSA plugin:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

This will enable all sound from all applications and let you independently mix and set volume for each app if you want.

I have perfectly working digital audio from my P5QL Pro motherboard over a coaxial SPDIF RCA cable to an A/V Receiver.
I think the #2 Solution is better, but the underlined part concerns me... How can I use a ALC888 driver for ALC1200?! [B]

So what should I do? Compile a driver or simply edit the hda_intel.conf?[/B]

(I'm new to Ubuntu. This is my first post. If there is problem with it, I'll delete it.)

---

### Post by djamu on 2010-02-10
sorry for the late reply

> **mutha88 said:**
> Hi! I have a question... I have an ASUS P5Q motherboard with the ingloriuos :popcorn: Realtek ALC1200 audio chipset.

I can't have more than 2 channels in Ubuntu 9.10 Karmic. I use analog audio (6 channels, 5.1 surround, 3 analog cables - 1 for the 2x fronts, 1 for the 2x surround and 1 for the center and subwoofer). 

Where is the problem?


mmm, I'm afraid I don't understand your question, 

Does it work without any of those 2 fixes ?

> 
One more question... Which solution is better?:
[B]
Solition 1:[/B]

or:
[B]Solution 2:

[/B]I think the #2 Solution is better, but the underlined part concerns me... How can I use a ALC888 driver for ALC1200?! [B]

So what should I do? Compile a driver or simply edit the hda_intel.conf?[/B]


**Ignore the previous post about the ALC888 ...**



What is better ? The one that suits your needs / the easiest.


Adding the hda_intel.conf  file is done in less then 30sec. 
If it works ( and it should work ) then there's no need for you to look any further. ( It's just a tweak on an available driver )


On the other hand compiling a new driver can be good if you want to hone your linux skills > a warning is in place though, there's no guarantee of success.
Don't worry about that driver being written for a different device. A lot of components from the same family share the same hardware design > and with that share the same base code. 
For example if one is unable to find a driver for a specific device from a manufacturer > 

***Most board designs are based on reference designs -meaning a certain chip on a board has to be accompanied by a certain other chip-, this means PCB boards from different manufacturers will look very much alike > ( for example an nvidia board with a specific GPU from brand A will have (almost) the same layout as those from brand B, and it's very safe to assume a driver from manufacturer B will work on a board from manufacturer A***


In contrast to M$ drivers, Linux drivers are ( almost) always based on chip family rather then brand... which is in a way smarter, but there's one problem with that.
Some chips ( for example the X58 chipset ) have capabilities that are not used in brand A but are in use by brand B.
For example an additional bus where one is able to connect a 3rd party controller.

***A good example for this is the X58 chipset ( for those i7 CPU's ) it doesn't have a PATA controller but does have a bus for a 3rd party PATA controller > any manufacturer can hook up whatever PATA controller they like. This means a X58 board will work flawless in linux .... but the PATA controller most likely won't  ( because it's custom ) ***


To make a long story short, my fix enables some switches the generic driver had not enabled > so if your board works without my "fix" you simply don't need it ..

;)

Jan

---

### Post by jdash1 on 2010-02-10
Let me try this one
;)

thanks

---

### Post by mutha88 on 2010-02-11
[LEFT]Thank you **djamu**!

Well here are the results. I've installed Ubuntu on a fresh partition, now I have Win 7 + Ubuntu on my PC.

My audio is running... I have 5.1 surround... All I've done was to open Sound Preferences and select Analog 5.1 Surround Output.

Now here is my problem. When I minimize some windows or open Vuze torrent client or make some kind of a very small load to Ubuntu, the mp3 I am playing stops for a second... Basically there is a "lag" if you understand, what I mean.

Why is this happening? Should I do the config you've posted? Will it stop the lagging?

I have one more small question... Is it normal my CPU1 to be at 99,5% all the time? Is it because of the audio drivers? :(

I can make screenshots of my audio, but in Audacious2 it says, that I'm using ALSA with Realtek ALC1200 (hd:0)... Something like that.

I'm a noobie, sorry for the lame questions...
[/LEFT]

---

### Post by djamu on 2010-02-11
> **mutha88 said:**
> [LEFT]Thank you **djamu**!
snipsnipsnip....

My audio is running... I have 5.1 surround... All I've done was to open Sound Preferences and select Analog 5.1 Surround Output.

....with my fix or with a compiled driver  ?
> 
Now here is my problem. When I minimize some windows or open Vuze torrent client or make some kind of a very small load to Ubuntu, the mp3 I am playing stops for a second... Basically there is a "lag" if you understand, what I mean.

Why is this happening? Should I do the config you've posted? Will it stop the lagging?

I have one more small question... Is it normal my CPU1 to be at 99,5% all the time? Is it because of the audio drivers? :(

I can make screenshots of my audio, but in Audacious2 it says, that I'm using ALSA with Realtek ALC1200 (hd:0)... Something like that.

I'm a noobie, sorry for the lame questions...
[/LEFT]

Open a terminal and give the "top" command, with that your able to see the process that is causing the load. Copy that and come back to me.

---

### Post by mutha88 on 2010-02-12
**djamu, **hi again! Sorry for the long pause, I'm busy these days... :(

I just wanted to share with the community, that my drivers are working... But I'm not sure, that everything is all right...

[B]I've done your settings for the driver!
[/B]
When I open Sound Preferences, I see "Internal Audio" as a device and under it: Analog Stereo Output. In this "scenario" I get a 5.1 surround on mp3s, flac and basically audio playback.

Strangely, if I try to switch to "Analog Surround 5.1 Output" I begin to hear only 2 channels??? In every application... Why is that?

It is quite bizarre (for me...). Anyway, I tried a DTS file - everything is working fine - In smplayer I'm using "output driver: alsa (0.0 HDA Intel)" and 5.1 Surround channels. 

In Audacious2, Exaile, RhythmBox I have proper playback, all 6 channels are working.

So... does this mean that all of my drivers are OK now?

One more thing - I can't get a proper playback in Amarok... Sometimes it plays, sometimes It doesn't play... It just pops a "ballon" saying, that Realtek ALC1200 Analog isn't working...I don't know why... But I kind of want to work with Amarok, it is the best player for me...

These days I'll try to find time and make more tests.
[B]
EDIT:[/B]

Here is my audio, detected after typing aplay -l in the terminal:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by UnicornsRock420 on 2010-03-05
DJamu, I've been trying to overcome this same issue with ALSA and PulseAudio.

I've compiled the latest RealTek drivers/plugins/libs/etc. Tried the probe_mask=1 option in the /etc/modprobe.d/sound configuration file. Nothing changes the behavior of the machine, which is zero sound except that amarok does make something very faint, while the volume/mixer is cranked to the max.

Any ideas?

Thanks,
Paul

```
Prompt: aplay -l
aplay: device_list:223: no soundcards found...
Prompt: sudo cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC1200
Prompt: sudo lshw -class sound
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
Prompt: uname -a
Linux Host 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

---

### Post by Trinity33 on 2010-03-05
[QUOTE=UnicornsRock420;8922058]DJamu, I've been trying to overcome this same issue with ALSA and PulseAudio.

hi i assure u that there is no problem not even in 0.00001% to get acl 1200 work in karmic or lucid. i wasted 2 weeks before i found best solution to get it to work. there is if u start in fresh karmic for example u cant just go to modprobe.d edit add your card and it would work u need few things alsa new driver library etc. so if u have freh lucid or karmic that the right way to do follow that tutorial :

<snip>

in place where u wil need to install alsa driver and lib go to realtek web and get the newest audio pack in it u will have alsa driver lb tools utils. 
after u finish reboot pc as that guy says in that tuto then start alsaconf from shell and save it your card still wouldnt work. so than go to that web:

<snip>

there will be part u need to cpy and paste in your alsaconf file in modprobe.d u need to use gksudo nautilus to be abble to save changes.

in part where u chose model i used targa 8ch so i have propper surround and strong sound.

after that reboot and your sound will work for sure jut follow those tutorials took me mpre then 2 weeks to get my sond work find the propper solution etc tnx and good luck

ps with those tutos u will get max u can get from your acl 1200 without need to uninstall pulse audio oss etc

---

### Post by Trinity33 on 2010-03-05
> **djamu said:**
> Proper fix for Realtek ALC1200 

took me a while to figure this one out > thanks to the guys at the Fedora forums.

solution is simple. just create an option config file in /etc/modprobe.d/

```

sudo gedit /etc/modprobe.d/hda_intel.conf

```and paste this in it.

```
options snd-hda-intel model=auto probe_mask=1

```save this 
reboot ( or restart your services etc ... )

check your volume is up...

have fun...
):P


so thats not the proper fix it wouldnt work if u got new karmic or lucid or interpid u need first install proper drivers lib utils codecs etc

---

### Post by djamu on 2010-03-05
sorry was away for a while 

> **Trinity33 said:**
> DJamu, I've been trying to overcome this same issue with ALSA and PulseAudio.

snipsnip....

hi i assure u that there is no problem not even in 0.00001% to get acl 1200 work in karmic or lucid. 


[B]Obvious ...this wasn't a fix for karmic / lucid in the first place .... check 1st post date before you claim something
[/B]

> 
[http://monespaceperso.org/blg-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blg-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

snipsnip ... 

[http://forums.pensuse.org/hardware/laptop/422949-acl1200-ich9-82801i-4-1-surround-sound-problem-2.html](http://forums.pensuse.org/hardware/laptop/422949-acl1200-ich9-82801i-4-1-surround-sound-problem-2.html)



**WTF ... these links don't work / exist ( 4 hours after you posted them ) ... **

> **Trinity33 said:**
> so thats not the proper fix it wouldnt work if u got new karmic or lucid or interpid u need first install proper drivers lib utils codecs etc


I think your just a spammer / newbie > ... again this wasn't a fix for karmic / lucid but for 9.04


](*,)

---

### Post by djamu on 2010-03-05
Hi paul

> **UnicornsRock420 said:**
> DJamu, I've been trying to overcome this same issue with ALSA and PulseAudio.

I've compiled the latest RealTek drivers/plugins/libs/etc. Tried the probe_mask=1 option in the /etc/modprobe.d/sound configuration file. Nothing changes the behavior of the machine, which is zero sound except that amarok does make something very faint, while the volume/mixer is cranked to the max.

Any ideas?

Thanks,
Paul


What version of ubuntu are you using ? 
The fix was for 9.04 with default driver .. ( it just enabled it )

The very faint sound can mean that you didn't crank up all volume controls ( not just the master volume control ) 

> 

```
Prompt: aplay -l
aplay: device_list:223: no soundcards found...
Prompt: sudo cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC1200
Prompt: sudo lshw -class sound
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
Prompt: uname -a
Linux Host 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

mmm looking at the kernel I assume you are indeed using 9.04 

Unfortunately the for-mentioned motherboard is now in use as a fileserver for my raid-6 running debian. I might have some time on sunday to temporary install ubuntu 9.04 on it ( I need to move my compute nodes / servers to a new rack ... )  

... I'll keep you updated 

Jan 

;)

---

### Post by fazzledanny on 2010-03-12
Hi.
, i just joined a few days ago and lost my sound playability when i went to hardware updates. The info page said my software modem was deactivated.....of course thinking there was more to add to my operability i chose to activate/enable it, which then made my computer soundless.
5 minutes ago i returned to hardware updates and deactivated it.
Im proud to say sound is back on ready to rock and rolla!!! 
I hope this helps anybody else out there.
.
Quote of the day by fazzledanny:  Opensource freeware turn stingy selfish ignorant people into caring sharing teamplayers, dont you forget that!

---

### Post by curtissthompson on 2010-03-14
> **djamu said:**
> Proper fix for Realtek ALC1200 

took me a while to figure this one out > thanks to the guys at the Fedora forums.

solution is simple. just create an option config file in /etc/modprobe.d/

```

sudo gedit /etc/modprobe.d/hda_intel.conf

```

and paste this in it.

```
options snd-hda-intel model=auto probe_mask=1

```

save this 
reboot ( or restart your services etc ... )

check your volume is up...

have fun...
):P

I recently installed Ubuntu 9.10 on a newly built PC with ASUS M4A79T Deluxe motherboard that uses Realtek ALC1200 integrated audio and am having the same problem with no audio.  I'm looking to get analog working for my Logitech z-5300.

My motherboard is AMD and I'm wondering what I'd have to do differently with this fix to get my audio working.  Also, does the Realteck ACL1200 driver come with Ubuntu 9.10 Karmic Koala as a stock driver (because I haven't installed it manually myself)?

I'm an audio noob, so any help would be greatly appreciated.

---

### Post by LittleJakub on 2010-04-22
-

---

### Post by zazkia on 2010-04-30
Oh the realtek soundcard( i have it on my msi s420) made me have this problem over and over again. Under ubuntu 8.04 it miraculously worked, i guess due to OSS. 
I upgraded recently to 9.04, 9.10 and today to 10.4 and in neither of the three the sound worked and i cant find the switch to OSS. 
solution one, the sudo gedit /etc/modprobe.d/hda_intel.conf thingie, didnt do it for me. Now im trying the realtek driver 
How I hate this, ill promiss never to buy a realtek-embedded computer again.

---

### Post by zazkia on 2010-05-02
Well mixed results, with the driver that is provided by(?) realtek. 
For Ubuntu; it has to be installed by hand, this is not easy. 

Ill post the readme that is provided with the package here: 
```
The source code copy from www.alsa-project.org.      ver:5.14
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC259
ALC269
ALC270
ALC272
ALC275
ALC660
ALC660VD
ALC661
ALC662
ALC663
ALC665
ALC670
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A
ALC892

Installation:
This Source Code is from www.alsa-project.org.
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure (--with-cards=hda-intel)<= for HDA options
	c. make
	d. make install
	e. alsaconf

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.6 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
```

I posted it here because this may be tricky and because it includes a long list of realtek chipsets that have this problem. 
In terms of steps, make install won't go right unless you do it as root or as sudo. Step 2 can be skipped. I am stuck halfway down step 4 because there is neither a /etc/modules.conf or /etc/modprobe.conf file to edit. 

Does anyone know if I can safely put the module info in the "etc/modules" file instead? :confused:

---

### Post by zazkia on 2010-05-02
ok just added the files to /etc/modules and one thing for sure, still no sound. 
the weird thing is the sound did work in 8.04 out of its own, ill look into how that could be.

---

### Post by Stray Wolf on 2010-05-04
My system sounds don't work which is ok by me.  Rhythmbox has no audio, but lmms does (after a wiki fix), and I just downloaded Amarok for music.  I don't know what I'll do about Totem.  Prolly be lazy and find a working equivalent.  KDE stuff seems to be reliable.  Whoever did lmms is awesome that's for sure!  Point being, if edting lines in folders gets old sometimes its easier just to try other software.

---

### Post by Wandang on 2010-05-10
if any1 like me still doesnt have sound, try this:
```
options snd-hda-intel model=targa-dig
```

---

### Post by EthanGergen on 2011-03-30
It kind of worked, kind of didn't. I get sound out of one speaker, but not the other. Any ideas?

---

