---
title: "MP3 quality problem (codec?)"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by Jhonbus on 2006-11-24
Hi, I've installed Edgy pretty recently, and I've got a problem with my mp3 playback. In either Rhythmbox or the standard Movie Player app, the sound quality in some certain mp3s is shockingly bad, with an awful rumbling scrumpling sound like really heavy distortion. However when I play the same files with VLC they sound perfect. Am I right in assuming this is a codec issue and that VLC is using another codec to the other two apps?

If so, how might I get Rhythmbox to use whatever codec VLC is using? As you might be able to tell I'm a bit of a Linux noob.

Thanks a lot
John

---

### Post by Jhonbus on 2006-11-25
Anybody have any ideas? (bump bump :))

---

### Post by pay on 2006-11-25
You can install most of the codecs with this command ```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

---

### Post by Jhonbus on 2006-11-26
No luck, I'm afraid. I have those codecs installed already. There must be something on my system capable of playing the files properly since VLC can do it... I just have no idea why or how to get the quality VLC is giving me from Rhythmbox. :(

---

### Post by Jhonbus on 2006-11-26
I think it's just happening with VBR mp3s, someone else seemed to be having the same problem here: [http://ubuntuforums.org/showthread.php?t=218690&highlight=vbr](http://ubuntuforums.org/showthread.php?t=218690&highlight=vbr)

Looks like nobody was able to solve it, though :(

---

### Post by DarkDead on 2006-11-26
Hi. I've got the same problem but mp3s also sound bad in VLC. (Jhonbus have you checked carefully the VLC issue?). It only happens with VBRs, CBRs work perfectly.
I'm using Edgy and gstreamer0.10-plugins-ugly. I've also tried the "bad" set and gstreamer0.10-fluendo-mp3, however they have the same problem.
Are there any codecs or music players I should try?
Can anyone without this problem post what is using (if different)?

---

### Post by Jhonbus on 2006-11-26
The audio definitely works fine in VLC, and it also works fine in every other sound-playing app I have tried. Only Rhythmbox and Totem movie player have this weird distorted sound.

---

### Post by Jhonbus on 2006-11-27
I have now fixed the problem. I narrowed it down to apps using the GStreamer plugins, and from there, by installing and uninstalling various GStreamer plugin packages, found the culprit to be the Fluendo mp3 decoder plugin. Once I uninstalled that, but still had all the other plugins installed, the problem was fixed.

---

### Post by galv on 2006-12-03
> **Jhonbus said:**
> I have now fixed the problem. I narrowed it down to apps using the GStreamer plugins, and from there, by installing and uninstalling various GStreamer plugin packages, found the culprit to be the Fluendo mp3 decoder plugin. Once I uninstalled that, but still had all the other plugins installed, the problem was fixed.

Just done that, apparently there is no problem any more, but further testing is necessary. Thanks :D

---

### Post by JackosKing on 2006-12-05
Yes it's better, but the sound is always a little bit worst than on os X or Windows.
Maybe due to the codecs quality?

---

### Post by DarkDead on 2006-12-27
I still got the problem. I didn't have the fluendo package installed only the ugly. However I tried to install it and remove completely (because I had tried it before). Nothing happened, I continue with a bad quality in MP3 files.

---

### Post by imon9 on 2007-01-17
i am not 100% positive this can help, but uninstall your mixer software and installing other one might help...in my case, i have a Realtek AC 97 soundcard build-in with my twinhead laptop (nevermind if u never heard of it)....as i was saying, i tried ALSAmixer, xfce-mixer, gnome mixer but all somund bad, but when i changed to QAMix, all went to nice normal sound, go try your luck...

my mic however is currently not functional after changing mixer, so be aware of the possible problem with mic recoding for now..

if this workes,  please post a reply..and if it is not too much of toruble, please private massage me too...

i cant keep track where i answer these treads in the forums, so i can't check back wether it is working, but if this solve the problem, i want to write an article for the rest fo the ubuntu commmunity to know it... (and port it in the forum, in hope it can help others)

---

### Post by imon9 on 2007-01-17
i update ALSA and the mic start working flawlessly. Previously, with other mixer, my mic will be hard over my speaker ALL THE TIME no matter how i set to mute it.

Now, it record my sound, but will not echo it over the speaker which is PERFECT.

so, i think changing Mixer software INDEED wll help to fix those bad quality sound...

For other who it didn;t solve it, try update your ALSA driver to the later ones (ALSA 14 RC2, at this moment) and use ALSA instead of OSS or other mechanism for playback... ESD is old sound driver, so it might be the cause of problem if ur machine use it as default

---

### Post by mruncieman on 2007-03-03
I just wanted to add to this thread as I was having a problem with distorted MP3 playback also.  The suggestion above about removing the gstreamer0.10-fluendo-mp3 worked for me.  All my mp3s are playing back perfectly now.

Thanks!

---

### Post by tisk on 2007-03-08
yes, thanks very much, it fixed the very annoying bumpy background sound in some vbr files in rhythmbox :)

---

### Post by Webspot on 2007-03-19
uninstalling the fluendo mp3 plugin and replacing with the bad one help perfectly! Great! Is there any cases where it would be better to have the fluendo plugin enabled. Or is it just pointless? Should the bad plugin be automatically enabled on install?

---

### Post by hotani on 2007-03-21
I was having the same problem and it has been driving me nuts, thanks for the fix.

---

### Post by SmartyPants on 2007-03-28
(linux n00b warning :P)

just installed ubuntu two days ago. today I tried to play some mp3s, couldn't because rhythmbox was missing some plugins or something, I dug around and bumped into gstreamer fluendo mp3 so i installed that.  So now i can play mp3s but as you people said, the quality leaves much to be desired...

now, if I uninstall the fluendo plugin, I would go back to the world without mp3s right?  :( what's original mp3 codec/plugin that you guys are using?

EDIT: btw, there aren't any snaps, crackles, or pops with playback, it just sounds much worse than winamp under windows.

---

### Post by hotani on 2007-03-29
Nope, you can safely uninstall fluendo and still have mp3 playback. I'm not sure what the story is there, but it works. Go into synaptic, seek and destroy. :D

---

### Post by davidgarcin on 2007-04-07
I had the same problems as above, but didn't have the fluendo codec installed.  Instead, I went to System -> Preferences -> Sound and changed all my output devices to ALSA (they were on auto before).  Voila, all better.  (kudos to talbain for discovering this in another thread: [http://ubuntuforums.org/showthread.php?t=218690&highlight=vbr](http://ubuntuforums.org/showthread.php?t=218690&highlight=vbr))

---

### Post by davidgarcin on 2007-04-07
it also helps to turn down the system volume to 85 % or so

---

### Post by Badmonkey005 on 2007-04-08
Just wanted to thank *Pay* for his first reply. My MP3 codec wouldn't work at all (or was never there? I'm new to Ubuntu) and the command you gave got my music up and running.

Thanks.

---

