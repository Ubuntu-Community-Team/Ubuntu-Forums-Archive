---
title: "Wireless problems - ath9k on Ubuntu 9.10"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by warden976 on 2009-11-05
Hi all,

I've been running ubuntu 9.10 since release day no problems, did some updates last night (didn't really pay attention to what they were) and shut down shortly after. When I've come to use the PC again this evening my wireless connection keeps randomly disconnecting and won't re-connect, eventally popping up the passphrase box (which i can re-enter my WPA passphrase and it still won't connect). I have to reboot to get it to re-connect.

No other devices seem to be affected and so I don't think it's my router.

I've got ubuntu 9.10 32bit installed on an acer aspire 5535.

Any ideas?

Cheers

---

### Post by libertychuck on 2009-11-09
I am experiencing the exact same problem, except with an Acer Aspire 5732z.  I am anxiously awaiting a solution, as it is very frustrating.

---

### Post by Elif on 2009-11-10
Very annoying bug. I've had this problem since upgrading to karmic on my aspire 5810. I had no problems under 9.04.

It seems specific to the ath9k drivers, as my external adapter works flawlessly. 

After some googling, It appears to be a bug in the 2.6.31 kernel and not an ubuntu-specific bug. 

There are some patches in wireless-testing that will fix the issue, but reportedly at the expense of traffic speed and CPU usage. See [this post]("http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg02159.html") to the ath9k-devel list for more info.

---

### Post by warden976 on 2009-11-27
i'm sadly still getting this problem, just wondering if anyone else has been able to resolve?
 
I did start to think it could've been some wireless headphones i have interferring but have since realised I get disconnected even when it's all powered off and physically unplugged, including when my laptop is the only wireless device on in the house (other than the router :D)...
 
I've scanned for other networks and only my neighbour has another wireless network which is at the opposite end of the channel spectrum. I've also changed my wireless channel multiple times just in case.
 
I also installed a newer firmware on my router to no avail...
 
i've got 32bit 9.10 netbook remix working on an eee 901 and that's working 100% fine. :P
 
In a last ditch attempt to fix I even wiped the laptop and did another fresh install of 32bit 9.10, but it didn't work.
 
I did even try 64bit which, during the hour or so it was on there, didn't disconnect me, but flash does not work very well in 64bit so not really an option for me.
 
bit gutted really - having to reboot so frequently is turning into a bit of a show stopper for me :(

---

### Post by warden976 on 2009-11-27
as a last ditch attempt tonight i've tried the fix here - [http://ubuntuforums.org/showthread.php?t=1137780](http://ubuntuforums.org/showthread.php?t=1137780)

I know it's not for the same issue, but like i said - last ditch attempt.

I had to modify it a little - *sudo apt-get install linux-backports-modules-**karmic*** - and didn't install wicd, but my wireless has stayed connected for the last 20 minutes after rebooting, and has direct downloaded 160 meg of an ISO while downloading 2 other ISOs via bittorrent.

will have to leave it longer to know for sure that it's not just randomly not manifesting itself...

---

### Post by netrati on 2009-11-27
Hey I was having the exact same problem that you guys are describing. My fix was to download the latest compat-wireless drivers...

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

After you extract the tarball, run ./scripts/driver-select ath9k
Then run make and sudo make install

Problem fixed!

---

### Post by coffeecat on 2009-11-27
> **warden976 said:**
> I had to modify it a little - *sudo apt-get install linux-backports-modules-**karmic*** 

If your Atheros chipset is using ath9k and you've got a flaky connection, that's the way to go. I installed the package linux-backports-modules-wireless-karmic-generic as well. Ever since, my Atheros wireless has been steady as a rock.

---

### Post by warden976 on 2009-11-29
> **coffeecat said:**
> If your Atheros chipset is using ath9k and you've got a flaky connection, that's the way to go. I installed the package linux-backports-modules-wireless-karmic-generic as well. Ever since, my Atheros wireless has been steady as a rock.

turns out the backports hadn't fixed the issue, so i've gone for a 64 bit install and installed both sets of backports. found a good post on getting 64 bit flash working with 10.0 (apparently 10.1 isn't working yet), so now just fingers crossed with the wireless.

:)

---

### Post by warden976 on 2009-11-29
> **warden976 said:**
> turns out the backports hadn't fixed the issue, so i've gone for a 64 bit install and installed both sets of backports. found a good post on getting 64 bit flash working with 10.0 (apparently 10.1 isn't working yet), so now just fingers crossed with the wireless.

:)

3 hours up and counting - best it's been in weeks.

---

### Post by warden976 on 2009-11-29
> **warden976 said:**
> 3 hours up and counting - best it's been in weeks.

5 hours uptime now - this is much better.

i ran *sudo apt-get install linux-backports-modules-karmic* followed by *sudo apt-get install linux-backports-modules-wireless-karmic-generic* (thanks coffeecat) and rebooted. 

Another noticeable difference is the signal is now seeming to flux between 70% and 90% rather than 10% to 30%.

---

### Post by coffeecat on 2009-11-29
Interesting that your 64-bit is steady with the backports, but not the 32-bit. (If I read you correctly.) The installation on my Acer laptop with the Atheros AR928X chipset using the backported driver is 64-bit. I haven't tried the 32-bit version with that wireless chipset.

---

### Post by warden976 on 2009-11-30
a difference was I installed both sets of linux-backports-modules on 64 bit, but only the linux-backports-modules-karmic on 32 bit.

---

### Post by warden976 on 2009-12-05
quick update - wireless has been fine for days now after installing both sets of backports.

cheers for the help!

---

### Post by musonic on 2009-12-05
I'm having exactly the same problem on an acer aspire 3500. I'm afraid I'm not as technical as some other posters, so could someone explain to me in laymans terms what I need to do to solve the issue. I don't understand how I can download fixes or updates if I can't connect to the internet! I'm running the machine as a dual-boot with Windows XP and can connect using that OS. Is that of any use?
Any help would be much appreciated because I'd far rather be using Ubuntu than Windows... :-)

---

### Post by coffeecat on 2009-12-05
> **musonic said:**
> I'm having exactly the same problem on an acer aspire 3500. I'm afraid I'm not as technical as some other posters, so could someone explain to me in laymans terms what I need to do to solve the issue. I don't understand how I can download fixes or updates if I can't connect to the internet! I'm running the machine as a dual-boot with Windows XP and can connect using that OS. Is that of any use?
Any help would be much appreciated because I'd far rather be using Ubuntu than Windows... :-)

Before we go any further, let's make sure you have an Atheros wireless chipset. Just because you have an Acer laptop doesn't necessarily mean you do. :) The fix described in this thread is for people who are having problems with Atheros wireless. Since you say you are getting no wireless connection at all, it could be that you have a completely different wireless chipset. My experience was that I could connect but that it would keep disconnecting randomly - that is until I installed the (updated) modules (drivers).

Open a terminal (Applications > Accessories > Terminal) and do this command:

```
lspci
```Look for a line with 'Wireless' and/or '802.11' in it. Does it mention Atheros or something else? Post the line so that we can look at it. If it does say Atheros, can you connect your laptop to your router with an ethernet cable? If you can, then go to System > Adminstration > Synaptic. Click on 'Reload' and when that has finished downloading some package information, look for and mark these two packages for installation:

*linux-backports-modules-karmic**linux-backports-modules-wireless-karmic-generic*

 Click on 'Apply' to install and reboot. Now go to the network manager icon (top right), click on it and select your network.

Don't do this if you don't have Atheros, but post the information and we'll take it from there.

---

### Post by adrian_nye on 2009-12-06
The backports fixed my issues on Acer 5810, which has the Atheros AR928X.

---

### Post by musonic on 2009-12-06
Thanks CoffeeCat for your message. Sorry it's taken me a little while to get back. It seems that my machine users the Atheros AR5005G wireless network adapter - which I'm assuming is the same thing as a chipset.
I would try connecting using an ethernet cable if only I could find one! Is there anyway I could download the packages on the windows side of the computer, save them on a USB stick and then access them from there when I reboot into Ubuntu?
Thanks again for your help - I really appreciate it!

---

### Post by coffeecat on 2009-12-06
> **musonic said:**
> It seems that my machine users the Atheros AR5005G wireless network adapter - which I'm assuming is the same thing as a chipset.

The AR5005G refers to the actual chipset, which is a different Atheros one (AR928X) mentioned earlier. No guarantee that the backports will work for the 5005 but if you're willing to give it a try, here goes.

The two packages mentioned earlier (linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic) are what are called metapackages. They don't have any binaries or drivers themselves but, if selected, pull in a number of dependencies. In this case one only, the backports modules for the specific version of the kernel you are running. The reason you would normally select the metapackage is that every time the kernel is updated, the modules are updated as well. But in your case we need to download and install the specific numbered package - the metapackage won't do any good until you get an internet connection. So...

Step 1 - boot into Ubuntu, open a terminal and...

```
uname -r
```Make a note of the output. It will be one of:

2.6.31-14-generic
2.6.31-15-generic
2.6.31-16-generic

Probably -14 if you haven't yet done any upgrades.

Step 2 - boot into Windows and go to:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/)

