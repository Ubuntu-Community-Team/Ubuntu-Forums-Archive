---
title: "delay exceeding spare time"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by playersgc on 2006-08-12
I'm running Dapper on a Compaq Evo N115 with a SoundMAX Digital Audio card.
I've gotten the Jack server to start ok, but when I try to run any apps that might use it, the message window fills up with:
```
delay of 20231.000 usecs exceeds estimated spare time of 20004.000; restart ...
delay of 20114.000 usecs exceeds estimated spare time of 20004.000; restart ...
delay of 20301.000 usecs exceeds estimated spare time of 20004.000; restart ...
delay of 20239.000 usecs exceeds estimated spare time of 20004.000; restart ...
delay of 20004.000 usecs exceeds estimated spare time of 20004.000; restart ...
```

I've also tried booting with "StudioToGo" and "Dynebolic" CD's, and Jack runs fine with no complaints no matter what I do!  I've duplicated the settings from the "Setup..." window in Dapper, but still the same thing happens.
Are there other settings somewhere else I can look at to see why it might work in those other systems and not Ubuntu?

---

### Post by playersgc on 2006-08-13
](*,) 
I'm stuck.  Any suggestions on other places to look for hints?
Do I need to post more information about my hardware to get help?

---

### Post by playersgc on 2006-08-13
I got it!
Somehow I had neglected to follow the instructions to give my audio group permissions to access the rtprio, nice, and memlock limits.

For some reason it doesn't stay there when I reboot, though.
How do I make that permanent?

---

### Post by floogy on 2006-08-14
Ah, good point. I guess that's exactly the reason why I think that I have no improvements in the rt-kernel I compiled yesterday over the dapper stock kernel!

I'll looking into that this evening, and if I find a way to make it permanent I'll tell you.

I think you have to look into /etc/init.d for a local start script.

Can this 'delay exceeding' error lead into heavy crashes where the whole panel and almost all other apps are affected as well?

---

### Post by playersgc on 2006-08-14
Yes, that error seemed to affect everything concerned.
I read elsewhere that badly distorted sound was another result.

---

### Post by floogy on 2006-08-14
One other place to look for that issue might be udev.permissions ?

---

### Post by floogy on 2006-08-14
Hmm... I'm not shure what you're talking about, because the changes I made to 
/etc/security/limits.conf are permanent.

```

$ tail -n5 /etc/security/limits.conf

# End of file
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10
```

And it seems to me, that the latency isn't improved at all, maybe the patch failed, and I patched only the two chunks out of >80 by hand. 

I thought patch patched everything beside the two chunks that it complained of?? 

I'll look into that later.

How can I test if my system has such rt capabilities?

---

### Post by dolson on 2006-08-14
Firstly, check in the other thread that you mentioned your kernel compile for the answer to why your latency is not improved.

Secondly, the changes in limits.conf do not magically configure JACK to a lower latency, you have to do that yourself. It simply enables you to run applications with the FIFO scheduler, which is as high a priority as you can get, basically.

Thirdly:
find . -name '*.rej'
Run that command to get a list of files that contain rejected hunks. Note that if you get any rejected hunks, you're patching the wrong kernel.

--

to the original poster, i don't have any idea why your file is overwriting changes automatically.. it shouldn't be.

---

### Post by playersgc on 2006-08-14
I checked my /etc/security/limits.conf file, and apparently, I edited it three times, because those lines from the setup wiki about the realtime priority are still there, three times.

So now I have no idea how I fixed the "delay exceeding..." error.
hmm.

---

### Post by playersgc on 2006-08-16
well,  it's broken again.  I'm stumped.:confused: ](*,)

---

### Post by floogy on 2006-08-16
Hmmm... I'm stuck, too. I'm sorry to hijack somewhat your thread, but I can imagine, that's related to your issues... At least I hope so.


I managed, to get a single irq for my soundcard with pci=biosirq [1], but that doesn't help on audio output. 
I got also a recompiled kernel with CONFIG_HZ=1000 instead of 250. 

[1]
```
~$ grep noapic /boot/grub/menu.lst
kernel  /boot/vmlinuz root=/dev/sda9 ro console=tty0 quiet splash apic=off nolapic noapic pci=biosirq
```
The only thing that seems to work well is hydrogen, and midi. There are no xruns at all. 
But when I run jacklauncher ./lastfm.sh it plays nothing. xmms crashes after a millisecond or so, 
but I hear the initial sound, and qjackctl shows for a flash the appropriate connection, the same with beep-media-player, 
but it last 20 milliseconds longer ;-)

