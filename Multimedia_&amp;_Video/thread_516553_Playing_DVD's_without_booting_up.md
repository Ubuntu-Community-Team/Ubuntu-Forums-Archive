---
title: "Playing DVD's without booting up"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by mjbarks on 2007-08-03
Hi everyone! (This is my first post)

I've heard rumours that it is possible to play DVD's and CD's with Linux. Is it true? Is it possible with Ubuntu?

Thanks in advance for help :)

Matt

---

### Post by buzzmandt on 2007-08-03
rumors? rumors are nasty, vile and often are backed with a grain of truth

but in this case, yes, you can play dvd's and cd's in any linux as long as the proper codecs are available/installed

---

### Post by LaRoza on 2007-08-03
I don't understand. You can play DVD's and CD's with Linux, if that is what you asking. What kind of CD are you talking about?

I also don't understand the title.

---

### Post by mjbarks on 2007-08-03
Wow, that was fast.

Sorry, I wasn't clear....

I'd like to know if it is possible to play DVD's or CD's without actually booting up the operating system?

---

### Post by buzzmandt on 2007-08-04
don't think so, you need codecs to "de-code" the "code" on the cd/dvd.  codecs must be installed into a player, which is installed into an operating system

---

### Post by lisati on 2007-08-04
> **mjbarks said:**
> Wow, that was fast.

Sorry, I wasn't clear....

I'd like to know if it is possible to play DVD's or CD's without actually booting up the operating system?

Probably not - the "Biult-in operating smarts" that comes with your computer, commonly known as BIOS (and more correctly known as Basic Input-Ouput System), and which will get called into play at some point when you turn your PC on, generally isn't designed to have the capabaility to play CDsor DVDs without some help.

Having said that, the CD-ROM on one of my computers can play CDs without calling up a suitable player. The catch is I have to plug in headphones to the CD-ROM drive.

---

### Post by mjbarks on 2007-08-04
I've heard that HP do something called 'quickplay' which runs on a 'small linux partition that uses a 2.4 kernel and mplayer to turn the laptop into a dvd player' what is this 'small linux partition'? Would I be able to do something like this to put on my PC?

---

### Post by Percius on 2007-08-05
Yes it is true that HP and others have "Instant Boot" Media devices. Yes they work. Yes you could install one on your pc.

To do this you would want to find / build a very minimalistic . If it doesnt have anything to do with processing, display, or sound you wouldnt want it. Since given this question I assume your running windows you would need to move your partition slightly with any number of partition management programs outthere and install such a partition. I would not reckernelomend useing Unbuntu for this as that installs way more then you need. 

I would be searching the web for it. If you cant find it you can always try HP. They should be forthcoming since its based on linux (note SHOULD).


[SIZE="5"]**BUT**[/SIZE]
The HP instant on system uses a stream lined bios too so that it can boot that fast, and the bios directly intercepts the keystroke and boots a different partition. Unless you want to make your own bios (NOT RECOMENDED) you will have to boot the bios (5-10s) grub (2-3s) and a micro linux distro with mplayer (3-20s depending on how tiny you can get it).

---

### Post by irw on 2007-08-17
HP used to use a linux based 'quickplay'; now it is a hibernated stripped down Windows,

---

