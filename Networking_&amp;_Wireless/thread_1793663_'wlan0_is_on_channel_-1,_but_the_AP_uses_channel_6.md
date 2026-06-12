---
title: "'wlan0 is on channel -1, but the AP uses channel 6' with airplay-ng"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by kexus on 2011-06-29
So, I'm trying to crack my wep password just for kicks, but I keep running into the same error.  When I try to use airplay-ng for the packet injection, it always gives me the error 
" wlan0 is on channel -1, but the AP uses channel 6".  I've tried setting wlan0 to channel 6 manually, but that doesn't help.  I spent a while searching for a solution, but it seemed like each page had a different, usually highly complex solution, that still doesn't work.  I have the most recent drivers for my wireless card, and it meets all the requirements. So, is there any solution to this that will actually work?

---

### Post by TechSupportx86 on 2011-06-29
lol, i love airplay-ng :)

Most of the time this is due to using airplay-ng on an ubuntu machine with network manager installed (basically if gnome is installed, it's hard to work with).

Since you need airplay-ng to control what channel the NIC uses, you either need to disable network manager (which is a pain) or use back|track (i prefer backtrack). I would either install ubuntu server edition, OR download and burn backtrack to a CD so you can boot from it (it's a live CD). It has airplay-ng and aircrack-ng pre-installed, and many other useful wifi auditing programs...

[COLOR=Red]Please note, the above advice is given under the assumption that this is for personal use only, or for an authorized wireless security audit. [/COLOR]
[SIZE=1](I don't care either way, but the TOS might have something else to say about it ;))[/SIZE]

Also i have alot of experience with backtrack and the entire "air" suite. If you need help with anything else, feel free to PM me.

---

### Post by kexus on 2011-06-30
I think I'll try using a Backtrack live cd. Thanks for the advice.

---

### Post by Dangertux on 2011-06-30
I don't think that Back Track is gonna help you in this case ; since the reason this happens is because you're using the commands wrong. 

aireplay-ng is going to take it's channel setting from the original airmon-ng interface you created. So if you started airmon-ng on channel 3 for mon0 and you are trying to inject on channel 6 with mon0 it's probably not going to work. 

Hence you're probably seeing a warning something along the lines of Fixed Channel : 1

Does that make sense?

P.S: Back Track is actually a LiveDVD ;-)

---

### Post by TechSupportx86 on 2011-07-01
Where does it show what command he is running? If it's tellig him "wlan0 is on channel -1, but the AP uses channel 6" this is most likely due to the fact that network manager is running. I am assuming he is trying to run this command on ubuntu (seeing as how this is ubuntuforums.com), which is possible, but to much trouble than it's worth. I know because i tried it, had this problem, and went back to backtrack.

Using backtrack will solve this issue as there is no network manager and will allow you to put your device into monitor mode and allow you designate channels.

If you don't think this is the problem, then please install aircrack-ng on your ubuntu machine and try cracking your network, you will get the same error.

---

### Post by Dangertux on 2011-07-01
Don't be so touchy, I am suggesting something. It may be because of several things.

1 - It is possible nm is causing a problem (but this will usually only occur when there is also a connection on a different channel)

2 - The commands were issued wrong.

3 - He does not have injection capable drivers

4 - Any various sundry of other 802.11 magic that can occur.

So like I said I'm FAIRLY certain this is the issue, he likely missed the channel when he was configuring airodump-ng OR when he put it in monitor mode with airmon-ng

I also assure you this works fine for me on both Ubuntu AND Back Track. 

Additionally : This will slow down the attack but you can use the --force-ignore-negative-1 option in aireplay-ng ;-)

So I ask again why so touchy? I'm not downing Back Track, it's useful for what it is, I use it quite regularly, however I'm trying to save the guy 2 1/2 hours of downloading a LiveDVD just to figure out he typed his command wrong. 

You can also remove nm from Ubuntu and install Wicd which btw IS the network manager that comes with Back Track, so saying there isn't a network manager, is a false statement. Additionally, his error really has nothing to do with "cracking" his network, since aircrack-ng can be used entirely off line. Either with a wordlist or bruteforcer such as john the ripper in the case of WPA or you can crack WEP online using aireplay or offline using aircrack if you'd like. His problem is coming in where he is not going to capture either the handshake (if WPA) or anywhere near enough IV's if WEP.

P.S : Back Track is based on Lucid...

---

### Post by Dangertux on 2011-07-01
Works fine on my Ubuntu install btw ;-)

Verified it just for you guys.

---

### Post by pannet1 on 2011-07-01
hello,

i run the following scripts

#terminal 1
airmon-ng stop wlan0
airmon-ng stop mon0
ifconfig wlan0 down
ifconfig eth1 down
macchanger --mac 00:11:22:33:44:55 wlan0
service network-manager stop
service upstart-udev-bridge stop
service avahi-daemon stop
killall -9 wpa_supplicant
airmon-ng check kill wlan0
airmon-ng start wlan0 1

#terminal 1
airodump-ng --channel 1,1 --encrypt wep -w /media/data/3linux/scripts/aircrack/dummy mon0

i am getting the same error. what am i doing wrong. i installed backports as well. tried compiling wireless-compat but i have an error. btw am i doing any mistake with my commands. why its always channel -1 that wlan0 is monitoring.

can you please help. thanks.

---------------
running ubuntu maverick
alfa usb wifi (rtl chipset)

---

