---
title: "ubuntu 9.04 wireless help"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by jg579224a on 2011-07-30
Hello everybody, I require some help, if you would be so kind it would be most appreciated.

I am running Ubuntu 9.04 as a partition with windows 7 on a acer aspire 5742, I would like to connect to the internet in Ubuntu, wirelessly, but I am unable to turn my wireless on in Ubuntu, and network manager says "no network connections available".

I have the following network adapters:

Atheros AR5B97 Wireless Network Adapter

Broadcom NetLink (TM) Gigabit Ethernet

Microsoft Virtual WiFi Miniport Adapter

---

### Post by chili555 on 2011-07-30
An Acer, you say? Please open a terminal and run and post:```
rfkill list all
lsmod | grep ath5k
```Does your Acer have a wireless switch? Does it work?

---

### Post by jg579224a on 2011-07-30
Hi, when you say a wireless switch, I have a fn key which I press and there is a wireless logo on the f3 key, I press both together to turn wireless on.

I am a total newby, I dont know how to enter that code into command prompt, I need it written down explicitly so I can type it in.

---

### Post by chili555 on 2011-07-30
Please go to Applications > Accessories > Terminal. Open it and type in:```
rfkill list all
```Press Enter. Some data will appear that will give us some clues as to what is wrong and how we may correct it. Post it here; if there is no other method, use pencil and paper. It won't be very long.

Next type in:```
lsmod | grep ath5k
```Press Enter. The pipe symbol | is on the right side of my US keyboard on the same key with \. Post that data, too.

Thanks.

---

### Post by jg579224a on 2011-07-30
I typed that in with spaces and it says "command not found"

---

### Post by jg579224a on 2011-07-30
I feel like an absolute moron

---

### Post by chili555 on 2011-07-30
It has been a long time since I ran 9.04. I am guessing that 'rfkill' was not yet a usable, valid command in that release. I'm sorry, maybe *I* should be the one feeling like a moron.

How about the second command?

---

### Post by jg579224a on 2011-07-30
When I type the second command, it doesn't return "cmd not found", it just starts a new line for me to type another command

---

### Post by jg579224a on 2011-07-30
I would have the latest version, but I need to get on line on Ubuntu first, so I can update; am I a hopeless case or can you still help me?

---

### Post by chili555 on 2011-07-30
You are not a hopeless case as long as I draw breath! Your wireless card ought to work with a driver module called ath5k. Let's try to load it and see if your wireless comes to life; or, alternatively, it spits out an error that will tell us what's wrong. Please run and post:```
sudo modprobe ath5k
```You will be asked for your password. For security purposes, it will not be echoed back; not even ****. Just enter it and press Enter. Also run:```
iwconfig
```Is there a wlan0 listing?

---

### Post by jg579224a on 2011-07-30
O.K. here is what I got:

**sudo modprobe ath5k =** 

*WARNING: All config files need.conf: /etc /modprobe.d/ndiswrapper, it will be ignored in a future release.*

**iwconfig = **

[I]lo             no wireless extenstions.


pan0        no wireless extensions.[/I]

---

### Post by chili555 on 2011-07-30
Ah, haaaa! You already tried ndiswrapper to get your wireless working. What does this tell us?```
ndiswrapper -l
```That's a lower-case L for 'list.'

If I ask you to get a full log in a big text document, can you transfer it on a USB key to post here? Please do:```
lsmod > jg57.txt
dmesg >> jg57.txt
ndiswrapper -l >> jg57.txt
lspci -nn | grep 0280 >> jg57.txt
zip jg57.zip jg57.txt
```In your user directory, you will find a file called jg57.zip. Please transfer it on a USB key and attach it to your reply using the paperclip tool at the top of the reply box.> I have a fn key which I press and there is a wireless logo on the f3 key, I press both together to turn wireless on.When you press Fn+F3, does the light go on and off as expected?

---

### Post by jg579224a on 2011-07-30
O.K. I will send this in parts, as it is too big to send in one go

alex@alex-laptop:~$ ndiswrapper -l RETURNED :

net5211 : driver installed

---

### Post by jg579224a on 2011-07-30
When I press FN+F3 the light does NOT go on as expected.

P.S.  your being extremely helpful, I cant thank you enough.

---

### Post by chili555 on 2011-07-30
Back after supper. I think I have it!

---

### Post by jg579224a on 2011-07-30
cool, what time is it there? (assuming your in Carolina)

By the way, are you a computing specialist? 

and one more question lol, how would I gain mastery of UNIX? I dearly want to and a little advice would go a long way.

---

### Post by chili555 on 2011-07-30
A computing specialist? Who, me? Nope, I retired early and love helping new users get over the biggest hurdle, networking and especially wireless. I never worked in computers in my life.> how would I gain mastery of UNIX? I dearly want to and a little advice would go a long way. I hope you mean Linux. As far as I know Linux is used far more than UNIX. I'd suggest any number of books on Ubuntu available at Amazon and other places.

It is 7:00pm here.

Let's try a temporary measure. Your wireless card is here:> Network controller [0280]: Atheros Communications Inc. Device [168c:002e] (rev 01)It uses the module ath[COLOR="Red"]9[/COLOR]k. My guess from above was incorrect. Let's unload two modules and load ath9k and see if your wireless works. If so, we'll tweak a couple of files and you'll be all set. Please do:```
sudo rmmod -f ndiswrapper
sudo rmmod -f acer-wmi
sudo modprobe ath9k
```If the first two error out, that's OK. If there is any error or warning after ath9k, please post it.

Now does your wireless work?

---

### Post by jg579224a on 2011-07-30
I post it all just in case:


