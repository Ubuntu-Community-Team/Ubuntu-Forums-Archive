---
title: "What keeps Turning Down the PCM Volume? Can I Stop this Annoying Behaviour?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-02-03
Hi. This has been happening since an upgrade or two ago, and while I am somewhat used to it, it still is quite annoying, so I wouldn't mind finding out what's doing it, or at least how to stop it happening. Basically, the PCM volume gets turned down to zero (not muted, just turned right down), which I usually notice when I can't hear anything from what I am playing in Rhythmbox. Sure enough, when I double-click the volume icon in the system tray, the PCM volume has yet again been turned down to zero.

I would like to say SMPlayer is the likely culprit, as often when I load it and play a vid, once again no sound, and it invariably is the PCM again. But since SMPlayer doesn't do this every time I start it, and since it happens to Rhythmbox without me touching SMPlayer, it has to be something else.

Just now I was playing a song in Rhythmbox and I inserted a DVD, and when I opened DVD Shrink under Wine, suddenly the PCM was turned down again.

Any ideas guys?

---

### Post by thomlark on 2009-03-28
I also am having the same problem with my PCM volume being turned down by something.

I am running Ubuntu 8.04 LTS.

My device is HDA ATI SB (Alsa mixer)  

Any suggestions will be appreciated.

---

### Post by mc4man on 2009-03-28
Some apps by default use the sound card mixer for volume control (pcm), others don't. (software mixer..?

The easiest way to see is open alsamixer and use your various media apps, adjusting the volume in the app will either move your pcm level or not.

Of my 4 apps, 2 use pcm by default - smplayer and audacious, 2 don't - vlc and amarok.
Both smplayer (gmplayer also) and audacious have an option to use software mixing, I'm not up on the pro's and cons there. I just set their default level high enough so that when they start the pcm level stays at what I want

Though it does seem every once and a rare while the level is reduced from some unknown or unnoticed reason, in which case i just reset.

---

### Post by spike_naples on 2009-03-29
Thanks. I haven't encountered these yet but it's good for me to know early as I'm planning on installing VLC soon.

---

### Post by mwillams73 on 2009-05-27
I have the exact opposite problem every once in awhile my pcm gets turned all the way up and as im sure most of you know the pcm is the master control for your sound card, sorta like an amplifier, if it gets turned all the way up then the sound gets majorly distorted and can after a lil time actually fry out your card so dont turn it all the way up, please, you'll save yourself time and money , the rule on amps is 75 percent of total volume maximum, you shouldnt need to turn it all the way up . Im tired of seeing posts telling people to turn their pcm all the way up its bad for your sound card!!!! Would you do that to the amp in your car ? No!!! it would fry out thousands of dollars of very expensive equipment! If you dont believe me do a google search on how amplifiers work and OHMs law. Then maybe we can get these posts to stop!!! Do the mods around here even know anything about how sound electronics work? Or do they just accept what people say as a fact? Im really getting tired of this!

---

### Post by OzzyFrank on 2009-05-27
OK, now seriously I mean no offence here, but from how VEHEMENTLY you said what you did, and looking at what you said, I have to ask: **Are you for REAL?**

First off, if people don't know stuff about hardware or OHMs, please don't assume it is a deliberate attempt to rouse your anger and generally make your life hell.

Secondly, most of us have never ever heard of anything like only having the PCM at 75%. I'm not saying it is a load of absolute rubbish, but sort of smells like it, no offence. I mean, I've been using PCs for 18 years and have never heard that, and nor have I ever burned out a sound card... the only reason I've ever had to pull one out is to upgrade to a better one.

Thirdly, what kind of crappy sound cards are you using that would distort the sound above 75% PCM volume? Or have you messed with some other settings to achieve this? Using the wrong driver or something? All I get is crystal clear sound on any of my PCs with sound cards ranging from generic cheap ones to my Creative Audigy ZS Platinum. When I turn down the PCM, it sounds like it isn't quite there.

Lastly, I have to point out then when people post to get a question answered, they usually don't mind people going slightly off topic and even to disagree with them... but, um, to come here pleading that people stop asking questions... and to complain about the moderators not knowing about sound equipment, and even letting such questions to be posted... isn't that a bit much?? I mean, dude, seriously, have you had your coffee today? Or is it that you had too many??

I mean: [COLOR="DarkRed"]"Then maybe we can get these posts to stop!!! Do the mods around here even know anything about how sound electronics work? Or do they just accept what people say as a fact? **Im really getting tired of this!**"[/COLOR] - does this seem even slightly rational? Once again, seriously, no offence meant here - but I'm not the one who came in here kicking and screaming, hehehe.

So, please, take it easy, and of course feel free to back up your statements with links to said info that is apparently all over the web.

---

### Post by mwillams73 on 2009-08-02
First ozzy i never said PCM 75, i said amp at 75 percent, Every computer ive ever had ( that would be 6 at present) has the problem that when the PCM is turned up to 100% It distorts the sound( which is a common problem when gain and resistors or being exceeded), this ranging from creative PCI cards to built in cards. It is a fact that when the gain is turned too high that it can and sometimes will burn out solid state electronics, this is true with all solid state components including sound cards. I never said you shouldnt post questions, i said people should stop posting that you should turn your PCM all the way up. Im sorry but after 400 threads of my sound isnt working and the answer being oh just turn your PCM all the way up got on my nerves.

I came to this thread because i had sort of the same problem which has somehow rectified itself. I apologise for any vehemence in my tone of writing, But that does not make me wrong about the PCM thing, Just because you choose to run yours all the way up with no problems doesnt mean that other people wont have problems. I mean really would you run your home stereo at full volume all the time? Eventually it will either pop a fuse or completely fry the boards and resistors and diodes and transistors, not to mention the micro chips on newer models.( which by the way are the same parts used in sound cards) 

In closing im sorry that you think my info is bunk but its true, read up on OHMs law as i suggested in my earlier post and you'll see that im not far off the mark for setting levels in solid state amplifiers and gain adjustment. If you dont want to prove me wrong thats perfectly fine but im not gonna do a search for you to prove im right just because you dont believe me. Oh and they have these things called LIBRARIES where i come from that give you books for free. Go in and ask them for some text books on solid state equipment, specifically radio and TV solid state repair manuals and modern Computer solid state equipment. The parts that are used in radios and TV's are relatively the same. But the same OHMs law applies to all solid state components, whether you like it or not.

---

### Post by CatKiller on 2009-08-02
Just as a heads-up, you might want to read up on DSP. Whilst it's true that running an amp too hard will lead to distortion, wherever it is in the signal chain, that's not the same as manipulating a string of numbers. Some sound cards may let you directly control the amp settings and have insufficient headroom to run that at 100% of whatever they're calibrated to, but not all of them. And it's certainly not an issue if you are only manipulating an audio stream in software.

---

