---
title: "Toshiba Satellite M70-212"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by zoe-scutterbug on 2006-09-04
Firstly intro...

hiya...i am a moderate experience/techno dummy who runs
kubuntu/windows on my laptop and currently panther on a`new second
hand pink 400dl imac.

I love my kubuntu best of all but I have 3 problems (four if you count
me myself too) and I would be naturally very appreciative and keen to
recieve any advice. My brill friend has helped me out on many occasions as
 I am exceedingly good at crashing computers prior to kubuntu.
 I have limited skills with the command line, using adept and synaptic to do most of my installs. here goes.....

my laptop is an ex shop display Toshiba Satellite M70-212
[http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=UK&PRODUCT_ID=113318&DISC_MODEL=1](http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=UK&PRODUCT_ID=113318&DISC_MODEL=1)

ok problemo numero 1...many thanks for any help

 No sound under linux.
(using [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=kmix](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=kmix)
as a guide)

sound works under windows xp

2.  Sound system
manufacturer : Toshiba Bass Enhanced Sound System with SRS(r)
TruSurround XT™ System
supported audio format : 16-bit stereo
supported sound standards : MIDI support
speakers : built-in stereo speakers
microphone : external
type : Realtek ALC250 (on board)
maximum sampling rate : 48 kHz
full duplex support : Yes
direct sound : Yes
direct 3D sound : Yes
volume dial : Yes

3. Cosole

aplay: device_list:221: no soundcards found...
zoe@laptop1:~$ lspci -v

stuff


0000:00:1e.2 Multimedia audio controller: Intel Corporation
82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
       Subsystem: Toshiba America Info Systems: Unknown device ff00
       Flags: bus master, medium devsel, latency 0, IRQ 10
       I/O ports at 1c00 [size=256]
       I/O ports at 18c0 [size=64]
       Memory at b0040800 (32-bit, non-prefetchable) [size=512]
       Memory at b0040400 (32-bit, non-prefetchable) [size=256]
       Capabilities: <available only to root>

more stuff


zoe@laptop1:

4. check [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

failure...soundcard not found

5.
console

zoe@laptop1:~$ sudo modprobe snd-
Password:
FATAL: Module snd_ not found.

6.
console
zoe@laptop1:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
 alsa-base* alsa-utils* linux-sound-base*
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 2294kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135324 files and directories currently installed.)
Removing alsa-base ...
Purging configuration files for alsa-base ...
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing linux-sound-base ...
Purging configuration files for linux-sound-base ...
zoe@laptop1:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
 alsa-base alsa-utils linux-sound-base
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/1189kB of archives.
After unpacking 2294kB of additional disk space will be used.
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
grave bugs of alsa-utils ( -> 1.0.10-1ubuntu14) <done>
 #325142 - alsa-utils conflicts with current udev from testing
 #347204 - alsa-utils: alsa-base should be Depends: not Recommends:
grave bugs of alsa-base ( -> 1.0.10-4ubuntu4) <done>
 #348927 - alsa-base: No sound with Yamaha YMF-774B (DS-1S)
 #349405 - alsa-base: No Sound with Intel 82801DB/DBL/DBM AC'97
Summary:
 alsa-utils(2 bugs), alsa-base(2 bugs)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]


7 oh poo bugs!! but maybe dont sound too bad reports ..here goes

Are you sure you want to install/upgrade the above packages? [Y/n/?/...]  y
DESTROY created new reference to dead object ' Qt::VBoxLayout', <>
line 3 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at
/usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 3.
Use of uninitialized value in substitution (s///) at
/usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at
/usr/share/perl5/Debconf/Format/822.pm line 84.
Selecting previously deselected package linux-sound-base.
(Reading database ... 135215 files and directories currently installed.)
Unpacking linux-sound-base (from
.../linux-sound-base_1.0.10-4ubuntu4_all.deb) ...
Selecting previously deselected package alsa-base.
Unpacking alsa-base (from .../alsa-base_1.0.10-4ubuntu4_all.deb) ...
Selecting previously deselected package alsa-utils.
Unpacking alsa-utils (from .../alsa-utils_1.0.10-1ubuntu14_i386.deb) ...
Setting up linux-sound-base (1.0.10-4ubuntu4) ...
Use of uninitialized value in join or string at
/usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 3.
Use of uninitialized value in substitution (s///) at
/usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 3.
Use of uninitialized value in concatenation (.) or string at
/usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 3.

Setting up alsa-base (1.0.10-4ubuntu4) ...

Setting up alsa-utils (1.0.10-1ubuntu14) .

9. Restart. no sound

10. check again
 zoe@laptop1:~$  aplay -l
aplay: device_list:221: no soundcards found...

11.
zoe@laptop1:~$ sudo apt-get install build-essential
linux-headers-$(uname -r) module-assistant alsa-source
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-9-386

12
zoe@laptop1:~$ sudo apt-get install build-essential linux-headers
Reading package lists... Done
Building dependency tree... Done
Package linux-headers is a virtual package provided by:
 linux-headers-2.6.15-26-server-bigiron 2.6.15-26.46
 linux-headers-2.6.15-26-server 2.6.15-26.46
 linux-headers-2.6.15-26-k7 2.6.15-26.46
 linux-headers-2.6.15-26-686 2.6.15-26.46
 linux-headers-2.6.15-26-386 2.6.15-26.46
 linux-headers-2.6.15-26 2.6.15-26.46
 linux-headers-2.6.15-25-server-bigiron 2.6.15-25.43
 linux-headers-2.6.15-25-server 2.6.15-25.43
 linux-headers-2.6.15-25-k7 2.6.15-25.43
 linux-headers-2.6.15-25-686 2.6.15-25.43
 linux-headers-2.6.15-25-386 2.6.15-25.43
 linux-headers-2.6.15-25 2.6.15-25.43
 linux-headers-2.6.15-23-server-bigiron 2.6.15-23.39
 linux-headers-2.6.15-23-server 2.6.15-23.39
 linux-headers-2.6.15-23-k7 2.6.15-23.39
 linux-headers-2.6.15-23-686 2.6.15-23.39
 linux-headers-2.6.15-23-386 2.6.15-23.39
 linux-headers-2.6.15-23 2.6.15-23.39
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

13.\stuck...help..dunno how to proceed](*,) 

regards
zoe

pssst. remember I am a techno dummy following instructions..I havent
got a real clue what I am actually doing.

---

### Post by sebastfr on 2006-09-05
hello

i have a toshiba laptop too (but a35) with the same ac97 sound card and it works fine...

here are the modules which are loaded on my system:

> 
lsmod | grep snd

snd_intel8x0           30236  1
snd_ac97_codec         83360  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            44704  0
snd_mixer_oss          16384  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              22148  1 snd_pcm
snd                    49024  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm


maybe you should try to insert some of those...

it seems to me (but might be wrong) that the correct modules are not loaded in order for you to use the sound (cf. the error 'no soundcards found')

when the sound card is properly set up with alsa, you should have a '/proc/asound/card0' directory so that's an easy way for you to check.


concerning the linux-headers problem... as you can see, they don't seem to ship the version for your kernel (apparently "2.6.12-9-386" according to your 'uname -r' command).... well maybe you just need to download the kernel sources yourself (from kernel.org). this is the way i've been doing it on my machine as i'm using a custom kernel.

or you may also update your kernel to a 2.6.15xxx version, which is what i would do in your case (this may mean you need to include the "unstable" branch to /etc/apt/sources.list, check a tut on how to do this if needed)

good luck,

seb

---

### Post by tseliot on 2006-09-05
> **zoe-scutterbug said:**
> 11.
zoe@laptop1:~$ sudo apt-get install build-essential
linux-headers-$(uname -r) module-assistant alsa-source
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-9-386
That command is incorrect. What are you trying to do in point 11 ?

If you want to compile an alsa module (?) you should type:
```
sudo module-assistant a-i alsa
```

---

### Post by akak8ty on 2006-09-05
Okay- I'll have to say tseliot comes through diligently with the answers-
I lost my sound last night, and in going through my system I also noted I was running an Unstable release- which I only downloaded a few short weeks ago.
Every thing worked great (sans the xserver issue) But last night I lost my sound, I tried to install a package I was told I was missing which really jammed me up.
Somehow my postscript config started fail
I was concerned it may have disrupted my server which another machine runs xp home- but that is fine. 
Its only my machine that is kafunct.
I have also installed Ubuntu files that have gone into the abyss.
I went on a search and sieze mission, but to no avail.
I want to try the code you have provided and see of I can get my sound back first.
~k

---

### Post by zoe-scutterbug on 2006-09-05
Many thanks for the advice
I am seriously overworked this week (16 hours today inc travel) so it
might be next week I can have another go based on your much
appreciated advice.

yep I def got my stage 11 wrong, due to newbie ignorance and serious lack of sleep..

As a newbie I asked the same question on my local LUG group and two good folks replied with suggestions though folks did get a bit mixed up between ALC250 and 650.

 I am not sure if I should post the advice I recieved from the local group but I have so much to\ learn & take in plus there are so many basic things i should really know about before going further. 

I love me linux (far better than my new cheap pink`imac) but I do want my sound, wireless and printer all working too ;)))

