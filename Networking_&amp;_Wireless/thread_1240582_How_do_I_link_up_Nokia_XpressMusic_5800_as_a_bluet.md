---
title: "How do I link up Nokia XpressMusic 5800 as a bluetooth 3G modem?"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Vignesh S on 2009-08-14
I would like to know how to link up a Nokia XpressMusic 5800 to an IBM Thinkpad R31 running Ubuntu 9.04 32 bit as a Bluetooth 3G modem. If it isn't possible by bluetooth, I guess I'll also accept it if it is attached to the laptop by a USB cable (though I am a bit reluctant to do that because it only has USB 1.1 ports)

---

### Post by Vignesh S on 2009-08-21
<bump> Surely someone out there knows...

---

### Post by theozzlives on 2009-08-21
> **Vignesh S said:**
> I would like to know how to link up a Nokia XpressMusic 5800 to an IBM Thinkpad R31 running Ubuntu 9.04 32 bit as a Bluetooth 3G modem. If it isn't possible by bluetooth, I guess I'll also accept it if it is attached to the laptop by a USB cable (though I am a bit reluctant to do that because it only has USB 1.1 ports)

The only way my Samsung works using CDMA is with a cable. Never heard of using bluetooth.

---

### Post by PatrickVogeli on 2009-08-22
you could try [blueman]("http://www.blueman-project.org/")

---

### Post by Post Monkeh on 2009-08-22
when i connected my nokia 5800 by usb, i get an option in my network manager connection menu for mobile broadband.

i selected my network provider and ubuntu did the rest.  all i have to do now is connect my phone, then after a few seconds i get an option in my connections menu for 02 contract (faster) click it, and away i go.


i don't have bluetooth on the laptop so i don't know if it will work with that, but that should get you going by usb anyway

---

### Post by LauriM on 2009-08-27
> **PatrickVogeli said:**
> you could try [blueman]("http://www.blueman-project.org/")
Thank you for the hint!

I set up the PPA, installed Blueman, connected it to my E51 and my existing connection in NetworkManager (that I had set up with the USB cable) started working right away. Now happily surfing with 3G!

---

### Post by Vignesh S on 2009-09-12
I managed to do it. But the problem is, I can't do it under 9.10. When I downgrade back to 8.10, I'll post how I did it. It is very easy though, albeit with a few things in mind i.e. turning wifi off before connecting via Blueman.

Is there any way for me to post my HOWTO in the documentation or something like that?

---

### Post by fosgon on 2009-10-07
Vignesh
Did you ever post a howto. I woudl love to do this with my machine so I can run without cabling up my mobile.
 
Fosgon

---

### Post by Vignesh S on 2009-10-08
Sorry, haven't been able to yet. Been really caught up here. But how do I post a howto in the Ubuntu documentation?

EDIT: This just sucks, Ubuntu 8.10 doesn't work on my lappy :-(. I'll have to reinstall 9.04...

---

### Post by Vignesh S on 2009-10-09
Well, I don't think I can add a howto to the Ubuntu documentation. Anywhere else I can put it?

---

### Post by eotakos on 2009-10-11
You can always post a howto at the "tutorials and tips" section of the forum... :-)

---

### Post by Vignesh S on 2009-10-11
Yeah, that's right. Thanks for that, eotakos. I will hopefully be able to post it sometime this week. Exams are just around the corner though :-( See how it goes.

By the way, is it possible to post it in the documentation too? I know it is possible to, but I'm not all that sure as to how.

---

### Post by Vignesh S on 2009-10-30
hmmm... Blueman in Ubuntu 9.10 RC doesn't like the Nokia XpressMusic 5800 :-(. I'll try the real deal...

By the way, I'm working on the howto. Just want to see if I can get this to work in Ubuntu 9.10. Its on the way though :-)

---

### Post by Vignesh S on 2009-11-11
Well, this isn't good...

Blueman on Ubuntu 9.10 doesn't like the Nokia XpressMusic 5800! It simply will not connect, even after all the steps I did to get it working in 9.04!

Oh well, back to square one, trying another solution...

---

### Post by ryu kun on 2010-11-19
Dial-up networking by using Nokia 5800 via bluetooth does not work in Ubuntu 10.10 even with Blueman. 

Here is a [bug]("https://bugs.launchpad.net/blueman/+bug/457134") reported about this in the times of 10.04. It's sad that it's still not solved.

---

