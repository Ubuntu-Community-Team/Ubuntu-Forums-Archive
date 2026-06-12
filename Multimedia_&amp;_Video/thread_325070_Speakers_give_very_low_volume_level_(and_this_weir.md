---
title: "Speakers give very low volume level (and this weird ticking noise)"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by TeeAhr1 on 2006-12-24
I just got a set of Creative T2900 speakers off Woot ([these ones]("http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=1424"), they were quite nice for the money), and I feel like I'm getting about half the volume I should be getting out of them.  I've got "master" turned all the way up in alsamixer, but I didn't really know what the other options in there were so I didn't want to mess with them.

Also, I swear to god, I'm getting this weird rhythmic tick out of them sometimes too.  It comes and goes, I have no idea what makes it happen.  Any advice on either of these questions would be greatly appreciated.

Happy $HOLIDAY-OF-CHOICE
-pete

EDIT: Did an "lspci -v" and I apparently have a "VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)," for what it's worth.

---

### Post by BitTorrentBuddha on 2006-12-25
I don't know, I always seem to get low speaker volume out of Ubuntu, I have never been able to determine the cause nor the solution. I am very interested if there is one though.

---

### Post by cilynx on 2006-12-25
Check your PCM volume.  That's all your "normal" wav type sounds

Vol: Master Volume
Pcm: Just about everything.  mp3, system sounds, etc...
Line: Line in
Mic: Microphone
CD: CD being played in non-buffered audio mode
IGain: Hardware gain (leave this alone)
Line1: Extra line in if you have it
Digital1: Digital input
PhoneIn: 1/8" stereo input
PhoneOut: 1/8" stereo output
Video: Hardware Video (TV card, ect) sound level

As for your crackle, do you have anything magnetic around your speakers?  Cell phones, cordless phones, monitors, tvs, many other things are known to cause interference, especially if you have to have the volume cranked.

---

### Post by TeeAhr1 on 2007-01-02
Well, add "wireless router" to that list of known interference-causers... /sheepish

Thanks also for the primer on audio settings.  Didn't immediately fix the volume issue, but I appreciate it nonetheless.  I'll keep messing with it, as I am wont to do.  Happy New Year, all.

-pete

---

### Post by msjulie on 2007-01-03
Hello Pete,

Here is what I have found so far...from reading other posts and experimenting with my settings to get lots of volume from an OLD RIptide sound card.

I set my PCM aboutin 'alsamixer' about 95%

My Master Volume varies quite a bit based on mood currently 65%.  It is tied to my volume knob on my keyboard.

Here is the real trick I found.
In Rhythm Box, and I believe Sound Juicer, and Totem, there is a volume setting there.  This was not a Master Volume, like in Windows Media player, this is its own volume control.  I had to turn this way up (100% in Rhythm Box).

I get tons of sound and my little speakers I play through are at 50% volume (stinky little speakers integrated to my LCD screen.

As far as the Rhythmic clicking.  Try a little test:
In Ubuntu goto *System->Preferences->Sound* and switch in the **devices** tab the *Sound Events* and *Music and Movies * to OSS or ESD setting.  See if that changes anything.

My sound card is very odd.  There are no alsa drivers for it, just some depricated OSS drivers.  My card works through Alsa, but I get Rhythmic poping and distortion through it.  Even the *Test* sine wave test in the *Sound* settings experiences this through Alsa.

Just my thoughts.  When I get $40 I'll just replace that stinky card with a cheap and better low end replacement that Alsa supports.

Julie S.

---

