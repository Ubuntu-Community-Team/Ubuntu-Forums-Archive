---
title: "RaLink rt2800 ,wpa, kernel 2.6.38 - can't connect"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by The Adi on 2011-03-05
Hi all!
I've just realized that this is not only ubuntu problem but mainly 2.6.38 kernel but I hope I can get some answer here because it is pissing me off like hell ;) 

Copy from other forum:

Hi guys, the problem I'm trying to figure out since few weeks is that I can't login to WPA/WPA2 protected WIFI network on kernel 2.6.38. And I know for sure that this is the kernels fault because I've made some nice tests - I've had mint installed, I've made update to Natty and on boot I had two kernels to choose from so I could check both of them and of course on the 2.6.38 I couldn't connect. It was repeatedly asking for a password and nothing. I've also tested it on numerous Ubuntu live cd's and when I've tried Maverick life - all was nice and smooth, but after trying Natty from the firsts testing versions last year up to last nights alfa3 - I still can't connect. And the last proof of 2.6.38 kernels fault is the test of the latest Kanotix with the 2.6.38-rc6 (Ubuntu recompiled) - also with no luck  All distros with kernels lower than 2.6.38 are connecting very smoothly and all distros with all rc's of 2.6.38 gives me no luck. So the question is What The Heck is going on??  Is this kernel really so f*#¤%d up?

Hope that on this global forum is somebody who know something what is going on :)

---

### Post by zenarcher on 2011-03-05
Sounds like the identical issue I'm having with the same kernel and Atheros wireless.

Cheers,
zenarcher

---

### Post by The Adi on 2011-03-05
Hey zenarcher, yup, and on the net I've seen many problems of that kind but....in over two months I can't find the answer! Come on! What is wrong with this "linux world" :D Do I really need to write to the Guru Linus? :P

---

### Post by rapiertg on 2011-03-05
You should check which modules are loaded on each kernel with lsmod. I had similiar problems, so i added some lines to my /etc/modprobe.d/blacklist.conf:
blacklist rt2800usb
blacklist rt2x00usb
which resulted in loading rt2870sta which works very good.

---

### Post by The Adi on 2011-03-05
Thanks for the tip rapiertg, I'll try to do it,
dzieki ;)

---

### Post by zenarcher on 2011-03-05
Well, here's what I have with lsmod:

zenarcher@stanmain:~$ lsmod
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  0 
snd_hda_codec_hdmi     28103  4 
snd_hda_codec_realtek   336647  1 
snd_hda_intel          33211  4 
snd_usb_audio         112390  1 
arc4                   12529  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_pcm                96625  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
nvidia              10674131  40 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath5k                 155409  0 
ath                    23773  1 ath5k
snd_timer              29602  2 snd_pcm,snd_seq
ppdev                  17113  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              294370  1 ath5k
uvcvideo               68099  0 
videodev               82052  1 uvcvideo
psmouse                73535  0 
cfg80211              178528  3 ath5k,ath,mac80211
joydev                 17606  0 
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
edac_core              53845  0 
k8temp                 13016  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36959  1 
edac_mce_amd           23464  0 
i2c_nforce2            13058  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
pata_amd               14130  0 
ahci                   25951  3 
libahci                26642  1 ahci
forcedeth              63555  0 

My Atheros wireless uses the Atheros AR5001X chipset....but I'm thinking I have a similar problem.

Regards,
zenarcher

---

### Post by rapiertg on 2011-03-05
> **zenarcher said:**
> 

My Atheros wireless uses the Atheros AR5001X chipset....but I'm thinking I have a similar problem.

Regards,
zenarcher

Was it working before on this ath5k driver? I found something related here:
[http://ubuntuforums.org/showthread.php?t=1505100](http://ubuntuforums.org/showthread.php?t=1505100)

Hope it helps you.

---

### Post by zenarcher on 2011-03-05
Thanks for that link.  I'm not real sure, as it's been working fine until this last kernel update, which is when it began to act up.  It might die within a couple of minutes...and other times, it will stay connected for an hour or so.  Doesn't seem to be any real pattern to it, other than it always connects up and works fine, right after I reboot the system.  It's doing the same thing with three different systems, all using the same wireless card and all with Natty and Kubuntu.  It was doing the same with Alpha 2 and I was hoping Alpha 3 might have a fix.

Cheers,
zenarcher

---

### Post by rapiertg on 2011-03-06
> **zenarcher said:**
> Thanks for that link.  I'm not real sure, as it's been working fine until this last kernel update, which is when it began to act up.  It might die within a couple of minutes...and other times, it will stay connected for an hour or so.  Doesn't seem to be any real pattern to it, other than it always connects up and works fine, right after I reboot the system.  It's doing the same thing with three different systems, all using the same wireless card and all with Natty and Kubuntu.  It was doing the same with Alpha 2 and I was hoping Alpha 3 might have a fix.

Cheers,
zenarcher


If i were you, i would boot up maverick, and check if wifi is using the same driver as in natty. If so, i would file a bug or search for one already submitted.
Sorry i couldn't help more but i have never used atheros cards.

---

### Post by zenarcher on 2011-03-06
Thanks for the info.  I do have one system running Maverick and all is fine with the same Atheros wireless on it, so long as I'm not using this latest kernel.  Everything else seems to be the same versions, so I'll have to dig in a bit more deeply.  I've always used Atheros as it's always "just worked out of the box."

Edit:  I'm thinking this may be the fix.  [https://bugzilla.kernel.org/show_bug.cgi?id=27382](https://bugzilla.kernel.org/show_bug.cgi?id=27382)

Thanks,
zenarcher

---

### Post by rapiertg on 2011-03-06
> **zenarcher said:**
> Thanks for the info.  I do have one system running Maverick and all is fine with the same Atheros wireless on it, so long as I'm not using this latest kernel.  Everything else seems to be the same versions, so I'll have to dig in a bit more deeply.  I've always used Atheros as it's always "just worked out of the box."

Thanks,
zenarcher

The problem here can be some driver as in my case. Everything worked out of the box in maverick, but in natty kernel devs decided one staging driver to be mature enough to "turn it on" by default. It works well, but cant connect to some secure networks. In your case it can be the same, thats why you better check if the same modules are loaded in lsmod.
Cheers

---

### Post by zenarcher on 2011-03-06
Well, so far, I have rebooted my Natty systems with the previous kernel and the problem is solved.  Looking at the kernel bug reports, it appears there are a few of us having this same issue with the same kernel.

Cheers,
zenarcher

---

### Post by The Adi on 2011-03-06
Hi and hello guys :) I have a great news for you...well, I don't know if this is for you but for me indeed :D Ok, to cut the story short for me the problem is solved...at last after so many weeks :D What have I done? Just what rapiertg advised, in /etc/modprobe.d/blacklist.conf I've blacklisted rt2x00pci and rt2800pci and instead rt2860sta started to work very nicely :) 
So.....I should back my words about the 2.6.38 up and say - sorry dear kernel, youre awesome :P
Ok, if the thread is'nt needed anymore maybe we can mark it solved :)

Thanks rapiertg for the solution (niech bóg cie w dzieciach wynagrodzi ;) )

See you friends and have a great time,

Namasté

P.S. Oh, and yes, the best way to find out whats going on is to check what modules and drivers are on and off writing lsmod in console, in my opinion it definitely seems that some modules/drivers are "fighting" with each other and trying to gain the "ownership" over some processes or hardware and we just need to direct them to do their job and to tell others that they are fired :D

Cheers
Adi

---

