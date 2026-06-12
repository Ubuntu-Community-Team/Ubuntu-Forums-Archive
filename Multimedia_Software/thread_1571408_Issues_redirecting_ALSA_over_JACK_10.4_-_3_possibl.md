---
title: "Issues redirecting ALSA over JACK 10.4 - 3 possible bugs"
date: 2010-09-09
forum: Multimedia Software
---

### Post by kleinebre on 2010-09-09
Hello all,

My apologies in advance for the long post. Summary: I've got great latency running ALSA over JACK but am still experiencing some issues which spoil the fun. Any help would be much appreciated!

I finally ditched PulseAudio and set up my system with a realtime kernel. I'm redirecting ALSA over JACK.

The good: 
- Awesome, I can get <5ms latency without any xruns! (although 23.2 msec as described below is just fine for me, thank you)

The bad: 
- I'm a long-time linux audio user, but have got some minor issues which spoil the fun.

1. Without pulseaudio, the indicator applet refuses to show a volume control applet. The old gnome-volume-control-applet (the one with tooltip!) loads but doesn't show in the gnome-panel. Although I can set the volume with envy24control, it's not quite as practical as using the scrollwheel! Any way to fix this?

2. When I launching any application (such as a terminal) from the gnome-panel, a new JACK connection is created, but not cleaned up after closing the application. As a result, the QJackCtl connection list is flooded with alsa-jack.jackP.8528.xx connections (where 8528 is the process ID of gnome-panel). The jack_lsp command line program shows the same
(added spaces after every : to get around the smiley filter):

  mrjb@mrjb-desktop:~$ jack_lsp
  system: capture_1
  system: capture_2
  system: playback_1
  ...
  [some output ommited]
  ...
  alsa-jack.jackP.8528.12: out_000
  alsa-jack.jackP.8528.12: out_001
  alsa-jack.jackP.8528.13: out_000
  alsa-jack.jackP.8528.13: out_001
  alsa-jack.jackP.9604.0: out_000
  ...
  [some output ommited]
  ...
  alsa-jack.jackP.8528.20: out_001
  alsa-jack.jackP.10305.8: out_000
  alsa-jack.jackP.10305.8: out_001

Question: Is there any way to prevent all those superfluous Jack connections (even just a workaround)?

3. I've got an audio quality problem where buzz/crackle occurs in the
audio if I do the following:

a. Make sure jackd is already running and audio is playing
b. Start up a terminal
c. Run qjackctl from said terminal
d. Kill the terminal
e. Audio is now buzzing.

Can anyone confirm they can reproduce this crackle, hum and buzz?

Configuration info:

- I run Linux mrjb-desktop 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

- I start the JACK daemon during login with the following script:
-----------
  #!/bin/bash
  COUNTER=0
  
  sleep 1
  while [ $COUNTER -lt 10 ]; do
  
  nohup /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2 -s >>/home/mrjb/bin  /jack.log &
  sleep 1
  
  # Did startup work? If so, exit. Otherwise try again 
  # up to 10 times- something may be locking the device.

  if ps ax | grep -v grep | grep jackd > /dev/null
  then 
      exit 0
  fi
  
  let COUNTER+=1
  done
  # Failed to start.
------------

My ~/.asoundrc looks as follows :
------------
  pcm.!default {
                  type plug
                  slave { pcm "jack" }
          }
  
  pcm.jack {
  	type jack
  	playback_ports {
  	       0 alsa_pcm: playback_1
  	       1 alsa_pcm: playback_2
         }
  	capture_ports {
  	       0 alsa_pcm: capture_1
  		1 alsa_pcm: capture_2
  	}
  }
----------------

Audio lines in /etc/security/limits.conf:

@audio          -       rtprio          100
@audio          -       nice            -15
@audio	-	memlock	2995341


Qjackctl setup:

** I usually have my system set for a bit more latency than the 5 msec described above.
frames/period 512; periods/buffer:2; rate: 44100; realtime, soft mode,
(latency 23.2 msec)
Driver: alsa

Misc: 

Start jack audio server on application startup, enable system tray, start minimized to system tray, enable alsa sequencer.

Options: Do not execute any scripts.

Hardware: m-audio audiophile 2496; envy24/ice1712 chipset.

---

### Post by kleinebre on 2010-09-18
> **kleinebre said:**
> 
1. Without pulseaudio, the indicator applet refuses to show a volume control applet. The old gnome-volume-control-applet (the one with tooltip!) loads but doesn't show in the gnome-panel. Although I can set the volume with envy24control, it's not quite as practical as using the scrollwheel! Any way to fix this?

I've solved this by using the Volti volume control applet instead. It does not depend on pulseaudio. I did need to tweak it to work with my M-Audio audiophile 2496 - I've submitted these tweaks to the author and they will be in version 0.2.3 (but if you have a built-in soundcard 0.2.2 probably does the trick for you).

> **kleinebre said:**
> 
2. When I launching any application (such as a terminal) from the gnome-panel, a new JACK connection is created, but not cleaned up after closing the application. As a result, the QJackCtl connection list is flooded with alsa-jack.jackP.8528.xx connections


This was due to the fact that the .asoundrc configuration file I picked off the net was WRONG. 

------------
  pcm.!default {
                  type plug
                  slave { pcm "jack" }
          }
  
  pcm.jack {
  	type jack
  	playback_ports {
  	       0 alsa_pcm: playback_1
  	       1 alsa_pcm: playback_2
         }
  	capture_ports {
  	       0 alsa_pcm: capture_1
  		1 alsa_pcm: capture_2
  	}
  }
-------
ALSA audio is being forwarded to JACK, and JACK was playing back sound over ALSA. JACK is clever enough to not loop this infinitely, but it did give some unintended consequences.

The fixed .asoundrc looks as follows:

--------
pcm.!default {
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
----------

This does not create the superfluous ports. For rock solid JACK performance, it would be recommended not to have an .asoundrc file at all though- Although the browser will then not forward its audio to JACK.

> **kleinebre said:**
> 
3. I've got an audio quality problem where buzz/crackle occurs in the
audio if I do the following:
a. Make sure jackd is already running and audio is playing
b. Start up a terminal
c. Run qjackctl from said terminal
d. Kill the terminal
e. Audio is now buzzing.


I have contacted the authors of JACK for this and the general answer is "donm't do that then". I've also found that the current version of jackdmp (1.9.5?) no longer seems to exhibit this behaviour. Although heavy loads may still cause the occasional pop, click or xrun, under normal circumstances they don't occur. If they do, jackdmp seems to at least recover gracefully, without rattle.

---

### Post by sieve on 2011-03-08
> **kleinebre said:**
> I've solved this by using the Volti volume control applet instead. It does not depend on pulseaudio. 

I'll have to try this.  I uninstalled pulseaudio in 10.10 because of sound issues and went with ALSA.  But I couldn't get gnome-volume-control-applet to work.  It used to work fine in previous versions.

---

### Post by kleinebre on 2011-03-08
> **sieve said:**
> I'll have to try this.  I uninstalled pulseaudio in 10.10 because of sound issues and went with ALSA.  But I couldn't get gnome-volume-control-applet to work.  It used to work fine in previous versions.
[Volti 0.2.3]("http://code.google.com/p/volti/downloads/list") has been released by now, including my changes. The link will take you to the download page on code.google.com.

---

