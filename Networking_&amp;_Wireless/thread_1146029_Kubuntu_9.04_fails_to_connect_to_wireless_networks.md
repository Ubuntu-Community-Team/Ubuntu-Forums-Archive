---
title: "Kubuntu 9.04 fails to connect to wireless networks"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by vletoh on 2009-05-02
Kubuntu 9.04 fails to connect to wireless networks! Though the new network manager might look cool, it fails to connect to any wireless WPA network with a hidden SSID.

I guess the developers must have followed the course "How to loose the battle with Windows again"...

Unbelievable that (k)ubuntu versions are released with such MAJOR bugs.

---

### Post by Ichido on 2009-05-02
I agree.
Ubuntu 7.10, 8.04, 8.10 & 9.04 all have this problem.
Puppy Linux and PCLinoxOS do not have this problem.
IMHO, the Wireless 'Network Connections' is the one "Trouble Spot" in an other wise Excellent Linux O.S.!
I wish I could help.

---

### Post by Alfred_McGee on 2009-05-05
Kubuntu 9.04 is a slight improvement over 8.10 in that it recognizes wireless networks, even if it won't connect to them. The last few versions of Ubuntu, on the other hand, have supported my wifi card OTB, and even before that, all that was needed was some minor tweaking.

---

### Post by Saibot Sivad on 2009-05-19
The title should be "Kubuntu 9.04 fails to connect to hidden wireless networks"

I just installed Kubuntu 9.04 to a secondary partition, and could not connect to a hidden secured (WPA) wireless network.

Can someone with a bit more authority on the subject confirm this as a bug, or is there a different method? I found this as the number one post for a Google search of "kubuntu connect hidden wireless network" and would appreciate an answer on this issue quickly. I will continue searching...

My method (not entirely sure, since I had to reboot into Ubuntu) which did not work:
Right click on network manager icon
Go to "Manage networks" (or similar)
Go to Wireless tab and add new
Type in name of hidden network
Click on tab called "Security"
Select WPA and type in password
Click OK, Click OK of "Manage Network" thing
No auto connection, none shows up with the left-click either

Can someone else confirm that Kubuntu 9.04 cant connect to hidden wireless?

---

