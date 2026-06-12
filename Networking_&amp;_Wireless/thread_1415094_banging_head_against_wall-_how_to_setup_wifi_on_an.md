---
title: "banging head against wall- how to setup wifi on an Inspiron 9300?"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by BastardNamban on 2010-02-24
I've had 8.04 for almost a year & a half now, but the one thing that seems to confuse me after getting the rest of ubuntu is how to get wifi working.

Before you say "read XXX FAQ, wiki, page", etc, I've read so many and despite understanding every normal thing about ubuntu, and all the customization I have, I haven't seen a single, up-to-date guide for making sense of wifi.

Here's what I know:

My wireless card is Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05), supported in linux only by using a windows driver, ipw2200, which I do have running and installed somehow.

```
shogun@Valhalla:~$ sudo lsmod | grep ipw2200
[sudo] password for shogun: 
ipw2200               146248  0 
ieee80211              35528  1 ipw2200

```

I also realized I needed ndiswrapper, so I installed that. Beyond this, I'll just admit it- I'm very confused. I have always had a working connection over ethernet cable plugged in, but I really need wireless lately, and found an old Netgear WGR614v7 G band wireless rounter in my basement, hooked it up, and have a wired connection from it right now.

So how do I set-up/get my wireless working with all this thus far? How do I set up the router's network through Ubuntu as well, so I can create a named network to connect to? I'm reading every guide I can, and am just coming up more confused.

---

### Post by chili555 on 2010-02-24
ipw2200 is the native Linux driver, not the Windows driver. If you open a terminal and do:```
iwconfig
```Do you have a wireless interface, eth1, perhaps? When you detach the ethernet cable and click the Network Manager icon, do you see networks? What happens when you click your network? Does it ask for WEP or WPA details and try to connect?

---

### Post by BastardNamban on 2010-02-24
> **chili555 said:**
> ipw2200 is the native Linux driver, not the Windows driver. If you open a terminal and do:```
iwconfig
```Do you have a wireless interface, eth1, perhaps? When you detach the ethernet cable and click the Network Manager icon, do you see networks? What happens when you click your network? Does it ask for WEP or WPA details and try to connect?

The output of iwconfig: ```
shogun@Valhalla:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

And when I unplug the ethernet cable, and click the network manager, nothing comes up, ie, no networks are shown. When physically connected, it says I'm connected to a wired network with a selected circle icon.

Originally, this laptop had XP on it when I bought it, and there was an app from Dell to turn on or off the wireless card at will. I'm wondering if there's a way to do that again- as that output is saying "radio off", as if there were a way I could turn it on...

---

### Post by chili555 on 2010-02-24
> there was an app from Dell to turn on or off the wireless cardPlease try an experiment for me. Open a terminal and do:```
rfkill list
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Now do you see networks?

---

### Post by Onesimus on 2010-02-24
You could try a number of different things:

