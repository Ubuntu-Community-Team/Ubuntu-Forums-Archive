---
title: "Wirelss stops working periodically Ubuntu 10.10"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by VideoRoy on 2010-10-15
New Toshiba laptop dual booting with Windows 7.  I really like MM 10.10 and most things are working great!

Periodically I will be web browsing and I lose connection.  At first I thought it was Firefox but if I try to disconnect wireless and reconnect it will no longer connect unless I reboot.

My network is hidden but Ubuntu finds it no problem on a fresh boot and connects per my settings and it is not a network problem since I can connect to Windows all day long and the rest of the family never has problems.

My wirless device is:
Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)n

and all OS updates are applied that I can find. 

I am thinking about un-hidding my network since years ago that used to be a problem with Redhat and even early Ubuntu but beyond that I cannot think of what else to try.

It is hard to reproduce since I can work for a long time with no problems.  Any help or suggestion appreciated.

---

### Post by david.matheson on 2010-10-16
I seem to have this problem when running a BitTorrent client.  Is that your experience?

---

### Post by VideoRoy on 2010-10-16
Thanks for the reply.  

I do not run bit torrent on my laptop so that is probably not it for me.  I am not really downloading any very big either, just surfing around.

I worked on the laptop for 4 hours last night with no problems so it is very random.

---

### Post by hambai on 2010-10-17
I have the same problem - the wireless network randomly stops.

Toshiba Laptop
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
with r8192se_pci module

If I remove and load the module (r8192se_pci) it works again for a while.

Help please - it is very annoying.

---

### Post by mabarian on 2010-10-17
Me three! 

I have the same problem. Every morning I wake up to see how bittorrent client have worked during the night; always appear a message which says: 

You need to authentificate for the conection (I understand it was disconnected during the night)

And randomly, connection gets interrupted with no torretn client running. I have to disconnect the wifi antena and to connect it. It's really annoying.

I also have Maverick Meerkat installed and not necesary a torrent client working for that damned disconnection.

---

### Post by systemarpi on 2010-10-18
Same here, but as I can see, nobody is going to help, I compiled my own drivers with 10.04 but got the same result, so it does not look like a drivers problem, I will try the new released Realtek drivers and post some results later.

---

### Post by VideoRoy on 2010-10-18
Are any of you folks using a hidden wireless connection?  Just wondering if that was a common theme.

---

### Post by hambai on 2010-10-20
I use normal wireless connection both in home and at work (visible ssid, wpa2) and it drops, as I explained earlier, on random intervals.

---

### Post by comeara on 2010-10-20
I'm having the same issues with my wireless. Here's how lspci reports it:

Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

I've experienced the problem on an open wireless network at work as well as an encrypted network at home. Both networks broadcast their ssid.

Following the suggestion in an earlier post, I tried unloading the module and reloading it. That seems to be a viable workaround.

% sudo rmmod r8192se_pci
% sudo modprobe r8192se_pci

I also tried downloading the latest driver (rtl8192se_linux_2.6.0018.1013.2010) from Realtek, building and installing it. That didn't seem to fix the problem.

Distro is Xubuntu 10.10. Hardware is Lenovo ThinkPad T410.

Does anyone have a lead on getting reliable wireless?

---

### Post by z08595 on 2010-10-21
Yet another user with the same problem.  I'm running on a brand new Pangolin Performance from System76.  Everything worked well until I upgraded.  I even installed System76's repositories after I upgraded.  

My network name is broadcast and has WPA2 security.  The only way to restore the connection is to restart my computer, which is very annoying.

Edit: The problem became so persistent that I had to downgrade to 10.04.  Problems like this are completely unacceptable.

---

### Post by BigMoeW on 2010-10-21
I'll throw my two cents in as well

Running Ubuntu 10.10 64-bit on HP G62-220US
RTL8191SEvA Wireless LAN Controller
Driver - rtl819xSE 
Version - 0018.1013.2010

When I installed, it came with version 0017, wireless would connect w/o problem and then cut out after a while, unable to reconnect to wireless until a reboot.
Upgraded to version 0018 via Realtek, but problem wasn't solved
Tried switching/connecting my router in both WPA and WPA2, but no joy
Currently usb-tethered through my phone for wireless internet access

I'll try the module kill/restart method and see if that works for me

Edit: The module method allows my wireless to work for a bit, then it randomly cuts back in and out. Back to the tether for now

---

### Post by VideoRoy on 2010-10-22
Well, seems like not a lot in common except the controller itself which I would have to believe means there is something not right in the driver or 10.10 itself since there are so many implementations (IBM, Toshiba, etc.).

Also it never drops in Windows on the dual boot so probably not the hardware.

I have been lucky for the past week and have not dropped once.  Getting ready to run a major Update Manager update but nothing in there that I noticed referred to wireless network.

---

### Post by VideoRoy on 2010-10-24
I began temping fate and suspended my laptop multiple times over a couple of days and each time I woke it up it worked perfectly until today.

I tried everything again until finally the on option is to reboot and connects immediately.

Pretty frustrating and not easy to diagnose since it is so random.

---

### Post by VideoRoy on 2010-10-24
Using the laptop a lot today and the loss of wireless is worse and worse.  After a lot of searching I see some people trying WICD instead of Network Manager.  It looked promising so I installed that instead and what a disaster.

WICD could never connect to my wireless network.  I even made it un-hidden but no matter what it would always say bad password even after trying every option available.  WICD could find my network and all the other wireless networks around me but could not connect to anything with WPA.

Looks like I am going to have to give up.  Every year I try a new distribution of linux and Ubuntu and I always run into one problem that is just a non-starter and I end up spending days / weeks trying to solve.  Flaky wireless on a laptop is going to cause me to move back to Windows 100%.  Everything else about 10.10 I love which is the shame.

10.10 still runs great on my desktop machine with wired network so I will continue to use it there but with all the other reports of wireless pains in this release that I have run across it is just not ready yet in my opinion.

---

### Post by saketh321 on 2010-10-25
yeah i can add to that as well... my Qosmio F60 does the same thing... and when it is working, the signal keeps going up and down like a rollercoaster. hopefully they come out with a fix for that

Btw do any of your guys's soft keys light up on your laptops?

---

### Post by enque on 2010-10-25
I have had the very same problem since upgrading to 10.10, but it MIGHT be solved now.

**The Problem:**

Randomly dropping my wireless connection, for at least 1 minute each time. This happens at least once every half hour, but usually every 4 minutes. Network works immediately upon boot, so a reboot temporarily solves it. Same laptop dual-boots windows, and all works fine on windows so it's not a hardware problem.

**The Possible Solution:**

I opened up "Network Tools", chose the "Wireless interface" and hit "Configure". In the "Wireless network connection" I noticed a few strange things;
1. I had TWO connections instead of just one. My network is called "HomeNet" and one of them said "HomeNet" and the other said "Auto HomeNet".
2. Both of them said "last used: never".

I became suspicious, since I very clearly HAD been using that very connection just a minute ago.

So I edited their details, re-entered the password (I use WPA by the way) and clicked "Apply". Suddenly the little sign said "last used: now", and my network have worked since then without going down even once. It's been working for an hour now, so I think it might be fixed.

So I figure that the upgrade to 10.10 must've somehow PARTIALLY overwritten/replaced the old wireless network configuration, and done it in a sloppy way. I suggest doing what I did, or manually deleting your old connection and re-adding it as a new one. Might solve your problem as well.

