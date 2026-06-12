---
title: "So I fired up the old 8.04 live CD..."
date: 2010-06-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-06-23
I fired up a live CD of 8.04 (7.10 wouldn't work on this hardware) and started looking around, because I was curious how much things have changed since then (for memories sake).

Then I realised something, when I open up an application, it appeared really smooth, and also when I closed it. When I clicked through the menu bar, they faded in and out. It felt really smooth, how come the last few releases they decided to scrap the nice default effects?

And is there any wiki page etc that outlines plans for default compiz effects etc for Maverick?

---

### Post by ranch hand on 2010-06-23
I have no idea about compiz because;
A>it would not work for me on Hardy
B>I  hate compiz

However, Hardy was (and is) one heck of an OS.  It is still my secure business OS.  Not very exciting or particularly fun to use, but very solid and reliable.  Nice stuff.

---

### Post by psyke83 on 2010-06-24
> **ranch hand said:**
> I have no idea about compiz because;
A>it would not work for me on Hardy
B>I  hate compiz

However, Hardy was (and is) one heck of an OS.  It is still my secure business OS.  Not very exciting or particularly fun to use, but very solid and reliable.  Nice stuff.

[RANT]
Hardy was solid, except for the way that PulseAudio was integrated into this release: it was configured to run without intercepting sound from any ALSA applications. This meant that any application without explicit PulseAudio support - i.e., pretty much anything that did not use GStreamer - would not work if PulseAudio was using the sound card at the same moment. This was a major oversight and caused a great deal of negative press against PulseAudio (IMHO). PulseAudio's upstream clearly documented how to configure PulseAudio to properly intercept sound from ALSA applications, and most distributions followed these guidelines, but our implementation was incomplete.
[/RANT]

Aside from this pet peeve of mine, and despite having no major qualms with Hardy, I have to say that Lucid is a much superior release. I found Lucid to perform much better than Hardy on my *ancient* desktop system (Pentium II 233MHz with 196MB ram).

Taking into account the commonly held view that newer software equals more bloat and complexity, Lucid works surprisingly well - nay, better than Hardy, on this dinosaur of a system. Of course, I unchecked some items in **System -> Preferences -> Startup Applications** to maximize the limited memory available, but I'm sure that I performed the same steps for Hardy as well.

---

### Post by VMC on 2010-06-24
> **psyke83 said:**
> ...I found Lucid to perform much better than Hardy on my *ancient* desktop system (Pentium II 233MHz with 196MB ram).

Taking into account the commonly held view that newer software equals more bloat and complexity, Lucid works surprisingly well - nay, better than Hardy, on this dinosaur of a system. Of course, I unchecked some items in **System -> Preferences -> Startup Applications** to maximize the limited memory available, but I'm sure that I performed the same steps for Hardy as well.
Interesting. Because I have the exact same specs on an ancient Compaq laptop that I couldn't get anything except an old version of PCLinuxOS to run on it. Also Windows XP runs very well on that system. Obviously you used the alternate install. I'll have to try Lucid now that I know someone else with limited ram got it to work.

---

### Post by ranch hand on 2010-06-24
> **psyke83 said:**
> [RANT]
Hardy was solid, except for the way that PulseAudio was integrated into this release: it was configured to run without intercepting sound from any ALSA applications. This meant that any application without explicit PulseAudio support - i.e., pretty much anything that did not use GStreamer - would not work if PulseAudio was using the sound card at the same moment. This was a major oversight and caused a great deal of negative press against PulseAudio (IMHO). PulseAudio's upstream clearly documented how to configure PulseAudio to properly intercept sound from ALSA applications, and most distributions followed these guidelines, but our implementation was incomplete.
[/RANT]

Aside from this pet peeve of mine, and despite having no major qualms with Hardy, I have to say that Lucid is a much superior release. I found Lucid to perform much better than Hardy on my *ancient* desktop system (Pentium II 233MHz with 196MB ram).

Taking into account the commonly held view that newer software equals more bloat and complexity, Lucid works surprisingly well - nay, better than Hardy, on this dinosaur of a system. Of course, I unchecked some items in **System -> Preferences -> Startup Applications** to maximize the limited memory available, but I'm sure that I performed the same steps for Hardy as well.
I just got this box just before 8.10 came out and installed 8.04.1 with the same hardware as I have now.  Have never had trouble with sound.

The sound in 10.04 is better than any release so far.  Quality is about the same but the volume is at least 25% greater meaning a little more control all around.  I like to listen to music and it is just great.

I would love to run 10.04 as I think it is a better OS too.  The fact that, by the clock on my desk here, 8.04 boots slightly better than twice as fast, does not require me to edit the menu to get it to boot and shuts down 5 times as fast has me staying with it for now.

---

### Post by wilee-nilee on 2010-06-24
> **ranch hand said:**
> I just got this box just before 8.10 came out and installed 8.04.1 with the same hardware as I have now.  Have never had trouble with sound.

The sound in 10.04 is better than any release so far.  Quality is about the same but the volume is at least 25% greater meaning a little more control all around.  I like to listen to music and it is just great.

I would love to run 10.04 as I think it is a better OS too.  The fact that, by the clock on my desk here, 8.04 boots slightly better than twice as fast, does not require me to edit the menu to get it to boot and shuts down 5 times as fast has me staying with it for now.

Your testing maverick eh, I like it. 

Hows it going in big sky country, my mom was born in Helena, been there liked it.:p

---

### Post by ranch hand on 2010-06-24
Yup, a long way from Helena (there is a bluegrass band in Helena - Helena Hand Basket).  Things are pretty fair here considering the economy.

Hardy is my business OS.  I think it will be replaced by Debian Squeeze.  I do not spend a lot of time on that OS, the security is no fun at all.  Pretty safe though.

I spend most of my time at night on 9.04 (that is where I am now) and in the daytime it is on the current testing OS (6 installs so that I can play with various things and at least have one running at all times.  Haven't lost either of my "first line" installs yet this round.

I like 9.04 best for just using.  10.04 would be great if it booted and shut down.  10.10 may well be another fun one and, at least right now it boots, in less than a minute on clean installs in spite of plymouth.  Upgrades not so fast.

Some folks have trouble with sound here too.  It, so far for me, rocks just like 10.04.  My altec-lansing surround sound system really likes it.  I do not know about the neighbors on the occasional "just crank that puppy up" whim.

I am looking forward to Naughty Newt already.

---

### Post by wilee-nilee on 2010-06-24
> Helena Hand Basket
Thats a great name, especially for a bluegrass band. Those accomplished bluegrass and country players can keep up with us Jazz musicians with no problems. Any mastery of a instrument no matter what genre always gets my attention. Although some of the most creative people I know can't read music and are self taught.

---

### Post by psyke83 on 2010-06-24
> **VMC said:**
> Interesting. Because I have the exact same specs on an ancient Compaq laptop that I couldn't get anything except an old version of PCLinuxOS to run on it. Also Windows XP runs very well on that system. Obviously you used the alternate install. I'll have to try Lucid now that I know someone else with limited ram got it to work.

I used the live installer (making sure to boot directly into the installer instead of the live environment). In previous releases, including Hardy, the memory pressure would usually cause the system to freeze long before the live installation could complete. In Lucid, the live installation could complete successfully without such freezes. Keep in mind that the system's drive already had a swap partition (which I believe the live CD uses automatically).

I also recall that I removed/disabled ureadahead. It was slowing down the boot due to this system's disk controller being limited to UDMA2. With that removed, bootup feels faster than Hardy.

---

### Post by go7Ul1ai on 2010-06-24
This thread has been pretty much off-topic since the 2nd post, could we please discuss something along the lines of what I'm trying to say in the original post please :) ^_^

---

### Post by malspa on 2010-06-24
Still using Hardy and the Hardy-based Mint Elyssa here!  I know it's time to wipe them out for the current LTS versions, but...

---

### Post by psyke83 on 2010-06-24
> **ranch hand said:**
> I just got this box just before 8.10 came out and installed 8.04.1 with the same hardware as I have now.  Have never had trouble with sound.

The sound in 10.04 is better than any release so far.  Quality is about the same but the volume is at least 25% greater meaning a little more control all around.  I like to listen to music and it is just great.

I would love to run 10.04 as I think it is a better OS too.  The fact that, by the clock on my desk here, 8.04 boots slightly better than twice as fast, does not require me to edit the menu to get it to boot and shuts down 5 times as fast has me staying with it for now.

Ubuntu audio developers are doing a great job, and PulseAudio integration has been excellent since Karmic. Before that... not so much. If you don't remember having mixing issues with Hardy, and your recollection is accurate, then I suspect that you're lucky enough to have a sound card which supports hardware mixing. Most sound cards (such as AC'97 chipsets) are limited to software mixing, which would cause the audio conflicts in Hardy. [Bug #198453]("https://bugs.launchpad.net/bugs/198453") dealt with this issue (and if you are ever interested, the rest of the bugs are explained/linked in my old HOWTO).

Anyway, my impressions of Lucid's performance (on my dinosaur system and modern systems alike) are the opposite to yours. Bootup is fast on all my systems (though on the dinousaur, it only became faster after removing ureadahead), and Lucid's shutdown is so ridiculously fast that I always wonder if it's really unmounting the drive properly.  I also get disconcerted by the "emergency power down" sound that my laptop drive makes - though I suspect that's a genuine bug.

---

### Post by ranch hand on 2010-06-24
My son recommended an Audigy1 card as it worked for him.  It was my first attempt at Linux so I got one (the on board  sounded like a early transister radio under Vista).  SB seems to be real well supported.

---

### Post by psyke83 on 2010-06-24
> **lee.jarratt said:**
> This thread has been pretty much off-topic since the 2nd post, could we please discuss something along the lines of what I'm trying to say in the original post please :) ^_^

Whoops ;)

My original interpretation (and perhaps the interpretation of some others) of your post was talking about the general performance of the system. Looking back, I guess you were only interested in the issue of default the compiz setttings being different... ;)

---

