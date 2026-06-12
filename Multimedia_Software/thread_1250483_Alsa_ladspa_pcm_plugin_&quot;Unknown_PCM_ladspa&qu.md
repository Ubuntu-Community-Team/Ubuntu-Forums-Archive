---
title: "Alsa ladspa pcm plugin &quot;Unknown PCM ladspa&quot;"
date: 2009-08-26
forum: Multimedia Software
---

### Post by samuelhug on 2009-08-26
I've been playing around with the /etc/asound.conf file for a couple of days now and I ran into a problem when I tried to use the ladspa plugins.

I copied the example from [http://alsa.opensrc.org/index.php/Ladspa_(plugin)](http://alsa.opensrc.org/index.php/Ladspa_(plugin))

```
pcm.ladspa {
    type ladspa
    slave.pcm "plughw:0,0";
    path "/usr/lib/ladspa";
    plugins [
        {
            label delay_5s
            input {
                controls [ 0.8 0.3 ]
            }
        }
    ]
}
```

after I put that in my /etc/asound.conf file I restarted Alsa
```
sudo /etc/init.d/alsa-utils restart
```

and then I ran
```
aplay -Dplug:ladspa test.wav
```

to test it and I recieved the following output
```
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM ladspa
aplay: main:590: audio open error: File exists
```

Any help would be appreciated

---

### Post by george_ubnt on 2009-09-01
I am facing exactly same problem.... Any updates?

---

### Post by samuelhug on 2009-09-01
nope. still havn't figured it out.

---

### Post by samuelhug on 2009-09-03
Ok I found the following article but I can make much scene out of it.
As far as I can tell I need to recompile libasound2-plugins maybe?

[The Article]("http://ubuntuforums.org/showthread.php?p=7245877&highlight=Unknown+PCM+ladspa#post7245877")

---

### Post by samuelhug on 2009-10-01
it worked for me after I upgraded to karmic beta

also I should mention that pulseaudio is the default audio system for karmic but I didn't like it cause it was giving me problems so I switched it back to alsa.

---

### Post by v_2e on 2012-01-07
Hello!
Stopping the PulseAudio daemon helps in this case.
Just type
```

pulseaudio --kill
```in the terminal of yor user and try playing the sound in a regular ALSA way. For example mplayer will determine the ALSA output device automatically.
--------
**Update:** One more problem may be that PulseAudio daemon will start itself automatically when you try to play something.
A quick but dirty workaround may be making the PulseAudio configuration ***incorrect*** for PulseAudio could not start.
I simply added a not existent device to the following string in the */etc/pulse/default.pa* file:
```

load-module module-alsa-source device=hw:1,0

```There is no device "hw:1,0" in my system, so PulseAudio cannot start. And Mplayer will play everything directly through ALSA (as well as any other player, I believe).

P.S. If you do so, just don't forget to correct the PulseAudio configuration back when you need it.
P.P.S. Still it would be much better to figure out how to play the sound through the LADSPA plugins with PulseAudio running.

---