---

### Post by VideoRoy on 2010-10-25
> **enque said:**
> I have had the very same problem since upgrading to 10.10, but it MIGHT be solved now.
 
**The Problem:**
 
Randomly dropping my wireless connection, for at least 1 minute each time. This happens at least once every half hour, but usually every 4 minutes. Network works immediately upon boot, so a reboot temporarily solves it. Same laptop dual-boots windows, and all works fine on windows so it's not a hardware problem.
 
**The Possible Solution:**
 
I opened up "Network Tools", chose the "Wireless interface" and hit "Configure". In the "Wireless network connection" I noticed a few strange things;
1. I had TWO connections instead of just one. My network is called "HomeNet" and one of them said "HomeNet" and the other said "Auto HomeNet".
2. Both of them said "last used: never".
 
I became suspicious, since I very clearly HAD been using that very connection just a minute ago.
 
So I edited their details, re-entered the password (I use WPA by the way) and clicked "Apply". Suddenly the little sign said "last used: now", and my network have worked since then without going down even once. It's been working for an hour now, so I think it might be fixed.
 
So I figure that the upgrade to 10.10 must've somehow PARTIALLY overwritten/replaced the old wireless network configuration, and done it in a sloppy way. I suggest doing what I did, or manually deleting your old connection and re-adding it as a new one. Might solve your problem as well.
 
I hope that works for you.
 
For me this was fresh install on a new laptop. I have reconfigured dozens of times and I only have one profile. I actually added a second config for the same network and it worked for a little while then eventually just loses connection and requires a reboot.

---

### Post by VideoRoy on 2010-10-25
> **saketh321 said:**
> yeah i can add to that as well... my Qosmio F60 does the same thing... and when it is working, the signal keeps going up and down like a rollercoaster. hopefully they come out with a fix for that
 
Btw do any of your guys's soft keys light up on your laptops?
 
I do not have a soft key for my wireless but I know what you are talking about since I have that on my business computer.
 
However my wireless light is on but is always on.  It is also always the same color on my particular problem laptop.

---

### Post by VideoRoy on 2010-10-26
Ok, I may have made some progress on this.
Since I just could not let it go, I completely uninstalled network manager with the purge option this time and I install WICD.  The strange thing was that it appear WICD was partial installed already and I do not think it was left over from what I tested before because I still could not connect wirelessly.

So I remove WICD with the purge option and reinstalled.  There is a bug in 1.70 that does not handle hidden SSID very well so I made my SSID visable and I connected right away!!!!

A couple of reboots and I am still connecting every time so now I need to let this run for a few days and see if I drop network connection.

If I can prove that I am no longer dropping under WICD I may purge that again and reinstall Network Manager again and see what happens.

So my question to anyone who is still following this is, while running Network Manager can you check and see if WICD has some process running as well?  That is what was definitely causing part of my problem if not all.

Good luck.
!

---

### Post by sirkeith on 2010-10-26
VideoRoy, I have a Toshiba 650 01T that gave me all kinds of problems with Lucid and Maverick. I ended up going to a newer kernel. 2.6.36 and all my problems are gone. Wireless was the main one for me as well as no USB, but those guys upstream seem to be keeping an eye on things. I bought the laptop with win 7 on it and I formatted it off the hardrive when I installed Lucid. I kicked myself a few times but now it is good. :P

---

### Post by VideoRoy on 2010-10-26
sirkeith,
That is great news!  What is the best way to move to that version of kernel?

I have compiled before but it has been a long time.

Thanks.

---

### Post by BigMoeW on 2010-10-28
Found a solution:

