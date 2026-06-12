---
title: "Dell XPS m170 Front Multimedia Buttons"
date: 2008-11-07
forum: Multimedia Software
---

### Post by t3hparad0x on 2008-11-07
To start this off right, I should say briefly that I've already read various posts referencing the same issue. 

Sadly, I've found very few to be of use. 

Here is the issue. The front Multimedia Buttons are active and working. They seem to change only the "master" Default Mixer Track. My device is the Intel ICH6 (Alsa mixer.) Maybe it's just my perception, but I would prefer a hierarchy system where the master selection controls the other "tracks"... such as PCM, Line-IN, etc. When the Master is adjusted, all others are adjusted.

At the moment, the only buttons that seem to be working GLOBALLY, are these:

Play/Pause, prev. track, next track, & stop.

The "x" button to the far left (As I changed in XP) is set to mute all. This likewise, is changing only the master Default Mixer Track.


----


**NOTE: I have had success with altering my selected output track from Master to PCM. This is only a workaround, and a rough one at that, being that the overall success is pending on utilizing this hierarchy for all systems. If I change Tracks from PCM to Headphones for instance... in order to control volume output control, I will have to manually change the settings... located: system < preferences < sound

If anyone else has any success changing this, please let me know!

It could be something as simple as an oversight on my part... maybe as easy as swapping my selected default Track... who knows?! LOL

Anyhow, thanks in advance!

---

### Post by t3hparad0x on 2008-11-07
Alright everyone... two points of interest. 

Firstly, I made the jump to Linux FULL-TIME. I'll still leave a dormant version of XP Media Center Edition loaded (but unused) in the event I choose to play a game anytime soon, or if I happen to (knocks on wood) have a problem with Ubuntu.

Yay for me. (BTW... this switch required me to reinstall my system... gotta love that 15 minute Ubuntu Install time.)

Anyhow, Secondly, we've got the issue at hand... which is still present after reinstall and checking drivers thoroughly.

I've read through a few more forum posts, discovered that my problem is a mixture of things. These are mixers and my button assignments. I have somehow been able to select the Headphone mixer as assigned to my front panel buttons. Don't ask me how I did this, because it seems to be a default setup or a fluke. Luckily for me, I use external speakers (connected to a surround system.)

I have left my defaulted button assignments in tact this time, so as to avoid any confusion. This is a fresh install, with only various programs and settings upgraded... but none touched.

When not using the headphones (or audio out jack) I have semi-distorted sound coming from my in-pc speakers. The distortion seems to be a poorly aligned Master vs Master Mono mixer level. I can correct this temporarily, however, I will have to adjust the sound via software from the music device in order to get a decently suitable amount of sound. It also goes without saying that I will have to adjust not only my Master level manually, but I will have to match up my Master Mono (laptop's sub-woofer) levels at the same time... hoping to find a happy medium.


If anyone gets a wild hair to write some software, this seems to be an issue found prevalent in these systems. I'm no guru w/ programming, otherwise I'd try my hand. Anyhow, any suggestions or further progressive work-around will be appreciated!

Thanks all!

---

### Post by TropheusJon on 2008-11-08
I'm using Dell Studio laptop.  Do you have problems when you adjust the screen brightness when using the Fn key with the up/down arrows?

I have major cpu usesage when using that and the usesage doesn't die down afterwards.

---

### Post by TropheusJon on 2008-11-08
I'm using Dell Studio laptop.  Do you have problems when you adjust the screen brightness when using the Fn key with the up/down arrows?

I have major cpu usesage when using that and the usesage doesn't die down afterwards.

---

### Post by t3hparad0x on 2008-11-20
To be honest, I have yet to try my FN keys. However, I'm pretty sure they're functional to a moderate degree. Ubuntu has done an amazing job with it's integration of features from various systems.

Update: I've reinstalled Ubuntu several times (not in effort to fix the problem, this was more or less due to my fowl-ups.) During this, I have still encountered the problems... even after all synaptic updates are installed. 

I have attempted to tweak the ALSA settings with no success. The problem still persists.

One thought, I have considered writing a program (more like an addendum) that would instruct my mixer sources to increase or decrease volume at the same time. (Think of it more like linking several separate mixers together and utilizing the "MASTER" setting to raise and lower the volume.) Another idea was to add a checkbox in the ALSA GUI to "bridge" the selected mixers. For instance... in my system, I have PCM, Master, Line-In, and Headphones (the audio-out jack) among others. In my particular situation, I would like to be able to select PCM and Headphones to both be controlled by the Master setting. In the suggested GUI, I would select the PCM and Headphones settings (after adjusting them to an appropriate level) then raise and lower the Global Audio level (or Master setting... system-wide) by my chosen keyboard shortcut, which in my case would be my front panel.

I'm sure this add-on sort of program could benefit someone, or in any event, if I can find someone to help... this may be able to expand toward other pc's and laptops using similar setups. Hopefully, someone may consider adding this into Ubuntu's generic "driver" list... or whatever it's called.

'We'll see. Until then, If anyone has any input, I would love to hear it. I'm not AT ALL a proficient programmer, so this may take some time.

---

