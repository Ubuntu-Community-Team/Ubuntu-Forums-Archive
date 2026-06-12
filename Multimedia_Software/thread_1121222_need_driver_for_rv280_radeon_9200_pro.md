---
title: "need driver for rv280 radeon 9200 pro"
date: 2009-04-09
forum: Multimedia Software
---

### Post by portdizzal on 2009-04-09
I have been fighting this for the longest time. I am running Ubuntu 8.10and i have a rv280 radeon 9200 pro video card. Does anyone else have this card? And if so, what driver are you using? i press, system->admin->hardware drivers and nothing comes up. completely blank.

---

### Post by markbuntu on 2009-04-10
Hardware driver is for getting proprietary drivers. Your card is no longer supported by ati proprietary drivers. The open source ati and radeon drivers fully support your card and are already installed on your system.

---

### Post by Cru1210 on 2009-04-29
i have the same problem... -_- i'm trying to run compiz with this card and nothing.

---

### Post by tinman6700 on 2009-11-12
Same here, 9200 pro, and absolutely no acceleration. I have tried a few of the step by step guides on here, all of which have resulted in an os reinstall, as the last two caused my computer to boot into the gui, and it was so garbled that I couldn't do anything with it. I am running the latest UUE, which I believe is based on 9.4. I know my graphics card is good, because it worked beautifully with uue 1.4, and windows xp pro. I am getting to my wits end

---

### Post by sawick61 on 2009-11-12
I have a 9600 with the same issue...no acceleration and no proprietary support.  I think I'm dropping ubuntu.  If I see one other person say, "they're already supported and installed" i'm going to lose it.  yeah they're installed i know...i can see what my screen is outputting however, its very shitty in quality.

---

### Post by shadetree1 on 2009-11-12
I have a 9250 with the open rv280 driver, it works great after I dumped X.  The compiz-config-settings-manager, gives complete control over the rv280.;)

shadetree

---

### Post by tinman6700 on 2009-11-12
> **markbuntu said:**
> Hardware driver is for getting proprietary drivers. Your card is no longer supported by ati proprietary drivers. The open source ati and radeon drivers fully support your card and are already installed on your system.

ok, well that has been said in a few threads, but what I need to know is how in the name of Zeus's butt do I enable those drivers. I know my hardware is a little bit older, but it's certainly no slouch, it's an Alienware for cryin out loud, and unlike a lot of the people who are having problems, I didn't upgrade, I did a fresh install

---

### Post by sawick61 on 2009-11-13
> **tinman6700 said:**
> ok, well that has been said in a few threads, but what I need to know is how in the name of Zeus's butt do I enable those drivers. I know my hardware is a little bit older, but it's certainly no slouch, it's an Alienware for cryin out loud, and unlike a lot of the people who are having problems, I didn't upgrade, I did a fresh install


if you're using that pc right now with ubuntu installed then it is already enabled...otherwise you wouldn't get any video output.  shitty i know, but thats the best quality ur gonna get on here.  you either have to use a legacy version of linux where the driver is supported or get a newer card.  or, use a diff legacy OS.

---

### Post by tinman6700 on 2009-11-13
ok, thanks for the help, at least I can stop beating my head against the wall, but that really sucks though

---

### Post by piccoloprincipe on 2009-11-26
Wait, I have your card and I have accelerarion with Ubuntu 9.04 (Jaunty).
```
[17:13:26][giorgio@Marty:~]$ lspci -nn | grep VGA && glxinfo | grep "direct"
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
direct rendering: Yes
```
The problem is in Ubuntu 9.10 Karmic the pc randomly crashes, and freezes if I run glxgears. I'm opening a bug for this regression but what distro version are you using?

---

### Post by Jerfo on 2009-11-26
I used to have a perfectly working radeon 9250 with both 8.10 and 9.04, all it took was following the instructions that about installing and adding lines to xorg.conf, they're somewhere in the ubuntu site but there's no way I've been able to make it work with 9.10, so my advice is look for that guide and don't get into 9.10! As far as I've been able to tell from all the research I've been doing, this is a fairly common issue :/

---

### Post by JulesBl on 2009-11-29
Yes I am getting problems with 9.10 and this card as well, stuff crashes and if a game changes the resolutions and goes full screen the system remains at that resolution till you change it back.

Jules

---

