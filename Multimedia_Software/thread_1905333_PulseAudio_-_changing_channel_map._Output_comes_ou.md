---
title: "PulseAudio - changing channel map. Output comes out of the wrong speakers in 5.1!"
date: 2012-01-06
forum: Multimedia Software
---

### Post by g0l3m on 2012-01-06
Hi all,

I've been struggling with this for a while now...Read up lots of posts, tried lots of solutions, no luck! My problem (in theory) is very simple. In my 5.1 configuration the wrong sound comes out of the wrong speaker. So, I just need to change my channel map (correct me if I'm wrong on this). Here's what list-sinks in pacmd shows:

sample spec: s16le 6ch 44100Hz
channel map: front-left,front-right,rear-left,rear-right,front-center,lfe
Surround 5.1

Here's the output from speaker-test -c6 -l1 -twav:

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
0 - Front Left
4 - Centre
1 - Front Right
3 - Rear Right
2 - Rear Left
5 - LFE
Time per period = 9.278501

Trouble is only 2 of these are correct, the front-left and front-right. The others are in weird order, e.g. center comes out from rear-left, rear-left comes out of the subwoofer, etc.

Here's what I've tried so far (having searched A LOT):

In /etc/pulse/daemon.pa changed sample channels to 6 (and also the default channel map) - no joy.

In /etc/pulse/daemon.conf changed system.pa and default.pa to not load the autodetect modules but instead use module-remap-sink as per [http://confignewton.com/?p=211](http://confignewton.com/?p=211) - no joy.

In /usr/share/pulseaudio/alsa-mixer/profile-sets/ changed the channel map in default.conf for the 5.1 configuration - no joy.

This last solution I was hoping would do the trick but when I list-sinks in pacmd the order seems to be the same all the time.
Essentially, all I need is instead of:

channel map: front-left,front-right,rear-left,rear-right,front-center,lfe

to have this:

channel map: front-left,front-right,lfe,front-center,rear-left,rear-right

I'm hoping I'm missing something really obvious and the solution is pretty straight forward. Please help if you can!
If you require any addition info please do ask. This is on a brand new 11.10 installation with:

alsa.card_name = "Intel ICH5"
alsa.long_card_name = "Intel ICH5 with AD1985 at irq 17"
alsa.driver_name = "snd_intel8x0"

3 jacks at the back of the card to connect to speakers.

cheers,
g.

---

### Post by g0l3m on 2012-01-08
bump!

I'm still stuck...will post the solution if I ever find one.
Please do tell if you have _ANY_ ideas of what I could try.

---

### Post by g0l3m on 2012-01-18
bump! still stuck! any ideas? please!!!

---

### Post by BicyclerBoy on 2012-01-18
Do you have the 3 jacks plugged into the correct sockets?

I would suspect that wrong channel order has its root cause in the audio h/w detection..
Or the fact that alsa ffmpeg pulse & AC3-spec all have different channel orders. There are 2 spec orders for AC3 & 2 versions from ffmpeg.

speaker-test drives the audio h/w directly via alsa driver..
You have not specified the alsa device (-D) so it uses default.

Should you be using surround51 ?
Not sure what your alsa default is...
aplay -L

None of the pulse tweaks will influence(corrupt) speaker-test unless you point speaker-test at the pulse device or change your /etc/asound.conf..
Even then I'm not sure the channel reordering will effect speaker-test.

You can find 5.1 test tracks (AAC & AC3) that you play with VLC etc.
These let you test the pulse audio setup.
AviaSurroundTest-AAC.mkv
Test-AC3-v2.0.avi
www_lynnemusic_com_surround_test.ac3

Alternatively you can reorder channels in alsa:
```

#/etc/asound.conf
# speaker-test -c 6 -r 48000 -D pcm.swap51
pcm.swap51 {
   @args.0 SLAVE
   @args.SLAVE {
               type string
               default "surround51"
   }
   type route
   slave {
         pcm $SLAVE
         channels 6
   }
   ttable {
     0.0= 1
     1.4= 1
     2.5= 1
     3.2= 1
     4.1= 1
     5.3= 1
   }
}

```
The channel ttable is not setup to fix your order..

---

### Post by g0l3m on 2012-02-04
Hi,

Thank you for your reply.
I don't seem to have an /etc/asound.conf.

Any suggestions?

---

### Post by BicyclerBoy on 2012-02-05
Its a simple text file in a specific location in the file system.
You can just create it with gedit etc..

---

