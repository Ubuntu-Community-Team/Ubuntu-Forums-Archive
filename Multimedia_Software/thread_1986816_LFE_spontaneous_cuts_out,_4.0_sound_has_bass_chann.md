---
title: "LFE spontaneous cuts out, 4.0 sound has bass channel, high pitched squeals"
date: 2012-05-25
forum: Multimedia Software
---

### Post by AbeFM on 2012-05-25
Posted this to not a single review or response from anyone other than other folks who've been asking questions and haven't even gotten a "dude, I have no idea, you're f*#ked I guess, buy a mac"... so perhaps if I start a new thread, someone will at least READ an issue that's kept me from using my projector, HTPC, or sound system for over a month. If you can help, tell me how to help myself, or know enough to tell me it's just something I'll have to live with or install windows to get around... please do so.
----------------

I've given a quick look at the guides in this thread, if you think I need to run through them to give you more info, say the word and I'll run them... But perhaps something will sound familiar enough to you.

My system started as 10.04 and has followed the routine upgrades to 12.04. The system was built for this, a intel i3 with a Zotac H67ITX-C-E (H67 chipset). I've done several fresh installs, and always have the same issue:

After some indeterminate amount of time/interaction/sounds, I'll find the LFE (the .1 from my 5.1) channel no longer playing. Going into the sound controls and selecting most anything (even a non- bass channel system like 4.0) will instantly find the sub-woofer working again. As you can imagine, the ultimate home theater isn't that great when I have to get up and tweak the settings twice a night.

Anyway, now on the fresh 12.04 install, I'm also getting very high frequency noise, like when WINE used to have ALSA issues on my other desktop. I could believe it to be bit shifting on the outputs - least significant bits making a high frequency output on the highest volumes - but it could be something else entirely. 

This kinda sneaks in, and sometimes muting and unmuting fixes it. If not, even running alsamixer won't fix it. Interestingly, switching to 4.0 (which gives me 4.1 sound) does fix it, going back to 5.1 restores everything.

Does anyone have any suggestions? This issue has been going on for years, but as it was only dropping base, I didn't care. Now that it's endangering my speakers and my relationships, I need to do something. It seems to happen after a couple hours of listening to music.

--> If this has been covered and I missed it, please point me to where I can read up on it. Thank you.

THANKS!!!
-Abe.
__________
System Summary:
Ubuntu 12.04 (clean install, issues present before)
Intel i3 2600t
Zotac H67ITX-C-E (H67 chipset, 2nd motherboard, same symptoms)
5.1 sound hooked up through analog outs

The closest I could find was [http://www.thinkwiki.org/wiki/Proble...audio_clipping](http://www.thinkwiki.org/wiki/Proble...audio_clipping) about Z68 boards, but it's not really clipping per se.

---

### Post by AbeFM on 2012-07-29
Here's a copy of the sound itself.
[https://docs.google.com/open?id=0B-zph_ei3gtGYVppTlZZay1UUVk](https://docs.google.com/open?id=0B-zph_ei3gtGYVppTlZZay1UUVk)
It plays for 2/3 of the file then I switch the audio to 4.0 then back to 5.1 in the GUI.


 I've opened it as a bug at [https://bugs.launchpad.net/bugs/1004593](https://bugs.launchpad.net/bugs/1004593) as well.

---

### Post by AbeFM on 2012-07-29
On another forum, someone linked a video with the same issue:

> I have sandy bridge asrock p67 extreme4, with integrated audio. The audio works but 3-4 times in a day i receive a very noise audio. I made a video for help you to understand the problem.

[http://youtu.be/IBeVKkmQB3Y](http://youtu.be/IBeVKkmQB3Y)

For stop the noise i need to stop the playback and wait for about 20 seconds. I receive this problem when i listen music or watch video.

I don't know what i need to do for solve it. I hope anyone can help me.

This is the output of aplay -l

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0 

That's a P67 verses my H67... Maybe it's a SandyBridge issue?

---

