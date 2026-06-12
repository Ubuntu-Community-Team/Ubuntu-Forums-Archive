---
title: "Amarok/firefox/flash sound problem"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by radicaledward on 2008-03-04
I recently just switched to an external usb sound card (behringer uca202). Currently, while running amarok and firefox at the same time, sound from amarok heads to my usb sound card and flash sounds go through the internal speakers. I've tried any of the countless fixes for similar problems; editing the firefoxrc file does nothing; messing with asoundconf does not help.

Any help is appreciated.

---

### Post by radicaledward on 2008-03-09
Bump.

Again, any help is appreciated.

---

### Post by eznet on 2008-05-07
Yea, I don't know what the problem is with sound in Hardy, but I think it has something to do with the new adoption of Pulse.  When I am running Firefox(Flash) and load any audio application, it either hangs (lack of exception handling in the programming) or throws an error (good programmer) - usually pertaining to the audio system being inaccessible or something.  For me, I am limited to one audio app at a time - which is kinda lame when you want to listen to music and surf the internet...

-Matt

---

### Post by r!ots on 2008-05-08
Same thing with me:
Whenever I start a flash video in firefox while at the same time running amarok, the video starts without any sound and hangs after 10 seconds. If I do a refresh of the site or any other action in firefox after that, it freezes and has to be forced quit and restarted.
Is there already any solution out there? I didn't find anything when searching the forums.
It's actually a very annoying bug and probably the biggest flaw in Hardy, cause apart from that I really like it and it works just great for me. Once again it has been great work by the developers. Big thumbs up.

I just did a quick google search and actually the bug has already been filed ([https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470")) and there are some suggestions on how to solve it. I will check them out later and let you know.

Oh and btw, altough it's totally off-topic: does suspend/hibernate work for you? It doesn't for me, editing */etc/default/acpi-support* and changing the following lines to ```

      SAVE_VBE_STATE=false
      POST_VIDEO=false
```
which worked for me in Gutsy, didn't do anything. Any ideas?

---

### Post by r!ots on 2008-05-08
Alright, it seems as if I got it working doing  the following:
I reinstalled pulseaudio and libflashplugin support (which wasn't even installed): 
```
sudo apt-get install --reinstall pulseaudio libflashsupport

```
and then changed everything to pulseaudio in "system->preferences->audio settings".
This advice was posted [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470/comments/11").
Now amarok and flash run at the same time and everything seems to be fine.
Hope this helps.

---

### Post by eznet on 2008-05-11
SAAAWEEET!  You da man.  That fixed it for me, which is rad!  Going to to it on my desktop now :)
BTW, no, suspend and hibernate do not work for me either.  I am using a DV6000T and have not found any tips that will get it to work...

**UPDATE:** On my desktop I set everything to PulseAudio in my sound settings without reinstalling the sound server or the 'flashlib' and all is well in the world... glad to see such a simple fix resolves the issues.  Thanks again.

-Matt

---

### Post by trhodes on 2008-05-12
Thanks r!ot. Worked like a charm. Been having this problem ever since I upgraded. Glad to get it fixed!

---

### Post by c4mden on 2008-06-26
fixed my problems too.  thanks!

---

### Post by PC_load_letter on 2008-07-21
Unfortunately, this does not fix the problem if you are using ALSA. I despise Pulseaudio, and have been using ALSA on my new laptop w/ Hardy installed. I can NOT watch flash videos (on ffox or Opera) while Amarok is playing.
This is very disappointing given that I do not have this problem on my Feisty desktop. Any ideas?

---

