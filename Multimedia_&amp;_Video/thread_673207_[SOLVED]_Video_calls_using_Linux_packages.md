---
title: "[SOLVED] Video calls using Linux packages"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by IanB2 on 2008-01-20
I hope you can help .... my Mum-in-Law's Windows PC is seriously unwell and I'd like to wipe out windows and install Ubuntu .... however the main reason she uses the PC is for trans-Atlantic video calls using a webcam and MSN Live Messenger.
I really don't want to have to re-install Windows but I've been unable to find a Linux application that will support video calls. 

Do you know of any?

I have been using aMSN (a really nice package) but unfortunately this package does not support simultaneous voice and picture (yet). I been trying to find a Linux package that will allow me to connect my webcam to my family on MSN. So far I've drawn a blank on my google/forum searches.

I also have family members around the globe and we keep in contact using MSN Live Messenger with webcams. It is great to be able to see one another and talk at the same time .... really helps to keep us close.

Any thoughts would be appreciated ...... I'm sure I'm not the only Linux user wanting to use a webcam???!!??

---

### Post by smoka on 2008-01-20
I believe Skype 2 beta for Linux can handle video. 

[http://www.skype.com/download/skype/linux/beta/](http://www.skype.com/download/skype/linux/beta/)

Obviously everyone else would have to install Skype too.

---

### Post by tgalati4 on 2008-01-20
ekiga.net

---

### Post by imon9 on 2008-01-20
if she insist using webcam with MSN , then best bet is use kopete...

else use skype

open source choice is use some SIP server...but u gonna find some free server and register i supposed

other choice:
if she of u use v4l webcam, try use the [www.mebeam.com](www.mebeam.com)
no registration needed, very simple flash-based videochat, try it

---

### Post by YannickDefais on 2008-01-20
Hi,

[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

Regards,
Yannick

---

### Post by nikkkko on 2008-01-21
[Kopete]("http://kopete.kde.org/") will allow you to connect to other users using an MSN account. Kopete comes as standard with Kubuntu and works perfectly with my Labtec webcam.  For what it's worth, Kubuntu looks and behaves a bit more like Windows than Ubunutu, so it might be a better bet for your mum.  I have no axe to grind here; I use both Ubuntu and Kubuntu as well as Skype and Ekiga, but if you don't want to ask every one to change to a new service - i.e., stay with MSN - then you'd be better off with Kopete.

---

### Post by WinterWeaver on 2008-01-21
Another promising project is OpenWengo.

Seems to be a great alternative to Skype, and you can add you MSN, Yahoo, Jabber etc. accounts to it also.

OpenWengo also supports video chat. Worth a look I say.

I played with it very long ago, but I found 1 or 2 minor bugs which wasn't really big, but it was a bit annoying. That was long ago however, and it may have improved quite a bit.

Fool around with it, and see if you like it :)

WW

EDIT: Link >>  [http://www.openwengo.org/](http://www.openwengo.org/)

---

### Post by nikkkko on 2008-01-22
> Another promising project is OpenWengo.
Wengo is a french VOIP operator and OpenWengo was their open source softphone project, (WengoPhone), which they supported.  Unfortunately, they dropped support for OpenWengo and  WengoPhone around September last year.  Wengo users, such as me, are no longer seeing bugs fixed, such as no ringing on incoming call.  If all you want to do is connect to other MSN users, stick to Kopete.

---

### Post by IanB2 on 2008-02-10
> **nikkkko said:**
> [Kopete]("http://kopete.kde.org/") will allow you to connect to other users using an MSN account. Kopete comes as standard with Kubuntu and works perfectly with my Labtec webcam.  For what it's worth, Kubuntu looks and behaves a bit more like Windows than Ubunutu, so it might be a better bet for your mum.  I have no axe to grind here; I use both Ubuntu and Kubuntu as well as Skype and Ekiga, but if you don't want to ask every one to change to a new service - i.e., stay with MSN - then you'd be better off with Kopete.

I've got two boxes for testing purposes ..... one on windows XP and Ubuntu with web cam connected and recognised in both systems. I'm using kopete and MSN messenger.

I've been able to 'request' a webcam image from MSN and have that open in a separate window. This works fine :-)

 If I try to 'send' a webcam image from kopete, the window starts, the invitation is sent and accepted, my video window opens in kopete and then is immediately closed. The message on MSN on the other box is that I have 'stopped viewing the webcam' in ubuntu. Not sure why this is happening?

Also, is it possible to send and receive webcam images at the same time in Kopete? 

If I try to send a video request from MSN, I can accept the incoming call in Kopete and the next message in MSN is that 'Your video call has ended'.

I've not even attempted to get sound working yet .... but is this possible as well?

Cheers

---

### Post by Tamim-h on 2008-03-28
I have the same situation, and this is what I've found...
Ekiga detects my camera perfectly as well, but i havent tried calls to netmeeting.
Kopete does not detect my camera, Amsn does not detect my camera, Wengo does not detect my camera and mebeam doesnt work (because of lack of support for v4l2 in flash).
Skype is working for me, so that's what I'm sticking with. Previous versions of skype were crashing during video calls... i'm using 2.0.0.68 now.

-Tamim

---

### Post by IanB2 on 2008-03-30
Cheers!

I too have been experimenting with the latest version of Skype and have bought a Logitech Quickcam Messenger which works very nicely (including the built in microphone).

At last ..... a system that works reliably and means we can switch to using solely Ubuntu!

---

