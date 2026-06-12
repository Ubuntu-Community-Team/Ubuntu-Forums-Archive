---
title: "Netgear WNDA 3100 v2 wireless adapter working on Ubuntu 9.10"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Green_Bean on 2010-01-17
Well after days of combing the internet and beating my head against the wall, I finally got my Netgear WNDA 3100 v2 wireless adapter working on my old Dell PC running Ubuntu 9.10 (Karmic Koala).

 I am not highly technical, and am fairly new to linux, so this was a real challenge for me, so this is a kind of "Wireless for Dummies".

 I will try to describe step by step for those other frustrated n00bs out there who are struggling with this.

 First I installed the firmware by typing into terminal:

 sudo su #
cd /tmp
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
mv ar*.fw /lib/firmware

 (you can copy that whole chunk and just paste it into terminal)
 Thanks to Tom Wright on Linux.com for that.
 [http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html](http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html)

 then I went to [http:kb.netgear.com/app/answers/detail/a_id/12115]("http://kb.netgear.com/app/answers/detail/a_id/12115")
 and downloaded that file to my desktop. (For some reason this same process with software on the cd that came with my adapter did not work the driver was “invalid”).

 I used Wine to “install” the drivers. Install Wine and make sure it is configured to Windows XP. It does not really install the drivers, but runs the install wizard like it was on windows and unpacks them into a kind of phony [C:\]("file:///C:/") drive so you can use them. Use Wine to browse that [C:\]("file:///C:/") drive and you will find a folder WNDA3100v2. Inside that folder is a folder- Driver and in that WinXP200. There you will find a file **bcmwlhigh5.inf.** That is the prize you have been looking for.

 I just dragged the whole WNDA3100v2 folder to my desktop to make it easy to find. But, as I understand it, wherever you put it you will need to leave it in place afterward (or at least the folder with the drivers in it, not sure about that) so put it somewhere where you can keep it forever.

 Then at the top of your screen, go to System/Administration/Windows Wireless Drivers (install it if you don't have it). Then click install new driver and use Windows Wireless Drivers to browse to the .inf file, click install. That's it, you should be good to go.
 
 Somewhere in this whole process, my Network Manger Applet disappeared from the panel at the top of my screen. Just in case this happens to someone else, I installed Knetwork Manager from the Ubuntu Software Center, and was then able to configure my network so I could finally get online with my wireless adapter. One last note, my router is currently unsecured, so I'm not really all the way there yet.

 It's been quite a journey, I hope my story helps someone else.

---

### Post by drew08 on 2010-02-18
Thanks for the detailed post! When I get to the following step, I'm a little confused what to do next:

> Then click install new driver and use Windows Wireless Drivers to browse to the .inf file, click install. That's it, you should be good to go.

When I go to System - Administration - Windows Wireless Drivers an error message pops up saying "Unable to see if hardware is present.". When I click okay, next to bcmwlhigh5 it says "Hardware present: Yes". I try to click "Configure Network" but nothing happens.

Where do I go from here?

---

### Post by sambo625 on 2010-06-05
is there a solution for WNDA 3100 v2 wireless adapter on Ubuntu 10.04

---

### Post by grey_1 on 2010-07-23
Thanks for the informative post Green_Bean - it did help a lot as the OS (10.04) now sees the adapter. It's also apparently working as it's detecting other networks in the area, just not mine. :)

I have the Netgear WNR3500L wireless n router and even with a basic setup I can't get the 2 to talk.

My question, is the BSSID necessary for the connection setup? 

thanks in advance!

---

### Post by NWK on 2010-08-19
I just got two of these usb dongles (wnda3100v2) On both of my computers i am running lucid 10.04 2.6-32-generic. I have tryed using this tutorial and a few others on both machines but neither seem to work. At first when i lsusb it will list the netgear, inc. After I add the driver via Ndiswrapper lsusb no longer displays anything, and when i try to open the ndiswrapper gui it goes to force close. Any updates on getting this device to work would be most appreciated.

---

### Post by Spindizy on 2010-09-11
The two firmware files are for the V1 or Atheros chipset adapters... They have no effect on the V2 or Broadcom chipset adapters... They are uneeded for this guide and do not need to be downloaded.

---

### Post by brialyn on 2010-09-14
Thanks for this. I really thought I would get there. However, after installing windows wireless drivers and trying to install  bcmwlhigh5.inf I get an error message "Invalid Driver". I must be doing something wrong. Please advise what I can check. Thanks and Regards, Brian



> **Green_Bean said:**
> Well after days of combing the internet and beating my head against the wall, I finally got my Netgear WNDA 3100 v2 wireless adapter working on my old Dell PC running Ubuntu 9.10 (Karmic Koala).

 I am not highly technical, and am fairly new to linux, so this was a real challenge for me, so this is a kind of "Wireless for Dummies".

 I will try to describe step by step for those other frustrated n00bs out there who are struggling with this.

 First I installed the firmware by typing into terminal:

 sudo su #
