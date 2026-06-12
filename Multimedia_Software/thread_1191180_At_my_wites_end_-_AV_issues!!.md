---
title: "At my wites end - A/V issues!!"
date: 2009-06-18
forum: Multimedia Software
---

### Post by stonymd on 2009-06-18
I apologize in advance if this type of issue has been posted in the past, but, honestly I'm a bit overwhelmed. I had an old IBM ThinkPad R40 laying with a broken hard drive, so I bought a new 40gb hard drive and though I would give Linux a whirl. I downloaded and installed Ubuntu 9.04 Jaunty and loaded it up just fine. I also downloaded all of the latest system updates. I would like to use the laptop as a community PC for the family, strictly for the pre-packaged games and Internet use. On some graphics intensive websites (i.e. youtube.com, barbieworld.com or panfu.com) that the kids use, I was getting the big grey circle with the 'play' triangle in it. After clicking on the triangle, I would get some graphics, but, only one at a time on the website. I started playing around trying to troubleshoot my graphics problems (xorg.conf, etc) but have gotten nowhere. I've tried updating xorg.cong based on some info I found on the ATI website to no avail. I also have choppy audio problems. I found in these forums some information related to PulseAudio, but, I don't have that app. So, I have spent countless hours over the last 3 days trying to get somewhere, and am frustrated at this point. I am very new to Linux, but have a fairly technical background. If someone couple please be generous and help me with these issues, I would be eternally grateful. Any information that is needed, please let me know. Thanks in advance!!

---

### Post by fooman on 2009-06-18
have you installed flash?

running the following command in a terminal (applications > accessories > terminal) should install that and a few other goodies as well.  just type or copy/paste:

```
sudo apt-get install ubuntu-restricted-extras
```

after typing that out,  press enter followed by your password.   the password will be invisible as you type it,  so be sure to get it right. ;)

hope that helps.

---

### Post by stonymd on 2009-06-18
I ran that, and everything seemed to install OK. I did a fresh restart, and tried some of the websites again. I tried [www.panfu.com](www.panfu.com) (kids site; go to the site and press play and I get just a big white square in the middle of the page), [www.barbie.com](www.barbie.com) (another kids site; go to the site and the front page just flashes), [www.barbiegirls.com](www.barbiegirls.com) (another kids site; go to the site and the audio is ridiculously choppy and none of the links work. Also, when I go to youtube.com, the audio and video are also choppy (not as bad as the kids' sites, but definitely worse than my XP box). I ran the same video on my XP box and this ThinkPad and the quality is significantly worse on the ThinkPad running Ubuntu. What's weird is, when I have one of the kids' sites up, EVERYTHING slows down.. There's even a delay between each character I'm typing in this post! If it's any consellation, the R40 I'm using has an ATI Radeon Mobility 7500 graphics card in it.. I don't know if that helps at all. But, I'm no better than I was 30 minutes ago. :-)

---