### Post by Saibot Sivad on 2009-05-19
And I quote:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/339313](https://bugs.launchpad.net/ubuntu-release-notes/+bug/339313)
"Kubuntu Jaunty: Cannot Connect To Wireless Network with WEP shared key"

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/330811](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/330811)
"Can't connect to a hidden network"

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/339313](https://bugs.launchpad.net/ubuntu-release-notes/+bug/339313)
"Kubuntu Jaunty: Cannot Connect To Wireless Network with WEP shared key"

And there is more: It appears that the Kubuntu developers *knew* that the included network manager did not work, yet they included it. Now, you can apparently install some other wireless network manager and have it work, but everything on Kubuntu requires a working network connection, so it's a big F U if you can only get wireless. Like me.

Let me say it this way: If you installed Kubuntu 9.04 and can only connect to a hidden and secure wireless network, the Kubuntu developers essentially said "Screw You".

Well, if someone can tell me I am wrong, I will apologize, otherwise I say "Screw You" to Kubuntu.

*Other quotes by people who may or may not be similarly minded:*

"Shipping code that is known to be broken in a system which is ostensibly designed for new Linux users to find easy to use is disgraceful, frankly, when there is at least one existing solution that seems to be better."

"I would understand if this was an old issue that developers were still looking to resolve, however these types of networks worked just fine in Kubuntu 8.10, so there is absolutely no excuse for Canonical to have released Kubuntu 9.04 with such a huge bug."

"There should not have to be a workaround installed on a fresh install of Kubuntu. If it doesn't work then dont' put it in."

"I must add that I find Ubuntu KDE in its present form a rather unpleasant experience"

---

### Post by Old *ix Geek on 2009-05-19
> **Alfred_McGee said:**
> Kubuntu 9.04 is a slight improvement over 8.10 in that it recognizes wireless networks, even if it won't connect to them.Based on my experience I must disagree. I've posted about my problems getting wireless to work with 9.04 (Kubuntu), but the short version is: All I did was boot my HP dv6000 laptop after installing Intrepid and it found, configured, and immediately had working its Broadcom BCM43xx card. Silly me, I thought Jaunty would be just as painless!  Nope.  I NEVER did get wireless working and finally gave up.  I'm back on Intrepid now.

---

### Post by fedexnman on 2009-05-19
my wireless decided to work today, i put my password in differently,i put it in  the 1st wep key option instead of the 2nd  the wep passphrase option. i unhooked my wired connection, it took bout 2 mins maybe but it finally connected n good too.:popcorn:  im lovin 64bit jaunty, my flashplayers workin too
:biggrin:.

---

### Post by MyR on 2009-05-25
What the hell. I just installed kubuntu but can't use it now?

---

### Post by Terry851 on 2009-05-25
Have you tried entering the mac address of your wireless router in the BSSID and MAC fields in Network Manager?  I was unable to connect to my wireless router until I did this.  Still a bug in my opinion as you may not know the BSSID / MAC of a router, but this may allow you to use Jaunty until it's fixed.

---

### Post by MyR on 2009-05-25
> **Terry851 said:**
> Have you tried entering the mac address of your wireless router in the BSSID and MAC fields in Network Manager?  I was unable to connect to my wireless router until I did this.  Still a bug in my opinion as you may not know the BSSID / MAC of a router, but this may allow you to use Jaunty until it's fixed.
doesn't work :[
knetworkmanager doesn't work either.
I even tried putting the MTU in.

I have no use for an offline OS

---

### Post by t0mppa on 2009-05-25
Why not just install an alternative manager (WICD for instance) then, since it's a known issue that the default one won't work? Will get much better GUI functions as well as a side product. Or alternatively just configure wireless from terminal.

---

### Post by MyR on 2009-05-25
> **t0mppa said:**
> Why not just install an alternative manager (WICD for instance) then, since it's a known issue that the default one won't work? Will get much better GUI functions as well as a side product. Or alternatively just configure wireless from terminal.

Thanks for the suggestions.  I decided I didn't like Kubuntu & went back to Ubuntu.

---

### Post by Saibot Sivad on 2009-05-26
I installed WICD (after a great effort, since my network was not accessible, see previous posts) to see if I would like Kubuntu, but I don't like the interface much, and I find it hard to put up with a group that puts known-to-be-broken software in it's major release.

Kubuntu makes extensive use of the internet, with the standards like the package manager and so on, but it adds a clever bit of functionality where you can get new themes from gnome-look.org without opening a browser. Very neat ideas, although still being polished up a bit.

What I am saying is that Kubuntu basically *needs* the internet to work, and putting in a faulty network manager was probably the *absolute worst* mistake they could have made, in my opinion.

Now, if you don't use a wireless connection, or if your wireless connections are all unsecured, I think KDE would still be fun to play with. I just don't have the time to be fiddling with buggy software. 

I admire the effort the Kubuntu group has put in so far, and I look forward to when it becomes stable again.

---

### Post by t0mppa on 2009-05-26
WiFi Radar is another option, if you don't like WICD.

I totally understand what you're saying and am a little disappointed at the state of Kubuntu 9.04 myself (installed it to a friends computer, since she wanted it). Neither it nor the KDE 4.22 that they decided to use is fully bug free yet and it's a bit of a hassle getting it set up.

Although this is particularly an Ubuntu problem, since they insist on doing a full OS upgrade every 6 months and that doesn't seem to be enough time to polish away the rough edges. Just do a search and count at how many "9.04 broke my wireless that has worked just fine since x.xx" posts there are on this forum for instance. And wireless isn't the only area having problems. ATI & 9.04 cut out everyone with a bit older ATI GFX card for example.

Should rather just label the new version as late beta or a release candidate or some other name that clearly tells people it is fully operational, but there's a good possibility of running into issues. That way non-tech savvy people who get utterly frustrated when running into problems (because they're not used to doing fixes through terminal or compiling new software manually) wouldn't swap to the new version before it got its biggest issues worked out.

As you probably noticed though, Jaunty was hyped a lot even before it was released and the day that it was, pretty much all mentions of Ibex disappeared from ubuntu.com, leaving new comers no idea that they might be better off with an older version - for the first few months anyway.

---

