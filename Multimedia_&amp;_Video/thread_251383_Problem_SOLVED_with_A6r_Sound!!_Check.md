---
title: "Problem SOLVED with A6r Sound!! Check"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by Fugazii on 2006-09-05
Hi there Guys!
I will write what you will need for getting sound on A6r 'family' notebooks::

1. Download alsa drivers: alsa-driver-1.0.12, alsa-lib-1.0.12, alsa-utils-1.0.12

2.Unpack them

3.Now open unpacked alsa-driver-1.0.12::
::do::
./configure --with-cards=hda-intel --with-isapnp=no

(note): if You getting error like:::

"checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux-source-2.6.12/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)."

read this topic-> [http://ubuntuforums.org/archive/index.php/t-104882.html](http://ubuntuforums.org/archive/index.php/t-104882.html) and read mo_x answer.

Then when ./configure work fine and it will make: make and make install
::do::
make

then
::do::
sudo make install

when everything will be fine go to alsa-lib dir and
::do::
./configure

then
::do::
sudo make install

When there will be no errors go to alsa-utils dir and
::do::
./configure
(note) when You will recieve error like:

'checking for initscr in -lncurses... no 
checking for initscr in -lcurses... no 
configure: error: this packages requires a curses library'

read this topic-> [http://ubuntuforums.org/showthread.php?t=209576&highlight=checking+initscr](http://ubuntuforums.org/showthread.php?t=209576&highlight=checking+initscr)

and read killerjay_47 answer

when ./configure will run normally now
::do::
sudo make install

4. Configure:

when all packet's will be installed run:

alsaconf

Find there Your soundcard and config it ( just press ok ok ok.... )

When alsa will finish configure Yours soundcard edit file:

mcedit /etc/modprobe.d/alsa-base

and paste there this in last line-> 

options snd-hda-intel model=uniwill-m31

Save file and restart notebook and PRAY!!! =) i think that solution will help with Your soundcard =)

Thx to others who wanted to help with this Problem

---

### Post by mario_7 on 2006-09-10
Everything works except headphones jack - just as it is written in my Alsa bugreport [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2320](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2320) about which i told you last time :)

I tried the newest drivers from Realtek - [http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs) but no changes... I'm going to try Alsa 1.0.13rc1 but have no time for that now... Maybe I'll try to make some changes by myself in the driver, but really not now :)

---

### Post by mario_7 on 2006-12-31
Sorry for my 2nd post, but it is just to let you know that beginning with the newest Alsa (1.0.14rc1) there is a patch for Asus A6R(p) included and there should be no problems with sound :)

Be sure to remove "options snd-hda-intel model=uniwill-m31" from /etc/modprobe.d/alsa-base or it won't work!

---

### Post by sturmdogg on 2007-01-05
has this solved the no microphone problem on the Asus A6R?

---

### Post by pakulo on 2007-01-06
I have just done all from your instruction and got some problems.

System: Ubuntu 6.06.1, laptop: ASUS A6R

Problems begin from "4. Configure:"

Starterd alsaconf, but it said about problems:
> 
No supported PnP or PCI card found.              
Would you like to probe legacy ISA sound cards/chips? 
 <Yes>                  <No>    

i pressed "yes"

> 
Probing legacy ISA cards might make 
 your system unstable. 
 <Yes>              <No> 

"yes" :)

then in the terminal i have got:
> modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8



Then i restart my system, and in terminal i hear some sound (i think it is an internal dynamic), i started BM player, but got:
> Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.

Then in terminal entered aplay, and got:
> ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2143: (snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: audio open error: No such device


In system there are no sound-cards (System->prefs->Sound).

Help me :(, thanks!

P.S.
Sorryr, for my English :(

---

### Post by pakulo on 2007-01-06
I have just recompile sources without "--with-cards=hda-intel --with-isapnp=no", and aslaconf started without problems.
But sound is still don't work :(

---

### Post by pakulo on 2007-01-06
[ lsmod | grep snd ] produces 

snd_atiixp_modem       16264  0
snd_atiixp             19724  1
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_ac97_codec         96804  2 snd_atiixp_modem,snd_atiixp
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm                81032  4 snd_atiixp_modem,snd_atiixp,snd_pcm_oss,snd_ac97_codec
snd_timer              24964  1 snd_pcm
snd                    56164  9 snd_atiixp_modem,snd_atiixp,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  3 snd_atiixp_modem,snd_atiixp,snd_pcm

---

### Post by mario_7 on 2007-02-28
Try ./configure without additional parameters - some A6R laptops haven't got hda-intel compatible sound card onboard (your is ac97)...

---

### Post by enchance on 2007-09-25
I'm getting a problem at the very first step in my A6R. Using the terminal I go to the folder where I extracted alsa-driver-1.0.14 and when I run
```

./configure --with-cards=hda-intel --with-isapnp=no

```

I get the ff error
```

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Did I do anything wrong here?

---

