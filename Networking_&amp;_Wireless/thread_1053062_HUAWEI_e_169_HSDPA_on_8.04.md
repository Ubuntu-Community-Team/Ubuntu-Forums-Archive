---
title: "HUAWEI e 169 HSDPA on 8.04?"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Nidding on 2009-01-28
I just installed 8.04 on my acer aspire 4315 laptop and now I want to use a HUAWEI e 169 hsdpa 3G usb modem. I read some where thet it should work 'out of the box'. But frankly I don't know how it's supposed to work. Is there supposed to be a 'tab' in the networks over view or something?

---

### Post by Nidding on 2009-01-28
I tried this thread
[http://ubuntuforums.org/showthread.php?t=858032](http://ubuntuforums.org/showthread.php?t=858032)
but with no luck.
I don't have an internet connection on the computer (currently using a win xp machine withe the usb modem), so I can't install gnome-ppp.
Any ideas?

---

### Post by Nidding on 2009-02-01
Anyone???

---

### Post by theinnercityhippy on 2009-02-01
I would suggest upgrading to Ubuntu 8.10 which includes Network Manager 0.7 by default. I have an acer aspire one and use the same dongle to connect to the internet and it runs fine with Intrepid Ibex. Once you plug the dongle in, a dialog will open up asking what provider you have and autoconfigure the card for you. If you don't wish to upgrade at this point, and you are confident with the command line, wvdial will also work fine under hardy, although without knowing what network you are subscribed to, I can't help you further. Googling for the setup information would be a good starting point. If you wish to go down this route I can help you configure it if you message me but I am not always available so would be best to postto this thread first.

If you don't have a Live CD for 8.10, you can order one at

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If you don't have internet access at home, can you use it at a friends house or your local library/internet cafe?

Good Luck

JimDog*

---

### Post by Nidding on 2009-02-01
Then this could be the time for an upgrade. It sounds like it works without too much fuzz. 
I'm not confident with the command lines at all, but already after 3 days of windows useage, I'm getting sick of it. So I'm willing to do what it takes to get the dongle working with Ubuntu. 
Thanks for the help so far :D

---

### Post by Nidding on 2009-02-02
Ok. So now I got 8.10 installed, and the network app recognice the dongle alright, but my service provider isn't on the list. Is it possible to configure it manually?

ps. My service provider is 3-Denmark.

---

### Post by Nidding on 2009-02-02
Never mind.
I figured it out :)
Thanks for the help, theinnercityhippy.

---

### Post by theinnercityhippy on 2009-02-03
> **Nidding said:**
> Never mind.
I figured it out :)
Thanks for the help, theinnercityhippy.

You're welcome. glad you got it sorted :-)

(ps - don't forget to mark the thread as solved so it may be of use to others)

---

### Post by Nidding on 2009-02-03
Haha. now it gets a little embarrassing...
How do I do that?

---

### Post by royston on 2009-02-05
[QUOTE=Nidding;6663156]Never mind.
I figured it out :)
Thanks for the help, theinnercityhippy.[/QU

Having same problem would you please  in detail  how you  got  around this problem . thanks ..

---

### Post by royston on 2009-02-08
> **Nidding said:**
> Ok. So now I got 8.10 installed, and the network app recognice the dongle alright, but my service provider isn't on the list. Is it possible to configure it manually?

ps. My service provider is 3-Denmark.

I have this problem ..3 days and still no luck ..Please can any member help.. my service provider isn't on the list. Is it possible to configure it manually?

my  service provider  is iprimus.com.au

---

### Post by Nidding on 2009-02-09
I made it work by editing a setup from a provider on the list. You'l have to get some info regarding some of the settings. I needed to set my APN, user name and passwork (the two later just being guest).

I found these settings which you could try out
iPrimus Settings:
SP Code: 	310P1
APN: 	PRIMUSLNS1
Access Number: 	*99#

(Source: [http://support.iprimus.com.au/index.php?option=com_content&task=view&id=559&Itemid=203](http://support.iprimus.com.au/index.php?option=com_content&task=view&id=559&Itemid=203))

If that doesn't work, try contacting your provider for info.

---

### Post by royston on 2009-02-09
> **Nidding said:**
> I made it work by editing a setup from a provider on the list. You'l have to get some info regarding some of the settings. I needed to set my APN, user name and passwork (the two later just being guest).

I found these settings which you could try out
iPrimus Settings:
SP Code: 	310P1
APN: 	PRIMUSLNS1
Access Number: 	*99#

(Source: [http://support.iprimus.com.au/index.php?option=com_content&task=view&id=559&Itemid=203](http://support.iprimus.com.au/index.php?option=com_content&task=view&id=559&Itemid=203))

If that doesn't work, try contacting your provider for info.
  Thank you  will see how it goes ..

---

### Post by royston on 2009-02-12
> **royston said:**
> Thank you  will see how it goes ..
Thank  you  it  worked  okay ..
Now  I can get down to fully enjoying & learning the Linux experience .

---

### Post by Nidding on 2009-02-13
Glad that it helped :)

---

