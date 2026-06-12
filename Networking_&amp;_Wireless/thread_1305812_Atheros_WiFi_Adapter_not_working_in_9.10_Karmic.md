---
title: "Atheros WiFi Adapter not working in 9.10 Karmic"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Chrono Reaper on 2009-10-30
I have installed 9.10 Karmic on my Toshiba Satellite and right out of the box my Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter is not detecting Wireless connections. The current wifi driver from the installation is not working. I haven't done anything yet and have done some research and thinking about installing Madwifi, but the recent history is outdated and only goes up to hardy heron. Any ideas?

---

### Post by drumkitcat on 2009-10-30
> **Chrono Reaper said:**
> I have installed 9.10 Karmic on my Toshiba Satellite and right out of the box my Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter is not detecting Wireless connections. The current wifi driver from the installation is not working. I haven't done anything yet and have done some research and thinking about installing Madwifi, but the recent history is outdated and only goes up to hardy heron. Any ideas?

Hi,
Last night I installed Kubuntu 9.10 as a fresh install on my Toshiba Satellite A40 laptop - it worked great (did the full drive reformat, etc).  I also have the AR242x Atheros wireless adapter and the laptop is on my home network amongst some Windows XP machines.  I had no problem detecting the wireless network - it was a little tricky getting the WEP coding right, but once I did the thing was working great.  I haven't tried the wired LAN connection yet, but wireless is best with my laptop.

Last time I used Linux was Ubuntu's Edgy Eft, and had to use MadWiFi to get the Atheros driver working - which it did, but I found it didn't have the same range it originally had when I was using Windows XP on the laptop. 

So, I can say that Madwifi does work - I recall it took a fair bit of configuring to work, but that could be an option for you.

---

### Post by jelkimantis on 2009-10-30
I had this problem.  I don't know if it will help you at all, but I found that following the directions on :

