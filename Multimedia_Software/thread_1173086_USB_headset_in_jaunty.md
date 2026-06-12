---
title: "USB headset in jaunty"
date: 2009-05-29
forum: Multimedia Software
---

### Post by kasper.s on 2009-05-29
Hello

My Logitech USB headset is not working anymore at jaunty x64. 

------------------------Seems that usb audio modules are missing.
 ~$ lsmod | grep usb
dvb_usb_af9015         33092  0 
dvb_usb                27148  1 dvb_usb_af9015
dvb_core              106924  1 dvb_usb
usbhid                 47040  0 

---------------------------USB device is found
~$ lsusb
Bus 001 Device 002: ID 15a4:9016  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:0a0b Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---------------------------No USB sound card found
~$ asoundconf list
Names of available sound cards:
NVidia

Please help me!  Im so desperate:o

- Greetings Kasper.s

---

### Post by ashcarr on 2009-06-01
I'm having the exact same issue, lsusb is recognising it, yet the card isn't shown in cat...
When I boot up (with it plugged in) I get the odd pop during bootup, though this is probably just the power fluctuating?
Obviously since it isn't recognised as a sound card, nothing shows up in sound preferences nor alsamixer.

I hope this gets resolved!

---

### Post by xx58 on 2009-06-01
):PI had same problem and another problems in Jaunty. I was not able to resolve that problem and then I just install again Ubuntu 8.10 and now everything just work nicely. Jaunty have too many other problems, so better wait and try again on September. I hope then everything is just fixed.

---

### Post by kasper.s on 2009-06-02
This worked for me. I used alsa upgrade script 

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
[]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")
with option

   -r     Restore ALSA 
          Kernel and all ALSA relevant Ubuntu packages will be restored
          (done by re-installation of relevant packages)

Now 

$ lsmod | grep usb
snd_usb_audio         108832  1 
snd_usb_lib            27392  1 snd_usb_audio
snd_hwdep              16776  1 snd_usb_audio
dvb_usb_af9015         33092  0 
dvb_usb                27148  1 dvb_usb_af9015
snd_rawmidi            33920  2 snd_usb_lib,snd_seq_midi
snd_pcm                99592  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
dvb_core              106924  1 dvb_usb
snd                    78792  19 snd_usb_audio,snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
usbhid                 47040  0 

And headset is working very very fine:o


. Greetings kasper.s

---

