---
title: "Wireless is unable to get the IP address"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by adam_ski on 2009-11-30
I've switched from Ubuntu 9.04 to Xubuntu 9.10 and I now cannot get the wireless network to work. I've installed my Linksys WPC54G card using ndiswrapper and that seems to work because I can see the wireless network. However, when I try to connect to the wireless network using the wicd manager, I get the error message "Connection Failed: Unable to Get IP Address". The problem remains when I try to connect using the Network Manager, although that doesn't give me an error message.

If it's any help ```
ifconfig
``` gives the following results:

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a7:fb:21  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea7:fb21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1153879 (1.1 MB)  TX bytes:141852 (141.8 KB)
          Interrupt:6 Base address:0x3800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8680 (8.6 KB)  TX bytes:8680 (8.6 KB)
```

Does anyone have any hints to overcome this problem?

Thanks.

---

### Post by teward on 2009-11-30
First thing I have to ask (because its necessary):  Is your wireless router/modem working?  Test this by powering down your router/modem for a few minutes, then turning it back on.  If this fixes it, it means your wireless was not assigning you an IP address with DHCP.

However, if this does not fix your problem, someone else might be able to help more.

---

### Post by adam_ski on 2009-11-30
I haven't rebooted the rooter, but another computer was connected wirelessly to it and therefore I hadn't considered that it could be a rooter issue. I'll reboot it, just in case.


Edit: Rooter has been rebooted and it still is not working.

---

### Post by adam_ski on 2009-12-01
It's still not working, but I've noticed that when I open up the ndiswrapper GUI I get the message *Unable to see if hardware is present.* When I select the Configure Network option in the ndiswrapper GUI I get an error that says *Could not find a network configuration tool.*

Could either of those account for the wireless not failing to find the IP address?

---

### Post by hoopsterj2 on 2009-12-01
DON'T HAVE SOLUTION. But I have a similar problem, and thought I'd post here. Last night I installed xubuntu 9.10 onto a 10 yo laptop (dell latitude CPx H500gt). I tried & failed to get wifi working w/ network manager. uninstalled it w/ gui synaptec. I installed/tried wicd. didn't work. uninstalled. am now trying wicd. It simply tries to connect for about 10 min's, then posts the same error message.  

What I don't understand is that it offers a "hidden" configuration after all this, which i was once able to see - i'm able to input the WPA 1/2 passphrase, and it has a good signal, and the correct MAC address for the AP (the router). I can't replace "hidden" with the SSID. At one point it offered to set up an ad-hoc but i've always set things up as "infrastructure". I don't know what to post to get help w/ this frankly. I'm not proficient at command line.

---

### Post by mo.reina on 2009-12-01
have you tried connecting through the command line?

you can see post #15 for instructions:

[http://ubuntuforums.org/showthread.php?t=1342574&page=2]("http://ubuntuforums.org/showthread.php?t=1342574&page=2")

you can also try a script i've written :)
[http://ubuntuforums.org/showthread.php?t=1342833]("http://ubuntuforums.org/showthread.php?t=1342833")

---

### Post by adam_ski on 2009-12-01
My wifi is now working, but I'm not sure how I got to this stage :confused:. Partly I followed the information in this [guide to wireless networking](http://wiki.linuxquestions.org/wiki/Wireless_networking), which then lead me to a [guide about WPA](http://wiki.linuxquestions.org/wiki/Wpa). However, on following some of the instructions from those guides I was getting errors, so go figure :confused:. I've not rebooted the machine since it started working, so that'll be the next test.....

Actually, what finally seemed to kick Xubuntu into life was placing an Ubuntu 9.10 liveCD into the CD drive and that threat seemed to be enough to convince Xubuntu to behave :D.

---

### Post by adam_ski on 2009-12-02
> **adam_ski said:**
> I've not rebooted the machine since it started working, so that'll be the next test.....

OK, so I rebooted the machine this morning and the wireless is again not working ](*,). When I try to connect using the wicd connection manager I get a message saying [Connection Failed: Unable to Get IP Address](http://farm3.static.flickr.com/2681/4152815994_2c201acdf8_o.png), but it then shows me connected to [an odd IP address](http://farm3.static.flickr.com/2580/4152816084_77c3b818be.jpg), which in the screenshot is 169.254.102.243 but it's also "connected" to 169.254.213.23. I can then ping that particular IP address, but I've no idea why, or where, that odd IP address is appearing. And it still means I'm not connected wireless. Arrrggghhh! 

I'd be grateful for any help you can provide. Thanks.

---

### Post by Lord_ on 2009-12-02
Have you checked whether this is working when you give your machine a static IP address? DHCP could be struggling on the router. Check whay IP address you other machine is using, give it a different one, i.e the other machine is on 192.168.1.5, so give your 192.168.1.25 and use the same subnet mask and default gateway that you are using on the working machine. At the end of the day, your probably better off with a static IP on your home network anyway.

---

### Post by adam_ski on 2009-12-02
I gave up messing around with settings I don't understand and reinstalled Xubuntu. Things are now working and, touch wood, they'll continue to behave..... During the installation process the computer automatically figured out what my wireless card was and I didn't need to use ndiswrapper, unlike when I initially installed Xubuntu.

Thanks for the various suggestions for my problem.

---

