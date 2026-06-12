---
title: "HOWTO : Compile PodXT Live / Line6 USB driver under Gutsy"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by fourmiii on 2007-12-14
Hello world !!

I just bought myself a nice birthday present : a brand new Line6 PodXT Live  !!

To my big surprise, detecting it as a USB audio device doesn't work OOTB like my m-audio mobile pre did.. so I quickly figured out I had to use the line6usb driver found here :
[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)

Surprise again : the driver doesn't compile OOTB on Gutsy .. there are some implicit declarations in pcm.c :

implicit declaration of function " snd_pcm_group_for_each "

So I google around, finding no solution at all for this particular problem.. so I rolled up my sleeves and dug in the code in pcm.c .. after some fiddling around I successfully compiled, installed and loaded the line6usb module !!!

I attached a patch that works on my system with kernel 2.6.22-14-rt

So in order to make this driver work under gutsy, assuming you downloaded the driver at [http://www.tanzband-scream.at/line6/download/line6usb-0.7.2.tar.bz2](http://www.tanzband-scream.at/line6/download/line6usb-0.7.2.tar.bz2) and the attached line6usb.patch.txt :
```

sudo apt-get install build-essential linux-headers-$(uname -r)
tar jxvf line6usb-0.7.2.tar.bz2
cd line6usb-0.7.2
patch -p1 < ../line6usb.patch.txt
make
sudo make install
sudo modprobe line6usb

```

Have fun and spread the word for this patch !!!

Fourmiii

---

### Post by fourmiii on 2007-12-14
Forgot to mention it works perfectly with JACK too !!!

This works flawlessly on my realtime setup :

Frames / Period : 256
Sample Rate : 48000
Periods / Buffer : 3

Latency : 16 msec

---

### Post by Hito_kun on 2007-12-18
Could you tell me wich other interfaces works with this driver?

Does Pod 3.0 or toneport works?

I was looking so many options because of the lack of support of line-6 products, but if this works, oh my ... :)

---

### Post by traitor on 2007-12-22
I worship the ground you walk on. Thanks for that.

---

### Post by kipi on 2007-12-27
I'm having issues getting JACK to work with my POD as a capture device and my soundcard as a playback device: It works fine if I have capture and playback through the POD but my PC freezes when I have my POD for capture and my SBLive for playback. Anyone got any ideas? Is JACK designed for this kind of multi-device configuration? (PS. Thanks for your line6usb patch fourmii, it works great!)

---

### Post by kukat on 2007-12-28
helo!!! 

First, sorry for my english, i'm from Valencian (Catalan Loco Team) 
I have a Tone Port UX1, and I installed the Usb with the Patch. 

In the Jack I see two ports ( Guitar and Vocals?). 

What I do for running my Tone Port ? It's on and in the Jack i see two ports.....

How do running the Line 6 ? 

Sorry again for my English....:)

---

### Post by RSVampire on 2007-12-31
anybody want to post a .deb for me? I don't want to go through the trouble of compiling it....

---