I am hopeless at reading maybe I should wishfully find a linux evening course.



*****************
A's replied
  2.  Sound system
> type : Realtek ALC250 (on board)

This is the key piece of information. Googling for 'realtek ALC250 alsa'
finds

<http://www.bruceshankle.com/_mgxroot/page_10767.html>

which suggests that the ALC250 chipset is supported by ALSA (or version
1.0.11rc4, at least, which is slightly newer than your version of Kubuntu
provides, which *may* be some/all of the problem).

That page links to
<http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp>
which suggests that the driver module is named snd-card-atiixp, therefore,
you should have done:

$ sudo modprobe snd-card-atiixp; sudo modprobe snd-pcm-oss; sudo \
   modprobe snd-mixer-oss; sudo modprobe snd-seq-oss

rather than

> 5.
> console
>
> zoe at laptop1:~$ sudo modprobe snd-
> Password:
> FATAL: Module snd_ not found.

***********************

B responded

On my crusty old Debian/Sarge machine:

$ dpkg -s alsa-base | grep ^Version
Version: 1.0.8-7


$ strings
/lib/modules/2.6.8-1-686/kernel/sound/pci/ac97/snd-ac97-codec.ko
| grep ALC250
ALC250


This suggests to me that there was (some) ALC250
support back in Debian's alsa-1.0.8 (so is probably
supported in Kubuntu's current alsa modules too).  

Also, if the snd-atiixp driver doesn't do the trick,
the snd-intel8x0 driver _might_ succeed:

$ strings
/lib/modules/2.6.8-1-686/kernel/sound/pci/snd-intel8x0.ko
| grep ICH6
info_devices={{Intel,82801AA-ICH},{Intel,82901AB-ICH0},{Intel,82801BA-ICH2},{Intel,82801CA-ICH3},{Intel,82801DB-ICH4},{Intel,ICH5},{Intel,ICH6},{Intel,6300ESB},{Intel,MX440},{SiS,SI7012},{NVidia,nForce
Audio},{NVidia,nForce2
Audio},{AMD,AMD768},{AMD,AMD8111},{ALI,M5455}}
Intel ICH6

*****************

many thanks

zoe

---

