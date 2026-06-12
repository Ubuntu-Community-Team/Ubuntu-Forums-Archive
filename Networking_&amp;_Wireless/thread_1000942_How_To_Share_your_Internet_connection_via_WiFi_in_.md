---
title: "How To: Share your Internet connection via WiFi in Intrepid"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by elyase on 2008-12-03
I never got working methods based on Firestarter or iptables, dont know why, but I think this is the easiest and probably the Gnome´s intended way of getting the job done. As you probably know Fedora 10 brings the new [[COLOR="Navy"]ConnectionSharing[/COLOR]]("https://fedoraproject.org/wiki/Features/ConnectionSharing") feature. I was wondering why this doesn't work in Ubuntu Intrepid, even when nm-applet has a similar "Shared Connection" option. So here is the answer:
First and most important thing:
```
sudo apt-get install dnsmasq-base
```
(you dont have to do this in Fedora, lets hope in the next Ubuntu Jaunty we wont have to either).

Then left-click on the Network Manager Applet-> Create new wireless connection, put a name "xxxx", click on "Create" button, wait some seconds and if everything goes well, it will display a message like "Now you are connected to xxxx wireless Network". Thats all!! Now your wireless devices (friends/second laptop, Iphone, Ipod Touch,...) will be able to see and connect to your Internet connection.

There are also video instructions of the second part [[COLOR="Navy"]here[/COLOR]]("http://www.redhatmagazine.com/2008/10/16/video-fedora-10-connection-sharing/").
Bye

---

### Post by tamman2000 on 2008-12-14
I would absolutely love it if this worked!

I was just in a hotel for a week that had one cat5 port, and my wife and I had to keep trading off.  It occurred to me (of course, after we left) that I should be able to share the connection from my Intrepid system to her mac...  But in the testing of this that I just did (of the method described in this post), I can't see, from my other laptop, the networks I have tried to create...

Has anyone tried this out?  Any ideas why it isn't working on my set up?

---

### Post by Reiger on 2008-12-14
Probably this bit might have something to do with it (emphasis added by me):
> 
Connection sharing allows to easily set up an ad-hoc wifi network on a machine **with a network connection and a spare wireless card**. If the machine has primary network connection (wired, 3G, **second wireless card**), routing is set up so that devices connected to the ad-hoc wifi network can share the connection to the outside network. (From the page OP linked to.)

---

### Post by Lusse on 2008-12-27
Help!

I have installed dnsmasq-base (and dnsmasq by the way) and this just wont work, have tried this on two different computers (HP 2710p and HP nx6110) and they have both diffrent wireless-cards (Intel and Broadcom). The network won't start and the other computer can't connect to it, please help...

//Linus Unnebäck

---

### Post by caue.rego on 2009-01-07
Worked wonders on my intrepid. Thank you very much! :)

---

### Post by rockin_goliath on 2009-01-18
Also got it working on intrepid. My girlfriend is even able to connect with her mac! dnsmasq-base should really be installed by default for Jaunty!

---

### Post by tamman2000 on 2009-01-18
Goliath,

Did you do anything other than what was described in this thread?  I wonder why this works for some people and not for others...

---

### Post by caue.rego on 2009-01-19
> **tamman2000 said:**
> Goliath,

Did you do anything other than what was described in this thread?  I wonder why this works for some people and not for others...
I'd guess NM 0.7 and dnsmasq is all you need. I did nothing but apt-get dnsmasq, and probably so did Goliath.

---

### Post by cooco on 2009-01-20
I tried to share internet from thinkpad t61 to thinkpad x31 and it didn't work. When i tried it the other way around, it worked just fine. Does anybody know where the problem is? Both same ubuntu intrepid.

---

### Post by rockin_goliath on 2009-01-21
Yup, installing dnsmasq-base was all I did. Oh, I also restarted the computer too.

It might be a question of drivers. Some cards might not be able to do it yet. As I remember, Intrepid isn't even using Network Manager 0.7, just cvs snapshots of it.

---

### Post by bgerlich on 2009-01-21
Some cards just don't have a working AP mode on linux, plus madwifi driver probably won't work with that solution, because it uses it's own interface for setting wireless modes...

EDIT:

Well in case of most cards ad-hoc mode should work, haven't thought about that ...

---

