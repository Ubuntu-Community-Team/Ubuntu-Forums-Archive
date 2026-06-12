---
title: "Wireless Internet really slow in Ubuntu 9.04!"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by v2rocketboy on 2009-09-25
Hi all, I recently got sick of xp being really laggy so i finally switched to ubuntu 9.04, i think the most recent version, 
 
everything works fine, I can connect to the internet, but it is really friggen slow.
 
I know that it can connect to the internet because google loads, but after about 4 - 5 frustrating minutes.](*,)
 
Its a usb netgear wireless network adapter too if that helps.
 
Can anyone help, Im only new to this so I have no clue how to code stuff?
 
Plz Help
 
:(

---

### Post by MaindotC on 2009-09-25
Are you dual booting?  Have you downloaded all the latest updates?

---

### Post by v2rocketboy on 2009-09-26
I am dual booting with xp, i haven't been able to download latest updates because the wireless is that slow it times out, its not the range because that is fine, i downloaded my copy of ubuntu last night.

---

### Post by v2rocketboy on 2009-09-26
now the internet just doesn't connect at all, but it is perfectly connected to the router.

---

### Post by baskar007 on 2009-09-26
> **v2rocketboy said:**
> now the internet just doesn't connect at all, but it is perfectly connected to the router.

your ISP have enabled IPv6 ?
If not try to disable IPv6.

if it does not work edit nss.conf file.
:lolflag:

---

### Post by v2rocketboy on 2009-09-26
I did some tinkering somehow, and now it occasionally connects and loads up the google page, i go to click google images and it never loads, i close, open, doesnt load, reboot, and it may load the google page, what is ipv6?

---

### Post by v2rocketboy on 2009-09-26
I did a ipconfig/all in command prompt on the computer (runs on vista) which is connected to the (modem/router) unit, there is a pressence of ipv4 but no ipv6, does that mean anything?

---

### Post by MaindotC on 2009-09-26
If you can't connect to the internet, how are you posting this???

---

### Post by Jugantor on 2009-09-26
Hey v2RocketBoy,

Sorry for hijacking your thread, but its true that I am facing almost the same problem as yours. I have dual boot system with Ubuntu 9.04. The odd part is ... the wireless internet works fine when I am on Windows(that answers strAlen's question!), and then when I switch to Ubuntu, sometimes the internet works(very fine) and at other times, it doesn't. It just stops working all of a sudden... although the icon in the toolbar(beside the clock) says I am actively connected to wireless. 

The situation becomes frustrating when I am on Ubuntu, browsing something on the internet and the internet stops working all of a sudden.

Please Help !:confused:

Jug

---

### Post by himynameiszac on 2009-09-26
Same thing has been happening to me. I am new to Linux. Finally got fed up with Windows 7 last week. I needed something new, and this is awesome!
I currently have LinuxMint 7 installed as my OS and have the same problem, I also had it when I was trying out Ubuntu 9.04(it was the first one I installed). 

The strange thing is, though, I tried Fedora(along with almost every other distro out there) and I had 98-100 percent connectivity all the time. Where-as, on Mint and Ubuntu(along with some other distros I tried) I get anywhere from 30-60. I tried installing the madwifi, but to no avail. It doesn't work at all, doesn't even *show *any wireless connection. 

Don't worry, this definitely will not sway me back to Microsoft like it did to a few others I saw. I can put up with it, I just am looking for a fix. I heard some people got there's to work with ndiswrapper though. 

If anyone knows anything about that working please let us know.

---

### Post by himynameiszac on 2009-09-26
And sorry for jumping on the thread with no solutions, but I can help out with info if it's needed.

---

### Post by baskar007 on 2009-09-26
> **v2rocketboy said:**
> I did some tinkering somehow, and now it occasionally connects and loads up the google page, i go to click google images and it never loads, i close, open, doesnt load, reboot, and it may load the google page, what is ipv6?

This may help you:
h[ttp://softwareroxer.blogspot.com/2009/09/how-to-disable-or-remove-ipv6-on-ubuntu.html]("http://softwareroxer.blogspot.com/2009/09/how-to-disable-or-remove-ipv6-on-ubuntu.html")

---

### Post by baskar007 on 2009-09-26
Sorry for the sloppy post on above,

IPv6 mean Internet Protocol version 6.:P

Currently IPv4 is a default internet protocol. Ipv6 is a next generation internet protocol.

as you can see your problem is ubuntu comes out with IPv6 enabled, So if your ISP(country) have not enabled IPv6 then you need to disable it.

first try to disable IPv6: [http://softwareroxer.blogspot.com/2009/09/how-to-disable-or-remove-ipv6-on-ubuntu.html ]("http://softwareroxer.blogspot.com/2009/09/how-to-disable-or-remove-ipv6-on-ubuntu.html")

If it not work I'll give you anothersolution.:)

---

### Post by Jugantor on 2009-09-26
I did that ... the problem is still there....

I also tried to disable ipv6 by typing 'about:config' in the browser and setting the value of network.dns.(something).disable.ipv6  to true

did a reboot...

But the problem still persists](*,)](*,)](*,)

---

### Post by baskar007 on 2009-09-26
> **Jugantor said:**
> I did that ... the problem is still there....

I also tried to disable ipv6 by typing 'about:config' in the browser and setting the value of network.dns.(something).disable.ipv6  to true

did a reboot...

But the problem still persists](*,)](*,)](*,)

