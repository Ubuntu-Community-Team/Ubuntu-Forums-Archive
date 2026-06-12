---
title: "USB sound: Lexicon Omega bandwidth problem"
date: 2010-10-22
forum: Multimedia Software
---

### Post by Danstroem on 2010-10-22
Hello,

I have trouble to get a USB 2.0 soundcard working on Maverick 64 bit (linux-image-generic 1.9.5~dfsg-19ubuntu1, alsa-base 1.0.23+dfsg-1ubuntu4). The Lexicon Omega is a 24bit soundcard with 4 inputs and 2 outputs. Alsa does support it out of the box ( [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Lexicon](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Lexicon) ) with the module snd-usb-audio.

When trying to record more than 2 channels from alsa, the following shows up on kern.log
```
kernel: [ 3240.838515] cannot submit datapipe for urb 0, error -28: not enough bandwidth
```When trying to start "jackd -v -r -dalsa -dhw:2 -r44100 -p512 -n2", it fails with a broken pipe from alsa and the bandwidth message on kern.log. When starting in simplex mode, it works. Also, when forcing the input and output count to "2", it works, too. So: is there really not enough bandwidth on USB for alsa?

My guess is no, because:

[LIST]
[*]No other USB devices connected, soundcard directly plugged into notebook (tried restart and cold boot)
[*]soundcard works in full on the same machine with M$ Win7 and vendor drivers
[*]soundcard works in full on another notebook with Karmic 32bit
[/LIST]

Tried to:

[LIST]
[*]disable pulseaudio ( echo autospawn = no >> ~/.pulse/client.conf ) and restarted
[*]reinstall the Ubuntu sound system and configuration ( [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) )
[*]hard-reset soundcard
[*]Fiddle with snd-usb-audio module parameters "async_unlink" and "nrpacks"
[/LIST]

Additionally, when disconnecting the device (even when it was not used after plugging it in), a bunch of errors occurs on kern.log:
```
kernel: [ 3437.687384] urb status -32
kernel: [ 3437.687749] urb status -32
kernel: [ 3437.687995] urb status -32
kernel: [ 3437.688249] urb status -32
...
kernel: [ 3440.283103] urb status -32
kernel: [ 3440.283342] urb status -32
kernel: [ 3440.283596] urb status -32
kernel: [ 3440.284379] usb 2-1.2: USB disconnect, address 3
```It doesn't hurt me, because I disconnect the device, but maybe it helps debugging the problem. Output of alsa-info.sh is attached. Any hint is greatly appreciated! Thank you very much! ):P

---

### Post by utilitytrack on 2010-10-22
> **Danstroem said:**
> is there really not enough bandwidth on USB for alsa?


I think will be better if you ask this in ALSA developers. 

You can subscribe to Alsa-devel mailing list here: [http://mailman.alsa-project.org/mailman/listinfo/alsa-devel]("http://mailman.alsa-project.org/mailman/listinfo/alsa-devel")

---

### Post by utilitytrack on 2010-10-22
Also see this:

[https://bugzilla.redhat.com/show_bug.cgi?id=527813]("https://bugzilla.redhat.com/show_bug.cgi?id=527813")

[http://www.mail-archive.com/linux-usb@vger.kernel.org/msg00192.html]("http://www.mail-archive.com/linux-usb@vger.kernel.org/msg00192.html")

[http://comments.gmane.org/gmane.linux.usb.general/33921]("http://comments.gmane.org/gmane.linux.usb.general/33921")

---