[http://art.ubuntuforums.org/showthread.php?t=1163380]("http://art.ubuntuforums.org/showthread.php?t=1163380")

really helped me out.  I'm running wireless right now! :-)

jsl

---

### Post by SuperSonic4 on 2009-10-30
Madwifi has largely been replaced by the ath5k driver for atheros

What is the output of ```
sudo modprobe ath5k
```

---

### Post by swansong on 2009-10-30
After upgrading from 9.04 to 9.10, my Atheros (ar5212/ar5213) wireless device was not working, although it had been working before the upgrade. After hours of searching many, many websites, I found a post that mentioned "blacklist-ath_pci.conf". I typed "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf". This is what opened:

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k 

I put a "#" in front of the last line (#blacklist ath5k) saved the file, and rebooted (logging out and back in probably would have worked, but after all my searching and reading I wasn't taking any chances.)

It works.

---

### Post by GreatBunzinni on 2009-10-30
I've just logged in to say exactly what swansong said. Kubuntu's default install (or, in my case, automatic update) is set to ignore the default atheros driver. Just remove that default config from:

sudo vim /etc/modprobe.d/blacklist-ath_pci.conf

...and when you restart your system you have a nice network config, free of any proprietary drivers.

Score yet another point for linux. Yey! :D

---

### Post by Eric Lathrop on 2009-10-30
I have an Atheros AR5001+ nic, and removing the blacklist got me connected to the network, but I can't load any web pages reliably. I get a ton of connection timeouts, and when it does work it's really slow. Should I go back to madwifi?

---

### Post by dmp1ce on 2009-10-30
I have a AR2413 802.11bg NIC and swansong's advice worked for me.  Thanks!

I had upgraded from 9.04 to 9.10.

---

### Post by theWrkncacnter on 2009-10-31
> **swansong said:**
> After upgrading from 9.04 to 9.10, my Atheros (ar5212/ar5213) wireless device was not working, although it had been working before the upgrade. After hours of searching many, many websites, I found a post that mentioned "blacklist-ath_pci.conf". I typed "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf". This is what opened:

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k 

I put a "#" in front of the last line (#blacklist ath5k) saved the file, and rebooted (logging out and back in probably would have worked, but after all my searching and reading I wasn't taking any chances.)

It works.
Not only does this work, it works friggin *immediately!*
Thanks Swansong!

---

### Post by buspital on 2009-10-31
swansong's advice also worked for me after upgrading from 9.04 to 9.10. ar2413

---

### Post by wattage on 2009-10-31
Another high-five for **swansong**. That did the trick for me, too.

I have from lshw:
description: Wireless interface
product: Atheros AR5001X+ Wireless Network Adapter
vendor: Atheros Communications Inc.


Anybody know why 9.10 broke what was working fine in 9.04?

---

### Post by sodden on 2009-10-31
Thank You so much!!!! I'm new to ubuntu, and Your post sorted it out for me in no-time!!!
nice one !!!!

---

### Post by caustic386 on 2009-10-31
+1

Is there a particular place we can check for blacklisted hardware in these situations?

---

### Post by whenelvisdied on 2009-10-31
> **Eric Lathrop said:**
> I have an Atheros AR5001+ nic, and removing the blacklist got me connected to the network, but I can't load any web pages reliably. I get a ton of connection timeouts, and when it does work it's really slow. Should I go back to madwifi?

I've had the exact same problem.  The Ath5k driver gets me connected, but load times are ridiculous and unusable.  I have an Atheros AR5001X+ d-link (DWL-G520, I think), and when I upgraded to 9.10, my wifi stopped working.  This happened the last time I upgraded, and then, I just went into System Administration => Hardware drivers, and selected the madwifi drivers--everything worked great.  But this time, there were no madwifi drivers to select. I think they were in the linux-modules-restricted package, but that package doesn't exist anymore.  

I've tried installing madwifi from source, and while I can load the drivers (ath_pci, ath_hal, etc....), when I connect I get NO page loading, or ability to ping with any response. I would also get an error in my dmesg that said:

ath0: unknown SIOCSIWAUTH flag 12

I've resorted to booting the previous kernel (2.6.28-16), which gets me wifi back, but because of the upgrade, looks terrible.  

Any advice?  I've tried the IPV6 stuff, and this seems totally unrelated.

---

### Post by jtwillobee on 2009-10-31
My wireless WAS working, albeit slowly. Now it does not work at all. Their is nothing in my resolvconf if that means anything. My wireless is Atheros AR9285. This is an uber pain in the @ss. 

Help please. :(

---

### Post by whenelvisdied on 2009-10-31
Okay, on a lark, I downloaded ndiswrapper and went back to the new kernel. Using the drivers on my wireless card CD-rom, I was able to get wireless working.  It's certainly not my preferred option, especially since I can tell that it's a little sluggish.  I really hope someone can make the atheros drivers/madwifi drivers work.

---

### Post by jtwillobee on 2009-10-31
> **jtwillobee said:**
> My wireless WAS working, albeit slowly. Now it does not work at all. Their is nothing in my resolvconf if that means anything. My wireless is Atheros AR9285. This is an uber pain in the @ss. 

Help please. :(

I just installed the backports, and now it works great.

```
sudo apt-get install linux-backports-modules-karmic
```

---

### Post by whenelvisdied on 2009-10-31
Still nothing--I had already had that installed from the get-go.  I think that the ath5k driver simply doesn't work with the chipset I have.  Madwifi did, but doesn't now for some reason.  

Ndiswrapper is a poor substitute, with VERY slow load times, but better than ath5k.

---

### Post by addtoqueue on 2009-10-31
Still nothing for me too even with with the backports and "Swansong's fix".

---

### Post by robata on 2009-11-01
I'm new to ubuntu and am having the same problems. Call you tell me how to enter the following "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf" on my laptop.

---

### Post by Sparken on 2009-11-01
> **robata said:**
> I'm new to ubuntu and am having the same problems. Call you tell me how to enter the following "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf" on my laptop.
@ robata: Just use a text editor to edit the /etc/modprobe.d/blacklist-ath_pci.conf file while you are the root user or using sudo. Or open a terminal window and type:
*sudo nano /etc/modprobe.d/blacklist-ath_pci.conf*
that should open the nano text editor and you can modify the file.

---

### Post by joelmezzanotte on 2009-11-01
Anecdotal evidence but  if you are having random disconnections/slow unusable connectivity using the  0.9.4 madwifi driver seems to have corrected the issue for me.

[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)


My link is up at 11mbps as opposed to 1mbps. 

lspci |grep Ather
02:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


thought it might be helpful :)

Also added the following to the blacklist:

blacklist ath
blacklist cfg80211
blacklist mac80211

---

### Post by skyl4rk on 2009-11-01
In Ubuntu 9.4, I had change the driver to madwifi to get it to work.  After the upgrade, wifi didn't work.

swansong's fix worked on my Dell Latitude C640 running a D-Link DWL-AG660 wireless adaptor.  I had to edit the Wireless network to reenter my WPA password. System->Preferences->Network Connections / Wireless.

[http://ubuntuforums.org/showpost.php?p=8200371&postcount=5](http://ubuntuforums.org/showpost.php?p=8200371&postcount=5)

---

### Post by addtoqueue on 2009-11-01
> **joelmezzanotte said:**
> Anecdotal evidence but  if you are having random disconnections/slow unusable connectivity using the  0.9.4 madwifi driver seems to have corrected the issue for me.

[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)


My link is up at 11mbps as opposed to 1mbps. 

lspci |grep Ather
02:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


thought it might be helpful :)

Also added the following to the blacklist:

blacklist ath
blacklist cfg80211
blacklist mac80211


Just finished installing that driver and rebooted.  Wireless still not working.  The driver was installed following these steps:
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

lspci | grep Ather

06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

---

### Post by addtoqueue on 2009-11-01
Just tried [drpjkurian]("http://ubuntuforums.org/member.php?u=805294")'s attempted fix and it didn't work:
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Wireless still not working.

---

### Post by danwood76 on 2009-11-01
Hi I was having this same issue but following the thread posted above managed to fix it.

The instructions are  alittle garbled but just make sure you remove the ath_pci blacklist from /etc/modprobe.d/blacklist-ath_pci.conf and add ath5k and ath9k.
Then reboot.

Please note that the madwifi driver doesn't support all atheros cards but check dmesg output for module loading upon reboot.

```

dmesg | grep ath

```

you should see something like this upon a successful load:
```

[    7.881256] ath_pci 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.468962] MadWifi: ath_attach: Switching rfkill capability off.
[    9.256034] ath_pci: wifi0: Atheros 2413: mem=0xc0110000, irq=22
[   25.396020] ath0: no IPv6 routers present
[   54.070804] ath0: unknown SIOCSIWAUTH flag 12

```

---

### Post by BlueJeep on 2009-11-01
Hi,

Additionnally to what swansong recommended (which did not work for me) I edited the file "madwifi.conf" which is also in my "/etc/modprobe.d" folder, and I commented the line "blacklist ath5k". After rebooting my wireless connection became available.

Here are the first lines of the madwifi.conf :

## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
##blacklist ath5k

I left the remaining lines untouched, which means that now all the lines are commented.

---

### Post by addtoqueue on 2009-11-01
> **danwood76 said:**
> Hi I was having this same issue but following the thread posted above managed to fix it.

The instructions are  alittle garbled but just make sure you remove the ath_pci blacklist from /etc/modprobe.d/blacklist-ath_pci.conf and add ath5k and ath9k.
Then reboot.

Please note that the madwifi driver doesn't support all atheros cards but check dmesg output for module loading upon reboot.

```

dmesg | grep ath

```you should see something like this upon a successful load:
```

[    7.881256] ath_pci 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.468962] MadWifi: ath_attach: Switching rfkill capability off.
[    9.256034] ath_pci: wifi0: Atheros 2413: mem=0xc0110000, irq=22
[   25.396020] ath0: no IPv6 routers present
[   54.070804] ath0: unknown SIOCSIWAUTH flag 12

```

Thanks but still not working.  The contents of my blacklist-ath_pci.conf file are:

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci
blacklist ath5k
blacklist ath9k

The output of dmesg | grep ath is:

[    1.911618] device-mapper: multipath: version 1.1.0 loaded
[    1.911623] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.497238] ath_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.196023] MadWifi: ath_attach: Switching rfkill capability off.
[   20.069786] ath_pci: wifi0: Atheros 2413: mem=0xc0200000, irq=22

---

### Post by Sparken on 2009-11-01
I have the Atheros AR5001X+ (according to lspci). I stupidly rushed into doing the upgrade from 9.04 to 9.1 promptly lost wifi. 

I originally tried swansong's fix earlier in this post and got the wifi to work (albeit with 30% packet loss) for one session. After a shutdown and restart the wifi failed to work. 

I tried all the previous stuff, backports, madwifi drivers, wicd. I couldn't see the router with any of the gui managers until I did a console
*iwlist scan*

Then the chosen wifi manager could see the router, but could never successfully connect. I turned off wpa and left it an open network and still no joy. 
Finally I had had enough and saved my user data and did a clean re-install of 9.1. 

Wifi worked right out of the chute, stock network manager, no packet loss. Since the network manager stores the wpa passphrase in the stupid wallet system, ( I hate that freakin wallet thing) I have to put up with it asking me for the wallet password everytime I log in, but at least the wifi works for now.
It also kills the wifi connection when I log out, a real pain considering I connect to an nfs server for the bulk of my projects. 

If it helps anyone, the current working system has a blacklist file for the ath-pci. It is called blacklist-ath_pci.conf and contains the uncommented line "*blacklist ath_pci*"

The loaded module is the ath5k (lsmod), the /etc/network/interfaces file contains only "auto lo" and "iface lo inet loopback" lines.

So I don't know what got broken in the "upgrade" but all the king's horses and all the king's men couldn't put wifi together again.
BTW, even with a working wired connection on my upgraded 9.1, I could no longer connect to my nfs server. Grrr.

Now I'm going to try bypass this insipid network manager so I can get the network up at boot time and try to get my nfs shares work.

---

### Post by robata on 2009-11-03
Sparken: Thanks for your reply. I made the change using the terminal window. Then I hit the CTRL key and 'X', the 'Y' to try and save the change. However, when I re-opened the terminal window and typed in the same string you gave me the '#' was again missing from the start of the last line. Please advise. Thanks again.

---

### Post by addtoqueue on 2009-11-03
Posting from a Windows boot because wireless still not working in Ubuntu 9.10.

---

### Post by hactarux on 2009-11-03
> **robata said:**
> I'm new to ubuntu and am having the same problems. Call you tell me how to enter the following "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf" on my laptop.
You need to go to the top menu bar. Click where it says applications, go to accessories, and near the bottom is terminal. open terminal. you can then copy paste the command into terminal and hit enter. it will ask you for your password. enter it. and voila you have gedit running on the specified file!
Sorry about that. I didnt read page 3. i am a forum noob. Also this page will be perfect for fixing ym sisters ubuntu box with its atheros wifi! THANK YOU ALL!

---

### Post by rswhiting on 2009-11-03
I have a eeePC 1005HA with and Atheros wireless card. I upgraded to 9.10 and not only did the wireless die, the wired died after it was put to sleep. I've been searching forums for two days. I downloaded  and clean installed 9.10 NBR with the hope that it would solve my problem, but it didn't fix the wireless.

Swansong: you saved me from the shame of a wired netbook. Thank you.

---

### Post by nuser on 2009-11-03
> **joelmezzanotte said:**
> Anecdotal evidence but  if you are having random disconnections/slow unusable connectivity using the  0.9.4 madwifi driver seems to have corrected the issue for me.

[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)


My link is up at 11mbps as opposed to 1mbps. 

lspci |grep Ather
02:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


thought it might be helpful :)

Also added the following to the blacklist:

blacklist ath
blacklist cfg80211
blacklist mac80211


So I had the same problem - wireless wasn't working at all after the update. I tried the modprobe ath5k and that helped - wireless came up but the connection was really slow with ping times of several seconds even to my own router. Then I got the latest svn code for madwifi and build and installed the ath_pci module and loaded that - it pretty much worked the same way as the ath5k - painfully slow. Then I tried the tgz that joelmezzanotte posted and bulit that and it worked! Now I get normal speeds and all that. Thanks joelmezzanotte. I still hope they fix it in the main distro so that I can install kernel updates and not worry about it.

---

### Post by jimincascadia on 2009-11-04
> **SuperSonic4 said:**
> Madwifi has largely been replaced by the ath5k driver for atheros

What is the output of ```
sudo modprobe ath5k
```
Am happy to say this seems to have worked - the wireless icon re-appeared (am on a toshiba laptop whose wireless ceased to function with the 9.10 upgrade)- however - it does not 'hold' after re-booting - on re-boot - no wireless icon/connection so must re-enter the code <sudo modprobe ath5k> to activate it.

Any idea on how to make the change permanent?

Learning as I go - -

---

### Post by emanueleg on 2009-11-04
> **jimincascadia said:**
> Any idea on how to make the change permanent?

I had to comment the line
```
blacklist ath5k
``` in both */etc/modprobe.d/madwifi.conf* and */etc/modprobe.d/blacklist-ath_pci.conf* files.

ciao

emanuele

---

### Post by paul724 on 2009-11-04
I had two problems getting internet to work on my ancient armada m700 after upgrade from 9.04 to 9.10.

- **Wifi Atheros Adapter** - had to comment out blacklist ath5k in /etc/modprobe.d/blacklist-ath_pci.conf as mentioned by others.
- **DNS** - *NetworkManager* was a disaster - couldn't control DNS servers and couldn't see how to manually configure them, so I installed *Wicd* instead - simply using synaptics packet manager which also removed NetworkManager cleanly

Now it looks like I have a better system than before!:grin:

---

### Post by jimincascadia on 2009-11-04
> **emanueleg said:**
> I had to comment the line
```
blacklist ath5k
``` in both */etc/modprobe.d/madwifi.conf* and */etc/modprobe.d/blacklist-ath_pci.conf* files.

ciao

emanuele


...and here my beginner status shines.

I can certainly enter <blacklist ath5k> - but even after scouring the forum I don't see the process for opening either/both of those files to repeat the process - or am I over thinking this and it only needs to be entered one time?

cheers.

---

### Post by cadu-fpolis on 2009-11-04
[SOLVED FOR ME]
Just giving my thumbs up for the solution posted by joelmezzanotte in the page 3 of this thread.

I was getting high and unstable latency with Ubuntu 9.10 Karmic and Atheros Wireless card. Ping to a LAN host was like 200ms, then 1300ms, then back to 70ms, and so on.

Like joelmezzanotte posted, I downloaded the new MadWifi drivers ([http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)), then edited my /etc/modprobe.d/blacklist-ath_pci.conf with the following:

#blacklist ath_pci
blacklist ath5k
blacklist mac80211
blacklist ath
blacklist cfg80211

(Note the line "#blacklist ath_pci", so MadWifi's version can load at boot)

Then, compiled the MadWifi driver following the instructions on the INSTALL file provided with the package, and rebooted.

Wireless now is back to normal, latency between 1-2ms on the LAN, and Internet seems to work like it should now.

Thank you all!
Cheers.

---

### Post by robata on 2009-11-05
Swansong's solution worked for me moving from 9.4. to 9.10. I was able to make the change and save it (ctrl +o) using the terminal window. I'm using a Toshiba laptop with a Netgear WG511T wireless PC card.

---

### Post by Sparken on 2009-11-05
@robata : I believe you need to hit ctrl+o then it will prompt for the filename
which will already be listed so just hit enter then ctrl+x to close.

---

### Post by emanueleg on 2009-11-05
> **jimincascadia said:**
> ...and here my beginner status shines.

I can certainly enter <blacklist ath5k> - but even after scouring the forum I don't see the process for opening either/both of those files to repeat the process - or am I over thinking this and it only needs to be entered one time?

cheers.


[LIST=1]
[*]open a terminal
[*]type: sudo gedit  */etc/modprobe.d/madwifi.conf*
[*]wherever you can see a line like "blacklist ath5k" (there could be zero, one ore more lines like this), put a '#' in front of it; it should become
#blacklist ath5k
[*]save and close the text editor
[*]type: sudo gedit */etc/modprobe.d/blacklist-ath_pci.conf*
[*]repeat point 3 and 4
[*]restart your system and cross your fingers :-)
[/LIST]
ciao

emanuele

---

### Post by wadhwa100 on 2009-11-06
I upgraded from Ubuntu 8.04 to 8.10 and then onward to 9.04 and finally 9.10! Every upgrade without fail my DLINK DWL-G630 AirPlusG refused to run on my Compaq Pressario Laptop without tweaking something somewhere, but work it did every time (post tweaking)! For 9.10 thanks to the above posts all I did was

sudo modprobe ath5k

I tried the blacklist # option mentioned above in the blacklist file! It did not work for me! I located another file called madwifi.conf in the same directory that also has a blacklist ath5k which also will also require to be #'ed out.  

Also for some reason the eth0 interface (wired interface) had to be removed from the /etc/network/interfaces file. Otherwise ubuntu was defaulting to wired connection and not sending any packets to wireless interface. I also knocked off the "auto" eth0 from network manager. 

Things seem to be fine for the time being..... until the next upgrade, I guess!

---

### Post by Sam_S on 2009-11-07
> **BlueJeep said:**
> Hi,

Additionnally to what swansong recommended (which did not work for me) I edited the file "madwifi.conf" which is also in my "/etc/modprobe.d" folder, and I commented the line "blacklist ath5k". After rebooting my wireless connection became available.

Here are the first lines of the madwifi.conf :

## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
##blacklist ath5k

I left the remaining lines untouched, which means that now all the lines are commented.

In my case, I made the suggested change to blacklist-ath_pci.conf and my wireless still did not work.  Then I tried just uncommenting the "blacklist ath5k" line in madwifi.conf and it still did not work.  Next, I renamed the madwifi.conf file (since I did not want to uncomment all the other lines within it).  After reboot, the wireless now works fine on my Toshiba satellite laptop.  

Thanks for the help.

---

### Post by CoolDreamZ on 2009-11-08
This looks like a similar problem to the broadcomm wifi issue resolved on this thread [1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

### Post by TwoToneSpirit on 2009-11-08
A friend of mine has a AR5001 - same problem but commenting out the blacklist does not help.  In fact, there is no "blacklist ath5k" in the file - instead "blacklist ath_pci".  Neither un-blacklisting this nor blacklisting ath5k helps.

As per usual, the network device seems to work, but won't see any wireless networks.  If I uncheck "enable wireless" in the NM, it becomes grayed out and cannot be re-checked.

---

### Post by simosahla on 2009-11-08
> **swansong said:**
> After upgrading from 9.04 to 9.10, my Atheros (ar5212/ar5213) wireless device was not working, although it had been working before the upgrade. After hours of searching many, many websites, I found a post that mentioned "blacklist-ath_pci.conf". I typed "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf". This is what opened:

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k 

I put a "#" in front of the last line (#blacklist ath5k) saved the file, and rebooted (logging out and back in probably would have worked, but after all my searching and reading I wasn't taking any chances.)

It works.

Thanks Swansong, this works. What rules is that you can find good advice from these forums. What sucks is that you have to spend lots of time (browsing forums with my mobile, because my computer can't connect) getting basic things working again after a simple upgrade :(

---

### Post by digital-cipher on 2009-11-08
Worked a treat for me as well, cheers **BlueJeep**

---

### Post by robbi60 on 2009-11-08
I have an Atheros Communications Inc. AR5001 Wireless Network Adapter. It was perfectly working with kubuntu 9.04. After the upgranding and some various attempts (like commenting out the blacklist etc...) it is working in the sense that it is up and I can see many routers around me, but NOT my router (*Conceptronic* C54BRS4A 802.11g Wireless Broadband *Router*). I tried to change using the gnome network applet but the main problem is that, even if my router is just 1 meter far from my laptop, I don't see it if I make a scan:
> sudo iwlist wlan0 scan
I just see 5 other routers (protected unfortunately). The router is working (another PC is connected and working).
Any ideas? Best. r

---

### Post by SatelliteUser on 2009-11-08
> **emanueleg said:**
> 
[LIST=1]
[*]open a terminal
[*]type: sudo gedit  */etc/modprobe.d/madwifi.conf*
[*]wherever you can see a line like "blacklist ath5k" (there could be zero, one ore more lines like this), put a '#' in front of it; it should become
#blacklist ath5k
[*]save and close the text editor
[*]type: sudo gedit */etc/modprobe.d/blacklist-ath_pci.conf*
[*]repeat point 3 and 4
[*]restart your system and cross your fingers :-)
[/LIST]
ciao

emanuele


Cheers Emanuele, worked a treat. :D Just need to get my AC97 sound working now. #-o

---

### Post by ammar_ahmed3000 on 2009-11-09
Pleeeeeeeeeeeeeeeeeeeeeeese help
i am new in ubuntu i heve install ubuntu 8.10 then upgrade to 9.04 now 9.10
on hp 530 put wirless never work on ubuntu
the device is 
PRO/Wireless 3945ABG [Golan] Network Connection
any help plzzzzzzzzzzzzzzz

note:- when i press wlan buton it's not lit

---

### Post by Ragi on 2009-11-09
Bymyself I'm using atheros 5001 and had same problem, couldn't connect to internet via wireles in 9.10. But after abit search I found this: [http://dimitar.me/?p=616](http://dimitar.me/?p=616) and it got work on me instantly. :)

---

### Post by ammar_ahmed3000 on 2009-11-11
any help for
PRO/Wireless 3945ABG [Golan] Network Connection

---

### Post by mer.man on 2009-11-13
OK, I'm going out of my gourd....

Just did an update with update manager and now my wireless died.  WTF?  It was working FINE before the update running under the ath5k, not madwifi.

I'm running 9.04 on and AspireOne ZG5. Atheros AR5BXB3.

I've tried the various blacklist options in this thread and that got me nowhere.

Any help would be VERY appreciated.

---

### Post by warroomcbw on 2009-11-14
> **SuperSonic4 said:**
> Madwifi has largely been replaced by the ath5k driver for atheros

What is the output of ```
sudo modprobe ath5k
```


I just did this...and all of a sudden my wifi started working......?????
FYI

~$ sudo modprobe ath5k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

typed it in, and the notification that I was connected came on!

---

### Post by warroomcbw on 2009-11-16
> **SuperSonic4 said:**
> Madwifi has largely been replaced by the ath5k driver for atheros

What is the output of ```
sudo modprobe ath5k
```

what does this mean?  wifi life was short lived.



WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by whenelvisdied on 2009-11-28
Hey all,

Somehow, through a series of steps I can't reproduce, I was able to get the madwifi trunk drivers to work on my D-Link DWL-G520 Wireless card (Atheros AR5001X+).  

The recent kernel upgrade that just went through (31-14 -> 31-15, I believe) killed whatever it is that I did, so I tried to recompile the madwifi drivers.  I get ath0 visible in iwconfig, and a list of wireless connections in NetworkManager.  However, it will only intermittently connect, and when it does and I open up a browser or anything else, I get nothing.  No connection, no loading any content. 

Strangely, when I tried to use the ath5k driver (which had NEVER worked before), I now get a connection, albeit one that is freakishly slow and one that will occasionally drop.  It takes a while to connect, and  I get some version of the following, repeated over and over in dmesg while I wait:

> [ 1419.135922][ 1419.135922] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 1)
[ 1419.332056] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 2)
[ 1419.532084] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 3)
[ 1419.732059] wlan0: authentication with AP 00:24:b2:15:b5:02 timed out
[ 1424.886003] wlan0: direct probe to AP 00:24:b2:15:b5:02 (try 1)
[ 1425.084043] wlan0: direct probe to AP 00:24:b2:15:b5:02 (try 2)
[ 1425.180676] wlan0: direct probe responded
[ 1425.180688] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 1)
[ 1425.380078] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 2)
[ 1425.580043] wlan0: authenticate with AP 00:24:b2:15:b5:02 (try 3)
[ 1425.780267] wlan0: authentication with AP 00:24:b2:15:b5:02 timed out



