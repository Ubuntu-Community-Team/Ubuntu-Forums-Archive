---
title: "Webcam Not Working"
date: 2010-02-25
forum: Multimedia Software
---

### Post by greg387 on 2010-02-25
Hey Guys,
My webcam isnt working o n my laptop. I just instlaled latest version of ubuntu. When I type lsusb i get:

Bus 003 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any ideas

---

### Post by greg387 on 2010-02-25
anyone?

---

### Post by Saito Chikara on 2010-02-25
I can't even get my computer to even recognise my webcam.. otherwise I might offer a hand.. :sweat:

---

### Post by Dougie187 on 2010-02-25
Is it a built in webcam? Do you know what type it is?

---

### Post by dadgetboy on 2010-02-25
I had this problem for a while, and I easily solved it today. There is a program called Cheese
```
sudo apt-get install cheese
```

and if that does not work
there is luvcview
```

sudo apt-get install luvcview
```

Lemme know how it works out :p

---

### Post by no2498 on 2010-02-25
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each

now you need a program to see it on
get ( cheese and wxcam )
you should have cheese
wxcam you can get from [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)
or [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by greg387 on 2010-02-25
Nothing worked!

---

### Post by Dougie187 on 2010-02-26
Again

> **Dougie187 said:**
> Is it a built in webcam? Do you know what type it is?

Just so you know, it may or may not be compatible with ubuntu.

It obviously sees it because of this
```
Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
```

It's just a matter of making sure you can "use" it.

---

### Post by greg387 on 2010-02-26
It is a built in webcam
I understand. That is my question. How can I get my laptop to use it.

---

### Post by gordintoronto on 2010-02-26
Have you tried Cheese?  What is the result?

UVC webcams should "just work" under Karmic.

---

### Post by Dougie187 on 2010-02-26
> **greg387 said:**
> It is a built in webcam
I understand. That is my question. How can I get my laptop to use it.

Ok, so then the next question is what have you tried? and what happens when you try each of these. Be as detailed as possible.

---

### Post by David2009 on 2010-03-01
Dear Greg,

Sorry you are having webcam troubles.  I had the same problems with my Chicony webcam in a Toshiba A305 using both Ubuntu and OpenSuse.

If you find a solution, please post it.  Someone is bound to find the solution.

David

> **greg387 said:**
> Hey Guys,
My webcam isnt working o n my laptop. I just instlaled latest version of ubuntu. When I type lsusb i get:

Bus 001 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Any ideas

---

### Post by pickarooney on 2010-03-01
I have a Chicony as well (labelled as Labtec) and it has only worked twice (in Cheese) and never again. Also, never in skype. This is the third webcam I've failed to have Ubuntu exploit consistently.

---

### Post by no2498 on 2010-03-02
pickarooney go back to my post do as i said
get a diff program to use the cam with
an do not open cheese its not working well with other programs at this time
skype you need to make a preload file for not just preload 

try your cam in ekiga softphone its loaded under internet

---

