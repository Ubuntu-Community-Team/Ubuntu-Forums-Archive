---
title: "No problems with D-link wda-1320"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by questions on 2006-07-08
just wanted to let you guys know that i was so worried about which wlan pci card would work and i tried out the dlink wda-1320 and it worked perfectly with 6.06 ubuntu. so far so good, restarted it to see if it kept my wep setting and it sure did. Hope no problems in the future with it.

---

### Post by Zerocool10482 on 2006-07-09
Thanks I'll get ASAP. I'm tired of buying stuff that doesn't work. I think D-Link is the only products that work. I think I'll only use D-Link. Thanks.

---

### Post by questions on 2006-07-09
Let me know asap how it comes out zero. Im happy with it, no run around just str8 forward out the box

---

### Post by StoneMan353 on 2006-07-09
Another vote here for D-Link,

I'm using the DWL-G520 pci card which uses the Atheros chipset.
Works flawlessly out of the box under Ubuntu 6.06, although some manual tinkering with wpa_supplicant was required in order to get WPA-PSK encryption working properley.

D-Link products have never let me down. *touches wood*

---

### Post by justintime32 on 2006-07-11
Hi Guys,

What a coincidence, I was just looking for a new wireless card last night and stumbled on this exact model and contemplating to get it, although because I couldn't find what chipset it used, I was hesitant to do so. I guess now I can get it without worries.

Just as a question, what chipset does the WDA-1320 use? I guess it doesn't really matter, as long as it works, but it would be nice to know.

---

### Post by Zerocool10482 on 2006-07-18
I have that card. And it worked out of box. I love it. I'm so happy that I have hardware that works. I'm just going to buy D-Link from now on.:KS

And about the chipset. I don't know but it worked. Go to the D-Link website for that info. Good luck.

PS. Never get Airlink. Your just killing yourself.

---

### Post by loserboy on 2006-08-07
> tried out the dlink wda-1320 and it worked perfectly with 6.06 ubuntu.

can you tell me what version you have (h/w f/w?)

I just bought one and I don't wanna open it if its not gonna work.

Edit:  sweet nm it works perfect, better than my WMP45G v.4

---

### Post by tadams_zz5 on 2007-01-21
No such luck with Edgy 6.10.  I am currently trying to get my machine to see the wireless card.

---

### Post by dsegarra on 2007-01-23
No luck either. Not even on Dapper release. I havent been able to set up two different atheros cards. Have followed every possible tutorial, help, reference. I am to the point of trying another distro. Have tried Xubuntu as well. The card starts but it just doesnt scan or finds any router and the power and activity lights both blink. By the way I am running an AMD 64. Any thoughts, comments or tips before I sadly say goodbye to ubuntu??. Thanks 


d.

---

### Post by nzruss on 2007-02-11
I've been messing with the Linksys WMP-54G V4.1 and what a waste of time.  I partially got the wmp-54g  working after downlading the newest ndiswrapper (1.37) and latest drivers.   I've spent more than two  weekends on just getting the WMP-54G scanning let alone connecting getting WPA running. What a piece of crap. Why the heck doesn't this stuff "just work"? Linksys should have one of their coders sort the linux drivers and a simple script to get it all working. </rant> ).  

So, today  i went an  purchased and installed the D-Link WDA-1320, and man, what a piece of cake!!!!! 

I did a fresh install, (Edgy i386), updated everything, then installed "network-manager-gnome" though synaptic. I logged out, then logged back in and network manager showed all the wi-fi networks around me. I clicked on my network and it asked for my WPA passphrase. I entered it, it connected!!!! YAY!!!! 

I then had to enter a key-ring password, and that was it. I unplugged my Ethernet cable and it set me free!!! 

This is how it should be. I cannot recommend the WDA-320 enough.  Worth every cent.

---

### Post by flysurferrosa on 2007-03-01
I'm pretty new to the linux stuff and I just installed Ubuntu 6.1 on my computer.  I bought the WDA 1320 PCI and put it in there, but I still can't get the internet.  Any advice?  I've been reading up on this board and also this other place, "Eureka" but still nothing has worked.  I tried re-installing ubuntu with the hardware in there, that didn't work.  Thanks everyone!

---

### Post by BluJai on 2007-03-28
After trying two other wifi cards, I found this thread and others about success with the D-Link WDA-1320. I must share the fact that **it worked beautifully for me as well** -- on a completely clean 6.10 install. All I had to do was specify my SSID and WEP password!

---

### Post by DisabledTrucker on 2007-04-07
> **nzruss said:**
> I've been messing with the Linksys WMP-54G V4.1 and what a waste of time. I partially got the wmp-54g working after downlading the newest ndiswrapper (1.37) and latest drivers. I've spent more than two weekends on just getting the WMP-54G scanning let alone connecting getting WPA running. What a piece of crap. Why the heck doesn't this stuff "just work"? Linksys should have one of their coders sort the linux drivers and a simple script to get it all working. </rant> ). 
 
