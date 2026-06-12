---
title: "Intel-HDA no input"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by whitewizardcoder on 2006-06-27
Hi everyone,

I have an HP dv5000 with an Intel HDA soundcard.  The sound is fine, though a bit low on the volume, but I am unable to get any sound to come in through the microphone port.  If anyone can help, that would be great.  Also, if anyone knows how to fix the low volume, that would be great too.

Thanks,
WhiteWizardCoder

---

### Post by david_e on 2006-07-01
I am having this problems too under ubuntu-kubuntu, but I had it also with Debian testing and Mepis. 

Don't know how to solve it... under breezy I had a similar problem with another AC'97 card and solved it by tipping "+20db" under galsa-mixer, but I don't see it any more with this version of alsa-mixer...

---

### Post by LordRaiden on 2006-07-02
I don't cover microphones in my guide (I might later on). Did it ever work before? If you feel confident, I would suggest getting the latest alsa-drivers (not anything else) from alsa-project and trying them. I have instructions in the guide in my signature. good luck!

---

### Post by david_e on 2006-07-02
Thanks to your HOW-TO I was able to compile and install alsa driver from source, but I am still having the low volume issue and I still can't use an external mic.

I have also tried compiling ALSA library, oss and plugins as said here:

[http://www.ubuntuforums.org/showthread.php?t=187156](http://www.ubuntuforums.org/showthread.php?t=187156)

using the things I have learned thanks to your how-to...

---

### Post by david_e on 2006-07-02
Update: I had the ALSA driver compiled and installed using a little "script" that follows [this instructions]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel") and reboots the computer.

However because this doesn't work I have tried following the steps "by hand": I can't compile alsa-utils. 

I have attached the output messagges of make...

I have tried recompiling after reboot and issueing an:

```
apt-get remove --purge alsa-utils
```

before compiling.

I must say that the computer I am working on is not my computer (the one with kubuntu 6.06 on of my user infos)  but now runs a Mepis 6.0 RC2 (that is based on Ubuntu). (removed debian testing and dapper since I thought Mepis is better for owner of this PC) 

Any ideas?

PS : Sorry for my English!

---

### Post by david_e on 2006-07-03
Finally solved!

I was able to make the external mic work, even if I could not compile alsa utils. 

This is how I did.

I downloaded the Alsa 1.0.11 drivers and library from the ALSA site:

[www.alsa-project.org](www.alsa-project.org)

Compliled and installed the drivers using [LordRaiden HOW-TO]("http://www.ubuntuforums.org/showthread.php?t=205449"), but with a different configuration:

```
./configure --with-cards=hda-intel --with-sequencer=yes --with-oss=yes
```

then I compiled the library with the standard sequence of comands:

```

tar xjvf alsa-lib-1.0.11
cd alsa-lib-1.0.11
./configure
make
sudo make install
```

Installed the utils from repos (as I was not able to compile):

```
sudo apt-get install alsa-utils
```

Then looked into the /etc/modutils directory for a config file for ALSA and made it look like this:

```
# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-hda-intel
        # module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
        
        # card #1
        alias sound-service-0-0 snd-mixer-oss
        alias sound-service-0-1 snd-seq-oss
        alias sound-service-0-3 snd-pcm-oss
        alias sound-service-0-8 snd-seq-oss
        alias sound-service-0-12 snd-pcm-oss
```

If there is no configuration file for ALSA (like in my modutils dir) (I read all the files in that dir to ensure there was none) you should add a new file (eg. /etc/modutils/alsa) and copy-paste the above code into it. (you should be root to do this) (sudo gedit/kate /etc/modutils/alsa) (ubuntu/kubuntu).

Then issue an:

```
sudo update-modules
``` 

after reboot my external mic was working.

*** EDIT ***
The low volume issue is still present: maybe there is some compile option to raise the volume? I have read something about a patch to apply to the driver, but didn't understand exactly what I should do....

---

### Post by whitewizardcoder on 2006-07-04
david_e,

That is awesome!  I'll have to try it when I have more time.  Thanks for the help!

---

### Post by LordRaiden on 2006-07-05
I found this thanks to  pinballkid responding to my guide

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2106]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2106")

One of the posters in the link, louisvd, fixed his problem by adding this to /etc/modprobe.conf (he also uses an HP PC)


alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0 model=basic
remove snd-hda-intel { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-hda-intel

---

### Post by david_e on 2006-07-05
Bad update: after a cupple of nice day with the mic working I have experienced a new issue: if I start the computer with the mic unplugged I could not use the mic any more: I have to restart the computer into windows, plug the mic and then switch back to Linux. The mic will work (I can plug and unplug it anytime I want while the computer is on), but if I start the computer with the mic unplugged there is no way to get it but to run Windows....

This is not satisfactory at all... sorry whitewizardcoder maybe I posted it to early... :( 

I will try LordRaiden suggestion ASAP (thanks again for your help!) and report...

---

### Post by david_e on 2006-07-10
Finally I was able to try it... nothing. The only way to have the mic working is to connect it in a Windows session and reboot with it connected...

Tried also with a custom 2.6.17 kernel, but it was useless...

---

