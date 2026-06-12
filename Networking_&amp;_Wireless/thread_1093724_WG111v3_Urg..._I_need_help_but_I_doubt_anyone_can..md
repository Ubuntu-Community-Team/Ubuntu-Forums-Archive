---
title: "WG111v3: Urg... I need help but I doubt anyone can."
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by jobuntee on 2009-03-11
Right, very new to linux... I know what it is and a few things but I'm not a fan of doing my own commands and less a fan of writing my own drivers... 

Anyway, put xubuntu on my old laptop to start learning.

The only way it is getting on the internet is if I make it work with my USB wireless stick... a Netgear WG111v3... which doesn't work when you just stick-it-in...

I have tried various suggested solutions including messing around with something called ndiswrapper and even a suggestion on here where I actually open up and modify a driver file... that failed too but I suspect it may have been something to do with me making a mistake maybe...

I have version 8.10 of xubuntu...

Can anyone offer me a solution where I don't have to do so much messing around with things that newbies like myself simply shouldn't touch OR if I do have to touch stuff, can people offer me help that tells me what to do in idiot-proof language (e.g. when it's a case of downloading a tar.gz or whatever, I need to be *told* how to make it work when I have it)...

I do feel like an idiot proof solution would be useful for users like myself and it isn't as if the WG111v3 is a terribly old piece of kit...

Anyone got enough pity and a little time to help me?

If not no worries, I understand it probably isn't a simple request... I'd really like to start using linux a bit though...

Jobuntee

---

### Post by lindsay7 on 2009-03-11
You may not want to hear what I did but it may be useful to you anyway.

I gave up trying to get My wg111v2 to work and bought one that would plug and play,  Linksys WUSB54G. I have also read that the Belken f5d7050 is plug and play.  

There was no good documentation that I could find that the netgear wg111v2 was ever going to work for me. I do not know abut the v3.  There is a real good write up on wireless cards and adaptors on the networking and wireless forum section of the forum.  There are different chip sets used in some of these adaptors like the wg111 and some work and others do not.. If you type sudo lsusb in the terminal it will show what devices are connected to the usb ports and give you some idea of what is going on.

---

### Post by Skripka on 2009-03-11
You'll need to Ndiswrapper the driver...This site provides a good overview

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

I hope this linky still works....

[http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI](http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI)

And for 64bit

[http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111)


All the above were my go-to guides when I used a WG311v3, they worked just fine for me.  The WG311v3 can work fine-you just need some patience and read carefully.

---

### Post by jobuntee on 2009-03-11
OK, I'll attempt that stuff again...

Interestingly, I first tried 8.04 and now I am on 8.10 (intrepid ibix I think?) the usb stick actually shows a light when you stick it in...

And ALSO, if I type sudo lsusb it correctly identifies the stick... so, I shall try the stuff recommended AGAIN now I have 8.10...

Anyone with a better idea now it's identifying correctly please chip in with their 10 cents ;)

Thanks for comments so far too.

---

### Post by jobuntee on 2009-03-11
OK, it's looking good!

Thing is I am having trouble with this bit (driver installed, managing to search for available wireless connections):

Step 7: Configure your Wlan card.

Code:

sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl](www.ubuntu-linux.nl) (tests the connection)

The name of my router is ADDON GWAR3000

I can't type the space because it says 'GWAR unrecognised command' etc...

What do I type? Just ADDON?

Because, whatever I type, when I get to doing:

iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 

I get this error message:

SET failed on device wlan0 ; Operation not permitted.



Any thoughts?

---

### Post by sailthesea on 2009-03-11
Have you rebooted into 8.10 with the usb plugged in? Sounds obvious I know
 I found that mine started up enough to download a better driver (rtl8177 I think) I've been trying get my netgear working properly for ages!
Will get back

Edit: Just realised your on Xubuntu
 May still be a worth a look at this sledgehammer of a fix It at least got me some sort of connection!