the problem may be name server switching .

type in terminal
>  sudo gedit /etc/nsswitch.conf


Now the file look like this:

> #
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

** hosts:          files**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis



In this file change** hosts:          files  **to **hosts:          files          dns**          now save and restart.
Net should come back with its speed.:lolflag:

---

### Post by brncao on 2009-09-27
I'm also having problems. I tried disabling ipv6 and it still doesn't work. I run my tests on speedtest.net and compared the results with win7. win7 is 3 times faster than Ubuntu. Don't know what the problem is.

---

### Post by baskar007 on 2009-09-27
> **brncao said:**
> I'm also having problems. I tried disabling ipv6 and it still doesn't work. I run my tests on speedtest.net and compared the results with win7. win7 is 3 times faster than Ubuntu. Don't know what the problem is.

optimize your mtu setting on connection setting.

---

### Post by Jugantor on 2009-09-27
> **baskar007 said:**
> the problem may be name server switching .

type in terminal


Now the file look like this:




In this file change** hosts:          files  **to **hosts:          files          dns**          now save and restart.
Net should come back with its speed.:lolflag:
I think my wireless internet has gone better now.. Thanks a lot.
  The connection does get slow sometimes (and sometimes stops working for a minute or 2, but comes back to original speed).
Any solution for that ?? (thats because the internet runs almost flawlessly when I am on Windows, although I have no intention of switching back to it)

Frankly speaking, I have to keep my fingers crossed everytime the internet stops working!:)

Jug

---

### Post by baskar007 on 2009-09-27
> **Jugantor said:**
> I think my wireless internet has gone better now.. Thanks a lot.

Frankly speaking, I have to keep my fingers crossed everytime the internet stops working!:)

Jug

Glad to help you..

I think your problem may caused by tower/signal strength for your wireless card ?

---

### Post by balo1313 on 2009-09-27
I hope someone there could pls assist me. I just installed jaunty, ubuntub 9.04 version but cant get connected tru this USB modem. on plugging in the USB it tried to detect and install it but gave me option for another network in thre country and not WARID telecom Uganda. pls i need to surf with the sys, any help their?

---

### Post by baskar007 on 2009-09-28
> **balo1313 said:**
> I hope someone there could pls assist me. I just installed jaunty, ubuntub 9.04 version but cant get connected tru this USB modem. on plugging in the USB it tried to detect and install it but gave me option for another network in thre country and not WARID telecom Uganda. pls i need to surf with the sys, any help their?

you need to setup setting for your ISP manually . :popcorn:

---

### Post by Jugantor on 2009-09-28
Hi baskar007,

Can I have one more solution ? Since last night, my internet has stopped working once again!! duhh !!
](*,)

Jug

---

### Post by v2rocketboy on 2009-09-28
Ok I have the solution,

I found some documentation for what to do when the drivers that a open source, automatically take control of your wireless device. The open source drivers, just dont do the job properly for some wireless devices like my usb netgear wg111v3 device. So I followed these directions and I am now talking to you through ubuntu!

Go to:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here you will find all that is to on how to connect your device,

One tip, when it comes to using ndiswrapper, install utils, common, and the graphical interface, so that you can do either through the terminal or through graphical interface. You will also have to have your windows drivers for your networking devices.

Ndiswrapper allows you to use windows drivers in ubuntu.

Hope this works, take it slow, follow the directions and hopefully it will be good

enjoy, while I go put another shrimp on the barbie!:lolflag::)

---

### Post by baskar007 on 2009-09-29
at this time, speed of windows internet is what?
do you done optimize mtu and other setting?

---

