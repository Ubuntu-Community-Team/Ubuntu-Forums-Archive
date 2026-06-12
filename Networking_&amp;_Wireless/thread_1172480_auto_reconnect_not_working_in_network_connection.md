---
title: "auto reconnect not working in network connection"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by brad_pitt on 2009-05-28
Hi,

I am using Ubuntu 8.10 - the Intrepid Ibex - released in October 2008. I have a broadband connection and i connect to internet using DSL connection as shown in the below picture:
[IMG]http://i722.photobucket.com/albums/ww228/brad_pitt1/Screenshot-EditingDSLconnection1.png[/IMG]

When internet connection gets disconnected it is not attempting to reconnect on its own instead i have to connect manually.

It is very frustrating because i am not able to download because of this :(

Regards
Brad

---

### Post by brad_pitt on 2009-05-29
guys any replies..:(

---

### Post by brad_pitt on 2009-05-30
Please help me guys..:cry:

---

### Post by pastalavista on 2009-05-30
Why is your internet being disconnected? What does it show under the "wired" tab? It should be checked auto too, I think. Also lets have a look at the PPP tab. Most DSL connections use PPPoE.

---

### Post by brad_pitt on 2009-06-21
Below are the screen shots of all the tabs

 [IMG]http://i1005.photobucket.com/albums/af171/sudhakar_karnati1/Screenshot-EditingDSLconnection1-3.png[/IMG]

[IMG]http://i1005.photobucket.com/albums/af171/sudhakar_karnati1/Screenshot-EditingDSLconnection1-1.png[/IMG]


[IMG]http://i1005.photobucket.com/albums/af171/sudhakar_karnati1/Screenshot-EditingDSLconnection1.png[/IMG]

Please help me guys..I want this network manager applet to keep trying to connect even my network connection goes down for 20 minutes..like we have redialling option in Windows..

Sorry for delay reply..

Regards
Brad

---

### Post by brad_pitt on 2009-06-21
Any suggestions guys :)

Regards
brad

---

### Post by brad_pitt on 2009-06-22
waiting for help :sad:

Regards
Brad

---

### Post by pastalavista on 2009-06-22
I really don't understand why you are having this problem. Open a terminal and enter ```
sudo lshw -c network
``` and also ```
sudo lspci | grep Ethernet
``` to determine the kind of ethernet card you're using and check System > Administration > Hardware Drivers to see if you have any drivers available for your card. Probably not since ethernet support is in the kernel for almost all network adapters. You could also try upgrading to Jaunty 9.04. Also check your router or modem to make sure auto-reconnect is enabled. Good luck with this. You could have one of those network cards that just isn't supported properly.

edit: ps, have you tried it with echo turned on?

---

### Post by brad_pitt on 2009-06-22
ram@ram-desktop:~$ sudo lshw -c network
[sudo] password for ram: 
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:e9:81:16:d0:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ram@ram-desktop:~$ sudo lspci | grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
ram@ram-desktop:~$

Above is the out put of running the commands told by you..

> ps, have you tried it with echo turned on?

Could you please explain.i could not understand what you were saying?


Thanks a ton for reply..You are only my hope

Regards
Brad

---

### Post by pastalavista on 2009-06-22
> **brad_pitt said:**
> ram@ram-desktop:~$ sudo lshw -c network
[sudo] password for ram: 
  *-[COLOR="Red"]network DISABLED[/COLOR]      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:e9:81:16:d0:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ram@ram-desktop:~$ sudo lspci | grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
ram@ram-desktop:~$

Above is the out put of running the commands told by you..



Could you please explain.i could not understand what you were saying?


Thanks a ton for reply..You are only my hope

Regards
Brad

I was saying, in the picture of your PPP config applet, at the bottom, the word 'Echo'... the box below it is not checked. Have you tried to see if it works with the box checked?

also, your network is disabled... do you know why? Try right-clicking the network-manager icon in the notification area and check, uncheck and check again the "enable networking" box... make sure it is checked when you try to connect.

---

### Post by brad_pitt on 2009-07-05
> **pastalavista said:**
> I was saying, in the picture of your PPP config applet, at the bottom, the word 'Echo'... the box below it is not checked. Have you tried to see if it works with the box checked?

also, your network is disabled... do you know why? Try right-clicking the network-manager icon in the notification area and check, uncheck and check again the "enable networking" box... make sure it is checked when you try to connect.

pastalavista,

I have tried what you said but still it is not working.
I have upgraded my OS to ubuntu 9.04.
I think we should have a feature like in windows(redialling)

Thanks
Brad

---

### Post by alphageek89 on 2009-07-11
i am facing the same problem.I'm using Jaunty and using a dsl connection.

---

### Post by ZhuaSD on 2009-07-22
I have this problem too.  Really not sure what to do next.

---

