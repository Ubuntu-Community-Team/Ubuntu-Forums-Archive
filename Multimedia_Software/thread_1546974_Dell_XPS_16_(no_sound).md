---
title: "Dell XPS 16 (no sound)"
date: 2010-08-06
forum: Multimedia Software
---

### Post by deman88 on 2010-08-06
I have sound IN HEADPHONES only, no speakers

In 9.10 adding 


```
options snd-hda-intel model=dell-m6
options snd-hda-intel enable_msi=1
```

to /etc/modprobe.d/alsa-base.conf fixed the sound.

```
cat /proc/asound/card0/codec#* | grep Codec
```

returns

```
Codec: IDT 92HD73C1X5
```

so my sound card is recognized there and also its recognized in alsamixer where the speaker and master are both set to a decent volume.

EDIT: Alsamixer speaker volume refuses to stick, even with sudo alsactl store 0, but even sessions where I already changed alsamixer no sound.

I also added my username to /etc/group 

```
audio:x:29:pulse
```

to

```
audio:x:29:pulse:david
```

---

### Post by Yellow Pasque on 2010-08-06
Quick note:
> audio:x:29:pulse:david
should have a comma(,) between pulse and david (it shouldn't be necessary to add your user to that group if he's already in pulse though).

---

### Post by deman88 on 2010-08-06
> **Temüjin said:**
> Quick note:

should have a comma(,) between pulse and david (it shouldn't be necessary to add your user to that group if he's already in pulse though).

I changed to a comma, I also tried adding a file  with the model in /etc/modprobe.d/sound

---

### Post by Yellow Pasque on 2010-08-06
Did you put it in /etc/modprobe.d/alsa-base.conf? 
> /etc/modprobe.d/sound
Remove that file. It's in modprobe.d and doesn't end in .conf, so it will annoy you with warnings.

---

### Post by utilitytrack on 2010-08-06
to **deman88**

You know how to right ask to help. It's simply nicely for me (but you still forget to give here: [FONT="Courier New"]dpkg -l alsa* , lshw --sound[/FONT] and [FONT="Courier New"]uname -r[/FONT]. This need for to help you).

Ok, try update ALSA by following these instructions: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") and post here your impressions.

---

### Post by deman88 on 2010-08-06
> **utilitytrack said:**
> to **deman88**

You know how to right ask to help. It's simply nicely for me (but you still forget to give here: [FONT="Courier New"]dpkg -l alsa* , lshw --sound[/FONT] and [FONT="Courier New"]uname -r[/FONT]. This need for to help you).

Ok, try update ALSA by following these instructions: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") and post here your impressions.

utilitytrack, here are those codes! going to follow link that you gave now, thank you.

```
dpkg -l alsa*
```

returns

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                                         Description
+++-=====================================-===============================================-============================================
un  alsa                                  <none>                                          (no description available)
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
un  alsa-oss                              <none>                                          (no description available)
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
2.6.32-24-generic
```

and

```
lshw -c SOUND
```

returns

    ```
 description: Audio device
       product: RV710/730
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:39 memory:cfeec000-cfeeffff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:37 memory:f1000000-f1003fff
```

and

```
uname -r
```

returns

```
2.6.32-24-generic
```

I think it may be a lot with AlsaMixer not sticking, just thinking

---

### Post by deman88 on 2010-08-06
updating alsa didn't work, alsamixer STILL won't stick (sudo alsactl store 0) headphones still work.

I ran alsaconf and it changed /etc/modprobe.d/sound but still no go... :(

---

### Post by utilitytrack on 2010-08-06
What is that file? [FONT="Courier New"]/etc/modprobe.d/sound[/FONT] 
Also, **deman88** not worry and try pass to module other args (see [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#383]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#383")). May be simply it's broken mini-jack? Check it. 

PS 
post here [FONT="Courier New"]lspci -nn | grep Audio[/FONT]

---

### Post by lidex on 2010-08-06
First try these terminal commands:
```
sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

```
Reboot

No help?
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by deman88 on 2010-08-07
> **lidex said:**
> First try these terminal commands:
```
sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

```
Reboot

No help?
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```


the mv command won't work i dont have those files, commenting out the first line did nothing, and the third file doesn't exist. :(


I am on 64 bit ubuntu sorry for not mentioning this before.

in think my audio fixing things may be interfering with one another :(

aksamixer has speakers at 0 on boot, may not have changed on some tests :( ugh

---

### Post by deman88 on 2010-08-08
could it be my device doesnt work on 64 bit hardware?

---

### Post by lidex on 2010-08-09
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Sophont on 2010-08-15
> **deman88 said:**
> could it be my device doesn't work on 64 bit hardware?

I have a Dell XPS 16 and zero problems with sounds.
I installed Ubuntu (64 bit) 9.10 around Alpha 3 last year and then upgraded to 10.04 in April.

This
```
cat /proc/asound/card0/codec#* | grep Codec
```
produces the same
```
Codec: IDT 92HD73C1X5
```
output as you get on your system.

I never made any changes to sound config.

I did none of the things that were mentioned in this thread so far.

I would recommend to boot with a Live CD and see if you still have sound problems - perhaps come config got messed up by something you did earlier?

Let me know if you need any config settings for comparison. But as far as I remember, I have everything regarding sound at default. So a test with a Live CD should give you the same result.

```
dpkg -l alsa*
```
returns
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
un  alsa                           <none>                         (no description available)
ii  alsa-base                      1.0.22.1+dfsg-0ubuntu3         ALSA driver configuration files
un  alsa-oss                       <none>                         (no description available)
ii  alsa-utils                     1.0.22-0ubuntu5                ALSA utilities

```

```
lshw -c SOUND
```
returns
```
  *-multimedia            
       description: Audio device
       product: RV710/730
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:cfeec000-cfeeffff
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fc400000-fc403fff

```

Hm - looks like we have different sound hardware after all.
You got "product: 5 Series/3400 Series Chipset High Definition Audio" where I get "product: 82801I (ICH9 Family) HD Audio Controller".

---

### Post by excetara2 on 2010-11-26
Did you ever figure this out?? I got a replacement Dell and my old one had the IHC9 which worked fine out of the box but now have the 3400 series driver. 

My audio out of the sound card actually works but if I plug in headphones I get nothing. It detects there are headphones plugged in because the speakers shut off but nothing will come out. No matter what settings I change in the sound settings. Anyone figured anything out on this that'd be great.

Cheers

---

### Post by wet-willy on 2010-11-26
> I think it may be a lot with AlsaMixer not sticking, just thinking
> alsamixer STILL won't stick (sudo alsactl store [COLOR="Red"]0[/COLOR])
> aksamixer has speakers at [COLOR="Red"]0[/COLOR] on boot

The proper command is:
```
sudo alsactl store
```

---

