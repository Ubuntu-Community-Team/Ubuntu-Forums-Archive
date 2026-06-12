---
title: "snd_hda_intel options database"
date: 2009-01-18
forum: Multimedia Software
---

### Post by markbuntu on 2009-01-18
**snd- intel-hda options Database**

**Please do not post problems or ask for help here**

**The list has been updated to include everything up to post 81 so you do not need to wade through them, I already did that for you. Thanks to everyone who contributed.**

As many of you have found out, there are hundreds of laptops and motherboards out there and every one of them seems to need its own particular option added to the /etc/modprobe.d/alsa-base file to operate properly.  

I have begun to put together this database of options for specific makes and models.  It is not much but it is a start and with your help we can make it bigger and better. The idea is to get all the information in one place.

If you have found the option that works with your particular make and model, please post in this thread and I will add it to the database.   When posting please include the make and model of your machine or motherboard, the alsa version, and the alsa-base option or options. Also please report if the mic/speaker or digital output switches work if you have tested them or anything else you think people should know. Some of these options also require alsa 1.0.18 or 19 or .20 or.21. I have tried to note this where information was made available to me but, as I said, this is user supplied info and much is taken from other posts and elsewhere so this sort of information was not always available.

If you find a thread that may be helpful please post a link.

To use the database, find the make and model of your machine and then open the alsa-base file as root so you can edit it
```

sudo gedit /etc/modprobe.d/alsa-base

```

(If you are using Jaunty the file name has changed to alsa-base.conf to conform to the new configuration file naming convention)

at the end of the file add

```

options snd-hda-intel xxx...=xxxx....

```
replacing the xxxx with the option you found. More than one option may be necessary and can be placed on the same line. You will see examples below. If there is more than one line listed after your machine, use them as listed.

Restart alsa. 
```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```
(You also may be able to just log out and log back in but you may need to reboot for the option to be implemented.)

The database is arranged by manufacturer and model. If there is no option listed for your machine you should try the options used for similar machines. Some dell and compaq models have been reported to work with hp options and some hps with toshiba options so you can see how confusing this is getting.

These are options as reported by users so there may be errors. If you have found an option that works better, please let us know. There are also some links at the end for more options and other help with sound.

ACER , options snd-hda-intel model=acer
Aspire 4710, Aspire 5600,Travelmate         options snd-hda-intel model=acer
Aspire 9810                                   model=acer-aspire
5920g,Aspire 8930,                               model=auto
M50sa-x1                                      model=haier-w66
Acer Aspire 9815WKMi   options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
                       options snd-hda-intel model=acer-aspire position_fix=1 enable=yes  
Aspire5536-5883   options snd-hda-intel model=auto(no built in mic)
Aspire 6920G (codec ALC889)
ALSA 1.0.20
options snd-hda-intel model=auto

Advent 6555 (MSI GT725)
options snd-hda-intel probe_mask=1
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
options snd-hda-intel model=targa-dig

Alienware
M9750                                         model=6stack-dig

ASUS
A7J                                           model= asus-a7j
A7M                                           model=asus-a7m
F2/F3                                         model= asus-laptop
F6A-2                                     model=6stack
                                          enable_msi=1
                                          single_cmd=1
G50v                                          model=g50v
G71v                                          model=g71v
H13                                           model=h13
M2R32-MVP                                     model=6stack
M51SN-AP067G                                  model=lenovo
NV80                                          model=g50v position_fix=0
X20G, U1E                                     model=lenovo
W2JC                                          model=w2jc
Eeepc P701                                    model=eeepc-p701
Eeepc-EP20                                    model=eeepc-ep20

Compaq
Compaq CQ40, CQ71 
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
Compaq 6735s
options snd-hda-intel model=laptop


Dell                                          model=dell
T3400, Vostro 1200                            model=dell
XPS 410                                      model=dell-bios
Dimension E520                                model=dell-3stack
Dimension 9150                               model=dell-m81
Inspirion 1420n options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
Adamo
options snd-hda-intel model=dell-eq
Dell M1330, model=dell-3stack
dell vostro 1000 / inspirion 1501   model=dell-m23
  
1526                                    model=dell-m81
Inspirion 530                             model=6stack-dell
desktops                                  model=dell-m4-1    STAC92HD71B
                                          model=dell-m4-2    STAC92HD71B
                                          model=dell-m6         STAC92HD73
                                          model=dell-bios       STAC92HD73
Studio 540                               snd_hda_intel probe_mask=1              


Fujitsu                                   model=fujitsu
Pi1536                                    model= 3stack-dig
Pi2515                                    model= fujitsu-pi2515
The following needs Alsa 1.0.19 or later
Pi3540                                    model=fujitsu-xa3530
xa3530

Gateway                                 model=gateway
gt5405e                                 model=gateway
T-1616                                  model=dell-m42
mx (not all)                            model=m2-2
nx  (not all)                           model=m6
P-6831FX, 6860-fx
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1

HP                                      model=hp
tx1000, tx2000z                                  model=hp
3013                                    model=hp-3013
nx6325                                  model=toshiba
6535b                                   model=laptop
6735s                                   model=laptop enable_msi=1  
TX2635us (tx2500 series)      model=toshiba position_fix=1
xw4400/6400, 8400/9400                  model=hp-bpc
BPC D7000                               model=hp-d7000
Thin Client  T5735                      model=hp-tc-t5735
dv4-1120us, dv4-1124nr, dv4-1124cl, dv4-1150, dv4-1000ea, dv7   enable_msi=1
dv5 (some), dv4z            model=dv5
dv4-1210ef
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
dv5 (some)
options snd_slots=snd-hda-intel
options snd-hda-intel enable_msi=1 singel_cmd=1
hptx2510us model=toshiba position_fix=1
or
options snd-hda-intel model=zepto position_fix=1
dv6
options snd-hda-intel model=dell-m4-3 enable_msi=1
dv7t-2000
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-Upgrade ALSA to 1.0.19
HP dv5 -1235dx l
HP DV3510nr
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
HP dv6 1100.EO
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
HP DV6z 
ALSA  1.0.20 
options snd-hda-intel model=dell-m4 enable_msi=1
HP Pavilion DV 3500 or DV 3000
options snd-hda-intel model=dell-m4-1
hp dv6-1007tx
alsa 1.0.21
options snd_hda_intel model=hp-dv5
HPdv6t-1200
option snd-hda-intel model=dell-m4-1
HP Pavilion DV7-1002tx
ALSA 1.0.21
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
HPDV7-1125ea
options snd-hda-intel enable_msi=1
(no subwoofer)
Hp Pavilion Dv6-1108sl
alsa 1.0.20
snd-hda-intel model=dell-m4-3 enable_msi=1
(no headphone/ext mic)
HP HDX9300
options snd-hda-intel model=5stack position_fix=0 probe_mask=-1 bdl_pos_adj=-1 enable=yes
(no heaphone jack 1)
HP TouchSmartPC tx2 - 1025dx
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

Lenovo                                  model=lenovo
3000, C200                              model=lenovo
101e                                    model=lenovo-101e
3000 N100                               model=6stack
MS7195                                  model=lenovo-ms7195
NB0763                                  model=lenovo-nb0763
Thinkpad, X300, T60/X60/Z60/T61/X61     model=thinkpad
y410                                    model=lenovo-3000

LG                                      model =lg
LW20/LW25                               model=lg-lw

Mac
iMac (24inch)                           model=imac24
Macpro                                  model=macpro
Macbook Pro rev3                        model=mbp3

MEDION MD 96380                        model=lenovo-nb0763 

MSI
M662                                     model=targa-dig
                                         model=targa-2ch-dig

Packard Bell
Easynote                                 model=3stack
See post #4

Samsung                                 model=laptop
M50                                     model=laptop
R65                                      model=laptop-eapd
Ultra tablet pc                          model=ultra

Sony                                     model=sony
Vaio                                     model=sony
VGN-FZ35M, VGN-SZ750N, S460N/C           model=vaio
Vaio VGN-CS360A,                         model=toshiba-s06


Toshiba                                  model=toshiba
A200                                     model=lenovo
A205, Tecra A10, U205                    model=toshiba 
A135-S4577                               model=3stack (no mic/spkr switch)
L30-106                                  model=dallas
L35-S2174                                model=6stack-digout
Satellite A100-192                       model=3stack

**ALC889 on Acer Aspire 6920G**

[http://ubuntuforums.org/showthread.php?t=1013750](http://ubuntuforums.org/showthread.php?t=1013750)

**ALC1200**
Alsa 1.0.17 or 1.0.18

options snd-hda-intel probe_mask=1

**More Stuff to try**
These links have many more options that may be helpful for you. These lists are by sound chip type rather than make and model. If your machine is not listed you can try other options available for that chip. 

Temujin also has many options listed here

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

And there is a large list of options from Donny K. here

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

For more hda troubleshooting help you can go here

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

**Upgrading ALSA**
If you have a newer model machine you may get better support from the newest version of Alsa.

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

You can also get the debs for ALSA 1.0.19 for Hardy and Intrepid and Jaunty from here

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

** General help**

For a quick guide to getting sound setup in Hardy and Intrepid

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
 
For Jaunty

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

For more extensive sound troubleshooting and setup

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thank you for all your help and best regards. 
mark

P.S. To all who gave thanks, you are entirely welcome.

---

### Post by hugoheden on 2009-02-01
Sound (the speakers) suddenly started working when I added

   > options snd-hda-intel model=dell-m81

at the end of /etc/modprobe.d/alsa-base (and rebooted), as suggested by [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) -- Donny K. Also tried dell-d81 and dell-d82, but neither of them seemed to work.

Dell Dimension 9150. 

> $ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> $ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9221 A1


> $ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


> When posting please include the make and model of your machine or motherboard, the alsa version, and the alsa-base option or options.


If needed, let me know how to get that information.. Currently running an updated Intrepid.

---

### Post by hugoheden on 2009-02-02
PS: Just a quick check: You wrote 

> options snd_hda-intel model=xxxxx

-- are you sure it works with the underscore (snd_hda-intel)? Most other sources use a dash (snd-hda-intel).

---

### Post by Eric06 on 2009-02-25
Addition to your database (i am so glad sound works :p )

Ubuntu 8.10
Packard bell laptop Easynote RS65-M023FR pn=PC28E01502
windows = sound ok; ubuntu no sound +

config:

cat /proc/asound/cards
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfdcf8000 irq 22
1 [HDMI ]: HDA-Intel - HDA ATI HDMI
HDA ATI HDMI at 0xfddec000 irq 17

cat /proc/asound/modules
0 snd_hda_intel
1 snd_hda_intel

aplay -l
**** Liste des PLAYBACK périphériques ****
carte 0: Intel [HDA Intel], périphérique 0 : ALC663 Analog [ALC663 Analog]
Sous-périphériques: 0/1
Sous-périphérique: #0: subdevice #0
carte 1: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI]
Sous-périphériques: 1/1
Sous-périphérique: #0: subdevice #0

Upgraded to ALSA 1.0.19 without problem using the script from the forum

I added the following line at the end of /etc/modbase.d/alsa-base file:
options snd-hda-intel model=m51va

there are mutiple values that get the speakers to work but not the headset... so i tryed all the ones corresponding to my hardware device to test them (lots of 'sudo alsa force-reload' and 'alsamixer' commands during the test)

summary of the behaviors i see on my machine: 

#ALC662/663:HP/mic/headset/ touchpad
#3stack-dig: ok/no/no
#3stack-6ch: ok/ no/no
#3stack-6ch-dig: ok/no/ no
#6stack-dig: ok / no / no
#lenovo-101e: ok / lo / no/ no
#eeepc-p701: bad sound
#eeepc-ep20: ok / no / no / no
#m51va: ok / lo / ok / part
#g71v: ok / no / ok / part
#h13 : ok / low/ ok / part
#g50v: ok / no / no / part
# auto: no sound

I did not get good results on MIC and I did not test the HDMI ouput too

Thanks to you forum gurus ):P

---

### Post by markbuntu on 2009-02-25
> **hugoheden said:**
> PS: Just a quick check: You wrote 



-- are you sure it works with the underscore (snd_hda-intel)? Most other sources use a dash (snd-hda-intel).

OK, I fixed that.

---

### Post by rztmartini on 2009-03-11
okay i have the Asus G50V and was having earlier issues with the wireless card working. i found a thread on the forum that gave 2 lines of script that fixed it, but then the sound went out. ive tried your method, as well as a couple others but still have no sound. any other ideas?? thanks.

---

### Post by markbuntu on 2009-03-11
What is this script and when do you run it?

---

### Post by athaki on 2009-03-12
option ```
options snd-hda-intel model=gateway
``` 
works for my Gateway GT5405E with  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01).  It took the buzzing away that is used to have.  Thanks a million.

---

### Post by Username4 on 2009-03-18
An addition to your database:

Fujitsu Pi3540 model=fujitsu-xa3530

I haven't tested everything but finally my built-in mic works as well as built-in speakers. There are now enough channels in the mixer to suppose that everything else works too.

