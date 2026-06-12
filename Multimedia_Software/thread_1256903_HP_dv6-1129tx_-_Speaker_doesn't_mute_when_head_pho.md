---
title: "HP dv6-1129tx - Speaker doesn't mute when head phone is plugged"
date: 2009-09-03
forum: Multimedia Software
---

### Post by kallunga on 2009-09-03
Hi guys, does anyone have **hp dv6-1129tx**?
Finally the sound worked but still with some issues. 
To acheve this I had to I use "options snd_hda_intel model=hp-dv5" in /etc/modprobe.d/alsa-base.conf - but my note is DV6!
 
_Now the problem is:  it doesn't mute speakers when I plug a headphone. _

If I want to mute my speakers I am doing it manually using Alsamixer.

My Codec:
```

leonardo@leolinux:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040


``````

leonardo@leolinux:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xda100000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xda010000 irq 17


```For "options snd_hda_intel model=xxx" I have tried everything possible and no luck.

If anyone has HP and had the same experience please tell me about it.

Thanks

Leonardo

---

### Post by chloraldo on 2009-09-23
> **kallunga said:**
> Now the problem is:  it doesn't mute speakers when I plug a headphone.

Same problem here with a DV6-1240ez.

It would be great to get a solution for this!

---

### Post by boblong on 2009-11-12
Come on guys, I would really appreciate a response.

---

### Post by Keronn on 2009-11-12
Hi,

In Karmic, installing *linux-backports-modules-alsa-karmic-generic* fixed the problem with an HP dv6-2012sf. You should try...

BTW, I use "options snd_hda_intel model=hp-dv5".

---

### Post by Neezer on 2009-11-13
How does a person install that, and can I just change karmic to jaunty if I am running 9.04?

---

### Post by Keronn on 2009-11-13
> **Neezer said:**
> How does a person install that, and can I just change karmic to jaunty if I am running 9.04?

No you have to be running 9.10 for this fix, sorry.

---

### Post by pyrys on 2010-01-02
I received my hp dv6-2030sa with windows 7. I did a clean ubuntu karmic install (runs lightening fast). Sound didn't work and scouring around the forums, ran the script to upgrade ALSA drivers which got the sound working. After installing the backports modules main speakers mute when headphones are plugged in!!! Awesome

---

### Post by mbelos on 2010-01-12
> **pyrys said:**
> I received my hp dv6-2030sa with windows 7. I did a clean ubuntu karmic install (runs lightening fast). Sound didn't work and scouring around the forums, ran the script to upgrade ALSA drivers which got the sound working. After installing the backports modules main speakers mute when headphones are plugged in!!! Awesome
Hey pyrys, can you post more info? I just ran the ALSA upgrade script... What did you do next?

I have full sound working, but no muting when the headphones are plugged in (HP DV6T-2000).

---

### Post by hopugop on 2010-03-19
It works!! I have a DV6-1245dx.

I installed *linux-backports-modules-alsa-karmic-generic* and added the following to my */etc/modprobe.d/alsa-base.conf*:

```
options snd_hda_intel model=hp-dv5
```

Rebooted but sound was still coming out the speakers when headphone jack was plugged in. So I changed for the following:

```
options snd_hda_intel model=hp-dv6
```

After reboot speakers were muted when headphone jack was plugged in. Jackpot!

You should try it! :D

---

### Post by euriconeto on 2010-03-20
Hi Everyone,

I installed karmic in a HP dv62120tx, fixes the sound bug, but can't fix this problem posted here.

Could you, please, post here an easy to follow instruction? I'm a complete beginner and don't understand the process.

Cheers!

---

### Post by pablogrb on 2010-05-24
The issue is still present on a fresh install of Lucid

---

### Post by pablogrb on 2010-05-24
Instructions to fix on Lucid:

Install *linux-backports-modules-alsa-lucid-generic* via synaptic

Copy your original *alsa-base.conf*
```
sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.old
```

Add the following line to */etc/modprobe.d/alsa-base.conf* with your editor of choice
```
options snd_hda_intel model=hp-dv5
```

---

### Post by dr_rimzi on 2010-06-15
I have this problem too, but my system differs:

Running Lucid Lynx, Kubuntu
My laptop is HP dv6018ea, with nvidia audio (I think).
Here is the "modprobe -l | grep audio" output
```
kernel/drivers/media/video/tvaudio.ko
kernel/drivers/usb/gadget/g_audio.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko

```

Could anyone help me on this problem? :confused:

---

### Post by bobpress on 2010-07-16
I had this problem with the HP dv6-1240

I opened up a terminal ;
typed;
Code:

> sudo gedit /etc/modprobe.d/alsa-base.confand copy and pasted the following in it at the bottom of the file; 

> options snd-hda-intel model=auto enable_msi=1and put # in front of the current options line which for me was;

