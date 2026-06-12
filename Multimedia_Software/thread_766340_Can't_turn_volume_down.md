---
title: "Can't turn volume down"
date: 2008-04-25
forum: Multimedia Software
---

### Post by romansky on 2008-04-25
Installed 8.04 yesterday, and most things seem to work well enough. My only problem though, is that I'm unable to adjust the volume, it just stays on 100%. When I try to slide the volum button downwards, it just goes back up again to 100%.

Maybe not such a huge problem, but the loud log in tune annoys my wife :), and I didn't have this problem in 7.10.

---

### Post by kpkeerthi on 2008-04-25
Go to System -> Preference -> Sound and select Master Volume (and/or any other channels you want to be controlled with the slider or multimedia keys)

---

### Post by romansky on 2008-04-25
> **kpkeerthi said:**
> Go to System -> Preference -> Sound and select Master Volume (and/or any other channels you want to be controlled with the slider or multimedia keys)

Hi, thanks for the reply.

I am aware of this configuration tool. The problem is, however, that when I try to move the slider down, it goes straight back to 100% by it self. I can adjust the volume within each sound application, such as last.fm, by I just can't make the slider on PCM-2 on my OSS mixer (Realtek ALC861) go down. Any hints?

---

### Post by romansky on 2008-04-26
You see, I can mute the volume, but I can't adjust it. It's just either 100% or 0%. I'd like ii to be around 30%, I think :-)

---

### Post by Erikhh on 2008-04-27
I have exactely the same problem.

When I, in a terminal, writes "alsamixer", I get the message:

alsamixer: function snd_mixer_load failed: No such file or directory

I have found a way of modulating the sound:

When PCM-2 is set to 100% (there is only the possiblity of 100% or 0%), then I can go into Totem and regulate the sound from the soundbutton there. But it should not be necessary to go that way.

---

### Post by romansky on 2008-04-27
> **Erikhh said:**
> I have exactely the same problem.

When I, in a terminal, writes "alsamixer", I get the message:

alsamixer: function snd_mixer_load failed: No such file or directory

I have found a way of modulating the sound:

When PCM-2 is set to 100% (there is only the possiblity of 100% or 0%), then I can go into Totem and regulate the sound from the soundbutton there. But it should not be necessary to go that way.

Seems like the same problem. I, too, get the same message upon writing "alsamixer" in the terminal. I've tried reinstalling all the alsa and pulseaudio related packages, but that didn't do anything either.

It is possible to adjust the volume within every application, such as totem and others. But it is a bit impractical, especially when streaming media over the net. I have to make sure to turn the volume down every time I open e.g. a flash movie, or else I'm afraid my speakers will blow.

It seems, then, that the problem is alsa-related. Anyone have any clues as to a possible solution?

---

### Post by mat087 on 2008-04-27
I've got the same problem, I fix it doing this.

