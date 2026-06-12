---
title: "Audio problems after upgrading to Hardy Heron"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Ederico on 2008-04-26
Hello,

I'm having audio (and video) problems after I upgraded to Hardy Heron from Feisty Fawn. The problem surfaced after, meaning that before everything was great.

Basically when I open up some video (.flv) in Totem I either don't get audio at all, I only get audio, playback doesn't work or the application just blocks itself altogether. When this happen, I try using Amarok but it doesn't work either (using different files and file formats as well) giving me no playback at all and showing me a jammed thing.

Anyone have any idea on what's the problem?

Ederico.

---

### Post by Sabayenda on 2008-04-26
I am having similar problems...
If I watch a youtube video or listen to Pandora, I am unable to listen to music in Rhythmbox and I am unable to play any video in Totem.
I upgraded from a fresh install of Gutsy 
<rant>(I downloaded the torrent for Hardy, but the iso was whack and didn't work!!!!!!!!!(This release is the most disapointing in that I've done a fresh install for every one since edgy and this one was the absolute WORST experience, I was unable to try hardy out before I installed because it refused to load gnome, and then I tried to just do the install option in the first menu, and that would always stop at 35% because it had CORRUPT FILES!!!!!!AND IT COMPLETELY WIPED OUT MY HARD DRIVE!!!! BOOOOOO!!!!!))
</rant>
The only way I can fix this is to restart my computer, which is unacceptable...
In Gutsy I could listen to music AND watch youtube videos/pandora (meaning I could listen simultaneously or pause one and listen to the other, with no problems whatsoever)
I do know that hardy has the new PulseAudio, which I thought was mainly introduced because it is supposed to handle audio from multiple things, which it absolutely does not! I want an answer as to why one of the main features of this new release of Ubuntu does exactly the opposite as it was promised to do!!!!
All in all, I am happy with hardy heron, because it's faster and snappier than any previous version I've tried, but it's also the most unstable feeling and uses a lot more CPU power than any other, oh, and suspend would work without a hitch in Gutsy, now I get these weird messages when I open my lid after it's gone into hibernation, and sometimes it comes back, though other times it just shows me this weird message and I have to hold down the power button.
Another thing that was very unsettling was when I did the upgrade from Gutsy to Hardy through Update Manager, it downloaded the fastest of any other release, but when it went to install all the new software, it had a LOT (at least 20, maybe even 30!) of new packages that it would not install, and these were pretty major ones like Synaptic and important background Gnome packages.  Thankfully when I restarted my computer and connected to the internet (which was a chore too. Thankfully I was able to go to my school's library and hijack their wired connection so I could install the firmware for my wireless card (Broadcom) which makes no sense at all, because most people don't do wired connections anymore, everything's wireless, duh!) and install all these missing packages through a simple little command it gave me when I ran update manager again and it told me that it couldn't install those important packages, so that's taken care of.

To sum up, Hardy Heron is absolutely THE most difficult release of Ubuntu to install, and therefore takes longer, and even though it's been a headache and kind of disappointing, I'm glad I did it because of the speed increase (OpenOffice opens up in less than a minute, Rythmbox doesn't take ten minutes to load up my iPod and is now instant(!!!!SO awesome!!!), and the new clock with WEATHER(!!!!so awesome as well!!!I don't care about the multiple locations yet, since all the foreign people I know are living in the US right now), also, since I got my wireless working, it hasn't cut out once yet( it used to cut out constantly, though I fixed that a little bit in Gutsy by installing Wicd, and still use it as NetworkManager(reminds me of windows) is far inferior to Wicd(is more in line with a linux desktop as it's open about what's going on, and it actually works), never going back to NetworkManager!!! 
I'm running this on an old Dell Inspiron 6000 with a 1.5ghz celeron processor, 1gig of ram, and 40gig hard drive with no graphics card :(

---

### Post by Sabayenda on 2008-04-26
So I think I fixed the problem with PulseAudio...
Just install libflashsupport, and everything else that looks like it will help when you search pulse audio in Synaptic.
I installed that, restarted Firfox and now youtube videos play sound!!!
Pandora works too!!!!

---

### Post by jmexia on 2008-07-24
All I did was install the libflashsupport through Synaptic, and that seemed to work.  Now I can play Rhythmbox and Pandora at the same time.  I can even toggle (pause/play) between the two.  Thanks, Sabayenda!

---

### Post by dartrod on 2008-09-28
I am also having this problem.  After reading every thing I could on this problem, it appears that this is a Hardy Heron problem.  There is no simple fix!!!
I'm awaiting the next release, hopefully the problem will be addressed.  If not I will be looking for a different distro.

RSW

---

