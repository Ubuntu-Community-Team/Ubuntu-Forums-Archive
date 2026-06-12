---
title: "This is so ******* stupid!!!"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by TIMU-Is-My-Username on 2009-01-26
Okay, why can't there be a simple answer to any ******* thing regarding Ubuntu?  TRY to get Wine, but I'm told I need internet because otherwise it would be too hard to compile.  Don't have it, so I try following all the guides on how to get Wine anyway.  Leading me in ******* circles, I don't know where to start... even when to know when I'm finished!  What's the end result supposed to look like?  How will I know I'm there??  When I get the program right?  There's no ******* installer to say, "Oh, your ******* installation is done."  No, damnit!

God...

And then I decide, fine I'll try to get the wireless up, so I can use Synaptics Manager, because of all these stupid dependency files.  Great.  So I think it's going to be an easy process.  After all, an HP Pavilion dv6700... fairly common laptop.  There should at least be some easy guides out there for that!  ********!  I'm supposed to extract my driver's .exe file for WHAT??  A .sys and .inf file?  Where did those come from?  How the hell do I get that?  Terminal who??  Okay, so I downloaded my driver's .exe file.  But because I can't get Wine up, I can't install the driver's .exe file.  Oh, but I need to install the driver in order to install Wine.  Gaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaah!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

And how come I try reading everybody else's threads and everybody else gets everything fixed and up and working, everybody else is like, "Oh, is THAT all?" and I'm left in the dark wondering, "Why isn't that working for my computer?  I did the same thing!"  Why does this need to be such a pain in the ***?!  Should I have stayed with Vista??  Isn't Linux supposed to be BETTER than Windows??  Damn!!!!!!!!

---

### Post by Sub101 on 2009-01-26
What exactly is your question?

---

### Post by 5BallJuggler on 2009-01-26
firstly, do you have a wireless router?

if so and you can't connect, then why don't you use a Lan cable, ubuntu will detect that it is connected, 

then you will be able to use the synaptic to load all of your drivers for wireless.

....and also you will be able to load wine from there too.

---

### Post by TIMU-Is-My-Username on 2009-01-26
> **5BallJuggler said:**
> firstly, do you have a wireless router?

if so and you can't connect, then why don't you use a Lan cable, ubuntu will detect that it is connected, 

then you will be able to use the synaptic to load all of your drivers for wireless.

....and also you will be able to load wine from there too.

I use wiFi.  As in, I don't pay for internet, but when there is free internet around, I can use it on my laptop.  USED TO BE ABLE TO on my laptop, when I had Vista.  Wiped that out for Intrepid.  I don't have internet that I can just plug in.

---

### Post by TIMU-Is-My-Username on 2009-01-26
> **Sub101 said:**
> What exactly is your question?

I guess that's my question too.

---

### Post by bgerlich on 2009-01-26
Try an Internet Cafe, most will allow you to plug in.

---

### Post by damis648 on 2009-01-26
Just calm down and we can try to help you. You need to understand that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"). Do not expect everything to be exactly like Windows, that is not the point.

Please continue the support discussion in[ this thread]("http://ubuntuforums.org/showthread.php?t=1050936").

---

### Post by Sub101 on 2009-01-26
So you want to get wireless connected?

Go to your terminal and type:

```
iwconfig
```

What is the output?

---

### Post by Kevbert on 2009-01-26
To get wireless going you'll probably need firmware drivers. Go to Applications-Accessories-Terminal and enter
```
lspci
```
This lists all pci devices (assuming that your wireless adapter is not usb). If it is a usb device then you should use
```
lsusb
```
instead to list all usb devices.
Please post the output from the command by setting the text and pressing Ctrl-Shift-C to copy and Ctrl-V to paste into a text file.  These commands should give us a clue as to what wireless chipset you have and what drivers you need.

---

### Post by damis648 on 2009-01-26
> **Kevbert said:**
> To get wireless going you'll probably need firmware drivers. Go to Applications-Accessories-Terminal and enter
```
lspci
```
This lists all pci devices (assuming that your wireless adapter is not usb). If it is a usb device then you should use
```
lsusb
```
instead to list all usb devices.
Please post the output from the command by setting the text and pressing Ctrl-Shift-C to copy and Ctrl-V to paste into a text file.  These commands should give us a clue as to what wireless chipset you have and what drivers you need.

Continue this [here]("http://ubuntuforums.org/showthread.php?t=1050936").

---

### Post by kevdog on 2009-01-26
Hmmm, I don't really reward bad behavior and temper tantrums like this.  If you would like to repost your question in an adult like manner I might be more inclined to help you!

---

### Post by Rocket2DMn on 2009-01-26
Closing this thread, please continue your discussions in the other thread in a calm and professional manner.
[http://ubuntuforums.org/showthread.php?t=1050936](http://ubuntuforums.org/showthread.php?t=1050936)
Thank you.

---

