---
title: "SdlMame - Bursts of static when busy"
date: 2010-02-20
forum: Multimedia Software
---

### Post by Listerofsmeg01 on 2010-02-20
Hi folks,

I am running sdlmame on my Aspire Revo, Everything is generally hunkey dorey & sound is perfect.

However, when the processor gets a bit bogged down I sometimes suddenly get loud static through my speakers for a second or two before it reverts back to normal. Sometimes I lose it completely and just get constant static, although the game continues to play normally. Very occasionally the sound will recover, but normally that's it and I have to quit the game.

Pausing the game pauses the static but does not recover the sound (static continues when game continues).

Setting mame to mix at a lower rate results in lower quality static, so it seems to be a problem with mame itself rather than my ALSA setup (I upmix everything to 48000Hz due to using digital out).

Fiddling with mame's buffer length settings seems to make no difference.

If I increase frameskip, then it decreases the likelyhood of static, but it's frustrating that I know the game can be driven at fullspeed. Sometimes I have to slow it down dramatically to completely guarantee non static.

mame is the only app I have this problem with. All other sdl apps work fine, including other emulators.

Anyone come across this before? It's really annoying when I'm playing Afterburner on my 60" plasma and 5.1 setup, and then I'm suddenly deafened by static. It's killing my perfect setup. :(

Many thanks for any suggestions.

---

### Post by mocha on 2010-02-24
This sounds like a common bug with SDL audio that I've run into as well with SDLMAME.  In the mame.ini file, I believe it's located at /etc/sdlmame/mame.ini but I'm not at my Ubuntu box right now.  At the bottom of the file it says "sdlaudiodriver" or something like that.  Change the part that says "auto" to "esd".  You also need to install a package from the repos to get the esd SDL audio library.  Search for "libsdl esd", there's a package with a name like "libsdl audio all", or something like that.

---

### Post by Listerofsmeg01 on 2010-03-30
Many thanks for the reply. Sorry, forgotten I'd even posted this! :oops:

Unfortunately your suggestion did not cure the problem. I installed libsdl-all and manually ran esound after configuring mame, but if anything it was slightly worse! :(

As an aside, my amp is in for repair so I am temporarily running sound out of the normal analog port and I have exactly the same problem, so obviously nothing to do with my digital audio either.

Has no-one else had this problem. I can't believe nobody else has mentioned it? :(

---

### Post by engmex on 2010-04-06
You are not alone! I have the same problem, and I'm looking for a solution

---

### Post by mocha on 2010-05-15
This still seems to be an issue on Lucid although no where near as bad.  I still need to use the esd driver for SDL apps otherwise I get crackling and high CPU usage.

---

### Post by Listerofsmeg01 on 2010-12-31
Thought I'd resurrect this thread as I finally fixed this!!!!!

Turns out it was the sample rates I was using in MAME. For some reason it doesn't like the standard rates of 22050, 11025 (Didn't check 44100). These all cause bursts of static.

Setting to any other round figure seems to work fine, (eg 11000, 22000 etc). I do get a few hiccups/stutters in CPU heavy games, but I'd far rather that than deafening static!

Please note that this is not the same problem as generally scratchy/noisy sound in mame (as Mocha's post seems to be referring to). This is perfect sound punctuated by LOUD bursts of pure static lasting one or two seconds, or indefinitely.

Hope this helps someone.

---

