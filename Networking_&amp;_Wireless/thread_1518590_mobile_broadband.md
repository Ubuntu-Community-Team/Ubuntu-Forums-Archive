---
title: "mobile broadband"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by hyballs on 2010-06-26
Hi folks, I am using 9.10 and have a Virgin (Australia)mobile broadband that has worked a few times but generally doesn't work!  I've put it in before booting and after booting but it seems to have a mind of it's own whether it works or doesn't.  Is there a an update on the software for a fix or is it something I have done wrong in the set-up?  Thanks

---

### Post by utkarsh009 on 2010-06-26
is your modem a 3g dongle?

---

### Post by pdc on 2010-06-27
this is likely a Huawei modem; 

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

if you search for Virgin on this webpage you can see they advise to disable chap: have you done that?

Virgin Oz does seem temperamental:

[http://ubuntuforums.org/archive/index.php/t-1467991.html](http://ubuntuforums.org/archive/index.php/t-1467991.html)

but posts #14 and #15 describe success here

[http://ubuntuforums.org/showthread.php?t=1354619&page=2](http://ubuntuforums.org/showthread.php?t=1354619&page=2)

see if your settings are the same ..

if all that fails ..........

If you can download an .iso for 10.04; and use the usbcreator facility on your existing 9.04, you can then get a liveCD running on a usb stick (or an SD card if your computer has that): I do that with our Eee ...

---

### Post by Rhubarb on 2010-06-27
I've found Ubuntu 9.04 and 9.10 to be a little buggy when using 3G dongles.
Ubuntu 10.04 is fine, I've had no problems with connecting to Three Australia. - Which could be the problem.

If you want lots of reliability, and don't want to upgrade to 10.04, I suggest you play around with wvdial - send me a pm and I'll dig up how I did it and will post here the solution.

---

### Post by pdc on 2010-06-28
if you are still out there hyballs ..

if you look at this post 

[http://ubuntuforums.org/showthread.php?t=1470505](http://ubuntuforums.org/showthread.php?t=1470505)

and go to post #8;

a fellow Australian reports success;

[I]if you copy and paste the commands below 
[/I]
what he did was 

> sudo gedit /etc/udev/rules.d/temp-e169-modem.rules

you enter your sudo password, and the text editor gedit opens an empty page ..

... into that paste the following

> ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

........ save .......... close .......... reboot ......... plug your modem in 

(I am assuming you are using the Huawei E169 that Virgin sells ...)

any joy?

---

### Post by chris5 on 2010-06-28
Interestingly my Huawei 3g dongle was pretty much plug and play on 9.10 - I just had to enter the APN, username, etc and off it went. When I upgraded to 10.4 I had to install the zerocd, usbmodeswitch and vodafone mobile connect packages to get it working.
 
A case of newer not necessarily being better?
 
Peace

---

### Post by hyballs on 2010-07-01
Thanks for everyones help.  Will upgrade to latest version and go from there.

---

### Post by dvn3ch on 2010-07-01
I have a very similar problem on a MX6214 Gateway laptop but with a Huawei EC360 (PCMCIA card).  I installed a fresh copy of 10.04 Ubuntu, plugged in the card and the OS found it and connected with minimal input on my part.  It connected to the Internet with speed and no dropping....then....

After two or three start-ups, the connection went away.  At one point, my network icon disappeared.  Tried every trick that I knew or could find on the net and still could not get the connection back or my network icon (active network discovery).  I reinstalled Lucid and tried again but basically the same thing happened except I have yet to lose my network icon.  

Some interesting points: 1) I had to download a Broadcom (proprietary) driver to recognize/use my wireless card (internal), 2) No matter what I check or uncheck in the Gnome-Network-Manager it still wants to search for a wireless connection and drops my mobile broadband card. 3) I removed the broadcom driver but the GNM fails to make a connection to the Mobile Broadband card and still shows broadcasting networks in the neighborhood.

I seldom use my wireless card (broadcom), my mobile broadband card is almost exclusively what I use so this is unbelievably annoying.

Does anybody have any ideas????

---

### Post by utkarsh009 on 2010-07-02
use sakis 3g. it's the software which should be included as default but unfortunately isn't. download it from [www.sakis3g.org]("http://www.sakis3g.org"). use it and post whether successful or not. well its the only software from which i have been able to connet to the internet and also got increased speed somewhat close to that in windows.(actually, slightly more)

---

### Post by dvn3ch on 2010-07-02
> **utkarsh009 said:**
> use sakis 3g. it's the software which should be included as default but unfortunately isn't. download it from [www.sakis3g.org]("http://www.sakis3g.org"). use it and post whether successful or not. well its the only software from which i have been able to connet to the internet and also got increased speed somewhat close to that in windows.(actually, slightly more)

utkarsh009, you are the sh!##.  That script worked perfectly.  From the website and from what I witnessed, it will work with just about any mobile broadband modem.  The strange thing was, as I typed the last line in the terminal my Alltel connection icon appeared like magic.  I have restarted and rebooted about 12 times and the connection comes up in less than 2 seconds with a "Connection Established" notification.

Thanks a million for that one.:D

BTW, do you have to do this for all users?

---

### Post by dvn3ch on 2010-07-02
Sorry, may have to hold off the celebration for now.  I have lost connection again.  It sees the modem but just will not connect.  I have logged off and rebooted many times and nothing.

Update: I ran gnome-ppp at root and rebooted.  It connected and seems to be steady after several reboots and log-offs/switch users.  I will report how it is doing in a couple days.

---

### Post by utkarsh009 on 2010-07-03
did you get any error information?
if yes then please tell about it.
if it is related to modem-manager, then you have to disable networking of the network manager applet on your taskbar. just right click on the icon and check "disable networking". 
post your results after that.

---

### Post by hyballs on 2010-08-09
Hi folks, I finally got around to installing 10.04 and then taking heed of PDC's advice re: To disable CHAP in post #3....which I did....and for the last couple of days things have been working in a normal fashion.  Although I am keeping my fingers crossed. ;)

The HuaWei E160E dongle seems to be a strange one!

I thank all who have posted in this thread and hope to return the favour some time in the future when I know what I am doing with Ubuntu! ):P

---

