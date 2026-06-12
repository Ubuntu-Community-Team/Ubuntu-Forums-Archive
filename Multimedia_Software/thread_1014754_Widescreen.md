---
title: "Widescreen?"
date: 2008-12-18
forum: Multimedia Software
---

### Post by Goshe on 2008-12-18
Hi,I am new here and new on Ubuntu :) I have syncmaster 943 nw and I cant setup larger resolution than 1280x1024 even I cant use widescreen.I found something on net that says I have to edit file in X11 directory but I don't beleive too much.So can anybody help me. I tried to install some drivers also and I get the message you are not logged as root.I have only one user

I have ECS GF8200a motherboard and AMD Athlon 5400+

thanks

---

### Post by Mahinva on 2008-12-19
Hey there, I do not own this board but was reading Newegg.com reviews and found the following:

> "Like others have stated if you dont change the HT from 200mhz to Auto your going to have issues with the screen. 1024x768 was highest setting without getting lines going across the screen or a big green spot on the screen. games ran very slow, But after i changed the settings i have not had any problems" - Reviewed By: zero2491 on 12/15/2008

I searched all reviews for the keyword "Ubuntu" and found this review:

>  Pros: Board has a great combination of features with HD audio & HD video, etc. So, I was really excited to try it out and see what it could do.

Cons: Just bought this board for my new Phenom 9850 system and I really wanted to install Linux on it... After 5 or 6 hours of trying different distributions and 3 different monitors I finally visited Newegg.com

Sure enough, other folks have commented that you *MUST* switch the BIOS setting for HT from "200 MHz" to "AUTO" in order to get the board to work.

I was getting severe flickering and I had just about given up on it, but that did the trick.

Other Thoughts: My guess is that the factory default setting for 200 MHz is severely restricting the video which should be Hyper-transporting at more like 1000 MHz or 2000 MHz, etc. This might explain why the (usually pretty good) auto-detection of Ubuntu & Dreamlinux that I was trying got tripped up.

Thanks to other reviews on this Forum, I think I'm going to try to keep this board and will write a review in another month or two to confirm that it stays in operation. A number of other reviewers have noted that the onboard video failed after 1-2 months.

I hope this provides some insight to you or anyone else who can help with the issue.

Out of curiosity, I've a few questions that I'd appreciate your feedback on, as I'm contemplating buying this motherboard.

- What version of Ubuntu are you using?
- Does onboard sound work?
- Aside from resolution problem, does onboard video work well?

I hope someone can help you resolve your problem - I have a 1440x900 monitor and may find myself in a similar situation.

---

### Post by Goshe on 2008-12-19
Well I hope that someone will help me (us):):)

About your questions,I am using Ubuntu 8.04 and I haven't tested audio or video on it. Because I do only compiling for now on Ubuntu. On WinXP works great

You can also read this
```
http://www.bigbruin.com/2008/ecs8200_1
```

---

### Post by IQRules on 2008-12-19
Try this in /etc/X11/xorg.conf file

Section "Screen"
        Identifier   "Screen0"
        **Device       "MATCH to your card"**
        Monitor      "Monitor0"
        DefaultDepth    24

        Subsection "Display"
                Depth       24
                **[COLOR="Red"]Modes       "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"[/COLOR]**        EndSubsection

EndSection

---

### Post by Mahinva on 2008-12-20
> **Goshe said:**
> Well I hope that someone will help me (us):):)

About your questions,I am using Ubuntu 8.04 and I haven't tested audio or video on it. Because I do only compiling for now on Ubuntu. On WinXP works great

You can also read this
```
http://www.bigbruin.com/2008/ecs8200_1
```

Thank you for the link! Here's a review I was reading: [http://www.legitreviews.com/article/837/1/](http://www.legitreviews.com/article/837/1/)

I hope IQRules' suggestion will solve your problem.

Cheers!

---

### Post by Goshe on 2008-12-22
IQRules that wont work. Gave to me only 800x600 resolution,but I am trying to find proper instructions for it

tnx anyway

---

