---
title: "No sound in Ubuntu dapper. hda-intel card. Toshiba sat pro p100-187 laptop"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by maladath on 2006-09-06
So, like quite a few other people it seems, I also have trouble with sound in Ubuntu 6.06. There is no sound. I have tried numerous troubleshooters and guides, including the comprehensive sound problem solutions guide on the forum here. After I downloaded, installed and ran and tested for a few days, and nothing worked, I decided to reinstall ubuntu and have a clean install to work from. So im on scratch.

Details:I have a toshiba sat pro p100-187 laptop. Sound works perfectly in windows

Card: HDA Intel

**aplay -l result:** 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**Relevant lspci -v result:** 0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>


So at least it seems ubuntu finds my soundcard.

I have two cannels avaliable to view in alsamixer. Master and PCM. Master is not muted hile PCM does not have the option of being muted/unmuted. All other sound settings in ubuntu are unmuted and have sufficient volume.

I followed the stickyed guide on the forum here, I found the driver for my cards chipset on the alsa-project.org site, which would be the hda-intel one. I run: sudo modprobe snd-hda-intel. I type in my admin pass, but nothing happends... I dont get an error message, but nothing happends and there is no sound.

I tried both the following options afterwards, Getting the ALSA drivers from a fresh kernel and the alsa driver compilation step. None fixed my problem. Still no sound. 

Any ideas?

---

### Post by maladath on 2006-09-08
I dare to invoke a little bump here.

 Im a nubcake when it comes to Linux, having installed ubuntu as my first distro only a few days ago, so would really appreciate some input. Realize there are a lot of sound problem posts, but as my attempts to solve the problem using tips and guides has been to no avail so far, I guess maybe my problem might be elsewhere.

---

### Post by xinel on 2006-09-08
Ive been trying to solve this same problem for months now. Its not your fault, I think we might just have to wait for new alsa drivers :(

---

### Post by gniss on 2006-09-14
Same problem and details here with a Toshiba P105-S9312

---

### Post by maladath on 2006-09-16
kk. Thanks for the replies people. Ill watch out for new alsa drivers and make sure I post on here if I resolve the problem of course.

---

### Post by johnwlittle on 2006-09-16
I have a p105 with the Intel HDA sound and it's an ALSA issue. We might have to wait for new drivers. I'm just now looking into it but I'm not sure if anyones found a fix for the low volume/quality issue.

If you don't have sound at all you'll need to edit /boot/grub/menu.lst to add acpi=off   

Here are the relevant parts from mine:

> 
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro [COLOR="blue"]acpi=off[/COLOR]

#### DELETED STUFF #####

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash [COLOR="blue"]acpi=off[/COLOR]
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot


You may not need it in both spots and if you have multiple kernels you may want to add it to those as well. It only gets you halfway there but low crappy sound is better than none.

---

### Post by gniss on 2006-09-17
Found a solution: boot with acpi=off fixes the problem for me...

---

### Post by strgt on 2006-09-19
> **johnwlittle said:**
> It only gets you halfway there but low crappy sound is better than none.

The ACPI=off thing did work on my P105-S921 but it sounds low and crappy. Anyone knows if it will get better someday?

---

### Post by zgornel on 2006-09-19
Try and get a 2.4.x kernel and see if it works. It's hardly a solution but a laptop with no ACPI is ueless. Plus, the sound is crappy ;)

---

### Post by BillMeyer on 2006-09-23
Toshiba Satellite P100-221
Same issues here. acpi=off works - but sound is very low and crappy.

---

### Post by jtaylor on 2006-09-23
I get sound out of the box on my P100-SD300 but the sound is extremely quiet.

---

### Post by Daniel15 on 2006-09-26
The sound works for me (no volume problems), but in some games, the sound seems to 'stutter'. In Super Tux, Planet Penguin Racer, and Unreal Tournament, the sound works perfectly. However, in DOSBox, there's no sound at all, and in Nexuiz, the sound stutters. Wine crashes when I run 'winecfg' and click the Sound tab. 

Is there a fix for any of these problems?

---

### Post by jtaylor on 2006-10-20
I had a problem of low sound quality.

I am tremoundously pleased that this patch fixed it!:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

Cheers.
Jon.

---

### Post by dfraser on 2006-11-03
Does this patch fix the initial problem or only work if acpi=off? 

BTW I am a complete newbie to Ubuntu and don't know how to apply a patch to alsa, could one of you kind folk out there please give me step by step instructions a lifetime windows user would understand?

Cheers
Dave

---

### Post by LarsBjerregaard on 2006-11-10
Posting this in case it helps anybody.

Sound worked for me in Ubuntu Breezy, but in a completely new install of Dapper - no sound at all.
I see many people all over the place struggling with this. After many hours of googling, I found a simple workaround which works for me. It was described on: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038)

So basically what I did (as root):
1) Backup /etc/modprobe.d/alsa-base
2) Add to the bottom of /etc/modprobe.d/alsa-base: options snd-hda-intel model=ref
3) Reboot

Voila! Sound works.