### Post by Saibot Sivad on 2009-05-27
I understand that things will break in a new version, but if a new program is not functional (i.e., if you KNOW it doesn't provide even half support) than use the old version until you can finish it.

This is exactly what the Kubuntu developers did: They KNEW the updated network manager program was practically non-functional--if it can't reliably connect to secured networks, I think it is safe to call it non-functioning. The old network manager program worked fantastic. They should have used the old version but instead made a very poor choice, and now they are taking heat from highly frustrated users like myself.

It would be like Microsoft releasing Windows 7 before Vista and calling it a normal operating system: If I had payed money for it and wasted time installing it, I would be downright pissed and get my money back plus some for false claims. Of course, the Kubuntu developers aren't looking for the bottom dollar as much, so things like this wireless fiasco invariably turn up more frequently than with proprietary software.

Note that I am still using Open Source (Ubuntu), since I do think it is fundamentally better (philosophical reasons), I just think in this case the Kubuntu development team really took a nasty turn.

---

### Post by mendieta on 2009-06-28
I think there is no need to be harsh with the developers. I also lost wifi after the upgrade (from 8.04 to 9.04). Oddly enough, right after the upgrade it did work for a couple hours, but once I cleaned up some of the mess from the (two version in one shot) upgrade, there was no wifi connection and I found no way to bring it back :-( I spent circa 5 hours trying very many things, googling and what not. Still no luck. This is an eeepc 701. Any pointers, truly appreciated. I think I'll try to get a cheap usb dongle and be done with it.

---

### Post by MyR on 2009-06-28
> **mendieta said:**
> I think there is no need to be harsh with the developers. I also lost wifi after the upgrade (from 8.04 to 9.04). Oddly enough, right after the upgrade it did work for a couple hours, but once I cleaned up some of the mess from the (two version in one shot) upgrade, there was no wifi connection and I found no way to bring it back :-( I spent circa 5 hours trying very many things, googling and what not. Still no luck. This is an eeepc 701. Any pointers, truly appreciated. I think I'll try to get a cheap usb dongle and be done with it.

wow that sucks.  i think the eee 701 has a great wifi card (atheros) because it is fully supported by aircrack ;] i run xubuntu on my eee.

---

### Post by mendieta on 2009-06-28
> **MyR said:**
> wow that sucks.  i think the eee 701 has a great wifi card (atheros) because it is fully supported by aircrack ;] i run xubuntu on my eee.

Interesting, is Xubuntu 9.04 running the wifi ok out of the box? Maybe I should try that, unistall some heavy programs and try xubuntu-desktop. Yes, this has been horrible. Thanks a bunch!

---

### Post by MyR on 2009-06-28
> **mendieta said:**
> Interesting, is Xubuntu 9.04 running the wifi ok out of the box? Maybe I should try that, unistall some heavy programs and try xubuntu-desktop. Yes, this has been horrible. Thanks a bunch!

xubuntu works perfectly out of the box

---

### Post by theozzlives on 2009-06-28
I never have cared for Kubuntu, but was going to make a Flash Drive to play with. Not only does the wifi not work, but neither does the USB-creator. So I figured screw it and put Ubuntu back on my flash.

---

### Post by mendieta on 2009-06-28
> **MyR said:**
> xubuntu works perfectly out of the box

Thanks a bunch, I think XFCE has a very clean interfac, I like it, even though I prefer KDE, but I would like it. Before I go on a massive install, would you be so kind to check what kernel module you are running in Xubuntu for wlan? That would be awesome. Also awesome would be the name of the network applet for Xubuntu, maybe installing it would do. It is really hard to install too much stuff in the tiny 4Gb SSD.

Thank you so much in advance!

---

### Post by MyR on 2009-06-28
I don't even know.  It worked perfectly so I didn't have to mess around with the wifi at all.  It's my mom's eee so I don't have access to it at the moment.

I believe it uses the same network-manager as gnome.  Furthermore I suspect that any flavor of Ubuntu would use the same kernel module for a given nic.  Kubuntu just has shitty gui applications that can't handle connecting to wifi.

peace

---

### Post by mendieta on 2009-06-28
> **MyR said:**
> I don't even know.  It worked perfectly so I didn't have to mess around with the wifi at all.  It's my mom's eee so I don't have access to it at the moment.

AH, Ok!
> 
I believe it uses the same network-manager as gnome.  Furthermore I suspect that any flavor of Ubuntu would use the same kernel module for a given nic.  Kubuntu just has shitty gui applications that can't handle connecting to wifi.


Mmm, I did try installing network-manager-gnome, ran nm_applet and same issue. It's something deeper. In fact, this was running perfectly in Kubuntu right after the upgrade, but there were a couple broken package, I ran a massive "dpkg --reconfigure -a" and screwed wifi (go figure). I am guessing a clean install of either xubuntu or kubuntu would work, but installing xubuntu-desktop here would probably not make a difference. Worth a shot perhaps if I can do it with little effort ...

I also tried Wicd with no luck after wifi was broken, I can't tell you how many things I tried! And I know my way around!

Thanks a lot for taking the time!

---

### Post by mendieta on 2009-06-29
I fixed my problem! It was some leftover blacklisting in  /etc/modprobe.d/ 

Cleaning that up and using the open source driver worked just dandy! Thanks a lot MyR for hanging in there with me. I'll try Xubuntu from a thumbdrive when I get a chance :)

---

### Post by Saibot Sivad on 2009-07-12
> **mendieta said:**
> I think there is no need to be harsh with the developers.
I don't think I was being harsh, just stating a realistic criticism which I had not seen anywhere else when I wrote it.

As an example, consider if some operating system developers released a new version which broke all IDE hard drive support. Even though many people use SATA drives, the IDE drive is still used by a large enough user base, and IDE support is so critical, that I think it would be right to level some serious criticism at those developers.

In a similar way, when KDE released a new version which cut off all secured wireless network support, they cut off a significantly large user base and basically ruined the usability for those users.

Of course, within an operating system there are known bugs that still have no solution, many hardware drivers come to mind, but you do what you can to get the majority to work. This is an understood predicament within the open source community, and within Linux based releases in general.

However, consider that: 1) There was no need to change the software, since a working solution already existed, and 2) it was a reported bug early enough that they knew it wouldn't work.

