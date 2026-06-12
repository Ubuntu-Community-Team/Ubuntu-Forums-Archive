---
title: "Directing the system sound to jackd"
date: 2010-04-13
forum: Multimedia Software
---

### Post by nezurian on 2010-04-13
Hi. I have been having troubles with having sound from my soundcard "M-Audio Firewire Solo" since I installed Ubuntu, more than 1 year ago. 

Today, I have the sound from audacious 2 by using jack which means I can now listen music because audacious supports jack. what about other stuff? 

I mean, forexample I cannot hear anything on youtube. becouse firefox does not try to send the sound to the jack - or something like that I assume. So I think, there must be a way that I can hear all the sound that my computer produce. (welcome sound, pidgin sounds, video sounds, game sounds etc...)

So that, I am searching for a way that I can direct the whole sound to the JACK which can send the sound to my firewire soundcard and to my speakers.

OR

What the hell is FFADO - Mixer? Is this problem have something to do with that? :) do I need to use jack always in order to have sound ? I am not going to produce something on ubuntu - I do it with Win. so All I need is to use my soundcard  as a regular soundcard :) 

I am now using an upgraded version of vanilla ubuntu to studio Karmic. 
Thanks.

---

### Post by cchhrriiss121212 on 2010-04-14
Firewire audio devices are only functional through jack and ffado (the firewire driver), so you can't hear everything through your card. You can hear video with jack, search for vlc + jack in synaptic to install the plugin, then select jack as the output in vlc preferences.

Maybe you should just unplug it when you are not using it and use your onboard sound.

---

### Post by nezurian on 2010-04-14
But what about the stuff about pulseaudio to jack - for example? 

I mean... I have been searching for the forums for a long time and what I get (if I did not misunderstand) that the the sound that uses pulseaudio can be directed to jack. But the explanations are not really helpful ( I cannot follow the steps because they're not for new versions of ubuntu, and &#305; have faced problems about dependencies etc...) so I cannot find my way through that. 

And this must be actually really simple - telling ubuntu that "just send the whole data that goes through pulseaudio, or alsa or whatever it is, to the jack. and let the jack handle all the other stuff"! 

I believe that this is possible. But I found nothing really helps to the people that cannot understand every word written.

---

### Post by cchhrriiss121212 on 2010-04-14
I've also seen packages/guides for pulse+jack, but have not been able to get it working myself. I gave up as I have a PCI card that works with alsa, so removing pulse works best for me. 

Every time I see it mentioned on the forums, its just to say that it is a pain to configure, or that it does not work at all.

> And this must be actually really simple - telling ubuntu that "just send the whole data that goes through pulseaudio, or alsa or whatever it is, to the jack. and let the jack handle all the other stuff"!
The thing to remember about jack is that it is designed for low latency audio work with specific audio programs, and not as an always on system wide server. I should also add that if you are not recording any music with ubuntu, then upgrading to studio won't give you any benefits.

---

### Post by nezurian on 2010-04-14
hmmm. So that, maybe there's something to do with FFADO. People **must** use their hardware with ubuntu or other linux distros. 

Whatever. Thank you for sharing your time and your concern.

---

### Post by shyseeker on 2010-05-22
I found how to play both things, jackd based apps and your normal alsa based ones, like youtube on browsers, movies and music ;)

following these instructions: [http://alsa.opensrc.org/index.php/Jack_(plugin](http://alsa.opensrc.org/index.php/Jack_(plugin))

I found that you just create this file:
```
~/.asoundrc
```

and put these lines there:
```

pcm.!default {
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

ctl.mixer0 {
    type hw
    card 0
}

```

log out -> log in

And Voila! your alsa apps will use jack whenever you start it, I personally use it for plugging my synthesizer to qsynth, and now I can listen to music on youtube at the same time or whatever.

Hope it helps!

---

### Post by karl.lensson on 2010-05-23
> **shyseeker said:**
> I found how to play both things, jackd based apps and your normal alsa based ones, like youtube on browsers, movies and music ;)

following these instructions: [http://alsa.opensrc.org/index.php/Jack_(plugin]("http://alsa.opensrc.org/index.php/Jack_%28plugin"))

I found that you just create this file:
```
~/.asoundrc
```and put these lines there:
```

pcm.!default {
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

ctl.mixer0 {
    type hw
    card 0
}

```log out -> log in

And Voila! your alsa apps will use jack whenever you start it, I personally use it for plugging my synthesizer to qsynth, and now I can listen to music on youtube at the same time or whatever.

Hope it helps!

If the link doesn't work it's because this thingy ) at the end of the link isn't recognised as part of the link.[http://alsa.opensrc.org/index.php/Jack_(plugin)]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29")

---

