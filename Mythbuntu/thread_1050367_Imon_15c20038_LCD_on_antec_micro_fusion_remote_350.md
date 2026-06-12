---
title: "Imon 15c2:0038 LCD on antec micro fusion remote 350"
date: 2009-01-25
forum: Mythbuntu
---

### Post by Aliheth on 2009-01-25
Hi

I recently bought an Antec micro fusion remote 350 case.  I tried the LCD and remote with vista which worked fine. 

Using Kubuntu 8.10 with KDE 4.2 RC1 I tried to get the LCD working using lirc and lcdproc using the instructions from [here]("http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote?pli=1")
however the LCD just displays complete gibberish, on a cycle (see the piccies attached) 

When using IRW with the included VERIS RM100 remote the buttons i press are recognised when using a custom lircd.conf. I can also get the "ugly clock" displayed by running 

perl -e 'print pack "H*", "80000000091e0088"' > /dev/lcd0

I've also tried it on Kubuntu 8.04.1 with the same results.  I'm sure i'm probably doing something stupid, but after spending 2 days trying to figure it out i'm stumped! 

my results from "sudo cat /proc/bus/usb/devices" is as follows:    

T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1     
P:  Vendor=15c2 ProdID=0038 Rev= 0.01                            
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA                           
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms                           
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms 

The thread on [http://xbmc.org/forum/showthread.php?p=251930]("http://xbmc.org/forum/showthread.php?p=251930") says that these drivers should be "imon_lcd" However, i'm not sure how to change this. 

When following the instructions on [http://xbmc.org/forum/showthread.php?p=251930]("http://xbmc.org/forum/showthread.php?p=251930") i couldn't do the sudo dpkg-reconfigure lirc-modules-source step as I would get "Error! 
"Build of lirc_imon.ko failed" and "Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree" output

If someone could give me some suggestions/ pointers I would be very grateful!                  

Thanks 

Ali :D

---

