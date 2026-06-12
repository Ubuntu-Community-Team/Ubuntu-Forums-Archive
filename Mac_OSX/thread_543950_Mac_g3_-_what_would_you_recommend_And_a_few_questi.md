---
title: "Mac g3 - what would you recommend? And a few questions =)"
date: 2007-09-05
forum: Mac OSX
---

### Post by Tommerz on 2007-09-05
Hey everyone, altho this is a bit of an OSX question, I'm asking here due to my great respect for the Ubuntu community :popcorn:. If anyone has any other thoughts on what would be a cool thing to do with an Imac g3, let me know!

Today I aquired an Imac G3 biggrin.gif with a whopping 512mb ram :) (which is actually v. good, considering the system's age!!)

It's got osx 10.1 installed, which runs really well, but I've got a few problems :(

I'm having a few problems with disk permissions, and don't know how to fix them. Disk utility doesn't seem to work, and I would boot from dvd and run disk utility from there but I only have Tiger on dvd, and the Imac doesn't have a DVD drive sad.gif Does anyone have any idea how to sort this permissions problem out?

I'm also wondering what browser to use - it comes with internet explorer, which is very similar to it's Windows counterpart hence the desire for something a bit better :popcorn: I'm thinking either firefox 1.5 or seamonkey. Safari won't install cos the operating system is too old!!

Possibly connected to the disk permissions problem, I'm having trouble mounting dmg files for firefox and seamonkey, altho safari's mounted fine (but wouldn't install). Does anyone know if this is down to my operating system version or more likely to be permissions based? The only error I get is something to the affect of "File invalid". I've downloaded from several sources and had the same error message.

Also, does anyone have any tips for how to best use this awesome Mac. I'm considering installing xubuntu, but it'll spoil the vintage mac feel, especially if I have a fugly yaboot loader :confused:

---

### Post by marsmissionaries on 2007-09-07
buy an external DVD drive and install tiger that way perhaps?

---

### Post by twocargar on 2007-09-07
Hey Tommerz,

Which iMac G3 do you have?  Is it a slot-loading optical drive, or a tray-loader?  If it's a slot-loader, you can go all the way up to Tiger on it, but it may be unusable for you.  Tray loaders will only install up to Panther out of the box.  Also, pack in the RAM if you got it (up to 1GB on slot-loaders).

If your iMac has firewire, you can put it into target-disk mode, connect it to another Mac running the same or higher Mac OS, run Disk Utility and try fixing your permissions that way.  Otherwise, you can yank the drive & put it in an enclosure & connect it to your other Mac, OR drop it in a G3 or G4 tower (if you got one)--then run DiskUtility.  If that doesn't work you may need to reinstall.  By any chance did you put a 7200 RPM drive in it?

I have a 600MHz slot-loader that I run Mac OS X Server (10.4) on and it works great.  It's mainly a backup machine and a novelty.

I hope this helps,

TCG

---

### Post by Tommerz on 2007-09-10
Hey, chaning disk permissions via firewire sounds like a great idea ;) I'll have to double check my bro's mac mini has firewire.

Mine is a slot loader, I'm thinking of trying to get hold of Panther and loading that on - I like 10.1, but it won't run much software (only runs firefox1.0, no abiword) which makes it's usablilty pretty low :(

I'm thinking of using it as family machine for when people need to just look up train times or check mail.

Is it fairly easy to install more ram? I have a left over 256 stick from the mac mini which might fit :) which would give me 768 ram.

I havn't messed with the hardware at all, just left it as is.

Btw, I booted up feisty fawn on it just to see what it was like and it ran beautifully. I'm wondering whether I should consider this option, for a nice secure system. Only annoying thing is that beryl won't work (ati rage card), I'd love to be able to mimic Mac functionality with beryl :guitar:

The only thing is, I love Mac OSX + Apple too... is it possible to make yaboot optional ie: it doesn't appear unless you hold a key?

---

### Post by dynamicv on 2007-09-11
I used to have an iMac G3 400MHz.  If you know what you're doing it's very easy to stick in a larger hard disk and partition it for both Linux and OSX, although Linux was painfully slow compared to OSX due to the lack of graphics acceleration (this was on Ubuntu 5.04 though, it may be quicker now).  The fastest OSX on the machine was definitely Panther.  I believe Tiger has a number of altivec dependent optimisations which can't run on a G3 processor.  Tiger is also more memory hungry with all its add-ons such as widgets.

I don't think you can make yaboot optional, but you can set it with OSX as the default OS and stick a timeout on it, so unless you hit the L key within 5 seconds the Mac loads OSX.  Not quite as pretty as you want, but it would have the same effect.

---

### Post by twocargar on 2007-09-12
Yeah, 10.3.9 should run fine on it.  I installed 10.4 on a blue & white G3 tower with 768MB of RAM and it didn't run well at all.

As far as RAM, the Mac Mini's RAM won't work with it.  You need PC-100 DIMMs which are relatively cheap.

---

### Post by hellion0 on 2007-09-15
Well, with a G3 iMac, there's plenty of ways you can go.

OS: I'd go with maxed-out Panther, unless you absolutely positively NEED Tiger for something. Keep in mind that any G3 iMac (even my tray-loading 266MHz one sitting in the "to repair" pile) CAN run Tiger, but you may need a firmware upgrade - if so, do so BEFORE you try upgrading the OS! Afterward, it gets very, very messy to try. 
Browser (In order of preference): Safari/Webkit, Camino, Firefox, lynx, any other browser, IE for Mac. My opinion only, though.
Memory: Mac Mini memory will NOT work here! You need PC100 DIMMs, like you'd find in an older laptop. The tray-loader in my "to repair" pile had 512 when I started with it. 256MB of that now resides in my Thinkpad 600. Keep interchangability in mind.

---

### Post by Tommerz on 2007-09-18
Wow, thanks guys, awesome ideas, youve given me some excellent ideas :)

I think I'm gonna go for panther as the main os, and maybe dual boot with ubuntu so that I can sync more effectively with my laptop (maybe rsync tomboy notes and the like).

What's the best way to get hold of Panther? My imac doesn't have dvd capabilities, so I need to get it on CD :(

---

### Post by twocargar on 2007-09-18
Maybe eBay or smalldog.com

Apple had an exchange program for a while (when Panther first came out) so you could trade in your install DVD for install CDs, so I'm sure someone's got them.

Good luck

---

### Post by 3rdalbum on 2007-09-20
You can set Yaboot as optional, I did it accidentally once :-)

After installing Ubuntu, you boot up from the Mac OS X CD. This resets the NVRAM to start up the Mac OS partition automatically.

When you want to get to Yaboot, you hold down Command-Option-O-F on startup and type the following at the Open Firmware prompt:

```
boot hd:6,yaboot
```

Substitute "6" for whatever partition number the Yaboot is installed on. If you don't know, it's perfectly safe to try numbers from 0 to 13 until you get it.

---

