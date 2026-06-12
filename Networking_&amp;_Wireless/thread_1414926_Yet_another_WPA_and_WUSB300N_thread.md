---
title: "Yet another WPA and WUSB300N thread"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by ColinMc on 2010-02-24
I'm running Ubuntu 9.10 for reference...

Ok so I went through what a bunch of threads here described how to do...installed ndiswrapper, installed the WUSB300N driver. I can now see my network but when I try and connect it won't connect. Asks for the WPA passkey again, i put that in...it keeps searching for a while then just asks for the passkey again. Yes it is the right passkey.

I can connect through my PCI modem(with an ethernet cable) no problem but really need to get this wireless working. The router is a Linksys system setup on a Dell PC running Windows XP if that makes a difference.

I've searched everywhere and found a few threads with similar problems...and I do get the "command 12" problem, but i'm not sure how to get around this. The couple threads that describe how to do it involve using two Linux machines...and that I don't have. 

Sorry but yeah i'm completely new to Linux...loving it so far lol.

Or if someone can recommend an easy to get wireless USB network adapter that would be easier to use i'd go that route if it's the adapter causing the problems. I don't want to go buy a new one though and still not be able to connect to my WPA network...

---

### Post by Redquill on 2010-03-04
8:44 AM 03/03/2010   RLD
How I Installed Linksys WUSB300N Wireless adapter under Ubuntu 910

     Obtain a Windows Driver appropriate for this adapter that can be used in conjunction with Ndiswrapper.
(I tried the latest Vista one but could not get it to work so used the WinXP_2K one.)  Here is the contents of the package that I downloaded using Windows XP as my laptop dual boots XP SP3 and/or Ubuntu910.

 Directory of C:\Linksys Driver\WUSB300N_20071204\Drivers\XP_2K

03/01/2010  07:35 PM    <DIR>          .
03/01/2010  07:35 PM    <DIR>          ..
09/26/2007  05:00 PM           470,912 Mrvw243.sys  
12/03/2007  03:54 PM            11,042 mrvw245.cat
09/26/2007  04:58 PM           461,952 Mrvw245.sys
10/26/2007  05:07 AM            21,169 netmw245.inf

     If necessary update ndiswrapper-common and ndiswrapper-utils.  Also ndisgtk if you are using the toolkit
but these instructions do not use the toolkit.  I moved the four driver files into ~/Public/ .

     Start up a Terminal and run:

           sudo ndiswrapper -i ~/Public/netmw245.inf    (to install the windows driver)
           ndiswrapper -l   (you should now see the driver is installed and the device is present)
           sudo ndiswrapper -m   (add alias)
           sudo depmod -a       (make dependencies)
           sudo modprobe ndiswrapper   (this should load the module and attempt a connection)

           tail /var/log/messages  (check for any error messages)

     If it is working now you need to configure your connection but first configure Network Manager to manage
the wireless adapter.
           sudo gedit /etc/NetworkManager/nm-system-settings.conf (under [ifupdown] next line should be managed=true )

     I used the Network Manager Network Icon that should be located at the right section of the top panel. For a wireless connection
this will be a tiny antenna with dots or a bar graph. When searching for wireless connections it will be a spinning image.  Right click 
the icon and make sure enable wireless is checked and then select edit connections. Select wireless and add the information appropriate 
for your setup.

           sudo ifup wlan0  (to start the connection) 

           iwconfig   (should show the wireless device as wlan0)

     Here is iwconfig output for my WUSB300N when linked to my AP.  For some reason it seems not to be able to run at 802.11n draft
speeds under Ubuntu 9.10.  It does ,however, do so when I boot Win XP SP3 on the same nearly 8 year old Toshiba Satellite Pro laptop.

wlan0     IEEE 802.11g  ESSID:"*********"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:14:D1:C3:5F:96   
          Bit Rate=52 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

      I always try the route command first to see if my connection is progressing.  Here are some other commands that I used to try to
figure out what was happening.  I hope this information is correct but I am doing some of it from memory and I am very new to the
use of Ubuntu but I really do like it, so far!  I just did get this functioning reliably during the last two days. 
      
           sudo ifdown wlan0  (will stop wlan0)
           sudo iwlist scan
           sudo lshw -C network
           sudo cat /etc/network/interfaces
===================================================================================================================================
Thanks to the following web page for much help to me on this topic:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart)

---

