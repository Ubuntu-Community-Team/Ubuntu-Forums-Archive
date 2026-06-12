---
title: "No sound on toshiba netbook"
date: 2010-04-18
forum: Multimedia Software
---

### Post by withnail420 on 2010-04-18
Can't find anything in any other threads...all volume controls are up, all updates applied. Help!

---

### Post by Yellow Pasque on 2010-04-18
More info. At tlease the output of:
```
aplay -l
```

---

### Post by lidex on 2010-04-18
Yes, more. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by withnail420 on 2010-04-19
> **lidex said:**
> Yes, more. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Ok guys, sorry for not giving enough information.
```
d@sniffy:~$ uname -a
Linux sniffy 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
d@sniffy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
d@sniffy:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
d@sniffy:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272
d@sniffy:~$ 

```
Netbook model is a Toshiba Mini NB200.

The software seems to think everything is fine, but the hardware doesn't want to know.

---

### Post by Ulysses361 on 2010-04-19
Please try this solution procedure:

[https://answers.launchpad.net/ubuntu/+question/106135](https://answers.launchpad.net/ubuntu/+question/106135)

---

### Post by withnail420 on 2010-04-19
edit: Never mind previous post....

Got as far as ```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```
and got this error
```
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.22/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.22/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.22/alsaconf'
make: *** [all-recursive] Error 1

```
This is an error that sudo make throws. I have no god damn clue what to do with this now. I just had to install 229mbs of files because my system didn't have xmlto installed.
I'm getting incredibly mad now.

---

### Post by withnail420 on 2010-04-19
god damn bump.

---

### Post by Yellow Pasque on 2010-04-19
If you're trying to build the latest ALSA, there's a script that does it for you: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Before you run it, edit hte version lines near the top:
```
PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17
}
```

---

### Post by withnail420 on 2010-04-19
> **Temüjin said:**
> If you're trying to build the latest ALSA, there's a script that does it for you: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Before you run it, edit hte version lines near the top:
```
PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17
}
```

Just installed the alsa-source from lucid and still not getting anything.
All the software still reports it as working, but the hardware doesn't work.
There is no emoticon to describe the rage.

---

### Post by Yellow Pasque on 2010-04-19
Try the script. It builds the newest ALSA if you edit it like I posted...

---

### Post by withnail420 on 2010-04-19
> **Temüjin said:**
> Try the script. It builds the newest ALSA if you edit it like I posted...

i have installed alsa-unstable. It doesn't work. Like I posted.

---

### Post by Yellow Pasque on 2010-04-19
You said you used ALSA source, which is 1.0.22.x...
I was suggesting try ALSA 1.0.23

---

### Post by withnail420 on 2010-04-19
> **Temüjin said:**
> You said you used ALSA source, which is 1.0.22.x...
I was suggesting try ALSA 1.0.23

After a bit more digging it looks like it's a driver issue. lspci reports my soundcard to be this
```
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
and all I can find here and on google are other people with the same problem. Sucks.

---

### Post by lidex on 2010-04-19
Did you add the options to your alsa-base .conf?
> 1. Open a terminal and use the gedit editor to edit /etc/modprobe.d/alsa-base.conf as follows:

Run the following command in a Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

When the file is open, please add the following 3 lines to the end of the file after "options snd-pcsp index=-2"

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=toshiba-nb200

2. Save/close, reboot and retest sound via speakers

---

### Post by Yellow Pasque on 2010-04-19
> **lidex said:**
> model=toshiba-nb200
Where did you get this model keyword? I don't see it on the ALSA 1.0.23 list..
```
ALC662/663/272
==============
3stack-dig    3-stack (2-channel) with SPDIF
3stack-6ch     3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig     6-stack with SPDIF
lenovo-101e    Lenovo laptop
eeepc-p701    ASUS Eeepc P701
eeepc-ep20    ASUS Eeepc EP20
ecs           ECS/Foxconn mobo
m51va         ASUS M51VA
g71v          ASUS G71V
h13           ASUS H13
g50v          ASUS G50V
asus-mode1    ASUS
asus-mode2    ASUS
asus-mode3    ASUS
asus-mode4    ASUS
asus-mode5    ASUS
asus-mode6    ASUS
dell          Dell with ALC272
dell-zm1      Dell ZM1 with ALC272
samsung-nc10  Samsung NC10 mini notebook
auto          auto-config reading BIOS (default)
```
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)

---

### Post by lidex on 2010-04-19
> **Temüjin said:**
> Where did you get this model keyword? I don't see it on the ALSA 1.0.23 list..


Yeah, I wondered about that myself. Seems 'made up', to me. I quoted it from the launchpad page *withnail420* was working from; posted by *Ulysses361*:
[https://answers.launchpad.net/ubuntu/+question/106135]("https://answers.launchpad.net/ubuntu/+question/106135")

---

### Post by djmoore85 on 2010-04-28
Not to piggyback off this thread, but same issue, Toshiba NB205-N312 netbook. Just installed Lucid, and excited, camera and mic are picking up right out of the gate but no sound OUTput. Only reason i assume mic is working is that when playing with sound preferences it is showing input levels and they are fluctuating as they should when speaking into it. Anyone come up with a straightforward sound solution for the Toshiba netbook hardware? Or at least a working one?

---

### Post by withnail420 on 2010-05-23
Thought I would bump this thread as I have solved the problem.
The instructions here
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
work in 10.04, although they are for an earlier version. Glad to finally fix it.
It involves removing pulseaudio and alsa, and installing OSS and esound. 
Hope this helps somebody.

---

### Post by withnail420 on 2010-05-23
> **lidex said:**
> Yeah, I wondered about that myself. Seems 'made up', to me. I quoted it from the launchpad page *withnail420* was working from; posted by *Ulysses361*:
[https://answers.launchpad.net/ubuntu/+question/106135]("https://answers.launchpad.net/ubuntu/+question/106135")

Sigh. Why the hell would I make up my netbook model? Jesus...

---

### Post by lidex on 2010-05-23
> **withnail420 said:**
> Sigh. Why the hell would I make up my netbook model? Jesus...

Sorry. Not saying you made it up, but it's not shown as an working option in alsa documentation. It would be easy for someone to see the other options that apply to specific models, using the model name, and assume it works that way for all, when it doesn't. Not referring to your netbook model, just the option model. I believe you. ;)

---

### Post by lidex on 2010-05-23
BTW, this seems to work also.
1) Upgrade to latest alsa (currently 1.0.23)

2) Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.

---

### Post by withnail420 on 2010-05-23
> **lidex said:**
> Sorry. Not saying you made it up, but it's not shown as an working option in alsa documentation. It would be easy for someone to see the other options that apply to specific models, using the model name, and assume it works that way for all, when it doesn't. Not referring to your netbook model, just the option model. I believe you. ;)

Hehe, fair enough.
I ended up having no joy with alsa here (only got headphones working with that and pulse), it's running just on OSS. It's like I'm really back in 2004.

---

### Post by mtalexan on 2010-07-05
> **withnail420 said:**
> Hehe, fair enough.
I ended up having no joy with alsa here (only got headphones working with that and pulse), it's running just on OSS. It's like I'm really back in 2004.

I know what you mean.  I had to change all my audio support over to OSS when I first installed 9.04, and it was a mess until I upgraded to 10.04.  You can't use Skype, even though you have a nice webcam and mic built in, because Skype doesn't support their OSS version anymore, and all the audio settings are very non-user friendly, just like 2004 all over again.  Hopefully the ALSA upgrade will fix the issues the Ubuntu update caused for me when it tried to force me back to using Pulse Audio instead of OSS.  Here's hoping.

---

