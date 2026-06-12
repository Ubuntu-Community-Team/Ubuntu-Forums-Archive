---
title: "Wifi WORKING.. but connection drops after some time.."
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by nismoskys on 2006-02-23
Thanks to the awesome info on this site, and **hours** of fiddling, i finally got wifi working (yay!). very happy, im finally connected and dont have 2 go back and forth to the comp in the other room to go online (to ubuntuforums.org of course).

However, yes unfortunately, however... with the perfect-workingness i get (using network manager (and?) ndiswrapper..(dunno i installed ndiswrapper first but then installed networkmanager to try to fix the problem) disconnected after some use. i believe it happens when i start doing too many things online, but im not sure. the activity light on my Linksys WUSB54G V4 blinks fine, but then the light will just stay on.. thats when i know im disconnected.

i had this problem when i was using just ndiswrapper, and had to restart everytime it did this.
but when i installed network manager, i just have to unplug the USB, "Stop all wireless devices", plug back in, and "start all wireless devices" again. and it works fine.. but will reoccur again after some time.

i've been using this wifi adapter for quite a while and no have not ever encountered this problem in windows.

know whats the problem?:confused: 

thanks

---

### Post by dbarbi1 on 2006-02-23
I'm experiencing the same thing on my other (play) laptop.  It has a D-Link dwl-650 revision M card, using a nonstandard driver that some one posted in this forum for that card.  I'm also using Network Manager to control connectivity.  It works until i try downloading something or putting it under heavy load, then it disconnects and i have to reset the card.

---

### Post by stilmatik on 2006-02-23
whoops

---

### Post by stilmatik on 2006-02-23
booyah, I HAVE THE SAME PROBLEM

---

### Post by nismoskys on 2006-02-23
3 noobs 1 problem.

We sit. We wait.
lol


(okay even if you 2 guys arent noobs lol i am.. somewhat).

---

### Post by HumBug on 2006-02-24
I had this problem too with my sis163u wifi usb stick. After i installed the latest ndiswrapper (1.10) it only looses connection after a few days (my pc is always on). So upgrading ndiswrapper might help...

---

### Post by direwolf on 2006-02-24
are you all using ndiswrapper?

---

### Post by dbarbi1 on 2006-02-24
Alright I think I've got it working now.  It's been downloading a file now for the past 20 minutes at least which it never did before.  I edited the config.opts file located /etc/pcmcia.  In that file there are a few lines that say "include memory xxxxxx" and "include port xxxxxx", basically all i did was comment them out and reboot.  
   I havent noticed any problems so far from commenting them out, but that was only an hour ago and i havent extensivly tested things since then.  Most likely it was only one or two lines in there that were causeing the problem, but i was too lazy to go through and try one line at a time.
   Let me know if this helps.

---

### Post by nismoskys on 2006-02-26
hmm.. im not home right now.. but ill try that when i do get home.. btw though, sorry, noob question: comment them out? add quotes around them? thanks

---

### Post by billylh on 2006-02-28
im also using the wusb54g v4 with ndiswrapper and the rt2500usb driver provided on my linksys disc.  my connection drops after 10minutes or so of inactivity.  my only solution is to reboot the computer in order to regain connection.

---

### Post by nismoskys on 2006-03-01
you should use network manager, maybe then it would be easier to reconnect when your connection drops..

as for me, i switched back to LAN, yay! no more disconnects, it feels so good :)

---

### Post by trubblemaker on 2006-03-01
sounds like yall need to find a different driver for your ndiswrapper to run, I had a simalar issue and after changing the driver to the correct one I was golden, 
 to find out what actual card you have you can look at your systems specs that came with your box or 
use 
```
lspci | grep Ethernet
```
to detemine which driver you have 

here's an imcomplete list of drivers: (from fwcutter)

