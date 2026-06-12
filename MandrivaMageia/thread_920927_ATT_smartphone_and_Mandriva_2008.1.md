---
title: "ATT smartphone and Mandriva 2008.1"
date: 2008-09-15
forum: Mandriva/Mageia
---

### Post by Mr Pockets151 on 2008-09-15
Can someone help me get Mandriva to recognize my smartphone when I connect it to the PC.   

I have a  Samsung BlackJack II(SGH-i617).  Thx.  I've tried doing a google search and can't get anything.

---

### Post by AdamWill on 2008-09-16
It depends exactly what you're trying to do with it. For synchronizing it, see:

[http://wiki.mandriva.com/en/2008.1_Synchronization](http://wiki.mandriva.com/en/2008.1_Synchronization)

Or was it something else you wanted to do?

---

### Post by Mr Pockets151 on 2008-09-16
Yeah I just wanted to be able to add music and photos to my memory card.  (I don't have a memory card reader, maybe that would be the best way)  I will take a look at the article you linked.  Thx.

---

### Post by AdamWill on 2008-09-17
Ah, I see.

For 2008 Spring, the easiest way to do that is just to use wm5torage on the phone:

[http://freewareppc.com/communication/wm5torage.shtml](http://freewareppc.com/communication/wm5torage.shtml)

it's a little app. You can run it and then click a button and then, as long as that's running, it'll make the phone act like a USB mass storage device. So if you plug it into the PC with that app running it'll just look like any old USB drive and you'll be able to copy files to it with Konqueror or a console or whatever you like.

For 2009 I've added tools which will make it show up in Konqueror and GNOME without using wm5torage, but for 2008 Spring, wm5torage is the way to go.

---