When it does connect, Google loads in approximately 20-25 seconds from start to finish (before it had taken 2-3) and you don't want to know how long it took to load this reply page.... Also, my "speed" seems to change randomly from 54 mb/s to 1 mb/s, depending upon when I do iwconfig, or look at "connection information" in NetworkManager. 


What the heck is going on?

---

### Post by drpjkurian on 2009-11-28
Hi Guys
Those who are having problems in installing Madwifi, Please visit my thread and solve it. Madwifi is a robust drivers for Atheros card. I am using it since Hardy heron. No glitches so far.
The thread is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck

Dr Kurian

---

### Post by jajodo on 2009-11-29
> **drpjkurian said:**
> Hi Guys
Those who are having problems in installing Madwifi, Please visit my thread and solve it. Madwifi is a robust drivers for Atheros card. I am using it since Hardy heron. No glitches so far.
The thread is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck

Dr Kurian
Tried for hours to straighten this bug out until cured by Dr Kurian's link.
THANK YOU!
Had wifi connection but virtually no throughput and frequently dropped.
The Ath5k driver simply is not stable for the AR5211 in my Asus EeePC 1000HA.
Madwifi fixed the problem.

---

### Post by drpjkurian on 2009-11-29
> **jajodo said:**
> Tried for hours to straighten this bug out until cured by Dr Kurian's link.
THANK YOU!
Had wifi connection but virtually no throughput and frequently dropped.
The Ath5k driver simply is not stable for the AR5211 in my Asus EeePC 1000HA.
Madwifi fixed the problem.