### Post by caue.rego on 2009-01-21
I haven't even restarted my notebook. :)

And I don't think it's a question of drivers at all, but I couldn't pinpoint what it might be right now.

As for NM 0.7, well, I'm using the one that came with intrepid, and it says 0.7.0 on the about box.

---

### Post by tednumber8 on 2009-01-21
Will this now be used in conjunction with firestarter or is it not needed and some other firewall used?

---

### Post by tednumber8 on 2009-02-03
This worked for me the other day but I had to reinstall ubuntu... now it wont work again... hmmm

---

### Post by subzero.amir on 2009-02-05
> **elyase said:**
> I never got working methods based on Firestarter or iptables, dont know why, but I think this is the easiest and probably the Gnome´s intended way of getting the job done. As you probably know Fedora 10 brings the new [[COLOR="Navy"]ConnectionSharing[/COLOR]]("https://fedoraproject.org/wiki/Features/ConnectionSharing") feature. I was wondering why this doesn't work in Ubuntu Intrepid, even when nm-applet has a similar "Shared Connection" option. So here is the answer:
First and most important thing:
```
sudo apt-get install dnsmasq-base
```
(you dont have to do this in Fedora, lets hope in the next Ubuntu Jaunty we wont have to either).

Then left-click on the Network Manager Applet-> Create new wireless connection, put a name "xxxx", click on "Create" button, wait some seconds and if everything goes well, it will display a message like "Now you are connected to xxxx wireless Network". Thats all!! Now your wireless devices (friends/second laptop, Iphone, Ipod Touch,...) will be able to see and connect to your Internet connection.

There are also video instructions of the second part [[COLOR="Navy"]here[/COLOR]]("http://www.redhatmagazine.com/2008/10/16/video-fedora-10-connection-sharing/").
Bye

Yes... it works... on the first try!!! Simple yet Robust.. Thank you. Have been looking for ways to share my 3G connection.

---

### Post by tusharmax on 2009-02-06
yuppie. working like a charm!!! for broadcom corporation 4312 802.11 a/b/g.

thanks mate!

---

### Post by acat on 2009-02-08
i am new to ubuntu and i had installed intrepid on my dell d410 laptop. searched high and low for this and even had to reinstalled ubuntu because i got some instructions mix up. well some very complicated instructions mixed up.

anyways i tried this and it worked like a charm.

thanks.

---

### Post by subzero.amir on 2009-02-08
Hi Elyase, is there anyway we can control the connection from the client computer?
I use my old laptop as the host for my 3G connection. I use my Acer as the client. If I am done with browsing, I would like to be able to turn of the 3G connection from my Acer.

Thks.

---

### Post by sxcmandan on 2009-02-12
Hi,
- I connect to the internet through wlan0 on my laptop.
- My aim is to share this internet connection to my ps3 via ethernet.
- on windows this was as easy as checking the 'share internet connection' box.
-This ethernet connection is to my ps3, however this should not matter as it did not in windows xp.
-My question is...How do i achieve this in ubuntu (intrepid)?

im new here by the way :)

---

### Post by priegog on 2009-04-05
First off, thanks a bunch to elyase, because this worked perfectly. I am using an atheros wifi card, for those interested in the reasons this doesn't seem to work for some people. 
Secondly, people, jaunty is coming in a couple of weeks, and with the new kernel, chances are a lot of the cards that don't work right now will then. Also, there's a newer version of network manager on there too.

---

### Post by NorQue on 2009-04-07
Is there a way to choose a custom IP range with this method?

Because I can easily connect to my Notebook with my Nokia 9300i via WLAN, but I can't with my Nintendo DS. It always throws an [Error Code: 51099](http://www.nintendo.com/consumer/wfc/en_na/ds/results.jsp?error_code=51099&system=DS&locale=en_US), for which one of the possible problems is "*Your router may not be assigning an IP address to the Nintendo DS.*". Now, I tried setting one manually, but any IP from the IP range 10.42.43.0 gets rejected as invalid when I try to save that setting.

---

### Post by priegog on 2009-04-07
NDS's are very tricky little machines. They don't work with some brands of routers just because. And that reason has nothing to do with the routers not having a dhcp server; and this internet connection sharing is not the exception. The blame should fall on nintendo, but a more realistic approach would be to file a bug report for network-manager. Or search if there isn't one already. But reast assure, your devices ARE getting an IP address assigned. Otherwise, NOTHING would work.

