---
title: "Wireless Network Dualband 300N Gaming Adapter II WL-329 GM problem"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by Tuxdroid on 2011-03-02
Hi i think i requested in wrong section of this forum, no replies atm so i begin the same post here.

I have a Wireless Network Dualband 300N Gaming Adapter II WL-329 GM, my new PC need ubuntu 10.10, just hate the slow windows. But i'm not sure its possible to install this.
Its not possible to get a wired connection so need this usb. 

i have a laptop if any drivers had to get downloaded ...

I  ask sitecoms support for help, the onlything i get is this

> Dear Mr. ...
 
 Thank you for contacting the Customer SITECOM.
 
 I understand from your e-mail that you are looking for drivers for Ubuntu 10.10.
 
 Unfortunately, not a Linux operating system supported by Sitecom.
 
 We have officially only drivers for our products for Windows and Mac OS.
 
 Which does not mean your product will not work under Linux.
 
 Possibly the product itself or recognized by Linux, the chipset driver solution.
 
 This chipset driver is not offered by Belkin and is not supported.
 
 Use of such drivers is therefore at your own risk.
 
 Your product uses the Ralink RT3572 chipset.
 
 You can find it by googling the driver.
 
 I hope this sufficient information and evidence or information that your problem solved.
 If you have further questions on this topic please feel free to contact  us again, please notify the following reference number: 110227-0040  SIT.
 
 Sincerely,
 
 
 SITECOM Customer Care
 Diederick 			 		

So i need RT3572 any i dea how to install etc.

Greetz

Tuxdroid

---

### Post by chili555 on 2011-03-02
I have a pretty fair idea how to install it: [http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta](http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta)

Before you proceed, how about plugging the device in and running, in a terminal:```
lsusb
```Please post the result. Let's be sure that's the correct driver for your device.

---

### Post by Tuxdroid on 2011-03-02
ok will try to morrow, because ubuntu is not installed, just want to be sure its no wast of time :p
 
thx for reply
 
 
btw > In order to compile drivers, you must install build-essential and kernel-headers-generic. Obtain a wired ethernet connection and do:i dont have the ability to get wired

inserted it in my laptop also on ubuntu 10.10 

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04ca:0030 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0df6:0041 Sitecom Europe B.V. WL-329 Wireless Dualband USB adapter 300N
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tom@tom-AMILO-PI-1536:~$ 


---

### Post by chili555 on 2011-03-02
```
modinfo rt3572sta | grep 0041
alias:          usb:v[COLOR="Red"]0DF6[/COLOR]p[COLOR="Red"]0041[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```That's the correct driver for your device.> i dont have the ability to get wiredIt will be a real challenge to download and install the package otherwise, but maybe we have a miracle or two available.> will try to morrow, because ubuntu is not installed, just want to be sure its no wast of time Let me know when you're ready. I'll be anxious to hear from you.

---

### Post by Tuxdroid on 2011-03-03
Ok, Ubuntu 10.10 64bit is installed, no connection can be established and nothing in additional drivers

---

### Post by chili555 on 2011-03-03
Please run and post:```
sudo modprobe rt3572sta
dmesg | grep rt3
iwconfig
```Thanks.

---

### Post by Tuxdroid on 2011-03-03
ik i did it.

>    	 	 	 	p { margin-bottom: 0.21cm; }  tom@tom-Aspire-X5950:~$ sudo modprobe rt3752sta  
 [sudo] password for tom:  
 FATAL: Module rt3752sta not found.  
 tom@tom-Aspire-X5950:~$ dmesg | grep rt3  
 tom@tom-Aspire-X5950:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

---

### Post by chili555 on 2011-03-03
> FATAL: Module rt3752sta not found. It looks like you haven't correctly installed the driver. Do you want to retrace your steps and try again? Any errors encountered along the way?

---

### Post by Tuxdroid on 2011-03-04
ow didnt tried to install the driver bescause your manual said that i had to get a wired con, but i dont have one :s

---

### Post by chili555 on 2011-03-04
:s ???

So I guess you thought if you skipped a few steps, you could go to the last step:> tom@tom-Aspire-X5950:~$ sudo modprobe rt3752sta
[sudo] password for tom:
FATAL: Module rt3752sta not found. And then a miracle would occur.

Here's a whole thread about missing the Network Manager icon: [http://ubuntuforums.org/showthread.php?t=1646150&highlight=applet](http://ubuntuforums.org/showthread.php?t=1646150&highlight=applet)

---

### Post by Tuxdroid on 2011-03-04
sry chili

only working with ubuntu for a month now, and that was on a laptop which was full supported, i dont know every code, so i just jam thoughtless on buttons now

tomorrow i will move my desktop to the basement to get wired con, and follow your guide

---

### Post by Tuxdroid on 2011-03-05
dear chili

i followed your guide
my usb is now reconized but i cqn't connect wireless

> sudo modprobe rt3572sta
[sudo] password for tom: 
tom@tom-Aspire-X5950:~$ dmesg | grep rt3
tom@tom-Aspire-X5950:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"SitecomA5D8D4"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-39 dBm  Noise level:-39 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




---

### Post by chili555 on 2011-03-05
Is the wired ethernet disconnected? Network Manager will disallow wireless if wired is available.

When you click the Network Manager icon, do you see your network? When you click it, does it try to connect? Are you asked for your encryption key? What does this tell us?```
sudo iwlist ra0 scan
```

---

### Post by Tuxdroid on 2011-03-05
i see all wireless networks, and he is trying to connect automatically, he asked my WPA key, so no problems, but somehow he can't connect

Ok tryed to reinstall it, but didnt work, so installed ndiswrapper, but also didnt work, removed ndiswrapper, now i can't even see any wireless connection, in additional drivers de drivers are still activated :s

tom@tom-Aspire-X5950:~$ sudo modprobe rt3572sta
tom@tom-Aspire-X5950:~$ dmesg | grep rt3
tom@tom-Aspire-X5950:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

tom@tom-Aspire-X5950:~$

---

### Post by chili555 on 2011-03-05
> so no problems, but somehow he can't connect

Ok tryed to reinstall it, but didnt work, so installed ndiswrapper, but also didnt work, removed ndiswrapper, now i can't even see any wireless connection, in additional drivers de drivers are still activated :sI don't even know what to say. You were 95% done and you decided to install and remove and reinstall things on your own and now it's wrecked. Your reaction to this is 

:s

I have to go cry.

---

### Post by Tuxdroid on 2011-03-05
ok idd i wrecked it :s, gonna reinstall everything including windows and ubuntu

---

### Post by Tuxdroid on 2011-03-05
thx chili

For the manual, the patience and the TIME, a reinstalled ubuntu and everything including the USB wireless works like a charm :p, the difference with last try, is that i first updated my kernel from 22 to 27.

Somehow in 22: this command didnt work 

sudo apt-get install build-essential linux-headers-generic 


but i could continue  with CD...
afterwards he asked my to update to latest version ... no wireless any more

No i just installed ubuntu and updated to latest version and then tried the guide, i only hope i wont have to call your help again if he updates again or if 11.04 comes out

MANY THX

Best regards 

Tuxdroid

---