My system:

Dell Dimension 9150

OS: Ubuntu Dapper (6.06 LTS)

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

lspci -vv | fgrep Audio:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

cat /proc/asound/card0/codec#0:
Codec: SigmaTel STAC9221 A1

The problem seems to be Alsa headaches with STAC9221, and also seems to be fixed upstream now.

---

### Post by Avian00 on 2006-12-12
> **jtaylor said:**
> I had a problem of low sound quality.

I am tremoundously pleased that this patch fixed it!:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

Cheers.
Jon.

Any chance this patch allows me to have Sound *and* ACPI at the same time?

---

### Post by Avian00 on 2006-12-14
By passing the "acpi=off" argument to my kernel at boot time, I magically get sound! Now my question becomes, if disabling ACPI fixes my found, is the problem really with my sound card driver? My working theory is that ACPI turns my speakers amplifiers off. In that case, it's really an ACPI problem and not an ALSA problem (as many other forums have suggested). What do others think of this theory?

---

### Post by elv on 2006-12-24
I am having simial problems with my new Gateway laptop.But the acpi=off dosent work, compiling Alsa dosent work, so no sound for......and I only use my computer for audio work lol
I think it is really amazing how many people are having trouble with soundchip.And it is supposed to be the next AC97 with multichannel audio.

---

### Post by ClintiePoo on 2006-12-27
> **LarsBjerregaard said:**
> Posting this in case it helps anybody.

Sound worked for me in Ubuntu Breezy, but in a completely new install of Dapper - no sound at all.
I see many people all over the place struggling with this. After many hours of googling, I found a simple workaround which works for me. It was described on: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038)

So basically what I did (as root):
1) Backup /etc/modprobe.d/alsa-base
2) Add to the bottom of /etc/modprobe.d/alsa-base: options snd-hda-intel model=ref
3) Reboot

Voila! Sound works.

My system:

Dell Dimension 9150

OS: Ubuntu Dapper (6.06 LTS)

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

lspci -vv | fgrep Audio:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

cat /proc/asound/card0/codec#0:
Codec: SigmaTel STAC9221 A1

The problem seems to be Alsa headaches with STAC9221, and also seems to be fixed upstream now.

I also have a Dell Dimension 9150 with the same setup.  That worked perfectly. Thanks!

---

### Post by naaman on 2007-01-03
Give [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) a go, it's the steps that worked for me.

For the record, I didn't have to create an /etc/modprobe.d/alsa (or similar file) nor did I turn acpi off.  My laptop is a HP Pavillion dv5129TX.

---

