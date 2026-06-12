---
title: "Banshee memory leak..."
date: 2009-04-15
forum: Multimedia Software
---

### Post by racerraul on 2009-04-15
Has anyone using Banshee noticed that the longer it plays the more memory it uses?

I tend to leave it running all night during my shift, and after 10+hrs it is taking over 400-500mb ram.

This isn't a big deal for me... I have 8g of Ram, but I was wondering if anyone else noticed it...

other than that I have come to like it more than RB.

---

### Post by Davsdu on 2009-04-16
I haven't checked the memory usage, but it's using more RAM and CPU usage than RB. At least that's how it feels. I love Banshee, but it would be great if it could become lighter in some way, like Rhythmbox. But I guess you can have it all. How many other Linux multimedia players which have media library + both music and video player included are there out there?

---

### Post by gustaf. on 2009-06-14
> **racerraul said:**
> Has anyone using Banshee noticed that the longer it plays the more memory it uses?

I tend to leave it running all night during my shift, and after 10+hrs it is taking over 400-500mb ram.

This isn't a big deal for me... I have 8g of Ram, but I was wondering if anyone else noticed it...

From top:
```
31513 gustaf    20   0 1739m 924m 8188 R    1 23.5 262:48.99 banshee-1
```924 mb of ram. That's not just "too much" or even buggy, that's insane. I seriously cannot find it reasonable for banshee to eat more than 50mb, but given it's .net, I'd say 100mb. At most!
It's getting seriously irritating that there simply is no good enough media library/player in linux that doesn't grow like a virus and swallows all your memory after a couple of days. My firefox just crashed, after having eaten approx 2gb memory, and X.org is not really doing its job well neither, simply stealing 500 megabytes from me:

```
31513 gustaf    20   0 1739m 924m 8192 R    0 23.5 262:53.89 banshee-1
7823 root      20   0 1201m 500m  12m S    2 12.7 351:10.49 Xorg
```I've talked to X developers on IRC about these issues regarding X, and filed bugs here and there regarding all kinds of programs that steals too much memory (gnome-panel [the applets], gnome-terminal, pidgin, etc), but no one seems to think this is a problem. I would have to restart my 4gb machine almost every day to have a reasonably decent system running.
Next machine will be at least 16 gb. I will hope that is enough for modern gnu/linux systems.

---

### Post by ghaefb on 2009-08-12
I can confirm that also. Running banshee for a couple of days and the memory usage grows to 1Gb of ram almost every time.

This is a serious issue and we need to inform banshee developers asap.
It could be the ubuntu build specific issue, but I'm not sure.

---

### Post by TMAN 1 on 2009-08-12
I haven't noticed it.And Banshee is awsome.I didn't like Rythmbox so much,but it is an okay player.

---

### Post by glorinand on 2009-09-12
This is really awful... If you didn't notice, just open up gnome-system-monitor, and change playlist in banshee... Every time you do that, memory usage grows... I am not sure I want to use a media player that has to be restarted every time I change the playlist... XD It really seems like it uses enough memory *without* doing that...

However, now that I am writing this I noticed that the behaviour might have changed in the version I just downloaded after all... Let's see... XD

Hmm... actually, it's happening again... Such a shame, if you ask me...

---

### Post by dutchhome on 2009-09-28
This is actually related to plugins, I believe.  If you turn off all of them, it seems the memory doesn't climb.  I haven't tracked down exactly which one(s) are causing it though.

---