cd /tmp
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
mv ar*.fw /lib/firmware

 (you can copy that whole chunk and just paste it into terminal)
 Thanks to Tom Wright on Linux.com for that.
 [http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html](http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html)

 then I went to [http:kb.netgear.com/app/answers/detail/a_id/12115]("http://kb.netgear.com/app/answers/detail/a_id/12115")
 and downloaded that file to my desktop. (For some reason this same process with software on the cd that came with my adapter did not work the driver was “invalid”).

 I used Wine to “install” the drivers. Install Wine and make sure it is configured to Windows XP. It does not really install the drivers, but runs the install wizard like it was on windows and unpacks them into a kind of phony [C:\]("file:///C:/") drive so you can use them. Use Wine to browse that [C:\]("file:///C:/") drive and you will find a folder WNDA3100v2. Inside that folder is a folder- Driver and in that WinXP200. There you will find a file **bcmwlhigh5.inf.** That is the prize you have been looking for.

 I just dragged the whole WNDA3100v2 folder to my desktop to make it easy to find. But, as I understand it, wherever you put it you will need to leave it in place afterward (or at least the folder with the drivers in it, not sure about that) so put it somewhere where you can keep it forever.

 Then at the top of your screen, go to System/Administration/Windows Wireless Drivers (install it if you don't have it). Then click install new driver and use Windows Wireless Drivers to browse to the .inf file, click install. That's it, you should be good to go.
 
 Somewhere in this whole process, my Network Manger Applet disappeared from the panel at the top of my screen. Just in case this happens to someone else, I installed Knetwork Manager from the Ubuntu Software Center, and was then able to configure my network so I could finally get online with my wireless adapter. One last note, my router is currently unsecured, so I'm not really all the way there yet.

 It's been quite a journey, I hope my story helps someone else.

---

### Post by brialyn on 2010-09-14
Thank you. I responded saying that I had a response saying the .ifo file was invalid. Of course it is valid if you have the appropriate .sys file in the same place. Sorry.


> **Green_Bean said:**
> Well after days of combing the internet and beating my head against the wall, I finally got my Netgear WNDA 3100 v2 wireless adapter working on my old Dell PC running Ubuntu 9.10 (Karmic Koala).

 I am not highly technical, and am fairly new to linux, so this was a real challenge for me, so this is a kind of "Wireless for Dummies".

 I will try to describe step by step for those other frustrated n00bs out there who are struggling with this.

 First I installed the firmware by typing into terminal:

 sudo su #
cd /tmp
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
wget [http://launchpadlibrarian.net/27826554/ar9170-1.fw](http://launchpadlibrarian.net/27826554/ar9170-1.fw)
mv ar*.fw /lib/firmware

 (you can copy that whole chunk and just paste it into terminal)
 Thanks to Tom Wright on Linux.com for that.
 [http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html](http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html)

 then I went to [http:kb.netgear.com/app/answers/detail/a_id/12115]("http://kb.netgear.com/app/answers/detail/a_id/12115")
 and downloaded that file to my desktop. (For some reason this same process with software on the cd that came with my adapter did not work the driver was “invalid”).

 I used Wine to “install” the drivers. Install Wine and make sure it is configured to Windows XP. It does not really install the drivers, but runs the install wizard like it was on windows and unpacks them into a kind of phony [C:\]("file:///C:/") drive so you can use them. Use Wine to browse that [C:\]("file:///C:/") drive and you will find a folder WNDA3100v2. Inside that folder is a folder- Driver and in that WinXP200. There you will find a file **bcmwlhigh5.inf.** That is the prize you have been looking for.

 I just dragged the whole WNDA3100v2 folder to my desktop to make it easy to find. But, as I understand it, wherever you put it you will need to leave it in place afterward (or at least the folder with the drivers in it, not sure about that) so put it somewhere where you can keep it forever.

 Then at the top of your screen, go to System/Administration/Windows Wireless Drivers (install it if you don't have it). Then click install new driver and use Windows Wireless Drivers to browse to the .inf file, click install. That's it, you should be good to go.
 
 Somewhere in this whole process, my Network Manger Applet disappeared from the panel at the top of my screen. Just in case this happens to someone else, I installed Knetwork Manager from the Ubuntu Software Center, and was then able to configure my network so I could finally get online with my wireless adapter. One last note, my router is currently unsecured, so I'm not really all the way there yet.

 It's been quite a journey, I hope my story helps someone else.

---

### Post by New_Age_Ninja on 2010-11-29
2 days u have made my day good thank you Green Bean.

Part of those 2 days was working with the wrong WNDA3100 not the WNDA3100v2 *Kicking self in the NO NOs*

---

### Post by lindolo on 2010-12-02
Worked for me on Dell D420 once I remembered my wireless switch was set to disable all. I copied the WinXP2000 folder from browsing applications>wine>browse c: drive>program files>netgear>drivers into my documents folder. I installed the .inf from their. 

Thanks for the instruction.
:D

---

### Post by barcade134 on 2010-12-15
> **brialyn said:**
> Thanks for this. I really thought I would get there. However, after installing windows wireless drivers and trying to install  bcmwlhigh5.inf I get an error message "Invalid Driver". I must be doing something wrong. Please advise what I can check. Thanks and Regards, Brian

This worked up to a point for me but I had to copy the entire folder and not just the bcmwlhigh5.inf and bcmwlhigh5.sys.  Here are the files in my folder:
bcmh43xx.cat, bcmh43xx64.cat, bcmwlhigh5.inf, bcmwlhigh5.sys, bcmwlhigh564.sys.  It probably needed the *564.sys file.

What I mean is that I can get ndiswrapper to finally load the driver but that is where the fun stops.  iwconfig gives "me no wireless extensions" on both eth0 and lo.  ifconfig gives me info on my loopback lo and eth0 ethernet card no wireless.

---

### Post by kylehaas on 2010-12-17
I am also trying desperately to get my WNDA3100V2 running.
Ndiswrapper crashes when I try to load the driver, then it will not start until I completely uninstall the program and restart the computer.

Please PM me or email [email]haazenpfeffer@yahoo.com[/email] if you can help.
I really want this to work!! I've tried everything: 32-bit and 64-bit windows drivers... tons of different processes... nothing works! Please, someone, help!

---

### Post by TenPlus1 on 2010-12-18
Might help folks: [http://iheartubuntu.blogspot.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://iheartubuntu.blogspot.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)

---

### Post by kylehaas on 2010-12-18
Still not working. I've followed every guide available online, but to no avail.
Everytime I get the same error when it crashes. It does not work!!!

I've never been so dissapointed with ubuntu. I've been using it casually for years and this is outrageous.
Also, I'm on Ubuntu 10.10

---

### Post by Gamax13 on 2010-12-19
Hi,

First of all, i'm sorry for my english. :p

I reply to this thread to thanks **TenPlus1**, because his last post helped me to solve the problem.

Since  three days I was searching desperately for a way to run my WNDA3100v2 on Ubuntu 10.10, and now it works fine.

I don't know why it doesn't work with you **kylehaas, **but I hope you will solve your problem soon.

;)

---

### Post by kylehaas on 2010-12-20
Anybody have any idea why this does not work for me? I have tried every solution that has been posted on the internet and still nothing works. This is exactly what happens:

I run Windows Wireless Drivers after installing correctly. A window comes up and I click Add new driver/device. I then choose the appropriate .inf file. Immidiately, a window appears showing "MODULE COULD NOT BE LOADED, ERROR: [BLANK]"

I check and see if anything is working and it is not.
I restart the computer after completely uninstalling Windows Wireless Drivers.

After rebooting, I reinstall the Windows Wireless Drivers and run it again.
Now the .inf file is shown as installed and it says "Hardware Present: Yes".

Nothing works, even after trying the second .inf separately and both .inf at the same time.
If I try removing the .inf (which is, supposedly, installed) it will remove it from the list.
If I try adding a new .inf, the program will give me the same error as before.

:(

---

### Post by Gamax13 on 2010-12-21
Have you tried to reboot without uninstall Windows Wireless Drivers?

When  it says "Hardware Present: Yes", try to reboot.

Maybe what I say is stupid but this is what i did.

---

### Post by kylehaas on 2010-12-22
Sadly, I did exactly what you said and it still does not work.
I think I might as well give up. I've spent too much time on this.

---

### Post by walt.smith1960 on 2010-12-23
> **kylehaas said:**
> Sadly, I did exactly what you said and it still does not work.
I think I might as well give up. I've spent too much time on this.

If you're able to download Natty Narwahl (11.04) easily, it might be worth a try.  I  have 2 devices that needed non-Ubuntu files to work in 10.04 & 10.10. Both devices are recognized by 11.04's kernel without any non-Ubuntu software. 11.04 is not really ready for prime time but it seems to be more WiFi friendly.

---

### Post by w_barnes on 2011-01-01
Hi, I got my WNDA3100 working but  not very well. In windows I get a blue light and about 150Mb/s but in Ubuntu I got an orange light and max speed is 54Mb/s.

Any suggestions on how to improve performance?

TIA!

Update: I have determined that what I need to do is put the wireless adapter into 802.11n 5GHz mode. The instructions in this thread do not mention how to set the mode. Is 802.11n supported for the WNDA3100v2 in Linux?

---

### Post by GAtkins on 2011-02-04
> **TenPlus1 said:**
> Might help folks: [http://iheartubuntu.blogspot.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://iheartubuntu.blogspot.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)
 
I used a combination of this thread and the one above to get this to work.
 
What I discovered is that security needs to be set to WPA and not WPA2.
 
Glenn

---

### Post by rich_hemmings on 2011-09-10
It seems there are many threads relating to the WNDA3100v2 in the forums? And a lot of confusion RE: OS/architecture? 

Has anyone found a working solution for 11.04 64Bit? 
I've got it showing as present in Windows Wireless Devices, but wlan0 isn't enabled/present in Network Tools.
Any help is much appreciated... This worked fine on 320Bit, but I want to use all my RAM :P and would like to avoid buying a new w/less adapter if poss!! ;)

---

### Post by eli2 on 2011-09-19
> **rich_hemmings said:**
> It seems there are many threads relating to the WNDA3100v2 in the forums? And a lot of confusion RE: OS/architecture? 

Has anyone found a working solution for 11.04 64Bit? 
I've got it showing as present in Windows Wireless Devices, but wlan0 isn't enabled/present in Network Tools.
Any help is much appreciated... This worked fine on 320Bit, but I want to use all my RAM :P and would like to avoid buying a new w/less adapter if poss!! ;)

I having the same problem :(

---

### Post by kinu on 2011-10-04
> **eli2 said:**
> I having the same problem :(
Same thing here.

---

### Post by lynux77 on 2011-10-09
I think we all suffer from the same problem: Linux lacks the ability to Plug and Play, such as windows has. Most of the problem over this lies within that most of the hardware made today is made for Mac OS or Windows.  So, in turn, Linux cannot use plug and play functionality as external drivers need to be installed, and we all know that is a pain.

Native Linux drivers are rare. Most big shot companies think it is too expensive to make them, and linux users are a minority. To anyone working for those companies who is reading this, WE ARE HERE AND WE WANT NATIVE LINUX DRIVERS! So we are stuck with ndiswrapper. In my opinion, ndiswrapper is a pain to use for me. It frequently lies that the hardware is present, even though my adapter does not work. Most ndiswrapper errors go unexplained, until you look up what they mean using dmesg. The only other viable option is to go out, and buy a adapter that is compatible with linux, and tossing out your perfectly useable adapter because some company decided that no one uses linux anymore.

Sorry for the full scale rant, I'm just pissed off that companies would just shun Linux users like that. Its atrocious, and unfair. 

I suggest we all write a letter to the big companies (Netgear, Linksys, Belkin) and tell them how we really feel. I'm tired of this stupidity and want answers, not worthless excuses.

---

### Post by shinkenusa on 2012-02-17
One and all, I have spent the better part of three days sifting through all of your attempts.  The NetGear dongle is useful only to Windows.  Frustrated, I went downstairs to my box of impedimenta from years gone by, found a D-Link DWL-122 rather low speed USB wireless device, plugged it in, entered my security stuff, and viola (sic), it worked!  Immediately.  My sense is not to agree with those dissing on Ubuntu (for this sort of thing anyway).  Rather, NetGear should get out of Microsoft's pockets, get with the picture, and understand that the world is rather sick of Redmond.  Make room for the rest of us.  BTW, Mac is included with the rest of us (for the nonce) as far as I am concerned.

I suggest that the advice of others is useful:  buy something else!

Cheers.

---

### Post by Goosoid on 2012-04-18
I am using the Netgear WNDA3100v2 with Ubuntu 11.04.
 
I used ndiswrapper and installed the windows .inf file (bcmwhigh5 or something).
 
The wireless works fine except that I have to reinstall each time I reboot.
 
This might offer some help but anyone know what I have to do so it is not necessarey to reinstall driver every time I reboot?

---

### Post by marianlibrarian on 2012-04-23
These instructions are a MESS for 11.10. Nothing is where it is supposed to be. Is there anyone out there who could rewrite these instructions for 11.10???? Please? Getting desperate. I need to place this computer in a room that has no wire. Wireless is my only option. My summer reading starts in a few weeks. I really really need this to work.

As in no more SYNAPTIC!?!?!?!?!?!?

thanks in advance

---

### Post by chili555 on 2012-04-23
> **marianlibrarian said:**
> These instructions are a MESS for 11.10. Nothing is where it is supposed to be. Is there anyone out there who could rewrite these instructions for 11.10???? Please? Getting desperate. I need to place this computer in a room that has no wire. Wireless is my only option. My summer reading starts in a few weeks. I really really need this to work.

As in no more SYNAPTIC!?!?!?!?!?!?

thanks in advancePlease stick with your other thread.

---

### Post by wildmanne39 on 2013-04-02
Thread closed. Please do not post in old threads.

---

