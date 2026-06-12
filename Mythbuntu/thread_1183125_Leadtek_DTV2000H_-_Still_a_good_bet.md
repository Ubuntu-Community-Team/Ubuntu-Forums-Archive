---
title: "Leadtek DTV2000H - Still a good bet?"
date: 2009-06-09
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-09
Hi all,

I have been scrounging around for a good TV card that will most likely work on my Ubuntu based HTPC currently under construction using Jaunty, MythTV and XBMC.

From my general research it seems that the above mentioned card (Revision J) would be the go, and better yet as its been around for a while now its pretty cheap. The problem is when I went to the Leadtek/Winfast website to check it out it is listed as a discontinued model.

Now I have no problems getting it as it seems to be in stock everywhere, and seen as they are new (not 2nd hand) I'm sure they will work fine. So my question is should I go for that card, or spend a few more $$$ and get a newer model like the 2300 or something? I'm no TV-Tuner fanatic so my knowledge is limited at best. All I will be doing is watching, rewinding, pausing and recording live TV. 

If the 2000H is still a good bet then I'd prefer to go for it as it *should* work well.

Just after general opinions and any trapfalls really.

Thanks!

- Matt

---

### Post by laffinet on 2009-06-09
I've got 2 of these cards in my Mythbox, work fine. I'm running 9.04, can't remember if they worked out of the box or if I had to do something with /etc/modprobe.d/options (which was necessary on 8.10, but really simple so don't worry).
If you shoot me a message or post back here I can check when I'm back home.
Things I haven't bothered with are getting radio to work and using the remote (I'm using a separate USB remote). Both have been done by others, though (I think).

---

### Post by Mattaus on 2009-06-09
Yeah I have a post book marked from here that describes what line you need to add to the modprobe.d file. I had tried it with a Videomate T750 I had (but gave away) so I can't see it creating any issues.

As for the remote I dropped $180 on that mini dinovo keyboard thingy not more than 2 weeks ago so 'm going to get as much mileage out of that as possible lol.

I hadn't thought about radio at all until you mentioned it. Seen as my HTPC is going to be (rather will be once I've ironed out my hardware issues) the centre of all my media then it may be worth the effort.

Thanks for the reply! Might grab myself a card later this week :D

---

### Post by owg582pdu on 2009-08-07
Hi,

installed a LeadTek DTV2000H Plus rev J card into a 2.6.28-14-server without luck
modified /etc/modules and /etc/modprobe.d/options but the card still doesn't work.
Any one had luck getting this card to work?

---

### Post by Mattaus on 2009-08-07
It worked straight out of the box for me! At least I can't remember doing any modifications.

I did not need to modify any files what-so-ever as far as I can remember. It's been a while since I touched it as it's been humming along in my HTPC without hassle now since my last post.

I wish I knew why sometimes things worked without trouble and sometimes they didn't. They same thing happened to my wireless card - worked straight out of the box.

How do you know it's not working? What are you using to test it? For example I'm running it through MythTV...

---

### Post by owg582pdu on 2009-08-08
output from dmesg

[    8.520186] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    8.520188] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.520191] cx88[0]/2: subsystem: 107d:6f42, board: WinFast DTV2000 H [card=51]
[    8.520193] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.520194] cx8802_alloc_frontends() allocating 1 frontend(s)
[    8.543842] cx22702_readreg: readreg error (ret == -6)
[    8.543896] cx88[0]/2: frontend initialization failed
[    8.543898] cx88[0]/2: dvb_register failed (err = -22)
[    8.543900] cx88[0]/2: cx8802 probe failed, err = -22
[    8.580241] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    8.580244] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.580247] cx88[0]/2: subsystem: 107d:6f42, board: WinFast DTV2000 H [card=51]
[    8.580248] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.580250] cx8802_alloc_frontends() allocating 1 frontend(s)
[    8.581060] cx22702_readreg: readreg error (ret == -6)
[    8.581114] cx88[0]/2: frontend initialization failed
[    8.581116] cx88[0]/2: dvb_register failed (err = -22)
[    8.581117] cx88[0]/2: cx8802 probe failed, err = -22

there is no /dev/dvb device

---

### Post by theo404 on 2009-08-16
See this thread:

[http://ubuntuforums.org/showthread.php?t=1226048]("http://ubuntuforums.org/showthread.php?t=1226048")

The DTV2000H **PLUS** uses a different chip that is as yet unsupported it seems.

---