So, today i went an purchased and installed the D-Link WDA-1320, and man, what a piece of cake!!!!! 
 
I did a fresh install, (Edgy i386), updated everything, then installed "network-manager-gnome" though synaptic. I logged out, then logged back in and network manager showed all the wi-fi networks around me. I clicked on my network and it asked for my WPA passphrase. I entered it, it connected!!!! YAY!!!! 
 
I then had to enter a key-ring password, and that was it. I unplugged my Ethernet cable and it set me free!!! 
 
This is how it should be. I cannot recommend the WDA-320 enough. Worth every cent.
 
I'm beta testing the 7.04 and have the WUA-2340, which is the upgraded version of this in USB form and I've found that if you:
[LIST=1]
[*]Install the O/S,
[*]download the updates,
[*]install ndiswrapper using add/remove,
[*]use the instructions here: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#ndiswrapper](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#ndiswrapper) modifying the first instruction, to point to the folder that you put the drivers in, (I reccommend just grabbing the drivers from D-Link's site, version 1.01, and extracting them to get the files on a windows machine first, then save those files in a folder on your desktop, I chose "drivers". So my first line read "sudo ndiswrapper -i ~/Desktop/drivers/NetA5AGU.inf" and the rest just worked afterwards.)
[*]Once I finished with that, I rebooted, it found the device, then I clicked on the network and added my network in, added the WPA-PSK2 encryption in, and it logged into my network. When I was asked for the key-ring password, I put in the same password I used for my account log-in, you'll find out why below.
[*]Finally I finished up by following the instructions here: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-92c70cd59ecb39c8645a88a26134115395c7d904](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-92c70cd59ecb39c8645a88a26134115395c7d904) to fix it so I didn't have to worry about the network not being able to start when I logged in. This helps because this is my sons computer and this way he doesn't need to know my network access key to log into it each time he restarts his computer. Basically all I did was download the preconfigured file, then "sudo gedit gdm" to match:[/LIST]```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
## Added for pam-keyring so that NetworkManager doesn't ask for Keyring password.
## Please note that keyringpassword and login password must be the same.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```and that's all there was to it. 
 
<rant>I just wish it was easier than going through all of this just to get it working, but once I got it working, it just works now. It would be really nice if they just included the drivers for this device in the operating system, so one wouldn't have to do anything but install the operating system and log into their network, but that would probably be asking too much. I don't know much about the atheros chips they are using, but D-Link has always done me good, when others have miserably failed, especially linksys. I don't expect to get the "Rangebooster" feature to work, but the rest of the driver should already be added in, especially with this new equipment being as popular as it is.</rant>

---

### Post by wgbuntu on 2007-04-26
Just bought and installed D-link WDA-1320 in Ubuntu 7.04 Feisty without any problems.  Does use Artheros restrictedd driver which was installed when card was recognized and configured.  Switched to wireless connection and  found the internet with out a hitch.  I did have to deselct my wired NIC in networking to enable the wireless connection.

---

### Post by SkyScrap on 2007-06-08
Hi,

any other experiences with Feisty & WPA? Does WPA work with the network manager?

Andreas

---

### Post by moron on 2007-06-08
I found that it was impossible to connect using the network manager. I had to uninstall it and then manually configure my network.  As well, I have to manually run /etc/init.d/networking restart to get online at all at this point.  

I am also finding the WDA-1320 to be less than optimal as far as reception strength and reliability goes (under Feisty) though it is definitely possible this has something to do with my personal network setup.  I am about 20 - 25 meters away from the access point but it is through two walls and there is a fridge pretty much directly in the line of the sight between the two. It may also be related to a physical issue with my case where I cannot screw on the antenna 100% due to it hitting the metal besides the opening on the back of the PC between PCI slots (arrrgh).  It works, just not great is all.  

