---
title: "weird fix for 9200se &quot;gamma&quot; issue -need experienced help Pls-"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by CyberCod on 2007-01-21
The video card is a Powercolor Radeon 9250SE, being recognized as a 9200SE.

I'm running Ubuntu Edgy, I've tried both downloading the installer from ATI, and using the fglrx from the package manager. Both give same results.

After installation the CRT looks washed out like the gamma is very very high. Every color looks pastel if you can see it at all.

I managed to get the TV-out working, and that looks great.  But you can barely make anything out on the monitor it looks so bad.

I then tried using a DVI to HD15 adaptor to attempt using my monitor on the other output of the card. Upon switching the cable over to the adaptor, and restarting X, I get message on monitor that X has crashed, and I get dropped to TTY.  Mind you, this is on the DVI.  
 If I then switch the cable back, I get a black screen.  If I blindly type in "startx" then it actually comes up **PERFECT** on both the TV and the monitor, but this only lasts until I reboot or restart X.

I searched about and added in
```

Option "SWcursor" "on"
Option "HWcursor" "off"

```
even though I found through trial and error that only one of those two commands actually is important.

and that fixed the gamma issue but the cursor artifacts that the "fix" causes are annoying as hell.

I know it CAN work, because of the weird thing I did with switching the cables... I just don't know how to get it to work correctly all the time.

If anyone can help, I'd appreciate it... please hurry, before I've pulled out all my hair.

I really think that it has something to do with how it recognizes the monitor, or initializes the HD-15 port with those drivers.

Any ideas of what to try?   Even crazy suggestions are ok.  I'm willing to try just about anything.  Voodoo?  Cool, i got chickens, I got a knife.  Say the word.

...HELP ME PLEASE.... SOMEBODY..... S.O.S...

---

