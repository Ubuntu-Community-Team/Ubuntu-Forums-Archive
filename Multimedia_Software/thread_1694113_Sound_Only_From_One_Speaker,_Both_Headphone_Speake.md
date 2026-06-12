---
title: "Sound Only From One Speaker, Both Headphone Speakers Work"
date: 2011-02-23
forum: Multimedia Software
---

### Post by dv310p3r on 2011-02-23
Ok, I've looked up and down and I've tried a million and a half things. Please, any help would be awesome.

Basically I only get sound out of my right speaker on my laptop. If I plug in my headphones they work fine.

Any suggestions. What information do you need from me?

Thanks,

---

### Post by amin2084 on 2011-02-23
i think one of your speaker is fail and not working..

---

### Post by dv310p3r on 2011-02-23
> **amin2084 said:**
> i think one of your speaker is fail and not working..

Nah, it worked fine in windows.

Something I noticed. It seems as if whatever outputs sound is trying to output both channels trough the one speaker. When I open alsa mixer if I play with the balance, you can hear more sound when you're in the middle and less sound when your to either end of the balance.

---

### Post by dv310p3r on 2011-02-23
I thought this might help also. It's a report of my audio hardware.

[AUDIO HARDWARE REPORT]("http://www.alsa-project.org/db/?f=06ed3e30decaa33c55303a6dbb08894e2112daa6")

---

### Post by dv310p3r on 2011-02-24
I upgraded my Alsa driver or software or whatever it is, to version .23 using this guide:

[UPGRADE ALSA]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Still same issue. Again, it's very weird, it's almost like my system thinks there's only one speaker. Both channels are played through that one speaker. 

There's got to be a way to see the speakers and force it to use both instead of one. 

PLEASE HELP

---

### Post by Mojo McCracken on 2011-02-24
One solution *could* be to downmix your music to mono. That would at least determine whether or not the speaker actually recieves any signal. Try this in the terminal:

```
mplayer -af pan=1:0.5:0.5 -channels 1 http://interdisco.net/mp3/id15/id15_04_christian_walt-permanent_hangover.mp3
```

Sound from both speakers?

PS: You may need to install MPlayer to test this. To do so simply type the following in the terminal (then try the command above):

```
sudo apt-get install mplayer
```

And for the love of God, **please check your cables.**

---

### Post by dv310p3r on 2011-02-24
Only sound from the one speaker still.

Also, it's a laptop, really no speakers to check.

Thanks for the reply though.

---

### Post by dv310p3r on 2011-02-24
Ok, I think I got it. I've got sound coming from both speakers now. WOO HOO! 

Here's what I did.

in the /etc/modprobe.d/alsa-base.conf file I changed the following line:
 options snd-hda-intel model=5stack
to 
 options snd-hda-intel model=targa-dig

Now, I got the idea to do this from following most of the following instructions:
 [Ubuntu Sound Issues Troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

I couldn't find the codec that I had inside the ALSA-Configuration.txt file that was associated with the .23 version of the ALSA I was using. So in looking around within that same directory, (the one ALSA-Configuration.txt was in), I saw one that said HD-AUDIO-MODELS.txt. I went in there and found my particular codec. So I changed the line above to the only one I could find that had my computer model, MSI.

And Voila, I haven't really checked to see if the HDMI audio output is working, but I'll try when I get home and then I'll let you know in case anyone actually cares.

---

