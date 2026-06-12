---
title: "BBC iPlayer frustrations"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Phil _Taylor on 2008-11-15
I created an Ubutu 8.10 machine a couple of weeks ago, my first ever Linux machine, and have been very impressed so far.  However, I have become increasingly frustrated with one aspect.  I am a regular user of the BBC&#8217;s Web site and in particular the BBC iPlayer.  When I use my Ubuntu machine to visit the BBC iPlayer site I can see the video, and the quality looks very good, however, I get no sound.  The machine I have built is a Dell 270 SF desktop with an external sound card. Can anybody help?  Indecently, I can play MP3s and can hear them OK.  I can also listen to BBC Podcasts without a problem.

---

### Post by Namtabmai on 2008-11-15
Hi,

The BBC iPlayer is really just another flash based site, so the question is, can you hear sounds in other flash sites?

Try going to youtube and watching a video there to see if you hear any sounds.

If you can I'm very flummoxed, but my bet is that you won't.

The problem stems from the fact Ubuntu now includes pulseaudio by default. Pulse audio is great but unfortunately a few applications such as flash, can still have trouble with it. When this happens either the flash will get exclusive access to the sound card and play sounds but nothing else on your system will be able to. Or, as in this case, pulse audio has access to your sound card meaning flash can't, so it won't play any sounds.

I thought flash had been fixed in recent packages, so first off make sure you system is upto date.

System->Administration->Synaptic Package Manager

Then hit the reload button, then after that's reloaded, "Mark all upgrade", then hit "Apply".

If you're still no getting any sounds, try closing down all other applications and the starting firefox (if you already had firefox open, close and reopen). Then try youtube, and see if you get any sound.

---

### Post by aeiah on 2008-11-15
there should be tutorials for getting pulseaudio to play nice with flash and other audio streams and such on this forum so if what the poster above suggested doesnt work, you can look there. there are also tutorials for switching back to ALSA, which ubuntu used to use before switching the pulse audio and this works fine. i suggest updating flash or fixing pulse before switching to alsa as it could go wrong.

---