From reading various blog posts and bug report forums, I feel that KDE cut off a significantly large user base with their decision to include broken software, and I am not the only one who felt that way. I had not heard anyone voice this criticism clearly, and so I thought it was necessary.

> **mendieta said:**
> I also lost wifi after the upgrade (from 8.04 to 9.04). Oddly enough, right after the upgrade it did work for a couple hours, but once I cleaned up some of the mess from the (two version in one shot) upgrade, there was no wifi connection and I found no way to bring it back :-( I spent circa 5 hours trying very many things, googling and what not. Still no luck. This is an eeepc 701. Any pointers, truly appreciated. I think I'll try to get a cheap usb dongle and be done with it.

I see you were able to solve your networking problems, good luck. KDE is a fun interface with a lot of potential, if you like it keep on it!

---

### Post by Vladimir Hidalgo on 2009-08-13
Hi!, sorry for hijacking this thread or whatever, but I have a problem with knetwork manager.

I've installed Kubuntu 9.04 originally, knetwork was working partially with wireless (finds networks but can't connect to them), eth connection was fine so I decided to plug-in the eth cable to update to KDE 4.1, in which the same problem was present.

But I decided to install nm-applet (the Network Manager GUI for Gnome) and this applet **had not problems connecting to wireless**, so it's not a driver or fault of Network Manager core application.

My WiFi card is supported:
```
2:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1100                                                              
        Flags: bus master, fast devsel, latency 0, IRQ 28                                                     
        Memory at f6000000 (64-bit, non-prefetchable) [size=8K]                                               
        Capabilities: <access denied>                                                                         
        Kernel driver in use: iwlagn                                                                          
        Kernel modules: iwlagn      
```
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

nm-applet works fine, but it request key-ring access in every start, so I decided to update to KDE 4.2 but nothing, now I've updated to KDE 4.3 and still knetworkmanager refuses to connect.

I just click on the Wireless Network, enter WEP key and knetworkmanager just sit there with no progress nor information!.

For now I'm obligated to either use nm-applet or knetworkmanager with eth cable.

What could I do?.

~$ knetworkmanager -v
Qt: 3.3.8b
KDE: 3.5.10
KNetworkManager: 0.7


btw, I don't know why it says kde 3.5?, maybe I have an old knetworkmanager?.

After seeing this I searched in apt-cache for "KDE network manager" and figured that I only had network-manager-kde installed but not knetworkmanager... I'd installled the package knetworkmanager but the same problem persist in not being able connecting to a WiFi Network.

Running "knetworkmanager" from Terminal outputs this:

```

Activate Connection /org/freedesktop/NetworkManagerSettings/Connection/0 on Device /org/freedesktop/Hal/devices/net_00_13_e8_ad_75_1d
ICE default IO error handler doing an exit(), pid = 6554, errno = 11

```

---

### Post by Vladimir Hidalgo on 2009-08-13
ummm I was curious about the KDE 3.5 thing, and I searched through the web only to realize that knetworkmanager is not part of KDE 4...

I saw a post mentioning about installing a widget, which I though was network-manager-kde4...

But finally I've got it!, to solve connecting issues try this:

1st uninstall knetworkmanager:
```
sudo apt-get autoremove knetworkmanager network-manager-kde
```

2nd install the new widgets:
```
sudo apt-get install plasma-widget-network*
```

That will install two packages (at the moment of this writing of course):
plasma-widget-network-manager & plasma-widget-networkmanagement

Now add the the Widget "Network Management" and everything should be fine!

---

### Post by mendieta on 2009-08-16
> **Vladimir Hidalgo said:**
> 
That will install two packages (at the moment of this writing of course):
plasma-widget-network-manager & plasma-widget-networkmanagement

Now add the the Widget "Network Management" and everything should be fine!

Yes, and actually, if you install KDE 4.3 in Kubuntu 9.04, the upgrade automatically selects the KDE-4 widget for network management, and KNetworkaManager is greyed out, with a message explaining that it is broken right now. 

Having said that, I would love KNetworkManager to be fixed, and I think we need more tools like KNetworkManager, with a desktop agnostic library, and KDE, GNOME, et al frontends (I guess a gtk only for xfce, etc).

---

### Post by AmerNewbieInDE on 2009-08-16
try 

sudo modprobe -r iwlagn

sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

i had troubles connecting too, had to enter this everytime i started the notebook. then i upgraded the kernel to 2.6.31, since then never had a problem

---

