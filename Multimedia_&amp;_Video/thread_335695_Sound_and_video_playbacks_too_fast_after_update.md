---
title: "Sound and video playbacks too fast after update"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Stenico on 2007-01-10
Hi, after an update this morning, audio and video plays too fast in all the media players I have installed (mplayer, mpd, totem, xmms, rythmbox etc). :( 

This is the update log:
> 
2007-01-10 10:00:46 status installed linux-restricted-modules-common 2.6.17.7-10.1
2007-01-10 10:01:11 status installed linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1
2007-01-10 10:01:19 status installed wine 0.9.29~winehq0~ubuntu~6.06-1
2007-01-10 10:01:20 status installed xserver-xorg-core 1:1.1.1-0ubuntu12.1

I am using the Linux 2.6.17-10-generic kernel on an up to date Edgy installation.

Some hardware details are listed below, but given this problem is a direct result of the update, I'm not sure they are relevant to solving the problem. 

I have tried rebooting.

Any help much appreciated, for me this is a fairly major issue as I cannot listen to music/play videos etc now!

Additional info:

(1) The system clock keeps the correct time.

(2) I am using the following soundcard
> 
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)


(3) Another sound card is also installed, but not in use.
> 
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)


(4) lsmod grep | snd gives:
> 
snd_ens1371            28704  0 
gameport               17160  1 snd_ens1371
snd_rawmidi            27264  1 snd_ens1371
snd_seq_device          9868  1 snd_rawmidi
snd_intel8x0           34844  3 
snd_ac97_codec         97696  2 snd_ens1371,snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  5 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  13 snd_ens1371,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


(5) Asound.conf:
> 
pcm.card0 {
type hw
card 1
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}


---

### Post by Stenico on 2007-01-11
After a shutdown and boot up, this has problem spontaneously fixed itself. Fingers crossed it stays fixed!:cool:

---