---

### Post by NorQue on 2009-04-07
Problem was, I thought the DS couldn't handle that Address range (well, at least 10.*.*.* looked a bit suspicious to me). After further testing it looks like that "strange" (to me) range really isn't the culprit. Damn.

Stupid thing can't WPA encrypt and I haven't played online for two years now... so, of course when I stumbled over this thread a few days ago I heard a choir singing "Hallelujah". It really would've been to good to be true if that method really worked for DS. :(

---

### Post by ishwar on 2009-04-19
Hi , 
i have been tying to do this but its now working.. 
my config: ubuntu desktop gets the intenet from a lan cable.. which is connected to a wired router.

i bought a new usb - wifi adapter (EMTECG) which works perfectly on ubuntu - got recognized as soon as i pluggd it in. :)

i installed dnsmasq - base

and created a new network 

its seen on the list of wirless networks on both computers (ubuntu as well as my other laptops xp and macbook)

but when i connect my other computers they are not getting any ip's asingned ..

dont know why !! is there any additional setting i need to do! :(
any help will be of great use.. its been long time since i rested :(!!

cheers

---

### Post by priegog on 2009-04-19
Ok, lets see. Did you create it using click on icon > Create new wireless network wizard? 
If you did, to troubleshoot first create a connection without encryption to see if the simplest thing works. Also, make sure the computers you want to connect to it don't have a static IP address assigned beforehand. I know I've made the mistake of setting a static IP address and then forget about it, only to have it give me problems when I try to connect it to something other than my home network.
And lastly, bear in mind that using this method you will only be able to connect ONE other computer to the internet... but if you get THAT working, you can later share the internet from that second computer to the third one using an ethernet cable.

---

### Post by ishwar on 2009-04-19
Hi, thanx for the reply

Yes i did create using simple non-encripted network!! 

my ifconfig wlan0 output :
wlan0     Link encap:Ethernet  HWaddr 00:0*:2*:f*:c*:26  
          inet6 addr: fe80::20e:2eff:fef4:cd26/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1368 (1.3 KB)  TX bytes:19260 (19.2 KB)
my primary internet to ubuntu is from a LAN cable - which comes from the router.. 
ifconfig eth0:

eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:**  
          inet addr:192.168.123.115  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe13:5e28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103567811 (103.5 MB)  TX bytes:4632487 (4.6 MB)
          Interrupt:11 Base address:0x8c00 
if u need more info i can provide u !! thanx a lot for a quick reply

cheers

---

### Post by omelette on 2009-04-20
I'm also struggling with this.  2 newly-installed & fully updated Ubuntu Intrepid boxes, 'dnsmasq-base' installed on both, one successfully connected to the internet via a mobile-broadband connection, (huawei E160G)  but when I 'Create a new Wireless Network' I get no 'Connection Established...' message like you see in the Fedora video that was linked-to, just a 30sec or so 'connecting' before it times out.  It is also not self-evident (to me!) why creating a new Wireless connection like this will allow your internet connection to be shared anyway, when NM 0.7  has no specific internet-sharing GUI options available like in Windows - how does the new connection know what your internet connection is?

---

### Post by priegog on 2009-04-20
> **omelette said:**
> how does the new connection know what your internet connection is?
Can't help you with your problem, but I can explain a little about this. 
dnsmasq-base is precisely the package that allows a subnet for which the computer is the dhcp server to make dns requests through its internet connection (whatever that is). As for how does it know what the internet connection is... I'm no expert in network routings in linux, but I'd adventure to say that the same way any other application knows where to send the internet info, a sort of system-wide internet gateway if you will. Does it make any sense to you?

---

### Post by omelette on 2009-04-20
It helps a little.  Unfortunately, most of us have been weaned on M$, so the lack of an intuitive way of sharing an internet connection is utterly bewildering!  Microsofts offerings are pigs as well but at least I have never failed in at least getting working shared-internet over a **wired** connection - having just tried, (in desperation!) something else I have just failed in achieving with Ubuntu!!! - with Windows, set aa few IP addresses, stick in the cable, and it works, why does Linux insist on making everything so damn difficult...

For the record, I can only get an 'established' connection when the Wired connection is configured as "Link-local only" or "Shared to other computers", and despite installing Firestarter (as others recommend) to easily configure stuff, internet-sharing just will not work!  Nothing should be this hard.....

---

### Post by priegog on 2009-04-20
Wait, so you've been trying to do this via the ethernet cables? That is a different story, and you wouldn't have to do it via the "create new WIRELESS network". And about the cable, how on earth did you get them to work under windows? As far as I know, only macs have the special ethernet cards that automatically recognize if connected to another computer, and invert the cable (for normal computer with normal cards, you'd haev to use a crossover ethernet cable). Well, I guess there must be some computers that have these special cards too. But if that doesn't work using the "shared with other computers" setting, I'd say that's the cause. 
But for wireless it should work, altho I've heard it depends on the wireless card you have (and by it's support by the Linux Kernel). So if that doesn't work, it's bad luck. If your 2 computers are not the same model, try using the other computer to do the saharing. Maybe you'll get lucky and that card will work.

---

### Post by omelette on 2009-04-21
The wired-cable attempt was an act of desperation :)  And yes, it works fine between my Dell XPS and two much older desktop computers.  The difference between 'ordinary' network cables and cross-over cables I learned about the hard-way yonks ago and actually made a cross-over cable then - so I have both - and I was just as surprised when I discovered that the XPS worked fine with the unmodified one!

As I'm determined to get this working, lots more experimentation has been done.  First, to prove to myself that I wasn't totally inept, I got a Win2k<->Ubuntu combo working fine with both wired and wireless connections (took about 30 min!)  Unfortunately, I (still) cannot get a working encrypted wireless connection - never could between 2 Windows boxes either, for unknown reasons.  I then upgraded both PC's to NetworkManager 0.7.1 (non-trivial and time-consuming that, and the applet remains 0.7.0 - is this right?) and thought I had it cracked when the laptop then started coming up "connection established..." when a New Connection was first made!  Unfortunately neither of my desktops return the favour, and I'm beginning to think it may be 'cos both have identical D-Link wireless cards...  They do detect that the laptop has created a network but fail to make a connection.  So a little progress...

And like I said, the D-Link cards work fine, at least when Win2k was doing the internet-sharing for Ubuntu.  I'll see if the opposite works after a six-pack or three :)  Gotta say though, it's dissappointing so see something as 'old' as Win2k managing this easily, while Ubuntu runs away shrieking...

---

### Post by priegog on 2009-04-22
Firstly, yeah, nm showing 0.7.0 while being in fact 0.7.1 is a known bug, so don't worry, as long as "apt-cache policy network-manager" shows 0.7.1.
Secondly... ok let me tell you which settings I'd use if I wanted to share via a cable... and then we'll talk about the wireless.
Right click on applet > edit connections. On the "wired" tab, click Add. Click on "IPv4 settings" tab, and under method, select "shared to other computers". Apply, and close. This computer will be the server, while the other has to remain the client. As such, when you plugin the cable between the 2 (have you tried a crossover cable, just to troubleshoot?), you need to select on the server computer the connection you just created, and on the client computer the connection "Auto eth0". If this is how you've done it, then I wouldn't know what else to do.
As for the wireless... The fact that not even super-compatible-Windows was able to create a cyphered connection between them should tell you something about the capabilities of those cards... But tomorrow is the release of Jaunty, and with it a new version of the kernel, so MAYBE those issues will be solved?

---

### Post by priegog on 2009-04-22
Ugh. Guys, please report this guy as spam so that the mods will get to him.

---

### Post by omelette on 2009-04-22
Thanks for that, wasn't at all sure how to check what I had installed.  Hmmmm, no mention of '0.7.1' though, just re-installed it again, everything seems to go ok, or at least there's no mention of fatal errors or anything!

> network-manager:
  Installed: 0.7~~svn20081018t105859-0ubuntu1.8.10.2
  Candidate: 0.7~~svn20081018t105859-0ubuntu1.8.10.2
  Version table:
 *** 0.7~~svn20081018t105859-0ubuntu1.8.10.2 0
        500 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
        100 /var/lib/dpkg/status
     0.7~~svn20081018t105859-0ubuntu1 0
        500 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages


Right now, I have Ubuntu on the Dell laptop internet-sharing to the Win2k box, no problem at all, so Ubuntu obviously 'works' as well!  btw, it's the Dell that gives me the "connection established..." when I create a new wireless network - it auto-configures the settings as "Shared to other computers" which just confirms what you said - this ability to find the newly-created network seems to be the critical step, as neither of the desktops (with D-Link cards) manage this...

As for the wired-connection - btw, thanks for the "Shared to other computers" explanation - well, I have just got two Ubuntu installs working with wired internet-sharing for the first time!!!  And it also works with both the normal-network cable and the cross-over cable.  What's interesting is that it didn't work first-time, there was a fair bit of cable-swapping involved, but it first connected with the cross-over cable, internet-sharing and all.  Removing the cable and using the normal cable, everything continued to work!  Obviously the Dell laptop is doing something clever to differentiate what kind of cable is being used - but this could also be adding to the confusion!

Getting there!... :D

---

### Post by priegog on 2009-04-22
> **omelette said:**
> when I create a new wireless network - it auto-configures the settings as "Shared to other computers" which just confirms what you said - this ability to find the newly-created network seems to be the critical step, as neither of the desktops (with D-Link cards) manage this...

All right, I'm super glad you got the wired sharing working. You also said you got an ubuntu computer sharing to a windows one via wireless. So from what I gather (because at this point I'm not even sure how many computers you have, and what still doesn't work) you have yet to get the ubuntu computer (presumably the same one that is sharing to windows) to share to another ubuntu computer (if I'm wrong let me know). So in essence, you need to keep in mind the same server-client model that is true for the wired connection sharing, but with a difference: 
On the server, when you create the connection (or select it from the drop-down menu) it will show "connection established" when it is READY and setup for a client to connect; it doesn't mean there is actually a connection established yet. At this point, you need to go to your client computer (whatever it's OS may be) and look for that network in the drop-down menu (in ubuntu)p and select it in order to connect.
Is this how you've been trying to do it?

