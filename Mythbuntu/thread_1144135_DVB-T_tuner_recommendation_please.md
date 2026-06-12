---
title: "DVB-T tuner recommendation please"
date: 2009-04-30
forum: Mythbuntu
---

### Post by Chris Musampa on 2009-04-30
Hi all,
I need a new tuner to receive UK freeview as my old nebula digitv pci card died last night.  I have a good external aerial and have never had any signal strength problems, I don't mind if its PCI or USB as long as its well supported (digitv card above failed under jaunty, same symptom as this: [https://bugs.launchpad.net/bugs/366606](https://bugs.launchpad.net/bugs/366606)), reliable and hastle-free. Dual would be a bonus, cheap would be excellent  :P

Please give me your good/bad experiences.

Cheers

Edit: the machine is a athlon xp2400 with 1GB ram though I'd like to upgrade a few months from now, it is connected to a HDTV via VGA cable (no HD broadcasts via freeview in my area so this is not a consideration).

---

### Post by RoboNuggie on 2009-04-30
I have a Hauppauge WinTV Nova TD 500 Dual tuner ( [http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/B000I1RHWA](http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/B000I1RHWA) ) and have had it for nearly a year now, but I use the black remote from XP media Centre......

Faultless, nothing else to say really....:)

---

### Post by tobiz on 2009-04-30
I agree, I also have a Nova T-500 and has worked without problem. Best point is it's a 1/2 height card and Hauppauge will provide a 1/2 height mounting bracket if you ask. Unfortunately I've not had same results with DVB-S cards.

---

### Post by Chris Musampa on 2009-04-30
Thanks for the replies, I was swaying towards these, I just wasn't sure as I'd read of problems (mainly with older kernels though so probably no longer relevant) regarding the USB interface with them.

RoboNuggie do you know what the 'D' means the one at my local shop is a 'WinTV-NOVA-T-500', is this likely to be any different?  Also you say you say you use a different remote, is the silver one supplied OK?

---

