---
title: "MP3s Suddenly Stopped Working"
date: 2008-06-11
forum: Multimedia Software
---

### Post by abelianjeff on 2008-06-11
Hi everyone,

I'm new to Linux, and I'm running Ubuntu Hardy. I just installed the OS a few days ago, and when I did, I was able to play my MP3s fine (after installing the appropriate codecs). 

In the last few days, however, I have been downloading a few different audio programs, trying to find the one I like the most. I liked Amarok, but I discovered that when I asked it to play a song, the song just stayed at the 0:00 time mark and did not play. I tried Songbird...same thing. Finally, I tried playing a song in Rhythmbox, the program which worked originally....same thing. I don't know what happened in the last few days, but suddenly I cannot play MP3s. Other audio (i.e. Youtube) works fine. 

I'm not sure if my installing/uninstalling of different programs affected my plugins somehow...according to Synaptic, they are all still present, and I have run the commands in the Sticky at the top of this forum. Still, my MP3's will not play. They just remain stuck at 0:00.

At no time does any of these programs give me an error message.

Please help! 

Thanks,
Jeff

---

### Post by abelianjeff on 2008-06-11
*bump*

---

### Post by prshah on 2008-06-11
> **abelianjeff said:**
> 
At no time does any of these programs give me an error message.



Try running the programs from a terminal, then playing an MP3... any errors?

---

### Post by Raistlin82 on 2008-06-11
exactly the same problem, was all working fine an our or two ago, then when i turned on again its broke :(

---

### Post by abelianjeff on 2008-06-11
> **prshah said:**
> Try running the programs from a terminal, then playing an MP3... any errors?

Wow, I typed rhythmbox into the terminal, the program opened, it loaded all of my music into the playlist anew, and then the mp3 played! Not only that, I tried songbird next, and that was also playing my mp3s! Thanks so much!!

Does this mean I always have to run my mp3 program from the terminal for it to work? (That's fine if it does, I'm just curious as to why that is.) 

Thank you prshah!!

---

### Post by prshah on 2008-06-11
> **abelianjeff said:**
> Wow, I typed rhythmbox into the terminal, the program opened, then the mp3 played! I tried songbird next, and that also playing my mp3s! 



:lolflag:I'm just as stunned as you are; it was meant to be a troubleshooting step, not a workaround/solution.

Can you now try opening the players in the "regular" way and see if they work as well?

---

### Post by abelianjeff on 2008-06-12
> **prshah said:**
> :lolflag:I'm just as stunned as you are; it was meant to be a troubleshooting step, not a workaround/solution.

Can you now try opening the players in the "regular" way and see if they work as well?

I just tried it the "regular" way (opening it via the Applications menu) and it worked there, too!

Whether you intended it to be a solution or not, I'm giving you the credit for fixing my problem, haha. Thanks so much!

It will be interesting to see if this also works for Raistlin82...

---

### Post by Raistlin82 on 2008-06-12
Thats very weird, was gonna post pretty much the same message, tried running amarok through terminal this morning, and since then everything is working sound as, even after a reboot sound is fine without using terminal.  strange, but good :)  problem solved (touch wood!):popcorn:

---

### Post by abelianjeff on 2008-06-12
I think I've just discovered what is going on.

If I have Soundbird (or whatever) and I'm playing MP3s, then videos on the internet don't have sound. I need to close Sounbird and Firefox, then re-open Firefox to get those videos to have sound. However, now that my videos in Firefox are playing sound, Soundbird won't play MP3s...they just stay stuck at 0:00.

Very strange!

Does anyone know how I can get these two programs to play nicely and share the ability to play sound? ;)

---

### Post by hoatu on 2008-06-17
Exact same problem and solution here too.

Out of interest how did you all upgrade to Heron? I did dist-upgrade...
Maybe this has something to do with it?

---

### Post by abelianjeff on 2008-06-17
Mine was a clean install, I was running XP before.

---

### Post by Andrew-buntu on 2008-06-17
I'm having the same problem.  My wild guess is that it's the new PulseAudio sound server.  Linux has always had these ALSA-likes-one-thing-at-a-time issues.  So desktops like Gnome have their own little sound servers to make multiple applications play nice.  When they don't work well, you get one sound-making app at a time.

This has been annoying me since I did a fresh install of Hardy after release day.  I'll post back here when I find the solution (which is undoubtedly here on the most helpful forum on the net :)).

LATER...

Everything worked for me after changing everything in System > Preference > Sound to "ALSA - Advanced Linux Sound Architecture".  I was just watching YouTube while playing an MP3 and running the test bleep.  I have an HDA Intel sound card so YMMV.  This thread also looked helpful in case the ALSA thing doesn't work for you.  It tells you how to set up PulseAudio properly.

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by Mijder on 2008-06-20
I've had a similar problem. I can still play mp3s fine in VLC as well as other audi like in Totem, but RhythmBox and Songbird just do not want to play sound worth anything.

The only difference for me is, the counter isn't stuck at zero, it ticks along to the song.

---

### Post by Mijder on 2008-06-20
Oh, and the solution of just opening it up with terminal did not work for me.  Still no sound.

---

### Post by laluz on 2009-06-18
> **Mijder said:**
> I've had a similar problem. I can still play mp3s fine in VLC as well as other audi like in Totem, but RhythmBox and Songbird just do not want to play sound worth anything.

The only difference for me is, the counter isn't stuck at zero, it ticks along to the song.

I have the same problem. Changing the Gnome sound preferences to use OSS made Songbird to actually play sound, but then some other apps could not. Mplayer does not play at all. Xine would play video or MP3 if I set sound to pulseaudio, but would not play AC3. Amarok would play fine too, with xine configured to use alsa. 
A I am just lost myself at what is going on.

Anyways, try to set in gnome preferences to use OSS. May be it will solve your problem.

---