Also, remember that you can only connect ONE client to ONE server at the same time.

---

### Post by omelette on 2009-04-23
Yeah, sorry for the confusion - 3 'puters in all, better too many than too few! :)

Well, I've given up on the wireless with Intrepid, got Jaunty on d/l so let's see if that's any better.  Tried every Madwifi D-link (DWL-G520) driver I could find without success, only to discover that Ubuntu's drivers are sourced from the same code!  Thing is, I know that this D-Link card works with Linux, DSL Linux specifically, so it's almost certainly NetworkManager that is the problem!  There are also some hum-dinger bugs in the very latest release (0.7.1) - for instance, with the mobile broadband connection open, I am unable to get the wired connection to complete - shut down the mobile-broadband connection and re-connecting is not a problem!  Or better(!) yet, when you set up a wired shared-internet connection, once the connection is established, the 'client' side is then unable to run any program, or even open a window - Ubuntu tries but fails, and without issuing any error message!  Close the connection or remove the cable and you are then able to run progs again.  Initially I thought it was machine-specific, but not so, as two pc's do exactly the same thing.  After seeing that, whatever confidence I had in Network Manager evaporated, as did my resolve to continue.

How can bugs like this still exist on something that is touted as a premier Linux app?

---

### Post by JK3mp on 2009-04-23
Very interesting you would think it would be easier and capable in ubuntu if fedora is shooting it out there.