Hi Jajodo
You are most welcome. I am happy to hear that your wireless is back to life.

With regards
Dr Kurian

---

### Post by mdeschane on 2009-12-26
No joy for me. I just installed 9.10 on my EEE PC 1000H and everything works except the wifi. It was working in 8.04 and I just checked again and both Widows and the 8.04 installs are working fine. When I try to "Connect to Hidden Wireless Network" in NetworkManager the connect button is greyed out. 

I haven't tried the madwifi route yet, and I don't want to if the ath5k and 9k drivers are suppossed to work or there is something else I can try.

Any suggestions would be appreciated.

mike@mikey:~$ sudo lshw -C network
 ...
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:77:7c:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fbef0000-fbefffff


mike@mikey:~$ sudo modprobe -l ath*
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath.ko

mike@mikey:~$ cat  /etc/modprobe.d/blacklist-ath_pci.conf
...
# or the other. (Ubuntu: #315056, #323830)
# blacklist ath_pci

mike@mikey:~$ tail /var/log/syslog
...
Dec 26 15:20:28 mikey wpa_supplicant[941]: CTRL-EVENT-SCAN-RESULTS

---

### Post by Eric Lathrop on 2010-01-01
> **joelmezzanotte said:**
> Anecdotal evidence but  if you are having random disconnections/slow unusable connectivity using the  0.9.4 madwifi driver seems to have corrected the issue for me.

