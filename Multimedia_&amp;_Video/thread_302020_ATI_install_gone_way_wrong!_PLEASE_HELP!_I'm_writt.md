---
title: "ATI install gone way wrong! PLEASE HELP! I'm writting this from lynx!!"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by TrueJk7 on 2006-11-18
Hey, lol, this is really really sad. 

OK, I installed the recent ATI graphics Driver per the ubuntu wiki on how to do it. However I dont have the link because I am working by terminal right now (since the GUI will not come up) and I dont have the link to the wiki I used. So I would Like to know how to restore ubuntu to what I did before I installed the ATI Graphics. I appoligize for not searching the forums to find the answer only because I am using "lynx" (the text/terminal based www engine). So PPLLEEAASSEE Help me here. 

I did go into the dpkg and uninstall the ati driver there, then I went in /etc/X11/xorg.conf and removed the additions I made at the bottom and restarted but no real luck. 

So please, I'll keep this link written down until we all get this figured out. 

Thanks again
Jake

---

### Post by Antrix on 2006-11-18
If by ATI graphics driver you mean the fglrx driver (official binary from ATI), then change your Driver entry in xorg.conf FROM fglrx TO radeon. Now the open source (default) ati driver will be used instead.

Try this first. I assume you just changed the composite extension stuff earlier which is not sufficient.

---

### Post by tseliot on 2006-11-18
type:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "ati" driver (instead of "flgrx") and press ENTER whenever you don't know the answer to a question.

then you can access the desktop environment in the following way:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by TrueJk7 on 2006-11-19
Hey Guys, thanks again. I ran into some more issues after I posted and before I heard back. 

problem is after I ran into this thing I tried to use the Rescue CD just hoping that there was an option to reinstall the desktop interface, Found there was not. the rescue failed and then when I picked ubuntu under GRUB... nothing happened. I got where I could enter text and that was it. So i had to do a fresh install. Thanks for the responses I will be looking into this next time I try to install the *right* driver.

Thanks,
jake

Ps. Anyone know about wifi? [http://ubuntuforums.org/showthread.php?p=1777420#post1777420](http://ubuntuforums.org/showthread.php?p=1777420#post1777420)

Thanks

---