---

### Post by omelette on 2009-04-23
It's a long time since I 'played' with Fedora (Core 1, if memory serves) but I recall it was definitely a much better experience than my slightly earlier Suse-Linux experience - and I actually payed for that package :D  Still not a good enough reason to make the change from Windows though, not until Ubuntu, and that was only 7-8 months ago!  With Wine coming along in leaps and bounds (imo) I am very happy working exclusively with Ubuntu, but might jump-ship for the latest Fedora if I thought they had the internet-sharing thing sorted out...

---

### Post by priegog on 2009-04-24
I think you have very slim chances of Fedora working if Ubuntu doesn't, since after all all the upstream packages come from the same place (the kernel and network-manager). but you can always try... It is a shame such weird bugs seem to appear to you... have you looked in launchpad to see if someone already submitted them? If they have, subscribe to them, and if they haven't submit one yourself... That's the only way Linux can move forward... Because after all, how can they solve a bug with some specific hardware if noone tells them there is a problem?

---

### Post by omelette on 2009-04-24
Yep, good points, I'm just not that familar with how to report bugs.

But GOOD NEWS!!!  This is being composed from the laptop in another part of the house, and over a WEP-encrypted wireless connection courtesy of Jaunty!!!  After installing Jaunty on two computers, the first thing I noticed was that the D-Link machine's problem with creating a new connection had disappeared!  Unfortunately, despite being connected and messing for hours, I was unable to get internet-sharing working.  Until I completely removed the Firestarter firewall - then everything started working perfectly, even when I restart the PC's!  The reason for removing Firestarter was that it became obvious that even with the default settings, whenever the firewall function was enabled, I could no longer surf the internet, even though I had a direct connection!  Given that Firestarter has a specific button that can immediately block all internet access when selected, cutting the feed under normal circumstances should never occur - so either this is some incompatibility between Jaunty and Firestarter, or it's just a flaky app...