[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)

My link is up at 11mbps as opposed to 1mbps. 


Thanks so much! I actually tried installing madwifi from another post, but I used the trunk version, and I had the same speed issues. **After installing 0.9.4 instead of the trunk**, the speed issue has cleared up! 

I hope ath5k fixes this in the next version, because dealing with this is a pain in the neck, even for an experienced user!

---

### Post by rfay on 2010-02-13
I was successful with my Sony F-Series using the instructions in this post: [http://forum.notebookreview.com/showthread.php?t=448894&page=228](http://forum.notebookreview.com/showthread.php?t=448894&page=228)

The gist was: Install the linux-backports-modules-wireless-generic package.

---

### Post by kmiernik on 2010-02-21
I have Atheros AR5001X+ PCI wifi card. It won't go with ath5k driver so blacklisting should stay in place. It went on smoothly with ath_pci driver. If you experience problems and uncommenting ath5k don't work, try
sudo modprobe ath_pci

---

### Post by DLNoob on 2010-02-24
I recently did a bare-metal install of Karmic on my Toshiba Sattelite A40 with Atheros wireless card. Wi-Fi worked fine, then I ran the recommended updates and Knetwork manager started dropping the connection after the system was suspended (sleep/hibernate). Switched to Madwifi and WICD, and that seemed to work for a bit, then the connection started dropping again, but this time I couldn't see any networks at all. WICD had stopped communicating with the Atheros card. 
 
I tried the blacklist edit for ATH5K and the Madwifi backport update without success. Just for kick ran:
 
sudo iwtlist ath5k -scan
 
and discovered that the wireless card was not even on WLAN0 like WICD expected, but on ATH1. Switched the setting in WICD and got my networks back. Now I'm really hoping it stays stable.

---

### Post by shaijujanardhanan on 2010-04-11
@swansong 
Hi nice solution.my adapter started wotking:lolflag:

---

### Post by kimitj on 2010-04-13
I followed the steps in swansongs post and everything works now!

:)

---

### Post by Kieran.s on 2011-01-21
Swansong... almost a year on and still absolute magic. Cheers

---