Installed the latest linux kernel (Download [Here]("http://www.kernel.org/") & [Compile Instructions]("http://www.howtoforge.com/kernel_compilation_ubuntu"))
Updated latest realtek driver (Download [Here]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"), Terminal into folder: sudo make, sudo make install)
Added launchpad repo for the latest Network Manager (Copy and paste "ppa:network-manager/ppa" into synaptic repository) & Updated

Wireless had been continuous for a couple of hours; will update if anything changes.

---

### Post by VideoRoy on 2010-10-29
> **BigMoeW said:**
> Found a solution:
 
Installed the latest linux kernel (Download [Here]("http://www.kernel.org/") & [Compile Instructions]("http://www.howtoforge.com/kernel_compilation_ubuntu"))
Updated latest realtek driver (Download [Here]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"), Terminal into folder: sudo make, sudo make install)
Added launchpad repo for the latest Network Manager (Copy and paste "ppa:network-manager/ppa" into synaptic repository) & Updated
 
Wireless had been continuous for a couple of hours; will update if anything changes.
 
Awesome, thanks for replying back!!  I will probably give this a try this weekend.
 
I have to say since I got WICD loaded it seems to be much more stable.  I am guessing there is still the underlying problems that the new kernel / driver might fix but I think WICD does a good job of retrying if things get dropped.  Just a guess.

---

### Post by BigMoeW on 2010-10-29
No problem, Roy. Quick update: Went to sleep last night, PC went to sleep as well, and when I/it woke back up, wireless was still connected and working perfectly.

Edit: F*ck it, it's back to its old tricks again. Don't know why I even bother.

---

### Post by faketp on 2010-11-01
> **BigMoeW said:**
> Found a solution:

Installed the latest linux kernel (Download [Here]("http://www.kernel.org/") & [Compile Instructions]("http://www.howtoforge.com/kernel_compilation_ubuntu"))
Updated latest realtek driver (Download [Here]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"), Terminal into folder: sudo make, sudo make install)
Added launchpad repo for the latest Network Manager (Copy and paste "ppa:network-manager/ppa" into synaptic repository) & Updated

Wireless had been continuous for a couple of hours; will update if anything changes.

BigMoeW, I have the same problem: wireless works fine but disconnects periodically and not reconnect anymore. The only workaround I found is reload the module (rmmod r8192se_pci; modprobe r8192se_pci) every time...

Did you find a better solution? Tks!

---

### Post by VideoRoy on 2010-11-01
Have you guys given WICD a try?  Not sure if I am just lucky or not but it seems to be working pretty well.  Since I changed to WICD from Network Manager I have not had a drop.

---

### Post by hambai on 2010-11-02
I decided to log how often the connection drops so I started a ping to a nearby server and worked as I normally do. Since the ping was running (a few days) I have not experienced any connection drops - maybe the constant packet flow from the ping helped somehow? Please try it yourself and post your results.

---

### Post by faketp on 2010-11-02
VideoRoy, I tried WICD but the wireless not connects... unsuccessful

hambai, I will try with ping running... and post the results.

PS: curiously, since I posted yesterday, my wireless keep up and fine, connected all night long...

---

### Post by omaralqady on 2010-11-02
I have the same problem on a fresh maverick install on a Fujitsu Siemens Amilo 3710 laptop, wireless:rtl8187b. This same laptop worked fine with 9.10 and 10.04. I hope someone finds a fix soon, or an update fixes this because it's very frustrating.

---

### Post by comeara on 2010-11-02
I suppose it's the coward's way out but...

I found an Intel chipset-based card on eBay and solved my wireless problems for about $20 and 10 minutes of labor to swap it out.

If you really *need* reliable wireless it might be worth replacing the card.

---

### Post by rhy7s on 2010-11-03
I've been having similar issues with wireless on an Eee PC 901. The connection will drop quite frequently [edit: using network-manager], to re-establish it I need to Fn+F2 to disable then re-enable the wireless. WICD just doesn't connect at all by itself, if I create a manual connection it will come up after a while but I have to restart when the connection drops. I've also noticed on a couple of wired 10.10 machines that I don't get a DHCP address on the wired interface, I have to manually set the IP. No problem like this in 10.04 or the last few releases.

---

### Post by enque on 2010-11-05
> **enque said:**
> I have had the very same problem since upgrading to 10.10, but it MIGHT be solved now.


Nevermind that. It is back to its old tricks again. The "solution" I first posted only lasted for a day then everything went back to being bad again. Was probably a coincidence.

I'm going to try to do the network manager trick you guys were talking about.

About the ping -> I have also noticed that the connection is much more unlikely to drop if it is continuously used. Without "being put to sleep", so to speak.

---

### Post by omaralqady on 2010-11-05
I tried the ping solution hambai and enque talked about and it's working, but I don't think this can be a final solution! Maybe this means it has something to do with inactivity or power saving?! If anyone has any ideas, please share them with us. :)

---

### Post by groovomata on 2010-11-11
Hmm, that's interesting. I get the same problem when I download with Transmission BitTorrent client which has led me to think that perhaps my provider is kicking me off when they see BitTorrent activity but no other activity.

---

### Post by omaralqady on 2010-11-11
I don't think it's provider related because the network manager icon disappears from the panel so it's a local problem, at least that's what I'm facing and what I have understood that others here are facing. The connection between the wireless interface on my laptop and the router itself is down, not my internet connection which remains functioning as normal on other connected computers.

P.S.: Try to keep a ping going on and see if the connection goes down as suggested by others here because it seems to have worked for me.
```
ping -i 10 4.2.2.2
```

---

### Post by jirwin on 2010-11-11
I've got the same problem described throughout the post.  For me, it seems I get disconnect at times when I'm pulling a lot of bandwidth, such as a torrent or streaming a video.  Not so much when I'm reading a blog or sending emails.

---

### Post by cucu007 on 2010-11-11
This is a very weird problem, not sure what the issue is with my network card when i get home. At work it connects ok to the wireless network using RADIUS authentication but at home where I have configure WPA2 the connection keeps getting disconnected from the router. All other computer at home are running wireless and they work ok. I decided to update the kernel and build a custom one to see if that would fix it but even running 2.6.36  still having the same issue. The step would be upgrading the network module for the BCM4312 from broadcom, I surely hope this can be fix. Any ideas why is the connection keeps dropping and the WPA2 key continues being asked? Thank you in advance.

---

### Post by omaralqady on 2010-11-12
@jirwin: On my computer it has nothing to do with bandwidth, because I rarely do anything other than browsing, so that's not it for me.

@cucu007: When my connection drops, the network manager icon disappears and all connections are gone until I restart, and it does not ask for the password as in your case, but since it does so with you, I think it means the network manager is still functioning, which might mean you're facing a different problem, it might be related but I'm not sure.

---

### Post by edgeskier on 2010-11-12
I've tried most of the suggestions listed here and elsewhere as the new Novatech Xplora E16 laptop I'm using is wirelessly temperamental. Wireless LAN controller is RTL8191SEvB with r8192se_pci driver. Have tried many combinations of software tweaking and weakening the wireless router and recently connected (for testing purposes only) to a nearby SSID-broadcast insecure connection, which always works first time. Realised I normally have my SSID hidden (Belking N150 router) and as soon as I made it visible (with MAC filtering and WPA2 Personal encryption), it worked for the first time in 5 days - will post again if this changes

---

### Post by VideoRoy on 2010-11-12
> **cucu007 said:**
> This is a very weird problem, not sure what the issue is with my network card when i get home. At work it connects ok to the wireless network using RADIUS authentication but at home where I have configure WPA2 the connection keeps getting disconnected from the router. All other computer at home are running wireless and they work ok. I decided to update the kernel and build a custom one to see if that would fix it but even running 2.6.36  still having the same issue. The step would be upgrading the network module for the BCM4312 from broadcom, I surely hope this can be fix. Any ideas why is the connection keeps dropping and the WPA2 key continues being asked? Thank you in advance.
@cucu007,
I started this thread as very specific to Realtek wireless not Broadcom.  As it turns out I have a HP mini with Broadcom wireless and it works flawlessly in Ubuntu 10.10.  You should post Broadcom issue in a different thread.

Thanks.

---

### Post by VideoRoy on 2010-11-12
> **edgeskier said:**
> I've tried most of the suggestions listed here and elsewhere as the new Novatech Xplora E16 laptop I'm using is wirelessly temperamental. Wireless LAN controller is RTL8191SEvB with r8192se_pci driver. Have tried many combinations of software tweaking and weakening the wireless router and recently connected (for testing purposes only) to a nearby SSID-broadcast insecure connection, which always works first time. Realised I normally have my SSID hidden (Belking N150 router) and as soon as I made it visible (with MAC filtering and WPA2 Personal encryption), it worked for the first time in 5 days - will post again if this changes
@edgeskier,
I have exactly the same setup as you.  Since I have un-hidden my SSID and switched to WICD instead of Network Manager I have not dropped a wireless connection.  I am still using WPA2 and MAC filtering so I feel pretty safe.

I am not totally convinced the problem is solved and it sure seems to be a problem with the r9182se driver, but at least in the current config I am functional.  I also use an HP Mini Laptop with Broadcom chipset and it always works never fail even with Network Manager so I am quite convinced it is the Realtek driver.

Please report back if your setup breaks after the changes you have made.

Thanks.

---

### Post by omaralqady on 2010-11-13
I don't have a hidden SSID but I do have Realtek rtl8187b, and this issue is still unsolved for me as well. I also noticed that Realtek provides drivers for Linux for some of their cards but not mine for some reason, you guys should check to see if they provide drivers for your cards, perhaps they might solve your problems.

---

### Post by johnproyal on 2010-11-13
I'm having the same problem. I fixed it somehow for a little while by uninstalling the Network Manager and installing Wicd. It was a temporary fix, and hardly that. Band-aid. I'm dualbooting Windows 7, and it seems the problems with the wireless card have moved over to that, too. I can connect via the Ethernet cable - I am right now - but it wireless isn't working in Windows 7 or Ubuntu 10.10. It isn't a problem with the router, because other wired devices are connecting (an HP Windows 7 laptop and a Windows XP desktop) without a problem.

The SSID isn't hidden, and would connect fine before tonight. In fact, it just stopped working randomly tonight.

My network controller is Realtek Semicondunctor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22). After running lspci -v in the terminal, it returns this about the network controller:

> 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8182
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 7000 [size=256]
	Memory at d2100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8180
	Kernel modules: r8187se


Any help to solve this would be vastly appreciated. Right now all I have running is Wicd to connect to the Ethernet cable.

---

### Post by jmullagh on 2010-11-13
I was able to solve this issue on my mini by simply employing the Synaptic Package Manager as follows:
 In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

---

### Post by VideoRoy on 2010-11-13
> **jmullagh said:**
> I was able to solve this issue on my mini by simply employing the Synaptic Package Manager as follows:
 In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:
I might have confused things here again.  The problem in this thread is only Realtek wireless chipset.  That is what I have on my Toshiba Laptop and a number of people here have this chipset on other brands as well.  This particular thread has nothing to do with Broadcom at all!

I also happen to have an HP Mini with a Broadcom wireless chipset that works perfectly.  The only reason I mentioned it at all is because my environment is identical in all respects between the 2 computers (Ubuntu 10.10, same wireless network, etc.)  The only difference is the wireless chipsets.

This is Realtek issue only but when I started the thread I did not realize it was only a Realtek issue because I did not have the other computer and did not realize how many other people with Realtek chipsets have exactly the same problem.

It is has got to be a Realtek driver problem.

---

### Post by fletchermoore on 2010-11-14
Recently got a Lenovo Thinkpad T410. I should have Googled for wireless issues first.

I am using RTL8191SEvB, which was called the Thinkpad b/g/n or something similar under customization options.

As soon as I got the laptop, I installed Ubuntu 10.10 fresh, and everything seemed to work great. Quickly I noticed a wireless signal strength rollercoaster. It fluctuates from 10, 60ish, to 100% strength and occasionally stops working altogether for a minute or two, even though I am not moving around.

---

### Post by VideoRoy on 2010-11-15
> **fletchermoore said:**
> Recently got a Lenovo Thinkpad T410. I should have Googled for wireless issues first.

I am using RTL8191SEvB, which was called the Thinkpad b/g/n or something similar under customization options.

As soon as I got the laptop, I installed Ubuntu 10.10 fresh, and everything seemed to work great. Quickly I noticed a wireless signal strength rollercoaster. It fluctuates from 10, 60ish, to 100% strength and occasionally stops working altogether for a minute or two, even though I am not moving around.
Sounds familiar.  Unfortunately too many of us with the same issue.

I am not dropping quite a much any more but to be honest I am spending more time on my desktop and my Mini.  It is a shame too because I specially got my laptop with the problem for using Ubuntu.

---

### Post by VideoRoy on 2010-11-15
I found an email address for tech support on the Realtek website and send them a message with my original issue and a link to this thread.  Maybe someone will respond.

I have had Realtek chipsets (wireless, wired, audio, etc) on probably every computer for the past 5 years and have never had a problem before.

---

### Post by overly_verbose on 2010-11-15
I'll echo what others have said:Same here.

I tether off my Android phone mostly and only in the past week or so have I had issues.
I have to reboot in order to re-connect. It's getting annoying. FTR I have to reboot at the coffee shop or *any*wifi network I attempt to connect to before it will connect successfully.

Lastnite I got so frustrated that I did a complete wipe/re-install *and am still having issues.*

---

### Post by VideoRoy on 2010-11-16
One of the tech support engineers from Realtek is working with me to collect my information.  Here is the information that he requested:

[FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]1.[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2][COLOR=black][COLOR=black]Which driver version do you use?[/COLOR][/COLOR][/SIZE]
   [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]2.[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2][COLOR=black][COLOR=black]Which kernel version do you use?[/COLOR][/COLOR][/SIZE]
   [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]3.[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2][COLOR=black][COLOR=black]How to connect to your AP for surfing internet? By Linux OS UI or command line?[/COLOR][/COLOR][/SIZE]
   [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]4.[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2][COLOR=black][COLOR=black]Do you have plug power adaptor with AC mode or unplug power adaptor with DC mode?[/COLOR][/COLOR][/SIZE]

Perhaps if others here post the information in this thread he can read it here as well and find something common.

Here is how to collect the info if you do not know for the items:

1. type lshw in a terminal session.  Either direct it to a text file or just scroll up until you find the wireless card and right click, copy / paste.

My output is:

  > description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.109 latency=0 multicast=yes wireless=802.11bg2. type uname -a in a terminal session and paste here the same way.

My output is:
> 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux


3. I use Gnome version 2.32.0 and Firefox 3.6.12 and I always connect to my access point via the GUI not command line.

4. I am pretty sure I loose connection either with or without AC adapter but it is hard to remember now.

Hopefully we are on track to figure this out.

---

### Post by ehoeve on 2010-11-17
Hi all,

I just bought my HP G62 yesterday comes with the Realtek Wireless.

I had the same problem that the wireless keeps dropping after a short time.

I now set up my ip address manually instead automatic. Since then it has not dropped.

Maybe I am lucky and that works for me, I'll keep you posted in case it does drop again.

Cheers

---

### Post by VideoRoy on 2010-11-18
I have been working with Realtek tech support and after reviewing my log files have told me to enable QoS (WMM) on my router which I have done.  For me it was under Applications on my Linksys and apparently was disabled by default.  I will test now and see if it makes a difference.

If this does not work I will probably go back to WICD instead of NetworkManager.  I have been using WICD since I wrote the post a couple of weeks ago and I cannot remember a dropped connection.  Once I began troubleshooting this issue again since I had some time, I reinstalled NetworkManager at Realtek's request and I dropped my connection within 5 minutes.

For me there is definitely a connection between NetworkManager regardless of what other problems I might have.  I know some have said they had problems with WICD and I did too until I did 2 things.  One was to unhide my SSID and the other was to uninstall NetworkManager like this:

sudo apt-get remove network-manager
sudo apt-get purge network-manager

The purge option is what finally allowed me to run mostly error free with WICD.  Also I disabled the Network Manager app in Startup Programs but I do not think that made a difference after purging.

Just wanted to give an update to those following the saga.

---

### Post by brokenromeo on 2010-12-11
Same here, clean 10.10 64 bit install on a Toshiba A215-S7422 with the Realtek RTL8187B...works fine for a while but any downloads of any size crash wireless networking altogether...only way to get it back is to restart the system...everything else seems to work great.

---

### Post by VideoRoy on 2010-12-18
Update

I am not completely sure this is resolved but since I made the QoS change requested by Realtek support I have not dropped a connection even after many hours of use with Network Manager.  I am guessing Realtek knows of some issue in the driver for this because I have had this router for 5 years with many friends and family using it with no problem on all sorts of network adapters.

I say not completely sure about being fixed because I made the change on my router not the laptop so as long as I am at home it is no problem but if I travel I guess I could be in trouble again unless others have set QoS on.  In those cases I would have to reboot to Windows :(

I keep checking each updates looking for a new driver but none so far.  I am not going to set this thread to resolved though.

---

### Post by d1g170s on 2010-12-19
Escribe texto o la dirección de un sitio web o [traduce un documento]("http://translate.google.com/?tr=f&hl=es").
[Cancelar]("http://translate.google.com/?tr=t&hl=es")

Escuchar

  Hi, I think I found a good solution. At least to me is working. I hope you help. It's in Spanish but is easy to see the steps.

[http://www.ubuntu-es.org/node/140154](http://www.ubuntu-es.org/node/140154)
[INDENT] > Solucion:
1) Descargar el controlador RTL8192SE desde esta pagina (realtek, por lo  que es la ultima version, no te asustes el controlador rtl8192se es el  que se usa para el dispositivo rtl8191 se)
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
 2) Descomprimes y desde consola ingresas en la carpeta y ejecutamos:
$ sudo make
$ sed -i 's/install: modules/install:/g' ./rtllib/Makefile
$ sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
$ sudo make install
 3) Tienes dos opciones reiniciar, o ejecutas
