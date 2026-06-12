---
title: "FA-66: routing ALSA via jack and freebob to firewire device"
date: 2007-12-19
forum: Multimedia Production
---

### Post by nellinger on 2007-12-19
hi there
I've switched from windows to ubuntu some days ago for reasons we all know. fortunately most devices work properly. the only thing i have problems with is my fa-66 firewire audio device. i have read that it works with jack and freebob. aktually, applications that can access jack directly like audacity work. but i would like to route alsa to freebob so that every application like mp3 players can also use the fa-66.

------------------------------
error message
------------------------------
mario@mario-laptop-ub:/media/sda7/mp3$ aplay -D pcm.jackplug mario.wav
JACK tmpdir identified as [/dev/shm]cd.
Wiedergabe Wave 'mario.wav' : Signed 16 bit Little Endian, Samplingrate: 44100 Hz, Stereo
cannot connect alsa-jack.jackP.25595.0: out_000 to freebob_pcm:dev1p_LineOut
aplay: pcm_write:1265: Schreibfehler: Input/output error
mario@mario-laptop-ub:/media/sda7/mp3$

------------------------------
jack message
------------------------------
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
09:55:28.727 MIDI connection graph change.
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
09:55:28.769 MIDI connection change.
09:55:29.667 Server configuration saved to "/home/mario/.jackdrc".
09:55:29.673 Statistics reset.
09:55:29.677 Client activated.
09:55:29.680 Audio connection change.
09:55:29.684 Audio connection graph change.
JACK tmpdir identified as [/dev/shm]
09:56:41.757 Audio connection graph change.
unknown destination port in attempted connection [freebob_pcm:dev1p_LineOut]

--------------------------------
asound.conf
--------------------------------
pcm.jack {
type jack
playback_ports {
0 freebob_pcm:dev1p_LineOut 1+2 left
1 freebob_pcm:dev1p_LineOut 1+2 right
}
capture_ports {
0 freebob_pcm:capture_1
1 freebob_pcm:capture_2
}
}
pcm.jackplug {
#pcm.!default {
type plug
slave { pcm "jack" }
}

--------------------------------
aplay -L
--------------------------------
mario@mario-laptop-ub:/media/sda7/mp3$ aplay -L
default:CARD=I82801DBICH4
Intel 82801DB-ICH4, Intel 82801DB-ICH4
Default Audio Device
front:CARD=I82801DBICH4,DEV=0
Intel 82801DB-ICH4, Intel 82801DB-ICH4
Front speakers
surround40:CARD=I82801DBICH4,DEV=0
Intel 82801DB-ICH4, Intel 82801DB-ICH4
4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
Intel 82801DB-ICH4, Intel 82801DB-ICH4
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
Intel 82801DB-ICH4, Intel 82801DB-ICH4
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
Intel 82801DB-ICH4, Intel 82801DB-ICH4
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
Discard all samples (playback) or generate zero samples (capture)

any ideas? thank you.

---

### Post by Encestre on 2007-12-22
Hi, have you resolved your problem ? I've a firewire soundcard and plug jack from alsa don't work for me too !

Regards.

---

### Post by Em-Buntu on 2007-12-25
If I could get this to work I can finally dump Windows XP 64 & Cakewalk.
I'm using the FA-66 also, but haven't been able to get Jack and Rosegarden to work with it.
I believe the solution lays in getting Jack configured correctly. It sees the FA-66 but is not connecting to Rosegarden or Audacity as it should. My JACK install keeps giving timer resolution errors.

---

### Post by yannos1 on 2007-12-26
Hi nellinger,

This asound.conf works for me :

--------------------------------
asound.conf
--------------------------------
pcm.jack {
type jack
playback_ports {
0 0
1 1
}
capture_ports {
0 0
1 1
}
}
pcm.jackplug {
#pcm.!default {
type plug
slave { pcm "jack" }
}

I just replaced the port names by the port numbers.
I don't know why it does not work with the port names.
Hope this helps.

---

### Post by monogyre on 2008-01-19
Hi nellinger,

try putting quote marks round the device name as in:

pcm.jack {
    type jack
    playback_ports {
         0 "freebob_pcm:dev1p_LineOut 1+2 left"
         1 "freebob_pcm:dev1p_LineOut 1+2 right"
    }

that made it work for me anyway

---

### Post by tristan_koen on 2008-04-29
Has anybody had any success in doing the opposite?

I have an M-Audio Firewire Solo that I use for capture though jackd/freebob. 

In my particular case, I would prefer to route the output through alsa_pcm device.

I am running Hardy and tried using the Debian Pulseaudio Jack module (that doesn't exist in the repository for some obscure reason) and loading the jack-source module. It works for about 4 seconds before the whole audio system crashes.

I would prefer to bypass Pulseaudio completely and go straight to ALSA though. 

Any help here would be appreciated.

---

### Post by Tom Mann on 2008-05-19
Have you started the jack daemon either with qjackctl or jackd before running these tests?

---

### Post by daverich on 2008-05-26
i'm not sure if this is related but my firewire soundcard (onyx mixer) worked fine in gutsy, after the hardy install - it wont even recognise it! :(

the bad news is I only realised when I was all setup at a gig ready to record.

My instant gut reaction was to reinstall windows 'cos that always worked,- of course I should've checked after upgrading to hardy, but hey - this stuff should keep working if it worked before :(

Kind regards

Dave Rich

---

### Post by chevyvan10 on 2008-06-04
hey, I know this is an old thread, but I'm getting desperate to get my sound working with my presonus firebox... I've got jack working correctly and I can get sound in ardour... I just want to be able to listen to music, watch movies etc using my sound card. I've tried the codes both monogyre and yannos1 have provided, and neither worked for me. Any ideas? If you need any more information, let me know and I'll provide it as soon as I can.

---

### Post by hogiewan on 2008-06-25
I'm having problems with this as well.  I have my M-Audio NRV-10 working with jack/ardour, but I can't get alsa to pipe through jack to get sound.  Apparently libasound2-plugins doesn't include the jack plugin even though the docs say so.  I've tried compiling alsa-plugins, but when trying to play with aplay, I get this error

>  Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_jack.so
aplay: main:546: audio open error: No such file or directory


However, compiling the jack plugin in the alsa-plugins tarball, It creates a libasound_module_pcm_jack.**la**

I've tried renaming this to so, but (as expected) it didn't work, but I still get the "no file" error, even with a file named correctly in the right directory.

---