Download the .deb package appropriate to your architecture. This will be:

linux-backports-modules-2.6.31-14-generic_2.6.31-14.16_amd64.deb

for 64-bit, or

linux-backports-modules-2.6.31-14-generic_2.6.31-14.16_i386.deb

for 32-bit.

**OR**, download the 2.6.31-15 or -16 package if you are running the -15 or -16 kernel.

Step 3 - transfer the .deb.file to your Ubuntu and simply double-click on it. You'll be prompted for your password and it will be installed. You will probably need to reboot before trying network manager. If you can connect to your network, you are not yet finished, but go to....

Step 4 - Open System > Administration > Synaptic. Click on 'Reload' and let that process finish. **Do not yet click on 'Mark all Upgrades', and if the Update Manager pops up, close it**. There is one more thing to do before you do a full update otherwise you will lose internet connectivity.

Step 5 - In Synaptic, find the packages linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic and mark them for installation. (You probably only need one or the other, but it won't harm to have both.) Synaptic will probably also mark for installation all the packages for the latest -16 kernel. That's OK. Click on 'Apply' and those things will be installed.

Step 6 - Now reboot. You'll reboot into the -16 kernel together with the newly installed -16 backported modules and, hopefully, everything will be working OK. You can now apply all the updates either from the update manager or from Synaptic.

---

### Post by Hermitian Conjugate on 2009-12-06
> **warden976 said:**
> 5 hours uptime now - this is much better.

i ran *sudo apt-get install linux-backports-modules-karmic* followed by *sudo apt-get install linux-backports-modules-wireless-karmic-generic* (thanks coffeecat) and rebooted. 

Another noticeable difference is the signal is now seeming to flux between 70% and 90% rather than 10% to 30%.

This worked like a charm for me.  I noticed the signal strength improvement as well.  Thank you!

---

### Post by adrian_nye on 2009-12-06
> **adrian_nye said:**
> The backports fixed my issues on Acer 5810, which has the Atheros AR928X.

I spoke too soon - next time it awoke from sleep the wireless would not connect and kept popping up the wireless security password dialog.  I have uninstalled the backports and now it connect but randomly gets very slow or disconnects periodically.   If I sleep and then awaken it is normal for a while.

---

### Post by Kilz on 2009-12-06
Thanks for the info, the linux-backports-modules-wireless-karmic-generic has made my Acer 5536 usable again. It was a pain to have to reboot to reconnect.

---

### Post by musonic on 2009-12-08
Thanks so much for all of that, coffeecat. I really appreciate you going through it. I haven't had time to sit down and try it yet, but I will be sure to post back here and let you know how I get on!!!

---

### Post by barkej on 2009-12-15
> **netrati said:**
> Hey I was having the exact same problem that you guys are describing. My fix was to download the latest compat-wireless drivers...

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

After you extract the tarball, run ./scripts/driver-select ath9k
Then run make and sudo make install

Problem fixed!

Thanks! This worked wonders for my dodgy wireless card.

---

### Post by andlinux on 2010-01-01
> **barkej said:**
> Thanks! This worked wonders for my dodgy wireless card.
This didn't work for me, if I do ./scripts/driver-select ath9k
Then it tells me that this doesn't exist ???

---

### Post by fgossart on 2010-01-05
> **andlinux said:**
> This didn't work for me, if I do ./scripts/driver-select ath9k
Then it tells me that this doesn't exist ???

are you sure to be in the right directory where the scripts are extracted ?

---

### Post by dusher on 2010-01-05
warden976 + coffeecat solution worked for me in my ASUS Eee PC 1005HA with an Atheros AR9285 wifi card

```
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```I've tried almost everything.. and this was so simple that I couldn't beleive it's finally fixed!

---

### Post by andlinux on 2010-01-05
> **fgossart said:**
> are you sure to be in the right directory where the scripts are extracted ?
I made a mistake, I downloaded this file ( [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.31/compat-wireless-2.6.31-rc7.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.31/compat-wireless-2.6.31-rc7.tar.bz2) ) and the command is not working with this.

I also tried the backports but that didn't work for me. Neither the scripts from the link in this topic.

---

### Post by dougwyl on 2010-01-05
> **dusher said:**
> warden976 + coffeecat solution worked for me in my ASUS Eee PC 1005HA with an Atheros AR9285 wifi card

```
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```I've tried almost everything.. and this was so simple that I couldn't beleive it's finally fixed!

Thank you warden976 and coffeecat for your information.  This fix [Atheros] has worked wonders for my wireless connection.  My signal strength has now changed to a steady 100% from about a 70%; after more than 3 hours I have not yet lost a connection.

---

### Post by Jedster on 2010-01-06
Hi, I have similar problems and am still a learner at linux and am struggling to fix them, would someone be so kind as to assist me please?

I have an acer aspire one 150 which had 9.04 on and all was well.
I upgraded to 9.10 and I'm sure wireless used to work on that, now I find it's not working.
My wired network shows as disconnected.
My wireless network shows as disconnected.
Both networking and wireless are ticked.

To answer earlier qns
lspci shows Atheros AR5001
uname -r shows
2.6.31-16-generic
I downloaded linux-backports-modules-2.6.31-16-generic_2.6.31-16.18_i386.deb using windows, copied it to the Acer and double clicked it which seemed to install.
Rebooted, still no joy.
I downloaded linux-backports-modules-wireless-karmic-generic_2.6.31.16.29_i386.deb, copied it to the Acer and double clicked it which seemed to install.
Rebooted, still no joy.
I downloaded linux-backports-modules-karmic-generic_2.6.31.16.29_i386.deb etc...
Rebooted, still no joy and now my Enable wireless tickbox is greyed out...!

Help, how do I get wireless working again pls?

Thanks,
Jed

---

### Post by Jedster on 2010-01-07
ok, I think I may have found out what went on here. 
I tried installing the original 9.10 (prior to any updates) and still no wireless.
I tried installing 9.04 which used to work, still no wireless.
Starting to panic at this point I recovered the Acer to the CD supplied with the acer (Linpus lite) and still no wireless.
Until I noticed that the wireless light wasn't on, I flicked the wireless switch and suddenly wireless works again!
OK, now I possibly flicked this switch while I had 9.10 running, and maybe that stoped it working, I'm certain I tried flicking the switch with 9.10 and it didn't enable it again.

I'm guessing that 9.10 has some support for the wireless switch, i.e. enough to turn wireless off, but not enough to turn it on!

I think this time I'll do a dual boot between Linpus and UNR 9.10 so at least if I do the same it's an easy fix!
That's assuming that wireless works again when I install UNR 9.10 anyway, otherwise I think I'll just stick at 9.04.

Jed

---

### Post by tjohnson_nb on 2010-01-18
> **netrati said:**
> Hey I was having the exact same problem that you guys are describing. My fix was to download the latest compat-wireless drivers...

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

After you extract the tarball, run ./scripts/driver-select ath9k
Then run make and sudo make install

Problem fixed!
I am running Kubuntu 9.10 and I also did the above and it seems to be working so far. Before my connection was stopping and starting every few minutes.

---

### Post by Merlinson on 2010-02-04
Thank you so much.  I have an Acer Aspire One AO532h.  The backport module install suggestion has given me full signal bars in netbook remix when before I had one to two and frequent disconnects.

---

### Post by apc boss on 2010-02-07
> **coffeecat said:**
> If your Atheros chipset is using ath9k and you've got a flaky connection, that's the way to go. I installed the package linux-backports-modules-wireless-karmic-generic as well. Ever since, my Atheros wireless has been steady as a rock.
thank you that did it for me too its absolutely stable now:P

---

### Post by wobin77 on 2010-02-11
Confirmed! Steady as a rock now. 

--> don't forget to reboot

sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

---

### Post by prisoner849 on 2010-02-12
Hey everyone, I also had problems until installing the backports, but for whatever reason my ath9k is back to being next to useless again. The signal strength is now higher, and the connection was strong for a day or two, but now it drops out after only a few moments of use.

So, backports seem to solve the problem, but only for a few days.

I've tried a few different types of wireless access points, with and without encryption, only to get the same results.

I can confirm that 8.10 ubuntu, windows XP and knoppix work a treat on wireless (out the box). I do want to keep 9.10, but without wireless there is no point.

Anybody got any clues after having used back-ports?

---

### Post by andlinux on 2010-02-12
> **prisoner849 said:**
> Hey everyone, I also had problems until installing the backports, but for whatever reason my ath9k is back to being next to useless again. The signal strength is now higher, and the connection was strong for a day or two, but now it drops out after only a few moments of use.

So, backports seem to solve the problem, but only for a few days.

I've tried a few different types of wireless access points, with and without encryption, only to get the same results.

I can confirm that 8.10 ubuntu, windows XP and knoppix work a treat on wireless (out the box). I do want to keep 9.10, but without wireless there is no point.

Anybody got any clues after having used back-ports?Did you install any updates that's causing this problem ?

---

### Post by yevgeni on 2010-02-12
This issue is *far* from solved. I'll quote another thread that I started:

> 
ath9k: Still a turd sandwich

Ok... I don't mean to start a new thread to complain, but this is an ongoing issue. I've tried:

Installing backports... no noticeable difference.
Installing/uninstalling madwifi... no noticeable difference.
Installing wireless-compat... Signal strength a little better but still getting much lower than normal (some 75% 10 feet away from the router) and still dropped connections.
Installing wicd... No noticeable difference from previous step with the exception that wicd likes to drop the connection more frequently requiring me to modprobe the driver, and caused me to promptly reinstall gnome network manager.

So what's the deal? My friend has the exact same Aspire netbook that I do, except it has a Broadcom wireless chipset instead of Atheros... and works flawlessly.


So does anyone else have any bright ideas? A problem like this severely hurts Ubuntu and Linux overall.

---

### Post by prisoner849 on 2010-02-24
> **andlinux said:**
> Did you install any updates that's causing this problem ?

Sorry for the slow reply:

I'm not really sure. I have a bit a obsessive compulsive disorder when it comes to installing updates, so I've been keeping a good track.

The good news is, I have solved the problem which may have been caused by an update changing the black list config file.

I'll edit this post when I get home and confirm what I did on my laptop to fix it's wireless problem (just posting for now while I remember it).

---

### Post by gotsanity on 2010-02-25
> **prisoner849 said:**
> Sorry for the slow reply:

I'm not really sure. I have a bit a obsessive compulsive disorder when it comes to installing updates, so I've been keeping a good track.

The good news is, I have solved the problem which may have been caused by an update changing the black list config file.

I'll edit this post when I get home and confirm what I did on my laptop to fix it's wireless problem (just posting for now while I remember it).

I too am having the same problem. I have the backports installed and current but it doesnt seem to fix the problem. I sometimes have to re-connect to the network in order to get it running again and it gets a little bit annoying when connecting to things like youtube. Does anyone have a solid answer yet?

---

### Post by chrisolof on 2010-02-26
Installing linux-backports-modules-wireless-karmic-generic from Synaptic Package Manager fixed my issues - throughput and reliability are both great now.  Thanks!

---

### Post by prisoner849 on 2010-03-05
Sorry again for a slow reply to a slow reply. Stuff going on all over the place. Anyway, I thought I had it fixed by changing the blacklist (after installing back-ports) by editing /etc/modprobe.b

However, the issue has come back with serious vengeance: I pretty much can't use the wireless card for longer and a few seconds before it drops. I'll do a bit more testing and try to see if the logs can tell me anything, but at the moment I'm really over this. I really want to keep trying with ubuntu, but so far ubuntu is doing the impossible by making me miss my old winXP install.

---

### Post by coffeecat on 2010-03-05
There is one issue that may affect ath9k even if you have the backports package installed. This may or may not be relevant to those reporting problems.

I recently changed my G-only Linksys router to a N150 Netgear one. I don't really need N speeds - I just needed a new wireless modem-router. My laptop with the Atheros AR928X became problematic again with this router. The problem was a failure to establish a connection on about half the occasions I booted up rather than an unstable connection when it did connect. Although, to be honest, I didn't leave the system running for long before I found my fix. WPA2-PSK was **not** the problem. (The Linksys used the older WPA-PSK.) The problem was the mixed N/G wireless in the router. If I set it to G only the connection became reliable again. Interestingly, my other laptop with an N-capable Intel wireless chipset was unaffected. 

Whether this is a problem with N-speeds with the ath9k driver with my AR928X chipset (which is N-capable) or a problem with the way Netgear implements mixed N/G mode, I don't know. But I offer this as something else to try.

---

### Post by green.jon on 2010-03-06
Wireless chipset  - AR5001 <--- according to lspci
Initial problems started with network-manager

I was having similar issues of a spotty wifi connection when I had 9.04. Just 3 days ago I switched to 9.10 and wifi seemed to be working fine until Thursday. For some reason it didn't seem to be working at all. Luckily, I was able to hook it up to my ethernet cable and that worked great so I tried installing wicd. That didn't fix anything at all. After hours and hours of using google, I came across this thread and decided to dive in and try out the solution. Sure enough, it worked like a charm! Thanks guys!

Solution:
```

sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```Then reboot!

I wish I knew what caused the problem, but I honestly have no idea. I hope I posted this in the right thread!

P.S. I have the WNR1000 Netgear router and was having problems getting my Nintendo Wii to work with it until I changed the router to broadcast on Channel 11, which seemed to help my connection for a bit. I didn't find a way to switch it from N to G though.

---

### Post by Sponge34 on 2010-03-07
Hi,
Just another 'It worked for me' for the apt-get install solution.

Acer 5732Z, Safecom router, Ath9k driver, 32 Bit Ubnuntu 9.10

Symptoms: Wireless disconnects and prevents typing in a terminal window. Can't remember if I could ctrl-alt-f2 or not. Could sometimes restart the machine but more often than not had to pull the plug and yank the battery out. Wireless signal strength 10% or so even within 10 feet/3m of the router.

Action - once booted got a Terminal window open and 

[FONT="Courier New"]sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic[/FONT]

Rebooted and things seem to be a bit more stable. Signal strength up to 70% now and so far no crashes.

---

### Post by chrisolof on 2010-03-07
Ok - I had previously said the backports-modules solution had solved all my issues - and though things are much better it has unveiled a new problem.

Now it seems that about every five minutes the card stops sending and receiving for about 10 seconds.  It remains connected during this time, but just won't send or receive anything.

This isn't horrible, but certainly slows down work over SSHFS connections and makes for terrible 10-second lag wait periods in online games that assume a reliable network connection.

Is anyone else experiencing this?

If I had to guess I'd assume this has to do with NetworkManager periodically scanning for available networks - and for some reason this backport driver is unable to continue network communications while scanning for available networks.  It could also be that the card's hardware isn't capable of doing both at the same time.  In any case I'm going to try associating with the network without the help of NetworkManager and see if that solves it.

---

### Post by green.jon on 2010-03-07
I haven't had that problem. Have you tried Wicd? You may be right about the card not being able to handle those two functions at once. What chipset are you using?

---

### Post by chrisolof on 2010-03-08
Sure enough - installing Wicd in place of NetworkManager fixed the connection pauses I was experiencing.  I wish I would have found Wicd last week!  My chipset is:

AR928X Wireless Network Adapter (found by running "sudo lshw" in a terminal)

I'd recommend anyone with this particular adapter do the following to get it working reliably:
[LIST=1]
[*]Install the linux-backports-modules-wireless-karmic-generic package (which will install linux-backports-modules-karmic as well) and the wicd package.
```
sudo apt-get install linux-backports-modules-wireless-karmic-generic wicd
```
[*]Reboot your machine and connect to your preferred network through Wicd.  You may need to specify "wlan0" as your wireless interface in the Wicd preferences.
[/LIST]

My theory on why Wicd works and why the default NetworkManager doesn't:
[LIST]
[*]The AR928X adapter is cheap (or the driver isn't very capable) and can't send or receive while scanning for available networks.
[*]NetworkManager scans for available wireless networks every few minutes.
[*]Wicd only scans for available networks when you need it to - that is to say it only scans when you're looking for a network to connect to and does not scan when you're happily connected.
[*]Therefore, Wicd is a better choice for use with the AR928X Wireless Network Adapter because it does not interrupt one's connection with unnecessary scanning.
[/LIST]

---

### Post by coffeecat on 2010-03-08
> **chrisolof said:**
> My theory on why Wicd works and why the default NetworkManager doesn't:
[LIST]
[*]The AR928X adapter is cheap (or the driver isn't very capable) and can't send or receive while scanning for available networks.
[*]NetworkManager scans for available wireless networks every few minutes.
[*]Wicd only scans for available networks when you need it to - that is to say it only scans when you're looking for a network to connect to and does not scan when you're happily connected.
[*]Therefore, Wicd is a better choice for use with the AR928X Wireless Network Adapter because it does not interrupt one's connection with unnecessary scanning.
[/LIST]


I have no problems with Network Manager and the AR928X chipset (with the backports packages in Karmic). I think this is a your mileage may vary situation. I've seen posts from many people who are happier with wicd - I respect that. I've also seen posts from people deeply unhappy with wicd and who wanted to revert to NM. I've tried wicd - I was unimpressed.

---

### Post by andlinux on 2010-03-08
Another possible problem can be the Wlan router, some routers give more problems... 
I had a levelone router that didn't work decently with Ubuntu and the linksys that I bought had no problem.

---

### Post by green.jon on 2010-03-11
And it seems that WicD is being fussy and I'm without wifi in UNR again. I'm glad I dual boot on this netbook. I'm all out of ideas guys. Anyone have any suggestions? I have a feeling it's because of the router, but don't have the money to get another anytime soon and no others to test it with at the moment... :confused:

---

### Post by andlinux on 2010-03-11
> **green.jon said:**
> And it seems that WicD is being fussy and I'm without wifi in UNR again. I'm glad I dual boot on this netbook. I'm all out of ideas guys. Anyone have any suggestions? I have a feeling it's because of the router, but don't have the money to get another anytime soon and no others to test it with at the moment... :confused:
Test it somewhere where you have free hotspots.

---

### Post by prisoner849 on 2010-03-13
hi again everyone. The recent backport update hasn't changed anything: My connection is dropping out pretty frequently. 

However I've seen that there are plenty of issues using this chipset with an N speed router. I've since set the router to G speed but to no effect (other than slowing down my main computer running windows 7 and an N speed dongle with no problems).

What's the best way to gather info about these problems? I've been trying to find useful info in the system logs, but it  appear there are plenty of other bugs spamming my logs (battery report issues, samba still report issues after dismounting, wpa supplicant scan events).

---

### Post by green.jon on 2010-03-22
> **andlinux said:**
> Test it somewhere where you have free hotspots.

Sorry I've been MIA for awhile. Just finished finals and I did surprisingly good! Back to the matter at hand...

I was able to connect to my school's wifi so the only problem I can really think of (without looking in logs because I don't know WHERE to look) is the router. I still haven't been able to find a way to change it from N mode to G mode. This problem was quite a thrill killer in getting back into Ubuntu, but I won't let it stop me. Do you guys think it IS the router? I'll be moving in about 2 to 3 weeks so I'll be dealing with a different router (another story altogether) luckily, but I'd really like to know the cause of this problem.

Cheers!

---

### Post by green.jon on 2010-03-29
Just another quick update. Seems I can connect to the router again as I'm using it right now on my netbook to post this. This is getting really confusing. Anyone else care to post some updates please?

---

### Post by grimslider75 on 2010-03-29
> **warden976 said:**
> 5 hours uptime now - this is much better.

i ran *sudo apt-get install linux-backports-modules-karmic* followed by *sudo apt-get install linux-backports-modules-wireless-karmic-generic* (thanks coffeecat) and rebooted. 

Another noticeable difference is the signal is now seeming to flux between 70% and 90% rather than 10% to 30%.

THANK YOU SOOOOOOOO MUCH, ITS PERFECT!!!! :KS:KS:KS:KS:KS:KS

I posted 2 threads about to no avail..... but stupid me:D didn't search, but now that i found this i am eternally grateful!!! 

thanks! to everyone!:popcorn:

---

### Post by rburhum on 2010-04-05
I have an Asus G72X laptop that has an AR928X Wireless Network Adapter. Sadly, installing both backport packages (linux-backports-modules-karmic and linux-backports-modules-wireless-karmic) did not work for me. 

any pointers? :-/

EDIT: I should probably add that the wireless adapter is working better though. Now I can always hit disconnect and then reconnect which solves the connection problem 99% of the time. However, a few minutes later, my connection seems dead - although the icon still shows connected.

---

### Post by timjayko on 2010-04-05
sony vaio here, was having poor wireless performance, thought it might be my wireless access point (its a piece of crap), but installed the wireless backport modules and wifi running much better =).

---

### Post by ollifl on 2010-05-12
Same problem here with  Nokia N3G booklet and ATH9K, karmic worked great with the backport-wireless and I also thought that  I had fixed the problem in Lucid with the same fix, worked fine for a day but somehow it seems the problem got worse over period of 12 hours.
Yesterday I could surf the net for couple of hours without disconnecting and  the period seemed to get shorter and shorter by evening I had to disconnect every couple of minutes and this morning it was just a big mess, so I switched my ATT sim card from my phone to my netbook and atleast I have internet again. hopefully somebody finds a fix to this problem soon.
.

To top it all I have GMA500 graphics card, pretty much SOL with linux right now.....


After searching for awhile I came upon this page and it seemed to work atleast for now

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by Linxuxslate on 2010-05-17
I've tried lots of versions of the compat-wireless, but no long-term success.

Info:
Sony VAIO CW
ath9k
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ath9k

I've tried the backports from the karmic repos, compat-wireless from the releases, and compat-wireless from the bleeding edge builds.

They are all the same -- 
Low, and fluctuating signal even though I am in the same room as the router
Max of a few dozen MB/s
Seems to slow after a pretty good first burst
On occasion, i.e. for an evening or until I suspend or reboot, it works fine, but it does   not last.
Tried on several different networks: Home (wep), Local sandwich shop (open), and work (wep).  All are the same.

Other posts report that the same drivers work OK on other distros, so I think it is a kernel thing, or how the regdb talks to the driver/kernel in Ubuntu.
 
I, too hope this is fixed, I can't even show off my machine (Ubuntu is the only OS on the machine), because it keeps disconnecting.

---

### Post by rigobert77efc on 2010-06-29
> **netrati said:**
> Hey I was having the exact same problem that you guys are describing. My fix was to download the latest compat-wireless drivers...

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

After you extract the tarball, run ./scripts/driver-select ath9k
Then run make and sudo make install

Problem fixed!


*Consider your little japanese socks blessed netrati!* 

Worked a treat. I'm running 9.10 64bit on an ACER Aspire 5732z, fitted with a AR928X Wireless Network Adapter (or so I think.. I ran lshw and I think that's the appropriate hardware). Similar problem to everyone else; it would be fine for 20 mins or so, then cut out and ask for authorisation. After a reboot it would be ok for a while then cut out again. After extracting and installing compat-wireless-2.6/compat-wireless-2.6.tar.bz2, the signal boosted to 75% or so and has been running without a problem for about 6 hours. I can also change between routers and it works first time.

*Thanks again netrati*

---