$ sudo rmmod r8192se_pci
$ sudo modprobe r8192se_pci
 4) Conectate y disfruta![/INDENT]Thanks to        [montys2]("http://www.ubuntu-es.org/user/173753") for the solution.

---------

The problems persist. Realtek publish now driver today. I'm doing a new try with the new drivers (0019.1207.2010) and, in 2 hours i did'nt have problems.

---

### Post by vduke on 2010-12-20
i was having the same problem on my HP G72. First thing i did when i purchased the machine 2 weeks ago was remove windows and put ubuntu 10.10 on the machine. Testing with the live CD before hand I did not noticing this issue. 

I took the advice from a few threads i have found to use WICD instead of the Network Manager and Presto the problem was gone. I am still with a stable connection with 0% packet loss. 

Here are the steps I took:

1. I went to the Ubuntu Software Center and did a search for WICD and install it.
2.  I opened terminal and ran the purge command to remove the network manager.
```
sudo apt-[get]("http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=get&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99") purge network-manager network-manager-gnome
```3. Went to "Applications->Internet->Wicd Network Manager" and configured my connection.

Problem was gone and still is. I cannot say i like the interface of WICD vs the Network Manager, however the stability was/is a must for my line of work. 

NO MORE HAVING TO HIT MY WIRELESS SOFTKEY TO RESTORE MY CONNECTION!!