### Post by brendanpiater on 2009-10-15
Track this here: [https://bugzilla.gnome.org/show_bug.cgi?id=555365](https://bugzilla.gnome.org/show_bug.cgi?id=555365)

---

### Post by nortexoid on 2009-10-21
For me Rhythmbox **always** uses around 5-8% CPU while Banshee uses the same and first and then eventually grows to 20-30% over time. This is with Banshee 1.6 Beta 2 (1.5.1). Weird, and unfortunate since, besides this problem, I do like Banshee more, especially with 4th gen. iPod syncing.

---

### Post by nortexoid on 2009-10-21
For me Rhythmbox **always** uses around 5-8% CPU while Banshee uses the same and first and then eventually grows to 20-30% over time. This is with Banshee 1.6 Beta 2 (1.5.1). Weird, and unfortunate since, besides this problem, I do like Banshee more, especially with 4th gen. iPod syncing.

---

### Post by Kabezon on 2009-10-31
I didn't notice the RAM problem until today on my friend's new laptop, which he got for only $180... After about 2 hours he noticed Conky showed "RAM:78%" lol He's back with Exaile for now :P

Have you also notice how your CPU will go 99% if you use Conky to show what Banshee's playing? This sucks :S Banshee gives great audio quality, the EQ is just great, that's the main reason I switched to it :S I'm gonna have to go back to Amarok, I guess...

---

### Post by ene_dene on 2009-11-09
Same problem here on 9.10. 1.51 banshee.

---

### Post by akraievoy on 2009-11-12
> **ene_dene said:**
> Same problem here on 9.10. 1.51 banshee.

Yeah, same here, it ate up 1.6 GB in several hours. Plain vanilla Karmic with 1.5.1 (which reports itself as 1.6 beta 2). 

I'll try to spot the offending plugin (if that's a plugin, and not mono Garbage Collector itself, ;) ) and report that to the development team. Links to proper issues (maybe someone has more time to tinker with that).

[https://bugzilla.gnome.org/show_bug.cgi?id=555365](https://bugzilla.gnome.org/show_bug.cgi?id=555365)

[https://bugzilla.gnome.org/show_bug.cgi?id=586052](https://bugzilla.gnome.org/show_bug.cgi?id=586052)

---

### Post by ene_dene on 2009-11-13
> **akraievoy said:**
> 
I'll try to spot the offending plugin (if that's a plugin, and not mono Garbage Collector itself, ;) ) and report that to the development team. Links to proper issues (maybe someone has more time to tinker with that).


If you find something also post it here. It's just terrible that I have to go back to rhythmbox, banshee looks so damn good.

---

### Post by akraievoy on 2009-11-13
> **ene_dene said:**
> If you find something also post it here. It's just terrible that I have to go back to rhythmbox, banshee looks so damn good.

Okay, so far I have the following info:
The only enabled plugins are
[LIST]
[*]Audio CD Support
[*]Cover Art Fetching
[*]last.fm Radio and Scrobbling
[*]Multimedia Keys
[*]Notificaation Area Icon
[*]Play Queue
[/LIST]

The queue was set up to fetch tracks randomly from one playlist of 620 tracks by ratings. My 3.5 GB RAM was used up in approx 8 hours of ambient music: one track per 7 mins on average, I did not skip any tracks today.

The process banshee-1 had in top 2494m of VIRT, and 1.7g in RES, and - what was remarkable too - process notify-osd had 1027m and 531m in RES.

I guess I would try plugging off that Notification Area Icon and checking what the stats would be.

---

### Post by zi99y on 2009-11-17
Banshee is one of the nicer looking players with decent features but I get horrific cpu usage spikes with it. I have a (nicely organised) library of 160Gb or so, maybe it just doesn't deal well with large libraries. I've deleted the profile and rescanned it but the cpu spikes just come back making the app unusable until it's finished whatever it was doing.

For the record I have an intel quad core system with 3gb ram, running 64bit karmic.

Tempted to try mediamonkey in wine :/

---

### Post by akraievoy on 2009-11-17
> **zi99y said:**
> I've deleted the profile and rescanned it but the cpu spikes just come back making the app unusable until it's finished whatever it was doing.

Khm. Are those spikes occuring randomly? If there're no obvious event triggers - this one looks quite like mono garbage collector (and/or possible memory thrashing). Asking about that as this might shed some light on our memory leak problem.

**Btw, now after I disabled the Notification Area Icon - my memory usage does not grow that much.** I'll report in couple of days - as I collect more or less consistent data on this...