[LIST=1]
[*]Check in the BIOS that the wireless is switch on.  
[*]Check that there is no physical button/switch on the outside of the laptop (I spent two evenings trying to get my wife's laptop to work only to find a physical switch on the outside of the machine - once in the on position everything worked fine !)
[*]Upgrade to Karmic Koala - it may be that this could fix your wireless problem.  I would recommend trying the LiveCD option before you do a re-install.
[*]Wait until Lucid Lynx comes out in April
[/LIST]

Hope some of this helps.

---

### Post by BastardNamban on 2010-02-24
Nope. This is what I got: ```
shogun@Valhalla:~$ rfkill list
bash: rfkill: command not found
shogun@Valhalla:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory
shogun@Valhalla:~$ sudo rfkill unblock all
sudo: rfkill: command not found

```

I'm sorry, I know helping people like me must be like hitting yourself in the face with a hammer repeatedly. There's something simple that I should know and whatever it is, I don't. I wish I knew what I'm doing wrong...:(

And I'm waiting for Lucid to come out indeed, I won't bother with Karmic- I'm going to stick to LTS versions only. Maybe I'm stubborn- I want to keep the same OS and familiar interface as long as possible.

---

### Post by chili555 on 2010-02-24
> like hitting yourself in the face with a hammer repeatedly.Indeed; only because it probably is very easy...except I haven't *quite* figured it out yet. Let's try something else:```
dmesg | grep -e ipw -e eth
```Let's see what's going on under the hood.

Does the wireless button and switch have no effect at all? Does the wireless LED glow or flicker?

---

### Post by gradinaruvasile on 2010-02-24
Ubuntu 8.04 doesnt have the rfkill feature. It is introduced in later kernels, 2.6.30 or so. If you have a wireless switch, the 

dmesg

command should reveal it (in a terminal).

What you CAN do is issue the following command in a terminal (make sure you are in range of your wireless network):

sudo iwlist scan

and post the results.


I would suggest upgrading to newer version of Ubuntu (maybe wait for the next stable (err.. lts) release). The 8.04 version uses a really old kernel (reported to the growth of the kernel's features), there have been tons of features and new drivers added since.
Probably your problem is already solved in Ubuntu 9.01 or 9.10. Maybe burn a live-cd or make a bootable USB stick with 9.10, boot from it and see if the wifi is working OOTB.

---

### Post by BastardNamban on 2010-02-24
Ok, here's what I got this time: ```
shogun@Valhalla:~$ dmesg | grep -e ipw -e eth
[    8.580618] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:dd:68:16
[    8.610976] Driver 'sd' needs updating - please use bus_type methods
[    8.614198] Driver 'sr' needs updating - please use bus_type methods
[   13.196302] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.196306] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.236567] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   15.519794] ipw2200: Radio Frequency Kill Switch is On:
[   15.526856] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   54.418220] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.418861] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  123.946123] b44: eth0: Link is up at 100 Mbps, full duplex.
[  123.946132] b44: eth0: Flow control is off for TX and off for RX.
[  123.949561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  124.853340] eth0: no IPv6 routers present
[  178.959689] b44: eth0: Link is down.
[  180.384833] b44: eth0: Link is up at 100 Mbps, full duplex.
[  180.384842] b44: eth0: Flow control is off for TX and off for RX.
[  180.388276] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  181.736005] eth0: no IPv6 routers present
[  971.388340] b44: eth0: Link is down.
[  980.391178] b44: eth0: Link is up at 100 Mbps, full duplex.
[  980.391186] b44: eth0: Flow control is off for TX and off for RX.
[  980.394085] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  393.837735] eth0: no IPv6 routers present
shogun@Valhalla:~$ 


```

And since I put ubuntu on this laptop, I have never seen either the wifi or bluetooth leds come on next to the power button. I just assumed they could never work again because linux wouldn't recognize them?

---

### Post by BastardNamban on 2010-02-24
```
shogun@Valhalla:~$ sudo iwlist scan
[sudo] password for shogun: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

shogun@Valhalla:~$ 

```

I am waiting eagerly for Lucid, but being that I have never updated a linux build, I have this mindset that a lot of my interface would change if I updated to a newer kernal/build. I'm willing to do that for LTS builds, but otherwise, I don't want my system changing every 6 months!

If there is a way to update my kernal while keeping most of my stuff & meticulously customized settings "the same", I will, but being new to this, I have no idea what to expect in doing so yet.

---

### Post by gradinaruvasile on 2010-02-24
I do not advise messing with custom kernels, PPAs and stuff. And make sure you do a clean reinstall with Lucid - there have been many changes on and under the OS's surface (the kernel is new, some stuff is removed, some added) and you might have a non functional system. Also beware of PulseAudio.

You might want to grab the beta Lucid bootable cdimage and boot from it to see how it looks like.

BTW the wifi and bluetooth leds should work on newer kernels (i use a Dell D630 and i have functional leds since Ubuntu 8.10).

PS. Are really sure the wireless router is working?

---

### Post by chili555 on 2010-02-24
> ipw2200: Radio Frequency Kill Switch is On:It thinks the kill switch is on; that is, that the wireless capability is turned off by the switch(es). Let's try to jump that hurdle first. Please do:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 led=1
```Now are you able to press the button and see the wireless LED react? If you can get it to come on, try scanning again. If you see networks, try to connect, after disconnecting the ethernet cable, of course.> I have this mindset that a lot of my interface would change if I updated to a newer kernal/build. I have only upgraded from 7.04 to 7.10 to 8.04, etc.; that is, every six months and I have not had any real issues. I do have a separate /home partition, however. I have never tried LTS to LTS.