> # options snd-hda-intel model=dell-m4-3 enable_msi=1saved the file and rebooted.

Using the Volume Control icon, I chose "Preferences" and selected "Analog Output" in *Output*, *Sound Preferences* to select headphones.  Just switch back to "Analog Speakers" to go back to speakers.

If this does not work for you, simply reverse the changes in the /etc/modprobe.d/alsa-base.conf file and reboot again.  :P

---

### Post by lidex on 2010-07-17
For a Dv6 running lucid, I would first try stock, with no alsa-base.conf options. It should work - my Dv7, which had no audio in jaunty, now works perfectly in lucid out-of-the-box. If you still have issues the generic option line for these models is:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

---

### Post by bobpress on 2010-07-17
> **lidex said:**
> For a Dv6 running lucid, I would first try stock, with no alsa-base.conf options. It should work - my Dv7, which had no audio in jaunty, now works perfectly in lucid out-of-the-box. If you still have issues the generic option line for these models is:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

That was the first option line I tried and it didn't work for me.

---

### Post by lidex on 2010-07-17
> **bobpress said:**
> That was the first option line I tried and it didn't work for me.

Gotcha. I had to upgrade alsa and add the option to get sound. 
So lucid still needs tweaking for you?

---

### Post by bobpress on 2010-07-18
> **lidex said:**
> Gotcha. I had to upgrade alsa and add the option to get sound. 
So lucid still needs tweaking for you?

Yes, on this laptop HP Pavilion it did.  Only the change for the headphones.  It also uses Propriety drivers for the wireless so needed to have a wired connection to get that downloaded.

I've installed on Dell and Toshiba labtops also without needing tweaks.

---

### Post by lidex on 2010-07-18
> **bobpress said:**
> Yes, on this laptop HP Pavilion it did.  Only the change for the headphones.  It also uses Propriety drivers for the wireless so needed to have a wired connection to get that downloaded.

I've installed on Dell and Toshiba labtops also without needing tweaks.

I guess the Dv6 is just different enough. Even Aldeby's site shows a tweak for lucid:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio")

Out of curiosity, what version of alsa do you have:
```
cat /proc/asound/version
```

---

### Post by bobpress on 2010-07-18
> **lidex said:**
> I guess the Dv6 is just different enough. Even Aldeby's site shows a tweak for lucid:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

Out of curiosity, what version of alsa do you have:
```
cat /proc/asound/version
```

I upgraded to:
Advanced Linux Sound Architecture Driver Version 1.0.21

---

### Post by lidex on 2010-07-18
Hmm, just checked my new lucid install on the Dv7 and alsa is version 1.0.21
If you did an upgrade I would expect 1.0.23

---

### Post by bobpress on 2010-07-18
> **lidex said:**
> Hmm, just checked my new lucid install on the Dv7 and alsa is version 1.0.21
If you did an upgrade I would expect 1.0.23

I upgraded awhile back.  I'll do the additional upgrade.

---

### Post by bobpress on 2010-07-18
I have updated and used the dv5 line.  Working good.  Thanks.
> Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul 17 2010 for kernel 2.6.32-24-generic (SMP).


---

### Post by prarobo on 2011-09-04
Hey,

I have ubuntu 11.04, Hp-dvt6 laptop.

The speakers don't get muted when I plug the head phones. The sound output comes through both speakers and head phones.

I have dual audio output. ( i.e. 2 audio output jacks)

I have tried entering these lines in
/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=auto enable_msi=1
options snd-hda-intel model=hp-dv6
options snd-hda-intel model=hp-dv5
```

but nothing worked.
Kindly help me.

---

### Post by lidex on 2011-09-18
> **prarobo said:**
> Hey,

I have ubuntu 11.04, Hp-dvt6 laptop.

The speakers don't get muted when I plug the head phones. The sound output comes through both speakers and head phones.

I have dual audio output. ( i.e. 2 audio output jacks)

I have tried entering these lines in
/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=auto enable_msi=1
options snd-hda-intel model=hp-dv6
options snd-hda-intel model=hp-dv5
```

but nothing worked.
Kindly help me.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by prarobo on 2011-10-19
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

The alsa link is:-

[http://www.alsa-project.org/db/?f=355390716e8df5c70aea865ab365dabbe8818b41](http://www.alsa-project.org/db/?f=355390716e8df5c70aea865ab365dabbe8818b41)

For the time being I come up with a work around. I configured keyboard shortcuts to adjust the speaker and headphones volumes individually. I have recently upgraded to 11.10 . The problem still persists.

Thanks.

---

### Post by Mikenunes on 2012-05-17
same problem with HP dv7-3170 with Codec: IDT 92HD75B3X5
Solved with following line
options snd-hda-intel model=hp-dv5 enable_msi=1

---

### Post by prarobo on 2012-08-28
This issue seems to be fixed in Ubuntu 12.04

:guitar:

---

