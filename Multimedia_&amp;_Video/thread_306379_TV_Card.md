---
title: "TV Card"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by bigfatgeek on 2006-11-24
The search in this forum finds 0 results when I search for "TV", in titles, body, or anyplace. I have never been able to get either of my TV cards to work on Ubuntu. Suse was the only distro it ever worked on, but I've been on Debian based too long to switch now. Besides, too many other things were broke in Suse. 

Question 1 - Why can't I search these forums for "TV"?
Question 2 - Am I pissing into the wind trying to get a TV Wonder Pro card to work?  

I use Ubuntu 6.10 - stock setup, except added KDE and Automatix goodies. Card is "ATI TV Wonder 200" The chip says - "Conexant Broadcast Decoder" CX23883-19

I will supply any other info needed if requested. I have used Linux for 10 years, prefer to read and learn, but I just can't get this to work even following several Google paths. 

Any help is very much appreciated.

---

### Post by SIZABANTU on 2006-11-24
Hi i found that using kaffine had my card working in no time,Try it :p

---

### Post by drphilngood on 2006-11-24
Try TVtime, it´s in the repos and should work with your card, and post back.

---

### Post by bigfatgeek on 2006-11-25
> **drphilngood said:**
> Try TVtime, it´s in the repos and should work with your card, and post back.

Thanks Doctor! That did the trick and I'm philnbetter already!
--bfg

---

### Post by greatgoo on 2006-12-28
I am trying to get the card to work.  It is the TV wonder 200 spoken of in this thread.  The system message shows the card as not recognised.

What I probably need is a pointer to a very very basic modprobe howto, or one on making hardware work.

I have loaded 6.10 Edgy Eft on the machine now, but could easily reload what ever would be the best to work from.  Learning Linux using Ubuntu and I have learned just enough to be dangerous.

David Davis
Toledo, OR 97391   ](*,)

---

### Post by greatgoo on 2006-12-28
Here is a clip from the system log ..

Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]: Your board isn't known (yet) to the driver.  You can
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]: try to pick one of the existing card configs via
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]: card=<n> insmod option.  Updating to the latest
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]: version might help as well.
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]:    card=2 -> GDI Black Gold
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]:    card=3 -> PixelView
Dec 28 09:25:58 greatgoo-desktop kernel: [17179593.052000] cx88[0]:    card=4 -> ATI TV Wonder Pro

I am not sure what the module or file is that the log refers to.  I understand the insmod idea fairly well ..

insmod <some module> argument

I tried insmod cx8800 card=4  but I get a file not found return.  Looking over on the v4l site, as well as the TVTime site I see discussion of the bttv module.  Is the cx88 driver in that module?

David Davis
Toledo, OR 97391

---

### Post by staib on 2006-12-28
Hi all,

I have been trying to get a WinTV Nova-T usb device to work in 6.10, but most of the howto's I've seen relate to WinTV CARDS.  Has anyone managed to get the TV tuner in a USB device to work? Any suggestions or pointers appreciated. I know the gadget itself works as its a simple plug and play thing in XP (once the software/driver is installed)...  

But, of course I really WANT it to work in Ubuntu!

Cheers,

Nick

PS - I just tried TVTime and it recognised an existing on-board (analogue tuner) and gave a clean picture (but no sound...) - but I would prefer to get the little digital tuner working...

---

### Post by scto on 2006-12-28
Please have a look here:
[http://linuxtv.org/repo/](http://linuxtv.org/repo/)

you need mercurial, should be in the universe repos.

Cheers
Tom

---

### Post by scto on 2006-12-28
or here: 
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB#Solution_with_v4l_manual_installation](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB#Solution_with_v4l_manual_installation)

Cheers
Tom

---