---

### Post by BastardNamban on 2010-02-24
```
shogun@Valhalla:~$ sudo rmmod -f ipw2200
[sudo] password for shogun: 
shogun@Valhalla:~$ sudo modprobe ipw2200 led=1
shogun@Valhalla:~$ 

```

Nothing happened. No LED on. No wireless networks. Hopefully this is showing why I've had such a hard time getting wireless working.

BTW, there is no actual switch or button to turn on the LED or card on the outside of the laptop.

Any other ideas? And yes, the router is working- I'm taking my wired connection through it right now. So it does work wired...

---

### Post by chili555 on 2010-02-24
> there is no actual switch or button to turn on the LED or card on the outside of the laptop.Not even Fn+F2? Please see attached.

---

### Post by BastardNamban on 2010-02-24
> **chili555 said:**
> Not even Fn+F2? Please see attached.

Thank you- I forgot about that. Not an actual "button", but a set of hotkeys.

Some progress was made- my wifi LED never has come on, even after doing Fn+F2, but my network icon now shows 5 wireless networks around me. I tried toggling Fn+F2 several times, but they never go away- so I don't know if that had an effect, but my computer can indeed sense wireless networks around me. Can't connect to any of them as they have passwords.

Now assuming I've somehow "fixed" something, how can I set up a wireless network for this Netgear router? I will have to manually reset the thing to go to default passwords, but from there, I want to create a protected unique named network.

---

### Post by chili555 on 2010-02-24
I am not familiar with your actual router, however, most allow you to access the administration pages, set the ESSID to whatever you want and, most importantly, set up encryption, WPA, ideally.

Generally, you access the admin pages by hooking an ethernet cable to the router, setting your ethernet interface to a default found in the manual, generally something like:```
sudo ifconfig eth0 192.168.1.2 up
```Then open a browser and navigate to: [http://192.168.1.1](http://192.168.1.1)

The admin page will ask for the password, typically 'admin.'

The actual details are found in the manual, paper or on line.

---

### Post by BastardNamban on 2010-02-24
Ok- I reset the router, and got into the admin page. I found the manual online.

I believe we have a static IP here, and the router is asking for that, and a lot of other stuff that I don't know- IP subnet mask, Gateway IP address, primary & secondary DNS. Is there a way I can find that info to put in? I know how to lookup my IP but none of those other things, and the router won't configure without them.

---

### Post by chili555 on 2010-02-24
Generally, you can leave the defaaults, 192.168.x.y, etc. in the router. The router will probably be set up to get an external IP address automatically, that is, by DHCP, from the DSL or cable modem; however the internet is delivered to your house from your internet service provider.

Then set up the router to serve internal addresses; that is, to computers inside your LAN, by DHCP. You can probably specify the starting and ending IP address. Many routers allow up to fifty (!!!) addresses. In my LAN, six are sufficient. So you might specify a starting address of 192.168.1.100 and an ending address of 192.168.1.105.

It would greatly surprise me if your internet service provider gave you a static IP address to use, but I suppose it is possible.

Post back if you need more guidance.

---

### Post by BastardNamban on 2010-02-24
Great news- I am typing this from my kitchen. Wirelessly.

I got wireless working, and wired working, FINALLY! I just set up my router's options, named my wireless network, and set up a passphrase with WPA2 encryption.

Whatever I did in the course of this, I am wirelessly connected in linux from my Inspiron 9300. I noticed right clicking the network icon gives me options to turn on or off my wireless card or networking.

Thank you, thank you, all of you! :D

---

### Post by chili555 on 2010-02-24
That is good news. Glad it's working well for you. Enjoy!

---

