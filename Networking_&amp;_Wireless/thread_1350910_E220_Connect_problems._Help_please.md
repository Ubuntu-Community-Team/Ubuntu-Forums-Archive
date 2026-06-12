---
title: "E220 Connect problems. Help please"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by Generalloss on 2009-12-09
Hello

Iv have had some problems connecting to the Internet whit my mobile usb Internet. 
I have been looking around to see if i can find any help and i see that there are tons of others having problems whit this but do not  fix mine. Maybe i just don't understand i am new to this OS.

Any ways the problem i have is that i cannot always conect to the internet. 

I live in Sweden and have 3g as my operator.

And this is how i connect to the Internet.

First i plug in the USB divise before i start the computer and when its all done the only thing i did the first time was to go up to where i can connect to the interent and the computer found it whitout eny problems. I hade to go thrue short guide and everything workt just fine. But my roommate and i share this Internet and he have hes own computer. Whit Win XP. So when i plug it back in to my computer all hell brakes loss.

Try to conect to the intrent can take me up to 30 minits and all i do is just plug the USB out and back in and conect disconnect, I restart the computer and try that way. Delete the connections and remake one. And it always say that im connected but i cant use the Internet in any way. And just randomly wile i am into all this it starts. I don't understand what it is that i am doing be cos its all random it connects whenever it wants. Its not that every time i restart the computer it connects or every time i remake the connection or just simply disconnect and connect. My devise can sometime have been connected for 10 min and all of sudden work. It always seam to be random.

Iv been searching the net for the problem but i don't really get what they are doing. Something about reseting your USB devise and/or make a password. 

So if you can help me that wold be really grate its really a pain when you just need to get on to get something for my studies or watch my mail or as much as see when the buss comes that i haft o try for minits to get it connected

Thanks in advance and as i sayd im new to Ubuntu so whatever extra help you can put in there wold be really appreciated. :)

PS i have Ubuntu 9.10 - The Karmic Koala - Whit USB Devise  Huawei E220

---

### Post by alexfish on 2009-12-09
Hi

 Is it   the " Modem  not connecting "    or  the "   Web browser "

---

### Post by Generalloss on 2009-12-09
It is the web browser, As well as everething, Cannot connect to enething that have whit the intrent to do as for en examepl Spotify. How ever the Modem say its conected. But as far as i can se its not

---

### Post by alexfish on 2009-12-09
> **Generalloss said:**
> It is the web browser, As well as everething, Cannot connect to enething that have whit the intrent to do as for en examepl Spotify. How ever the Modem say its conected. But as far as i can se its not

Hi 

With Firefox

If you have problems with  "The Web Browser Connecting to The Server"


 Try This

Leave the Browser On  

  " Disconnect  The Mobile Connection "      Then Re Connect  

     Click The "Try Again Button"  in the Browser 

Then if You Don't Want   The Browser On    Select     " Work Off Line"

    Then Hide The Browser

---

### Post by Generalloss on 2009-12-10
Thanks for the tips. However i don't see how that wold help me. I mean its more like a bug that the connection say that i am connected. Be cos i am not connected to the Internet in any way.

And its kind of all randomly connect ( Every time i tell him to connect that is ). Sumtimes it works but 90% of the times i try im still not connected.

---

### Post by alexfish on 2009-12-10
> **Generalloss said:**
> Thanks for the tips. However i don't see how that wold help me. I mean its more like a bug that the connection say that i am connected. Be cos i am not connected to the Internet in any way.

And its kind of all randomly connect ( Every time i tell him to connect that is ). Sumtimes it works but 90% of the times i try im still not connected.
Hi
Not sure if a bug / Possible the browser remembers last link on tty 0,1,2/  Will post
 Screen shots to explain

Next time I plug it  may show different combination

 If any device show on the desk top safely remove them

   this will solve the problem the next post will show you the codes you can try

---

### Post by alexfish on 2009-12-10
Hi


 **Multiple instances of the device:** The only problem I have which is independent of software used is that modem is detected when you plug it in but it ends up with multiple installations of the USB devices the first time it is plugged in after the machine is booted up. If you unplug and plug in again it is perfect - you can do it many times without problems. This seems to be to do with the fact that it changes mode - initially it looks like a CD so the drivers can be automatically installed under Windows then switches to a modem mode.  
 You can check what you have after the first time you plug in by
 From the Terminal

 Code:

 lsusb
 


 which should show the Modem as well as other USB devices  
 
Bus 004 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 004 Device 002: ID 0c0b:2bcf Dura Micro, Inc. (Acomdata) 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
and then you can check the actual devices which have been installed by

 Code:

 ls -al /dev/ttyU*  
 


 you should only have two or three devices /dev/ttyUSB0 /dev/ttyUSB1 and possibly /dev/ttyUSB2 as it also has a built in card reader for a micro SDC card. **If you have more it will not work**. Unplug and plug in again, wait 30 seconds and check again. At one time I had 12 devices listed! You may want to write an alias for ls -al /dev/ttyU* or put it in a launcher on the desktop as one tends to use it quite often
 
crw-rw---- 1 root dialout 188, 0 2008-12-21 19:00 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-12-21 19:00 /dev/ttyUSB1

 some times there may be 3 entries

This may vary so // safely remove any devices which shows on the your desktop

  until it shows only 2

  you can also see the same results from the Disk Utility from the System Menu

    open the disk utility   then plug the device in 

         then safely remove any device that shows on the desktop see what happens //// if it Looks Like The Screen Shot Then Its Good

   Handy tool That Disk Utility

---

### Post by Generalloss on 2009-12-11
Thank you Alexfish! 

That did the trick. I was afraid id haft o switch over to WIN XP to get it to work well im really glad i don't haft o do that sens i don't have the money nor the interest in that.

Once agen thank you allot for you time and help! Cheers! :D
[]("http://ubuntuforums.org/member.php?u=934779")

---

### Post by uncaspi on 2009-12-11
Please take a look on this thread.

[http://ubuntuforums.org/showthread.php?t=1315463&highlight=Huawei+E220](http://ubuntuforums.org/showthread.php?t=1315463&highlight=Huawei+E220)

---