```
bcmwl5.sys	Link
-------------   -------------------------------------------------------
3.20.23.0	http://nicolas.bonifas.free.fr/inspiron/bcmwl5.sys
                http://www.fujitsupc.com/downloads/Wireless_Broadcom_802.11g_WPA_V3.20.23.0_XP_2K.exe
                http://files.codykrieger.com/mn720drivers/bcmwl5.sys
3.30.15.0	ftp://ftp.asus.com.tw/pub/ASUS/wireless/WL-100g-03/Driver_330150.zip
                http://web.belkin.com/support/download/files/F5D7010-v2.4.4.exe
                http://www.belkin.com/support/download/downloaddetails.asp?file_id=1425
                http://communications.siemens.com/repository/1135/113557/pccard54_V11200_eng.exe
3.40.20.0	http://broadband.motorola.com/consumers/products/WN825g/downloads/WN-WPCI-Web-Update-v1.1.exe
                http://broadband.motorola.com/consumers/products/WPCI810g/downloads/WN-WPCI-Web-Update-v1.1.exe
3.40.25.3	http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz
3.40.69.0	http://metahusky.net/~gavin/home/bcmwl5.sys
3.40.73.0	http://ftp.us.dell.com/network/R83097.EXE
                ftp://ftp.us.dell.com/network/R83097.EXE
3.40.100.0	ftp://ftp.wildpackets.com/pub/outgoing/brcmDvr340rc100a~@.zip		
3.60.7.0	ftp://ftp.asus.com.tw/pub/ASUS/wireless/WL-100g-03/Driver_3607.zip
3.60.7.5	http://www2.melcoinc.co.jp/pub/lan/wdrv_660.exe
3.70.12.0	http://files.wl500g.info/asus/wl120g/drivers/3.70.12.0.rar
                ftp://ftp.compaq.com/pub/softpaq/sp28001-28500/sp28198.exe
3.70.17.0	ftp://ftp.compaq.com/pub/softpaq/sp28501-29000/SP28538.exe
3.90.16.0	http://www.usr.com/support/5421/5421-files/5421-na.exe
3.90.41.1	http://www2.melcoinc.co.jp/pub/lan/wdrv_661.exe
3.100.35.1	http://ftp.us.dell.com/network/R94826.EXE
3.100.46.0	ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip
                http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true
                ftp://ftp.compaq.com/pub/softpaq/sp29501-30000/SP29845.exe
3.100.64.0	ftp://ftp.compaq.com/pub/softpaq/sp30501-31000/SP30676.exe
3.100.64.50	http://www2.melcoinc.co.jp/pub/lan/wdrv_661.exe
3.100.65.1	ftp://ftp.hp.com/pub/softlib/software5/COL3601/ob-31557-1/SP30379.exe
3.120.27.0	ftp://ftp.us.dell.com/network/R102318.EXE
3.140.16.0	http://files.techlabs.by/getfile.php?id=1844

bcmwl564.sys	Link
-------------   -------------------------------------------------------
3.70.17.5	http://ubuntuforums.org/attachment.php?attachmentid=186
3.100.64.0	ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip

bcmwl5a.sys	Link
-------------   -------------------------------------------------------
3.90.16.0	http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true

d11ucode.o	Link
-------------   -------------------------------------------------------
3.60.7.0	http://files.wl500g.info/asus/wl500g/gpl/broadcom/src/wl/linux/ap_d11ucode.o
3.90.7.0	http://dune.hu/gpl_tarballs/asus/broadcom/src/wl.orig/linux/ap_d11ucode.o

wl.o		Link
-------------   -------------------------------------------------------
3.50.21.0	http://nthill.free.fr/openwrt/sources/wl/wl-2.02.7.tar.bz2
3.60.13.0	http://nthill.free.fr/openwrt/sources/wl/wl-2.09.1.tar.bz2
                http://nthill.free.fr/openwrt/sources/wl/wl-3.37.6.tar.bz2
3.90.37.0	http://openwrt.inf.fh-brs.de/~nbd/wl1.o

wl_apsta.o	Link
-------------   -------------------------------------------------------
3.31.16.0	http://puma.ttc.cz/~jaha2x/openwrt/modules/drivers/net/wl/wl_apsta/wl_apsta.o
                http://jak.kvalitne.cz/pub/puma.habrova.jarov.czf/~jaha2x/wl500/wl_apsta.o
3.130.20.0	http://openwrt.inf.fh-brs.de/~nbd/wl_apsta.o
```

there's also hope: in the new kernel Dapper, stable in April it has native support for a bunch of drivers.

---

### Post by GTroy on 2006-04-05
same problem here.  I use a netgear wg111 usb v.2   I use ndiswrapper too.  seems to have just started.

---

### Post by akaihola on 2006-04-27
The files.techlabs.by link is outdated. The correct link is:
[http://techlabs.by/getfile.php?id=1844](http://techlabs.by/getfile.php?id=1844)

---

### Post by sefs on 2006-06-05
I have the same problem after upgrading to dapper.  Using ndiswrapper 1.16 with the Ralink rt73 driver.

USB adapter is the cnet usb dongle.cwp-854.

To get around the problem i have to physically unplug the dongle from the usb port and plug it back in and the network comes back up.

I am not sure if its due to too much activity on the computer but thats the feeling i get.

---