w00t!

Hope this helps someone!

---

### Post by BigMoeW on 2010-12-21
> **vduke said:**
> i was having the same problem on my HP G72. First thing i did when i purchased the machine 2 weeks ago was remove windows and put ubuntu 10.10 on the machine. Testing with the live CD before hand I did not noticing this issue. 

I took the advice from a few threads i have found to use WICD instead of the Network Manager and Presto the problem was gone. I am still with a stable connection with 0% packet loss. 

Here are the steps I took:

1. I went to the Ubuntu Software Center and did a search for WICD and install it.
2.  I opened terminal and ran the purge command to remove the network manager.
```
sudo apt-[get]("http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=get&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99") purge network-manager network-manager-gnome
```3. Went to "Applications->Internet->Wicd Network Manager" and configured my connection.

Problem was gone and still is. I cannot say i like the interface of WICD vs the Network Manager, however the stability was/is a must for my line of work. 

NO MORE HAVING TO HIT MY WIRELESS SOFTKEY TO RESTORE MY CONNECTION!!

w00t!

Hope this helps someone!

Switched over and, believe it or not, the connection problems got WORSE for me. Switching back to NM, unfortunately. Thanks for the suggestion, though.

BTW everyone, Realtek has a new driver; Version 19.

---

### Post by vduke on 2010-12-22
I will try out that new driver. WICD does provide me a stable connection for the most part. I didn't notice any issues until today when I attempted to use transmission or any P2P network. How sad I thought i had this worked out. 

Will give a report on that new driver if it gives me any better results!

---

### Post by vduke on 2010-12-22
Perhaps some light at the end of the tunnel here. Maybe it is to soon to say, But I removed WICD and put Network Manager Back on. I updated to the new driver ver 19 and I am currently downloading a large torrent, streaming pandora, downloading new software from the software center on what appears to be an even better connection. Ver 19 may of solved our problems folks. I'll post if any problems occur but at the moment it looks like this might be the fix! Thanks for the new driver notification ;)

---

### Post by vduke on 2010-12-22
First disconnect in 2 hours since the Driver Update, Perhaps the problem isn't solved =/

Anyone else testing the new drivers with any success? I can deal with disconnects hours apart from one another if need be but obviously would rather not.

---

### Post by chrispe on 2010-12-22
Hello, I'm kind of new to this kind of stuff, but I am having the same problem as all of you on my Lenovo sl510 with the same wireless card. The only thing I have tried so far is installing the new driver which would not work without the two sed lines in d1g170s' reply and while it seems to be working somewhat better, but still drops once in a while. Has anyone else still had problems with the new driver? Also if no one has what could I be doing wrong? I might try Wicd depending on how bad it gets, but would like to get this working with network manager even if that solves it.

---

### Post by vduke on 2010-12-23
New driver definitely performs better with network manager however I went back to WICD and it performs flawlessly for me. Before I was not able to use transmission with WICD and now I can. Network Manager with the new driver seems to disconnect every 2 hours or so.

Good luck to all I'll keep trying to find a solution for Network Manager hopefully with some form of success.

---

### Post by VideoRoy on 2010-12-24
> **vduke said:**
> New driver definitely performs better with network manager however I went back to WICD and it performs flawlessly for me. Before I was not able to use transmission with WICD and now I can. Network Manager with the new driver seems to disconnect every 2 hours or so.

Good luck to all I'll keep trying to find a solution for Network Manager hopefully with some form of success.
Interesting update thanks!

BTW how did you get the driver?  Did you have to compile and install or did you find a package somewhere?

I keep checking my kernel updates to see if there is a new driver there but none so far.

---

### Post by vduke on 2010-12-27
> **VideoRoy said:**
> Interesting update thanks!

BTW how did you get the driver?  Did you have to compile and install or did you find a package somewhere?

I keep checking my kernel updates to see if there is a new driver there but none so far.


Sorry for the late response.  

You can find the driver here: [B][http://tinyurl.com/yefqho5](http://tinyurl.com/yefqho5)

[/B]I have found so far only one RARE glitch that appears to be non-related. Evidently after my search there was an issue with WCID interfering with Transmission. Sometimes it would halt firefox, chrome, or anything but itself from connecting to the internet. (although it appeared my skype was unaffected). Recent updates seemed to have fixed this as I have not experienced the issue lately. I am considering trying network manager ONCE AGAIN! to see if the recent update fixed the previous issues.

Hopefully that is the case and we are 100% done with this!

At the moment my HP G72 is working flawlessly :)  Will give network manager another shot and report back ;)

---

### Post by vduke on 2010-12-28
Went back to network manager with the new driver and so far so good! Also, I finally got a response from Realtek!!

> 
Dear Sir / Madam,

Thanks for your email.
Please find the latest RTL8191SE Linux driver source from following URL and
try again, sorry.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid)
=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true
Description: Linux driver for kernel 2.6.X
This driver source is based on PC x86 platform, not support embedded system.
Please refer to readme file within the package for installation and follow
below steps.
You should clear previous drive or inbox driver first after you install this
driver source.
The previous driver will be stored within
/lib/modules/2.6.XXX/kernel/driver/staging.
Please remove "r8192se_pci.ko" files by following command.
1. sudo su (you should input you root password after it)
2. find /lib/modules/ -name "r8192se_*.ko" -exec ls -l {} \; 
3. find /lib/modules/ -name "r8192se_*.ko" -exec rm {} \;
 
After, You could execute "find /lib/modules/ -name "r8192se_*.ko" -exec ls
-l {} \;" to confirm it's clear properly.
And then, install this driver source as below steps. Don't forget to extract
this package before you install it.
1. sudo su
2. make
3. make install
4. reboot

If you have any questions, feel free to let us know.
Thanks.

Best Regards,
Roger_Liang
Realtek Semiconductor Corp.


Hope this helps!!

---

### Post by Bucky Ball on 2011-01-07
Did anyone find a solid fix for this? My problem is slightly different but along the same lines enough to be included here. I have hunted for weeks periodically and have been following the progress on this thread on and off.

Toshiba Satellite Pro L510. Realtek RTL8191SEvB.

Connection strength goes from anywhere between 100% and 56% (its favourite number it seems) totally at random and the connection speed is woeful, regardless of signal strength. I am getting less than 1Mbps as opposed to +10 on the other three machines in the house, one wired, two wireless (my desktop uses a wireless dongle and is behind two walls and a door but still getting +10Mbps!). 