More importantly, D-Link is absolutely pathetic as far as technical support goes.  They also mislabel products so beware (the DPR-1260 claims to be able to act as a wireless bridge but can't as was re-affirmed by D-Link support).   Finally, I purchased a really sketchy router from them (the WBR-1310, constant reboots and loss of connection on both wired and wireless connections) which makes me leery of purchasing anything else from them. 

I would go out of my way at this point to avoid them due to my negative experiences so far.   

Cheers

---

### Post by lossfound on 2007-06-09
I have this card in an old IBM Netvista all-in-one. It worked absolutely perfectly under Fedora Core 5. I let the machine sit for a while and decided to wipe it / go to Feisty. The restricted Atheros driver out of the box worked well enough to make the card work and let me see all the SSIDs available including my own, but I could not connect to the network (I use WEP, although I know I shouldn't). Manual config didn't work either, just made things worse. 

Got ndiswrapper-utils and ndisgtk along with the latest drivers. After being fed the .inf, ndisgtk insists that the hardware doesn't exist in the machine. 

Still trying to figure out how to make this work.

---

### Post by Tundro Walker on 2007-09-12
I've gotten 3 wireless cards so far, and have had varying luck. Starting with worst to best...
 
1) A LinkSys card from CompUSA. It uses a newer 48xx chip, so even though folks have had success with it using ndiswrapper, I didn't have any success. It and the drivers were just new enough to not be compatible. I beat my head into the ground on it for 8 hours, messing with network-manager, ndiswrapper, wicd & wifi-radar. Best I could do was detect the wifi networks around me, but couldn't connect to any of them.
 
2) A USB Airlink. I plugged it in, and it didn't work. I bought this at the same time as a bought a WDA-1320 (since most folks had success with it, I figured one of the two should work out of the box). This USB didn't work out of the box, even though it was on the Ubuntu Wifi list as doing so (can't remember the Airlink model name, but it was on the list as "out of box" compatible). Anyways, since I had bought the d-link pci card at the same time, I just quickly went to trying it out. 
 
3) Installed, got madwifi drivers, worked like a charm using wicd. Network I was connecting to was WPA, and it would auto-connect upon reboot. (However, sometimes Feisty wouldn't detect my card, which I noticed using iwconfig and saw ath0 not showing up sometimes). HOWEVER (you knew it was coming), while it was singing along when the networkd was visible, when my network owner (the guy I live with) hid the network, I've had trouble connecting ever since. Wicd would connect, then randomly disconnect me after a few minutes (of idle time, I think). I'd try to reconnect, but it wouldn't see the network. I'd refresh, and it wouldn't work. I click "Hidden Network", type in the ESSID, and try it, and it would sporadically connect or not. I finally got connected, and decided to dump wicd for wifi-radar (still using madwifi for drivers), and wifi-radar hasn't even been able to connect at all (I'm currently doing this reply, and trying to look for solutions, at work, which I'm really loathe to do, but need to find a solution.)
 
So, long and short... WDA-1320 works great with madwifi package / drivers, WPA, and wifi-radar or wicd as the connection too. Wicd is really good, too, because you can easily set up the options for the connection, and can just click a checkbox to get it to auto-connect you when you reboot. You'll have to go to sourceforge to get the link to their repo's, though, then add it as a 3rd party repo to d/l it through Synaptic / Apt-Get. In installing wifi-radar / wicd, they auto-remove network-manager, I assume because it can cause conflicts.
 
And, of course, all that greatness working like a charm just goes to cow pat when you make your network hidden.
 
As a last resort, I was going to try to tweak the /etc/network/interfaces file to make sure it's not conflicting. My theory is that, even though network-manager is uninstalled, the leftover config file(s) might still be conflicting with wifi-radar's or wicd's.
 
Worse comes to worse, my network owner said he doesn't mind just unhiding the network permanantly if that's what it takes (he's been pretty flexible). But it's just annoying that he should have to do so. Ubuntu was always "just working" for me with everything, and I heard rumblings of folks when it came to wireless, but I never knew it was this bad until I tried it myself. 
 
But, unlike others, I'm still a firm advocate and supporter of Ubuntu, even if wireless has been troublesome. I don't blame Ubuntu for not working with Wifi. I blame the Wifi manufacturers for not making Linux drivers. Ubuntu is just the messenger saying that the hardware doesn't work, and you shouldn't shoot the messenger. Sadly, I'm supporting those shoddy manufacturers, because I'm paying them for wifi stuff that doesn't really work out of the box with Linux. So, I'm just promotiing their bad behaviour. Two wrongs (them not making Linux drivers, and me still purchasing their product even though it's not Linux compatible off the bat) don't make a right. But, gotta get some wireless going... Really wish Mark Shuttleworth would work with some hardware manufacturers to get them to produce more Linux stuff as part of his "profiting off the Linux ecosystem, not Linux itself" game plan.

---

### Post by snickers295 on 2007-09-26
I have a dlink wda-2320 and it works fine on xandros 4.0 home premium but im downloading ubuntu 7.4 right now because microsoft if going to send xandros into the ground  with this junk there doing with them but anyway i'm wondering if my wireless card will work easy or take heck to get it to work or not even work so if anyone uses that card and uses ubuntu 7.4 could you tell me if it works or not.
thanks

---

### Post by ViaoV on 2008-06-26
I just picked up a Dlink wda-1320 and its not working out for me


it doesnt show up at all in ifconfig.

dmesg doesnt seem to have anything in it about the card

lspci | grep "Atheros" shows:
01:0a.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

lshw -C network shows:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10


Im assuming its a driver issue of some kind...seems odd since so many people have had no problems. Anyone have any idea what could be wrong?

---

