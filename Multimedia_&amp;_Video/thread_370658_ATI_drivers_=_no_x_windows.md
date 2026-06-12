---
title: "ATI drivers = no x windows"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by wyth on 2007-02-26
I'm pretty sure there's an easy answer to this that I'm just not finding, so I'm posting for some aid.

Earlier I tried installing beryl with the [automatic script here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI").  Didn't work. So I tried to remove beryl.  I'm not even certain my donkey of a machine can run it.  But when I did remove it, I couldn't get X windows again.  It would always boot to a tty1 screen.

Did a dpkg-reconfigrere xserver-xorg, and when I chose ati, I can get back in.  But when I try to configure the fglrx drivers, I end up back at the tty1 screen.  (sudo aticonfig --initial, sudo  aticonfig --overlay-type=Xv; did do sudo depmod -a, did disable Composite in xorg.conf.) 

- lspci -n | grep 0300 gets me 01:00.0 0300: 1002:4c66 (rev 01)
- lspci | grep VGA gets me 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)

I can offer any more info as needed.  I kinda need the right drivers; this screen goes all wonky without them, making it hard to work. If I have to go back to beryl, that's fine, because it wasn't running anyway.  But I had my nice desktop that didn't degrade.

Help anyone?

---

### Post by wyth on 2007-02-26
Bumping this before I go to work.

---

### Post by wyth on 2007-02-26
Ooooh, come on now... I know some of you know what's going on here.  ;)

---

### Post by wyth on 2007-02-26
So far I'm the only one responding to my own post, and I'm not helping myself AT ALL.  

There has to be an answer to this; when I configure the ATI drivers, I lose X.  This never happened until I removed Beryl.  What do I need to reconfigure/fix so I can have X back and video card drivers that work?  These fuzzy screens are getting on my nerves.

---

### Post by web-keeper on 2007-02-27
I also had problems with my ATI onboard video card.  Have a look at my post at this thread, it might help

[http://ubuntuforums.org/showthread.php?t=365837&highlight=ati](http://ubuntuforums.org/showthread.php?t=365837&highlight=ati)

---

### Post by wyth on 2007-02-27
Thanks to web-keeper, but I tried everything on that thread, and many more, and no matter what I do, whenever I install fglrx and set it up, I reboot into a tty1 with no X.

C'mon, aren't there any wizards who've seen this before?  T.S. Eliot?  Bueller?  Bueller?

---

### Post by web-keeper on 2007-02-27
Sorry but can you just explain to me what  "fglrx" is...?

If you could also give me a breaf run down of what you are trying to achieve exactly, and how,  cause now you have confused me a little, (and that does not take much to do..!), so I can see if I can try and help further.

---

### Post by wyth on 2007-02-27
Sure -- fglrx is the ati display driver for my card, ATI Radeon.  To get the ati drivers working, you need to install xorg-driver-fglrx.  That's the standard driver.  And that's always worked for me in the past.  

However, I tried playing with Beryl, decided to remove it, and when I did,  I could no longer log into an X Windows desktop -- meaning I lost my desktop, I only had a command line login.

So I did a dpkg-reconfigure xserver-xorg to get get my desktop back, and I got it back, but with the standard Ubuntu video drivers, which don't work for me -- after a while, my screen goes all fuzzy.  That's why I went with the fglrx drivers in the first place.  So I tried to re-install the fglrx drivers, and every time I do, everything seems to go just fine, but when I reboot, I only get a command line and can't start X.  

I've done this plenty of times in the past, and can't grok what I'm missing this time.  And I have my system working just like I want it to, and I need it for work, and am very busy -- I really don't feel like re-installing my OS right now.  This is getting pretty frustrating.

---

### Post by web-keeper on 2007-03-01
Although I have not yet had to do this, but could you possibly try a rescue procedure..? using the rescue CD.

Just a thought..?

I will ask around the gang at work and see if they have any suggestions for you..

---

### Post by wyth on 2007-03-02
I'm not quite sure how it happened, but this thing has sorted itself out.  All's I can say is that eventually I had an update with a new ATI driver and a new xorg, and after that I gave the [standard ATI configuration]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") another try.  This time it took.  For the first time in a work week I have a properly-working X Windows system.  

But I'm still interested in Beryl...

---

### Post by shwan on 2007-05-18
Having similar probs, I can't get fglrx to work either with R250 - I have to reconfigure to ATi with:
sudo dpkg-reconfigure xserver-xorg
It works 100% fine with ATI drivers, but I want to have best hardware acceleration/support as I'm wanting to connect to a HD Samsung TV to play content off my PC and maybe HD content if the wireless connection can take it! =P
Shwan

---

### Post by wyth on 2007-05-18
Y'know, since AMD bought ATI it's been floundering.  And now there's [a call out there to get AMD to open up ATI's specs]("http://www.sharms.org/blog/?p=105"), which would give them a big popularity boost.  

If that happens, we may get the performance we need to actually run the system as it was meant to be run.  I don't blame Ubuntu at all, but it's kind of heartbreaking to have so much power just a few steps out of reach.

---

