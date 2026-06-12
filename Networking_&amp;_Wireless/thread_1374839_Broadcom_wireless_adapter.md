---
title: "Broadcom wireless adapter"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Supernissen on 2010-01-07
Hi, I'm using Ubuntu 9.10. It is the first time i ever use ubuntu, so treat me as a newbie :) I have a  HP Pavilion zv6000 and (from what i've got from goolge) a Broadcom Wlan-adapter. I've been trying to conntect to my wireless network at home, without any sucess. Google told me to install a driver called b43-fwcutter. It worked and I was able to detect my network but when i connect the connect the connection drops every time. I cept on googling and read about a driver callet Broadcom STA Driver. Searching for it in Synaptic and installing "bcmwl-kernel-source" but can't fin the driver in "Hardware Drivers" Can anyone help me with this? :D

---

### Post by xsist10 on 2010-01-07
Try this:

Go to System -> Administration -> Hardware Drivers

If your wireless is picked up you should see 2 potential drivers listed for your wireless.

Broadcom B43 Wireless Driver
Broadcom STA Wireless Driver

Select the STA option and click on the activate button.
You may need to restart for it to take effect.

---

### Post by unmole on 2010-01-07
+1 for STA

---

### Post by Supernissen on 2010-01-07
> **xsist10 said:**
> Try this:

Go to System -> Administration -> Hardware Drivers

If your wireless is picked up you should see 2 potential drivers listed for your wireless.

Broadcom B43 Wireless Driver
Broadcom STA Wireless Driver

Select the STA option and click on the activate button.
You may need to restart for it to take effect.

I only got the Broadcom B43 Wireless Driver, the one that were causing troubles. So i deleted it. Now i only got one called "Software modem". Is there any other package that i need to install in order to get the STA driver working?
I've restarted the computer several times, trying to install, and reinstalling it. No luck :(

---

### Post by bkratz on 2010-01-07
I think we should take a giant step backwards and verify what wireless card you have.

If you enter in the terminal

lspci | grep Wireless
(that is LSPCI in lowercase)
What displays? If nothing just try 
lspci -nn

You might want to copy/paste the output here of:

sudo lshw -C network
(LSHW in lowercase)

---

### Post by Supernissen on 2010-01-07
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Then both Broadcom STA Driver and the B43 Driver should be right?

---

### Post by bkratz on 2010-01-07
> **Supernissen said:**
> Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Then both Broadcom STA Driver and the B43 Driver should be right?



since you have the rev 03 model the correct driver is b43. Earlier models would have required b43 legacy

See section named " supported chip types" 

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

The sta driver is for other versions

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Supernissen on 2010-01-07
Okay, now i got the wireless up and running. But I'm losing the connection often and the speed i very low (1 Mbps). Is it a unstable driver or any other problem?

---

### Post by bkratz on 2010-01-07
> **Supernissen said:**
> Okay, now i got the wireless up and running. But I'm losing the connection often and the speed i very low (1 Mbps). Is it a unstable driver or any other problem?

The b43 driver should be stable. Can you post the output of

Sudo iwlist scan

?

---

### Post by Supernissen on 2010-01-07
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:03:6D:7A
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"Hemma"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004f1a3e35
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 000548656D6D61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

---

### Post by bkratz on 2010-01-07
> **Supernissen said:**
> wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:03:6D:7A
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"Hemma"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004f1a3e35
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 000548656D6D61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

