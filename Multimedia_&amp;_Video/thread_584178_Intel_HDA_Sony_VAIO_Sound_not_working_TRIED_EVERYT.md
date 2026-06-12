---
title: "Intel HDA Sony VAIO Sound not working TRIED EVERYTHING"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by RachitGupta on 2007-10-20
Hi Guys

I have a Sony VAIO Computer with a HDA Intel Sound Card and I just can't get the sound to work

I've tried the huge comprehesnive guide, downloading the ALSA drivers, utils, etc. and reinstalling them

None of this is working...

---

### Post by prshah on 2007-10-23
Hi, post the output of :

lsmod | grep snd

to give us a clue...
Cheers,
PRS
PS: Sony Vaio which model?

---

### Post by RachitGupta on 2007-10-23
Hey dude, thanks so much for the reply
I really appreciate your help!

I have a Sony VAIO VGC-RC110G

the output to "lsmod | grep snd":

```
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
```



BY THE WAY i am more tha nhappy to give you remote administrative access to my computer so you can see for yourself what's going on if you'd like

---

### Post by wrat on 2007-10-23
if you have this chip SigmaTel STAC9271D,
which you can find out like so 
grep Codec /proc/asound/card0/codec#*
 
this is what worked for me
 mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.save
 sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.save
sudo /etc/init.d/alsa-utils start
 I found this after much searching and it worked for me

---

### Post by RachitGupta on 2007-10-23
Hi

I tried Ubuntu about a year ago on the exact same computer, and it used to say i have 
SigmaTel STAC9271D!!!!!!

This was on [http://ubuntusoftware.info/ultimate/](http://ubuntusoftware.info/ultimate/) Ubuntu Ultimate Feisty Fawn i believe

Right now on most current Ubuntu, grep Codec /proc/asound/card0/codec#* says:

```


/proc/asound/card0/codec#0:Codec: SigmaTel CXD9872RD/K
/proc/asound/card0/codec#1:Codec: Conexant ID 2bfa

```


doing "mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.save" results in:

```
mv: cannot stat `/var/lib/alsa/asound.state': No such file or directory
```


my /var/lib/alsa folder is empty, this is after clean install

---

### Post by wrat on 2007-10-24
Well that is odd considering... but the slight difference could be Im using kubuntu 7.10..if it used to say you had the stac chip but now it says otherwise that is odd
BUT then again who knows the sound worked without glitches for me from  the live cd (which I tried before install) then when installed it did NOT work until I found the solution which I posted..if your desperate for sound you could try some amped usb speakers..sorry

---

### Post by RachitGupta on 2007-10-24
Yeah, it is odd...

I can't buy usb speakers..

How can i get this sound card to work??

---

### Post by iamwonton on 2007-10-27
hi.. similiar problem with a Vaio PCG-TR1AP no sound in Gutsy Gibbpn. tried the above help, but nothing worked.... here's my info:

snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

any help would be great.. thanks

---

### Post by bekirserifoglu on 2007-10-28
i had the same problem tried everything and found a solution. you need to upgrade to alsa 1.0.15.
you should edit alsa-base with 
```
sudo gedit /etc/modprobe.d/alsa-base
```
add the line
```
options snd-hda-intel model=MODEL
```

below  is the model table for sigmatel audio. i have STAC9872. so 

```
options snd-hda-intel model=vaio
``` worked for me it should also work for you. i am waiting for your reply.

STAC9200/9205/9254
	  ref		Reference board

	STAC9220/9221
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF
	  intel-mac-v1	Intel Mac Type 1
	  intel-mac-v2	Intel Mac Type 2
	  intel-mac-v3	Intel Mac Type 3
	  intel-mac-v4	Intel Mac Type 4
	  intel-mac-v5	Intel Mac Type 5
	  macmini	Intel Mac Mini (equivalent with type 3)
	  macbook	Intel Mac Book (eq. type 5)
	  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
	  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
	  imac-intel	Intel iMac (eq. type 2)
	  imac-intel-20	Intel iMac (newer version) (eq. type 3)

	STAC9202/9250/9251
	  ref		Reference board, base config
	  m2-2		Some Gateway MX series laptops
	  m6		Some Gateway NX series laptops
	  pa6		Gateway NX860 series

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

---

### Post by RachitGupta on 2007-10-28
Hi bekirserifoglu

Do i do that on Ubuntu Ultimate Edition (where my sound card is detected as STAC something) or on the newest Ubuntu 7(where its detected as SigmaTel CXD9872 RD/K)?

---

### Post by bekirserifoglu on 2007-10-28
i think you should do it on Ubuntu Ultimate Edition.

---

### Post by iamwonton on 2007-10-28
[QUOTE=bekirserifoglu;3651516]i had the same problem tried everything and found a solution. you need to upgrade to alsa 1.0.15.
you should edit alsa-base with 
```
sudo gedit /etc/modprobe.d/alsa-base
```
add the line
```
options snd-hda-intel model=MODEL
```

below  is the model table for sigmatel audio. i have STAC9872. so 

```
options snd-hda-intel model=vaio
``` worked for me it should also work for you. i am waiting for your reply.

____

I downloaded and updated ALSA ( i think i did it properly ) but I'm not sure what my Model number is to put in alsa-base... which method do I use to find it?

iamwonton

---

### Post by bekirserifoglu on 2007-10-28
use 
```
cat /proc/asound/card0/codec#* | grep Codec
```
to see your soundcard model.

---

### Post by RachitGupta on 2007-11-22
I tried, none of these work guys :(

---

### Post by MirKO13 on 2008-01-19
I have the same PC & the same problem :'(
.......**RachitGupta** did you fix the problem? if so,tell me how PLEASE!!:confused:
if not,did you try another Linux distribution?

Thanks   :-\"

---

### Post by MirKO13 on 2008-01-21
....sorry for the double post....... :P

  It seems that Sony pcs have many problems with Linux :(

The same PC with the  same problem   

[Link]("http://www.linuxforums.org/forum/linux-newbie/54194-new-sony-desktop-linux-safe-even-capable.html")

:(

 Can someone suggest another LinuxDistribution, that may work in my pc? not to hard to use...please

Thanks guys :)

---

### Post by rcc2008 on 2008-02-13
After trying everything without result I plugged in the earphone and then plugg it out and sound came out.

---

