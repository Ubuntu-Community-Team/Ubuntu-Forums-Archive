---
title: "Output Audio From Both the Laptop Speakers &amp; the Headset Jack (green) Simultaneously"
date: 2011-06-20
forum: Multimedia Software
---

### Post by ellaivarios on 2011-06-20
Hi Everyone.

(I have a Dell Inspiron 9400, Duo Core, with an onboard SigmaTel STAC9200 codec, (after running "cat /proc/asound/card0/codec#* | grep Codec" without the quotes in a terminal) and from what it seems in Ubuntu the card uses ALSA as a driver although some applications I notice also use Pulseaudio. I have no problem with my audio, it works like a charm. BUT:

I would like to find a way to allow the same sound output from my laptop both from the laptop speakers and the headphone jack simultaneously.

Normally, as soon as you plug in a headphone jack (green jack) to the laptop, sound from the speakers is disabled. There should be a software switch (some kind of script) that can allow me to turn this feature on or off by assigning a keyboard shortcut to it. 

For some people having sound come out of the speakers and the headset at the same time is a bug, and they are right, IF YOU CAN"T CONTROL WHEN IT HAPPENS. For me something likethis would be bliss, as it would increase sound volume and sound quality, as my laptop speakers have a subwoofer, but the mini USB-powered speakers I attach to the headphone jack are mostly bass-less). In effect I would have the two front Laptop Speakers and the Laptop Subwoofer, and the two USB-powered speakers attached to the green jack, all outputting the same sound simultaneously.

Recently I found a pretty handy script I saved as a .sh file to turn off or on my screen and then I assigned a keyboard shortcut to it. Is there any way I can do something similar to switch between having audio go out both my laptop speakers and the headphone jack simultaneously and then switch it back to behave as it does by default: inserting jack disables laptop speakers?

Any help would be greatly appreciated!!

[Added info]
Ok After some more looking around, there seems to be a solution which is basically involves disabling or enabling the jack sensor on my laptop's headphone jack.
Ideally a script that does just this would be perfect.


[COLOR="DimGray"]This customizability of Linux -- without the need for programs for certain utilities -- makes you fall in love with Linux, but you need to learn a lot until you can do it yourself. It would be fantastic if Linux included a Learner's manual with installation, so users can learn basic commands, and scripting., and master the terminal, as well as the OS components and inner working functions and features, so as to achieve maximum tweakability.[/COLOR]

---

### Post by ellaivarios on 2011-06-20
Ok it's funny to reply to my own post, but It might help others too. I have not solved anything yet, but I think I'm getting somewhere after reading the information from the following threads, and especially the user [COLOR="Purple"]CasualObserver[/COLOR]:

[http://ubuntuforums.org/showthread.php?t=593132](http://ubuntuforums.org/showthread.php?t=593132)
[http://ubuntuforums.org/showthread.php?t=1687823](http://ubuntuforums.org/showthread.php?t=1687823)
[http://ubuntuforums.org/showthread.php?t=1316880](http://ubuntuforums.org/showthread.php?t=1316880)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect](http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect)

The basic idea here is to manipulate the headset sensor jack by turning it on or off. I managed to do everything described below, but i got stuck because I do not have this option in Alsa mixer when I open it from the terminal, so I can't turn the headset sensor on or off.

**1.** Find the name of your sound card chipset by typing in a terminal:

[HTML]cat /proc/asound/card0/codec#* | grep Codec[/HTML]

It should give you something like **Codec: SigmaTel STAC9200** (that's what mine is)

**2.** Using the name of your soundcard chipset you found before, find the chipset  based on your computer model/motherboard here:
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) 

You will get a list of possible models like this:

[HTML]STAC9200
========
  ref		Reference board
  oqo		OQO Model 2
  dell-d21	Dell (unknown)
  dell-d22	Dell (unknown)
  dell-d23	Dell (unknown)
  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
  dell-m22	Dell Latitude D620, Dell Latitude D820
  dell-m23	Dell XPS M1710, Dell Precision M90
  dell-m24	Dell Latitude 120L
  dell-m25	Dell Inspiron E1505n
  dell-m26	Dell Inspiron 1501
  dell-m27	Dell Inspiron E1705/9400
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)[/HTML]

The line saying "dell-m27" is my Model. You can also use "auto" (or maybe also "default") if it appears at the bottom.


**3.** Next you need to edit your ALSA config file:
[HTML]sudo nano /etc/modprobe.d/alsa-base.conf[/HTML]

and add this line to the bottom of the file replacing **XXXXXX** with the model above (mine is "dell-m27")
i.e. "options snd-hda-intel model=dell-m27":
[HTML]options snd-hda-intel model=XXXXXX[/HTML]

(exit nano by typing "<Ctrl>+x") 
(and nano will ask you to save before exit, or press "<Ctrl>+o" to save first and then exit with "<Ctrl>+x")
 You can also do all this using Gedit with a sudo command.

**4.** Now you need to reload the ALSA driver:
[HTML]sudo alsa force-reload[/HTML]

**5.** And you can test if your audio is working properly:
[HTML]speaker-test -Dplug:surround51 -c6 -twav[/HTML]

**6.** Finally you can turn on or off certain features of the sound card/chipset in the mixer. 
[HTML]alsamixer[/HTML]

Sometimes features will be muted by default. In particular, you need to "unmute" the headset jack sensor, and your laptop speakers should play at the same time as the headset, outputting the same sound. However, if you are unlucky as me, the feature "headset jack sensor" will not be present. So I'm stuck again. By the way for those of you who can play around with these features, you should be able to "mute" or "unmute" devices by pressing "M" on your keyboard. The rest is quite intuitive.

As for me, who doesn't have this feature/option appearing in the mixer, maybe I need to go back to that list and add a different model or "auto" in the bottom line of the ALSA configuration file that we added using the nano editor (?). I'll try and post again. Maybe ALSA is an older version (?) ALSA version 1.22. I'm not sure. And I'll also try downloading everything available for ALSA just in case, and restarted ALSA afterwards:
[HTML]sudo aptitude install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`[/HTML]
But it made no difference.


I even tried after finding some suggestions in other threads:
[HTML]amixer -c 0 sset 'Headphone Jack Sense' unmute[/HTML]
But of course it returns that there is no such control: 
[COLOR="Gray"]amixer: Unable to find simple control 'Headphone Jack Sense',0[/COLOR]


Below is firslty a screen shot of my ALSA mixer, where you can see I have no option to mute/unmute/disable the headset sensor jack and then there is a screen shot from Andrew Wileur whose post shows his ALSA mixer with all these controls. **I have this option in Windows. So it is supported by my Sound card. I just can't understand why it is so stubborn in Linux.**

---

