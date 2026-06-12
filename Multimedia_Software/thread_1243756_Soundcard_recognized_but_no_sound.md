---
title: "Soundcard recognized but no sound"
date: 2009-08-18
forum: Multimedia Software
---

### Post by ruebenkraut on 2009-08-18
Hi everybody, 
I'm knew to Ubuntu and installed 9.04 64-bit on my Dell Studio 15 laptop dual-booting with Vista. Everything worked fine, I got Flash etc going thanks to this Forum, but when youtube was eventually working I noticed there's no sound. I realised I haven't had any sound (not even login) on ubuntu, although it works fine in Vista.

I followed the Solutions Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) and step 1 was successful, my soundcard is recognized. Sound is not muted in the alsamixer or anywhere else I can see. According to the Guide my sound should be working now, but it isn't. And I'm lost.:(

Can anyone help me out? Any help would be greatly appreciated. Thanks!

EDIT: Problem solved!! The solution is somewhat weird and to befound here: [http://ubuntuforums.org/showthread.php?t=1139700&page=2](http://ubuntuforums.org/showthread.php?t=1139700&page=2)
Just adding a line to some file does the trick. Ubuntu is weird. Good job I' ll now be able to stay and explore!:)

---

### Post by andrew13321 on 2009-08-18
What kind of soundcard do you have?

---

### Post by ruebenkraut on 2009-08-19
I have a HDA Intel card with a IDT 92HD73C1X5 chip. I updated ALSA to v.1.0.20 but no luck.

---

### Post by haaxerei on 2009-08-19
i think i had same soundcard and same problem, an upgrade to the kernel:
2.6.28-14-generic
solved it for me

---

### Post by ruebenkraut on 2009-08-19
I had that kernel installed, and have just upgraded to...-15, still no sound. Any other ideas? Thanks for trying!

---

### Post by haaxerei on 2009-08-19
okey, sry then try this:

applications-> sound -> pulse audio chooser
then in the planel click on the symbol -> volume control-> output devices
if the brown? bar moves if you play any mp3 or smth.

---

### Post by ruebenkraut on 2009-08-19
I installed Pulse and yes, the bar is moving when I play back music.

---

### Post by ruebenkraut on 2009-08-20
Bump. So the card is recognized and Pulse shows output( bar moving), but still no sound. I really have to find a solution to this or I' ll have to move back to Windows, (as I' m taking this computer with me abroad for a while next week and I need sound) and I don't want to!

Please, anybody have any ideas?

---

### Post by Scott82 on 2009-08-20
I've had a lot of problems with Pulse Audio, you can try using alsa instead. But if you're like me and think that's a ton of hassle for something that honestly might screw things up to the point that it's easiest to fix it by reinstalling the OS, Just keep fidgeting with it. check all your sound preferences in system > sounds, check your volume control, change the drop box to Playback: yada yada Pulse audio and check that, check all the other things and see if something seems a bit off or set wrong or w/e. I actually had gone to Debian for quite a while because of annoyances with Pulse Audio. which worked out for a long time, then I came back to Ubuntu for reasons unknown to me really.

I also hate windows, it's total crap, but at least MS has most of the basic aspects of using a computer working when they release their OS. I really have no idea why Ubuntu went with such a buggy app, Pulse could have easily waited a couple distro releases.

I hope you get it going :D

---

### Post by ruebenkraut on 2009-08-20
Slightly confused right now, I thought I was using ALSA...and I can't find that playback dropbox anywhere either. 
I guess the sound must be lost somewhere"on its way o the speakers" but I really can't see where it could be.

---

### Post by Scott82 on 2009-08-20
Ubuntu 9.04 comes with Pulse Audio and most of Alsa (pulse is kinda like a big gooey mess that you stick alsa, oss and all that other crap into instead of just having them do their thing, they made this big gooey mess because there were a lot of sound systems being developed for linux that were basically incompatible with eachother, so instead of saying 'ok, let's go with Alsa 'cuz it's the one that isn't crap' they made a big gooey mess that you can throw them all into and it'll sometimes work.), but uses Pulse Audio by default. any chance you could do screen shots of your Volume Control window and the Sounds window?

also, have you tried the sticky at the top of the forum?

(that's what i've gathered from what i've read and seen about it all)

---

### Post by ruebenkraut on 2009-08-20
Yeah, as I said I did theSticky but according to that guide my sound should be working now. I had to install Pulse, I don't think my version(64bit perhaps) came with it.
Anyway, here's a screenshot with my Volume Control, my Alsamixer and System>Sound.

Edit: Just realised that the screenshot shows sound capture in sound preferences as Hda..., it usually says ALSA-Advanced Linux...
Anyhow, neither of them works. If it makes any difference at all.

---