While I definitely will have to get some type of firewall installed, right now I'm just happy to enjoy the secure-wireless experience :D

---

### Post by priegog on 2009-04-24
But firestarter is not a firewall in and on itself; it is just an interface to configure the firewall. So don't worry about installing it. Rest assure you are currently using a system firewall automatically setup and configured by ubuntu (I believe it's called ufw, THAT should be installed). So you're covered there. 
I suspect firestarter might have been the problem since Intrepid, but it doesn't matter now, does it?
Congratulations!

---

### Post by omelette on 2009-04-24
Cool, that's even better, and something else I didn't know!

I'm beginning to think it could indeed have contributed mightily to my problems, but I'm not about to re-install Intrepid to find out! :)  Just need to back-up my 'working-system' to DVD now, just in case I break it again!

Thanks for all your help. :)

---

### Post by dnordberg on 2009-06-10
> sudo apt-get install dnsmasq-base

So i've done this and managed to connect to the network using my iphone but i still cant access the internet. Using the iphone terminal and pinging the computers ip simply brings up "No route to host" and "Host is down".

Any ideas?

---

### Post by TwoD on 2010-07-14
I've got a desktop computer running Ubuntu 10.04 and a netbook which (for now) runs Win XP. The desktop has two Ethernet ports, one (eth0) connected directly to ADSL modem (router had died) and an internal WLAN card which I wanted to use as an access point for the netbook. I followed Elyase's steps from #1 exactly, except for installing just dnsmasq instead of dnsmasq-base and all seemed well, the new WLAN connection just took a while to show up on the netbook.

However, when I tried to connect with the netbook, all hell broke loose on the desktop. I got repeated notifications about the WLAN going up and down while the netbook was trying to connect (and ultimately failed).

Checked syslog, it was getting flooded with messages about the WLAN going up and down along with tons of debug/info messages from Network Manager and related services.

Something caught my eye: Network Manager stated that it started dnsmasq, but dnsmasq was unable to start because **it was already running**!
A simple ```
sudo service dnsmasq stop
``` later, the netbook was able to connect and syslog was no longer being flooded!

Looking at the package descriptions for dnsmasq and dnsmasq-base, I would assume only dnsmasq-base is needed as we don't actually need the daemon to run at all times, just when the WLAN is active and Network Manager will take care of managing it for us.

Later I lost the connection (went out of range) and had troubles reconnecting. All I had to do then was disable wireless in the applet and enable it again. (This time Network Manager logged that it killed the dnsmasq process and started it again.)

Oh btw, dnsmasq logs which nameservers it finds and will pass on to clients, and dnsmasq-dhcp will log traffic regarding IP negotiations/assignments. This can be invaluable information when trying to figure out why you get an incorrect IP, or none at all.

I hope this helps someone having similar issues. Wading through the logs can be scary (especially when they get flooded as you watch) but it's often worth it even if one doesn't know exactly how things work. ;)

---

### Post by priegog on 2010-07-14
Awesome, thanks for taking the time to write this...
It seems like a bug to me, so you might want to look if there's one already, and if not submit one yourself. However, I seem to remember that installing dnsmasque is not necesary since at least a couple of releases (it might have something to do with it)

---

### Post by Desigen on 2011-02-16
Hi,

Thanks a lot for this tip but my mobile is trying to get IP address from my computer. Should I download dhcp-server? or Is their anything else easy to do? 

Thanks

---