[http://ubuntuforums.org/showpost.php...8&postcount=68](http://ubuntuforums.org/showpost.php...8&postcount=68)

If I ever figure it out I will tell the world!!

---

### Post by jobuntee on 2009-03-11
Nope, same problem...

Am I typing the name of my router wrong for the command

sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 

???

My router comes up as

ESSID:"ADDON GWAR3000"

I can't type ADDON GWAR3000 with a space for reasons I said before but I have also tried just ADDON and also "ADDON GWAR3000"

Interestingly, when I use "ADDON GWAR3000" the error I get changes with an extra line when I type the 

iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 

it then says:

Error for wireless request "Set Encode" (8B2A) :
           SET failed on device wlan0 ; Operation not permitted.


EDIT: sailthesea, your link doesn't appear to work... anyway, this fix appears to be the correct one, I just have a little problem at the last hurdle!


EDITEDIT: Just realised I am using a WPA PSK string... I shall investigate more... (or just change my router settings hehe)

---

### Post by sailthesea on 2009-03-11
OK back to the begining 
Can you get on  a wired connection with your Ubuntu machine?
What distro of ubuntu are you using now?
What is the spec of your machine?
 You seem to having the same problems as I did and whilst I haven't fixed it yet I've managed to get things a bit better I'll be glad to help if I can:)

Edit : If you get things going with ndswrapper thats great

I put the wrong link in before should be:

[http://ubuntuforums.org/showpost.php...8&postcount=68](http://ubuntuforums.org/showpost.php...8&postcount=68)

If it works never mind any of the above

If not try it Its a bit brutal but effective!

---

### Post by jobuntee on 2009-03-11
Do you suspect my problem is because of something else aside of the WEP/WPA thing?

I am presently attempting to set my router to WEP but it wont do it... which reminds me why I picked WPA in the first place heh.

Funny you should ask about a wire connection... I hadn't bothered trying, but yes... I tried and I can connect to the internet via wire...

Spec of computer = old... 256mb ram, 1.7 or 2.7 pentium II or something... but still, no problems running most simple stuff...

Wish I could make my router do WEP... plus, looking at the alternative course of action ( [http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa](http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa) ) I don't fancy my chances...

---

### Post by jobuntee on 2009-03-11
I have managed (after trouble) to set my router to WEP 128 bit...

Still same error messages...

Am I typing my router's ESSID properly in the command?

EDIT:

And how would you type the WEP string? I typed both with spaces XX XX XX XX XX and without XXXXXXXXXX (for 64-bit strings)

Sorry to ask the basics but this might be where I am going wrong (it often is!)

---

### Post by sailthesea on 2009-03-12
Your machine should be able to handle it Its something else to do with the WPA encryption and other networks I think 
 Couldn't find that link by the way Will track it down
 Got to go Zz Sorry and good luck 
Will get back

Edit: Just try searching the forum with "netgear w111v3" there are many threads relating and its a good idea to do a bit of reading, sometimes you find what you need without ever having to ask That's learning!

---

### Post by mark bower on 2009-03-12
i am new also to 8.10.  to end the wireless connection pain i purchased the Belkin USB F5D7050 based on recommendation of others.  Immediate out of the box connection on both of my PCs and laptop.  i am not aware of any non-working situations.  i have read where use of native drivers is preferred, ie, no use of ndiswrapper.

---

### Post by jobuntee on 2009-03-12
I'm trying to avoid buying anything new... I'm skint and this linux venture is not a priority... just a testing thing... maybe if I got my present one working I could get myself into linux and then in future it would become a priority hmmm.

I'll keep looking for a solution... seems like there should be when the thing obviously works and my comp recognises it... just annoying error at the last step...

---

### Post by jobuntee on 2009-03-12
Weird...

Started it up again this morning and noticed a little message about wireless networks being available in the top right... showed me all the networks... i clicked mine, it asked for WPA pass key etc... and away I go...

So, for 8.10 (intrepid ibix, I think?) xubuntu you CAN make a WG111v3 work by following the steps suggested in

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

except that things might stop working when you get to step 7... just that if you restart your laptop again in the morning you will magically get a little graphical wireless wizard in the top right of your desktop (?!!!!)

Brilliant... thanks everyone... hopefully this will be the start of my wonderful relationship with linux... just need to find an autocad substitute... ehem (!).

---

### Post by sailthesea on 2009-03-12
Glad to see you solved the problem You'll find you have to do quite of that Buy it,s all good fun!
 If your looking for CAD packages there are a couple in the repos , not quite up to say AutoCAD 2007 But as a one time AutoCAD user they look adequate
If you interested try looking at 

[http://www.ribbonsoft.com/qcad.html](http://www.ribbonsoft.com/qcad.html) (I checked this one works)

  To install it:  Applications>Add/remove
               Find QCad in graphics and check the box
               Follow the install instructions and check it out (although running it may tax your hardware )

 Don't be afraid to ask for help even if it sounds stupid coz everyone new to linux has the same problem Its different from what your used to, there is so much you can actually DO! 
 Happy Voyage:)

---

### Post by abn91c on 2009-03-12
> **mark bower said:**
> i am new also to 8.10.  to end the wireless connection pain i purchased the Belkin USB F5D7050 based on recommendation of others.  Immediate out of the box connection on both of my PCs and laptop.  i am not aware of any non-working situations.  i have read where use of native drivers is preferred, ie, no use of ndiswrapper.

+1 for the Belkin it works for me I'm using it on a Dell GX 240 I got at a fleamarket for $100. Last week it was on sale at the walmart website for $35

---

### Post by lindsay7 on 2009-03-12
.

---

### Post by onfyreforjesus on 2009-04-22
Yep! thats the Key. When you use this Netgear WG111v3, use ndiswrapper and use the WPA2 personal key and everything works. Even after all the effort it still wont connect sometimes but a reboot does the trick. I'm hoping that there is a native driver in the jaunty that will rid the need of ndiswrapper. 
In fact there was a rtl8187b driver but wasnt optimised for the v3 so i would have to take my desktop to the place where i hooked my router to work. The windows drivers with the ndiswrapper just work fine. Hoping that this gets sorted out with jaunty.. waiting for tomorrow!

---