alex@alex-laptop:~$ sudo rmmod -f ndiswrapper
[sudo] password for alex: 
ERROR: Removing 'ndiswrapper': No such file or directory


alex@alex-laptop:~$ sudo rmmod -f acer-wmi
ERROR: Removing 'acer_wmi': No such file or directory


alex@alex-laptop:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by chili555 on 2011-07-30
Now run:```
iwconfig
```Do you have a wireless interface, wlan0 perhaps? Any action from Network Manager?

---

### Post by jg579224a on 2011-07-30
I'm not sure if I have a wireless interface

---

### Post by jg579224a on 2011-07-30
nothing from device manager

alex@alex-laptop:~$ iwconfig

lo        no wireless extensions.

pan0      no wireless extensions.

---

### Post by chili555 on 2011-07-30
Please do:```
sudo modprobe ath9k > jg57-2.txt
dmesg >> jg57-2.txt
modinfo ath9k >> jg57-2.txt
zip jg57-2.zip jg57-2.txt
```Please attach the ***zip*** file to your reply.

---

### Post by bkratz on 2011-07-30
Note to Dr. Chili- Not completely sure, but I don't think ath9k was in the kernel before  2.6.29.  I think he/she may have to change the sources.list to old-releases and and use the backports like in 

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Well wrong again!
From  [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)
"
Any distribution shipping a kernel >= 2.6.27 will have ath9k present but the ath9k driver on 2.6.32 is the oldest one recommended, anything older than that is completely unsupported
"

---

### Post by jg579224a on 2011-07-30
I meant to say that I don't know what a wireless interface is, although I am using wireless to connect to the internet right now through windows, I have a partitiond hard-drive with ubuntu

---

### Post by chili555 on 2011-07-30
> **bkratz said:**
> Note to Dr. Chili- Not completely sure, but I don't think ath9k was in the kernel before  2.6.29.  I think he/she may have to change the sources.list to old-releases and and use the backports like in 

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Well wrong again!
From  [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)
"
Any distribution shipping a kernel >= 2.6.27 will have ath9k present but the ath9k driver on 2.6.32 is the oldest one recommended, anything older than that is completely unsupported
"I'm not at all sure ath9k in 9.04 claims his device:> Network controller [0280]: Atheros Communications Inc. Device [[COLOR="Red"]168c:002e[/COLOR]] (rev 01) > I don't know what a wireless interface is, although I am using wireless to connect to the internet right now through windows, I have a partitiond hard-drive with ubuntu It would show up as wlan0 here, which it doesn't:> alex@alex-laptop:~$ iwconfig

lo no wireless extensions.

pan0 no wireless extensions. As soon as we solve that mystery, we'll be off and running.

---

### Post by jg579224a on 2011-07-30
zip file attached

---

### Post by bkratz on 2011-07-30
> **chili555 said:**
> I'm not at all sure ath9k in 9.04 claims his device:It would show up as wlan0 here, which it doesn't:As soon as we solve that mystery, we'll be off and running.

Back according to [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

It was not supported (that id corresponds to AR9287)

"
AR9287 (>= 2.6.32) 2x2 SB 11n PCIe

"

---

### Post by jg579224a on 2011-07-30
Haha, I wish I knew what was going on; although the shadow I'm in makes me more eager to become a linux master.

---

### Post by bkratz on 2011-07-30
@jg579224a

Don't let him kid you.  [COLOR="DarkRed"]A computing specialist? Who, me? Nope,[/COLOR]

Yes he is.

---

### Post by chili555 on 2011-07-30
Correct. The driver ath9k in your 9.04 system does not support your device:> filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5530FD7F98BD55CB1169801
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586Devices 002a, 0029, 0027, 0024 and 0023 are listed, but not 002e.

We could download and install a driver with great difficulty; eventually, we'd get it done. Alternatively, you could download and install the later version of Ubuntu. It is supported, for example in 10.04 LTS.

How much patience do you have? Which do you prefer?

---

### Post by jg579224a on 2011-07-30
Yes, I thought I'd sensed a little modesty in that thread; I'm lucky to be getting this service for free

---

### Post by jg579224a on 2011-07-30
Well I'd imagine that downloading a new version would take millennia? I was planning on updating when I got my wireless up and running in Ubuntu which would be quick?

I don't know if I'm right about that.

You strike me as a man who will see any task through, alas, I feel I have used much of your time already; how long would the difficult option take? and how difficult is it?

---

### Post by jg579224a on 2011-07-30
I have the patience of a saint, although it is 01:30 in the morning here, could we have the task done by 04:00?

---

### Post by jg579224a on 2011-07-30
P.S. I have a cd with quote "full versions of ubuntu 9.04, as well as Kubuntu, Edubuntu, Xubuntu and PPC releases!" would any of those do the trick?

---

### Post by chili555 on 2011-07-30
Nope on both counts. I will be headed for nap time in about an hour. Can you download here? [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Get either 10.04 LTS or 11.04, as you prefer. Burn the iso image to CD and install in place of your 9.04 version. You will thank me!

---

### Post by jg579224a on 2011-07-30
Thank you, you have been a great help, how long will it take ona average to download one of those?

---

### Post by chili555 on 2011-07-30
Let it run all night. When the coffee's ready in the morning, we'll be all set.

I depends, of course, on your download speed; a couple of hours, I'd guess.

---

### Post by jg579224a on 2011-08-10
Hello again Chili, hope your online, I have Ubuntu 11.04 on disk now, and as you know 
Ubuntu 9.04 on my partition, I would like to remove 9.04 and install 11.04, without destroying my life. Thank you

(If chili not online or busy, I would be glad for someone else's help)

---

