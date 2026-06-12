---
title: "How can i get 2x videocard, 3x monitor setup to work in 9.10?"
date: 2010-03-30
forum: Multimedia Software
---

### Post by keep_it_simple_stupid on 2010-03-30
Suppose i'm this guy right there:
[img]http://www.tunjiafonja.com/photos/uncategorized/2007/06/13/billgatesoffice.jpg

And all i'm used to seeing is this:
[img]http://img340.imageshack.us/img340/7889/hurrdurrm.png

And clearly NOT this:
[img]http://kevux.org/turtle/documentation/Documentation_Pics/Configuring_Xorg_Display-2.png

And my technical expertise dates back to early eighties, a few lines of x86 assembly and a few lines of C. And i haven't written a single line ever since (got bloody rich since win 3.1 shipped).

How can i get my gorgeous (20" portrait 30" 20" portrait) setup workin'? Just like in ol' good win xp - each monitor is handled like a separate entity not merged together in one big screen?

A step-by-step guide would be perfect!

Both v-cards are ATI, supposedly working from the same drivers.

I don't mind using a different linux distribution, if it makes matters any easier.

Don't let the Bill down, guys.

---

### Post by keep_it_simple_stupid on 2010-03-30
Bump.
You disappoint Bill.

---

### Post by markbuntu on 2010-03-30
What cards are they?
If they are newer cards you can easily do that with a newer version proprietary fglrx driver from the ati site through the included catalyst control center. If they are pre 3xxx cards then you will need to wait until the new randr makes its way into the distros.

---

### Post by keep_it_simple_stupid on 2010-03-31
> **markbuntu said:**
> What cards are they?
If they are newer cards you can easily do that with a newer version proprietary fglrx driver from the ati site through the included catalyst control center. If they are pre 3xxx cards then you will need to wait until the new randr makes its way into the distros.

Got x1950 pro and HD4350.

Tried installing the drivers with envyNG (catalyst still didn't detect two vcards).

Downloaded newest proprietary drivers from ATI, that resulted in "invisible mouse pointer" and now finally ubuntu boots into a "black screen", no console, just a black screen. Good riddance.

What a joke of an operating system.
Can't even get the basics (multimonitor support) working.

Bill is hugely dissapointed.

---

### Post by knowledgeiswisdom on 2010-03-31
well one problem is your using ati try nvidia, better compatibility for most games (not all thou), your other problem (if your refering to bill gates) is thinking bill gives a crap (if bill is your name KISS let me tell you this refering to yourself in the thrid person is a sign of mental instability)

---

### Post by keep_it_simple_stupid on 2010-03-31
> **knowledgeiswisdom said:**
> well one problem is your using ati try nvidia, better compatibility for most games (not all thou), your other problem (if your refering to bill gates) is thinking bill gives a crap (if bill is your name KISS let me tell you this refering to yourself in the thrid person is a sign of mental instability)

Yeah, now i'm gonna buy TWO new nvidia video cards. No.

Bill probably doesn't give a crap, because he's using windows and windows has NO PROBLEMS AT ALL with multiple monitors, multiple GPU's and drivers.

I'm referring to Bill Gates, because he has the same monitor setup i have(see pic. above) and if he hypothetically would like to switch to linux, his gorgeous secondary screens wouldn't work and he most likely would be disappointed(although in a way happy that his OS is at least in one way better)

---

### Post by lavinog on 2010-03-31
You do not need to think about buying nvidia.
ATI made a promise to work with the open source community...every month they release a new fglrx driver, and each month they add new features and enhancements.
Right now, fglrx is pretty much up to par with nvidia...so all of the rants that nvidia is the only card that works with linux should be ignored.

I do not have your cards.  I have a 3650 and multimonitor support was pretty easy using catalyst.

When you installed ubuntu, did you install the drivers using the restricted hardware manager?
You mentioned envyng.  envyng was needed in the past when there wasn't an easy way to install fglrx.  Now ATI creates their driver with a working gui installer so envy-ng shouldn't be needed anymore.

The X1950 is not supported by the ATI drivers anymore in linux.  Even in windows it requires a legacy driver.
[http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx?type=2.4.1&product=2.4.1.3.13&lang=English](http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx?type=2.4.1&product=2.4.1.3.13&lang=English)
edit: To clarify:  The X1950 is only supported by the open source driver.  The HD4350 is not fully supported by the open source driver, and really can only benefit with the proprietary driver.  The open source driver will have better support for the HD4350 in Lucid...although I don't know if multi-monitor support will be available.

So the problem you are probably experiencing is that the old hardware is preventing the driver from enabling features on the new hardware.
You need to update or remove the old card to get dual-head to work.

---

### Post by lavinog on 2010-03-31
> **keep_it_simple_stupid said:**
> 
What a joke of an operating system.
Can't even get the basics (multimonitor support) working.

Just curious...does it work in windows with the latest drivers?


From your other thread:
> 
And I don't mind paying for something what works. Haven't had problems with windows like EVER.

[http://www.x.org/wiki/SponsorshipPage](http://www.x.org/wiki/SponsorshipPage)
let them know you would like to help the radeon project

The radeon team has done some amazing stuff with their driver...especially since they only recently got the documentation for the hardware.

---

### Post by littlepeon on 2010-03-31
ok....gonna make some assumptions to try and help ya....
1st i am going to assume that you are NOT this type of user here:

[http://lemmycaution.files.wordpress.com/2008/06/successful-troll-is-successful.jpg](http://lemmycaution.files.wordpress.com/2008/06/successful-troll-is-successful.jpg)

2nd i take it that you are NOT afraid to look up or use this page here:

[http://www.v7n.com/forums/attachments/google-forum/4512d1165587663-different-google-homepage-google.jpg](http://www.v7n.com/forums/attachments/google-forum/4512d1165587663-different-google-homepage-google.jpg)

the reason that people are telling you to use nvida cards (other than the fact that they are better than ATI-crap) is that this is intergrated into the nvidia setup configs and others have gone thru this pain before and have guides:

[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)

[http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

[http://www.linuxquestions.org/questions/linux-hardware-18/2nd-video-card-4-monitors-dell-inspiron-530-ubuntu-64-a-724170/](http://www.linuxquestions.org/questions/linux-hardware-18/2nd-video-card-4-monitors-dell-inspiron-530-ubuntu-64-a-724170/)



Seems like the program you need is Xinerama:

wow google search of that and ubuntu popped up this guide which has a section on nvidia ATI and matrox:

[https://help.ubuntu.com/community/XineramaHowTo#ATI](https://help.ubuntu.com/community/XineramaHowTo#ATI)


seems like pretty soon you can be this guy:

[http://www.youtube.com/watch?v=brG3-yyvv9Q](http://www.youtube.com/watch?v=brG3-yyvv9Q)

or even this guy:

[http://www.youtube.com/watch?v=N6Vf8R_gOec](http://www.youtube.com/watch?v=N6Vf8R_gOec)


please come back for further questions...we will kindly assist you 

-Peon

---

### Post by Kein.Problem on 2010-04-01
> **lavinog said:**
> Just curious...does it work in windows with the latest drivers?

From your other thread:

[http://www.x.org/wiki/SponsorshipPage](http://www.x.org/wiki/SponsorshipPage)
let them know you would like to help the radeon project

The radeon team has done some amazing stuff with their driver...especially since they only recently got the documentation for the hardware.
Yes, of course it works on windows XP without ANY problems.
No additional tweaks or anything. Works out of the box.

Sponsorship doesn't automatically grant me the feature i want, does it? :/

While the hardware might be considered old from gaming perspective, it's in no way old in terms of age. It is still quite sufficient for most non-demanding multiplayer games (TF2, W3, WOW, CSS, etc) and multimedia applications and is still more powerful than vcards found in most laptops. Which is why i'm not hasty with a purchase for a new one. But gaming is not something you can seriously consider if you're using linux anyway and i'm fine with that.

> **lavinog said:**
> 
I do not have your cards.  I have a 3650 and multimonitor support was pretty easy using catalyst.
There's a huge difference. Do you have two video cards and three monitors?

Two monitor setups might be doable, but three monitors from two vcards is where the problems pop up.

I did somehow manage to run two monitors from one x1950 videocard a year or two ago (when i only had two monitors) by doing some voodoo magic in xorg.conf.

> **lavinog said:**
> 
When you installed ubuntu, did you install the drivers using the restricted hardware manager?
You mentioned envyng.  envyng was needed in the past when there wasn't an easy way to install fglrx.  Now ATI creates their driver with a working gui installer so envy-ng shouldn't be needed anymore.

I tried it both ways, by using envyNG and later by using drivers directly from ATI page. Catalyst doesnt deal with multiple graphics adapters in linux from what i've seen.

> **lavinog said:**
> So the problem you are probably experiencing is that the old hardware is preventing the driver from enabling features on the new hardware.
You need to update or remove the old card to get dual-head to work.You make it sound like I have an old 3dfx card or something. It's not old-per-se and works perfectly in windows. And performance is still very good (not talking hi-end games here).

---

### Post by Kein.Problem on 2010-04-01
> **littlepeon said:**
> ok....gonna make some assumptions to try and help ya....
1st i am going to assume that you are NOT this type of user here:

[http://lemmycaution.files.wordpress.com/2008/06/successful-troll-is-successful.jpg](http://lemmycaution.files.wordpress.com/2008/06/successful-troll-is-successful.jpg)
I'm just trying to make my hardware work.

> 2nd i take it that you are NOT afraid to look up or use this page here:

[http://www.v7n.com/forums/attachments/google-forum/4512d1165587663-different-google-homepage-google.jpg](http://www.v7n.com/forums/attachments/google-forum/4512d1165587663-different-google-homepage-google.jpg)

Googled quite a few pages, didn't find anything dealing with THREE monitors and TWO ATI videocards. In fact, i found some ubuntu threads where people where trying to get the same setup working without any success.

> **littlepeon said:**
> 
the reason that people are telling you to use nvida cards (other than the fact that they are better than ATI-crap) is that this is intergrated into the nvidia setup configs and others have gone thru this pain before and have guides:

I'm sorry, but i'm not going to buy TWO new NVIDIA vcards.
> 
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)

Deals with multi-seat systems, not really relevant url. Only two monitors anyhow.

> 
[http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

Deals exclusively with NVIDIA.

> 
[http://www.linuxquestions.org/questions/linux-hardware-18/2nd-video-card-4-monitors-dell-inspiron-530-ubuntu-64-a-724170/](http://www.linuxquestions.org/questions/linux-hardware-18/2nd-video-card-4-monitors-dell-inspiron-530-ubuntu-64-a-724170/)

Again NVIDIA.

> 
wow google search of that and ubuntu popped up this guide which has a section on nvidia ATI and matrox:

[https://help.ubuntu.com/community/XineramaHowTo#ATI](https://help.ubuntu.com/community/XineramaHowTo#ATI)

Deals with only two screens.


> 
seems like pretty soon you can be this guy:

[http://www.youtube.com/watch?v=brG3-yyvv9Q](http://www.youtube.com/watch?v=brG3-yyvv9Q)

or even this guy:

[http://www.youtube.com/watch?v=N6Vf8R_gOec](http://www.youtube.com/watch?v=N6Vf8R_gOec)

Deals with newest top-of-the-line ati cards having "eyefinity" and more than two DVI connectors per videocard.

Thanks for support, but the problem still stands unsolved.

---

### Post by lavinog on 2010-04-01
> **Kein.Problem said:**
> 
You make it sound like I have an old 3dfx card or something. It's not old-per-se and works perfectly in windows. And performance is still very good (not talking hi-end games here).

I am not saying it is old due to gaming reasons.  I am saying that since ATI officially deemed that card as a legacy card last year, there is a high chance that the two cards are not compatible.

On your 4350, everything is processed as 3d (even 2d)...since 3d support isn't finished in the opensource driver, the ATI driver is your only option.
Your 1950 processes 2d differently than 3d.

I have never tried 3 monitors, but 2 monitors was pretty simple.
You should be able to open the catalyst control center and manage the different displays. (see screenshot/only have one display on this machine at the moment)

---

### Post by lavinog on 2010-04-01
Ok I found this in the fgrlx changelog:
```

fglrx-installer (2:8.721-0ubuntu1) lucid; urgency=low

  * New upstream release:
    - Restore compatibility with kernel 2.6.32 and xserver 1.7 (LP: #494699).
    - Add Passive Stereo support on workstation (FireGL/FirePro) hardware.
    **- Add Eyefinity support (more than 2 monitors on Radeon HD 5xxx hardware).**
      Officially WS-only but should work on consumer boards as well.
  * Port packaging to the new alternatives system (LP: #258038).
 -- Alberto Milone <alberto.milone@canonical.com>   Wed, 17 Mar 2010 10:14:45 +0100

```
This is for Lucid which will be released later this month.
I still don't know if it would work for your setup though.

In the end, if it doesn't work, you might want to stick with windows then.  You might be able to try again in October.

---

### Post by Kein.Problem on 2010-04-01
> **lavinog said:**
> Ok I found this in the fgrlx changelog:
```

fglrx-installer (2:8.721-0ubuntu1) lucid; urgency=low

  * New upstream release:
    - Restore compatibility with kernel 2.6.32 and xserver 1.7 (LP: #494699).
    - Add Passive Stereo support on workstation (FireGL/FirePro) hardware.
    **- Add Eyefinity support (more than 2 monitors on Radeon HD 5xxx hardware).**
      Officially WS-only but should work on consumer boards as well.
  * Port packaging to the new alternatives system (LP: #258038).
 -- Alberto Milone <alberto.milone@canonical.com>   Wed, 17 Mar 2010 10:14:45 +0100

```
This is for Lucid which will be released later this month.
I still don't know if it would work for your setup though.

In the end, if it doesn't work, you might want to stick with windows then.  You might be able to try again in October.

AFAIK, Eyefinity is a feature for the new hi-end Radeon GPUs namely HD 5xxx series. And i'm not planning a hardware upgrade in foreseeable future unfortunately.

---

### Post by Kein.Problem on 2010-04-01
Now i did a fresh install of 9.10. (i think i had a bit older version of ubuntu before)
It does indeed has dual-monitor support out of the box. It even has quite nice GUI for it. That's nice.
(please, keep in mind, we are after 3x monitor setup)

However once you enable the second screen, hardware acceleration disappears, and everything - even moving windows gets very choppy.

Now once i updated drivers to proprietary using ubuntu hardware devices tool, now i'm booting into a blinking unusable console (you can't even type propertly)

How can i remove the proprietary drivers and restore ubuntu into a working condition?

EDIT: solved, booted into recovery mode and deleted xorg.conf file.

---

### Post by markbuntu on 2010-04-02
I have had three monitors working with my HD3650 and HD3450 cards for about 9 months now using the proprietary fglrx driver. Before that is was a little buggy. Since about the 9.08 driver I have been able to set it up entirely with the Catalyst Control Center. It is very easy. Before that you needed to diable randr and turn on xinerama manually and it was very buggy with some card combinations. but that is all automatic now and should work with almost every card combination and dual gpu cards like the 3850X2 and 4650X2.  Compiz does not work properly with xinerama so turn off desktop effects before doing this.

What you need is two cards that fglrx supports, which means anything after 3xxx. If you have a newer 4xxx or 5xx card, and there are a lot of those, you need a very recent driver. If you have one older card and one newer one you will need to wait until the new randr is available (the current one does not support multiple gpus) and use the latest open source drivers.

Anyway, if you are using fglrx and have two recent ati cards, install the driver and

aticonfig --adapters=all --initial

You can the use the catalyst control center to configure your displays and the cards. It can get a little tricky and only one change can be made at a time. There are a bunch of old threads around here about this.

---

### Post by lavinog on 2010-04-02
> **markbuntu said:**
> I have had three monitors working with my HD3650 and HD3450 cards for about 9 months now using the proprietary fglrx driver. 
I almost PM'd you to ask you if you ever got this to work...for some reason I figured you would have.

---

### Post by markbuntu on 2010-04-02
> **lavinog said:**
> I almost PM'd you to ask you if you ever got this to work...for some reason I figured you would have.

Well, when we started trying the driver was not really able to do it even though it was supposed to and then there was a while with the xinerama and randr thing and now it just works. ATI has come a very long way.

I am not so sure that someone with one old and one new nvidia card would be able to do it since nvidia's new drivers do not support their old cards either.

It will be better when we can ditch these proprietary drivers completely. Now that multi gpu support is back in randr the open source drivers should support this but that will be in the next x-server release which is this summer hopefully.

I am hoping that we will get this capability  OOB in the fall distro releases.

---

### Post by Kein.Problem on 2010-04-03
> **markbuntu said:**
> Well, when we started trying the driver was not really able to do it even though it was supposed to and then there was a while with the xinerama and randr thing and now it just works. ATI has come a very long way.

I am not so sure that someone with one old and one new nvidia card would be able to do it since nvidia's new drivers do not support their old cards either.

It will be better when we can ditch these proprietary drivers completely. Now that multi gpu support is back in randr the open source drivers should support this but that will be in the next x-server release which is this summer hopefully.

I am hoping that we will get this capability  OOB in the fall distro releases.

Both are ATI cards. 
x1950 pro - supposedly the "old" one - considered "legacy" by ATI. You can't even install proprietary drivers for it in newest ubuntu, because the installer thinks your distro is too new or something.

HD4350 - the "new" one, can install proprietary drivers, however catalyst does not see second adapter - the x1950. aticonfig tool doest show the x1950 either.

ATI has following disclaimer in the "legacy" page:
> 
Any customers using a combination of a ATI Radeon&#8482; HD 2000 Series, ATI Radeon&#8482; HD 3000 Series, or ATI Radeon&#8482; HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst&#8482; releases made available past the ATI Catalyst&#8482; 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

But you can't install ATI Catalyst 9.3(which according to markbuntu should show multiple GPU's, right?) in ubunu 9.10 :/

Should i just try using older ubuntu? And which version of ubuntu would allow to install Catalyst 9.3?

Or my only option is a hardware update (both v.cards HD 4xxx series)?

---

### Post by markbuntu on 2010-04-03
Don't bother with 9.3 or anything older, the drivers before 9.3 did not do multiple gpus properly. If you got another 3xxx 4xxx or 5xxx card any of them should work with your 3450 without any problems. 

You could give the latest open source radeon driver a try. It is vastly improved lately. There is an ongoing thread about that here, you should ask there about using that and the latest X for multiple gpus.

In any case, if you are patient all this should be straightened out in the next year or so.

---

### Post by schmolch on 2010-04-27
Do you have to use xinerama to bind multiple ati gpus together or are the ati-drivers sophisticated enough to bind them at the driver level?
Because if you still need xinerama i am not interested.
I use triple-head xinerama desktops since a long time and the performance (for basic 2D things) is just horrible.

---

### Post by lavinog on 2010-04-27
> **schmolch said:**
> Do you have to use xinerama to bind multiple ati gpus together or are the ati-drivers sophisticated enough to bind them at the driver level?
Because if you still need xinerama i am not interested.
I use triple-head xinerama desktops since a long time and the performance (for basic 2D things) is just horrible.

Have you tried it lately?  I can't say if it is getting better, but things change each month.
From what I have read 2d performance regressed some with DRI2, but 3d performance has improved greatly.

---

### Post by schmolch on 2010-04-27
> **lavinog said:**
> Have you tried it lately?  I can't say if it is getting better, but things change each month.
From what I have read 2d performance regressed some with DRI2, but 3d performance has improved greatly.

Yes, im always using 3 screens on my Desktops.
Somebody who seems to know what he's talking about told me on the nvidia-forums that there are 3 ways to get a fast 3+ Screen setup in Linux:
- xgl (there is a howto here), lets just say its difficult.
- basically the advanced drivers that nvidia uses for windows, meaning the cards get combined at the driver-level (AFAIK)
- a Matrox video-splitter (triple-head-2-go), they seem great but are $300 a piece (and i would need 2).

---

### Post by lavinog on 2010-04-27
> **schmolch said:**
> Yes, im always using 3 screens on my Desktops.
Somebody who seems to know what he's talking about told me on the nvidia-forums that there are 3 ways to get a fast 3+ Screen setup in Linux:
- xgl (there is a howto here), lets just say its difficult.
- basically the advanced drivers that nvidia uses for windows, meaning the cards get combined at the driver-level (AFAIK)
- a Matrox video-splitter (triple-head-2-go), they seem great but are $300 a piece (and i would need 2).
I take it that you are using nvidia then.
xgl is a little outdated isn't it?
When you say the advanced drivers for windows, are you referring to nvidia's proprietary driver for linux?  Since nvidia stopped supporting the open-source drivers the proprietary driver is the only option now.

---

### Post by schmolch on 2010-04-27
> **lavinog said:**
> I take it that you are using nvidia then.

currently yes, i have used other cards in the past. you can use xinerama with anything.
> 
xgl is a little outdated isn't it?

its deprecated unfortunately but the only way to get a fast multi-gpu-desktop:
[http://www.youtube.com/user/d2globalinc#p/u/0/c1TOAXAbOAI](http://www.youtube.com/user/d2globalinc#p/u/0/c1TOAXAbOAI)

> 
When you say the advanced drivers for windows, are you referring to nvidia's proprietary driver for linux?  Since nvidia stopped supporting the open-source drivers the proprietary driver is the only option now.

I dont know. i dont know anything about drivers or windows or X. Did nvidia ever support the xv-drivers? Since im using a nvidia dualhead card the prop. nvidia-drivers are the only option.

---

### Post by markbuntu on 2010-04-28
> **schmolch said:**
> Do you have to use xinerama to bind multiple ati gpus together or are the ati-drivers sophisticated enough to bind them at the driver level?
Because if you still need xinerama i am not interested.
I use triple-head xinerama desktops since a long time and the performance (for basic 2D things) is just horrible.

You can use the ati proprietary fglrx driver with multiple cards and use the catalyst control center to set them up. It uses a proprietary xinerama  but works quite well except with compiz which I do not use anyway. I am pretty sure that nvidia does the same but I am not certain about that.

The next Xserver will remove the need to use xinerama for multiple gpus for all drivers since the Xorg devs have re-enabled the multiple gpu functions in the randr which will be part of it.

---

### Post by Kein.Problem on 2010-05-09
> **markbuntu said:**
> Don't bother with 9.3 or anything older, the drivers before 9.3 did not do multiple gpus properly. If you got another 3xxx 4xxx or 5xxx card any of them should work with your 3450 without any problems. 

You could give the latest open source radeon driver a try. It is vastly improved lately. There is an ongoing thread about that here, you should ask there about using that and the latest X for multiple gpus.

In any case, if you are patient all this should be straightened out in the next year or so.

The lucid lynx is out, is there any change? Can i finally get the 2xgpu, 3x monitors working?
(even the single GPU dual screen setup was crashing)

Is there a release date for this "issue to be resolved"? (i'm not sure which part of the whole thing is responsible for handling the 3x moni, 2x setup). Or is there a date to look forward to?

---

### Post by McCroskey42 on 2010-05-18
Editor's note:  we really should have a sticky somewhere entitled "Triple Monitors: Abandon Ye All Hope (or a Significant Chunk Of Money) Who Enter Here".  It might save people a lot of time, money, and lower their blood pressure significantly.

I've tried just about every configuration under the sun (2xRadeon 5850, 2xnVidia), followed every how-to I could find, and spend at least 30+ hours repeatedly SSHing into a desktop with a hung X server trying to get a setup like this working. After all that effort, the best advice I can give to someone trying to do the same is "Don't Bother".  Because out of the box, it just doesn't work, and once you have three monitors working, there are serious limitations.

As for Lucid fixing things...I previously had a desktop with 2x Radeon 5850 and 3x HP 2709 monitors working under Karmic with the 10.3 proprietary drivers and Xinerama.  It worked...sort of.  Most accelerated features like Compiz were out, video playback was awful, and Eclipse would randomly get confused about window placement.  When I upgraded, Lucid steadfastly refused to acknowledge the existence of the second card or the third monitor, no matter how I poked and prodded xorg.conf, amdccle, or aticonfig.  We've standardized on 10.04 desktop and server, since it is the next LTS, but everyone who walked into my office for a month would immediately say "Hey, why is your left monitor off?"  As you can imagine, this did not make me a happy penguinista.

If you want a functional configuration, get a card with two DVI outputs of any recent vintage and hang a Matrox TripleHead2Go off one of the outputs.  It really is the only way to get OpenGL/VDPAU/Compiz or any other nifty technology working reliably with more than 2 monitors under Linux.  If the $300 price tag scares you, keep in mind that between the Radeons, nVidia cards, and that infuriatingly hard-to-find DisplayPort dongle that some forums claimed would enable a third monitor if/when the mythical ATI Eyefinity driver that supports it ships, I've spent nearly $1000 trying to get a configuration in Linux that replicated functionality present in Windows XP *back in **2003*.

Lest this seem like an angry anti-Linux rant:  I love Linux.  I've used it as my personal desktop since 1995, and I still have my original Slackware floppies sitting in a box on my desk.   I run my entire company on exclusively open-source software, desktop and server, with nary a Windows desktop to be seen.  Unfortunately,  this is one feature where Microsoft's offerings put Linux to shame.

---

