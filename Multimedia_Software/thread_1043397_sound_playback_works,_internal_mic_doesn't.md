---
title: "sound playback works, internal mic doesn't"
date: 2009-01-18
forum: Multimedia Software
---

### Post by mm0204 on 2009-01-18
Hi,

I have a new HP lappy.  Model number is dv9925nr. I installed 8.04 for amd64 and have been blown away by the speed, stability, etc.  I got the nvidia drivers installed and the broadcom drivers and even my built in webcam works OTB.  I'm stoked... except, I am getting no audio capture.  It''s weird, because the devices are listed in System-->Prefs-->Sound.  When I run alsamix, all levels are up and nothing is muted.  In fact, I'm not getting any errors at all.  I am on the verge of reinstalling vista just so i can verify that the hardware works... grrrrr..... 

anybody else having this problem?  what other info would be helpful?

thanks,
Matt

---

### Post by markbuntu on 2009-01-18
There are a lot of problems with the intel hda sound chip due to poorly documented OEM tweaks that make it almost impossible for alsa to detect the proper configuration option for your particular hardware so you need to figure that out yourself by trying the available options and configuring your etc/modprobe.d/alsa-base file. These threads explain how to do that and offer some specific options for specific hardware. 


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Once you figure out which options works for you, please let us know which option worked for your hardware.

---

### Post by mm0204 on 2009-02-10
> **markbuntu said:**
> There are a lot of problems with the intel hda sound chip due to poorly documented OEM tweaks that make it almost impossible for alsa to detect the proper configuration option for your particular hardware so you need to figure that out yourself by trying the available options and configuring your etc/modprobe.d/alsa-base file. These threads explain how to do that and offer some specific options for specific hardware. 


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Once you figure out which options works for you, please let us know which option worked for your hardware.
so far... nothing works... i can't make heads or tails of this stuff... the output of 

" cat /proc/asound/card0/codec#* | grep Codec " is:

"Codec: Conexant CX20561 (Hermosa)"

I can't find reference to the CX20561 anywhere.

any thoughts?

---

### Post by ReyPeste on 2009-02-12
Ok, This solution worked for me:

I had this problem on a new Dell Inspiron. Sound card OK but no internal mic input.
Other posts suggested I activate "Digital Input" on the mixer preferences, but the option was not there.

After much searching, finally I followed instructions on the first link above, and that worked for me.
Specifically the part titled "Manually Specify Module Parameters".

With 
> cat /proc/asound/card0/codec#* | grep Codec
I found out that my card was STAC9228

Then I found the file ALSA-Configuration.txt inside an archive at
/usr/share/doc/alsa-base/driver/
I extracted it to the Desktop and opened it.

Inside I found several models related to my card 
(An obvious but important advice: it is best to read through the text a bit, as the line referring to my card was STAC9227/9228/9229/927x and a simple search for the name gave no results).

As I couldn't really tell the difference between the models, I decided to go for the most obvious: 
"dell-bios	Fixes with Dell BIOS setup"

So I opened /etc/modprobe.d/alsa-base
> gksu gedit /etc/modprobe.d/alsa-base

And added this line at the end of the file:
> options snd-hda-intel model=dell-bios

I rebooted, and the Digital Input option was there
(Right-click on the Volume Control Icon > Preferences)

Then in the mixer (Double-click on the Volume Control Icon)
I had the choice between Digital and Analog Input.

Digital enables the internal mic, analog enables the front input jack.

I guess most of this solution is specific to my soundcard, but I hope it will be useful to somebody else.

---

### Post by mm0204 on 2009-02-12
Rey

Thanks for the help.  That file you refered to (ALSA-CONFIGURATION.txt) does not contain any references to anything resembling my output to > cat /proc/asound/card0/codec#* | grep Codec

not sure what to do now.

Matt

---

### Post by mm0204 on 2009-02-23
just a bump to see if anyone out there is thinking about this...

---

### Post by The hobbit on 2009-05-13
Hi, I've got exactly the same pc and the same problem.
I'm actually using Jaunty, and I've tried almost everything to fix it, but nothing, please, some help.);)

---