Strangely, mine's the newest machine in the house and the worst network performer. 

So, not dropping out exactly, but dropping off. I tried compiling the new driver awhile ago (I try to fix this problem now and then) but kept getting an error of some sort, can't remember what now. I am fairly Ubuntu literate so pretty sure I was doing it right.

I have tried wicd and it is *exactly* the same right down to the 56% signal strength drops (plus after suspend the connection is gone and I have to restart networking which doesn't happen with NM so wicd is in fact worse for me in this respect). It was happening before I tried wicd so it is not that causing the problem either. I have posted about this on a separate thread but no response. :(

Any suggestions would be more than welcome because this is now really starting to give me the s***s! ;)

---

### Post by vduke on 2011-01-07
I still cannot say that I have found a solid fix. My connection does not drop anymore, but the signal is not stable. Sometimes it's solid for hours and hours then sometimes it is a really odd connection. I am still on the hunt for a real solution. Anyone?

I currently went back to WCID as it is providing me a more stable connection than Network Manager but at the core of the problem is the software driver compatibility of Realtek not being supported at the moment. 

=/ cant wait until this is completely figured out.  

> **Bucky Ball said:**
> Did anyone find a solid fix for this? My problem is slightly different but along the same lines enough to be included here. I have hunted for weeks periodically and have been following the progress on this thread on and off.

Toshiba Satellite Pro L510. Realtek RTL8191SEvB.

Connection strength goes from anywhere between 100% and 56% (its favourite number it seems) totally at random and the connection speed is woeful, regardless of signal strength. I am getting less than 1Mbps as opposed to +10 on the other three machines in the house, one wired, two wireless (my desktop uses a wireless dongle and is behind two walls and a door but still getting +10Mbps!). 

Strangely, mine's the newest machine in the house and the worst network performer. 

So, not dropping out exactly, but dropping off. I tried compiling the new driver awhile ago (I try to fix this problem now and then) but kept getting an error of some sort, can't remember what now. I am fairly Ubuntu literate so pretty sure I was doing it right.

I have tried wicd and it is *exactly* the same right down to the 56% signal strength drops (plus after suspend the connection is gone and I have to restart networking which doesn't happen with NM so wicd is in fact worse for me in this respect). It was happening before I tried wicd so it is not that causing the problem either. I have posted about this on a separate thread but no response. :(

Any suggestions would be more than welcome because this is now really starting to give me the s***s! ;)

---

### Post by Bucky Ball on 2011-01-07
Thanks for that vduke. ;)

I installed the 2.6.36 kernel as someone suggested that had fixed the problem for them. It killed my wireless and my video driver! So, sticking with 2.6.35-24 for now. It will be sorted eventually I imagine.

---

### Post by Bucky Ball on 2011-01-07
Thanks for that vduke. ;)

I installed the 2.6.36 kernel as someone suggested that had fixed the problem for them. It killed my wireless and my video driver! It was going to be a dogs breakfast to sort out and now's not the right time for me. Gives me something to play with when I feel like it though. 

So, sticking with 2.6.35-24 for now. It will be sorted eventually I imagine (when hell freezes over? probably sooner).

---

### Post by VideoRoy on 2011-01-08
Hey guys, I am the original poster here and wanted to give an update.  While I have been following all the suggestions and making notes, I am still running the way I was after the last contact with Realtek.

I am still running the version 17 driver and after all the other changes I did the one change to my router (turn QoS on)  did seem to do the trick for me.  I recently upgraded my router so I will keep an eye on it from here.  I am getting 52mb/s on the other side of the house but we will see how long this works.

I know that have been a ton of updates of if you are having exactly the same problem a me with the same hardware the things that ended up working were:

1. Completely removing WICD and Network Manager with the Purge option.  Note: you will probably need a hard wire to reinstall NM later unless you know how to do it from media somehow.  It was easier for me to find a wire!
2.  Turning QoS ON in my older router (WRTG54)
3.  Reluctantly reinstalling Network Manager after talking to Realtek

One thing that I had found out during all that jumping around was there were pieces of Network Manager and WICD running at the same time before I even knew what WICD was.  I never installed it previously so this was from a fresh install.  This will definitely mess things up but the bad part is that it sort of works for a while with both running and there are no other indicators that I could find.

I see lots of problems from folks so who knows if they are all really the same but that was my experience.

Since I am now a new Netgear router, I will update here if things go south again.

---

### Post by BigMoeW on 2011-01-11
Hey Roy, I'm checking in as well. Currently running latest driver (19) and kernel (2.6.37), but still no improvement.

I know for a fact that my router is on the fritz AND that its not responsible for my pc's connection problem.

Keep on truckin', guys :)

---

### Post by emtdan on 2011-01-17
I have the same wireless RTL8191SEvB.  It works for 1-3 days usually then I have to reboot.  Sounds like the same problem the rest of you have.  Logging out does not work - only reboot.  Doesn't work on hidden or open wireless networks when it dies. I have no going to mess with a new driver since it doesn't seem to help.  Has someone posted this bug in the ubuntu bugs?

---

### Post by vduke on 2011-01-31
Per my previous post, the setup is working pretty well. The problem rarely comes into play anymore but it is still a problem. I do wish I could use network manager but not sure if I want to keep messing around with this until a solid solution presents itself.

---

### Post by VideoRoy on 2011-02-06
Well after no real problems for months, I started having the drop out problem again.  My only guess is one of the updates changed something in my setup.  I read through every update (or try to) and I have not really seen anything related but there must have been something.

I can continue to limp along I guess in hopes that Maverick 11.04 solves the problem but that means I have to boot back into Windows 7 when doing critical work on the network, yuck!

---

### Post by Bucky Ball on 2011-02-06
Maverick is 10.10. ;)

There has been an issue with it where it reports itself as 11.04. That is actually Natty Narwhal which is not due til April. This is a known bug but doesn't seem to be a problem as far as general operating system.

---

### Post by Morpheus751 on 2011-02-08
I had this issue too and tried the QoS tip listed by VideoRoy back in Nov/Dec 2010, it's been working for me ever since (been months now).
- RTL8191SEvA Wireless LAN Controller
- Linksys WRT54G router:
  Applications & Gaming > QoS >
  QoS=Enable, Bandwidth=Auto, Device Name=<make one up>, Priority=High, MAC Address=<your MAC Address>

Hope it keeps working.
Btw, ever go to "Preferences > Network Connections" and it says "Never" under "Last Used"?  I deleted the connection, re-created it from that interface and it reports the proper status now.

---

### Post by VideoRoy on 2011-02-10
> **Bucky Ball said:**
> Maverick is 10.10. ;)

There has been an issue with it where it reports itself as 11.04. That is actually Natty Narwhal which is not due til April. This is a known bug but doesn't seem to be a problem as far as general operating system.
Yep thanks Bucky.  I actually knew that but mis-typed :P

---

### Post by VideoRoy on 2011-02-10
> **Morpheus751 said:**
> I had this issue too and tried the QoS tip listed by VideoRoy back in Nov/Dec 2010, it's been working for me ever since (been months now).
- RTL8191SEvA Wireless LAN Controller
- Linksys WRT54G router:
  Applications & Gaming > QoS >
  QoS=Enable, Bandwidth=Auto, Device Name=<make one up>, Priority=High, MAC Address=<your MAC Address>

