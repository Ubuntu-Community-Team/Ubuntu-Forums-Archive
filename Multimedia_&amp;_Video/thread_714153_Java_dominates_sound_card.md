---
title: "Java dominates sound card"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by YAOMTC on 2008-03-03
Whenever I play [RuneScape](http://www.runescape.com/) (a free browser-based 3D MMORPG that uses Java), the Java applet dominates my sound card, and doesn't allow anything else to use it. For example, if I'm playing RuneScape, I can't play music, and if I have a video up, the audio won't work in RuneScape. I understand that this has been a problem for other people, too. Has anyone found a workaround or solution? Maybe some way to make Java go through the ALSA or OSS mixer rather than directly to the sound card, as it seems to do?

---

### Post by YAOMTC on 2008-03-04
.

---

### Post by Jeff250 on 2008-03-04
There are two crappy solutions to this problem.

Crappy solution 1:  (If you have a desktop machine) buy a sound card with hardware mixing.  I've had great luck with Audigy 2's and Linux.  But as long as you do research before buying anything, you should be fine.  (For example, X-Fi support blows, since Creative didn't release a spec for them.)  Of course, this costs money, and this solution won't work for laptops.

Crappy solution 2:  Use the beta version of Iced Tea (the open source version of Java 7) from the gutsy repositories.  Note that gutsy has b21, and this bug has been fixed in b20: [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6271108](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6271108) .  However, this solution means using beta software, and it may not even work with Runescape.

The problem with current releases of Sun's Java is that they neither include the alsa dmix device nor the alsa default device in the list of available mixers available to the program, either of which would solve the problem.  Instead, they only include alsa hw devices.  Using these monopolizes the sound device if it does not support hardware mixing.

---

### Post by YAOMTC on 2008-03-04
> **Jeff250 said:**
> buy a sound card with hardware mixing.  I've had great luck with Audigy 2's and Linux.  But as long as you do research before buying anything, you should be fine.I prefer *this* crappy solution. Stil, Sun needs to get to work and make this problem not require a crappy solution! Or preferably, *solve* this crappy problem!
> **Jeff250 said:**
> The problem with current releases of Sun's Java is that they neither include the alsa dmix device nor the alsa default device in the list of available mixers available to the program, either of which would solve the problem.  Instead, they only include alsa hw devices.  Using these monopolizes the sound device if it does not support hardware mixing.Now why would they do something like that, I wonder... laziness? Maybe they just wanted to get this port done with so Linux users would stop complaining? (I've noticed sub-par quality in the Linux port of Flash, too.)

---

### Post by Jeff250 on 2008-03-04
Last I checked, Sun's Java 7 final release won't be out until early 2009.  A year is a long time to wait for a fix.  I wish that they would backport the fix to Java 6.

If you're interested in going the hardware mixing route, I noticed that they have an Audigy 2 Value card on Pricegrabber for $50, which can be either a big deal or nothing, compared to your place in life.  Ignoring the Java bug, doing mixing on the hardware sound card is still better than doing mixing on the CPU via software, but these days, with the speed of CPU's, it doesn't make much difference.  Once PulseAudio applications take off, having a card with hardware mixing will be even less useful, sadly, since PulseAudio is a user-space software mixer.  These are just things to keep in mind about your purchasing decision.

---

### Post by YAOMTC on 2008-03-04
That's a good price for a good sound card. I'll have to put that on my list of things to get once I have a job!

As for PulseAudio... I haven't heard of it. What is it? I doubt it'll be taking off anytime soon if even *I* haven't heard of PulseAudio. (Not to be arrogant, but even as an Ubuntu user you could guess that I'd know significantly more about software than the general public.)

---

### Post by Jeff250 on 2008-03-07
PulseAudio:
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

PulseAudio vis-a-vis Ubuntu:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by YAOMTC on 2008-03-07
Aw... from what I read, I thought setting up PulseAudio would actually allow me to listen to my music in Amarok and, at the same time, hear the sounds in lbreakout2 or Frozen-Bubble, but no. That kinda defeats the purpose of me configuring that just now. :(

---

### Post by YAOMTC on 2008-03-07
Well, dang. Not only did it not solve my problem, it created a new one: There's *no* sound in Java and Flash now, despite me attempting that fix listed on the page... Hopefully fully uninstalling PulseAudio will bring it back...

---

### Post by jhnphm on 2008-04-10
Crossposting a solution I posted in Beginner Talk
[http://ubuntuforums.org/showpost.php?p=4688091&postcount=8](http://ubuntuforums.org/showpost.php?p=4688091&postcount=8)

Move or remove /usr/lib/jvm/java-6-sun/jre/lib/amd64/libjsoundalsa.so (for AMD64) or /usr/lib/jvm/java-6-sun/jre/lib/i386/libjsoundalsa.so (for 32 bit) and run Firefox, or anything that calls or runs Java w/ "padsp [appname]" (for Hardy), or install the alsa-oss package and use "aoss [appname]" (for Gutsy and below)

Modify .desktop files appropriately

---

### Post by YAOMTC on 2008-04-10
Unfortunately, jhnphm, that didn't work. I restarted Firefox and logged into RuneScape (a Java-based MMORPG), and the sound worked, but when I tried playing my Amarok playlist, the "device is busy" or whatever it was came up. I quit RuneScape and started up Frozen-Bubble, and the music played, but when I started RuneScape, there was no sound there.

---

### Post by jhnphm on 2008-04-11
Hrm, now that I test it again, it only reliably works w/ padsp, which requires the use of pulseaudio. You may have to resort to installing pulseaudio and using padsp to route the sound from java to that. You may need to run asoundconf to properly configure alsa to redirect stuff to pulseaudio.  I'm unsure how well pulseaudio works on Gutsy, since I've upgraded to Hardy which has pulseaudio installed by default.

---

### Post by YAOMTC on 2008-04-11
Yeah, I tried installing pulseaudio once, and even though I implemented the fixes listed there to make Flash and Java work with it, they still didn't work.

I'll try that when Hardy has its complete release. Maybe I can get this issue fixed then.

---