aplay -Dplug:jackplug doesn't work at all:
```
02:53:59.229 Audio connection change.
cannot connect ports owned by inactive clients; "alsaP.11987.0" is not active
cannot connect ports owned by inactive clients; "alsaP.11987.0" is not active
02:53:59.425 Audio active patchbay scan...
```
but aplay seems to play fine, but I don't hear anything ;-)
```
$ aplay -Dplug:jackplug ~/out.wav
Playing WAVE '/home/gerhard/out.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```
But alsaplayer works, with initial xruns:
```
883 Audio connection change.
02:56:25.931 Audio connection graph change.
02:56:26.088 Audio active patchbay scan...
subgraph starting at qjackctl-11026 timed out (subgraph_wait_fd=22, status = 0, state = Finished)
02:56:27.085 XRUN callback (1).
**** alsa_pcm: xrun of at least 1.196 msecs
**** alsa_pcm: xrun of at least 70.851 msecs
[...]
_pcm: xrun of at least 0.016 msecs
subgraph starting at qjackctl-11026 timed out (subgraph_wait_fd=22, status = 0, state = Finished)
02:56:28.894 XRUN callback (7).
**** alsa_pcm: xrun of at least 1.051 msecs
02:56:28.941 XRUN callback (5 skipped).
**** alsa_pcm: xrun of at least 127.841 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
02:56:30.966 XRUN callback (2 skipped).
subgraph starting at qjackctl-11026 timed out (subgraph_wait_fd=22, status = 0, state = Finished)
02:56:34.736 XRUN callback (10).
**** alsa_pcm: xrun of at least 1.326 msecs
**** alsa_pcm: xrun of at least 17.289 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
subgraph starting at qjackctl-11026 timed out (subgraph_wait_fd=22, status = 0, state = Finished)
**** alsa_pcm: xrun of at least 0.898 msecs
02:56:34.997 XRUN callback (3 skipped).
02:56:36.923 XRUN callback (14).
**** alsa_pcm: xrun of at least 2130.599 msecs

```
```
gerhard@ubuntu:~/download/Radio/Last.FM/svn/trunk/bin$ alsaplayer ~/out.wav
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
snd_pcm_open: Device or resource busy (default)
Failed to initialize plugin!
Failed to register plugin: /usr/lib/alsaplayer/output/libalsa_out.so
Failed to load output plugin "alsa". Trying defaults.
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
snd_pcm_open: Device or resource busy (default)
Failed to initialize plugin!
/usr/lib/alsaplayer/output/libalsa_out.so failed to load
jack: running interface at 48000 instead of 44100
```
bpm and xmms are using this alsa plug of .asoundrc:
```
#JACK http://gentoo-wiki.com/HOWTO_Jack#Any_application_that_uses_ALSA

pcm.jackplug {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 alsa_pcm:playback_1
        1 alsa_pcm:playback_2
    }
    capture_ports {
        0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}
#EndJACK
```
The dspload with hydrogen and alsaplayer running is 0,9% up to 1,2%, that seems to be very good.

beep-media-player crashes jack (uses plug:jackplug):
```
03:08:07.494 Audio connection graph change.
03:08:07.519 Audio active patchbay scan...
03:08:07.521 Audio connection change.
03:08:07.724 Audio active patchbay scan...
03:08:08.909 Audio connection graph change.
03:08:08.935 Audio active patchbay scan...
subgraph starting at alsaplayer-12531 timed out (subgraph_wait_fd=25, status = 0, state = Finished)
03:08:09.390 XRUN callback (19).
**** alsa_pcm: xrun of at least 0.271 msecs
03:08:17.864 Shutdown notification.
03:08:17.867 Client deactivated.
jackd watchdog: timeout - killing jackd
03:08:17.876 JACK was stopped successfully.
zombified - calling shutdown handler
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
```
I heard the first milliseconds, though.

Some of the needed informations I found here:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issues](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issues)
[http://www.sabi.co.uk/Notes/linuxSoundLatency.html](http://www.sabi.co.uk/Notes/linuxSoundLatency.html)

I'll try to run bmp, xmms and lastfm like this:
```
for p in $(pidof beep-media-player); do chrt -v -r -p 5 $p; done
```
```
aptitude install schedutils
``` provides chrt

but that doesn't work either!
```

$ for p in $(pidof beep-media-player); do chrt -v -r -p 5 $p; done
pid 17930's current scheduling policy: SCHED_RR
pid 17930's current scheduling priority: 5
pid 17930's new scheduling policy: SCHED_RR
pid 17930's new scheduling priority: 5
```

Any help would be highly appreciate!

Kind regards

Gerhard

---

