---
title: "Connection"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by tad214 on 2011-03-30
Hello, :)  I have a real quick question that should be rather simple for someone to answer. I am fairly new to ubuntu, so i am not smart enough to know what commands to type in to fix it. I have a Dell laptop that i just put 10.10 on. Everything went great and it boots up just fine. However, i have no internet connection. :(  When i click on the icon in the task bar, it shows that wireless is enabled and that all looks good. But, there is no connections showing up of any kind. I am sure the problem is simple to fix, i am just not smart enough to do it. So, would someone please help me get online with this laptop? Thank you so much in advance for any and all replies in advanced, and everyone have a great day. Dale :D

---

### Post by tad214 on 2011-03-30
Hello? Is there not anyone that can help me?  :(

---

### Post by ajgreeny on 2011-03-30
Please use a standard typeface; it is much easier to read than your colourful attempt to get our attention!

Try using a cable attached ethernet instead of wireless, do a full update, then try enabling available drivers in **System ->Administration ->Additional drivers**.

That is probably all that is needed, but come back again if not successful.

---

### Post by Ryan20 on 2011-03-30
[FONT=Arial]I've been keeping an eye on this thread just to see how someone manages to help out.  I'm clueless myself, but I suppose the best step would be to check out this thread to see that your card is supported and at the very least you'll be prepared with a bit more information for someone to help you out: 

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)[/FONT]

[FONT=Arial]You can open your terminal to type in the commands via clicking Applications > Accessories > Terminal or holding down Ctrl + Shift + T. 

The only other advice I can offer is to check out whether or not you have an active connection coming from your modem by plugging in the ethernet cable, opening up a web browser like Firefox or Chromium and typing in the adress bar:

[/FONT]```
[FONT=Arial]192.168.0.1[/FONT]
```[FONT=Arial]

Your user and pass should be admin / password by factory standards.

Sorry I can't be much more help as I'm still quite new to Ubuntu so I can't really give you any technical advice about the OS.
[/FONT]

---

### Post by Razorback on 2011-03-30
I assume you are planning to connect wireless.  Do you have the information about your network - i.e. name (SSID), encryption, pass key, etc.  Have you checked Network Manager (should be an icon in the upper left of your screen near time)?  You can click on it to see your network connections and set them up.

---

### Post by tad214 on 2011-03-30
**[SIZE=2]Hi.[/SIZE]**
**[SIZE=2]Well, 1st off, didnt mean to make anyone mad by using colors in my post. I sure wasnt trying to get any attention from anyone because of it. I dont think they should make things available on the forum, if they are not usable. Anyway, i thank everyone for the replies. I have done all that i know to do. It is a bcm-4306 network card. When i check my icon by the clock, as i posted earlier, it just says no connections. I have installed the the b43-fwcutter, and went and activated the driver, still, to no avail. Does anyone else have a clue what i need to do. Thanks again. Dale[/SIZE]**

---

### Post by tad214 on 2011-03-30
**Does not anybody on this forum have the knowledge to help me with this problem? I never been here and never got help. Surely, someone is on here that can help me with this ordeal. Dale**

---

### Post by tad214 on 2011-03-30
**Hi again,**
**Is there any Moderators on here? I just cannot believe this UBUNTU forum, thats supports UBUNTU, can not help me with this problem. Is there not any ubuntu specialists out there? I just need a little help, and that is all. Anyone?**

---

### Post by Razorback on 2011-03-30
Just curious, when you click on the network manager icon what exactly pops up?  I am wireless but I have a wired connection that says disconnected.  I believe I had to create a wireless connection for my home network to get wireless to work.

---

### Post by dineshs on 2011-03-31
Can you post the result of the terminal command (applications-accessories-terminal)```
sudo lshw -C network
```

---

### Post by tad214 on 2011-03-31
[B]Hi, thank you so much for the help. Here is the imfo. you asked for.                                         

dale@dale-Latitude-D600:~$ sudo lshw -C network
[sudo] password for dale: 
Sorry, try again.
[sudo] password for dale: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:de:bb:43
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5702-v2.25 ip=192.168.2.9 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fafee000-fafeffff
dale@dale-Latitude-D600:~$ 

[/B]

---

### Post by tad214 on 2011-03-31
[B]Hey Razorback,
Thanks for the reply. The only thing that is clickable, is vpn connections. The others are greyed out or whatever. That is all that it says.  Under configure, the wireless has NOTHING.  When i click on add, of course, i dont have the information needed to add one.  Thanks again. Dale[/B]

---

### Post by tad214 on 2011-03-31
[B]Hi Guys and Gals,
I was just thinking. I have had this issue once before. I believe that for some unknown reason, Ubuntu 10.10 didnt come with the correct drivers or something like that, the last time i had this problem. Because i have installed ALL the earlier versions, and they worked just fine without any problems. It is just this 10.10. What is the problem developers? I wonder if they have plans on fixing this issue before the next release? Which come to think of it, is next month i think. Anyways, i was able to get it fixed, but i dont remember exactly how. Well, maybe someone will be able to help me today. Thanks again everybody. Dale[/B]

---

### Post by Razorback on 2011-03-31
One last thing to check.  If you click on System > Preferences or Administrative (can't remember) > Network Connections does a box pop up with tabs for wired, wireless, etc.  Can you go in and setup your wireless this way.  Not sure if it will work, but I think I remember doing this to see my connection in Network Manager.

---

### Post by tad214 on 2011-03-31
[B]Hey Razor,
As i said in an earlier post, i can get that opened up, i just ant remember the info neede to set it up. Or how to et the info that it ask for. LOL[/B]

---

### Post by dineshs on 2011-04-01
> *-network:1 UNCLAIMED
description: Network controller
product: BCM4306 802.11b/g Wireless LAN ControllerI am not an expert,but from the output of lshw -c network I think there is a driver issue .Have you seen
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by tad214 on 2011-04-02
**Hey Din,**
**Thanks for the reply. I went to the link that you provided, however, i have no idea as to what to do with it. Lol. Can anyone break this down to where i could maybe understand a lil better as to what i need to do to fix this issue. I really want to get online with ubuntu. I just dont like Windows. Thanks again. Dale**

---

### Post by Razorback on 2011-04-02
OK, sounds like you need to find out the router network info.  An earlier poster (Ryan20) gave some input to finding that out.  Depending on the router, you will need to go online with it with some type of browser.  The default address is 192.168.0.1.  Type that in the address bar.  If you have not changed the default, (for linksys) the user name is admin and password in blank.  That should launch the setup pages for the router and can give you the info I think you need.

---

### Post by tad214 on 2011-04-02
**Hey Razor, **
**Thanks for the quick reply. I dont have a router. I am just trying to get this one laptop online, that is it. Dale**

---

### Post by tad214 on 2011-04-03
Well, i thought i would NEVER see the day that i would say this, but i guess there is nobody on this forum that can help me fix my problem.  I thank the ones that did attempt to help. I guess i am just going to have to go back to the dreaded windows os. Thanks again guys and gals. Dale

---

### Post by mikewhatever on 2011-04-04
The output of sudo 'lshw -C network' shows that the wireless driver is not loaded, so, since you have b43-fwcutter already installed, try loading it with the following:
```
sudo modprobe b43
```

...then post the output of 'sudo lshw -C network' again.

---

### Post by tad214 on 2011-04-10
> **mikewhatever said:**
> The output of sudo 'lshw -C network' shows that the wireless driver is not loaded, so, since you have b43-fwcutter already installed, try loading it with the following:
```
sudo modprobe b43
```
 
...then post the output of 'sudo lshw -C network' again.
 
 
Hi. How would i go by loading that b43-fwcutter? I do not know anything about networking stuff on ubuntu. Do i just use that line of code you gave me, and that will load it? Thank you so much for the help guys and gals. Dale

---

### Post by lisati on 2011-05-03
> **ajgreeny said:**
> Please use a standard typeface; it is much easier to read than your colourful attempt to get our attention!

Fixed!

---

### Post by tad214 on 2011-05-05
Hi Folks,
I just wanted to let everyone know, that the connection issue has been solved. I downloaded and installed the new version of ubuntu, and it works just fine. Apparently the other version has issues with wireless drivers. But anyway, i am up and running, and as always, ubuntu is as AWESOME as it has always been. Keep up the great work guys and gals. Thanks again for the replies and help. Dale

---