Hope it keeps working.
Btw, ever go to "Preferences > Network Connections" and it says "Never" under "Last Used"?  I deleted the connection, re-created it from that interface and it reports the proper status now.
I almost want to go back to my old faithful WRT54G but I upgraded to a Netgear higher end router for doing media streaming and multiple SSIDs.  Fantastic piece of gear and this is the only problem I am having.

My laptop was working fine on this new Netgear router for 2 months as well until one of the Ubuntu updates and I cannot figure out which one for the life of me.  Could just be coincidental.

I have to say Maverick 10.10 is the best version of Linux yet for me except this one nagging problem on this particular computer.

---

### Post by emtdan on 2011-02-19
I hate when people fix something and don't tell everyone else what they did.  Here is an update:

My computer currently has was seems to be a stable wireless connection with the RTL8191sevB card.  Here is was I did in order.

1. Downloaded and installed Wicd. 
2. Downloaded realtek drivers from the realtek site (they are a pain in the *** to find but look around the forums and the link is there if you are having trouble). 
3. I removed network manager and then purged it. 2 DIFFERENT steps.
4. Removed all native wireless drivers for realtek from my /etc/modules folder.  They were scattered about - make sure all "r8191se" drivers are gone.
5. Restarted
6. Installed realtek driver (start sequence with sudo su, then make clean, make, make install, and then modprobe r8191se)
7. Restart.
8. Open Wicd and enjoy.

So far, last 4 days this has been stable. Wireless has slowed down a couple times for a little while but I can either turn off and back on the wireless or just wait it out and it goes away. Infrequent though.

---

### Post by VideoRoy on 2011-02-21
> **VideoRoy said:**
> I almost want to go back to my old faithful WRT54G but I upgraded to a Netgear higher end router for doing media streaming and multiple SSIDs.  Fantastic piece of gear and this is the only problem I am having.

My laptop was working fine on this new Netgear router for 2 months as well until one of the Ubuntu updates and I cannot figure out which one for the life of me.  Could just be coincidental.

I have to say Maverick 10.10 is the best version of Linux yet for me except this one nagging problem on this particular computer.

Looks like it was just coincidental problem that was probably unrelated.  Been using my laptop really heavily for a few days, all weekend with lots of streaming content and still working good.

So I stick by my original update of purging both WICD and Network Manager and setting QoS on in my router then reloading Network Manager at Realtek's request although WICD was working for me.  WICD does not handle hidden SSIDs very well at all so getting back to NM has been nice in that regard.

I am still on my original driver loaded with Maverick.

---

### Post by PeMa GonGo on 2011-02-21
the problem is either a ubuntu nor a driver problem, it is related to NetworkManager. I have this issue on a Gentoo laptop happening. Only with Networkmanager, try wicd and it should work.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/361823]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173")

---

### Post by Pennoid on 2011-03-02
I'm using a Lenovo Thinkpad 410i with RTL8191SEvB, and what happens isn't really a disconnect, as much as a total slowing down to zero. Network Manager says I'm connected, but I can't transfer or receive information. If I reconnect, I get about five to ten minutes, until it slows down again, maybe twenty. I'm using Maverick 10.10 and Kernel 2.6.35-27 generic....


This is rough.

---

### Post by Jackson4christ on 2011-03-06
I'm wondering, could it have to do with your adapters power saving mode?  That Network Manager isn't correctly handling a wake up from power saving mode with certain drivers?

Does anyone know how to turn power saving mode off?

---

### Post by emtdan on 2011-04-14
Has anyone updated to Natty yet? Is the issue fixed?  I am still using WICD, but although it works, it takes a few minutes to connect on reboot.  It is also kind of buggy and there are no updates anymore... 

Are there any other Network Managers to consider using?

---

### Post by omaralqady on 2011-04-16
The only solution I have found other than using wicd, is assigning a keyboard shortcut (ctrl-shift-n) to run 'nm-applet'. It's not a 'solution', but rather a workaround, but it works :)

---

### Post by dazthejunglist on 2011-04-18
hi there just to let you know ive been having the same problem, mine goes when im streaming vids online when transmissions running or if i leave the computer on idle. 
:confused:

---

### Post by yungballla6 on 2011-05-03
Just trying to see if there was a solution to this problem. I'm running natty with a realtek card and the problem is very much here. Something needs to be done. I can't even use ububuntu anymore.

---

### Post by omaralqady on 2011-05-03
I don't have this problem since I installed natty, but I did a fresh install, not upgrade. Which did you do? It might have something to do with it.

---

### Post by aman_cc on 2011-05-04
> **VideoRoy said:**
> Looks like it was just coincidental problem that was probably unrelated. Been using my laptop really heavily for a few days, all weekend with lots of streaming content and still working good.
 
So I stick by my original update of purging both WICD and Network Manager and setting QoS on in my router then reloading Network Manager at Realtek's request although WICD was working for me. WICD does not handle hidden SSIDs very well at all so getting back to NM has been nice in that regard.
 
I am still on my original driver loaded with Maverick.
 
 
@ VideoRoy - I have the same problem. Have tried everything except for your QoS tip. I'm noob with all this stuff. So would be great if you could tell me how to do the QoS part please. 
 
 
Infact I started a thread for this myself - but didn't receive much response. [http://ubuntuforums.org/showthread.php?t=1725231](http://ubuntuforums.org/showthread.php?t=1725231)
 
Thanks

---

### Post by VideoRoy on 2011-05-04
> **aman_cc said:**
> @ VideoRoy - I have the same problem. Have tried everything except for your QoS tip. I'm noob with all this stuff. So would be great if you could tell me how to do the QoS part please. 
 
 
Infact I started a thread for this myself - but didn't receive much response. [http://ubuntuforums.org/showthread.php?t=1725231](http://ubuntuforums.org/showthread.php?t=1725231)
 
Thanks
The QoS setting will be on your router.  So to change this setting you will have to login into your router and make the change.

I have had a Linkysys and Netgear routers and have found this setting is typically under the Multimedia or Video options.  A quick google search on your router model and QoS should get you there.

As another update, I upgraded to Natty (not clean install) and I am still not having the problem any more.  I checked my driver version and remarkably I am still running the original v17 I had in Maverick.  I guess that version is the release in the current kernel.

I tend to think like a lot of others that the problem was really in Network Manager however since the Realtek guys asked me to switch back to it from WICD I am still not having problems.

Sorry I cannot help more.

---

### Post by aman_cc on 2011-05-05
> **VideoRoy said:**
> The QoS setting will be on your router. So to change this setting you will have to login into your router and make the change.
 
I have had a Linkysys and Netgear routers and have found this setting is typically under the Multimedia or Video options. A quick google search on your router model and QoS should get you there.
 
As another update, I upgraded to Natty (not clean install) and I am still not having the problem any more. I checked my driver version and remarkably I am still running the original v17 I had in Maverick. I guess that version is the release in the current kernel.
 
I tend to think like a lot of others that the problem was really in Network Manager however since the Realtek guys asked me to switch back to it from WICD I am still not having problems.
 
Sorry I cannot help more.
 
Thanks VideoRoy. QoS was already enabled for me. I still am facing the frequent freeze of the wireless. So guess this didn't help me. Nevertheless thanks very much for your response.

---

### Post by VideoRoy on 2011-05-06
> **aman_cc said:**
> Thanks VideoRoy. QoS was already enabled for me. I still am facing the frequent freeze of the wireless. So guess this didn't help me. Nevertheless thanks very much for your response.