### Post by dfraser on 2007-01-10
I still can't get sound to happen without acpi=off, now after installing beryl and using the nVidia  driver acpi=off wont load into X. (I'm guessing the GPU relies on ACPI [i'm fairly n00bish where all this is concerned])

The only thing I'd like to try would be a DSDT patch but I don't trust myself and actually have no idea what DSDT is. The people over at Gentoo seem to be able to do it but, like i said, i'm a n00b.

Here is the link [http://forums.gentoo.org/viewtopic-t-444743.html]("http://forums.gentoo.org/viewtopic-t-444743.html")

---

### Post by dags on 2007-01-24
> **Avian00 said:**
> By passing the "acpi=off" argument to my kernel at boot time, I magically get sound! Now my question becomes, if disabling ACPI fixes my found, is the problem really with my sound card driver? My working theory is that ACPI turns my speakers amplifiers off. In that case, it's really an ACPI problem and not an ALSA problem (as many other forums have suggested). What do others think of this theory?

Look I'm not an Ubuntu user (yet :)  but I have the exact same problem with my P100 - 103 and I'm using windows XP. I had to set ACIP=off in order to get my external sound interface (Presonus Firebox) to stop clicking and popping. Now the clicks and pops have stopped but the sound from the internal sound card is really low as most of you describe.

So all of you looking in Ubuntu for a resolution should concentrate in other areas. Obviously the problem is not with the OS. It's most likely the sound chip Toshiba used in these machines (in my case Connextant but there are various P100 models using various chips). Strange thing is that in windows it has problems with ACPI=off but in Ubuntu it has similar problems with ACPI=on. In any case the problem lies in the Conextant chip and ACPI. 

Has anyone here contacted Toshiba for answers?

---

### Post by Avian00 on 2007-01-24
> **dags said:**
> Look I'm not an Ubuntu user (yet :)  but I have the exact same problem with my P100 - 103 and I'm using windows XP. I had to set ACIP=off in order to get my external sound interface (Presonus Firebox) to stop clicking and popping. Now the clicks and pops have stopped but the sound from the internal sound card is really low as most of you describe.

So all of you looking in Ubuntu for a resolution should concentrate in other areas. Obviously the problem is not with the OS. It's most likely the sound chip Toshiba used in these machines (in my case Connextant but there are various P100 models using various chips). Strange thing is that in windows it has problems with ACPI=off but in Ubuntu it has similar problems with ACPI=on. In any case the problem lies in the Conextant chip and ACPI. 

Has anyone here contacted Toshiba for answers?

I haven't contacted Toshiba (I'm not very optimistic of the response I'd receive).  However, in response to the low sound, I've managed to fix that by downloading and compiling the latest version of ALSA.  You can read about how to do that here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Dusolais on 2007-01-27
The 'acpi=off' kernel boot flag also works for me. Not sure if its quieter than it was in windows cause its been unworking for so long :). I also have this line 'option snd-hda-intel model=3stack' in /dev/modprobe.d/alsa-base, not sure if that does anything now i could probably remove it.

I would love to know if/when anyone finds a proper fix for this.. 
Thanks
Alex.
(alex@quosmo.com)

My system:
Toshiba Satellite p100 series

---

### Post by klaas on 2007-01-31
This is how i fixed this problem for my Toshiba Satellite P100-343 (bios 3.30): [http://www.ubuntuforums.org/showthread.php?t=349491](http://www.ubuntuforums.org/showthread.php?t=349491).

Greetz,
Klaas

---

### Post by quickwitt on 2007-03-24
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

gksudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop-eadp

Worked for my Toshiba U205

:)

Seems the system sounds are back but no multimedia.
:(

---

### Post by quickwitt on 2007-03-26
The above procedure DID work to restore sound. After compiling ALSA and editing /etc/modprobe.d/alsa-base I had to go into settings=>sounds and select ALSA for every output. Reboot and it works!

One interesting thing I noted the next day; I dual boot Win XP, if sound is muted in XP and I boot into Ubuntu.... No sound. If I unmute in Xp and boot into Ubuntu sound works. Not sure how that is possible (maybe because sound is hardware controlled?) but it is true.

hope this helps someone.

---

### Post by rocketbomb on 2007-04-15
I have googled through many forums to find how to fix the problem on my linux box , ASUS a8jn notebook. many configurations has been tested and several driver versions were  recompiled. Luckily, I found a parameter for my asus notebook. After everything works fine I decided to post the solution in my blog but it may be work on some brands and models. Anyway there is nothing to lose for another try. at least I hope this could be a guideline.

[http://rocketbomb.bloggang.com](http://rocketbomb.bloggang.com)

---

### Post by djbenny on 2007-05-21
it says permission denied when trying to edit menu.lst and secondly how do i install that patch?

thanks

---

### Post by zanjabeel5 on 2007-05-21
@djbenny

gksudo gedit /boot/grub/menu.lst

enter your password.
to install the patch follow
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

good luck

---

### Post by djbenny on 2007-05-21
> **zanjabeel5 said:**
> @djbenny

gksudo gedit /boot/grub/menu.lst

enter your password.
to install the patch follow
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

good luck


i edited it rebooted and then it come up saying the x server could not be started!

please help

---

### Post by stchman on 2007-05-21
> **maladath said:**
> So, like quite a few other people it seems, I also have trouble with sound in Ubuntu 6.06. There is no sound. I have tried numerous troubleshooters and guides, including the comprehensive sound problem solutions guide on the forum here. After I downloaded, installed and ran and tested for a few days, and nothing worked, I decided to reinstall ubuntu and have a clean install to work from. So im on scratch.

Details:I have a toshiba sat pro p100-187 laptop. Sound works perfectly in windows

Card: HDA Intel

**aplay -l result:** 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**Relevant lspci -v result:** 0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>


So at least it seems ubuntu finds my soundcard.

I have two cannels avaliable to view in alsamixer. Master and PCM. Master is not muted hile PCM does not have the option of being muted/unmuted. All other sound settings in ubuntu are unmuted and have sufficient volume.

I followed the stickyed guide on the forum here, I found the driver for my cards chipset on the alsa-project.org site, which would be the hda-intel one. I run: sudo modprobe snd-hda-intel. I type in my admin pass, but nothing happends... I dont get an error message, but nothing happends and there is no sound.

I tried both the following options afterwards, Getting the ALSA drivers from a fresh kernel and the alsa driver compilation step. None fixed my problem. Still no sound. 

Any ideas?

My laptop has an SB450 (Intel sound card but says it is ATI) sound card and the sound did not work with Feisty.  Follow the procedure I have laid out here on my website:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

You invoke the hda-intel command so it should work for you.

It worked like a charm for me.

Hope this helps.

---

### Post by rocketbomb on 2007-08-02
there is a solution in [www.techindepth.net ]("http://www.techindepth.net")

---

### Post by doctorbaldwin on 2007-08-05
This problem has been solved for some Toshiba P100 models by patching the DSDT.  Check out [http://ubuntuforums.org/showthread.php?t=349491]("http://ubuntuforums.org/showthread.php?t=349491")

I got sound working on my P100-ST7211 after a LONG time trying using the directions here.  It's a pretty simple fix.  Check page 6 on that thread for my specs.

---

### Post by oxygenws on 2007-09-04
try this post, it helps me:
[http://ubuntuforums.org/showpost.php?p=1357412&postcount=23](http://ubuntuforums.org/showpost.php?p=1357412&postcount=23)

---