### Post by SiHa on 2009-05-01
The 'D' stands for 'Diversity', a variant to the standard model. The only one I can see on Amazon is a USB stick, but there are definitely PCI ones about. I have read of people really struggling to get this going with Linux - see [[COLOR="Blue"]here[/COLOR]](http://ubuntuforums.org/showthread.php?t=513147). However It seems from Robbo's post that these problems may be resolved.

Certainly the USB issues for the NovaT-500 have been fixed now. I've had mine running 24/7 for a year with no problems. It's very nearly a 'works out of the box' experience, just need to enable the onboard LNA - see [[COLOR="Blue"]here[/COLOR]](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500).

FWIW I'm using Mythbuntu 8.04.1 on the BE.

---

### Post by RoboNuggie on 2009-05-01
Having just realised, mine wasn't a Diversity model.... standard T-500 only.....  I think the PCI Diversity wasn't released in the UK, but then again I may be spouting steam!

The one on Amazon is the one I bought....

---

### Post by Chris Musampa on 2009-05-01
I'll get one this weekend,  many many thanks folks.

---

### Post by Chris Musampa on 2009-05-01
> **RoboNuggie said:**
> Having just realised, mine wasn't a Diversity model.... standard T-500 only.....  I think the PCI Diversity wasn't released in the UK, but then again I may be spouting steam!

The one on Amazon is the one I bought....

FYI the 'D' version **is** available in the UK, I just drove across town to buy a T-500 (having checked availability on the shop's website), I got there and ... you guessed it ... T**D**-500!

I'll probably have to mail order one now so will be Mythless for days, not happy.

---

### Post by Chris Musampa on 2009-05-03
Well I did a little more google trawling and decided to try the TD-500,  as expected it doesn't work with my hardy install but tuning/viewing does work out of the box with Jaunty (not tried the remote yet).

So far so good - :P

---

### Post by Chris Musampa on 2009-05-04
Sensitivity isnt as good as my old nebula (which happily shared the aerial with the freeview box using only a splitter), I had to buy an amp and its still not great on some channels if both tuners are in use.

As far as the remote goes, there was no sign of the IR receiver until I compiled the latest v4l drivers, a reboot later the remote was up and running, sweet.

---

### Post by SiHa on 2009-05-05
you did enable the LNA?

Here's a couple posts referring to getting this card running under 9.04, and specifically mentioning **/etc/modprobe.d/options**
[http://ubuntuforums.org/showthread.php?t=1132709&highlight=modprobe.d](http://ubuntuforums.org/showthread.php?t=1132709&highlight=modprobe.d)
[http://ubuntuforums.org/showthread.php?t=1140411](http://ubuntuforums.org/showthread.php?t=1140411)

---

### Post by Chris Musampa on 2009-05-05
> **SiHa said:**
> you did enable the LNA?

Here's a couple posts referring to getting this card running under 9.04, and specifically mentioning **/etc/modprobe.d/options**
[http://ubuntuforums.org/showthread.php?t=1132709&highlight=modprobe.d](http://ubuntuforums.org/showthread.php?t=1132709&highlight=modprobe.d)
[http://ubuntuforums.org/showthread.php?t=1140411](http://ubuntuforums.org/showthread.php?t=1140411)

No I haven't, I have seen that mentioned but wasn't sure if it applied to the TD version, will have a try after work and se if it makes any difference.

---

### Post by SiHa on 2009-05-05
If you've only got one aerial input (as opposed to two, which the **original** TD had) then you will definitely need the LNA. On my system it made the difference between getting no channels at all on a scan to about 60 with the LNA activated!

---

### Post by Chris Musampa on 2009-05-05
> **SiHa said:**
> If you've only got one aerial input (as opposed to two, which the **original** TD had) then you will definitely need the LNA. On my system it made the difference between getting no channels at all on a scan to about 60 with the LNA activated!

Hi SiHA, thanks for the tip, this is the Diversity version though and, as I guessed (I think the bridged input capability is offered instead of the LNA), the LNA option made no difference.  I think the Nebula card was probably more sensitive, which is fair enough as they cost a fair amount more than others.

---

### Post by SiHa on 2009-05-06
Oh well, live and learn!

---

### Post by canoemoose on 2009-05-06
Sorry to hijack the thread, but I'd like to clarify a few points.

0) Do you have the T-500 with 1 aerial connector, the TD-500 with 2 aerial connectors or something else?
1) Does this card work on AMD-based computers?  I infer it does.
2) If you have the TD-500, does this just behave like a T-500 (ie is it only the Diversity bit that doesn't work.  The LinuxTV wiki is unclear on this point and emails to Hauppauge UK tech support are answered with the equivalent of "Linux! Pfft!")

Cheers
Canoemoose

---

### Post by Chris Musampa on 2009-05-06
> **canoemoose said:**
> Sorry to hijack the thread, but I'd like to clarify a few points.

0) Do you have the T-500 with 1 aerial connector, the TD-500 with 2 aerial connectors or something else?
1) Does this card work on AMD-based computers?  I infer it does.
2) If you have the TD-500, does this just behave like a T-500 (ie is it only the Diversity bit that doesn't work.  The LinuxTV wiki is unclear on this point and emails to Hauppauge UK tech support are answered with the equivalent of "Linux! Pfft!")

Cheers
Canoemoose

Hi Canoemoose,
1.  The machine I have this card in is an AMD Athlon XP2400 in a Gigabyte motherboard with 1GB ram, all around 5 years old, works just fine.

2.  Yes this card is a TD-500 with 2 aerial connectors (please don't ask for the number on the sticker as I've just got round to putting the covers back on and stashing the machine behind the sofa).  Yes it operates as two seperate tuners as opposed to Diversity (bridged) mode.  Once new drivers were installed (surprisingly easy for my first attempt) the remote showed up and was easily configured in MCC as a T-500 remote.

The sensitivity problem mentioned in my previous post turned out not to be an issue once I'd shortened and tidied the cables, it now gets good signal strength on any channel with both tuners active.  Chris is happy.

---

### Post by canoemoose on 2009-05-06
> 1. The machine I have this card in is an AMD Athlon XP2400 in a Gigabyte motherboard with 1GB ram, all around 5 years old, works just fine.

2. Yes this card is a TD-500 with 2 aerial connectors (please don't ask for the number on the sticker as I've just got round to putting the covers back on and stashing the machine behind the sofa). Yes it operates as two seperate tuners as opposed to Diversity (bridged) mode. Once new drivers were installed (surprisingly easy for my first attempt) the remote showed up and was easily configured in MCC as a T-500 remote.

The sensitivity problem mentioned in my previous post turned out not to be an issue once I'd shortened and tidied the cables, it now gets good signal strength on any channel with both tuners active.

Cheers for the info and the prompt reply!

> Chris is happy.
That's what we like to hear! :p

Cheers
Canoemoose

---

### Post by RoboNuggie on 2009-05-07
Glad you are sorted Chris!

:guitar::popcorn:

---