I am still convinced one of the things that helped me was to totally remove WICD and Gnome Network Manager with the purge option then reload either one.

I noticed at one time that components of both were running at the same time even though I had not loaded both yet.  I even went into Startup Programs and made sure either WICD or Network Manager were not loading something.

---

### Post by aman_cc on 2011-05-06
> **VideoRoy said:**
> I am still convinced one of the things that helped me was to totally remove WICD and Gnome Network Manager with the purge option then reload either one.
 
I noticed at one time that components of both were running at the same time even though I had not loaded both yet. I even went into Startup Programs and made sure either WICD or Network Manager were not loading something.
 
I will try your purge option. Can you tell me how to purge WICD and Netwrok Manager please? Sorry if this is really a dumb q.

---

### Post by omaralqady on 2011-05-06
I think he means you should remove the packages for the network manager and WICD from synaptic by selecting completely remove, and then reinstall them.

*AFAIK purge from the command line does the same thing as completely remove from synaptic

---

### Post by VideoRoy on 2011-05-06
> **omaralqady said:**
> I think he means you should remove the packages for the network manager and WICD from synaptic by selecting completely remove, and then reinstall them.

*AFAIK purge from the command line does the same thing as completely remove from synaptic

Yes thanks for clarifying, either option will work.

However only install one or the other.  You might want to start with Network Manager first once you have completely remove them BOTH.

---

### Post by BigMoeW on 2011-05-14
Heh, this thread is still here? :popcorn:

Fresh installed Natty a while back and its using the Realtek driver, but version 17 instead of 19.

Haven't gone through one disconnect yet!

EDIT: ...and I see VideoRoy already has it covered, lol.

---

### Post by vduke on 2011-05-14
:popcorn: Indeed, I to also installed Natty and the problem as disappeared for me. HOWEVER I still cannot use Transmission Bit Torrent regardless how much i slow it's speed down. 

I would suggest this is essentially solved however after reading the subject again this is for Ubuntu 10.10 not 11.04.

Just a thought :)

Any ideas on the Torrent app? I have read around that a workaround is to install uTorrent in wine >.<

sigh..   were getting there! Next stop.  Netflix? lol *i feel the flame coming!*

---

### Post by BigMoeW on 2011-05-14
> **vduke said:**
> Any ideas on the Torrent app?

I've long had problems with torrents and port forwarding and the like, but this was my solution; I installed DD-WRT for my router which essentially overwrites the OS with an open source alternative (sounds familiar?). Then just use uPnP and you are good to go.

---

### Post by vduke on 2011-05-14
yeah... That sounds like fun and all.  Not sure if I am ready to potentially brick my $189 router :S .
Thanks for the suggestion though :)

---

### Post by karlm on 2011-05-14
Using 10.04LTS here, every now and then my connection seems to die for no apparent reason.

I use an ISP that allows me to log into other routers when I'm out and about in an open-exchange, so my router also puts out a public connection...

All my other machines connect including my android phone and my two daughter's smart-phones too.

Now the weird thing is, when I try to connect using a saved and working connection - it for no reason moves away from it and moves on to my free connection (the public one I broadcast, i.e. the same router and same wifi card - so it's NOT a hardware issue either on my laptop NOR on my router).

So I can connect to the very same router using the very same wifi card using windows & linux - but when I try to use my always previously working connection it doesn't want to know.

I've deleted it and got it to refind it - which it did without issue, and put my correct p/w back in and it continues to ignore it.

It's a lil on the infuriating side... 



ps - i'm currently connected via my ubuntu OS and on my public open-access connection, thus confirming there is no hardware issue.

---

### Post by omaralqady on 2011-05-14
@karlm: I think this problem is different than the one we had here, so I suggest you start a new thread for it. 

**NOTE:
If your public connection does not have a password, while the private one does, it might have something to do with that,at least that's what I guessed from what you say, it seems to be the only difference between the two connections.

---

### Post by Bucky Ball on 2011-05-15
> **omaralqady said:**
> @karlm: I think this problem is different than the one we had here, so I suggest you start a new thread for it. 



+1. This is an old thread about something else and you are buried deep. You will get more specific help and a much better chance of being noticed by posting a new thread with as much detail as possible and a descriptive thread title (this one doesn't match your issue at all). Good luck. You can post a link to the new thread here if you like. ;)

---

### Post by jonah1980 on 2011-05-17
Can everyone please report here and we may get somewhere:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758")

---

### Post by Bucky Ball on 2011-05-18
> My wirless device is:
Realtek Semiconductor Co., Ltd. **RTL8191SEvB** Wireless LAN Controller (rev 10)nThat is the very first post by the OP on this thread. Not the same wireless card your bug report link refers to, Jonah, so not really relevant (unless this card has several names).

I have emailed Realtek about the card in question and, as I posted quite awhile ago, their reply was that the drivers for it were for ***32bit systems***. There is no 64bit driver. I am surprised it doesn't work with 32bit packages installed but there you go. I still have inferior speed to the other three machines in the house and I have the newest laptop. Go figure, and Realtek, go make some 64bit drivers. ;)

---

### Post by Talin on 2011-05-30
Hi all, I realize this is an old thread but I wanted to chime in and say that I've been having pretty much the same problems.

I have a Thinkpad T400-S with the RTL8191SEvB wireless chip. As mentioned in this thread (and several other threads in this forum), it periodically just stops working. It's fairly random, sometimes it will go for a day or two, and other times it stops working after an hour or so.

Most of the time I can get the wireless to start working again by reloading the kernel module for the driver:

  sudo rmmod r8192se_pci
  sudo modprobe r8192se_pci

This works about 90% of the time - when it doesn't, the only way to fix it is to reboot. In any case, it means that I can't depend on the machine to operate unattended, since I have to manually kick the driver back to life every few hours or so.

Another thing that I find particularly frustrating is that I've gone through 4 Ubuntu releases with this problem (from Karmic through Natty) and the situation has not improved one iota. I've also updated the bios and done every other thing I can think of, with no improvement. Looking over the old threads, I get the impression that many of the users who have experienced these same problems have simply given up rather than pursuing it further.

While I'm at it, I also want to mention some other weird things about this chip. I normally use Ubuntu, but I have a dual boot setup to boot into Windows for testing purposes, and I also have an OS X machine. Both of these other OSes seem to connect much faster than my linux machine - on the order of 1-3 seconds to find the wireless signal, as opposed to 10-30 seconds under Ubuntu.

---

### Post by Bucky Ball on 2011-05-31
As I keep saying, it is the Realtek driver, not Ubuntu. Canonical can't do anything about third-party drivers.

Realtek have informed me this is a 32bit driver, as I have also mentioned. You might like to install a 32bit version of Ubuntu and give that a try if you are using 64bit. I am about to do just that during the mid-year holidays and find out for myself. ;)

---

### Post by hackwater on 2011-06-28
I've got some updated drivers from Realtek, posted on [this thread]("http://ubuntuforums.org/showthread.php?t=1267961&page=14"). Dunno if they're 64-bit, though my version of Natty is, and they compiled OK and solved my issues with the Realtek 8191se chipset. Also, the 3.0 kernel seems to have a fix as well, if the drivers don't work out for you.

---

### Post by Bucky Ball on 2011-06-28
Excellent hackwater. Which post exactly are those drivers on??? There are a long of posts on that thread. Any clues which are yours and what to try?

---

