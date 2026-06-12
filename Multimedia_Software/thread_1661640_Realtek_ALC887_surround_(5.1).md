---
title: "Realtek ALC887 surround (5.1)"
date: 2011-01-07
forum: Multimedia Software
---

### Post by TheHilikus on 2011-01-07
Hey guys,
i'm trying to configure alsa in my ubuntu server (running mythtv) to play surround sound. My soundcard is integrated in the motherboard and it supports 5.1 with jacks redirection. alsa reports it as HDA Intel with Realtek ALC887 chipset
When i play the test sound 
```

speaker-test -Dplug:surround51 -c6

```
i can hear only front left and front right, nothing else

I found some docs saying that 5.1 was transparent in alsa and that i only needed to specify the device as surround51 but that is not the case in my setup

i don't use gnome or pulse-audio.

does anyone know what am i missing or what can i try?

---

### Post by lidex on 2011-01-07
> You can hear sound coming from the front and rear speakers, but not from the other speakers you have
    This may be because your sound has fewer channels than you have speakers, for example because you are playing 4 channel sound onto a 5.1 channel speaker system. In this case there is no problem, things are working as they should.
    But it can be because your card uses the same sockets for some input and output channels. Often the Line in socket is also used for the LFE output channel and the Mic socket for the Center output channel, or viceversa. If this is the case you must use the appropriate toggles in the mixer controls to ensure that those sockets are used for output and not input.
    In order to test that all speakers work you can use multiple channel sound files or use the speaker-test utility, which has been included in the alsa-utils package for a while now.
Reference:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

---

### Post by TheHilikus on 2011-01-07
i am already using the speaker-test utility
the other option however, sounds plausible

i can't find the toggles mentioned.

are these supposed to be in alsamixer?

---

### Post by TheHilikus on 2011-01-07
btw, this is my configuration

[http://www.alsa-project.org/db/?f=ab677ea7ead25b0c4756c60ddb69558c1981366d](http://www.alsa-project.org/db/?f=ab677ea7ead25b0c4756c60ddb69558c1981366d)

thanks for the help

---

### Post by TheHilikus on 2011-01-07
ok, so i found out the driver does support 5.1

i tried a 10.10 live cd of ubuntu-desktop, with gnome, pulseaudio and all that stuff and it does work

here is the diff of the alsa info script, but i don't notice anything substantially different.

[http://pastebin.ca/2040549](http://pastebin.ca/2040549)

i think it must be some setting in an obscure file i don't know about

---

### Post by lidex on 2011-01-07
What is the make/model of your PC/laptop/MotherBoard?
You have a value of true for this setting in the working configuration, false in non-working
```
 comment.count 1
               iface MIXER
               name 'IEC958 Playback Switch'
-              value true
+              value false
        }
``` 
Same here:
```
Simple mixer control 'IEC958',0
   Capabilities: pswitch pswitch-joined penum
   Playback channels: Mono
-  Mono: Playback [on]
+  Mono: Playback [off]
```

---

### Post by marl30 on 2011-01-07
I have a 5.1 surround sound card as well. What I usually do to activate the other speakers is to go to sound preference> hardware> profile (settings for the selected device). Then from the drop down menu I choose Analog Surround 5.1 Output. This causes all my speakers to work. Hope this helps.

---

### Post by lidex on 2011-01-07
> **marl30 said:**
> I have a 5.1 surround sound card as well. What I usually do to activate the other speakers is to go to sound preference> hardware> profile (settings for the selected device). Then from the drop down menu I choose Analog Surround 5.1 Output. This causes all my speakers to work. Hope this helps.

Thanks for the input. That is how it's supposed to work, however he's not using pulseaudio.

---

### Post by marl30 on 2011-01-07
> **lidex said:**
> Thanks for the input. That is how it's supposed to work, however he's not using pulseaudio.

I'm also using alsa, at least that's what Jackd always says I'm using. I have a Realtek sound card as well.

---

### Post by lidex on 2011-01-07
Right, but pulseaudio is what implements the profiles and does the routing. It sits on top of alsa.

---

### Post by TheHilikus on 2011-01-08
lidex
i saw that flag you mentioned, but I didn't think that was it because that flag was for digital audio and ATM i'm not using digital, it's all analog

marl30
thanks for the help, but like lidex said, i don't use pulseaudio, so i need to find out what exactly is pulseaudio configuring on alsa so that i can do that on standalone alsa as well

---

### Post by lidex on 2011-01-08
Gotcha, too many hdmi threads...anyway see if this is in the ballpark:
[http://ubuntuforums.org/showthread.php?t=1491347](http://ubuntuforums.org/showthread.php?t=1491347)

---

### Post by TheHilikus on 2011-01-09
i don't think that configuration files are the problem.
in my live installation there are no configuration files (.asoundrc or asoundconf) and it still works

going back to your first reply, how does one change the sockets from input to output?? so far that has been the best description i have seen of my problem. it's hard to find help for this because many people report it doesn't work in players but it does in speaker-test, which is a different problem and means that alsa is fine with it

in my case, alsa is not fine with it

---

### Post by lidex on 2011-01-09
If it works in live-session, I'd say run the alsa-info script in it and compare the differences to install version.

---