### Post by Chaoswork on 2008-01-03
I still have a problem installing the driver. when i print a code you provided regarding a patch, it answers: bash: ../line6usb.patch.txt: No such file or directory.:(

---

### Post by cheaptrick on 2008-01-07
does it work on toneport gx?

---

### Post by ShadowZ on 2008-01-15
First of all, thank you for giving me hope with your patch, however i keep getting this error when i try to "sudo make install"

> FATAL: Error inserting line6usb (/lib/modules/2.6.22-14-generic/kernel/sound/usb/line6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1


When i check dmesg, the following appears:

> [15625.712000] line6usb: Unknown symbol snd_rawmidi_receive
[15625.712000] line6usb: disagrees about version of symbol snd_ctl_add
[15625.712000] line6usb: Unknown symbol snd_ctl_add
[15625.712000] line6usb: disagrees about version of symbol snd_pcm_new
[15625.712000] line6usb: Unknown symbol snd_pcm_new
[15625.712000] line6usb: disagrees about version of symbol snd_card_register
[15625.712000] line6usb: Unknown symbol snd_card_register
[15625.712000] line6usb: disagrees about version of symbol snd_card_free
[15625.712000] line6usb: Unknown symbol snd_card_free
[15625.712000] line6usb: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[15625.712000] line6usb: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[15625.712000] line6usb: disagrees about version of symbol snd_ctl_new1
[15625.712000] line6usb: Unknown symbol snd_ctl_new1
[15625.712000] line6usb: Unknown symbol snd_rawmidi_transmit_ack
[15625.712000] line6usb: disagrees about version of symbol snd_card_new
[15625.712000] line6usb: Unknown symbol snd_card_new
[15625.712000] line6usb: disagrees about version of symbol snd_pcm_lib_malloc_pages
[15625.712000] line6usb: Unknown symbol snd_pcm_lib_malloc_pages
[15625.712000] line6usb: disagrees about version of symbol snd_pcm_lib_ioctl
[15625.712000] line6usb: Unknown symbol snd_pcm_lib_ioctl
[15625.712000] line6usb: disagrees about version of symbol snd_pcm_lib_free_pages
[15625.712000] line6usb: Unknown symbol snd_pcm_lib_free_pages
[15625.712000] line6usb: Unknown symbol snd_rawmidi_transmit_peek
[15625.716000] line6usb: disagrees about version of symbol snd_pcm_set_ops
[15625.716000] line6usb: Unknown symbol snd_pcm_set_ops
[15625.716000] line6usb: disagrees about version of symbol snd_device_new
[15625.716000] line6usb: Unknown symbol snd_device_new
[15625.716000] line6usb: Unknown symbol snd_rawmidi_new
[15625.716000] line6usb: disagrees about version of symbol snd_card_disconnect
[15625.716000] line6usb: Unknown symbol snd_card_disconnect
[15625.716000] line6usb: Unknown symbol snd_rawmidi_set_ops
[15625.716000] line6usb: disagrees about version of symbol snd_pcm_period_elapsed
[15625.716000] line6usb: Unknown symbol snd_pcm_period_elapsed



I'm not sure if this dmesg log can be of any help, i really hope someone can guide me through the necessary steps to install this or else i will have to use windows (NOOOOO!!!) whenever i want to use the podxt :guitar::lolflag:

---

### Post by sacky on 2008-02-06
I got the driver running but I can't get it to capture at anything other than 39.1KHz.

The docs mentioned some way of loading it as a PLUGHW: device, but every time I try this, it won't load.

As far as playing back sound, it converts to 44.1 or 48 on the fly for mp3, wav or videos.  But when I go to record anything, it defaults to 39.1 and I can't force it to 44.1.

Anyone have any ideas for getting this to capture through the USB port at a "proper" sample rate?

sj

---

### Post by vapor0 on 2008-02-25
Hi,

I'm running Hardy development release 4. I get the same error as the second-last person above:

FATAL: Error inserting line6usb (/lib/modules/2.6.24-8-rt/kernel/sound/usb/line6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And here's dmesg:

[  548.788896] line6usb: Unknown symbol snd_pcm_period_elapsed
[  787.741650] line6usb: disagrees about version of symbol snd_pcm_new
[  787.741666] line6usb: Unknown symbol snd_pcm_new
[  787.741990] line6usb: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  787.741997] line6usb: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  787.743484] line6usb: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  787.743491] line6usb: Unknown symbol snd_pcm_lib_malloc_pages
[  787.743592] line6usb: disagrees about version of symbol snd_pcm_lib_ioctl
[  787.743598] line6usb: Unknown symbol snd_pcm_lib_ioctl
[  787.743702] line6usb: disagrees about version of symbol snd_pcm_lib_free_pages
[  787.743708] line6usb: Unknown symbol snd_pcm_lib_free_pages
[  787.744133] line6usb: disagrees about version of symbol snd_pcm_set_ops
[  787.744138] line6usb: Unknown symbol snd_pcm_set_ops
[  787.745135] line6usb: disagrees about version of symbol snd_pcm_period_elapsed
[  787.745140] line6usb: Unknown symbol snd_pcm_period_elapsed

Is there a way I can get this working?

Any help appreciated.
:guitar:

---

### Post by robig on 2008-03-17
ive the same problem like vapor0 :(

im thinking about giving the toneport back to the music store ive buyed it...
i thought that linux should have no problem with such a widely known sound manufactur.

robig

---

### Post by Arrrgh4life on 2008-05-28
I encountered a massive error doing this in Hardy Heron.  At first everything worked alright, until I tried to restart, then the system froze up, and after I finally got it reset I got a "Failure to Initialize Hal!" error on login.  The networking wouldn't work, opening the volume controls would cause the computer to freeze, and you couldn't reset.  I found that the error went away if I restarted without the PodXT plugged in.  So, I don't know, maybe I messed up something while installing the drivers, maybe if I can uninstall them and try again I can get it to work.

---

