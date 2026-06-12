---
title: "Ubuntu 9.10 on my Dell mini10v"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by JrBiem on 2010-03-02
Hello everyone. This is my first post in these forums, and I am a brand new ubuntu user (so please dont toss bricks! haha) Literally yesterday was the first time I even sat at a workstation with Ubuntu running. It intrigued me very much so I spent the next 8 hours skimming forums and doing research....the finished result is my Dell mini10v dual booting Windows 7 and Ubuntu 9.10 Then it took another hour or so to get the terminal code right for my bluetooth mouse to pair up, since it wouldn't work from the bluetooth icon.
 
Anyway, getting to my issue.. I know there are tons of posts on this topic as I have been reading them since about 10:00 this morning trying the suggestions and still no luck. Here it is:
 
My mini 10v has the dell 1510 wireless-n card. It is not being recognized when I boot to ubuntu, but it works just fine in windows. The first thing I did which seemed to be a common concensus here was to get rid of networkmanager and replace it with wicd. wicd picks up wired connections but still no go on the wireless card. I then used ndiswrapper to try and use the windows driver and still no go. My outputs for the common requested terminal commands look a little bit differently than the others I have read on here:
 
sudo ifconfig
 
[SIZE=3][FONT=Batang]eth0 Link encap:Ethernet HWaddr 00:24:e8:f2:f2:a7 [/FONT][/SIZE]
[SIZE=3][FONT=Batang]UP BROADCAST MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Batang]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Interrupt:27 Base address:0xa000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]lo Link encap:Local Loopback [/FONT][/SIZE]
[SIZE=3][FONT=Batang]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Batang]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT][/SIZE]
 
No wlan0 even shows up in my output, and if there is an easy fix to this I'll be damned because I cannot find it anywhere. It is also blank in the configuration of wicd as well. Hopefully this is a good start of information for someone to help me out, I would appreciate any helpful responses.

---

### Post by DownTown22 on 2010-03-02
My wife has a mini10v and hers came with 8.04 from Dell - which I uninstalled and replaced with 9.10 (full version not UNR - Ubuntu Netbook Remix).

To get the wireless working on hers, I kept Network Manager, plugged it straight into my router, ran all relevant updates Ubuntu wanted to run, then finally I enabled the wireless driver found in Hardware Devices (I think that's what it's called...I don't have my Ubuntu laptop handy at the moment).  This downloaded the necessary driver and I had wireless up and running after a reboot.

Hope that helps.

---

### Post by JrBiem on 2010-03-02
Thanks for the reply! I'll give that a try when I get home tonight, I'm on campus at the tech school in my area. Hopefully it works, I'm excited to learn about all the features of ubuntu but I dont even want to bother trying to get into those if I can't even make the basic functionality work.
 
 
Another thing that confuses me that I didn't mention, was that before I actually created partitions on my hard disk to dual boot the 2 OSs I booted ubuntu from a usb drive to play around a bit, and it got wireless just fine that way. :(

---

### Post by DownTown22 on 2010-03-02
You know, I've had that issue before too.  Not necessarily with the wireless, but in my case it was the graphics driver.  Everything worked fine with the live disc but once I installed I had some issues.  But, thanks to these forums, all was fixed!

Also, the driver was found here:

System > Administration > Hardware Drivers

---

### Post by JrBiem on 2010-03-02
OK so the updates are all installed and I found the driver right where you said it would be.  It's installed and functioning properly.  I ran the sudo lshw -c network command which showed the wireless is named eth2, so I opened wicd and put that into the configuration.  I can now see wireless networks, so that's awesome!

Now I am running into an issue with the network itself.  It is my home network that uses a WEP passphrase which I set up in the wireless connections in ubuntu.  It gets through the authentication fine and then gets stuck on the IP address with an error eventually coming up that says "Unable to Get IP Address"

Any suggestions there?

---

### Post by DownTown22 on 2010-03-03
Can I ask why you're using WEP and not WPA?  WPA is more secure.

I've never used wicd before, so I'm not sure if that's the problem.

A system reboot (including computer and router) never hurts either.  Logging into your router and checking all the settings are always a couple things you could try as a first pass.

---

### Post by JrBiem on 2010-03-03
I know very little about network security, WEP was the first available option in my router's menu and was very easy to set up.  All I was trying to do was keep the pesky neighbors off my network because I would get disconnected while playing WoW and a buddy told me that it was probably because people were using up my bandwidth or something.  Once I put WEP on that problem went away and it has just been the same setup for like two years now.  /shrug
 
 
Now that I'm majoring in the network specialist program at the local tech school I'm starting to care more about this stuff, so I will definatley be looking into WPA vs. WEP.  And I also have a network security class coming up next semester so I'm sure I'll learn enough to make my brain hurt. haha
 
I reset my router (erasing all previous security settings) and gave WPA a try.  Ubuntu couldnt even see any wireless networks at that point, (going to chalk that up as user error and do some research about WPA).  Anywho, with no security enabled I can connect to my home network in 7 and Ubuntu with no problems at all.  As soon as I re-enabled WEP it went back to the same issue as before, it sees the network and makes it through authentication but then hangs on obtaining IP address until it times out and gives me an error.

---

### Post by DownTown22 on 2010-03-03
Well, that's an interesting little predicament....

Have you tried reinstalling Network Manager and getting rid of wicd?

Also, is wpasupplicant installed?  Search for it in Synaptic.

*You didn't have to reboot the entire router..I just meant a power down and power back up. I Should have been more clear..my mistake.*

---

### Post by JrBiem on 2010-03-03
No worries on the router reboot, I knew what you meant, I just did it for the purpose of finding out if it worked without security enabled, and I had to reset it to do that because I couldn't remember the password. I have not tried getting rid of wicd and reinstalling network manager (was planning that for the next thing to try) and I'm not sure if wpasupplicant is installed or not either. I'm at work right now so I'll take a look when I get home tonight and try out those couple of suggestions.

---

### Post by JrBiem on 2010-03-04
Alright, awesome news!  I am officially making this post from my secure wireless network and Ubuntu running.  /sigh of relief

Now I just need to look into the more secure options than WEP.  But at least it's working :D

---

### Post by DownTown22 on 2010-03-04
> **JrBiem said:**
> Alright, awesome news!  I am officially making this post from my secure wireless network and Ubuntu running.  /sigh of relief

Now I just need to look into the more secure options than WEP.  But at least it's working :D

Good news!

What was the fix?

---

### Post by JrBiem on 2010-03-04
I uninstalled wicd, reinstalled networkmanager, installed wpasupplicant and rebooted the machine.  It noticed my network right away and asked for the key, typed it in and everything worked beautifully.  Now I am onto my next task (trying to customize grub2.

---