> 
This is already fixed [http://people.ubuntu.com/~ogasawara/hardy-buglist.html](http://people.ubuntu.com/~ogasawara/hardy-buglist.html)

If you don't want for the updates to get uploaded to repositories just do:

sudo apt-get install module-assistant

module-assistant a-i alsa-source

reload the sound modules (or restart) and it should be working.


[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382/comments/36](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382/comments/36)

And I added in "/etc/modprobe.d/alsa-base"

```
options snd-hda-intel model=6stack-dig
```


Mathieu

---

### Post by brunods on 2008-04-27
same problem here. And plus: in the Sound Settings, the option to choose alsa's master volume isn't there anymore! I mean, I can "sound test" clicking the "test" buttons with ALSA selected. But then there are no devices registered under ALSA in the combobox!

---

### Post by romansky on 2008-04-27
> **mat087 said:**
> I've got the same problem, I fix it doing this.



[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382/comments/36](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382/comments/36)

And I added in "/etc/modprobe.d/alsa-base"

```
options snd-hda-intel model=6stack-dig
```


Mathieu

OK, something changed, but not necesseraly to the better. This is what I did (whilst in Terminal):
1. sudo apt-get install module-assistant
2. sudo module-assistant a-i alsa-source
3. sudo pico /etc/modprobe.d/alsa-base
4. Added "options snd-hda-intel model=6stack-dig" at the end of the config file.

When I restart I can adjust the volume. Hooray! There are some nasty side effects though. Volume works in Rythmbox and Songbird. However, in Last.fm and in Flash content in firefox, the sound has disappeared all together. Other embedded media in Firefox plays with sound (wmv, mov, etc), but not flash. Also, it's a great loss not to have last.fm in the background. What has happened?

---

### Post by romansky on 2008-04-27
OK, so I solved it thanks to another thread about flash problems. This is what I did, in case others have the same problem:

1. sudo apt-get install module-assistant
2. sudo module-assistant a-i alsa-source
3. sudo pico /etc/modprobe.d/alsa-base
4. Added "options snd-hda-intel model=6stack-dig" at the end of the config file.
5. Restart machine
6. sudo apt-get install libflashsupport

Now, most things seem to work. I don't know exactly what I've done here, though...

---

### Post by tikkun on 2008-04-28
> **romansky said:**
> OK, so I solved it thanks to another thread about flash problems. This is what I did, in case others have the same problem:

1. sudo apt-get install module-assistant
2. sudo module-assistant a-i alsa-source
3. sudo pico /etc/modprobe.d/alsa-base
4. Added "options snd-hda-intel model=6stack-dig" at the end of the config file.
5. Restart machine
6. sudo apt-get install libflashsupport

Now, most things seem to work. I don't know exactly what I've done here, though...

The steps above fixed the problem for me. I'm running an EEE PC 701 for reference.

---

### Post by orawax on 2008-04-29
> **romansky said:**
> OK, something changed, but not necesseraly to the better. This is what I did (whilst in Terminal):
1. sudo apt-get install module-assistant
2. sudo module-assistant a-i alsa-source
3. sudo pico /etc/modprobe.d/alsa-base
4. Added "options snd-hda-intel model=6stack-dig" at the end of the config file.

I had the same problem after upgrading from Gutsy to Heron: no alsamixer, and oss-mixer only let choose between 100% (full) or 0% (mute). I followed this advice, now alsamixer is available, I can also choose it in volume-applet and every switch works nicely. The only problem is that the system is **totally mute**. I can hear the buzzing noise when I turn up the CD volume, but nothing comes out from the software side. :icon_frown:

I'd rather revert back to the old situation and remain waiting for the issue to be solved through repos. How to?

realtek / intel

---

### Post by mat087 on 2008-04-29
> **orawax said:**
> I had the same problem after upgrading from Gutsy to Heron: no alsamixer, and oss-mixer only let choose between 100% (full) or 0% (mute). I followed this advice, now alsamixer is available, I can also choose it in volume-applet and every switch works nicely. The only problem is that the system is **totally mute**. I can hear the buzzing noise when I turn up the CD volume, but nothing comes out from the software side. :icon_frown:

I'd rather revert back to the old situation and remain waiting for the issue to be solved through repos. How to?

realtek / intel

My sound was mute when I did this procedure. The solution was to restart "alsa" or something else. I just did a reboot. Try it.

Or maybe you should put something else instead of "6stack-dig" in "options snd-hda-intel model=6stack-dig". Try googling...


Mathieu

---

### Post by orawax on 2008-04-30
> **mat087 said:**
> Or maybe you should put something else instead of "6stack-dig" in "options snd-hda-intel model=6stack-dig". Try googling...

Found this: ["hda Intel soundcard solution"](http://ubuntuforums.org/showthread.php?t=314383), might help some with intel hda card but not me. I tried 6stack-dig, 3stack, 3stack-dig, asus-laptop, asus, laptop, fujitsu, ref, auto, laptop-eapd. None works. Some give the test sound through ALC861 Analog -device, but nothing else. Others don't work at all.

Wild 1st of May everyone!

---

### Post by orawax on 2008-05-07
FYI: The latest Linux updates brought the sounds back, but now I'm back where I began: no alsamixer available, only OSS.

---

### Post by romansky on 2008-05-09
I actually ended up wiping out hardy and reinstalling gutsy because of this sound thing, plus a couple of other annoying things (such as difficulties while trying to install VMware). I'll wait a few weeks, hoping there will be updates fixing thse problems, and the I'll reinstall hardy.

---