Xa3530 model probably also works with this. This option was introduced in 1.019 version of ALSA. Here is the original topic that helped me out of this: [http://www.amilo-forum.com/topic,2266,-Amilo-3540-microphone-problem.html](http://www.amilo-forum.com/topic,2266,-Amilo-3540-microphone-problem.html)

---

### Post by Textureglitch on 2009-03-19
HP Pavilion tx1410us works with model=3stack-dig

---

### Post by apoblepein on 2009-04-20
Please, add to database:

[B]HP tx2510us

options snd-hda-intel model=zepto position_fix=1[/B]

~$ uname -a
Linux NewYork 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

~$ lspci
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30f1
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16

~$ cat /proc/asound/modules
 0 snd_hda_intel

~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC268 Digital [ALC268 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

~$ arecord -l
**** Lista de CAPTURE Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 2: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---

### Post by markbuntu on 2009-04-20
Thank you. 
Can you confirm that everything works, especially mic and headphone speaker switching?

---

### Post by apoblepein on 2009-04-20
Sound works fine, also headphones switching.

I was so happy to hear my computer ... I've lost to check sound recording. It isn't working, records are just noise.
I'll post if I found the way

Regards!

---

### Post by apoblepein on 2009-04-22
Hi Markbuntu,

Confirmed!
Sound recording also works on **hptx2510us** using 
options **snd-hda-intel model=zepto position_fix=1**

(I just found the right levels on alsamixer)

Regards,
ra


ra@Madrid:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC268
  Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC268 Digital [ALC268 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
ra@Madrid:~$ arecord -l
**** Lista de CAPTURE Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
ra@Madrid:~$ uname -a
Linux Madrid 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by markbuntu on 2009-04-22
Excellent!

and thank you for your persistence in making sure the mic works.

best regards,
mark

---

### Post by apoblepein on 2009-04-22
You´re welcome,

Just one more think, I've checked that 
**model=toshiba position_fix=1** also works fine.

Regards,
Ra.

---

### Post by benorner on 2009-04-28
Fixed sound on my Asus F6A-2 with:

options snd-hda-intel model=6stack
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1 

Thanks for your work.

---

### Post by illogical_slacker609 on 2009-04-29
when i open the gedit alsa-base file, it's empty. i've seen some ppl say that the text is just hidden, but how do i make it show?

---

### Post by markbuntu on 2009-04-30
In jaunty the file name has been changed to alsa-base.conf to conform with new naming conventions for config files. I should update the OP for that.....

---

### Post by Test_ on 2009-05-04
Hi,
Does anyone has working sound on Acer Aspire 8930? I mean working like:

*surround 5.1
*full volume
*working build in mic

I've tried EVERYTHING to make my laptop's sound working but - so far - I've got one (maybe two - hard to say) working speaker, and not working mic.
Anyone?

---

### Post by guby_84 on 2009-05-04
Please mark help me in my Pc, do not exist sound is a HP DV6-1030us, whith ubuntu 9.04, in ubuntu 8.10 all ok. I don't understand please.

my chip is HDA Intel                                                              &#9474;
IDT 92HD75B3X5

---

### Post by wimpelmeesje on 2009-05-08
It fixed my audio, thanks! :)

My problem was a popping/cracking sound when trying to play audio. I could still hear the audio but it was accompanied by loud, irritating clicks.

I have a Dell Vostro 1510 and adding *options snd-hda-intel model=dell* to the config file and restarting alsa worked like a charm!

Thanks again!

Edit: seems like I have no sound at all on YouTube video's :(. Music and Video on Totem work though.

---

### Post by zachar9 on 2009-05-10
I have an Acer Aspire 6935G and sounds works:P well, but no headphones:confused:


alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
options snd-hda-intel model=auto
options snd-hda-intel single_cmd=1

---

### Post by Balogh on 2009-05-13
HP Pavilion dv4-1210ef

The following settings at the end of /etc/modprobe.d/alsa-base.conf enable correct sound through laptop speakers. The sound works after suspend and hibernate too:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Thanks to all of you whose contribution helped me find a solution for my laptop!

---

### Post by gnulab on 2009-05-21
Hi Mark,

I think this might be off topic a bit, but it has to do with trying out the options.

I'm executing the commands you showed us

sudo alsa force-reload
```

the output is this:
henry@henry-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/henry/.gvfs
      Output information may be incomplete.
Terminating processes: 3512lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/henry/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/henry/.gvfs
      Output information may be incomplete.

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/henry/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```Does that mean the alsa is successfully reloaded?

Then the command

pulseaudio -D
```

gives this output
henry@henry-laptop:~$ pulseaudio -D
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.

```I'm running laptop Compaq CQ40, and I'm curious if all the options mentioned are really necessary, thus trying them out one by one (total combination 120), but having to restart after combination is really too time consuming.

Please advise.
Henry

---

### Post by gnulab on 2009-05-21
Hi Mark,

My laptop is Compaq Presario CQ40-324TU

While waiting for your reply, I played around with various combinations.
At first the one you mentioned works, ie

```
Compaq
Compaq CQ40 
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

then I fiddled around, and for my case, this combo works as well, even the mic works, headphone works (speaker mutes automatically when headphone is plugged in)

```
Compaq
 Compaq CQ40 
 options snd-pcsp index=-2
 options snd slots=snd-hda-intel
 options snd-hda-intel model=hp-m4
#alias snd-card-0 snd-hda-intel
#options snd-hda-intel enable_msi=1
```

Hope this help for people in simiar situation.

Henry

---

### Post by banduan on 2009-05-22
unfortunately, CQ-40 settings didn't work for me
had the same set of error messages as gnulab

---

### Post by theromanone on 2009-05-27
> **dozepih said:**
> Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

from [HTML]http://ubuntuforums.org/newreply.php?do=newreply&p=7141145[/HTML]

worked perfect for my dv5, as the "options snd-hda-intel model=dv5" did nothing whatsoever in my case.

i then followed with the 
killall pulseaudio

sudo alsa force-reload

pulseaudio -D

log out, log in, and voila! thanks!!

---

### Post by markbuntu on 2009-05-27
> **banduan said:**
> unfortunately, CQ-40 settings didn't work for me
had the same set of error messages as gnulab

Well, I depend on people to report these things to me since I cannot afford to go out and buy every laptop there is. But someone said it worked with their CQ-40 so I have to take that on faith. Also, machine manufacturers often change the chips they use in the middle of a production run so there are many machines out their with the same label but different hardware. You probably hae  CQ-40 ver.xxxxx rev.yyyyy that is different from the one reported.

All I can say, is try some of the options for similar machines or try upgrading ALSA. There are fixes coming all the time for specific hardware but not all of them can be backported to older alsa versions. Jnauty cam out with ALSA 1.0.18 and now 1.0.20 is out. If you do figure it out, please let me know.

---

### Post by gnulab on 2009-05-27
> **guby_84 said:**
> Please mark help me in my Pc, do not exist sound is a HP DV6-1030us, whith ubuntu 9.04, in ubuntu 8.10 all ok. I don't understand please.

my chip is HDA Intel                                                              &#9474;
IDT 92HD75B3X5

Hi Guby,

You could try my settings, since my Compaq Presario CQ40 also reported it's using chipset IDT 92HD75B3X5

---

### Post by arazvan on 2009-05-31
TOSHIBA A200 works with lenovo option. Totally lucky try.
So anyone with ALC861-VD try this.
I had sound but the sound from the built-in speakers didn't mute when i plugged in headphones. Now it works.
Unbelievable, after months of trying I have almost given up.
That was the last thing keeping me away from using linux more.
I have it on my laptop but never used it much.

---

### Post by steffan72 on 2009-06-03
hey peeps
 
Just get me my new lappy yesterday and put jaunty on it.havin the sound issue
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

 
i added the following line to the /etc/modprove.d/alsa-base.conf
 
options snd-hda-intel model=hp-m4
 
and also tried it without the 'options'
 
but no luck and no change.
 
The model is a HP DV7-1211TX
 
any thoughts?

---

### Post by tim5901 on 2009-06-03
I have a eMachines T3604.  I have been running Ubuntu and at one time my sound was working.  But then I upgraded to 8.10 and it stopped.  I went through the forums followed a bunch of directions and never got it to work.  Finally I say 9.04 was coming out and I thought maybe that would fix it.  But it didn't.  I have been through the forums again and I still can't get it to work.

I think the problem is with the Alsa driver.  lspci sees the chipset but there are no sound cards in /proc/asound/cards.  Here are the outputs of the normal set of commands.

lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:01.0 Communication controller: Conexant Systems, Inc. Device 2f40
06:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)


lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards

--- no soundcards ---

cat /proc/asound/modules

(this returns nothing)

aplay -l

aplay: device_list:217: no soundcards found...

arecord

arecord: device_list:217: no soundcards found...

and just for good measure lsmod | grep snd

snd_hda_intel         435636  0
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_timer              29704  1 snd_pcm
snd                    62628  5 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm


can you provide some guidance?

---

### Post by PR_FM on 2009-06-05
hi.
i have hp pavilion dv4-1070 & don't have any sound , 
this is my sound card :
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevice : 0/1
Subdevice #0: subdevice #0
i'm not professional , please help me , 
where should i get my model to enter in alsa-base.conf !?

---

### Post by d4x2hhhy on 2009-06-05
Thanks guys, some progress here. Now I have one beep on start which is nice and some sound though very quiet.  I have a HP DV4 (1100 ea I think) Ive used the ALSA upgrade script, however in preferences sound only the Auto or OSS seems to work, so ive left it in auto.  Im not sure i have pulse installed anymore as when I killall pulseaudio it says pulse:nothing killed.

---

### Post by d4x2hhhy on 2009-06-05
changed my default sound card in preferences and ALSA seems to work at least with music!

---

### Post by kgpdeveloper on 2009-06-09
> **athaki said:**
> option ```
options snd-hda-intel model=gateway
``` 
works for my Gateway GT5405E with  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01).  It took the buzzing away that is used to have.  Thanks a million.


This used to work my ECS notebook as well. I was using Ubuntu 8.10 for over 7 months.
Now that I've installed Ubuntu 9.04, it doesn't work.
I wonder what has changed with Ubuntu that the old code didn't work.

---

### Post by markbuntu on 2009-06-09
The database is now updated with all reported fixes to here. So, if you are searching you do not need to look between here and the OP.

The database is getting a little messy so I should probably revamp it soon.

Thanks to everyone who contributed

best regards

mark

---

### Post by dakinibilyana on 2009-06-11
Hi All,

Anyone has any idea what would work with HP Compaq 6720s, i tried so many different options, still to no avail. 

Any help will be greatly appreciated. 
Thanks
Dakini

---

### Post by leemur on 2009-06-11
I have HP dv5 -1235dx laptop. I tried the following option and it worked.

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

---

### Post by modjoa on 2009-06-12
Hi Guys, I have a strange problem on my Desktop - Motherboard P5LD2 SE - the system is randomly rebooting, when I tried concurrently to use Skype(making a call) and playing music (for example from youtube). 

I have reinstall ALSA drivers, I tried all possible configurations(to use OSS, ALSA and PulseAudio Drivers), but unfortunately nothing seems to work for me....

Any idea how to solve the problem!??!

*If this post is not suitable for this thread, please let me know.*


Here is the info of my Audio Card:

 aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---------------------------------------------------------------------------------------------------
lspci -v


00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 817f
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at dddf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
---------------------------------------------------------------------------------------------------

In syslog, I get a lot of such messages, I don't know whether they are relevant to my case:

Jun 12 11:30:01 desktop /USR/SBIN/CRON[3896]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 12 11:40:01 desktop /USR/SBIN/CRON[4285]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

### Post by Tampler on 2009-06-14
> **dakinibilyana said:**
> Hi All,

Anyone has any idea what would work with HP Compaq 6720s, i tried so many different options, still to no avail. 

Any help will be greatly appreciated. 
Thanks
Dakini

Hi I am with HP Compaq 6735s. It's work for me with the following line:

options snd-hda-intel model=laptop

I have a sound with headsets and speakers as well. I don't have problem with the switching.

---

### Post by JSU on 2009-06-18
On my Dell M1330, model=dell worked. Thanks!

---

### Post by Hanisch on 2009-06-21
Notebook **MEDION MD 96380** works fine with *model=lenovo-nb0763 *

---

### Post by BMAN549 on 2009-06-21
> **leemur said:**
> I have HP dv5 -1235dx laptop. I tried the following option and it worked.

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

Thanks leemur!

I got my HP DV3510nr to work with these settings also!
I had to select "HDA Intel Stac92xx Analog (ALSA)" for all my outputs in the sound preferences.
I first enabled the "Play Sound effects when buttons are clicked" option in the sounds tab of the preferences. This gave me and idea that the new settings were working. From there i changed the output device and did a test until i hear sound from all of them.
The main part was added the lines above to the alsa-base.conf file

Hope this helps anyone else with a HP DV3510 laptop.

---

### Post by Pagnol on 2009-06-21
> **JSU said:**
> On my Dell M1330, model=dell worked. Thanks!

Works fine, but the fifth and sixth channels are not detected and therefore cannot be used. I prefer '3stack'.

---

### Post by Sxeptomaniac on 2009-06-22
I found that the given solution for the HP DV6 does not work for the DV6z version.  I have figured out a partial solution that gets the speakers working, though not the headphone jacks.

Configuration:
options snd-hda-intel model=dell-m4 enable_msi=1
I also had to upgrade ALSA to 1.0.20 (did not check 1.0.19, but it definitely does not work with 1.0.18.)

Edit:
I just checked on recording, and the microphone does not work, either.

---

### Post by raboofje on 2009-06-22
> **markbuntu said:**
> The database is now updated with all reported fixes to here. So, if you are searching you do not need to look between here and the OP.

The database is getting a little messy so I should probably revamp it soon.

Very useful list! Added a link to here from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) . Wouldn't it be convenient to maintain the whole list at the wiki instead of in OP's post? That'd allow anyone to improve on it.

---

### Post by markbuntu on 2009-06-23
You are welcome to drop this in a wiki if you want.Just post the link and I will add it in the OP next time I update it. Personally, I do not have the time or inclination to mess around in wikiworld.

---

### Post by mpie on 2009-06-29
dell vostro 1000 / inspirion 1501

use model=dell-m23

lspci -vv 

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Dell Device 022a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Omnutia on 2009-07-11
I'm having a [problem I've detailed in this thread]("http://ubuntuforums.org/showthread.php?t=1175564") where trying to open Pulse volume control brings my system almost to a halt.

My laptop is an HP nx6325 and I've been using the line:```
options snd-hda-intel model=toshiba
```This doesn't seem to have done anything, wondering if anyone here has ever seen something like this.

---

### Post by Dawei87 on 2009-07-11
ok, so i have a HP dv5, and followed some instructions here and everything works fine: mic, headphone jack etc. but the overall volume in jaunty is much lower than it was in intrepid. are there any options to raise the maximum volume? i have already maxed everything out in alsamixer and volume control, and other ideas?

---

### Post by raboofje on 2009-07-11
> **Dawei87 said:**
> ok, so i have a HP dv5, and followed some instructions here and everything works fine: mic, headphone jack etc. but the overall volume in jaunty is much lower than it was in intrepid. are there any options to raise the maximum volume? i have already maxed everything out in alsamixer and volume control, and other ideas?

Have you tried the advice at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ? Which codec are you using? Which model are you specifying?

---

### Post by Dawei87 on 2009-07-11
> **raboofje said:**
> Have you tried the advice at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ? Which codec are you using? Which model are you specifying?

thanks for the reply. i am using the IDT 92HD71B7X codec. and i am specifying the hp-dv5 module. i also built the new snapshot of alsa from source as it says on that page, and that gives me more range on the volume control, but the max volume stays the same, it sounds like people are whispering when i play audio. if you need any more info from me let me know.

---

### Post by Kilz on 2009-07-15
Acer Aspire 5536-5883

Jaunty 64bit (like I would install something other than 64bit? :) )

options snd-hda-intel model=auto

Everything works but the built in microphone. But the microphone port works now so I just pluged in cheap raido shack mic I had. None of the ports on the left side of the laptop worked even with auto untill I installed all the pulse packages listed on the main howto. The speakers even mute when you plug in headphones.

---

### Post by raboofje on 2009-07-16
> **Dawei87 said:**
> i am using the IDT 92HD71B7X codec. it sounds like people are whispering when i play audio.

[http://ubuntuforums.org/showthread.php?p=7625874#post7625874](http://ubuntuforums.org/showthread.php?p=7625874#post7625874) is about the same codec. This user reported that booting into vista solved the problem for him. 

This reminds me of a problem where the last volume in windows would determine the maximum volume in ubuntu. If you dual-boot, you might want to try that.

---

### Post by lordsidius on 2009-07-23
> **markbuntu said:**
> 

ACER , options snd-hda-intel model=acer
Aspire 4710, Aspire 5600,Travelmate         options snd-hda-intel model=acer
Aspire 9810                                   model=acer-aspire
5920g,Aspire 8930                                          model=auto
M50sa-x1                                      model=haier-w66
Acer Aspire 9815WKMi   options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
                       options snd-hda-intel model=acer-aspire position_fix=1 enable=yes  
 
mark

You can add the line for Aspire 6920G (codec ALC889):
options snd-hda-intel model=auto

MIC/Speakers/Head working perfectly after installing alsa drivers version 1.0.20

OS: Kubuntu 9.04

---

### Post by HarshReality on 2009-07-25
ALSA using 262 codec on VAIO VGN-NS325J/L and cant get the internal mic to work for anything :(

PM suggestions are more than welcome.. I use Skype in windows for calls and the like but this is all that is holding me from a constant lin run...

---

### Post by magostinelli on 2009-07-27
I have a Hp Pavilion Dv6-1108sl.

I have upgraded to alsa 1.0.20, i have found this configuration:
snd-hda-intel model=dell-m4-3 enable_msi=1

Audio ìs working, internal microphone too, but headphone and external microphone not working.

```
cat /proc/asound/card0/codec*|grep Codec
Codec: IDT 92HD75B3X5
```

Anyone can help me to work the headphone?'
How can i submit my hardware details to alsa team?

Regards.

---

### Post by the_guv on 2009-07-27
New entry for you:-

HP Pavilion DV 3500 or DV 3000 on Jaunty 9.04, using IDT 92HD71B7X codec

..

surprisingly, pretend you have a Dell and use this ..

options snd-hda-intel model=dell-m4-1

.. working that out took far toooooooooo long.  thank you, Ubuntans, for the guidance.  (and sod off HP, whose Linux support is pathetic.)

:popcorn:

---

### Post by Sxeptomaniac on 2009-07-28
> **magostinelli said:**
> I have a Hp Pavilion Dv6-1108sl.

I have upgraded to alsa 1.0.20, i have found this configuration:
snd-hda-intel model=dell-m4-3 enable_msi=1

Audio ìs working, internal microphone too, but headphone and external microphone not working.

```
cat /proc/asound/card0/codec*|grep Codec
Codec: IDT 92HD75B3X5
```

Anyone can help me to work the headphone?'
How can i submit my hardware details to alsa team?

Regards.
Same thing with my DV6z.  It's nice to have a working microphone, but I'd really like the line in and the headphone jacks to work at some point.

---

### Post by Javier Tapia on 2009-08-01
Hello, I have:

HP TouchSmartPC tx2 - 1025dx
HDA ATI DB Realtek ALC268
Ubuntu 9.04

and works fine with:

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1



Thanks

---

### Post by Krews on 2009-08-14
Hi , i own a hp dv2-1110eo and i was wondering if i this applies to my model as well ?.

---

### Post by Turk4n on 2009-08-15
Add this to the database !

dv6 1100.EO

Those with this card
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Should do this.
First, follow this and follow it carefully.
[http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)
Secondly do this.
```
In System/Administration/Users and Groups , make sure that your user and the root user are members of the following groups:

 pulse
 pulse-access
 pulse-rt
 audio
 video
```
Thirdly do this inside terminal**gksudo gedit /etc/modprobe.d/alsa-base.conf**
Then add these lines.
```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```
REBOOT.
Fifthly do this. Get gnome-alsamixer or just use alsamixer.
If you would like to use speaks. Just lift up the PCM and Speaker volume blocks.
If you would like to use headphones then lower Speakers and raise PCM.
*Why you should do this?* Because otherwise you will hear sound both from your speakers and headphones !

---

### Post by Tareg on 2009-08-21
Thank you very much for the information. This posting was the ultimate savior after months of struggling with Ubuntu 9.04 mic on Toshiba Satellite A100-192. The options I used are:

options snd-hda-intel model=3stack

They worked perfectly.

Cheers,

Tareg

---

### Post by dizee on 2009-08-21
> **Sxeptomaniac said:**
> Same thing with my DV6z.  It's nice to have a working microphone, but I'd really like the line in and the headphone jacks to work at some point.
I had the same problem with my dv6, adding 
```

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 enable_msi=1
```
fixed the no headphone issue. (The chipset is Intel 82801I (ICH9 family).)

There is a list of models to try for the options line:```

hp-m4
hp-dv5
ref
dell-m4-1
dell-m4-2
dell-m4-3
```
Hopefully one of them will work.

---

### Post by magostinelli on 2009-08-22
Dizee i have done your suggestions (on my dv6), but headphone not working for me!
Can you help me?

```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 enable_msi=1
```

---

### Post by starchini_ on 2009-08-24
HPDV7-1125ea

Updating the conf file with *options snd-hda-intel enable_msi=1* worked fine.. Don't think the subwoofer is working but i connect to external speakers so it's all good. 

I updated the conf file directly after a fresh install of ubuntu 9

---

### Post by psynapse on 2009-08-30
I've had many problems getting my new compaq cq61 to produce sound from its speakers (though headphones worked fine). I'm running 9.04 (kernel 2.6.28.15) with updated ALSA.  

Editing the file /etc/modprobe.d/alsa-base.conf, I tried all possible models in the line 

options snd-hda-intel model= xxx 

with no luck.

Most advice focuses on editing the /etc/modprobe.d/alsa-base.conf file, but one post suggested the file should be /etc/modprobe.d/sound    .  So I simply copied the existing alsa-base.conf to sound .... Worked first time ! (with model=hp-m4)   

I've no idea why! But if it helps anybody .....

---

### Post by dizee on 2009-09-02
> **magostinelli said:**
> Dizee i have done your suggestions (on my dv6), but headphone not working for me!
Can you help me?

```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 enable_msi=1
```

Just to add to that, having had to do this again recently I forgot to mention that you need to upgrade to the new alsa drivers first. Instructions here:
[http://ubuntuforums.org/showpost.php?p=7299632&postcount=60](http://ubuntuforums.org/showpost.php?p=7299632&postcount=60)

Hopefully it will work for you.

Also if you get a sound at the login screen but none after you log in, check if the "Front" volume is too low (needed to be 90 for me to get any sound).

---

### Post by AzT3K on 2009-09-03
I have a HP Pavilion DV7-1002tx running Ubuntu Jaunty. 

Codec: IDT 92HD71B7X
Codec: LSI ID 1040
Codec: Nvidia MCP78 HDMI

I can confirm that this fixes my sounds issues.

```

options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1

```

This also works:

```

options snd-hda-intel model=hp
options snd-hda-intel enable_msi=1

```

and so does this:

```

options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

```

There is some volume variation between the different models with options snd-hda-intel model=dell-m4-1 being by far the loudest.  This also one of the recommended codecs in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz for 92HD71B*

Im using alsa 1.0.21

Previously I was using options snd-hda-intel model=3stack-dig but this died when I upgraded KDE to 4.3 -> updating alsa to 1.0.21 and changing the snd-hda-intel options to the ones above resolved the issue.

---

### Post by magostinelli on 2009-09-04
> **dizee said:**
> Just to add to that, having had to do this again recently I forgot to mention that you need to upgrade to the new alsa drivers first. Instructions here:
[http://ubuntuforums.org/showpost.php?p=7299632&postcount=60](http://ubuntuforums.org/showpost.php?p=7299632&postcount=60)

Hopefully it will work for you.

Also if you get a sound at the login screen but none after you log in, check if the "Front" volume is too low (needed to be 90 for me to get any sound).


I had alsa 1.20, sound working but not headphone.
I installed alsa-driver snapshot, and now it works fine!!!!! Very good!!!

Thank you very much!

---

### Post by richwillal on 2009-09-06
I just upgraded to 9.04 and got no sound.  I found the following article:
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

That article helped greatly.  The following settings appear to work:

Laptop: HP HDX9300
Codec:  STAC9271D
Module: snd-hda-intel
Jacks:
    Rear: Front, Center/Sub, Side, Rear
    Front: Mic, Headphone 1, Headphone 2

Working options in /etc/modprobe.d/alsa-base.conf:

    options snd-hda-intel model=5stack position_fix=0 probe_mask=-1 bdl_pos_adj=-1 enable=yes

Results:
----------------------
Currently, I have 5.1 speakers attached to the Front, Center/Sub and Rear connectors.  All work correctly.

=> Laptop speakers work when the checkbox "Line in as Output" is checked.

Unchecking that checkbox leaves me with external speakers which works great when docked.

Headphone jack 1 does not work, but plugging headphones into headphone jack 2 works and mutes other outputs correctly.

HTH: I've found very few references for this laptop configuration running Linux.

Rich

---

### Post by vitoreiji on 2009-09-13
One more for the database. We should have a wiki page for this. Or there is one that I'm missing?
Sony Vaio VGN-CS360A, Realtek ALC262, running Jaunty
options snd-hda-intel model=toshiba-s06

$> lspci -vv
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 903f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d6800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by Iwavns on 2009-09-15
...In case there were people who were as stupid as me :) when reloading ALSA,
after 

killall pulseaudio

sudo alsa force-reload

there will be a message box asking you whether to reload or not (in Ubuntu 9.04)..press Reload..before you type 

pulseaudio -D

I am using Compaq CQ40, the configurations worked just fine for me..thanks!

---

### Post by karlakoala on 2009-09-16
Please help, I just can't get any sound at all from my hp dv6-1007tx
I have tried several of the above alsabase mods to no avail, all my info on set up & hardware is [here]("http://www.alsa-project.org/db/?f=1c27a007fd487a0e6d4d2190d8521114ea5020b9") 
Also after adding to the alsabase.conf file when I run the command killall pulseaudio nothing happens 
The command sudo alsa force-reload gives me
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
Terminating processes: 7993 8000lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

And the command pulseaudio -D gives me
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.

Then when I reboot the machine and run the command sudo gedit /etc/modprobe.d/alsa-base.conf again the file no longer shows my edit - even though I have definitely saved it - and I still get no sound at all, from speakers or headphones. :confused:

I have also tried to update the alsa with no luck - followed instructions [here]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") & [here ]("http://ubuntuforums.org/showthread.php?t=1046137")
still my alsa shows as 
Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18

---

### Post by karlakoala on 2009-09-16
> **karlakoala said:**
> Please help, I just can't get any sound at all from my hp dv6-1007tx
I have tried several of the above alsabase mods to no avail, all my info on set up & hardware is [here]("http://www.alsa-project.org/db/?f=1c27a007fd487a0e6d4d2190d8521114ea5020b9") 
Also after adding to the alsabase.conf file when I run the command killall pulseaudio nothing happens 
The command sudo alsa force-reload gives me
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
Terminating processes: 7993 8000lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mercedes/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

And the command pulseaudio -D gives me
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.

Then when I reboot the machine and run the command sudo gedit /etc/modprobe.d/alsa-base.conf again the file no longer shows my edit - even though I have definitely saved it - and I still get no sound at all, from speakers or headphones. :confused:

I have also tried to update the alsa with no luck - followed instructions [here]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") & [here ]("http://ubuntuforums.org/showthread.php?t=1046137")
still my alsa shows as 
Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18




I now have sound thanks to this post 

 					"Originally Posted by **shinjimx** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7676817#post7676817") 				
 				[I]I've just did this on my dv2-1020la (Latinamerican version), worked like a charm.

What you have to do in simple steps:

go to this website:

[http://ftp.kernel.org/pub/linux/kern...a/alsa-driver/]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/")

Download the file alsa-driver-snapshot.tar.bz2

Go to your download location, extract it (I did it via the file manager, double click the file and drag 'n drop the folder to where you want, say, Desktop)

Open a terminal (command line)

Go to the location you extracted the alsa-driver folder (if you did it on Desktop, type cd /home/xxx/Desktop/alsa-driver/ where xxx is your user)

Type the commands one after the other ends:
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)

copy and paste this:
options snd_hda_intel model=hp-dv5

save the file and restart your laptop

As I said, just did it (took me about 10-15 min.) and now Metallica is rocking on my system.

Good luck.
Greetings from Mexico City"

in[ this thread]("http://ubuntuforums.org/showthread.php?p=7958158#post7958158")

Updated alsa successfully & instead of dv5 added dv6
[/I]

It's quiet, but I have sound :guitar:   so it's a start! :P

Any ideas how to make it louder? :confused:

---

### Post by the_guv on 2009-10-07
> **karlakoala said:**
> I now have sound thanks to this post 

                     "Originally Posted by **shinjimx**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7676817#post7676817")                 
                 [I]I've just did this on my dv2-1020la (Latinamerican version), worked like a charm.

What you have to do in simple steps:

go to this website:

[http://ftp.kernel.org/pub/linux/kern...a/alsa-driver/]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/")

Download the file alsa-driver-snapshot.tar.bz2

Go to your download location, extract it (I did it via the file manager, double click the file and drag 'n drop the folder to where you want, say, Desktop)

Open a terminal (command line)

Go to the location you extracted the alsa-driver folder (if you did it on Desktop, type cd /home/xxx/Desktop/alsa-driver/ where xxx is your user)

Type the commands one after the other ends:
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)

copy and paste this:
options snd_hda_intel model=hp-dv5

save the file and restart your laptop

As I said, just did it (took me about 10-15 min.) and now Metallica is rocking on my system.

Good luck.
Greetings from Mexico City"

in[ this thread]("http://ubuntuforums.org/showthread.php?p=7958158#post7958158")

Updated alsa successfully & instead of dv5 added dv6
[/I]

It's quiet, but I have sound :guitar:   so it's a start! :P

Any ideas how to make it louder? :confused:


hey *shinjimx .. *tx to you, i now have ACDC rocking my sys!

:guitar::guitar::guitar:

couple things tho .. for some folks, i think jaunty up

> sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)you may need to use "alsa-base.conf", rather than "alsa-base"

> copy and paste this:
 options snd_hda_intel model=hp-dv5dunno if it's me or my setup, somehow, but for me it worked with hyphens rather than underscores, so i made that ..

 options snd-hda-intel-model=hp-dv5

er, dunno about Metallica, mind ;)  call me old-fashioned.

---

### Post by the_guv on 2009-10-08
> **karlakoala said:**
> 

It's quiet, but I have sound :guitar:   so it's a start! :P

Any ideas how to make it louder? :confused:

hey [karlakoala]("http://ubuntuforums.org/member.php?u=913295") .. I thought this was overridden by master volume in top panel but just tried and it's not, so try this ..

at terminal type:-

[B]alsamixer

[/B]er, guess what, that brings up the mixer!

have a play .. mine's too darn loud now.  that's what the missus said anyhow.

---

### Post by usagi629 on 2009-10-14
Thanks so much for this post!!!

I got sound working on my HP after finding this!

Model: dv6t-1200

On a clean install of Ubuntu 9.04 Jaunty - no sound through speakers or headphone jacks

After upgrading Alsa (compiling driver(s) from source), and adding this line: option snd-hda-intel model=dell-m4-1 to the Alsa config, I have sound now through speakers and headphones! Mic works too, but I never test that until after the fix. 

Thanks again!! :)

---

### Post by Aaardwark on 2009-10-15
Thanks for a great post!

The lines for Compaq CQ40 also works for Compaq CQ71.

---

### Post by markbuntu on 2009-10-15
I have updated the OP/database to include all machine information in all the posts up to here so no need to look.
We can always add more so please post if you can help.

Kudos to all who contributed. 
You are the people that make linx and ubuntu so great!!

Best regards and again, thank you,
mark

---

### Post by saias on 2009-10-17
Thanks for tha data base. I have been searching for a solution for more than 2 weeks and couldnt find the right post or get the correct answer. 

My model is HP pavillion dv3650

soundcard model:

inten HDA
IDT 92HD71BFX

Worked for HP model=hp like the dv3510nr and probably will be working for the whole dv3000 series.

---

### Post by sashhoney on 2009-10-23
i have recently bought  Dell Studio 1450 with following config

!!ALSA Version
!!------------

Driver version:     1.0.18a
Library version:    1.0.20
Utilities version:  1.0.20

!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfc010000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

i am unable to get my soundcard working
please suggest me proper options

---

### Post by abhiroopb on 2009-10-25
I made a mess of things. Basically, I added some repo's that totally destroyed my dependencies and I had to re-install a lot of packages (including alsa and pulse). I also had to re-install my kernel and numerous other things.

In between doing all this my configuration got messed up. Before adding the repo everything was fine. So, I assume if I were to re-install jaunty at this point everything would work fine. But, of course I'd rather not re-install everything.

What the basic commands show me:

```

$ aplay -l
aplay: device_list:217: no soundcards found...

```

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

```

lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I've done everything in these guides: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Nothing has worked for me. In fact I've done everything twice I think!

Please help!!

---

### Post by markbuntu on 2009-10-25
Please do not spew identical posts all over the forums. If people can help you they will when they can.

---

### Post by abhiroopb on 2009-10-25
I'm really sorry about that. I assumed that since these were the posts where people knowledgeable about sound issues congregated it would be a good idea to post here. After I posted I realised there were quite a few of them. So, I also started a new thread. Please have a look and ignore the one here. Thanks!

[http://ubuntuforums.org/showthread.php?t=1300743](http://ubuntuforums.org/showthread.php?t=1300743)

---

### Post by xdevnull on 2009-10-28
Anyone have an idea for an option for the acer aspire 1410 (1810T in europe).  I've tried =acer without much success.

Everything works fine except for the internal mic (it's near the webcam).  
lspci = 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I'm using Karmic rtm

Thanks...

---

### Post by netaldod on 2009-10-29
For a Dell Latitude E4300 sound was not working** (KDE4 Phonon and PulseAudio)**, so here is the way to fix it (everything works, loudspeakers, mic, headphones). In short you need :

options snd-hda-intel model=dell-m81

In practice I had to clean up a bit the original configuration file /etc/modprobe.d/alsa-base.conf as it contained all sort of unnecessary stuff. I will list it in the following. Here is my configuration

~$ uname -a
Linux ly 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6adc000 irq 21

~$ cat /proc/asound/modules
 0 snd_hda_intel

~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 3 : INTEL HDMI [INTEL HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

~$ arecord -l
**** Liste des CAPTURE périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 2/2
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1

and finally this is my configuration file /etc/modprobe.d/alsa-base.conf (this works using Pulseaudio with the Xine engine, which you can set in System Settings under Multimedia, other configurations may work but I did not try them)

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7
# My sound devices
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-hda-intel ; /sbin/modprobe --quiet --use-blacklist snd-pcm ; /sbin/modprobe --quiet --use-blacklist snd-seq ; /sbin/modprobe --quiet --use-blacklist snd-timer ; /sbin/modprobe --quiet --use-blacklist snd-seq-device ; /sbin/modprobe --quiet --use-blacklist snd-page-alloc ; }
# Dell specific option
options snd-hda-intel model=dell-m81

---

### Post by H4F on 2009-10-30
I have acer aspire 5720. Its not related to the aspire one taught my microphone worked when
options snd-hda-intel model=acer-aspire-one
I have
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by rafadev on 2009-10-31
EVERYTHING WORKING YEYYYYYYYY!!!

I have an ACER 5236-5322 running ubuntu 9.10 Karmic. At first audio came out both through the notebook's speakers and the headphones. I edited /etc/modprobe.d/alsa-base.conf.

The last line was:

options snd-hda-intel power_save=10 power_save_controller=N

I added model=auto and forced alsa reload and it was working perfectly!! Also, the camera works incredibly well. The microphone wasn't working, I went to sound options, selected the only device listed and the "microphone 2" input source.

---

### Post by dizee on 2009-11-01
In Karmic I have had to install the "linux-backports-modules-alsa-karmic" package as well as editing the configuration file. After that the headphones work as expected, yet to test the internal mic.

---

### Post by Fast_Wyvern on 2009-11-07
Thanks very much for the database

Alienware m5500i-R3 with Ubuntu 9.10 Desktop Karmic Koala

Sound and Mic works with

options snd-hda-intel model=F1734 position_fix=2
options snd-hda-intel enable_msi=1


Built in Mic is low or distorted if using boost with poor output to built in speakers when recording. Headphone and Ext Mic is fine for skype, Movies etc on Built in speakers fine

---

### Post by uterrorista on 2009-11-08
I have an LG P1. I updated today to 9.10.
No headphones neither speakers.

Solution:
```
sudo gedit /etc/modprobe.d/alsa-base
```
and add:
```
options snd-hda-intel model=lg
```

---

### Post by emilije on 2009-11-09
Hi guys,

What about non-hda cards? For example adi ac 97?
On my nx8220 i have a switching problem. On alsamixer for headphone is saying "jack sense off"
any ideas?

EDIT: well, this is embarrassing for me :) 
1. Go to terminal
2. type alsamixer
3. select headphone
4. press dot (".") on keyboard
5. voila, jack sense is ON, switching problem OFF
\\:D/

---

### Post by kongstad on 2009-11-10
I got my zepto 6625WD working by commenting out
#options snd-hda-intel power_save=10 power_save_controller=N

and adding

options snd-hda-intel probe_mask=1 model=auto

Model=zepto left the headphone out not working, but with auto everything is A-ok.

---

### Post by dumb on 2009-11-15
LG T1 Express

Add/change the following to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=lg
options snd-hda-intel power_save=0 power_save_controller=N

And sound works

---

### Post by stiperstones on 2009-11-17
model hp pavilion entertainment dv6-2010sa

added to alsa-base.conf

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=dell-m4-3 enable_msi=1
```

Works here thank you

---

### Post by Ghinn on 2009-12-03
I've spent the last two days fiddling with this, and reading the ALSA-configuration.txt file, and I finally got it to work.

Model: Toshiba Qosmio G35-AV660

Result of cat /proc/asound/card0/codec#* | grep Codec:
Codec: SigmaTel ID 7691
Codec: LSI Si3054

Wound up figuring out that I had an Intel 82801G (ICH7) chip. Tried snd-hda-intel, didn't work. snd-intel8x0 worked perfectly. It appears to be working just fine now.

---

### Post by kobayashison on 2009-12-06
**Notebook Model**: HP DV2555ea
**Ubuntu version**: Karmic Koala 9.10
**Alsa Codec**: Conexant CX20549 (Venice)
**Problem**: noisy pop sounds on audio card awakening from power save mode every few seconds.
**Solution**: in /etc/modprobe.d/alsa-base.conf modified line "options snd-hda-intel power_save=10 power_save_controller=N" in "options snd-hda-intel enable_msi=1"
**Bug page**: [https://bugs.launchpad.net/fedora/+source/linux/+bug/382140](https://bugs.launchpad.net/fedora/+source/linux/+bug/382140)

---

### Post by damnsavage on 2009-12-10
I have an SL Technology NetBook100 and the following line added to alsa-base.conf
   options snd-hda-intel model=eeepc-p701
This fixed an issue with the speakers not being muted when the headphones were plugged in.

The microphone works for skype/ekiga, although it does not work for the 
"sound recorder" application. I can get sound recorder working if I configure
the "sound capture" setting to "pulseaudio server" in system > preferences > sound
but this will break the mic for skype/ekiga calls.

Machine Specs.
  ubuntu 9.0.4 jaunty jackolope
  Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
  Codec: Realtek ALC662 rev1
  ALSA version 1.0.18

---

### Post by daelus0 on 2009-12-14
```
#Gateway m-6850fx
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel enable_msi=0 model=eapd
```

Thanks to[ http://ubuntuforums.org/showthread.php?t=1170581]("http://ubuntuforums.org/showthread.php?t=1170581")

this works in karmic you may need to use the [Alsa update script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") to make sure you have the latest alsa version. I tried that first so I'm not entirely sure.

---

### Post by DShad on 2009-12-22
Any idea for my Sony Vaio VGN-P530?

The only thing not working is my internal MIC.

Many thanks!

---

### Post by threetwoone on 2009-12-25
On Ubuntu 9.10 for the **asus g1sn** you need to add:
options snd-hda-intel model=3stack-dig
(works out of the box in 9.04)
I should have mentioned that this model uses the alc1200, sorry.
Also, it seems that the alc1200 is similar to the alc888, this may help others with troubleshooting.

---

### Post by eeeandrew on 2009-12-30
Hi, Do you think it would be possible to generate a text file from this database which a small program could then search through, compare with the users computer stats and make the correct change? Sounds like a useful wee project for a good programmer, unfortunately not something I think I could handle.

Any thoughts?

---

### Post by travisxcore on 2010-01-05
I have a Dv6105 and my computer speakers pop (on the laptop) when I hook up headphones/to my tv and over time it grows in loudness and pitch.  I've tried all of the hp fixes but non of them seem to work. 

Heres the specs:

> Codec: Conexant CX20549 (Venice)
> aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by ubusheep on 2010-01-16
.. And for Packard Bell Easy note MZ35 add the following:
options snd-hda-intel model=dallas

found this on a spanish forum.. thank god we have google translate!

[http://translate.google.be/translate?hl=nl&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F89285](http://translate.google.be/translate?hl=nl&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F89285)

---

### Post by MarkBrown667 on 2010-01-21
Update:  ubuntu version: 9.10 Model: Sony Vaio VGN-CS60B  model=toshiba-s06  works. Also, you need to use alsamixer to set the source to Int-DMic to use the internal microphone.  Don't know how to find out the alsa version requested in the top post. If you want people to report information, please tell them how to get it ;-)

---

### Post by nerozumim on 2010-02-01
Hi all,

I'm on an Asus K52F, Ubuntu 9.10 x64

Alsa: 1.0.22.1
Kernel: 2.6.32-02063206-generic

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX

Problem:  when I plug in my headphones, I still hear sound through my laptop speakers. No section (Conexant 5069) found in HD-Audio-models.txt.gz

This options fail:

options snd-hda-intel model=asus-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel model=laptop
options snd-hda-intel disable_msi=1
options snd-hda-intel model=generic
options snd-hda-intel model=5stack
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=3stack
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=laptop-asus
options snd-hda-intel model=k52f position_fix=1
options snd-hda-intel model=laptop
options snd-hda-intel model=haier-w66
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
options snd-hda-intel enable=1 index=0 model=lenovo
options snd-hda-intel model=lenovo

Any ideas?

---

### Post by eminembdg on 2010-02-21
ok, I have the oddest problem...

I can even use sudo gedit /etc/modprobe.d/alsa-base to edit the alsa-base file because when it opens its totally blank!

There are now words or nothing in the file at all. If I open alsa-base in READ ONLY view i can see it, but in sudo it&#347; blank.

Can anyone help me please? Thanks in advance

---

### Post by jhuntington on 2010-02-21
the configuration file has been moved to /etc/modprobe.d/alsa-base.conf i had the same problem but theres configuration information in the .conf file.

did anyone ever find out how to get these drivers working?
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX
i still have issues with the mic input jack and the headphones not turning off the speakers

---

### Post by eminembdg on 2010-02-21
> **jhuntington said:**
> the configuration file has been moved to /etc/modprobe.d/alsa-base.conf i had the same problem but theres configuration information in the .conf file.

did anyone ever find out how to get these drivers working?
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX
i still have issues with the mic input jack and the headphones not turning off the speakers

Ive opened that; /etc/modprobe.d/alsa-base.conf , but its blank in edit mode and viewable in read only

---

### Post by eminembdg on 2010-02-21
someone answered my problem , using gksu nautilus , i am able to see the content of the file now. thanks anyways

---

### Post by troipoison on 2010-03-14
alsa 1.0.20
ALC880
LG S1 Pro Express Dual
Karmic i386 Desktop

options snd-hda-intel model=lg
placed in /etc/modprobe.d/alsa-base

when I typed,
pulseaudio -D
E: main.c: Daemon startup failed.

not sure what that was, but no matter, confirmed speakers working
thx :)
Hope that helped anyone with the LG S1

---

### Post by save2 on 2010-03-17
thanks ! finally also speaker works (not only the headphone jack)

sound card: HDA Intel STAC92...
Codec: IDT 92HD75B2X5

Compaq CQ61 (more preciesly CQ61-120EJ) on Ubuntu 9.10 only headphones jack sound worked out of the box.
added to also-base.conf end of file:
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

restarted pulseaudio service or simply restart machine.

---

### Post by sleepitoff on 2010-03-19
> **nerozumim said:**
> Hi all,

I'm on an Asus K52F, Ubuntu 9.10 x64

Alsa: 1.0.22.1
Kernel: 2.6.32-02063206-generic

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX

Problem:  when I plug in my headphones, I still hear sound through my laptop speakers. No section (Conexant 5069) found in HD-Audio-models.txt.gz

This options fail:

options snd-hda-intel model=asus-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel model=laptop
options snd-hda-intel disable_msi=1
options snd-hda-intel model=generic
options snd-hda-intel model=5stack
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=3stack
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=laptop-asus
options snd-hda-intel model=k52f position_fix=1
options snd-hda-intel model=laptop
options snd-hda-intel model=haier-w66
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
options snd-hda-intel enable=1 index=0 model=lenovo
options snd-hda-intel model=lenovo

Any ideas?

Have you found out the answer? I have the same issue.

---

### Post by drbcladd on 2010-03-21
Alienware m17x: 
HDA NVidia STAC92xx Analog/Digital
Codec: IDT 92HD73C1X5

options snd-hda-intel model=alienware power_save=0 power_save_controller=N

The big deal appears to be pulse audio:
[http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html](http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html)

I purged pulse audio, I loaded the alsa backport, the bloody thing booted with boot-up sound.

```
$ sudo apt-get remove --purge pulseaudio
$ sudo apt-get install linux-backports-modules-alsa-`uname -r`
```

---

### Post by wilsontp on 2010-03-28
HP Pavilion TX2525nr works with model=3stack-dig

---

### Post by wiebe de haas on 2010-03-31
GATEWAY laptop
Model: m6823

LinuxMint 8 Helena (Karmic)
ALSA 1.0.20
codec: SigmaTel STAC9205  

I HAD no audio from Headphone-out.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  Everything else worked correctly 
after initial installation. 

I dug through these forums.
(I am very impressed with the persistence
of many contributors to this forum.)

ADDED to: /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=eapd enable=1 index=0
options snd-hda-intel enable_msi=1

rebooted, WORKS!!    [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by dpronin on 2010-04-02
Guys pls do smth with that problem. Its realy annoying thing at work for example. :(
[INDENT]```
Quote:
Originally Posted by nerozumim  
Hi all,

I'm on an Asus K52F, Ubuntu 9.10 x64

Alsa: 1.0.22.1
Kernel: 2.6.32-02063206-generic

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX

Problem: when I plug in my headphones, I still hear sound through my laptop speakers. No section (Conexant 5069) found in HD-Audio-models.txt.gz

This options fail:

options snd-hda-intel model=asus-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel model=laptop
options snd-hda-intel disable_msi=1
options snd-hda-intel model=generic
options snd-hda-intel model=5stack
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=3stack
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=laptop-asus
options snd-hda-intel model=k52f position_fix=1
options snd-hda-intel model=laptop
options snd-hda-intel model=haier-w66
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
options snd-hda-intel enable=1 index=0 model=lenovo
options snd-hda-intel model=lenovo

Any ideas?
Have you found out the answer? I have the same issue.
```[/INDENT]

---

### Post by LinuxBob on 2010-04-06
I changed the alsa-base.conf to 3stack to use a USB speaker system (actually a Thompson/RCA lyra wireless transmitter), which worked fine.

Now I Moved the Lyra USB devise to an XP machine (long story, but to transmit audio and video of MLB TV to TVs around the house) and need to change back alsa-base.conf, I think, to get back to using the original, internal sound card.

@zareason:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I did not backup als-base.conf or comment out the original line which now reads:

options snd-hda-intel probe_mask=8 model=3stack


Anyone know what I should replace "3stack" with? I do not see my card in the database.  Also, what are the steps once you;ve successfully edited alsa-base.conf to get sound?

Alsamixer just shows the card info and IEC958, the screen is blank where one might expect to see volume bars.  More output from terminal:

lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
	Memory at fae80000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: PC Partner Limited Device 437b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Memory at fae7e400 (32-bit, non-prefetchable) [size=256]
	Memory at fae7e000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 29
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=16]
	Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: faf00000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f9ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a108
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

---

### Post by tpsvca on 2010-04-15
> **nerozumim said:**
> Hi all,

I'm on an Asus K52F, Ubuntu 9.10 x64

Alsa: 1.0.22.1
Kernel: 2.6.32-02063206-generic

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX

Problem:  when I plug in my headphones, I still hear sound through my laptop speakers. No section (Conexant 5069) found in HD-Audio-models.txt.gz

This options fail:

options snd-hda-intel model=asus-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel model=laptop
options snd-hda-intel disable_msi=1
options snd-hda-intel model=generic
options snd-hda-intel model=5stack
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=3stack
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=laptop-asus
options snd-hda-intel model=k52f position_fix=1
options snd-hda-intel model=laptop
options snd-hda-intel model=haier-w66
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
options snd-hda-intel enable=1 index=0 model=lenovo
options snd-hda-intel model=lenovo

Any ideas?

I have the same problem with the K52F, but i'm using Ubuntu 10.04
Help me!

---

### Post by Kocka on 2010-04-17
> **tpsvca said:**
> I have the same problem with the K52F, but i'm using Ubuntu 10.04
Help me!
So do I :S.

---

### Post by jsevi83 on 2010-04-17
I have the same issue with my Asus A52F (reported to be K52F). Sound coming out of the speakers when headphones are plugged. Please, if anybody finds the solution let us know.

By the way, is your webcam upside down?

---

### Post by igogo three-thousand on 2010-04-18
Same problem with Asus K52JR

---

### Post by lidex on 2010-04-21
Update alsa or install alsa-backports. Add option:
```
 options snd-hda-intel model=3stack-dig 
```

---

### Post by jsevi83 on 2010-04-21
I just tried this, in case it was for us (Asus A52 or K52)

options snd-hda-intel model=3stack-dig

It doesn't work (for muting the speakers while headphones are plugged), so I guess it was a reply for somebody else. I am using ALSA 1.0.23 from ricotz-unstable ppa.

---

### Post by jsevi83 on 2010-04-23
For those with an Asus K52 or Asus A52, please go here
[http://ubuntuforums.org/showthread.php?p=9162799](http://ubuntuforums.org/showthread.php?p=9162799)

---

### Post by lidex on 2010-04-25
Update alsa or install alsa-backports. Add option:
```
options snd-hda-intel model=asus-mode3
```

---

### Post by demetrius2009 on 2010-04-26
2 -> lidex

I've tried this your advice to install ALSA backports - no luck, still I head sound from my external speakers when plug in headphones :(

---

### Post by xtrman on 2010-04-26
For the Conexant 5069 card I have found a way to mute the internal speakers. 
Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz).
Then execute 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 1 
```to turn the internal speakers off and 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 0 
```to turn them on again.

I have also filed a bug report upstream on this.

Edit: I have now created a daemon to automattically mute and unmute the internal speakers when headphones are plugged in and removed.
Program:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```Compile with g++ main.cpp -o pinsensed
Run with sudo ./pinsensed

---

### Post by jsevi83 on 2010-04-27
Thank you very much, that worked! The only thing, I had to compile using g++ instead of gcc. But now I can finally use my headphones without having my speakers sounding at the same time.

Asus A52F

---

### Post by 542 on 2010-04-28
xtrman - you are a legend. Works for me on an Asus K52J.

I added the pinsensed command to /etc/rc.local as well so it auto-starts. I also needed to use g++ in place of gcc.

---

### Post by demetrius2009 on 2010-04-28
You are the greatest man!!!! 
This worked for me too on my Asus K52JR Ubuntu Lucid 32 bit:guitar::guitar::guitar:

---

### Post by desuid on 2010-05-02
Its work on Lenovo G560. Many thanks!

---

### Post by mak7imus on 2010-05-02
Thank for this thread)))
Laptop: Samsung R25plus (no built-in mic)
Problem: external mic not working :( (no sound)
OS: Ubuntu Lucid Lynx
Sound: ALC262

Solution:
sudo gedit /etc/modprobe.d/alsa-base.conf
at the end of the file add

**options snd-hda-intel model=hippo**

and reboot!!!
digitall inputs work fine (with jack detection) 

:guitar: :guitar: :guitar:

---

### Post by diaz8 on 2010-05-04
My Sony VGN-NS21S works fine with 
options snd-hda-intel model=toshiba-s06

Regards

---

### Post by Wandang on 2010-05-10
Ubuntu 10.04

MSI Ex623

```
wandang@wandang:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8ef8000 irq 30
wandang@wandang:~$ cat /proc/asound/modules
 0 snd_hda_intel
wandang@wandang:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```

only sound throu headset after installation.
fixed with:
```
options snd-hda-intel model=targa-2ch-dig
alternativ (both worked):
options snd-hda-intel model=targa-dig
```

---

### Post by lidex on 2010-05-13
Fix for no headphone. Thread: [http://ubuntuforums.org/showthread.php?p=9294918#post9294918]("http://ubuntuforums.org/showthread.php?p=9294918#post9294918")

Add alsa-base.conf option:
```
options snd-hda-intel model=dell-eq
```

---

### Post by dolphinsonar on 2010-05-16
```
options snd-hda-intel model=dell-bios power_save=10 power_save_controller=N

```This fixed the problem with my Dell Inspiron 1318 laptop.  The build in microphone (mic) was not working until I added this.  Now Skype test call returns my voice using the built-in mic.

\\:D/

---

### Post by danny2525 on 2010-05-17
Helpppppppppppp

I have a Hp dv6-2170us the issue is that on the headphones and speakers work at the same time.Please help me I will provide any info 


*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
danny@danny-laptop:~$

---

### Post by lidex on 2010-05-17
markbuntu specifically asked> **Please do not post problems or ask for help here**

In other words, please start a new thread, with a proper title and any pertinent info. If you'd like to PM me the link to your post, I will be glad to help.

---

### Post by chris1974 on 2010-05-19
HP Pavilion dv7 3065dx
Running Karmic, which has ALSA 1.0.20

Out of the box, sound did not work. Eventually got everything working including the mic by adding the following to alsa-base.conf
```

options snd-hda-intel model=hp-dv5 enable_msi=1
```

---

### Post by butoyzki on 2010-05-20
hi, i am using an acer aspire 4736Z laptop and i can't seem to make the mic work. apart from that, everything else is ok. do you know of any configuration which might be able to help me out?

here are some details i got from my laptop:

```

cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

``````

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```i did try to configure it using

```

sudo nano /etc/modprobe.d/alsa-base.conf

```and added
```

options snd-hda-intel model=acer
```but it didn't help me at all. please help!

---

### Post by promet on 2010-05-20
First of all, thanks xtrman. Really, it's just great of you to share this. I am now using, very successfully, your "hda-verb" speaker shutdown method.

I also tried compiling your daemon (also awesome), but I got an error, I can't seem to resolve the meaning of the error from the code, way beyond my pay grade, so I was wondering if it mike make any more sense to you. 

After trying:

```
gcc main.cpp -o pinsensed
```

and got the following error:

```
/tmp/ccUFwPiX.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

Also I might mention, this is a brand new 10.04 install, which is still under pretty heavy renovation, so I suppose I could be missing some code building components (I installed "build-essentials" which, in the past, has done the job for me).

Please let me know if you have any thoughts. regardless getting some control over this audio thing has been a great thing, thanks again!

promet

---

### Post by xtrman on 2010-06-13
Try compiling with g++ instead of gcc.

---

### Post by careertargetph on 2010-06-13
You can build a program using c++ which can solve your problem

---

### Post by saiganeshb on 2010-06-14
> **butoyzki said:**
> hi, i am using an acer aspire 4736Z laptop and i can't seem to make the mic work. apart from that, everything else is ok. do you know of any configuration which might be able to help me out?

here are some details i got from my laptop:

```

cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

``````

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```i did try to configure it using

```

sudo nano /etc/modprobe.d/alsa-base.conf

```and added
```

options snd-hda-intel model=acer
```but it didn't help me at all. please help!

I had the same problem for conexant chips so i googled 'conexant audio drivers for linux' ...I suggest you try 'realtek audio drivers for linux' :) 
[http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

---

### Post by tpsvca on 2010-06-16
> **xtrman said:**
> For the Conexant 5069 card I have found a way to mute the internal speakers. 
Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz).
Then execute 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 1 
```to turn the internal speakers off and 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 0 
```to turn them on again.

I have also filed a bug report upstream on this.

Edit: I have now created a daemon to automattically mute and unmute the internal speakers when headphones are plugged in and removed.
Program:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```Compile with g++ main.cpp -o pinsensed
Run with sudo ./pinsensed

Hello,

I'm new on ubuntu and using 10.04 on Asus K52F.
Somebody can give me a step by step instruction for this trick?

Thanks in advanced

---

### Post by rewritems on 2010-07-04
Oh my god, this worked sooo perfectly! Thank you so much. (I use pavilion dv7 HP)

---

### Post by Caldrac on 2010-07-06
**Asus eeePC 1201T**

model=eeepc-p901

No or all other models, I tried (which does not include: "basic", "quanta", "lifebook" of the alsa list shipped with 10.04), lead to high CPU usage (pulseaudio, xorg), buggy behaviour, freezes (see [here]("http://ubuntuforums.org/showthread.php?t=1524287"))

This model **manages** to supress internal speakers, when something is plugged in on "line-out" but does **not manage** to make the internal microphone work.

---

### Post by Alex Paderin on 2010-07-16
> **xtrman said:**
> For the Conexant 5069 card I have found a way to mute the internal speakers. 
Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz).
Then execute 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 1 
```to turn the internal speakers off and 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 0 
```to turn them on again.

I have also filed a bug report upstream on this.

Edit: I have now created a daemon to automattically mute and unmute the internal speakers when headphones are plugged in and removed.
Program:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```Compile with g++ main.cpp -o pinsensed
Run with sudo ./pinsensed

It's was usefull for me) I had appended some features to this code if u not has objections) Look this one [http://wildmagic.ru/public/pinsensed.tar.gz](http://wildmagic.ru/public/pinsensed.tar.gz).

---

### Post by tpsvca on 2010-07-22
> **Alex Paderin said:**
> It's was usefull for me) I had appended some features to this code if u not has objections) Look this one [http://wildmagic.ru/public/pinsensed.tar.gz](http://wildmagic.ru/public/pinsensed.tar.gz).

I'm totally dummy with Ubuntu, but i like it. Please give an instruction step by step, what i must to do to mute speakers, when my headphones is plugged in. (PC -> Asus k52F)

---

### Post by simosx on 2010-07-22
An important note here:

These 'model=' settings should normally not be required because Alsa should autodetect the hardware.

The way this should work is that we find the proper 'model=' line, we verify it, and then we supply a patch to the Alsa project so that the specific hardware gets autodetected!

Here is an example of this process,
[http://simos.info/blog/archives/984](http://simos.info/blog/archives/984)

If we get more of these 'model' lines converted to patches, we will be able to do some really good things to Alsa. At the same time, we get our names in the Linux kernel source code :-) :popcorn:

---

### Post by kittyjay14 on 2010-07-30
I'm a newbie and I tried your fix through the command line

My computer (HP 110-1030NR) didn't like this part in particular:

killall pulseaudio

sudo alsa force-reload

pulseaudio -D


Ever since then my speakers haven't worked.  Before it was just the microphone, but now the speakers are gone too!

This is what I got in response to the command:

user@user-laptop:~$  gksu gedit /etc/modprobe.d/alsa-base.conf
user@user-laptop:~$ killall pulseaudio
user@user-laptop:~$ 
user@user-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1598(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
.
user@user-laptop:~$ 
user@user-laptop:~$ pulseaudio -D
E: main.c: Daemon startup failed.
_____________

Help? Please?

---

### Post by lidex on 2010-07-31
> **kittyjay14 said:**
> I'm a newbie and I tried your fix through the command line

My computer (HP 110-1030NR) didn't like this part in particular:

killall pulseaudio

sudo alsa force-reload

pulseaudio -D


Ever since then my speakers haven't worked.  Before it was just the microphone, but now the speakers are gone too!



Help? Please?

Try a reboot. Those commands just reload alsa and pulse. Then check your volume levels.

---

### Post by EternalSoul on 2010-08-01
In Ubuntu 10.04 on Fujitsu-Siemens AMILO Pi1505 i added model=3stack-dig , rebooted and all worked well:D

Others maybe need to add this as well, although on older version of Ubuntu sound worked out of the box like a charm

---

### Post by simosx on 2010-08-01
> **EternalSoul said:**
> In Ubuntu 10.04 on Fujitsu-Siemens AMILO Pi1505 i added model=3stack-dig , rebooted and all worked well:D

Others maybe need to add this as well, although on older version of Ubuntu sound worked out of the box like a charm

Thanks.

Could you please run alsa-info.sh and post the details of your sound card? This will be useful to get those information in the Linux kernel so that new versions of Ubuntu will work out of the box for your hardware.

To run alsa-info.sh, run

1. wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh
2. bash alsa-info.sh

When prompted, select to upload the details to the alsa-project.org website. 
What you then need to do is post the URL you will be given here! That's it. :popcorn:

---

### Post by jmfal on 2010-08-07
bump, how come this isn`t a stickie????????

---

### Post by jmfal on 2010-08-08
bump

---

### Post by Detective RooTz on 2010-08-08
I have a Gateway GT5448E and that is not up there.

Also when I try to reload alsa it gives me this.

```

ganjafreak@ub3rl33tubuntu:~$ killall pulseaudio
ganjafreak@ub3rl33tubuntu:~$ sudo alsa force-reload
[sudo] password for ganjafreak: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ganjafreak/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ganjafreak/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
ganjafreak@ub3rl33tubuntu:~$ 


```

I need someone to remote connect to me and work this out wtih me and when it's done I'll jot it down for further reference.

---

### Post by Detective RooTz on 2010-08-08
Also my file is completly empty, like there is nothing in it. Blank.

---

### Post by simosx on 2010-08-08
> **Detective RooTz said:**
> I have a Gateway GT5448E and that is not up there.

Also when I try to reload alsa it gives me this.

```

ganjafreak@ub3rl33tubuntu:~$ killall pulseaudio
ganjafreak@ub3rl33tubuntu:~$ sudo alsa force-reload
[sudo] password for ganjafreak: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ganjafreak/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ganjafreak/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
ganjafreak@ub3rl33tubuntu:~$ 


```

I need someone to remote connect to me and work this out wtih me and when it's done I'll jot it down for further reference.

I already replied to your thread,
[http://ubuntuforums.org/showthread.php?t=1547605&page=2](http://ubuntuforums.org/showthread.php?t=1547605&page=2)

Perform the task that I am requesting in order to take this further.

---

### Post by cajunaggie on 2010-08-08
Does anyone know the model tag for a Toshiba Satellite A665? I went through this thread but I can't seem to find it anywhere. Thanks in advance.

---

### Post by jmfal on 2010-08-10
bump  make it a stickie

---

### Post by rowland.otieno on 2010-08-17
This worked on my Toshiba Satellite with Conexant 5069. Now I can mute the external and listen to music in privacy without disturbing anyone. And I did it after 3 days of searching. I defiantly refused to in back to Windows 7 just to watch movies and listen to music. Bless you hda-verb!

---

### Post by simosx on 2010-08-17
> **rowland.otieno said:**
> This worked on my Toshiba Satellite with Conexant 5069. Now I can mute the external and listen to music in privacy without disturbing anyone. And I did it after 3 days of searching. I defiantly refused to in back to Windows 7 just to watch movies and listen to music. Bless you hda-verb!

Tell us your exact settings so that we can see if those settings can be added to the Linux kernel so that in Ubuntu 10.10 it will work for you without a hitch.

To do so, 
[FONT="Courier New"]
wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT]
When prompted, select to send the information to alsa-project.org. Finally, copy and paste here the URL you will be given.

---

### Post by jmfal on 2010-08-22
bump

---

### Post by techlivezheng on 2010-08-23
I'm using a Lenovo Thinkpad SL410k 28428VC with Arch Linux,and i suffered the same probem that the speaer is still work with headphone pluggined in.

I followed the instruction [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"),and finally get it done.

1. Run

> cat /proc/asound/card0/codec#* | grep Codec

I get

> 
Codec: Realtek ALC269
Codec: Intel G45 DEVCTG


2. Run

> lspci | grep -i audio

I get

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

3. Run

>  aplay -l 

I get

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Above it is my hda audio information

So,i came to look at [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") to find something about ALC269,and i got this:

> 
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)


then,i tried adding > options snd-hda-intel model=MODEL to my > /etc/modprobe.d/alsa.conf one by one,and it's luky that the model 'quanta' get worked.

so,hope this can help somebody.Now,with headphone plugined in,the speaker auto switch off,otherwise,it switch on.

---

### Post by simosx on 2010-08-23
> **techlivezheng said:**
> I'm using a Lenovo Thinkpad SL410k 28428VC with Arch Linux,and i suffered the same probem that the speaer is still work with headphone pluggined in.

I followed the instruction [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"),and finally get it done.
.......
then,i tried adding  to my  one by one,and it's luky that the model 'quanta' get worked.

so,hope this can help somebody.Now,with headphone plugined in,the speaker auto switch off,otherwise,it switch on.

This is nice. What's missing is the PCI ID for the soundcard. You need to 'lspci -n' to find the PCI ID.

Then, you can track in the Alsa source code and find the location where you can specify, for your PCI ID, that the quirk to enable is the 'quanta' quirk. In doing so, Ubuntu 10.10 will support your hardware out of the box. Also, other Linux users irrespective of distro will be able to use their same sound card.

Some hints on what you need to do, [http://simos.info/blog/archives/984](http://simos.info/blog/archives/984)
If you manage to complete the task, it would be beneficial to report back.

---

### Post by techlivezheng on 2010-08-23
> **simosx said:**
> 
This is nice. What's missing is the PCI ID for the soundcard. You need to 'lspci -n' to find the PCI ID.

Then, you can track in the Alsa source code and find the location where you can specify, for your PCI ID, that the quirk to enable is the 'quanta' quirk. In doing so, Ubuntu 10.10 will support your hardware out of the box. Also, other Linux users irrespective of distro will be able to use their same sound card.

Some hints on what you need to do, [http://simos.info/blog/archives/984](http://simos.info/blog/archives/984)
If you manage to complete the task, it would be beneficial to report back.


I was hoping to contribute to the opensource project for a long time,but i didn't konwn how the opensource development works,i am not that familiar with the opensource cummutity,all the bug tracking,irc channel and mailing list are new to me.In china,it is not that easy to start doing all this things,the English community evironment,and the people around you can teach you nothing about that.It is very appreciate that you can help me to learn all this stuff.

OK,below is the result of ```
lspci -n
```:
```

00:00.0 0600: 8086:2a40 (rev 07)
00:02.0 0300: 8086:2a42 (rev 07)
00:02.1 0380: 8086:2a43 (rev 07)
00:1a.0 0c03: 8086:2937 (rev 03)
00:1a.1 0c03: 8086:2938 (rev 03)
00:1a.2 0c03: 8086:2939 (rev 03)
00:1a.7 0c03: 8086:293c (rev 03)
00:1b.0 0403: 8086:293e (rev 03)
00:1c.0 0604: 8086:2940 (rev 03)
00:1c.1 0604: 8086:2942 (rev 03)
00:1c.2 0604: 8086:2944 (rev 03)
00:1c.3 0604: 8086:2946 (rev 03)
00:1c.4 0604: 8086:2948 (rev 03)
00:1c.5 0604: 8086:294a (rev 03)
00:1d.0 0c03: 8086:2934 (rev 03)
00:1d.1 0c03: 8086:2935 (rev 03)
00:1d.2 0c03: 8086:2936 (rev 03)
00:1d.7 0c03: 8086:293a (rev 03)
00:1e.0 0604: 8086:2448 (rev 93)
00:1f.0 0601: 8086:2919 (rev 03)
00:1f.2 0106: 8086:2929 (rev 03)
00:1f.3 0c05: 8086:2930 (rev 03)
02:00.0 0880: 197b:2382
02:00.2 0805: 197b:2381
02:00.3 0880: 197b:2383
02:00.4 0880: 197b:2384
05:00.0 0280: 10ec:8172 (rev 10)
08:00.0 0200: 10ec:8168 (rev 03)
```

And according to ```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
```,i guess ```
00:1b.0 0403: 8086:293e (rev 03)
``` is what you mean the  PCI ID,especially ```
0403: 8086:293e
```&#65292;is that right?

Which alsa should i download ??

---

### Post by techlivezheng on 2010-08-23
> **simosx said:**
> This is nice. What's missing is the PCI ID for the soundcard. You need to 'lspci -n' to find the PCI ID.

Then, you can track in the Alsa source code and find the location where you can specify, for your PCI ID, that the quirk to enable is the 'quanta' quirk. In doing so, Ubuntu 10.10 will support your hardware out of the box. Also, other Linux users irrespective of distro will be able to use their same sound card.

Some hints on what you need to do, [http://simos.info/blog/archives/984](http://simos.info/blog/archives/984)
If you manage to complete the task, it would be beneficial to report back.

Ok,Now,I cloned the alsa-kernel git repo,and add a patch just follow yours,please have a look.

```
diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
index 6b00a23..10a720a 100644
--- a/sound/pci/hda/patch_realtek.c
+++ b/sound/pci/hda/patch_realtek.c
@@ -14487,6 +14487,7 @@ static const char *alc269_models[ALC269_MODEL_LAST] = {
 
 static struct snd_pci_quirk alc269_cfg_tbl[] = {
        SND_PCI_QUIRK(0x17aa, 0x3bf8, "Quanta FL1", ALC269_QUANTA_FL1),
+       SND_PCI_QUIRK(0x8086, 0x293e, "Lenovo Thinkpad SL410k 28428VC", ALC269_QUANTA_FL1),
        SND_PCI_QUIRK(0x1025, 0x047c, "ACER ZGA", ALC271_ACER),
        SND_PCI_QUIRK(0x1043, 0x8330, "ASUS Eeepc P703 P900A",
                      ALC269_AMIC),
@@ -19359,6 +19360,7 @@ static int patch_alc680(struct hda_codec *codec)
  * patch entries
  */
 static struct hda_codec_preset snd_hda_preset_realtek[] = {
+       { .id = 0x8086293e, .name = "ALC269", .patch = patch_alc269 },
        { .id = 0x10ec0260, .name = "ALC260", .patch = patch_alc260 },
        { .id = 0x10ec0262, .name = "ALC262", .patch = patch_alc262 },
        { .id = 0x10ec0267, .name = "ALC267", .patch = patch_alc268 },

```

---

### Post by Yehudama on 2010-08-23
Helpppppp Please!

I have installed 10.4 lucid , my laptop is ACER ASPIRE 4930ZG
Need configuration for the alsa.conf file , my internal mic is noisy
and in Skype is dead.

ehudama@yehudama-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevices:1/1
Subdevices: #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevices: #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevices: #0: subdevice #0

Try to put in alsa.conf file:

options snd-hda-intel model=acer-aspire-4930g

doesn't help much. any solution?

---

### Post by simosx on 2010-08-23
> **techlivezheng said:**
> I was hoping to contribute to the opensource project for a long time,but i didn't konwn how the opensource development works,i am not that familiar with the opensource cummutity,all the bug tracking,irc channel and mailing list are new to me.In china,it is not that easy to start doing all this things,the English community evironment,and the people around you can teach you nothing about that.It is very appreciate that you can help me to learn all this stuff.

OK,below is the result of ```
lspci -n
```:
```

00:00.0 0600: 8086:2a40 (rev 07)
00:02.0 0300: 8086:2a42 (rev 07)
00:02.1 0380: 8086:2a43 (rev 07)
00:1a.0 0c03: 8086:2937 (rev 03)
00:1a.1 0c03: 8086:2938 (rev 03)
00:1a.2 0c03: 8086:2939 (rev 03)
00:1a.7 0c03: 8086:293c (rev 03)
00:1b.0 0403: 8086:293e (rev 03)
00:1c.0 0604: 8086:2940 (rev 03)
00:1c.1 0604: 8086:2942 (rev 03)
00:1c.2 0604: 8086:2944 (rev 03)
00:1c.3 0604: 8086:2946 (rev 03)
00:1c.4 0604: 8086:2948 (rev 03)
00:1c.5 0604: 8086:294a (rev 03)
00:1d.0 0c03: 8086:2934 (rev 03)
00:1d.1 0c03: 8086:2935 (rev 03)
00:1d.2 0c03: 8086:2936 (rev 03)
00:1d.7 0c03: 8086:293a (rev 03)
00:1e.0 0604: 8086:2448 (rev 93)
00:1f.0 0601: 8086:2919 (rev 03)
00:1f.2 0106: 8086:2929 (rev 03)
00:1f.3 0c05: 8086:2930 (rev 03)
02:00.0 0880: 197b:2382
02:00.2 0805: 197b:2381
02:00.3 0880: 197b:2383
02:00.4 0880: 197b:2384
05:00.0 0280: 10ec:8172 (rev 10)
08:00.0 0200: 10ec:8168 (rev 03)
```

And according to ```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
```,i guess ```
00:1b.0 0403: 8086:293e (rev 03)
``` is what you mean the  PCI ID,especially ```
0403: 8086:293e
```&#65292;is that right?

Which alsa should i download ??

(yep, you got the correct PCI ID).

What you need to do is be able to test any changes before you send them to the Alsa project.

1. For this, you need to build the latest (snapshot) Alsa using the instructions at [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
Thus, the first step is to build the latest Alsa and confirm that it works.

2. Then, remove the 'model=quanta' line from the configuration file in /etc/ and restart your computer. 

3. Verify that with the latest Alsa the problem actually exists, thus you need to fix.

I prefer to 

[FONT="Courier New"]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT]

Then, I save the output when prompted. You can verify from the output which version of alsa driver-kernel, alsa lib and alsa utils you have.

4. Now locate the file 'patch_realtek.c'. It should be in a alsa-kernel/pci/hda/ subfolder, and it's about 600KB.

(just noticed you already replied with patch. sending this message and reading your reply)

---

### Post by simosx on 2010-08-23
> **techlivezheng said:**
> Ok,Now,I cloned the alsa-kernel git repo,and add a patch just follow yours,please have a look.

```
diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
index 6b00a23..10a720a 100644
--- a/sound/pci/hda/patch_realtek.c
+++ b/sound/pci/hda/patch_realtek.c
@@ -14487,6 +14487,7 @@ static const char *alc269_models[ALC269_MODEL_LAST] = {
 
 static struct snd_pci_quirk alc269_cfg_tbl[] = {
        SND_PCI_QUIRK(0x17aa, 0x3bf8, "Quanta FL1", ALC269_QUANTA_FL1),
+       SND_PCI_QUIRK(0x8086, 0x293e, "Lenovo Thinkpad SL410k 28428VC", ALC269_QUANTA_FL1),
        SND_PCI_QUIRK(0x1025, 0x047c, "ACER ZGA", ALC271_ACER),
        SND_PCI_QUIRK(0x1043, 0x8330, "ASUS Eeepc P703 P900A",
                      ALC269_AMIC),
@@ -19359,6 +19360,7 @@ static int patch_alc680(struct hda_codec *codec)
  * patch entries
  */
 static struct hda_codec_preset snd_hda_preset_realtek[] = {
+       { .id = 0x8086293e, .name = "ALC269", .patch = patch_alc269 },
        { .id = 0x10ec0260, .name = "ALC260", .patch = patch_alc260 },
        { .id = 0x10ec0262, .name = "ALC262", .patch = patch_alc262 },
        { .id = 0x10ec0267, .name = "ALC267", .patch = patch_alc268 },

```

That looks great to me. Follow my previous steps so that you compile and test these changes. You need to restart Alsa (either reboot or sudo /sbin/alsa force-reload) and get it to detect your soundcard without having the 'model=quanta' hint. Once your patch achieves this, then you can post to the alsa-devel mailing list for the developer to include in Alsa.

---

### Post by Aegiusfang on 2010-08-23
Hello new to the forums and Ubuntu. I installed Ubuntu 10.04 over the weekend and do not have any sound. I have been scouring the forums this thread as well as [http://ubuntuforums.org/showthread.php?t=1509958&highlight=intel+ich9](http://ubuntuforums.org/showthread.php?t=1509958&highlight=intel+ich9) i followed the instructions and nothing really came of it. in fact now when i try the system testing it seems to hang up. Really though the instructions in the above post would help since the model of laptop is that same MSI 6275. Any suggestions on how to determine the correct settings for my sound card or is a trial and error process. Any help would be greatly appreciated

---

### Post by simosx on 2010-08-24
> **Aegiusfang said:**
> Hello new to the forums and Ubuntu. I installed Ubuntu 10.04 over the weekend and do not have any sound. I have been scouring the forums this thread as well as [http://ubuntuforums.org/showthread.php?t=1509958&highlight=intel+ich9](http://ubuntuforums.org/showthread.php?t=1509958&highlight=intel+ich9) i followed the instructions and nothing really came of it. in fact now when i try the system testing it seems to hang up. Really though the instructions in the above post would help since the model of laptop is that same MSI 6275. Any suggestions on how to determine the correct settings for my sound card or is a trial and error process. Any help would be greatly appreciated

Read the last posts in this thread. It helps if you can produce the 'alsa-info.sh' output. The information 'intel ich9' is not descriptive enough to warrant advice. The alsa-info.sh output is better. Once you have that, read the first post in this thread on the process of trying out different models. Finally, once you find a model (assuming it exists), help in informing the ALSA developers so that Ubuntu 10.10 supports your laptop out of the box.

---

### Post by Aegiusfang on 2010-08-24
I tried following the directions for taking a snapshot in step one above however I wasn't able to download the files in order to compile and install them. I then proceeded to use the wget command which produced 2 files:

alsa-info.sh

--2010-08-24 16:17:48--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80]("http://www.alsa-project.org%7C212.20.107.51%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-08-24 16:17:56--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80").
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `index.html?p=alsa-driver.git;a=blob_plain;f=utils%2Falsa-info.sh'

     0K .......... .......... ......                           22.2K=1.2s

2010-08-24 16:17:58 (22.2 KB/s) - `index.html?p=alsa-driver.git;a=blob_plain;f=utils%2Falsa-info.sh' saved [27026]



index.html?p=alsa-driver.git;a=blob_plain;f=utils%2Falsa-info.sh
Edit: Removed details of this file as they were extremely long.

I am not sure but the second file looks like the script i was asked to download.
As to getting more information I am not sure if lspci -v command will give additional info:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 6740
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Also the command aplay -l gives:

card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I am not sure if this information is of any help. If not I would appreciate help in resolving the inability to download the alsa snapshot files. I did record a log file for that but have not included it here.

---

### Post by gordintoronto on 2010-08-24
My computer is an HP G62 laptop, with 3 GB of memory, 320 GB hard drive, and AMD Athlon(tm) II P320 Dual-Core Processor. (The G62 is really a family of computers, thanks HP.)

Lspci: Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

Aplay: card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Sound works nicely now.

alsa-base.conf:
options snd-hda-intel model=auto

AND in Sound Preferences, select Output "connector," "analog speakers."

Sound comes out of the speakers when there are no earphones plugged in, then out of the earphones when I plug them in.

I'm running Lucid, 2.6.32-24-generic.

---

### Post by lidex on 2010-08-26
*Aegiusfang*
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Mariane on 2010-08-27
Please, anybody knows the line for a Dell Vostro 1520? Sound card is intel hda. 

Mariane

---

### Post by lidex on 2010-08-27
> **Mariane said:**
> Please, anybody knows the line for a Dell Vostro 1520? Sound card is intel hda. 

Mariane
Need to know your codec:
[In a terminal]

```
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by Aegiusfang on 2010-09-02
Thanks for the help. I was able to resolve my problem.

---

### Post by eds1 on 2010-09-10
> **Mariane said:**
> Please, anybody knows the line for a Dell Vostro 1520? Sound card is intel hda. 

Mariane

Mariane, I have the Vostro 1520, and model=dell-m23 worked for me as described in the first post on this thread.  Hope that helps.

---

### Post by nustrydas on 2010-09-29
hi everybody,

does someone know what model is for Asus K52F laptop? 
card: Intel HDA
codec: Conexant CX20585

i've searched through 
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)
but was not able to find appropriate model.

any help would be appreciated.

:confused:

---

### Post by lidex on 2010-09-29
> **nustrydas said:**
> hi everybody,

does someone know what model is for Asus K52F laptop? 
card: Intel HDA
codec: Conexant CX20585

i've searched through 
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)
but was not able to find appropriate model.

any help would be appreciated.

:confused:
Go here:
[http://ubuntuforums.org/showthread.php?p=9162799](http://ubuntuforums.org/showthread.php?p=9162799)

---

### Post by wmalik on 2010-10-03
Hi, I have a Sony Vaio VGN-CS26G. I am using Ubuntu 10.04 LTS and  the built-in microphone of my laptop was not working out of the box. I had to perform the following steps to make it work:

[LIST=1]
[*]**sudo nano /etc/modprobe.d/alsa-base.conf**
[*]Add the following line at the end of the file
[INDENT]**options snd-hda-intel model=auto**[/INDENT]
[*]Reboot your machine
[*]Open **gnome-sound-recorder** and try recording
[/LIST]

I hope it helps.

---

### Post by kariem2k on 2010-10-05
> **Wandang said:**
> Ubuntu 10.04

MSI Ex623

```
wandang@wandang:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8ef8000 irq 30
wandang@wandang:~$ cat /proc/asound/modules
 0 snd_hda_intel
wandang@wandang:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```

only sound throu headset after installation.
fixed with:
```
options snd-hda-intel model=targa-2ch-dig
alternativ (both worked):
options snd-hda-intel model=targa-dig
```

Headphone,External Mic, Jacksensing, No Internal Mic

```
options snd-hda-intel model=uniwill
```

Also use the drivers
[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

See:
[http://kariem2k.blogspot.com/2010/10/msi-ex623-sound-problems-on-alsa-linux.html](http://kariem2k.blogspot.com/2010/10/msi-ex623-sound-problems-on-alsa-linux.html)

---

### Post by MarkieB on 2010-10-06
no longer participating in ubuntuforums.org

---

### Post by mutha88 on 2010-10-10
> **kariem2k said:**
> Headphone,External Mic, Jacksensing, No Internal Mic

```
options snd-hda-intel model=uniwill
```Also use the drivers
[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

See:
[http://kariem2k.blogspot.com/2010/10/msi-ex623-sound-problems-on-alsa-linux.html](http://kariem2k.blogspot.com/2010/10/msi-ex623-sound-problems-on-alsa-linux.html)


Thank you, friend! I have the same audio chipset (ALC1200) and I'll try this solution later this week. The only OS I've got it working is XP... Now I can finally enjoy it under Ubuntu!

Thanks again!

---

### Post by heyho on 2010-10-30
Fujitsu Siemens Amilo pi1505 works with:

```
options snd-hda-intel model=3stack-dig
```

This enabled the speakers when only the headphone jack appeared to work.

Using 10.04/Mint 9 Isadora. I have never had to do this before (mind you, I have been using Jaunty until updates stopped yesterday!)

Ubuntu forums I love you.

---

### Post by asbesto on 2010-11-03
Sony VAIO VGN-NR31S

it works using "basic"  in /etc/modprobe.d/alsa-base.conf


```


options snd-hda-intel model=basic


```

...on debian squeeze. I left Ubuntu months ago, because is now a monster full of unuseful things and complications.

---

### Post by vishudh on 2010-11-05
for Toshiba Satellite C650
> 
options snd-hda-intel model=ideapad


---

### Post by bdudek on 2010-12-03
Ubuntu 10.10 x86_64
Intel DP55WG Motherboard

aplay -l
      card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
        Subdevices: 1/1
        Subdevice #0: subdevice #0
      card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
        Subdevices: 1/1
        Subdevice #0: subdevice #0


/etc/modprobe.d/alsa-base.conf
      options snd-hda-intel model=6stack-dig

Works fine. You can select either Analog or Digital SPDIF from the Hardware Tab in Sound Preferences.

---

### Post by simosx on 2010-12-06
I am writing an article on how to put these model information into the Alsa, so that in newer versions of Linux it would work without a hitch. 
If anyone wants to be my guinea pig and follow the instructions, please PM me.
If all goes well, you will be a Linux kernel contributor (the change is added to the Linux kernel).

---

### Post by ericmc783 on 2010-12-09
> **xtrman said:**
> For the Conexant 5069 card I have found a way to mute the internal speakers. 



I just purchased an asus k52f notebook. your fix here worked awesome. thank you.

---

### Post by ericmc783 on 2010-12-10
> **xtrman said:**
> For the Conexant 5069 card I have found a way to mute the internal speakers. 
Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz).
Then execute 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 1 
```to turn the internal speakers off and 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 0 
```to turn them on again.

I have also filed a bug report upstream on this.

Edit: I have now created a daemon to automattically mute and unmute the internal speakers when headphones are plugged in and removed.
Program:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```Compile with g++ main.cpp -o pinsensed
Run with sudo ./pinsensed


This fix works for me. However, I have to re-apply the fix every time I bootup, as it does not stay fixed after reboot. (specifically, I have to run both *Compile with g++ main.cpp -o pinsensed* AND *sudo ./pinsensed*). Could someone assist me with how to have Ubuntu apply this fix automatically everytime I log in? I'd really appreciate it and offer my deepest thanks. :-)

---

### Post by simosx on 2010-12-12
> **ericmc783 said:**
> This fix works for me. However, I have to re-apply the fix every time I bootup, as it does not stay fixed after reboot. (specifically, I have to run both *Compile with g++ main.cpp -o pinsensed* AND *sudo ./pinsensed*). Could someone assist me with how to have Ubuntu apply this fix automatically everytime I log in? I'd really appreciate it and offer my deepest thanks. :-)

What you would do is copy the program into some location of your system

```
sudo cp pinsensed /usr/local/bin/
```

and then edit the rc.local file for local bootup programs with

```
sudo gedit /etc/rc.local
```

and in the editor add the line '/usr/local/bin/pinsensed'. You add this before the 'exit 0' line. Finally reboot, and that's it!

---

### Post by lxapp on 2010-12-12
I'm using lenovo 3000Y500 7761 52Q with Ubuntu 10.04. Subwoofer and mic are not working, however, the two front speakers are working, but the sound is too low if the subwoofer is not working. Can someone suggest what is to be added in alsa-base.conf?

I've been stuck on this for more than a week.

---

### Post by lidex on 2010-12-12
> **lxapp said:**
> I'm using lenovo 3000Y500 7761 52Q with Ubuntu 10.04. Subwoofer and mic are not working, however, the two front speakers are working, but the sound is too low if the subwoofer is not working. Can someone suggest what is to be added in alsa-base.conf?

I've been stuck on this for more than a week.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Yellow Pasque on 2010-12-12
```
ALC262
======
  fujitsu	Fujitsu Laptop
  hp-bpc	HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000	HP BPC D7000
  hp-tc-t5735	HP Thin Client T5735
  hp-rp5700	HP RP5700
  benq		Benq ED8
  benq-t31	Benq T31
  hippo		Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1	Hippo (Benq) with jack detection
  sony-assamd	Sony ASSAMD
  toshiba-s06	Toshiba S06
  toshiba-rx1	Toshiba RX1
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)
```
Hmm. Maybe try lenovo-3000 keyword

---

### Post by lxapp on 2010-12-13
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

The link where the alsa information is located at
```
http://www.alsa-project.org/db/?f=7f5b29b714dea7937b1caddef4326f45215c7d3e

```

---

### Post by ericmc783 on 2010-12-13
> **simosx said:**
> What you would do is copy the program into some location of your system

<shortened>

and in the editor add the line '/usr/local/bin/pinsensed'. You add this before the 'exit 0' line. Finally reboot, and that's it!

This fixed it. Thank you! :-)

---

### Post by lxapp on 2010-12-14
> **lxapp said:**
> I'm using lenovo 3000Y500 7761 52Q with Ubuntu 10.04. Subwoofer and mic are not working, however, the two front speakers are working, but the sound is too low if the subwoofer is not working. Can someone suggest what is to be added in alsa-base.conf?

I've been stuck on this for more than a week.

You can find the alsa information of my system at:

```

http://www.alsa-project.org/db/?f=7f5b29b714dea7937b1caddef4326f45215c7d3e
```

I've tried,  model=lenovo ,
                model=lenovo-3000 , and
                model=auto so far. Still the subwoofer is not working.

Expecting help soon.

---

### Post by lidex on 2010-12-14
@lxapp
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by lxapp on 2010-12-15
> **lidex said:**
> @lxapp
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Tried updating alsa. Still the subwoofer of my laptop has not been picked up by alsa. Should I try oss? Subwoofer had worded fine when i had been using openSuse 10.3, which I believe, used oss. Is there anything else to try with alsa?

---

### Post by Mariane on 2010-12-16
> **lidex said:**
> Need to know your codec:
[In a terminal]

```
head -n 1 /proc/asound/card*/codec#* 
```

Answer is:
head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD81B1C5

Mariane

---

### Post by simosx on 2010-12-16
> **Mariane said:**
> Answer is:
head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD81B1C5

Mariane

See comment #2 at [https://bugzilla.redhat.com/show_bug.cgi?id=628003#c2](https://bugzilla.redhat.com/show_bug.cgi?id=628003#c2)
for the correct model.
(I did a google search for 92HD81B1C5)

Try it and tell us if it works. Some guy tried to fix it though it did not make it, [http://www.spinics.net/linux/fedora/alsa-user/msg09027.html](http://www.spinics.net/linux/fedora/alsa-user/msg09027.html)
If you are interested, we can help you fix this in the Linux kernel.
For this, you would need to provide the alsa-info output for your sound card.
See [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) on how to do this,
then post the URL to the hardware information.

---

### Post by raven88 on 2010-12-17
Hi all I didn't get my surround Sound working on my Laptop Acer 7520G with Ubuntu 10.10 I hope you could help me. Here is my Sound config.

[http://www.alsa-project.org/db/?f=a35a06acce490addec5688f58d56b6aaef83a94b](http://www.alsa-project.org/db/?f=a35a06acce490addec5688f58d56b6aaef83a94b)

With best regards
Tobias

---

### Post by gsullice on 2011-01-27
Toshiba Satellite L655-S5071:

options snd-hda-intel model=thinkpad

---

### Post by cyncicle on 2011-02-12
Dell XPS M140 (STAC 9200)

model=panasonic

ALSA 1.0.23

Glad I ran across this thread, the lack of sound was really annoying!  I tried OSS v4, and the sound worked, but it wasn't the ideal option.

---

### Post by Tiger85 on 2011-03-03
Dell Latitude E6400 IDT 92HD71B7X / STA92HD71B7X

options snd-hda-intel model=dell-m4-2

Alsa 1.0.22.1+dfsg-0ubuntu3
Ubuntu 10.04 


This codec / driver enables digital sound over HDMI / Displayport for this Dell Latitude model :)

---

### Post by foockinho on 2011-03-03
sorry this post is out of topic

---

### Post by foockinho on 2011-03-03
Hi 

In addition to your database

Samsung NP-R40 ALC262 chip works with "snd-hda-intel probe_mask=8 model=toshiba-s06" option placed on alsa-base.conf

byee

---

### Post by uhurusurfa on 2011-03-07
Dell Inspiron 1721 with Maverick: Sound works fine but external mic input is flaky.
The alsa-base.conf has no snd-hda-intel entry (using model=dell-m42 or model=dell-m44 does not work).
Plugging in external mic then restarting also (sudo alsa force-reload) and external mic starts working. You can unplug and the built-in mic takes over as expected but plugging external back in does not switch back to external mic (internal carries on working). Restarting alsa with ext mic plugged in seems only way to get it to work.

---

### Post by jaxxed on 2011-03-26
I wonder if you could help me with my card.

The machine is an ASUS AIO (ET2400IGTS).  The card Codec: Realtek ALC887

Behvaiour is that the sound works, the speakers sound great, but when trying to use the headphone jack, the sound goes quiet on the speakers but nothing comes out of the jack.

[http://www.alsa-project.org/db/?f=fc249ee28ce68bd0735926ced9649cdae25774fd](http://www.alsa-project.org/db/?f=fc249ee28ce68bd0735926ced9649cdae25774fd)

I've tried options model=auto and model=generic, but neither solves the problem.

---

### Post by Yellow Pasque on 2011-03-26
@jaxxed: Seems to be a common issue: [https://lists.linux-foundation.org/pipermail/bugme-new/2010-February/024298.html](https://lists.linux-foundation.org/pipermail/bugme-new/2010-February/024298.html)

---

### Post by jaxxed on 2011-03-28
@Temüjin: thanks.  I'll check it out and try to register on the kernel bug.

---

### Post by beansdad on 2011-03-30
options snd-hda-intel model=auto

worked with my Acer Aspire 7730

Many, many thanks for solving this long standing problem.

---

### Post by oooh on 2011-04-06
options snd-hda-intel model=sony

Works for me, on Sony Vaio FZ21M, with a Nvidia GForce800M

However, HDMI DOES NOT WORK !!

```
aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Any idea what could be wrong ? I have the latest Nvidia 260 from the Nvidia website

---

### Post by lidex on 2011-04-06
> **oooh said:**
> options snd-hda-intel model=sony

Works for me, on Sony Vaio FZ21M, with a Nvidia GForce800M

However, HDMI DOES NOT WORK !!

```
aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Any idea what could be wrong ? I have the latest Nvidia 260 from the Nvidia website

Have a look at this thread and ask questions over there:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by rrklinux on 2011-05-01
[SIZE=3][COLOR=Red]hi friends,
  
i have problem with my [COLOR=DarkGreen]lenovo z560[/COLOR]. Both  the headphone and internal speaker play at the same time. I have tried  everything posted in the forum.
  
my alsa.base conf file is as follows[/COLOR][/SIZE]
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it  anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=20060 enable=1 index=0
options snd-hda-intel enable_msi=1
#options snd-hda-intel model=laptop
#options snd-hda-intel model=lenovo 
#options snd-hda-intel model=thinkpad
#options snd-hda-intel probe_mask=1

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

[SIZE=3][COLOR=Red]please help me to get the problem solved.
  
with regards,[/COLOR][/SIZE]

rr

---

### Post by DShad on 2011-05-01
Let me know if you ever find the fix cause I have the same notebook and the exact same problem

Thanks

 > **rrklinux said:**
> [SIZE=3][COLOR=Red]hi friends,
  
i have problem with my [COLOR=DarkGreen]lenovo z560[/COLOR]. Both  the headphone and internal speaker play at the same time. I have tried  everything posted in the forum.
  
my alsa.base conf file is as follows[/COLOR][/SIZE]
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it  anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=20060 enable=1 index=0
options snd-hda-intel enable_msi=1
#options snd-hda-intel model=laptop
#options snd-hda-intel model=lenovo 
#options snd-hda-intel model=thinkpad
#options snd-hda-intel probe_mask=1

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

[SIZE=3][COLOR=Red]please help me to get the problem solved.
  
with regards,[/COLOR][/SIZE]

rr

---

### Post by Raberra on 2011-05-02
Gateway ID49C13u

options snd-hda-intel model=thinkpad

works for headphone jack

---

### Post by samizdatstudio on 2011-05-04
> **the_guv said:**
> hey *shinjimx .. *tx to you, i now have ACDC rocking my sys!

:guitar::guitar::guitar:

couple things tho .. for some folks, i think jaunty up

you may need to use "alsa-base.conf", rather than "alsa-base"

dunno if it's me or my setup, somehow, but for me it worked with hyphens rather than underscores, so i made that ..

 options snd-hda-intel-model=hp-dv5

er, dunno about Metallica, mind ;)  call me old-fashioned.
anyone know the code for fujitsu u810?
i try many seem not work well..

thanks

i only try 

"
options snd-hda-intel model=hp

"

do it need add "options snd-hda-intel enable_msi=1"
what does it code use for?
thanks

---

### Post by riftware on 2011-05-11
These entries / knowledge were found elsewhere, unfortunately I don't know who to credit but considering how hard it was for me to find them I think it's worth posting here to save others grief.

CLEVO P170HM   / Origin PC EON-17S  / also sager and ayva direct models based on Clevo p170HM
Sound based on Realtek ALC892  running under HDA Intel PCH codec

 If you are having trouble with headphone not turning speakers off the laptop has built in function  hit "fn + 5" not F5 .    This toggles the laptop speaker mode ( I bought it for development but apparently it has like 5 speakers plus a subwoofer built into it)     - I find it best to leave Pulse on Internal Audio Analog Stereo, Port "Analog Speakers" .    Then plug a head phone in and play something.   If you hear sound  hit "fn + 5"  - that should switch it to headphone only.    after that  plugging /unplugging the headphones works properly.  


If you are dealing with HDMI audio issues the other poster found adding this line to alsa-base.conf caused aplay -l to stop showing 4 or 5 hdmi sound devices and reduced it down to 1 which seems to work for them.  [FONT=Courier New]**options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff**2

He's not quite sure why and I would be interested in any tweaks anyone comes up with to refine either of these things.
[/FONT]

---

### Post by Serpentine Cougar on 2011-06-27
I have a **Toshiba Satellite L655-S5061** laptop and my headphones and microphone didn't work until I used the following:
[B]
options snd-hda-intel model=ideapad[/B]

---

### Post by Orlando84 on 2011-06-28
Hi all!
Samsung R40plus finally works fine with microphone under Ubuntu 10.10
sudo gedit /etc/modprobe.d/alsa-base
#add following line to the bottom of this file
option snd-hda-intel model=laptop
I've been searching for solution for a weeks, even recompiled alsa for another driver, but it's obvious  and better solution
Have a nice day!:)

---

### Post by CVirus on 2011-07-05
You're my new God .. Thanks a million !

> **xtrman said:**
> For the Conexant 5069 card I have found a way to mute the internal speakers. 
Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz).
Then execute 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 1 
```to turn the internal speakers off and 
```
sudo hda-verb /dev/snd/hwC0D0 0x1f 0x701 0 
```to turn them on again.

I have also filed a bug report upstream on this.

Edit: I have now created a daemon to automattically mute and unmute the internal speakers when headphones are plugged in and removed.
Program:
```

/* 
 * File:   main.cpp
 * Author: xtr
 *
 * Created on April 26, 2010, 5:26 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/io.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <syslog.h>
#include <signal.h>

#include <stdint.h>
typedef uint8_t u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

#define HDA_VERB(nid,verb,param)    ((nid)<<24 | (verb)<<8 | (param))
#define HDA_IOCTL_VERB_WRITE        _IOWR('H', 0x11, struct hda_verb_ioctl)

struct hda_verb_ioctl {
    u32 verb;    /* HDA_VERB() */
    u32 res;    /* response */
};

void daemonize()
{
    pid_t pid, sid;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
            exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then
       we can exit the parent process. */
    if (pid > 0) {
            exit(EXIT_SUCCESS);
    }

    /* Change the file mode mask */
    umask(0);

    /* Open any logs here */
    openlog("pinsensed", LOG_PID, LOG_DAEMON);
    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }

    /* Change the current working directory */
    if ((chdir("/")) < 0) {
            /* Log any failure here */
            exit(EXIT_FAILURE);
    }


    /* Close out the standard file descriptors */
    close(STDIN_FILENO);
    close(STDOUT_FILENO);
    close(STDERR_FILENO);

}

bool done = false;

void trpsig(int)
{
    done = true;
}

int main(int argc, char** argv) {
    daemonize();
    signal(SIGTERM, &trpsig);

    int fd, state;
    struct hda_verb_ioctl val;
    syslog(LOG_INFO, "Daemon started.");
    fd = open("/dev/snd/hwC0D0", O_RDWR);
    if (fd < 0) {
        syslog(LOG_ERR, "Failed to open snd device.");
            exit(EXIT_FAILURE);
    }
    val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");
    state = val.res >> 31;
    syslog(LOG_INFO, "Starting input value: %0x", state);
    while(!done)
    {
        sleep(1);
        val.verb = HDA_VERB(0x19, 0x0f09, 0x0);
        if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
            syslog(LOG_ERR, "Failed to write hda verb.");

        if(state != (val.res >> 31))
        {
            state = (val.res >> 31);
            syslog(LOG_INFO, "New input value: %0x", state);
            if(state == 0x1)
                val.verb = HDA_VERB(0x1f, 0x701, 0x1);
            else
                val.verb = HDA_VERB(0x1f, 0x701, 0x0);
            if (ioctl(fd, HDA_IOCTL_VERB_WRITE, &val) < 0)
                syslog(LOG_ERR, "Failed to write hda verb.");
        }
    }
    close(fd);
    syslog(LOG_INFO, "Daemon stopped.");
    exit(EXIT_SUCCESS);
}

```Compile with g++ main.cpp -o pinsensed
Run with sudo ./pinsensed

---

### Post by finomeno on 2011-07-07
Thought this might help somebody else out there.
The mic on my Lenovo G470 worked perfectly under Win7, but was totally silent under K/Ubuntu 11.04.

Adding the following line to the bottom of my */etc/modprobe.d/alsa-base.conf* did the trick.

```
#Load proper sound driver (mic fix)
options snd-hda-intel model=laptop position_fix=1 enable=yes
```

**UPD**
This fixes only the mic problem. Moreover, *position_fix=1 enable=yes* doesn't seem to have any influence on it. Unfortunately, this fix **does not** make the headphones jack work. Changing *model=laptop* to *model=ideapad* fixes the headphones, but screws the mic.
Still looking for a solution.

*cat /proc/asound/card0/codec* | grep Codec* outputs *[COLOR="Purple"]Conexant CX20590[/COLOR]* (which appears to be more widely known as *CX506e*, closely related to *CX5066*)

Cheers!

---

### Post by Yellow Pasque on 2011-07-07
@finomeno: Thanks for that. The multiple Conexant chip names are ridiculous and don't make for easy googling.

---

### Post by Wouter N on 2011-07-08
For the Asus K52F (mine is a ASUS K52f-sx051v) with the Conexant 20585 card(mine is rev06), add the following to /etc/modprobe.d/sound.conf

```

options snd-hda-intel model=ideapad

```

Hope this is helpful to some people.

---

### Post by sicode on 2011-07-18
Hi!

Dell Vostro 3750
Codec Realtek ALC269VB

Headphones doesn't work.

---

### Post by musa118 on 2011-07-18
Help! Mic internal not working, ALC269VB Toshiba Satelite pro r850-16h

---

### Post by csoler on 2011-07-19
> **riftware said:**
> These entries / knowledge were found elsewhere, unfortunately I don't know who to credit but considering how hard it was for me to find them I think it's worth posting here to save others grief.

CLEVO P170HM   / Origin PC EON-17S  / also sager and ayva direct models based on Clevo p170HM
Sound based on Realtek ALC892  running under HDA Intel PCH codec

 If you are having trouble with headphone not turning speakers off the laptop has built in function  hit "fn + 5" not F5 .    This toggles the laptop speaker mode ( I bought it for development but apparently it has like 5 speakers plus a subwoofer built into it)     - I find it best to leave Pulse on Internal Audio Analog Stereo, Port "Analog Speakers" .    Then plug a head phone in and play something.   If you hear sound  hit "fn + 5"  - that should switch it to headphone only.    after that  plugging /unplugging the headphones works properly.  


If you are dealing with HDMI audio issues the other poster found adding this line to alsa-base.conf caused aplay -l to stop showing 4 or 5 hdmi sound devices and reduced it down to 1 which seems to work for them.  [FONT=Courier New]**options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff**2

He's not quite sure why and I would be interested in any tweaks anyone comes up with to refine either of these things.
[/FONT]

My eternal recognition  goes to you !! Thanks! I spent 28h trying to find how to mute the speaker.

---

### Post by JDorfler on 2011-09-14
> **riftware said:**
> These entries / knowledge were found elsewhere, unfortunately I don't know who to credit but considering how hard it was for me to find them I think it's worth posting here to save others grief.

CLEVO P170HM   / Origin PC EON-17S  / also sager and ayva direct models based on Clevo p170HM
Sound based on Realtek ALC892  running under HDA Intel PCH codec

 If you are having trouble with headphone not turning speakers off the laptop has built in function  hit "fn + 5" not F5 .    This toggles the laptop speaker mode ( I bought it for development but apparently it has like 5 speakers plus a subwoofer built into it)     - I find it best to leave Pulse on Internal Audio Analog Stereo, Port "Analog Speakers" .    Then plug a head phone in and play something.   If you hear sound  hit "fn + 5"  - that should switch it to headphone only.    after that  plugging /unplugging the headphones works properly.  


If you are dealing with HDMI audio issues the other poster found adding this line to alsa-base.conf caused aplay -l to stop showing 4 or 5 hdmi sound devices and reduced it down to 1 which seems to work for them.  [FONT=Courier New]**options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff**2

He's not quite sure why and I would be interested in any tweaks anyone comes up with to refine either of these things.
[/FONT]

Thank you, sir.

---

### Post by solitary.angler on 2011-09-18
**Fujitsu Siemens AMILO Pa1510 Realtek ALC861**
AMD-Turion64
ATI Radeon Xpress 1100

/etc/modprobe.d/alsa-base.conf :
**options snd-hda-intel model=3stack-660 position_fix=1 enable=yes**

~ $ uname -a
Linux Capucine 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
(Linux Mint 11 Katya)

~ $ lspci -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Fujitsu Technology Solutions Realtek High Definition Audio
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

~ $ more /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

~ $ more /proc/asound/card0/codec#1
Codec: Realtek ALC861

~ $ more /proc/asound/modules 
 0 snd_hda_intel

~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~ $ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

AlsaMixer v1.0.24.2

---------------------------------------

Thank you,

 -Auro

PS: Internal speakers and Headphones were working fine. I had to add this to get the external mic working. I don't think this laptop has an internal mic. I don't see one (the laptop belongs to a friend). Now I can use headphones or the internal speakers with an external mic to use Skype for example.

PPS: Thank you very very much for this database! It sure helped me a lot.

---

### Post by UndeRus on 2011-09-28
Acer 5755G, speakers works, microphone works(internal and on headset), headphones doesn't work

Alsa info log output [http://www.alsa-project.org/db/?f=cc03a2b3a03dca2bd14c48796a828d953eacaaff](http://www.alsa-project.org/db/?f=cc03a2b3a03dca2bd14c48796a828d953eacaaff)

---

### Post by finomeno on 2011-10-02
Update for **Lenovo G470** (and possibly for some other Lenovo *Essential* and *Ideapad* series laptops/notebooks).

After several updates (from official ubuntu repos, not PPAs) one of the modes did the trick for me (albeit with a little glitch).

Making sure you have the latest alsa drivers installed and inserting ```
options snd-hda-intel model=asus
``` into */etc/modprobe.d/alsa-base.conf* enables the internal mic and the switching between speakers/headphones.

**Note** that you might need to ajust sound/mic volumes through PulseAudio Volume Control (pavucontrol) and check for the correct devices through PulseAudio Device Chooser (padevchooser). For more details on this see [u0x's blog]("http://u0x.blog138.fc2.com/?no=98").

The only downside for me at this time is that the mic volume is quite low and there is static noise, although not enough to make a Skype conversation unintelligible or uncomfortable.

Hope this helps those looking to fix sound issues on their Lenovos.
Any tips on getting rid of the mic static altogether greatly appreciated.

---

### Post by kaimadag on 2011-10-03
**BenQ P52 Realtek ALC2662**
AMD Turion64X2 TL-52
ATI Radeon Mobility X1600 (M56P)
Ubuntu 11.04 amd64

```
~$ tail -1 /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=benq-t31

~$ uname -a
Linux P52 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Benq Corporation Device 058f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

~$ head -1 /proc/asound/card0/codec#0
Codec: Realtek ALC262

~$ cat /proc/asound/modules 
 0 snd_hda_intel

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

By default sound worked fine except internal mic, external mic and headphones. With this setting everything works as expected, including automuting of internal speakers on connecting headphones.

---

### Post by www.rzr.online.fr on 2011-10-11
Is there a reported bug upstream ?
-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by AG* on 2011-10-16
Please please help.. I am on lenovo z560 and when I plug in my headphones, my speaker dont switch off...

---

### Post by AG* on 2011-10-16
Desperately want the solution to the same problem, model lenovo z560 ubuntu 10.04. Were you able to solve this problem?
> **jhuntington said:**
> the configuration file has been moved to /etc/modprobe.d/alsa-base.conf i had the same problem but theres configuration information in the .conf file.

did anyone ever find out how to get these drivers working?
Codec: Conexant ID 5069
Codec: Intel G45 DEVIBX
i still have issues with the mic input jack and the headphones not turning off the speakers

---

### Post by Lorthirk on 2011-10-18
```
options snd-hda-intel model=dell-m6-dmic
``` 
works for Dell Studio XPS 1645

---

### Post by www.rzr.online.fr on 2011-11-01
I noticed that mute on plug bug is reported on alsa tracker :



[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5466#](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5466#) mute


[http://rzr.online.fr/q/hda](http://rzr.online.fr/q/hda)

---

### Post by cHu-X on 2011-11-01
MSI CX420MX works using auto

---

### Post by AntonioL on 2011-11-18
Hi guys i have this problem i have a notebook Toshiba satellite A300-1RI whit Ubuntu 10.10 64 bit,
the my Ubuntu don't record audio, 
 
when i write this command 
#: cat /proc/asound/card0/codec*| grep Codec
Codec: Realtek ALC268
Codec: LSI ID 1040
when i write this command 
#: sudo nano /etc/modprobe.d/alsa-base.conf
i see:
# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; /sbin/modprobe --quiet snd-seq ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 && { /sbin/modprobe --quiet snd-emu10k1-synth ; : ; }

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

now i don't know what i do change because in this how-to 
[https://help.ubuntu.com/community/HdaIntelSoundHowto/](https://help.ubuntu.com/community/HdaIntelSoundHowto/) 
i read this:
options snd-hda-intel model=basic

but i don't have
please help me
best regads 
Antonio

---

### Post by jozeph78 on 2011-11-21
I have an HP dv6tqe. I cannot get all four speakers to work at the same time. I either use :

```
options snd-hda-intel model=ref enable_msi=1
```for the front two speakers or these get the rear:

```
options snd-hda-intel model=hp-dv6 enable_msi=1
```Here is the relevant output: 

Alsa-info.sh: [http://www.alsa-project.org/db/?f=78c4c6ec48f5c715bb4f2ef7588f1682aa6e2fed](http://www.alsa-project.org/db/?f=78c4c6ec48f5c715bb4f2ef7588f1682aa6e2fed)

```


jhirn@dv6inthemix:~ $ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD81B1X5
Codec: Intel CougarPoint HDMI
jhirn@dv6inthemix:~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jhirn@dv6inthemix:~ $ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
jhirn@dv6inthemix:~ $ cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc7500000 irq 53
jhirn@dv6inthemix:~ $ cat /proc/asound/modules
 0 snd_hda_intel

jhirn@dv6inthemix:~ $ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD81B1X5
Codec: Intel CougarPoint HDMI
jhirn@dv6inthemix:~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jhirn@dv6inthemix:~ $ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
jhirn@dv6inthemix:~ $ cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc7500000 irq 53
jhirn@dv6inthemix:~ $ cat /proc/asound/modules
 0 snd_hda_intel

jhirn@dv6inthemix:~ $ s cat /etc/modprobe.d/alsa-base.conf 
[sudo] password for jhirn: 
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
#options snd-hda-intel model=ref enable_msi=1
options snd-hda-intel model=hp-dv6 enable_msi=1


```

---

### Post by Wbbswonder on 2011-11-28
Advent 4211 (MSI Wind Clone Ubuntu 11.10 

Realtek ALC1200

options snd-hda-intel model=targa-dig

With this everything works, no sound hiss, speakers work and headphones and switches the speaker off when headphone connected. I will like everyone else file a bug. What a terrible regression in the Kernel. 

Thank you so much for this page. This was nearly a deal breaker for me. I listen to a lot of music!

---

### Post by Madkinder on 2011-12-02
Asus G60v

options snd-hda-intel model=asus-mode3

---

### Post by meco271 on 2012-01-04
no speaker sound one acer 1690 series (1694 WMLi), the rest works fine.
anyone can help? 
```
aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: ICH6 [Intel ICH6], dispositivo 0: Intel ICH [Intel ICH6]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH6 [Intel ICH6], dispositivo 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

alsamixer:

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.24.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;     Scheda: Intel ICH6                          F1:  Aiuto                   &#9474;
&#9474; Processore: Conexant Cx20468-31                 F2:  Informazioni di sistema &#9474;
&#9474;      Vista: Riproduzione                        F6:  Selezione scheda sonora &#9474;
&#9474;   Elemento: Master [Guadagno dB: 0,00, 0,00]    Esc: Esce                    &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                        &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                        &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;   100<>100 100<>100 100<>100 100<>100 100<>100   100                         &#9474;
&#9474;  < Master >Headphon   PCM      Line      CD      Mic    Mic Boos  S/PDIF     &#9474;

---

### Post by lidex on 2012-01-04
> **meco271 said:**
> no speaker sound one acer 1690 series (1694 WMLi), the rest works fine.
anyone can help? 

 &#9474;
 Go here for help:
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by meco271 on 2012-01-04
@lidex:
I did try all possible solutions.... but useless. sorry, I didn't find any help in the thread you mentioned.

---

### Post by hooluupog on 2012-01-18
Hi, 
I met the sound problem. In windows the sound is ok and loud , but in ubuntu the sound was so low that i can barely hear it even i set the sound volumn to max. I have always checked alsamixer (all the channels are in max volume).
At first, i thought it is a hardware compatible problem. but one day i suspend my ubuntu for dinner, and when i got back and resumed ubuntu, i found the sound become normal status just like in windows. after i reboot, the sound turn to very low again.
So these days, everytime i started my laptop, the first thing i do is sleep & resume to make the sound ok. this is driving me crazy, can anybody tell me how to fix it?:confused:
FYI,
```

Lenovo ZHAOYANG E46  
/etc/modprobe.d/alsa-base.conf :
options snd-hda-intel model=auto

$sudo head -1 /proc/asound/card0/codec#0
Codec: IDT 92HD81B1C5

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 $ lspci -v
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Lenovo Device 38af
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f0620000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Lenovo Device 391a
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at cdefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

 $ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 $ more /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0620000 irq 48
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcdefc000 irq 17

$ more /proc/asound/modules 
 0 snd_hda_intel
 1 snd_hda_intel

AlsaMixer v1.0.24.2

```
Thanks in advance

---

### Post by whitee700 on 2012-01-24
Alienware m15x manualy changed to "intel-alc889a" audio worked can not confirm mic

the guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
was hugely helpfull and iam grateful

---

### Post by NautilusUK on 2012-03-31
Hi Guys,

I found my solution for a Toshiba Satellite L750/L755 over on the Mint forums: [http://forums.linuxmint.com/viewtopic.php?f=49&t=98032](http://forums.linuxmint.com/viewtopic.php?f=49&t=98032)

A very big thanks to babysitteronacid

I used:

options snd-hda-intel model=ideapad
options snd-hda-intel enable_msi=1

A reload...... and SUCCESS! Sensing headphone jack!

---

### Post by limestrael on 2012-04-26
Hi!
Does someone have the settings for an Alienware M17x R3 under Precise Pangolin?
On Natty, just putting
options snd-hda-intel model=alienware
made the speakers work, but on Precise it doesn't...

---

### Post by abyss88 on 2012-04-28
Hello to all!
I've installed new Ubuntu 12.04 LTS and I got a surprise...
The soundcard is working, also the microphone... but the problem is that by default I hear the sound coming from internal speakers even when I plug in the headphones!!! And so I have the sound coming from headphones and from integrated speakers.

It is like the jack sensing is not working.

I've looked around for all suggestions but I can't get the jack sensing work.

As I said i have Ubuntu 12.04 LTS on Acer Aspire 6920G with:
```

aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC889 Analog [ALC889 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: ALC889 Digital [ALC889 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
and
```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.

```
and
```

cat /etc/modprobe.d/alsa-base.conf 
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

#only headphones
#options snd-hda-intel model=laptop

#options snd slots=snd-hda-intel
#alias snd-card-0 snd-hda-intel
#options snd-hda-intel model=laptop

options snd-hda-intel model=laptop

```
In /etc/modprobe.d/alsa-base.conf i tried options snd-hda-intel model=acer, auto, generic, acer-aspire, laptop. But nothing... Sometimes i get the sound only from headphones and not from integrated speakers (even when the jack is not plugged in...).

I hope there is someone that could help me!

Thank you

Artur

---

### Post by abyss88 on 2012-05-02
Hello to all!

Finally I make the soundcard working!!!
Now when I plug the jack I hear the sound only into the headphones and when I unplug them I hear the sound from internal speakers!!!

I did a kernel update. The last stable kernel version today is 3.3.4.
I downloaded the packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) choosing the v3.3.4-precise folder.

Here you can find the instructions of how to install kernels from .deb: [http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/](http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/)

Please, first un-install the proprietary drivers of videocard (if any).

So, audio... on my Acer 6920G is ok.

Please, feel free to ask any questions

---

### Post by HatarakiHalo on 2012-05-28
> **abyss88 said:**
> 
I did a kernel update. The last stable kernel version today is 3.3.4.

Thanks, abyss88. It helped me too (Asus G73jw).

---

### Post by liljoe2284 on 2012-06-01
Macbook 5,2 works with model=mb31

---

### Post by pandev92 on 2012-07-03
what option should I use? I have hp pavilion dv6 2120,  IDT 92HD75B3X5


My laptop doesn't automute mute with the default configuration

---

### Post by jmfal on 2012-07-04
bump

---

### Post by siguto on 2012-07-21
After I clean installed Ubuntu 12.04 64-bit I found my the internal speakers on my laptop worked but no sound was produced from anywhere when I plugged in my headphones. Apparently the sound was cut off in response to my headphones being plugged in, because I could usually hear a brief segment of sound from my headphones if I inserted the jack slowly or at an angle.

Laptop make: Gateway
Laptop model: M-6862
ALSA version: 1.0.24

I forget what I typed in the terminal to get this information:
SigmaTel STAC9205
Conexant ID 2c06

My solution was:
```
options snd-hda-intel model=eapd position_fix=1
```Which I found in [this thread which names SigmaTel STAC9205]("http://ubuntuforums.org/showthread.php?t=1219505").
 I also saw [this post that provides a slightly different solution]("http://www.linuxforums.org/forum/coffee-lounge/154383-take-sigmatel-stac9205.html").

The first time I tried the working solution I thought it didn't worked entirely because I was using VLC player, which is producing some sort of crackling noise for me. Rhythmbox played clean, though.

---

### Post by elporsche907 on 2012-08-09
Hi Everybody, I had the same issue on my Laptop after installing ubuntu 12.04 which has the following characteristics:
Model: Pavilion dv6-1276la
So I done the following procedure:

First check the codecs I had:

porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: ATI RS690/780 HDMI
porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ 
porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ cat /proc/asound/card1/codec* | grep Codec
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040
porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ 

Then verify the hardware audio settings I had:

porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ lspci
***
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
***
porsche@porsche-HP-Pavilion-dv6-Notebook-PC:~$ 

The next step was to consult the corresponding controller needed in the following link:
[http://lxr.linux.no/#linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt](http://lxr.linux.no/#linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt)

from the website I corroborate the controller which matches my system hw:
 ***hp-dv5***

Following the procedure, I logged as a root and positioned myself in the following path:

root@porsche-HP-Pavilion-dv6-Notebook-PC:/etc/modprobe.d# ls -la
total 60
drwxr-xr-x   2 root root  4096 Jul 11 23:28 .
drwxr-xr-x 136 root root 12288 Jul 11 23:30 ..
-rw-r--r--   1 root root  2538 Jul 11 23:28 alsa-base.conf
-rw-r--r--   1 root root   325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root   108 May 23 08:35 blacklist-cups-usblp.conf
-rw-r--r--   1 root root   210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root   661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Feb 15 21:03 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Jul  4 08:42 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root   127 Apr 22 02:31 dkms.conf
lrwxrwxrwx   1 root root    48 Jul  9 09:45 fglrx.conf -> /etc/alternatives/x86_64-linux-gnu_fglrx_modconf
-rw-r--r--   1 root root    30 May 18 03:03 vmwgfx-fbdev.conf
root@porsche-HP-Pavilion-dv6-Notebook-PC:/etc/modprobe.d# 

Then I modified the file named *"alsa-base.conf*" showed in the list placed above and wrote the following lines:

***options snd-hda-intel model=hp-dv5***

After saving the changes I restarted my system and everything was ok, 

I hope this documentation would be interesting and valuable for you!
regards!

---

### Post by kaimadag on 2012-10-21
BenQ P52 Realtek ALC2662
AMD Turion64X2 TL-52
ATI Radeon Mobility X1600 (M56P)
Ubuntu 12.04 amd64

```
~$ tail -1 /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=auto
```
Although "auto" is default it didn't work fully without setting it explicitly (no sound on headphones, no internal/external mic switching). 

When set explicitly:

[LIST][*]"speakers" output is enabled and gets replaced by "headphones" output on plugging it in
[*]speakers are muted on headphones plugging it in
[*]only "internal mic" input is active
[*]"internal mic" is replaced by "front mic" on plugging it in
[*]"line in" is activated on plugging it in[/LIST]

System specs:
```
~$ uname -a
Linux P52 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Benq Corporation Device 058f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

~$ head -1 /proc/asound/card0/codec#0
Codec: Realtek ALC262

~$ cat /proc/asound/modules 
 0 snd_hda_intel

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 0: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by lordamit on 2013-01-04
Lordy Reporting:

HP pavilion DV4 - 5110TX Beats Audio system

```
options snd-hda-intel model=ref
```

Worked for me

Here are some more details:

**output of grep "Codec:" /proc/asound/card*/codec***

```
/proc/asound/card0/codec#0:Codec: IDT 92HD91BXX
/proc/asound/card0/codec#3:Codec: Intel PantherPoint HDMI
```

**output of alsa-info.sh**

[http://www.alsa-project.org/db/?f=54e5fcf489c2276becc47b12b5dc09d952f5ec90](http://www.alsa-project.org/db/?f=54e5fcf489c2276becc47b12b5dc09d952f5ec90)

**Device Specifications**
2 x Beats Audio Internal speakers; Beats Audio Audio playback; HP Triple Bass Reflex Subwoofer

Problem in solution: Subwoofer does not turn off automatically after headphone is plugged in. Can be manually controlled using PCM value in alsamixer.

---

### Post by Yellow Pasque on 2013-01-04
@lordamit: I'd highly recommend reporting it as a bug on launchpad, since upstream ALSA will be interested in patching it (and fixing the subwoofer auto-mute).

---

### Post by gbdlin on 2013-01-16
options snd-hda-intel model=hp-dv5 works great for hp dv6-2110sw!

---

### Post by paranoidandroid845 on 2013-09-28
Hi,  I m using a Dell Inspiron 3520 and I can't find the name of the model for my alsa-base.conf...  The audio device is:  Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)  Please help!  Thank you very much

---

### Post by Yellow Pasque on 2013-09-29
^There are no specific models for Cirrus Logic CS4213 codec (which the Inspiron 3520 uses). What is wrong with it?

---

### Post by paranoidandroid845 on 2013-09-29
Headphones and speakers works at the same time, no headphones control in alsamixer thus no way to auto-mute speakers when headphones are plugged in... This is very annoying... Thanks for your help.

---

### Post by Yellow Pasque on 2013-09-29
> **paranoidandroid845 said:**
> Headphones and speakers works at the same time.

Try latest driver module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If it's not working after reboot, file a bug.

---

### Post by paranoidandroid845 on 2013-09-29
I already have DKMS... kernel, modules and alsamixer upgraded.   I also must precise that Im not running Ubuntu but Debian, i posted here because this is the only forum dealing with the asla-base.conf specifications related to the hardware. No solutions for my problems on debian forums, and I think perhaps the only way is to find the right name that fit in "options snd-hda-intel model=".

---

### Post by Yellow Pasque on 2013-09-29
^Post the info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
The only possible model I see in the code is cdb4210 ("stumpy" is for chromebooks): [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_cirrus.c#L698](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_cirrus.c#L698)

---

### Post by paranoidandroid845 on 2013-09-29
Ihe name cdb4210  doesn't work..  So I posted the info here: [http://www.alsa-project.org/db/?f=b55b50aa79a84b881e90693e1a3babdacfd3805a](http://www.alsa-project.org/db/?f=b55b50aa79a84b881e90693e1a3babdacfd3805a)

---

### Post by Yellow Pasque on 2013-09-29
```
Kernel release:    3.2.0-4-686-pae
Driver version:     1.0.24
```

You're still running a relatively old kernel/driver. If you don't want to mess with your install, get a LiveUSB ( [http://releases.ubuntu.com/13.10/](http://releases.ubuntu.com/13.10/) ) and test if the problem still occurs there. If so, file a bug using the LiveUSB.

---

### Post by paranoidandroid845 on 2013-09-30
Hello,

I just compiled a new kernel (3.11) and you are right ! The problem is solved. Thank you.

---

### Post by jzsmart3 on 2013-12-11
For Toshiba Satellite C655D and Linux Mint 16, setting model=laptop fixed the problem of no audio (i.e., no speaker, no headphone; mic ok). Previous attempt of model=toshiba (as well as asus and ideapad) did NOT work.

Prior version of Linux Mint worked fine, so Mint 16 default install picks up a regression in the alsa driver WRT this particular Satellite laptop. :mad:  But happy ending with above change. :P

In passing, I note that audio is:  Conexant CX20585

---

### Post by Andres_E._Parilli on 2014-03-03
I have try alot of things but i can still got audio with ALC662


> **Eric06 said:**
> Addition to your database (i am so glad sound works :p )

Ubuntu 8.10
Packard bell laptop Easynote RS65-M023FR pn=PC28E01502
windows = sound ok; ubuntu no sound +

config:

cat /proc/asound/cards
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfdcf8000 irq 22
1 [HDMI ]: HDA-Intel - HDA ATI HDMI
HDA ATI HDMI at 0xfddec000 irq 17

cat /proc/asound/modules
0 snd_hda_intel
1 snd_hda_intel

aplay -l
**** Liste des PLAYBACK périphériques ****
carte 0: Intel [HDA Intel], périphérique 0 : ALC663 Analog [ALC663 Analog]
Sous-périphériques: 0/1
Sous-périphérique: #0: subdevice #0
carte 1: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI]
Sous-périphériques: 1/1
Sous-périphérique: #0: subdevice #0

Upgraded to ALSA 1.0.19 without problem using the script from the forum

I added the following line at the end of /etc/modbase.d/alsa-base file:
options snd-hda-intel model=m51va

there are mutiple values that get the speakers to work but not the headset... so i tryed all the ones corresponding to my hardware device to test them (lots of 'sudo alsa force-reload' and 'alsamixer' commands during the test)

summary of the behaviors i see on my machine: 

#ALC662/663:HP/mic/headset/ touchpad
#3stack-dig: ok/no/no
#3stack-6ch: ok/ no/no
#3stack-6ch-dig: ok/no/ no
#6stack-dig: ok / no / no
#lenovo-101e: ok / lo / no/ no
#eeepc-p701: bad sound
#eeepc-ep20: ok / no / no / no
#m51va: ok / lo / ok / part
#g71v: ok / no / ok / part
#h13 : ok / low/ ok / part
#g50v: ok / no / no / part
# auto: no sound

I did not get good results on MIC and I did not test the HDMI ouput too

Thanks to you forum gurus ):P

---

### Post by Yellow Pasque on 2014-03-03
> **Andres_E._Parilli said:**
> I have try alot of things but i can still got audio with ALC662

Please start your own thread and give [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

