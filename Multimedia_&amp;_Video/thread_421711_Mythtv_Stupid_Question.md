---
title: "Mythtv Stupid Question?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by JAKEOTR on 2007-04-24
Hello, I'm having trouble getting my head around some concepts with Mythtv, mainly layout. I want to have a separate frontend and backend, the backend being a few rooms away from the front. A PVR-250 is in the backend, an nVidia card with TV out is in the front( standard PC next to my DishNetwork receiver). Can I change channels with an IR Blaster and run the remote from the front end or do I have to string wires to the backend? I assume I can run the the remote from the front, but do channel changes have to happen on the backend? Also what kind of IR Blaster setup do I need to run out of a PC (assuming I dont have to use the PVR-250 port)

Thanks for the help

---

### Post by reclusivemonkey on 2007-04-24
> **JAKEOTR said:**
> Hello, I'm having trouble getting my head around some concepts with Mythtv, mainly layout. I want to have a separate frontend and backend, the backend being a few rooms away from the front. A PVR-250 is in the backend, an nVidia card with TV out is in the front( standard PC next to my DishNetwork receiver). Can I change channels with an IR Blaster and run the remote from the front end or do I have to string wires to the backend? I assume I can run the the remote from the front, but do channel changes have to happen on the backend? Also what kind of IR Blaster setup do I need to run out of a PC (assuming I dont have to use the PVR-250 port)

Thanks for the help

You can control everything from the frontend. Channel changes you make on the frontend will only occur if nothing is record. TBH, you are much better off not bothering with Live TV at all. If you schedule a recording, you can start to watch it as soon as it records. You can also watch any recordings whilst MythTV is recording, but if you are watching LiveTV, you can't record. Sorry, I have no idea about IR Blaster. Try the MythTV Wiki or the Forums, I am sure someone will help you.

---

### Post by josesanders on 2007-04-24
What TV signal do you intend to have connected to the backend?

Correct me if I'm wrong, but in order to receive a TV signal when you have a dish, you need a special receiver, right?  Therefore you need to connect your backend to a receiver just to get the TV signals.  Then, you run the IR blaster from your backend to the receiver to change channels.  Essentially, all video inputs need to be connected to a backend, or there is no way to capture the signal.

Can you elaborate on your setup a bit more?  I'm a bit confused about what you are trying to do.

---

### Post by JAKEOTR on 2007-04-24
I know I need the connection from the Dish receiver to the backend, what I'm confused about is whether I need to run a long cable from the backend out of my PVR-250 to my HT area so that I can change channels with the hauppage remote...or can I change channels from my frontend (frontend telling the backend to change the channel)? If frontend changing is possible, how would I connect the IR receiver to the pc? I have the IR receiver that came with the PVR-250...would it be possible to use that?

Thanks

---

### Post by josesanders on 2007-04-24
I understand now.

Yes, you can change channels from the remote frontend as long as the frontend can receive the remote signals - your frontend tells the backend to output the signal on the IR blaster to change the channel on the receiver the backend is connected to - but in order to do that you need the TV card to receive the signal from the remote.  It may be possible to interface your remote with your frontend without the card, but it won't be easy.  The lirc website:
[http://www.lirc.org/](http://www.lirc.org/)
has some information about building a custom infrared receiver to connect to your serial port.

---

### Post by JAKEOTR on 2007-04-25
OK....not sure how others have their frontend/backend setups laid out....but, say I dont watch live TV with myth but only recorded TV then, I should be able to control everything from the frontend (set shows to record,etc)...with a remote (not sure how to work that yet..I assume it would have to be thru the serial port) and would only need an IR blaster cable from the backend to the Dish receiver to change channels based on recording schedules set by the front end. Does this sound right?

What kind of setups do you people use for remote control? can they be made or bought cheaply?

Thanks

---

### Post by josesanders on 2007-04-25
That sounds right to me.

For the frontend remote, I have an old saa7134 tuner card.  I could never get it to work with mythtv, but it did come with a remote, so now I use it in a frontend-only machine only for the remote.  The saa7134 tuner cards treat the remote simply as normal strokes from the keyboard, so you don't even need LIRC at all.  Admittably, there may be better solutions, but you should be able to find one of those cards on ebay for around $10 plus shipping.

---

### Post by JAKEOTR on 2007-04-25
Sounds good,

Thanks for all the help!

---

### Post by majoridiot on 2007-04-25
feisty lirc info here: [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

more changer info here: [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

a good buy on a remote for the frontend here: [http://cgi.ebay.com/MICROSOFT-MEDIA-CENTER-REMOTE-CONTROL-4-VISTA-or-MCE_W0QQitemZ130102812812QQihZ003QQcategoryZ51086QQtcZphotoQQcmdZViewItem](http://cgi.ebay.com/MICROSOFT-MEDIA-CENTER-REMOTE-CONTROL-4-VISTA-or-MCE_W0QQitemZ130102812812QQihZ003QQcategoryZ51086QQtcZphotoQQcmdZViewItem)

interesting and cheap IR devices here: [http://www.irblaster.info/](http://www.irblaster.info/)

other mythtv info starts here: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

happy shopping! :D

---

### Post by newlinux on 2007-04-25
[http://tekgems.com/Products/tg-pbr.htm](http://tekgems.com/Products/tg-pbr.htm)

An inexpensive remote and IR blaster...

---

### Post by JAKEOTR on 2007-04-30
OK...more stupid questions....looking in the Feisty Mythtv guide, if I have a pvr-150 card with the IR blaster then I can use that to change channels on my Dish box. Do I need lirc to accomplish this? 

Also, according to the guide, my remote uses the i2c driver thats built in to the kernel. If I am using this on the frontend without the PVR-150 (which is in the backend), then am I still going to need lirc on the frontend in order to hook it up the ir-receiver to a serial port? Is there a better way? 

It seems there is alot more issues with having things split (frontend/backend) rather than having it all together in one box using the same equip.....so any help will be appreciated, thanks

---

### Post by newlinux on 2007-04-30
> **JAKEOTR said:**
> OK...more stupid questions....looking in the Feisty Mythtv guide, if I have a pvr-150 card with the IR blaster then I can use that to change channels on my Dish box. Do I need lirc to accomplish this? 
Yes, if you want to use the IR blaster with the card...  More info/options:
[http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV)
> 
Also, according to the guide, my remote uses the i2c driver thats built in to the kernel. If I am using this on the frontend without the PVR-150 (which is in the backend), then am I still going to need lirc on the frontend in order to hook it up the ir-receiver to a serial port? Is there a better way? 


Yes you will want LIRC on both. You can use a USB IR receiver as well. Some use wireless keyboards, which wouldn't require LIRC. Some have had learning remotes learn the commands from an IR keyboard.
> 
It seems there is alot more issues with having things split (frontend/backend) rather than having it all together in one box using the same equip.....so any help will be appreciated, thanks

Let me us know if you have more questions.

---