---

### Post by zi99y on 2009-11-17
yes they're pretty random, although I have noticed that when a track finishes playing there will sometimes be a long pause, I'll switch to banshee and the window will be completely white, eventually the next track will play.

if there's anything I can try / provide logs to help, let me know. I'd prefer to use this app than the others I've seen. 

Another annoyance was the last.fm scrobbler didn't seem to work.

---

### Post by nortexoid on 2009-11-18
> **racerraul said:**
> Has anyone using Banshee noticed that the longer it plays the more memory it uses?

I tend to leave it running all night during my shift, and after 10+hrs it is taking over 400-500mb ram.

This isn't a big deal for me... I have 8g of Ram, but I was wondering if anyone else noticed it...

other than that I have come to like it more than RB.

I just noticed the memory leak issue. Also CPU usage goes up over time on my system. I'm using Karmic and ver. 1.5.1 (1.6 beta 2). This has been an ongoing problem for what seems like ages.

---

### Post by aPaSv5 on 2009-11-18
I've noticed the same thing, but with Inkscape in previous Ubuntu versions.

When I only had 384MB (only a number of months ago!), I'd find my machine bogged-down in no time at all.

I don't know if the latest version fixed this problem.

---

### Post by nortexoid on 2009-11-19
Hiding and revealing Banshee (via the notification icon) causes about 0.1MB of memory to be eaten up. So roughly ten hides/reveals eats up 1MB of memory.

Now, if rhythmbox had some sort of itunes import I would be very tempted to switch, at least until Banshee sorts out these issues.

---

### Post by Major_Kong on 2009-11-19
> **nortexoid said:**
> Hiding and revealing Banshee (via the notification icon) causes about 0.1MB of memory to be eaten up. So roughly ten hides/reveals eats up 1MB of memory.

Now, if rhythmbox had some sort of itunes import I would be very tempted to switch, at least until Banshee sorts out these issues.

I believe rb is at a dead end in terms of new features, unless new developers appear. You could always check if Songbird has the features you want.

---

### Post by joshzam on 2009-11-19
> **zi99y said:**
> yes they're pretty random, although I have noticed that when a track finishes playing there will sometimes be a long pause, I'll switch to banshee and the window will be completely white, eventually the next track will play.

if there's anything I can try / provide logs to help, let me know. I'd prefer to use this app than the others I've seen. 

Another annoyance was the last.fm scrobbler didn't seem to work.

This is the exact memory problem I've been experiencing. When a new track starts playing in Banshee, the CPU and memory usage will spike and stay that way for about 40 seconds, leaving the app completely unresponsive with the music (usually) playing in the background. I have disabled every plugin and nothing helps. Sometimes the program freezes and crashes my entire system! I was really hoping Banshee would be my new go-to music app.

---

### Post by directhex on 2009-11-19
> **joshzam said:**
> This is the exact memory problem I've been experiencing. When a new track starts playing in Banshee, the CPU and memory usage will spike and stay that way for about 40 seconds, leaving the app completely unresponsive with the music (usually) playing in the background. I have disabled every plugin and nothing helps. Sometimes the program freezes and crashes my entire system! I was really hoping Banshee would be my new go-to music app.

Check the settings - have you enabled BPM detection?

---

### Post by joshzam on 2009-11-20
> **directhex said:**
> Check the settings - have you enabled BPM detection?

As I said, I have disabled ALL of the extensions in the Preferences - including BPM detection. All of them, and the problem continues.

---

### Post by lunatico on 2010-05-04
Well I've been using Banshee for years now but it has gotten very unusable lately, performance is bad. High cpu and memory utilization.

The only reason I kept using it was because of nice osd notifications on every song and for the scroll on top of notification icon to change song feature. With Rhythmbox I hated the fact that osd notifications only showed when the main window was closed... until today that I went into the plugin preferences and realized this is configurable.
Edit -> Plugins -> Status Icon -> Configure -> Notifications = Always Shown

Bye bye Banshee.

---

