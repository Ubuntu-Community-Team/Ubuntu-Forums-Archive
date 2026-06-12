---
title: "volume control weirdness"
date: 2009-11-01
forum: Multimedia Software
---

### Post by iamnotthemessiah on 2009-11-01
ive got a problem with the karmic volume control, its impossible to get the volume at the level i want, i can only choose between no sound and superloud. if i set thte output to 23% its very loud, and above 23% even louder naturally, but at 22% and below the sound is off

any ideas?

---

### Post by hades_6_6_6 on 2009-11-02
Same thing here (9.10 fresh install on Dell Inspiron 1501).
I use the Fn-keys to control the volume.
On the first 3 lower levels the sound seems to be disabled but from level 4 (and of course above) sounds comes out, but much too load.:(

---

### Post by Kushkah on 2009-11-02
I had the same problem, and after several hours of googling, this fixed it:

First, open a root browser (gksu nautilus) and navigate to /usr/share/pulseaudio/alsa-mixer/paths/
Then open all the analog-output.conf* files in gedit. As far as I could see only the first two (analog-output.conf and analog-output.conf.common for me) needed to be changed, but I did it for all the analog-output files just in case.

Anyway, hit ctrl + H (Replace) in gedit and replace all instances of 'volume = merge' with 'volume = ignore' (without the quotes). Do this for each output file. (Note that I did so many X restarts and regular reboots trying to get this fixed that I don't really remember when and where it was actually necessary, so feel free to throw one in here if you want ;) )

Next, in a terminal type alsamixer to bring up the volume controls and mess with the levels until you find what sounds best (up/down arrows to adjust, left/right to navigate in case anyone didn't know), I *think* it's best to leave Master at 100, and just adjust the PCM and LFE (that one might be system specific, not sure, still sorta new at this stuff lol).  Master at 100, PCM at 90 and LFE at 74 had no distortion or tinnyness for me so I left it at that.

Might need a reboot but you should be able to use your regular volume controls now without pulseaudio randomly jacking up your volume :)

Credit for the fix goes to Daniel Chen at [https://launchpad.net/~crimsun](https://launchpad.net/~crimsun).  Just wish it was easier to find lol. Good Luck!

Also, if your having the problem where your sound starts out muted like I was, do the replace thing again but this time replace 'switch = mute' with 'switch = on'.

---

### Post by mazz0 on 2009-11-02
Thanks Kashkah, I might try that (I have the same problem), but I'm concerned - are we losing some functionality by changing merge to ignore?

---

### Post by Kushkah on 2009-11-02
I could be wrong, but as I understood it the merge refers to pulseaudio applying its settings to alsamixer or whatever settings it uses, as changing the volume in the gnome panel with alsamixer open shows.  So unless it has some other function i'm not aware of it shouldn't affect anything.  

Also worth noting, the fix came from an [Ubuntu Audio Development Team]("https://launchpad.net/~ubuntu-audio-dev") member and was posted in the bug report, so it should be safe.

---

### Post by mazz0 on 2009-11-02
Ah, groovy.  Got the link for the bug report?

---

### Post by iamnotthemessiah on 2009-11-02
thanks, ill try this a bit later (watching a movie on the computer right now) or tomorrow and report back

---

### Post by Kushkah on 2009-11-02
Here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420578](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420578)

---

### Post by seamuso on 2009-11-02
I've had nothing but weirdness with karmic audio. Right now it seems to be locked and not spontaneously changing if I adjust the volume, but regardless ..

alsamixer .. set correct volumes for your tastes

sudo alsactl store .. to save those settings

sudo alsactl restore .. to restore your saved settings from asound.state, should carry over through reboots.

reboot .. all volume controls whacked out again, asound.state rewritten, working levels gone. Touch anything in sound settings, volume weirdness returns.

With the changes to the files in /usr/share/pulseaudio/alsa-mixer/paths I'm raising and lowering volume from the panel again and my alsa settings have lasted through a couple of reboots.

For the record, my weirdness was -

2 channel audio source, analog stereo setting, plays out of 5 channels. Mute the center channel and all audio mutes, mute LFE, all audio mutes (these 2 need to be a 0 for me to get left,right only). Set working levels in alsamixer, good 2 channel playback, touch teh volume control and all 5 speakers are on again.

I know it's in the device mapping and I know that my card is being mis-detected as an ALC1200 when in reality it's an ALC888 (per all previous versions of ubuntu + windows realtek info).

---

### Post by cyprys on 2009-11-02
Similar problem here but proposed solution (replacing "merge" with "ignore") doesn't work for me.

In my case the only thing volume control slider can do is muting the sound when it's all the way on the left. Any other position (from 1 to 100 %) the sound is at it's full loudness. At the same time Rhythmbox and Totem control volume perfectly.

Any ideas?

---

### Post by seamuso on 2009-11-02
> **cyprys said:**
> Similar problem here but proposed solution (replacing "merge" with "ignore") doesn't work for me.

In my case the only thing volume control slider can do is muting the sound when it's all the way on the left. Any other position (from 1 to 100 %) the sound is at it's full loudness. At the same time Rhythmbox and Totem control volume perfectly.

Any ideas?


I had to change the "merge" option to ignore in ALL of the output files to make it seem to act right (so far OK, hoping it sticks), run alsamixer to set my levels and reboot

---

### Post by hades_6_6_6 on 2009-11-02
Thanks Kashkah. I've followed your instructions and the volume manager behaves normally now.

---

### Post by cyprys on 2009-11-02
> **seamuso said:**
> (...) run alsamixer to set my levels and reboot

Also, after the most default upgrade I can think of, the alsamixer doesn't work:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

---

### Post by iamnotthemessiah on 2009-11-02
Kushkah
that worked for me, thanks a lot. didnt test extensively cos im off to bed but as far as i can tell its back to how it was in jaunty :D

---

### Post by monkeyKata on 2009-11-02
Just wanted to throw a question into the thread.

After upgrading to Karmic, my audio has been working fine except for one oddity: the main volume control no longer works at low levels.  I guess that's not too clear.  What I mean is that once I lower the volume to a few notches above 0% (say 12%) it mutes, whereas before it would get lower and lower and only mute at 0%.  So when I get down to 12% volume everything goes mute, and I no longer have the ability to adjust it at those low levels.

Anyone get this as well, and did this thread help fix it?

EDIT:  Doh!  I obviously skimmed the thread too quickly, as it addresses this very problem....

Excuse my redundancy.

---

### Post by Kushkah on 2009-11-02
Glad to see everyone's getting it working :)

> **cyprys said:**
> Also, after the most default upgrade I can think of alsamixer doesn't work:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Make sure your user is in both the plugdev and audio groups ( System > Administration > Users and Groups ).  Otherwise you might have to reinstall alsa.

---

### Post by monkeyKata on 2009-11-02
Hey Kushkah.

So I changed those 'volume = merge' entries to 'volume = ignore' as you suggested, but now things seem worse.

If I try to adjust the volume in Rhythmbox (not the master but it's own volume control) the program crashes.  Also my overall volume output is much much quieter.

I'm not sure what the deal is.

---

### Post by Kushkah on 2009-11-02
Did you adjust your PCM volume in alsamixer?  Mine had to be pretty high to get much more than a whisper.

I'm not having any problems with Rhythmbox though, could you adjust the volume ok before you made the changes?

---

### Post by SouthOfHell on 2009-11-02
> **iamnotthemessiah said:**
> ive got a problem with the karmic volume control, its impossible to get the volume at the level i want, i can only choose between no sound and superloud. if i set thte output to 23% its very loud, and above 23% even louder naturally, but at 22% and below the sound is off

any ideas?

Weird man, I have the exact same problem, pretty irritating.

---

### Post by rocky462 on 2009-11-02
[This.]("http://lmgtfy.com/?q=ubuntu+karmic+volume+problem")  First result is a forum post about this very problem, in it is a link to the bug report with the solution.  Just sayin..

---

### Post by monkeyKata on 2009-11-03
> **Kushkah said:**
> Did you adjust your PCM volume in alsamixer?  Mine had to be pretty high to get much more than a whisper.

So I did that and it worked.  PCM was actually about all the way up (98%) and Master needed to be raised.  It's now at 100 and the volume control again gives the full range.  I thought the volume control applet just raised the master setting, but I guess it's different.  And rhythmbox isn't crashing anymore.  I'm not sure why it did, or why I only checked alsamixer *before* the reboot.  

Thanks for the fix.

---

### Post by iamnotthemessiah on 2009-11-03
update: as mentioned followed Kushkah's advice which worked perfectly however i just did a reboot and the login sound was so loud that pictures fell down from the wall...

---

### Post by Kushkah on 2009-11-03
> **iamnotthemessiah said:**
> update: as mentioned followed Kushkah's advice which worked perfectly however i just did a reboot and the login sound was so loud that pictures fell down from the wall...

This was a bug with gdm (maybe alsa?) in Jaunty and I guess it's still around.  I have it too but didn't realize until you mentioned it lol.  There's a fix proposed in the comments of the bug report here: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/378325](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/378325) but it didn't have any effect on my system unfortunately.

Update: (Edit: This might disable more than just your login sound, i'm not sure, I have everything else disabled anyway.)  If you'd rather have no login sound than an abnormally loud one, hit Alt+F2 and run ```
gconf-editor
``` then go to /desktop/gnome/sound/ and uncheck the 'event_sounds' box.  Not ideal but, at least for me, it's a better option.

---

### Post by iamnotthemessiah on 2009-11-03
Kushkah, thanks for the advice, ill try it. not sure when tho as ive also got severe 3g broadband trouble (as documented here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all) ) and im not keen on rebooting as my 3g usb modem is actually working at the moment. karmic really is terrible in many ways for me, ive been lucky not had any probs since breezy but in karmic its all piling up

---

### Post by IAmNoodle on 2009-11-05
> **Kushkah said:**
> I had the same problem, and after several hours of googling, this fixed it:

**First, open a root browser (gksu nautilus)** 

Please forgive my lack of understanding, but how would I do that?

---

### Post by Kushkah on 2009-11-05
> **IAmNoodle said:**
> Please forgive my lack of understanding, but how would I do that?

Hit Alt+F2 to bring up the Run Application window or alternatively you can run it in a terminal.

---

### Post by IAmNoodle on 2009-11-05
Cheers. That got it up.

> **cyprys said:**
> Also, after the most default upgrade I can think of alsamixer doesn't work:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

However, I'm suffering from this problem now too, and no amount of uninstalling/reinstalling is making any difference. I'm also in the user groups mentioned. Although I've got a feeling my problem is unrelated, since moving the volume slider literally makes no difference to the low level I have currently

---

### Post by cyprys on 2009-11-06
None of your ideas worked... But! [thread=1310170]My workaround[/thread].

---

### Post by SR_ELPIRATA on 2009-11-06
This new sound preferences is so strange to use that I'm still wondering why they would change the normal mixer for this. I've been having many sound issues and right before checking this thread I noticed that on my 5.1 setup... the subwoofer slider causes the soundcard to make this chirping noise that makes it impossible to listen to music unless at certain levels.

Noticed, also, that the output volume (on top) can do more and still its like limited there. But when the sub is set to 100 then the output volume can go higher, and as you turn the volume down, so does the sub setting, and then makes the noise to return :(

I'm going to try the suggestion listed here as well, cause I'm this close to returning to 8.10 (had some interface problems with 9.04) cause sound is almost flawless there.

One thing that keeps confusing me, too, is that we're using pulseaudio... and in 8.10 and 9.04 the reported sound driver on my system said HD ATI SB (Alsa Mixer), which... doh, confuses me. Now on 9.10 I can see I'm using the HDA-Intel and I'm wondering if this is part of the problems I'm having.

Nevertheless, I'm going to test the suggestion here and report back in a few.

ELP

PS: Nope, it doenst solve my problems :( All I can see is that whenever I get the sub to the max and try and move the output to the max as well, the 'noise' disappears and doesnt come back after the next restart (or if I set the sub back to zero)). Oh well, I guess this is it... back to 8.10.

---

### Post by rescyou on 2009-11-08
I had a similar problem and this worked for me:

Open -> gconf-editor
Goto -> Apps –> gnome_settings_daemon –> volume_step

Change the Volume Step to something smaller, mine was set super high for some reason so I changed it to "1" and now it works much better.

s.

---

### Post by niko3d on 2009-11-13
Thanks Kushkah and everyone else involved with the audio fix :) Works a treat on my dell xps m1710.

---

### Post by TomBull on 2009-11-13
How can anybody have 30 replies and 1300 views and only posted 1 minute ago?

---