Well it looks like other rates are available, (I'm getting close to my knowledge limit though) and the strength is really good, so maybe we should try to force it like in post #2 of the following:

[http://ubuntuforums.org/showthread.php?t=1363393](http://ubuntuforums.org/showthread.php?t=1363393)

You could try other available values too.

---

### Post by Supernissen on 2010-01-07
Followed your instructions without any result. The wifi is still very unstable. I tried to do a fresh install of Ubuntu 9.10 (32-bit) and it still won't work! Got the driver loaded correctly and i can connect to my router. At first the speed is at 54 Mbps and after two seconds it drops to 1 Mbps and as soon as i use the conection it disconnects. There is no problem as long as i don't use the connection. But when i open up firefox I can access google.com, but when i try to do a search the connection has already droped. And firefox just says "Looking for google.com...."
And when the connection has been down for some seconds it is like it is getting some kind of timeout and then reconnects to the router. After the reconnect i can use it to access one webpage and then the connection is gone.:(

---

### Post by bkratz on 2010-01-07
It really looks like your card doesn't like that driver, I will do some Google--ing and see what I can find.

---

### Post by Supernissen on 2010-01-07
Thanks I really appreciate it! Since I'm such a newbie i can't really understand the hits I'm getting at google. Hope you'll find something. I like Ubuntu so far, and do not want to go back for windows...

---

### Post by Supernissen on 2010-01-07
Got some news! I tested an other router and it seems to work okay. I can't test internet connection through that router, but the router configration pages are loading properly. The router i can't use is a D-link DI-524. Maybe there are some bugs with the connection to ths router? My D-link DIR-600 is working fine (at least the router configuration) :)

---

### Post by bkratz on 2010-01-07
That is great I spent the last 3 hours looking at the threads in wireless and networking, beginners, general help--finding that sometimes the rev3 works sometimes not. Some said that you had to use ndiswrapper-some not. The rev2 would be easier. Anyway since I found this stuff you have to look at it! here it is:

Ayuthia's post regarding the BCM4306 and the use of b43.
[http://ubuntuforums.org/showpost.php?p=7767008&postcount=152](http://ubuntuforums.org/showpost.php?p=7767008&postcount=152)

claim that it needs to use ndiswrapper to work reliably above 1mbs
see post #4
[http://ubuntuforums.org/showthread.php?t=1350366&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1350366&highlight=BCM4306)


posts 8-10
[http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306)

another whole thread
[http://ubuntuforums.org/showthread.php?t=1339364&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1339364&highlight=BCM4306)


Hopefully congratulations are in order

---

### Post by Supernissen on 2010-01-08
Thank you very much! I'm using my WiFi connectin right now. I switched the routers, cause my DIR-600 is working great. My DI-524 is working great with other computers, but not with ubuntu? My speed is curretly at 36 Mbps. So it is great to. Again, thank you! :)

---

### Post by bkratz on 2010-01-08
> **Supernissen said:**
> Thank you very much! I'm using my WiFi connectin right now. I switched the routers, cause my DIR-600 is working great. My DI-524 is working great with other computers, but not with ubuntu? My speed is curretly at 36 Mbps. So it is great to. Again, thank you! :)



Congratulations you did it!  I also found an interesting one last night for an open source version of the b43 which is guaranteed to work for your card. Keep this link just in case something happens>

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

Anyway, good work.  You might want to go to the thread tools and mark as [solved] in case this helps someone else.

---

### Post by flier1 on 2010-01-08
[QUOTE=bkratz;8625496]I think we should take a giant step backwards and verify what wireless card you have.

If you enter in the terminal

lspci | grep Wireless
(that is LSPCI in lowercase)
What displays? If nothing just try 
lspci -nn

Greetings! I'm a new Ubuntu (9.10) user, just installed on an HP mini 1101  and cannot connect to wireless. List for hardware drivers is blank Query (lspci | grep Wireless) for wireless card blank but query (lspci -nn) will list numerous controllers (express memory, graphics, audio, bridge, usb) but no LAN or wireless.

Help greatly appreciated, thanks all

---

### Post by bkratz on 2010-01-08
You probably should actually start a new thread, since I suspect this one to be shortly marked solved--so you may not receive the best help available. I will check back here and also look for a new thread.  Anyway,

Could you copy/paste the output you received for the second command so we can all see it?  If you really aren't getting anything showing at all--do you have wireless turned on in the bios?

---

### Post by Supernissen on 2010-01-08
Okay, I'll mark it as solved. Thanks :D

---

### Post by spigolo on 2010-02-11
> **Supernissen said:**
> Thank you very much! I'm using my WiFi connectin right now. I switched the routers, cause my DIR-600 is working great. My DI-524 is working great with other computers, but not with ubuntu? My speed is curretly at 36 Mbps. So it is great to. Again, thank you! :)

I've got a friend switching over to ubuntu with your configuration, he just called me saying his wireless didn't work.

so for what i understand, what you did to solve your problem was just using a different router???

---

### Post by bkratz on 2010-02-11
> **spigolo said:**
> I've got a friend switching over to ubuntu with your configuration, he just called me saying his wireless didn't work.

so for what i understand, what you did to solve your problem was just using a different router???



In case he is no longer monitoring the thread, I believe the only thing he resolved with the router change was the speed he was connecting at (bad English!).  Your friend needs to see what his wireless card is by going into the terminal (Applications>>Accessories>>Terminal) and entering in

lspci | grep Wireless

(that is LSPCI in lowercase- W in uppercase) or if no output just lspci

If he has the same wireless card he should see a BCM4306 rev 03 if he does he can use the thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)  and look at the threads mentioned in posting 16 of this thread.

If some other result is seen, please copy/paste or simply state what is seen back here so that someone can help you further.

---

