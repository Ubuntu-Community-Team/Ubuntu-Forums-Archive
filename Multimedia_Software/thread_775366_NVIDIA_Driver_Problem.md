---
title: "NVIDIA Driver Problem"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Eidolons on 2008-04-30
So I have fixed Flash and Rhapsody (my previous posts).  I'm now a few steps away from having everything setup exactly right.

I have a GeForce 8600M GT.  When I first started up using Ubuntu 8.04 (I was using Windows Vista previously but used Ubuntu on my other computers before) it suggested that I download an nVidia driver.  I did so and restarted.  What I got when it came to the GUI was a scrambled screen.

I read a bit into the problems with this card and my problem doesn't seem similar.  It seems a lot of people were having a problem with the screen going blank.  My screen is not blank, it is just filled with little lines of blue and gray.  They don't move in any way though.

I tried to disable the splash screen like some suggested.  Didn't do anything.  In the end I just changed 'nvidia' to 'nv' in xorg.conf in order to boot.  When I got back in the GUI it said that the 'nvidia' drivers were "in use."

I would really like to get this working properly.  It seemed a lot of people were having problems with this particular card.  Any help or suggestions would be appreciated.  Tell me if you need more info.

---

### Post by Padie on 2008-04-30
Maybe try Envy - search the package manager for "envy" or if it's not there, Google is your best friend, install it, and go to Applications -> System Tools -> Envy. Follow the instructions. Basically, this will download the latest driver for you and reconfigure your system to work with your card etc. At the end when it asks you if you want it to configure your Xorg file for you, LET IT!

Hopefully that will work. Hasn't failed on me yet!

---

### Post by Eidolons on 2008-04-30
Nope.  I tried that before I made the post.  Had the same exact result.  I also went and installed it manually using nVidia.com's driver (same one as the other two).

It seems that this particular card is not good for Ubuntu (or Linux in general).  My computer works fine, I just wanted the super-cool 3D effects. :P I was looking at other threads about this card and it seems no one can get it to work properly.  Usually when you read those support threads there will be some looking for help then some saying, "My GeForce 8600 GT works perfectly."  Not in this case.  Everyone seems to be SOL with this card.  I will look into switching if a solution is not made available in the near future.

---

### Post by babylon2233 on 2008-05-01
Just install envyng-gtk. It's work for me but make sure you already remove all nvidia driver before using envyng-gtk
```

sudo apt-get install envyng-gtk
```

After that go to system tools...Then you may install ur driver.

---

### Post by Zorael on 2008-05-01
This is obviously in Hardy, hmm? Did you do a fresh install or upgrade?

---

### Post by njparton on 2008-05-01
There seem to be a lot of hardy related video card bugs around this forum at the moment with a lot of people retreating back to 7.10 until they're fixed.

---

