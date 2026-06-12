---
title: "Questions about LIRC, iMon &amp; Mythtv"
date: 2009-02-09
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-09
I have an Antec Fusion Remote black htpc case, and after wrestling with several guides for getting the iMON 0038 LCD working with LIRC over the past week I have finally gotten the RM200 remote working perfectly. 

All of these guides state you MUST uninstall LIRC 0.8.3 which comes with MythBuntu 8.10. My question is, is this totally necessary? LIRC has a load of MythTv related dependencies, so ny uninstalling LIRC you strip out a load of MythTV related items (Including mythtv control centre).

Would it be possible for instance to leave LIRC 0.8.3 installed and just copy the LIRC 0.8.4 modules over the top? Or is this going to cause other issues?

---

### Post by nicoloks on 2009-02-09
To be exact, LIRC has the following Mythbuntu dependancies;

mythbuntu-common
mythbuntu-control-centre
mythbuntu-desktop
mythbuntu-lirc-generator

---

### Post by fatmonk on 2009-02-10
Nikoloks,

Could you describe what you did in the end to get the RM200 working? (That is the one with the Pad in the middle isn't it? And you've got it working with the built-in IR receiver in the Antec case? - if so that's exactly what I've been struggling with for months now).

-FM

---

### Post by nicoloks on 2009-02-10
When I say working, I mean it is showing all keypresses when running irw. I'm still to sort out getting it to work in MythTV. Just so happens that mythbuntu-lirc-generator was one of the components uninstaled when uninstalling lirc 0.8.3. When I figure out how to get this remote working with MythTV I can post my notes if you like?

---

### Post by fatmonk on 2009-02-10
All buttons working would be a big leap forward for me!

I'm still at the stage of only having the Nav Pad, mouse click and number buttons working (or was, I have a Hauppage receiver and remote with the same at the moment, but would prefer to have my RM200 working).

I'm confident that once I get all buttons being received correctly by lirc / irw, then once I record a config file and tweak the mythtv config then all will be good. That's the transparent bit, getting lirc to see the remote and for all key presses to turn up in irw is the struggle for me at the moment.

As I've said in previous posts, I suspect a HAL problem, but haven't got very far looking into that just yet.

Will be trying to upgrade to lirc 0.8.4a in the next night or two to see if that gets me any further...

-FM

---

### Post by nicoloks on 2009-02-10
Do check out 0.8.4a as there is a conf file in the remotes directory for the RM200. Have a look at the lircd.conf.imon-antec-veris file when you get it installed.

---

### Post by barras on 2009-05-11
Hi all, 

my case is thermaltake dh101 with iMON 0038 LCD. Following all the instructions found in this forum and in other sites I managed to have my remote "almost" properly working with Mythbuntu-9.0.4 and lirc-0.8.4a. I say almost because I can't use the channels and the arrows buttons. I'm sure that it's not only a problem of a misconfiguration of my lircd.conf, because when I test may remote with irrecord, nothing happen when I press channels and arrows buttons.

Please help me.

Regards,

Fabio

---

