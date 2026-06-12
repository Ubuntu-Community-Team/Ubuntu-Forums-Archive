---
title: "Chipset?"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by MeguhNad on 2012-01-24
Hi,

I have this USB Wireless Adapter: [http://www.shop.bt.com/products/belkin-surf-wireless-n150-usb-adapter-6P5T.html#specifications](http://www.shop.bt.com/products/belkin-surf-wireless-n150-usb-adapter-6P5T.html#specifications)

I installed Ubuntu 10.04 LTS a while back, and my internet connection wouldn't work. After this, I installed Ubuntu 11.10 and it worked straight away requiring no setup.

Now I want to use Ubuntu 10.10 (as I hate Unity)

Will my wireless work?

Also, how can I identify the "chipset" of my Wireless USB Adapter?

And if it won't work "out of the box", how can I make it work with no access to a router via Ethernet? Can only do wireless.

---

### Post by Kyslosh on 2012-01-24
Try reading this ;)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by MeguhNad on 2012-01-24
Thanks for your reply!

However, in my original question, I did ask how I can identity what chip set my wireless adapter has? Until then, I can't know.

---

### Post by Kyslosh on 2012-01-24
ok post here (I assume the USB device is plugged in) 
your
```

lsmod

```

and 
```

lsusb

```

---

### Post by MeguhNad on 2012-01-24
lsmod:

Module                  Size  Used by
binfmt_misc             6599  1 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8735  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
psmouse                59033  0 
serio_raw               4022  0 
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
ahci                   19013  0 
e1000                  97525  0 
hid                    67742  1 usbhid
libahci                21667  3 ahci


lsusb:

Bus 001 Device 002: ID 80ee:0021  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

