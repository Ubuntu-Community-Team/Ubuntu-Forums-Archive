---
title: "Turtle Beach Montego. Weird issues."
date: 2008-08-04
forum: Multimedia Software
---

### Post by Roasted on 2008-08-04
Guys, I'm fuming. I'm absolutely fuming. I bought a SIIG SoundWave 7.1 with a CMedia chipset, supposedly supported completely by Alsa. Of course, I run into trouble. It only turned on 50% of the time, the other 50% I had zero audio. So I'd have to reboot to regain it.

I returned it. Two days after I return it, somebody posts on here OMG I LOVE THIS CARD IT WORKED SO GREAT! Wow, I just returned it. And had problems. Wow.

Now I get this Turtle Beach Montego... and supposedly it works 100% out of box. K, great, so I dump 62 dollars and get it shipped to my place from Newegg.

I just installed it. When it boots up, I hear audio. After I boot, things freeze. When I open sys-pref-sound, it locks up after it loads the screen halfway, so I see a black box for the sound settings.

I opened Amarok and played a song. I heard audio great. Okay, so I figured I'd shut off Amarok and adjust alsamixer. Amarok shut off, but the bar for it in the lower taskbar froze to the taskbar itself... I did a killall amarok. "No process killed." WTF? 

Secondly, my audio is pretty quiet. Nothing is muted, and PCM and Master are 100%, and it's significantly quieter than the SIIG was, and the SIIG and this Montego I got have identical specifications.

I don't even know why I'm typing this. I'm so fed up with the weird issues I've been having (I also had the freezing problem with Amarok I spoke above with Frostwire as well) that I'm just going to reinstall. Not even patient enough to wait for a response.

But does anybody have any input as to what the problem may be? I'd love to hear some sort of constructive ideas... before I lose it. :mad::mad::mad::mad::mad:

---

### Post by Roasted on 2008-08-04
Okay, I reinstalled. Everything seemed good. I started to think that the Montego was quieter than the onboard card, which I didn't expect. So I thought, oh hey, it's re-enable the onboard card in bios and run that and see how it is so I can have more of a direct comparison... sweet!

I enabled the onboard card in BIOS. Booted into Ubuntu. Now, everything freezes. Synaptic won't open, my sound preferences opens halfway and gives me a black box without any options.

Okay, fine. Let's backtrack... so I went back to BIOS, de-activated my onboard card, and plugged my speakers back into the Montego PCI card. K, great. Back to where I started. Everything should be good now. Right?

Nope.

I also installed esound, which according to another thread sounded like a decent idea. It helps with certain sound issues, so I figured I'd try my luck. Was this a bad idea?

Now I don't know what to do. I have no idea how to even get my system running again. Someone help before I do something crazy like installing XP as my main OS...

EDIT again.

Hey! Reinstalled again just to get the system running. Installed medibuntu packages. Put in a live concert DVD, maxed out my speakers, system volume, and pcm... it's not "quiet" but it's certainly not as booming loud as it was with my onboard audio. I'm pretty disappointed. 

Help... !!

---

### Post by motang on 2008-08-05
Are you running on 32bit or 64bit Hardy? As far as I know they totally differnt beasts and that would be one of the reasons, as ALSA might not have 64bit drivers.

---

### Post by Roasted on 2008-08-05
My appreciation goes out to you, sir. I did not think of that at the time of installation that I was indeed running the 64 bit disc. 

I'll give 32 bit a shot when I get home and see if my mind can be laid to rest and my ears can be blown away.

:guitar:

---

### Post by Roasted on 2008-08-05
Bingo...

32 bit install did the trick.

I guess 64 bit Alsa support on this particular chipset just isn't that stable yet. Two cards, same chipset, same specs, both yielded same results in 64 bit Ubuntu.

SIIG SoundWave 7.1 PCI
Turtle Beach Montego 7.1 PCI

So anyway, I guess this mystery is solved.

However, I have a question. Where on the Alsa site (or anywhere in general) can I find particular information about Alsa and 64 bit driver support? I'm curious to read up on this stuff and see where it's at.

:guitar::guitar::guitar::guitar::guitar:

---

