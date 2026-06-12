---
title: "Total newbie in need of help with installation please"
date: 2012-09-10
forum: Mythbuntu
---

### Post by theonewhoshallnotbenamed on 2012-09-10
Hi all 

Ok so I am familiar with the frontend of Mythbuntu and have used it frequently on a machine on which it was installed and has been maintained by my housemate.  I am now moving out, and don't have a housemate who knows MythTV lol but I want to have my own MythTV on my machine.  

So basically I need step by step instructions please on how to a) get the software b) install it and c) maintain it. 

I realise that it is not actually as simple as those three steps but that's the direction I want to be heading in. 

Only thing is, I am not a proficient terminal user either.  I can do step by step copying but I have no idea what any of it really means.  

I fear I have a lot of learning heading my way :-/ 

Thanks all in advance.  Please keep it simple!!

---

### Post by opensshd on 2012-09-10
Ok, I've never actually used MythTV, but I do see that it is in the repositories (available software for UbuntuOS), so if you have Ubuntu 12.04 installed, it should be just

sudo apt-get install mythtv

Configure and go.

Not sure about how to hardwire your TV signal through your computer though. I imagine it needs a card that supports coax cable or a cable box that supports ethernet, hdmi or something... that I do not know.

---

### Post by crbnrod on 2012-09-10
I don't want to discourage or come off as a jerk or anything, but if you're stymied on these steps, mythtv may not be the hobby/project for you. That said, go here:

[http://mythbuntu.org/download-type](http://mythbuntu.org/download-type)

click the link that applies to you and follow the directions.

---

### Post by anonymousdog on 2012-09-10
So, first thing to determine is: What capture card do I need?  This is determined by your signal type (i.e., satellite or other set top box [STB], over the air, unencrypted cable, etc.)

Next, you'll probably build a combined back end AND front end machine around a good video card and "enough" storage (hint: there is never "enough").  As far as video card, you'll want a discrete card with an nVidia chipset (vs ATI or Intel or an onboard chipset).

The rest flows from there.  So,
What signal type(s) are you working with?
Are you looking to do this on a desktop (vs portable)?

---

