---
title: "Windows Wireless Driver problem"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by Jamie13810 on 2010-02-12
I have recently installed kubuntu 9.04 on my laptop. i then connected an ethernet cable and upgraded it to kubuntu 9.10. but i would like to connect to the internet using wireless. but i do not know how to install the windows wireless driver for my card on this OS. It would be greatly appreciated if someone could tell me exactly what to do. my card is: D-link AirPlus G DWL-g630.

Thankyou for your help if you do give it.

---

### Post by Xog on 2010-02-12
Install NDISwrapper

search online for your driver.

??

get online!

edit:

sorry, i'll be a little more helpful :p

Install NDISwrapper. If you don't have internet, you can use the liveCD and navigate to cdrom/pool/main/n/ndiswrapper and install all of them.

The driver you need is on the dlink website [http://www.dlink.com/](http://www.dlink.com/)

Select your country
on the top right click on Product Quickfind
scroll down to DWL-G630
on the right click "Support Resources"
select DWL-G630
click "Drivers"
select download now for "WinME, Win2K, WinXP" (or try clicking here: [ftp://ftp.dlink.com/Wireless/dwlg630/Driver/dwlg630_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg630/Driver/dwlg630_driver_100.zip) )
extract those files to a new folder anywhere you want

Open NDISwrapper by clicking System > Administration > Windows Wireless Drivers

Click Install Driver
go to where you extracted those files, and select the .INF file.

You should be able to connect now, even if it does give you error messages.

---

### Post by Jamie13810 on 2010-02-12
How would i install NDISwrapper with an internet connection? because i have an ethernet connection. i do not know what liveCD is or where it is. i'm sorry if i'm a little annoying but i.m not that great with this sort of stuff.

---

### Post by Xog on 2010-02-12
#

[http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
#

[http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
#

[http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk)

---

### Post by Jamie13810 on 2010-02-12
i didnt need the first 2 links as i have found the files in the original install folder (which you referred to as liveCD) it didnt have ndisgtk in it so i used the link you provided. i have setup the wireles, its working and im using it to post this. THANKYOU so much for your help it was much appreciated. i dont think i need anymore help. thanks again

---

### Post by Xog on 2010-02-13
You're welcome :-)

Just out of curiosity, did it give you an error message after installing the driver?

---

### Post by Jamie13810 on 2010-02-13
no, there was no error message.

---

