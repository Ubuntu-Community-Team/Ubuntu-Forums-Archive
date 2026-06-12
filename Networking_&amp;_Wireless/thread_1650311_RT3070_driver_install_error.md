---
title: "RT3070 driver install error"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by micako on 2010-12-21
Hi all. I am trying to install this driver in ubuntu 10.10 for a week. 
I am getting this error when I type {sudo make} 


cimi@cimi-pc:/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO$ sudo make
make -C tools
make[1]: Entering directory `/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/tools'
/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux/Makefile
make -C /lib/modules/2.6.35-23-generic-pae/build SUBDIRS=/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make[2]: *** No rule to make target `/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux/.c', needed by `/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux/.o'.  Stop.
make[1]: *** [_module_/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make: *** [LINUX] Error 2

this is the last driver in ralink website.The built-in driver works but don't recognize my chipset and i wanna install this driver.
my url card is levelone wua-0603 usb [http://www.wikidevi.com/wiki/LevelOne_WUA-0603](http://www.wikidevi.com/wiki/LevelOne_WUA-0603)/.

---

### Post by chili555 on 2010-12-21
> The built-in driver works but don't recognize my chipsetI don't understand. Can you please explain?

Do you have *build-essential* installed? It makes without error for me, however, I am not using the pae kernel.

---

### Post by micako on 2010-12-21
When I type iwconfig in shell that tells chipset=unknown and not rt3070 or rt2870.
Yes I have built esetial installed.

---

### Post by chili555 on 2010-12-21
Please post:```
lsusb
iwconfig
```Thanks.

---

### Post by micako on 2010-12-21
cimi@cimi-pc:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04b4:0060 Cypress Semiconductor Corp. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 045e:0761 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  


cimi@cimi-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-12-21
I don't see anything here that looks like a Ralink wireless device. What make and model is it?

---

### Post by micako on 2010-12-21
my url card is levelone wua-0603 usb [http://www.wikidevi.com/wiki/LevelOne_WUA-0603](http://www.wikidevi.com/wiki/LevelOne_WUA-0603)/.

---

### Post by chili555 on 2010-12-21
> **micako said:**
> my url card is levelone wua-0603 usb [http://www.wikidevi.com/wiki/LevelOne_WUA-0603](http://www.wikidevi.com/wiki/LevelOne_WUA-0603)/.I still don't understand why it doesn't show up in lsusb. Is it plugged into the hub? Can you try another USB slot?

---

### Post by micako on 2010-12-21
cimi@cimi-pc:/etc/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 004: ID 04b4:0060 Cypress Semiconductor Corp. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 045e:0761 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2010-12-21
> [COLOR="Red"]148f:3070[/COLOR] Ralink Technology, Corp. RT2870/RT3070 Wireless AdapterYour device should work with rt2870sta, as per modinfo:```
$ modinfo rt2870sta | grep 3070
description:    RT2870/RT3070 Wireless Lan Linux Driver
firmware:       rt3070.bin
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```It is also claimed by rt2800usb. Let's blacklist it and its dependencies.```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and give us your report.

By the way, compiling a new module would not have helped the driver conflict.

---

### Post by micako on 2010-12-21
Thanks for your help. can you tell me something. please type in shell "sudo airmon-ng" and show me the results please.
if you have this card !

---

### Post by chili555 on 2010-12-21
> **micako said:**
> Thanks for your help. can you tell me something. please type in shell "sudo airmon-ng" and show me the results please.
if you have this card !```
$ sudo airmon-ng
[sudo] password for chili: 
sudo: airmon-ng: command not found
```Probably not the result you were expecting. I don't have airmon-ng installed. I also don't have that card.

I suggest we get the wireless working and then you can post another thread about airmon-ng based on a working wireless card.

---

### Post by micako on 2010-12-21
thank you my friend. the card is working. 

here is my results when i type airmon-ng

cimi@cimi-pc:~$ sudo airmon-ng


Interface    Chipset        Driver

wlan0        Unknown         usb

the problem is the chipset is unknown

---

### Post by chili555 on 2010-12-21
I think you need to post a new thread and reference airmon-ng. That is not a package I have any experience with.

---

### Post by Zeno Cosini on 2011-02-06
I have the same problem as micako: My Ralink USB wireless adapter does not work. I followed the advice given by chilli555 and extended blacklist.conf. Unfortunately, this did not solve the problem for me. The NetworkManager Applet still shows that the "wireless is disabled", and the "Enable Wireless" option is grayed-out. 

What do I need to do to enable wireless connection with this adapter? :confused:

Here is the output of lsusb:

```
Bus 006 Device 002: ID 413c:8138 Dell Computer Corp. Wireless 5520 Voda I Mobile Broadband (3G HSDPA) Minicard EAP-SIM Port
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 008: ID 1028:0204 Inovys Corp. 
Bus 001 Device 007: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 001 Device 006: ID 413c:9001 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Here is the output of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Please help!

---

### Post by TBABill on 2011-02-06
You may also need to ```
gksudo gedit /etc/modules
``` and add ```
rt2870sta
```to the end, then restart. Hopefully that works for your card.

---

### Post by Zeno Cosini on 2011-02-06
Thanks a lot for your help. Unfortunately, nothing has changed. The output of lsusb and iwconfig is as before, and the wireless is still disabled, with the "Enable Wireless" option grayed-out in the NetworkManager Applet.

---

### Post by noob.bot76 on 2011-03-19
I'm having a similar problem and would appreciate any updates or help. I have done both the "blacklist" suggestion and the the "gedit...modules" suggestions. 

This is my current Terminal readout:
[noparse]XXXX: iwconfig
lo        no wireless extensions.

wlan0     802.11bg  ESSID:"2WIRE296"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:56:14:50:31   
          Bit Rate=24 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=65/100  Signal level=-72 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-79 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

~~~~~~~[/noparse]

The device is recognized under my wireless icon -- when I click the wireless icon in the toolbar, "RALink 802.11 n LAN" is listed as a wireless connection. 

When I reboot with the USB Antenna plugged in, my computer attempts to connect via the RALink device -- but won't connect. I've gotten requests for passwords; entered my wireless network password, but this did not work. I have to disconnect the device in order to connect to the internet. 

One difference from the above posts, is that when I type "lsusb" I get only: 
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp.  

There is no listing of 2870, and no RT. 

Many thanks

---

### Post by noob.bot76 on 2011-03-19
sorry, but i don't know why my Terminal readout has emoticons -- please be patient, I'm a newbie :)

---

### Post by howefield on 2011-03-19
> **noob.bot76 said:**
> sorry, but i don't know why my Terminal readout has emoticons -- please be patient, I'm a newbie :)

Use noparse /noparse tags to stop emoticons appearing in your terminal output.

---

### Post by noob.bot76 on 2011-03-19
bump

perhaphs i should start a new thread?

thanks howfield -- now if i only knew what that meant! lol

i'll try to figure it out.

---

### Post by noob.bot76 on 2011-03-19
my readout without smileys:
[noparse]lo        no wireless extensions.

wlan0     802.11bg  ESSID:"2WIRE296"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:56:14:50:31   
          Bit Rate=24 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=65/100  Signal level=-69 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

wlan1     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-59 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/noparse]

---

### Post by chili555 on 2011-03-19
I am quite sure Network Manager is stumbling over two wireless cards. Why do you want that? Some kind of hacking/cracking/injection nonsense?> One difference from the above posts, is that when I type "lsusb" I get only:
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp.

There is no listing of 2870, and no RT.
Perfectly normal.

Anything interesting in:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by noob.bot76 on 2011-03-19
believe me, i'm not trying anything as exotic as "hacking and cracking" -- I simply don't know what i'm doing!

I've been searching through Ubuntuforums trying to find different install directions for RALink drivers, etc. 

I've just now tried the directions here: [http://ubuntuforums.org/showthread.php?t=1476007&highlight=ralink+install+driver+bz2](http://ubuntuforums.org/showthread.php?t=1476007&highlight=ralink+install+driver+bz2)

But I got stuck on step 6: there is nothing in any of my file names that end in a ".ko". In my file name, after 'sta' comes "v2_2.5.0.1_DPO"

Anyhow, something seems to have happened. My ordinary/old wireless connection name disappeared from my wireless connection, but then reappeared under wireless connection "RALink 802.11...etc." My old signal strength was about 62%. I am now **inconsistently** getting 85% -- but it fluctuates wildly -- down to as low as 45% -- usually right after opening a new window etc. 

Here is my current iwconfig readout: 
[noparse]lo        no wireless extensions.

wlan1_rename  802.11bg  ESSID:"2WIRE296"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:56:14:50:31   
          Bit Rate=24 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"2WIRE296"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:56:14:50:31   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=83/100  Signal level:-77 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[noparse/]

thanks for your help

---

### Post by noob.bot76 on 2011-03-19
sorry, i don't know why my noparse tags didn't work

---

### Post by noob.bot76 on 2011-03-19
i didn't reply to the second part of you post. 

here is what i get when for the command dmesg | grep -e rt2 -e rt3



[   13.934955] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.094438] usbcore: registered new interface driver rt2870

anything that includes "you have been warned" sounds bad to me, lol, but what do i know

---

### Post by chili555 on 2011-03-19
Ahem. Why do you have two wireless cards? What about the Realtek made you say to yourself, "By golly, noob.bot, let's go down to the store and buy a Ralink and torture ourselves learning to compile a driver THAT"S ALREADY IN THE KERNEL." What, pray tell?

Can't we tune up the Realtek and give the pesky Ralink to our ex-wife's lawyer?

---

### Post by noob.bot76 on 2011-03-19
LOL -- love the dry sarcasm, really. 

You have to keep in mind that I have NO IDEA what I'm doing. I wasn't trying to buy a second wifi card, but a wifi "booster". The reviews of the product described going from one bar to three bars, etc. And one reviewer said the install with Ubuntu 10.10 was a "plug and play" breeze. I've since learned otherwise. 

Here is the product: [http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_1?ie=UTF8&qid=1300564779&sr=8-1](http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_1?ie=UTF8&qid=1300564779&sr=8-1)

So...have I screwed up my system or networking abilities?? I don't suppose there's an "undo" button. 

Any advice and help is appreciated. Many thanks.

---

### Post by chili555 on 2011-03-19
Let's get the Realtek to stop interfering. Find out what driver it's using:```
lsmod | grep r819
```Whatever it is, blacklist it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist r819whateveryoufound
```Proofread, save and close gedit.

Now, let's see what drivers are running the Ralink:```
lsmod | grep rt2
```Post the mess you find and let's go from there. Reboot while you wait for my reply to your next post.

---

### Post by noob.bot76 on 2011-03-19
Here is everything that comes out from the commands you listed:
[noparse]bazja@bazja-laptop:~$ lsmod | grep r819
r8192se_pci           447966  0 
bazja@bazja-laptop:~$ sudo gedit /etc/modprobe.d/blacklist.conf
[sudo] password for bazja: 
bazja@bazja-laptop:~$ lsmod | grep rt2
rt2870sta             461811  1[noparse/] 

I added to the blacklist list in gedit; but I had previously added lines to my blacklist list (from another one of your posts I believe); so I'm included every blacklist line that I've added: 
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
blacklist r8192se_pci           447966  0 

Should those last numbers be included?? 

Jeez, I feel should buy you a beer or something for all this help. Maybe they should start up a "newbie payback corner" so we can repay all the gurus on here. Anyways, :cheers:

---

### Post by chili555 on 2011-03-19
> Should those last numbers be included?? Nope. Amend it to remove the highlighted part:```
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
blacklist r8192se_pci [COLOR="Red"]447966 0[/COLOR] 
```Otherwise it looks just fine. So how is wlan0 running now? Can you connect at expected speeds?> I feel should buy you a beer or something for all this help.I work for the joy of someone posting that it works and they're happy. Of course, if you wanted to make a contribution to disaster relief in Australia, New Zealand or Japan, I wouldn't be displeased.

---

### Post by noob.bot76 on 2011-03-19
Okay, superfluous numbers deleted. 

Wifi connection is showing 80-90%, but is still fluctuating. Sometimes, so far, it dips down to 52%. Of course, I've never been quite this attentive to wifi connection percentages. 

Donation to Relief International made in your name -- i.e., "Chili555". You should receive an email confirmation at Yahoo -- though I can't be sure since I couldn't use your real name. 

Does all this tinkering mean that I can't connect wirelessly without this new usb card? That kinda blows. Or does it mean, that when the usb card is recognized (plugged in), it has a "priority"? That would be cool. (Sorry for my non-techy language) 

Lastly, Ubuntuforums is officially awesome. And, just so you know, this is quite fun for me even though I'm just beginning -- hope that brings you some reward.

---

### Post by noob.bot76 on 2011-03-19
Update:
tried to watch a video on Amazon -- my ongoing nemesis. Couldn't get video to stream. Wifi connection dipped to 38%:confused:

---

### Post by chili555 on 2011-03-19
> Does all this tinkering mean that I can't connect wirelessly without this new usb card? Yes, unless you reinsert the r8192se_usb module:```
sudo modprobe r8192se_usb
```> this is quite fun for me even though I'm just beginning -- hope that brings you some reward. Quite a lot; it's fun for me, too.

Have you tried different channels in your router? By default, most are set to channel 6, the same as cordless phones, dimmers, microwaves and all kinds of interfering gadgets. I have better luck on channel 11 and somewhat better on channel 1.

Does your router have a setting for power? Is it at maximum? Please see attached.

I am very grateful for your thoughtful contribution. Many spots in the world need a bit of help. I'll give up a few beers and I'm happy to see that you will, too.

---