### Post by Dangertux on 2011-07-01
Usually the reason for the forced channel -1 is because of a connection to another network. 

In your case that doesn't seem to be the issue. Try the following 

Try stopping network manager prior to bringing down the interface. 

If that doesn't work try the --force-ignore-negative-1 option though it might still fail.  I honestly don't have the problems you guys are having with nm. Also make sure you're only running one instance of airodump. That is really all I can think of.

---

### Post by kexus on 2011-07-01
Thanks for the help guys. I'm almost positive the problem is with the network manager, not my wireless card (which can do injections), or the commands I'm using, since I've been following a tutorial. What do you think would be easier, disabling the network manager, or just using Backtrack?
Would running Backtrack as a VM using VirtualBox work just as well as booting into it?

---

### Post by kexus on 2011-07-02
I'm going to try this on backtrack and see if it works.

---

### Post by kexus on 2011-07-02
Its magically working now.  I tried it on Backtrack, and it wouldn't work, but when I went back to Ubuntu, it worked fine. No clue why.

---

### Post by Dangertux on 2011-07-02
Ok, I totally forgot about this thread sorry :-P

But -- What worked? I guess you edited it out of your post? 

As far as Back Track vs Ubuntu, that is entirely up to you particularly if you can make it function in the way you want on either (I think? not really clear on if you got it working in ubuntu or back track or both lol).

Back Track offers a lot of different tools, mostly for professionals, however if it's something you're interested in learning about I would give it a whirl. With the caveat that pen-testing systems that don't belong to you or you don't have permission to is illegal.  If you just want it for the aircrack aspect, and it's working on Ubuntu I wouldn't bother having a whole different OS just for aircrack, or if I did I would set up a live usb drive.

As far as BT in a VM that works fine as well, that's the way I use it at work. If you do it that way it makes it really easy to set up your own lab, to test out code you write, you can just run your VM's on one system and set them up to be vulnerable in order to test out your code. Saves you the problem of looking for targets, which is slightly less then moral or legal lol.

Honestly it's up to you though.

---

### Post by Raf99 on 2012-01-22
I just wanted to write in and give the answer to this for anyone who may need it. Before you set the NIC into monitor mode, and before you kill the network manager you need to disconnect from any APs and set the channel:

sudo iwconfig wlan0 channel 1

Then turn off the network manager and enable monitoring on the NIC (kill any processes it comes up with that may get in the way).

sudo airmon-ng start wlan0 1

Now you are safe to run airodump-ng and aireplay-ng in separate term windows.
The order matters here as well.

Cheers

---

### Post by jao_madn on 2012-02-08
hi,  in addition i had a asus laptop with wireless N intel nic and fine using injection in my lucyd64, in my experience before my lucyd32 has the same problem, tried in backtrack 5, with --ignore-negative-one option works fine, now when i switch to lucyd64 its working fine, i tried it in oneiric, precise and show the same error..  Now im working in my TP-Link TL-WN821N USB in my desktop with atheros chipset with the same problem..I believe its in my ath9k_htc driver problem. I will try it in backtrack soon..  

as of 2012-02-08
In addtion i fixed this problem in my Desktop using TP-Link TL-WN821N USB wirelessN adapter using the procedure found in this furom [Link]("http://ubuntuforums.org/showthread.php?t=1598930"). Had some modification in the compat driver instead of using compat-wireless-2010-10-16.tar.bz2 i used compat-wireless-2.6.39-1.tar.bz2 since this driver make my wireless function normally and compile with no error. Other driver won't compile even with out patch yet.

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2 
tar -jxf compat-wireless-2.6.39-1.tar.bz2
cd compat-wireless-2010-10-16 
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch 
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch 
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch 
patch ./net/wireless/chan.c channel-negative-one-maxim.patch 
gedit scripts/update-initramfs 
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build 
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build 
make 
sudo make install 
sudo make unload 
sudo reboot
```Heres are my system details:
TP-LINK TP-WN821N Usb wirelss N adapter
Lucyd 64bit with 2.6.32-37-generic kernel
ath9k_htc module driver
```
 lsmod | grep ath9k
ath9k_htc              53695  0 
mac80211              292125  1 ath9k_htc
ath9k_common            3465  1 ath9k_htc
ath9k_hw              325638  2 ath9k_htc,ath9k_common
ath                    17105  2 ath9k_htc,ath9k_hw
cfg80211              176656  3 ath9k_htc,mac80211,ath
compat_firmware_class     7600  1 ath9k_htc
compat                  9773  4 ath9k_htc,mac80211,cfg80211,btusb
led_class               3764  2 ath9k_htc,compat

```

---

### Post by TheStrategist on 2012-07-27
Also for anyone wondering, network manager can be temporarily disabled  and re-enabled for use of aircrack-ng in Ubuntu by use of the following  command:

```
sudo service network-manager stop
```Then re-enabled just as easily by using:

```

sudo service network-manager start
```This will allow for you to get he job done without having to worry with uninstalling or switching distros.

---

### Post by jjxcrunner on 2013-06-12
I set up my original airedmp to be set onto channel 10 and for the BSSID of 00:1D:7E:6D:18:AA

So when I started it up it looks like this

CH 10][ Elapsed 21 mins ][2013-06-12 ][fixed channel mon0: -1


But I never set the mon0 channel, only the wlan0 channel to channel 10.

I keep getting the same message no matter if I try wlan0 or mon0 they all say alan0 is on channel -1, but the AP uses channel 10.

---

