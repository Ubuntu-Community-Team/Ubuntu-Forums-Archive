---
title: "CrossPlatformUI for reliance Netconnect Broadband"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by raunhar on 2010-10-16
I am trying to install CrossplatformUI from the CD to run Reliance Netconnect Broadband on Ubuntu 10.04
While installing it says that "Failed to install CrossPlatformUI-V-1.0.38-Reliance HSD-i386-Ubuntu.deb

How do I solve this problem.

While trying to uninstall it through Synaptic Package Manager i get the error E: crossplatformui: subprocess installed post-removal script returned error exit status 1

---

### Post by amitmandal on 2010-10-16
hello raunhar,
   I'm on 10.10 maverick and I confirm that Reliance Netconnect Broadband (usb modem) is being automatically detected by 'Network Manager'. I have had tried to install the cross-platform UI .deb file in 9.10 and I encountered the same error.
  Coming back to what i'm delighted about :) is in 10.10, the Reliance Broadband usb modem (ZTE AC2726 model) is working out of the box. I guess this is b'cuz of the support in the new linux kernel. Some changes were to be made, though, @ the Network Manager console: Mobile Broadband section -
Under 'PPP' tab, in 'Allowed methods' select only 'PAP'. By default all available options are checked. In 'Compression' keep 'MPPE' unchecked.
 Thats it. You of course fill out your 'username' and 'password' under the 'Mobile Broadband' tab and your ready to go.

---

### Post by raunhar on 2010-10-19
I have ZTE 2736. But it is not working on any Ubuntu version even 10.10

---

### Post by raunhar on 2010-10-21
I was able to get the device detected and working. It worked one day and the next day I tried, it got detected, but did not connect. The network manager tries to connect, but after some time, it says Network Discoonected.

I tried keeping all/PAP checked. But no success.

---

### Post by alexfish on 2010-10-21
Hi

possibly try sakis3g, it also has good diagnostics

**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=_xfATNXQK8jh4Abx14CoDA&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

they also have a forum , very helpful

in  Ubuntu 10.10 you may have to disable modem-manager

alexfish

---

### Post by raunhar on 2010-10-21
Sakis3g has mentioned that it is recommended for GSM not CDMA.
Reliance is CDMA, so I do not think that it will work.

I am able to create the connection, but unable to get it connected. It is unable to locate the network under LINUX but under windows there is no problem.

---

### Post by alexfish on 2010-10-21
Hi
sakis3g can act as mechanism to prepare the modem

However lets see   if the device is see on the system

ensure the device is connect .From the terminal enter this code:


Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines which indicate the device and post only those parts

then

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]


alexfish

---

### Post by amitmandal on 2010-10-21
hello raunhar,
 in case these help. I'm posting this message using connection from ZTE AC2726.

---

### Post by raunhar on 2010-10-22
result of usb-devices
T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fff1 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Tech
C:  #Ifs= 6 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


Result of 
ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-10-22 10:52 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-10-22 10:52 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-10-22 10:52 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-10-22 10:52 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root 13 2010-10-22 10:52 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if04-port0 -> ../../ttyUSB4

---

### Post by m4enigma on 2010-11-07
Hi,

Just wanted to say thanks. I got my Reliance Netconnect working in 10.10 due to this post. Thanks a lot guys. You rock!   :guitar:

---

### Post by kiers on 2010-12-20
ahh...yes. but are there config options to connect only high speed for example? what are the settings?

---

### Post by alexfish on 2010-12-20
Hi

not quite sure what options your looking for

however can have a look through

[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

How to set ZTE specifics post #8

and then how the devices baud rate can be changed post #26
sometimes important if the device has been left in low baudrate / by other software accessing the device , such as sms texting etc

---

### Post by kiers on 2010-12-20
Alex, WOW your link is a treasure trove of info!

Yes , what i meant is if you are using the cross platform dialer that zte and reliance provide, you will see that you have a choice of connecting in hybrid mode, or ONLY HSD mode. it appears you have captured all of that on your "HOW To" page! 

where'd you get all that? Even reliance "tech support" doesn't know this stuff? is that output from sarkis3G? brilliant!
making this public enables full functionality of the silly little zte dialer replicated for Linux.
thanks!

---

### Post by krishnitdgp on 2010-12-21
> **raunhar said:**
> I am trying to install CrossplatformUI from the CD to run Reliance Netconnect Broadband on Ubuntu 10.04
While installing it says that "Failed to install CrossPlatformUI-V-1.0.38-Reliance HSD-i386-Ubuntu.deb

How do I solve this problem.

While trying to uninstall it through Synaptic Package Manager i get the error E: crossplatformui: subprocess installed post-removal script returned error exit status 1
Hi RAUNHAR, I'm also facing the same problem installing crossplatformUI bsnl evdo. installation failed and unable to uninstall showing error. I do not know how to get rid off it. If you any solution plz help me out....thanx

---

### Post by sunasra on 2011-05-13
> **m4enigma said:**
> Hi,

Just wanted to say thanks. I got my Reliance Netconnect working in 10.10 due to this post. Thanks a lot guys. You rock!   :guitar:

@enigma

How did u solved problem?

---

### Post by sidfadnis on 2011-06-01
hi. I too face same problem. I have Huwei EC150 device. Ubuntu 10.04, 10.10 and 11.04 all have inbuilt support. But it lasts good only till the device works on broadband+ network. My plan forces the device to switch to CDMA 1X speed after 5 GB usage. And the inbuilt connection does not support connecting to CDMA 1X network. 

However some browsing on internet gave me a good workaround. Logon to windows, use the dialer software provided and connect the device to 1X speed network. Leave the device connected. Restart, only this time start Ubuntu. And then the device automatically connects to internet.

But it won't connect to 1X on its own. I think the solution here is to get the installer provided in CD converted to suit Ubuntu OS. The installer provided for me is for FedoraCore 6.0 distro. 

Any clues how to do that ?

---

### Post by Fawk3s on 2011-10-29
> **amitmandal said:**
> hello raunhar,
   I'm on 10.10 maverick and I confirm that Reliance Netconnect Broadband (usb modem) is being automatically detected by 'Network Manager'. I have had tried to install the cross-platform UI .deb file in 9.10 and I encountered the same error.
  Coming back to what i'm delighted about :) is in 10.10, the Reliance Broadband usb modem (ZTE AC2726 model) is working out of the box. I guess this is b'cuz of the support in the new linux kernel. Some changes were to be made, though, @ the Network Manager console: Mobile Broadband section -
Under 'PPP' tab, in 'Allowed methods' select only 'PAP'. By default all available options are checked. In 'Compression' keep 'MPPE' unchecked.
 Thats it. You of course fill out your 'username' and 'password' under the 'Mobile Broadband' tab and your ready to go.


Hey, Amit.. The configuring the authentication methods part really helped.. Kudos!

---

