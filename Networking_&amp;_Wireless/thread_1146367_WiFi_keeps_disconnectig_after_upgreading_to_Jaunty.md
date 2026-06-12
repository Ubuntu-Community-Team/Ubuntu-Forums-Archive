---
title: "WiFi keeps disconnectig after upgreading to Jaunty"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by lampak on 2009-05-02
I have a problem with my wireless connection - from time to time it disconnects and I have to reconnect manually. I hadn't had such problems before upgrading to Jaunty and I do not have them in Windows, so it is rather not a hardware issue. The signal strength is good. I use a built-in WiFi in my Asus laptop. Any ideas what can be the reason?

---

### Post by jmurch on 2009-05-03
I hope someone replies as this is exactly the problem that I have after upgrading.

Jeff

---

### Post by irishbeer on 2009-05-10
same problem here !!!
 
 it is very embarrassing... I have replaced windows XP in a friend computer with Ubuntu... I have told him that XP is not good... that he should use Ubuntu etc...
 
 a now he is upset as he cannot use WIFI !!!!!....
 
 
 it connects right... but after using it for a while it just hangs... so I need to reconnect manually !!! that happens every 2 minutes !!!!

is Ubuntu team working on any fix about it ?

---

### Post by ubuser_7 on 2009-05-10
Exact same problem. Thinkpad T61, with Atheros. 

Happened only with an upgrade to Jaunty. Anyone found a solution yet?

---

### Post by MasterPoulos89 on 2009-05-11
I didn't use wireless in Intrepid but I'm using wireless in Jaunty and I have this problem. Hope something is done about this cause its annoying.

---

### Post by t0mppa on 2009-05-11
Sounds like something that might not have a quick and simple fix around the corner. You people should divert your anger by going to file a bug report about it or if one already exists, make sure they know how common this issue is in order to get the ball rolling towards a fix. This is just a forum for asking help, the developers don't read every post out here.

---

### Post by MasterPoulos89 on 2009-05-11
I'm having trouble finding how to file a bug report. i never done so cause most of my problems have been solved. Can someone point me in the right direction.

---

### Post by ubuser_7 on 2009-05-11
The report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342802](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342802)

It becomes very similar to my problem later. 


>  Fabio Malagoli Panico  wrote on 2009-04-15:  (permalink)

    * dmesg.log (43.2 KiB, text/plain)

=== Wifi not working properlly on MacBook Pro 1,1 running Jaunty Beta ===

I had Ubuntu 8.10 running and the Wifi worked fine. I've installed Jaunty 9.04 Beta (and all updates) and although wifi is working, I notice several problems:

1. Keeps disconnecting and reconnecting without reason;

2. Sometimes it won't reconnect and keeps asking for the WEP/WPA password (this happens specially after resuming from suspension); and

3. Sometimes the Wifi card is not detected, at all, even after reboot.
3.1. Yesterday, after a resume from suspend, wifi couldn't connect, so I mannualy disable by right-clicking on the network applet and unchecking the box "enable wireless" (or something like this). After few minutes I tried to re-unable it, but it wasn't able to detect any network.
3.2. So I reboot into MacOS and even then the computer showed "no wifi card detected", so I had to reset the PRAM (alt + command + P + R) and then it was detected.

4. I've notice that there was an option of installing an alternative proprietary driver (mad-wifi if I'm not wrong), but I didn't.

5. Right now, after resuming from suspension, the Wifi was unable to reconnect to the any network (although able to detect them), so I turn it of and return it on, but the card was no long detect.  I reboot but even then the wifi card was not detect.

The commands outputs down below reflects this state (wifi card not detected). Dmesg.log as attached also reflect this present situation.

I very occasionally have those card not detected things, but mostly I am limited to 1 and 2.

I have subscribed to this thread and am actually looking for existing bugs, because I am almost certain this must have already been filed.

---

### Post by l-x-l on 2009-05-11
Same problem here with my connection. I've tried a number of solutions presented on this site to no avail. So far I've:

Disable Network Manager & use WICD
Disabled ipv6
Reduced the Beacon Interval on my router
Made my router a dedicated wireless G instead of dual G & N
Updated the iwlagn driver
Swiched my router channel
Moved my router around the room

None of them have worked. I still get regular connection drops. No problems of this kind when I use my othe OS (Vista).

---

### Post by ubuser_7 on 2009-05-12
Yea, I tried a few of them, but I havent disable my ipv6 yet. Another thing I noted is that its difficult to reproduce this bug. Like I am running fine for a day now, with very similar situations. 

however as t0mppa mentioned, no pointing ranting here. we should provide as much info/help we can in the bug reports.

---

### Post by db260179 on 2009-05-12
I'm afraid the new linux kernels are suffering from the wireless gremlins.

Im not sure what chipset you have in your Asus laptop?

My advice is to install the linux-backports-modules or the latest compat-wireless to fix these issues.

sudo apt-get install linux-backports-modules

or

(make sure to uninstall the backports if you are going to install compat-wireless)

wget wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2 ~

then extract the archive, then
make
sudo make install

> **lampak said:**
> I have a problem with my wireless connection - from time to time it disconnects and I have to reconnect manually. I hadn't had such problems before upgrading to Jaunty and I do not have them in Windows, so it is rather not a hardware issue. The signal strength is good. I use a built-in WiFi in my Asus laptop. Any ideas what can be the reason?

---

### Post by t0mppa on 2009-05-12
> **MasterPoulos89 said:**
> I'm having trouble finding how to file a bug report. i never done so cause most of my problems have been solved. Can someone point me in the right direction.
[URL="https://launchpad.net/ubuntu/+bugs"]
Here's[/URL] the address for the Ubuntu bugs listing, you'll need to register an account on launchpad to add your input. And [here's]("https://help.ubuntu.com/community/ReportingBugs") something you should read before posting anything. Also make sure you search first, to find out if the issue is already reported, so that you don't just post a duplicate of an existing bug report.

The more information the developers get on the issue, the easier it is for them to reproduce it and get to the bottom of what causes it and why.

---

### Post by MasterPoulos89 on 2009-05-13
I read somewhere someone said they were told to change the MTU from their router to 1400. So instead of changing the router I changed the MTU from the Network Manager to 1400 and its been a few hours now that I have not been disconnected. I think this is the solution.

I restarted after changing it just to make sure it registered.

---

### Post by MasterPoulos89 on 2009-05-13
Guess Not.......I got disconnected again.

---

### Post by noblerabbit on 2009-05-17
mine has been at 13% and breaking connection very often.

i downgraded to ibex but the same problem happened.

then i downgraded again, back to Hardy, where it works perfectly!

guess it isnt just me then.

---

### Post by blackjack3 on 2009-05-17
I did a fresh install of 9.04 and my wireless won't connect at all.

wireless was working flawless before.

---

### Post by t0mppa on 2009-05-17
> **blackjack3 said:**
> I did a fresh install of 9.04 and my wireless won't connect at all.

wireless was working flawless before.

Since you're not suffering from the same problem as described above (they can still connect, just get disconnected at random), why don't you make a new thread for this? The basic forum policy is one problem per thread for simplicity's sake. Also, post output of 'lshw -C network' and 'ifconfig' from the terminal to your new thread to give people an idea of what's wrong.

---

### Post by blackjack3 on 2009-05-17
I have never posted a bug report, do I need to regester to do this?

Thanks

jack

---

### Post by bwolf1 on 2009-05-17
Same problem here. I posted this thread [http://ubuntuforums.org/showthread.php?t=1161153](http://ubuntuforums.org/showthread.php?t=1161153) but nobody has replied--at least not yet. 

I have some interesting dmesg output. Maybe someone can tell me if it's helpful.

First, the output of dmesg | grep 3945 when the wireless is working:

```

[    9.632281] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.632283] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.632380] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.632394] iwl3945 0000:0b:00.0: setting latency timer to 64
[    9.632471] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.638969] iwl3945 0000:0b:00.0: irq 2297 for MSI/MSI-X
[    9.697472] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.698077] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.083533] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   71.775543] iwl3945: Radio Frequency Kill Switch is On:
[   76.092635] iwl3945: MAC is in deep sleep!
[   76.092737] iwl3945: MAC is in deep sleep!
[   76.092826] iwl3945: MAC is in deep sleep!

```Now the output of dmesg | grep 3945 after I recreate the problem by simply clicking on a YouTube video or two, to increase bandwidth usage:

```

[    9.632281] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.632283] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.632380] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.632394] iwl3945 0000:0b:00.0: setting latency timer to 64
[    9.632471] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.638969] iwl3945 0000:0b:00.0: irq 2297 for MSI/MSI-X
[    9.697472] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.698077] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.083533] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   71.775543] iwl3945: Radio Frequency Kill Switch is On:
[   76.092635] iwl3945: MAC is in deep sleep!
[   76.092737] iwl3945: MAC is in deep sleep!
[   76.092826] iwl3945: MAC is in deep sleep!
[ 9160.108462] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 9160.108478] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0276 ser 0x0000004B
[ 9160.112133] iwl3945: Can't stop Rx DMA.

```I'm running:

```

lsb_release -d

Description:    Ubuntu 9.04

``````

uname -mr

2.6.28-11-generic i686

```

---

### Post by sameerorth on 2009-05-17
I have the same problem in Ubutu itrepid after installing updates and the message is serial port disconnected. Modem hangup. Further at times it gets reconnected automatically withou any action from my partand some times I have to manually connect it.
Dell Inspiron 700m with Intel Wireless builin adaptor with Linksys ADSL modem

---

### Post by pieguy on 2009-05-21
I just put 9.04 on my laptop and it keeps dropping wireless connection.  And it WONT reconnect unless I shutdown and start.  9.04 is not on par or better then previous version.  Regression.

edit: christ, now it wont even connect anymore after shutdown...

---

### Post by Rofko on 2009-05-23
This seems to be a HUGE problem. I have this afflicting two computers now. Jaunty has given me all kinds if problems in general - I am a very long term linux and ubuntu user - but this one is frankly terrible. There are many many many bug reports reporting this, and many complaints of similar problems. How many people can't even get online to complain about it? There are several foprum threads on this on thius site now with many views, and goodness knows how many searches on google. This has to be sorted out very very quickly. not ebing able to get onto the internet AT ALL is franly about the worst bug you could have with an operating system. Sorry for this tone everyone, but this is not an easy situation. Like most people, my job depends on access to the internet, and I don not have a windows partition or any such luxury.

---

### Post by emeraldgirl08 on 2009-05-23
I've been having that problem almost everytime I log into Ibex. I was just going to post a thread about this also. It's beginning to get a little irritating and is making me consider going to the xp side of my boot!

Downgrading or upgrading? UGH. I may do the downgrade to 8.04 because of the long Term Service. I'm wondering also which cards this is affecting. Maybe someone should create a poll of some sort.

---

### Post by wintermute000 on 2009-05-25
Another afflicted user here. IBM T41 w/ atheros, worked fine in intrepid with the manual modprobe script workaround to sort the no wireless on suspend issue. Heck it worked fine in Fedora 7, 8 and 9 which is usually far more fiddly than Ubuntu when it comes to hardware issues

Of course, the ultimate insult..... it works fine in XP :( 

I would stick with intrepid except I want to play around with KDE4 more and having the latest and greatest 4.2.x fully integrated is much nicer than the usual mucking around you get when you manually upgrade major DE versions (of course, 4.1 is not an option ;) )

Rofko, if your job depends on wifi and you are stuck with the hardware you have, I highly recommend finding yourself a USB adapter with rock solid linux support like a ralink chipset as a cheap fallback. Of course with USB wireless sticks its a bit hit and miss since vendors will gladly shove an entirely different chipset on what is otherwise an identical model stick, even identical hardware revisions (heck with some its pot luck and there's no way of telling the chipset on the box).  I found this out the hard way when I went USB adaptor hunting for aircrack fun and games

---

### Post by Rofko on 2009-05-25
johannlo
thanks for the advice. Actually this problem is not due to the wireless network card, so a usb one would not make any difference. Indeed, I own one which is supported perfectly by ubuntu. It throws me off my network just the same, and won't let me reconnect.
is anyone close to understanding this problem, does anyone know?

---

### Post by Diamond B on 2009-05-25
I'm having the exact same issues, had them with Intrepid as well.  When my system starts up my wireless connection works fine (though at low quality) after a completely random amount of time it disconnects and will not reconnect.  I manually restart the connection, but the problem will just return.  I've tried two different wireless locations - thinking maybe it was my router - with both WEP and WPA encryption with the same results.

The annoying thing is the wireless worked just fine in Windows XP and as I'm washing my hands of that OS I don't want to resort to ndiswrapper.

Here's the info on my card, I'm hoping someone out there has some advice.
---
Dell Inspiron 8200

$ lspci
07:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 11)

$ iwconfig
wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod
mac80211              217208  1 adm8211
eeprom_93cx6           10240  1 adm8211
cfg80211               38032  2 adm8211,mac80211

$ dmesg
[   16.030871] adm8211 0000:07:00.0: enabling device (0000 -> 0003)
[   16.030892] adm8211 0000:07:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   16.030916] adm8211 0000:07:00.0: setting latency timer to 64
[   16.071211] 0000:07:00.0 (adm8211): Channel range: 1 - 11
[   16.071217] 0000:07:00.0 (adm8211): RFtype=1 BBPtype=1 Specific BBP=0 Transceiver=0
[  289.096105] phy0: adm8211_write_bbp(17,128) failed postwrite (reg=0x20a61180)
[  289.176262] phy0: adm8211_write_bbp(20,20) failed postwrite (reg=0x20a61414)
[  289.256113] phy0: adm8211_write_bbp(21,80) failed postwrite (reg=0x20a61550)
[  289.336124] phy0: adm8211_write_bbp(28,0) failed postwrite (reg=0x20a61c00)
[  289.416108] phy0: adm8211_write_bbp(29,132) failed postwrite (reg=0x20a61d84)

$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 11
       serial: 00:e0:98:a3:64:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 module=adm8211 multicast=yes wireless=IEEE 802.11b

$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     No scan results
pan0      Interface doesn't support scanning.

$ lsb_release -d
Ubuntu 9.04

$ uname -mr
2.6.28-11-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...  
Ignoring unknown interface eth0=eth0.

---

### Post by knappers on 2009-05-26
I've started having this problem about a month after upgrading to jaunty, which is very strange, just drops the connection every two minutes.
I reverted to the previous kernel, thought it had cured it but after an hour or so it started doing it again. Even the network manager wouldn't add it to the list for a while, even manual config didn't kick it in so i had two wireless connections the same name and config.
I loved the wireless in ubuntu it connected just as all the desktop was up, rather than windows messing about for ages and then picking the wrong one, because i had bthomehub and btopenzone.
 
I just can't tell if it's my wifi card that's dying, it's an old dell inspiron 1300 laptop, and the wife has hammered it, there's more food & fag ash in the keyboard than in the fridge or ashtray.
 
If anyone has any great ideas as to how to fix this problem i'll keep watching.

---

### Post by Rofko on 2009-05-27
Okay, some reading suggests this is a problem with ipv6 in the latest kernel. you need to disable ipv6. 

this page discusses it and suggests a solution.

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

i have to confess my ignorance and hesitance when it comes to attempting something like this. anyone else want to give it a try?

---

### Post by Rofko on 2009-05-27
Okay, some reading suggests this is a problem with ipv6 in the latest kernel. you need to disable ipv6. 

this page discusses it and suggests a solution.

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

i have to confess my ignorance and hesitance when it comes to attempting something like this. anyone else want to give it a try?

---

### Post by Mars73 on 2009-05-27
> **Rofko said:**
> Okay, some reading suggests this is a problem with ipv6 in the latest kernel. you need to disable ipv6. 

this page discusses it and suggests a solution.

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

i have to confess my ignorance and hesitance when it comes to attempting something like this. anyone else want to give it a try?

Well I've just installed one of the latest kernels (2.6.29.4) and did all the things that was in that side. Took me 5 or 10 minutes so it was quite easy to do.
I'm now going to watch a movie which always went wrong (loosing connection and after a while it reconnected). You can imagine how irritating it is that after a few minutes a movie stops and you can watch it again after a few seconds/minutes, so I want to get this fixed!

---

### Post by knappers on 2009-05-27
Done some messing around and the connection lasts for longer now, but then has spates of dropping out but connects quite quickly again when i choose my broadband from the wireless list.

i deactivated my broadcom b43 driver and reloaded it through thehardware  drivers and restarted.

Given this a try a try

[http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux/](http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux/)

i'll see how it goes for a few days, disables ipv6 which may be causing conflict problems.

My son has a my old desktop with ubuntu 9.04 playing WOW in wine  and a belkin wireless usb on it and he doesn't have any problems whatsoever the jammy sod, just this damn thing.

---

### Post by MasterPoulos89 on 2009-05-28
If that works thats seems good. Another way that fixed it for me that many may not want to do was update my kernel to 2.6.30rc7.

Go to this site [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) and download KernelCheck.

The version from the site may not work on jaunty. In that case type this in terminal.

sudo apt-get install bzr
bzr branch lp:kernelcheck
cd kernelcheck
sudo python setup.py install

Then go to System Tools/kernelCheck. 

For the website version click Get Kernel Information and it will say the update is 2.6.29. You may need an advanced option to get 2.6.30 I don't remember. Then on the top click Program then Build Kernel or what ever it says.

For the terminal version click Forward then Get Kernel Information then Forward then Custom compilation then forward than Stable Development Prepatch then Forward Forward and Apply.

I have restricted Nvidia drivers and I got an error about xserver but no problem just rebooted and re-enabled my drivers and rebooted again. If you want you could deactivate your restricted drivers before hand and reactivate after reboot.

This method works pretty perfectly and nothing broke and nothing seems not compatible. So all is good.

Hope you have the same success I have.


Edit: I may have replied too quickly. Give me a day or two to verify that my wifi problem is solved. If its not its definitely better.

Edit: OK..... Wifi still disconnects. Guess this post doesn't belong here. It still fixed my Microsoft Lifecam though. So its good for something.

---

### Post by Rofko on 2009-05-28
Sorry for hogging this thread when essentially I am adding little-to-no insight. 

Does anyone have any ideas about how to DIAGNOSE this problem? 

Deactivating ipv6 definitely does not solve the problem for me. 

This thread is going to hit 2000 views soon, and we are no nearer a solution. There are several other threads on here with the same issue, plus numerous bug reports. No-one seems to be able to put their finger on what the problem is. I am going to have to install another OS to ensure connectivity, which, aside from being a pain, is also admitting defeat!

Networking is definitely not my strong suit, so if someone would care to suggest a means of discovering the issue, I will gladly (!) spend some time diagnosing!

---

### Post by knappers on 2009-05-28
One thing I did see in my syslog is says that the router is out of range and disconnects and then starts the reconnection process.
 
Don't know if this is what everybody else is getting in their syslog?
 
But this seems to indicate that it is a recieve problem rather than a send problem, as my other box upstairs doesn't fail at all.
 
I will investigate this a bit further.

---

### Post by MasterPoulos89 on 2009-05-28
knappers, the site in your post is not for Jaunty. Its different to disable IPV6 now. I just found the right link to disable IPV6 in Jaunty. Doesn't necessarily mean its ganna fix our problem but thats what we all gotta find out. Here is the site.

[http://webupd8.blogspot.com/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html](http://webupd8.blogspot.com/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html)

Basically all you have to do is type the following in terminal and IPV6 is disabled.

sudo su -
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

Check the site to understand it better.

Now we wait and see if that fixes the problem.

---

### Post by Rofko on 2009-05-28
MasterPoulos89

Yeah, I thought that that hd solved my problem when I tried it out yesterday, but no. It would seem ipv6 is not the issue.

Chili555's suggestions on this thread seem quite promising though:
[http://ubuntuforums.org/showthread.php?t=1150544](http://ubuntuforums.org/showthread.php?t=1150544)

In the full awareness that my connection will fail right now as I right this, his solutions appear to have worked.

---

### Post by MasterPoulos89 on 2009-05-28
> **Rofko said:**
> MasterPoulos89

Yeah, I thought that that hd solved my problem when I tried it out yesterday, but no. It would seem ipv6 is not the issue.

Chili555's suggestions on this thread seem quite promising though:
[http://ubuntuforums.org/showthread.php?t=1150544](http://ubuntuforums.org/showthread.php?t=1150544)

In the full awareness that my connection will fail right now as I right this, his solutions appear to have worked.


My wireless card uses the RALINK drivers. I have RT2500 wireless card. I dont think Chili555's suggestion applies to me.

---

### Post by Rofko on 2009-05-28
MasterPoulos89, and anyone else. Could you post your dmesg output?

Here is the end of mine:

[ 5843.032106] wlan0: associate with AP xxx
[ 5843.055180] wlan0: RX AssocResp from xxx (capab=0x401 status=0 aid=1)
[ 5843.055187] wlan0: associated
[ 5843.055808] wlan0: disassociating by local choice (reason=3)
[ 5849.517017] wlan0: authenticate with AP xxx
[ 5849.520604] wlan0: authenticated
[ 5849.520614] wlan0: associate with AP xxx
[ 5849.546949] wlan0: RX ReassocResp from xxx (capab=0x401 status=0 aid=1)
[ 5849.546957] wlan0: associated

Well, for now, as you can see by the last line, I am connected. Does anyone know what this reason=3 is exactly? I am trying to find out. There are quite a few posts around with this problem discussed, with the consensus being that the issue is with the drivers. 

linux-backports-modules-jaunty includes newer drivers. What happens if people install this package?

---

### Post by MasterPoulos89 on 2009-05-28
Sounds like it could help. I want to see first if Disabling IPV6 worked for me maybe. If I get disconnected again I may try to install that.

Here is the end of my dmesg command.


[ 2731.273909] wlan0: associated
[ 2738.825483] wlan0: disassociating by local choice (reason=3)
[ 2751.672232] wlan0: authenticate with xxx
[ 2751.673698] wlan0: authenticated
[ 2751.673700] wlan0: associate with AP xxx
[ 2751.676058] wlan0: RX AssocResp from xxx (capab=0x411 status=0 aid=1)
[ 2751.676061] wlan0: associated
[ 2760.470037] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[10040.335023] wlan0: no probe response from AP xxx - disassociating
[10045.511946] wlan0: deauthenticated (Reason: 3)
[10054.669353] wlan0: authenticate with AP xxx
[10054.671351] wlan0: authenticate with AP xxx
[10054.674628] wlan0: authenticated
[10054.674631] wlan0: associate with AP xxx
[10054.678760] wlan0: RX ReassocResp from xxx (capab=0x411 status=0 aid=1)
[10054.678763] wlan0: associated
[12882.205028] usb 3-1: reset full speed USB device using uhci_hcd and address 2

---

### Post by Rofko on 2009-05-28
sorry - disconnect (for another reason!) caused a double posting!

---

### Post by MasterPoulos89 on 2009-05-28
I got disconnected again. So I re-enabled IPV6 and I installed 

linux-backports-modules-jaunty

And now I'm going to restart to make sure it takes effect.

I'll post my results if i get disconnected or not.

---

### Post by Rofko on 2009-05-28
Any luck?
It seems to have worked for me.

However (!) the signal strength of my network is now far lower running the latest kernel (confirmed by the "sudo iwlist wlan0 scan" output) compared to running the previous kernel, causing (I can just tell) a thousand other problems which I will spend this weekend solving.

---

### Post by Mars73 on 2009-05-28
> **Rofko said:**
> Any luck?
It seems to have worked for me.

However (!) the signal strength of my network is now far lower running the latest kernel (confirmed by the "sudo iwlist wlan0 scan" output) compared to running the previous kernel, causing (I can just tell) a thousand other problems which I will spend this weekend solving.

It's driving me crazy.
With running one of the latest kernels I have a very very low upload speed (download is okay, not super but okay) and this is giving all sorts of problems with streaming video to my xbox downstairs.
It's still disconnecting btw, with ipv6 disabled and a newer kernel. Plus now a very low upload and download speed. Guess thats why the kernel version is a bit behind, it's not tested thoroughly or something like that.
I'm up to point that I'm going to install 8.04 and regularly check these pages. I'm afraid though that when I install 8.04 (or 8.10) with newer updates the problem comes back.
On Network Tools when choosing my wlan0 it gives a 1Mbps link (on the problematic PC), whereas my laptop gives a solid 54Mbps.
If anyone has any ideas I'm all ears.

---

### Post by Rofko on 2009-05-28
mars73

post your output from > sudo iwlist wlan0 scan

did you try installing linux-backports-modules-jaunty to get newer drivers?

---

### Post by MasterPoulos89 on 2009-05-28
Installing the linux-backports-modules-jaunty package seems to of worked for me too.

As far as low signal due to the kernel, I am running  2.6.30rc7 and no problems what so ever.

Run in terminal:

iwconfig 

if bit rate is 1 MB/s then run in terminal:

sudo iwconfig wlan0 rate 54M
sudo gedit /etc/network/interfaces

then add the line

pre-up iwconfig wlan0 rate 54M

to the end and save.

then run in terminal:

sudo /etc/init.d/networking restart


If it is already 54 MB/s then I don't know

---

### Post by MasterPoulos89 on 2009-05-28
Any luck......hope you guys aren't downgrading......Mars73, I explained above how to fix your 1 MB/s problem above did you try it. As far as your xbox......I don't get.......do you have ubuntu installed on your xbox......if so maybe same solution.

If not same solution there may be a patch for xbox and new kernel. I don't know how that works cause I don't have xbox

---

### Post by MasterPoulos89 on 2009-05-28
Did you also try it Rofko it may be why you have low signal.

---

### Post by ZeroCool69 on 2009-05-28
Wow, it actually worked!

I've been trying to solve this issue for a while now.

I installed the backports, changed the rate to 54M, edited /interfaces, and restarted.

PRESTO!

Thanks a lot. I'm now showing a 54M bit rate in iwconfig. And my connection hasn't dropped after doing a few heavy workload tasks. Fingers crossed for sustained wireless.

---

### Post by Rofko on 2009-05-28
Yeah, I was just trying the same trick actually, masterpoulos89. You missed out the command in your code (just in case anyone is cutting and pasting: so something like sudo gedit /etc/network/interfaces )
I have seen some issues with low signal strength elsewhere - i'll have a look. For now it looks like everything is working pretty well though. Thanks for the input everyone.

---

### Post by Mars73 on 2009-05-28
> **Rofko said:**
> mars73

post your output from 

did you try installing linux-backports-modules-jaunty to get newer drivers?

I installed the kernel from the link that was a few pages back.

sudo iwlist wlan0 scan gives me:

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:22:AA:75
                    ESSID:"frits"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/100  Signal level:-74 dBm  
                    Encryption key:on
                    IE: Unknown: 00056672697473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0C12F00002A4640027A400004243C80062326400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD1E000AF50B10A4F013C0414E495F56455253494F4E000A0200C00003010305
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F0002A4640027A400004243C80062326400
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000133d0181
                    Extra: Last beacon: 1064ms ago

iwconfig gives me indeed 1Mbps.
After giving a:
sudo iwconfig wlan0 rate 54M

it gave me my 54M and upload speed back again. Thanks!
I also added it to interfaces. I'll see if this gives any improvements, if not I'll try an even newer kernel (the 30RC7 as you mentioned).

---

### Post by ZeroCool69 on 2009-05-28
Interestingly, I'm picking up some of my neighbors' wifi networks at a stronger signal than my own! 

Go figure, I'll try roaming around. Though it does seem a bit low compared to signal strength in Vista.

I believe you guys were having some similar issues?

---

### Post by aidanb on 2009-05-28
I've been having similar problems.  I'm going to try the fixes suggested in this thread, but I wanted to ask people, has anyone who's had this problem had trouble with wired connections?  I just installed Ubuntu on my MacBook last Saturday, and the ethernet connection worked fine until Monday morning, and since then, the Network Manager applet says "disconnected" no matter what I do.  I'm on a college network where your computer's MAC address is tied to the port you use in the dorms, but that shouldn't change from switching OSs...

---

### Post by MasterPoulos89 on 2009-05-28
> **Rofko said:**
> Yeah, I was just trying the same trick actually, masterpoulos89. You missed out the command in your code (just in case anyone is cutting and pasting: so something like sudo gedit /etc/network/interfaces )
I have seen some issues with low signal strength elsewhere - i'll have a look. For now it looks like everything is working pretty well though. Thanks for the input everyone.


Sorry about the command. I fixed it for others. Thanks for letting me know.

---

### Post by Rofko on 2009-05-28
aidanb

check out this thread, which is about a similar situation with wired networks:

[http://ubuntuforums.org/showthread.php?t=1141608](http://ubuntuforums.org/showthread.php?t=1141608)

---

### Post by MasterPoulos89 on 2009-05-28
I just like to sum up. The problem of this post was WiFi disconnecting and the solution is to install 

linux-backports-modules-jaunty

There are enough post on this same topic and I think someone could of figured this out sooner. The backports are there for a reason.

So since it was Rofko that pointed this out he gets credit for solving this post.

So Kudos to Rofko

---

### Post by MasterPoulos89 on 2009-05-28
I got disconnected.......It took a while but it happened. So is it solved? Is it not solved?

I guess were not done. Unless its only me now. Guess I'll have to wait to see if it happens again or if someone else still has a problem.

---

### Post by Rofko on 2009-05-28
Is this dmesg output the same? The disconnection reason=3 and all? For me it's working well. It disconnected once, but allowed me to reconnect immediately. Previously it disconnected after two minutes, then wouldn't let me back on at all, would sometimes disable wireless, and would require a restart, which would, in turn, sometimes turn off wireless completely. So in any case, things are infinitely better, even if I have the odd disconnect - that I can live with. The drivers seem to have improved even if they are still not back to how well it worked in 8.10.

---

### Post by MasterPoulos89 on 2009-05-28
My last disconnect was a while ago. dmesg doesn't show reason: 3 and doesn't even show the last time I disconnected.

I can say it is happening a lot less and it does reconnect right away. So I guess we could call it a win.

---

### Post by aidanb on 2009-05-29
I followed the instructions from the link from Rofko's first post
(ie, updating to a 2.6.29.3 or later kernel and disabling ipv6)
and it seems to work fine now.  Thanks for the link!

---

### Post by MasterPoulos89 on 2009-05-29
I left my computer on when I went to sleep and when I woke up I still had connection. That normally doesn't happen for me. So i guess even if it does disconnect once or twice in a long period of time it is normal or at least not a problem. So I still say it is solved.

All I did to get it working better is upgrade my kernel to 2.6.30rc7 and also installed linux-backports-modules-jaunty.

I think both had a positive effect on my wireless connection.

I'm just summing up what worked for me.

---

### Post by Dragonbite on 2009-05-29
Oh, I was afraid I was the only person noticing this after upgrading from Hardy! 

Which page has Rofko's first post?

---

### Post by MasterPoulos89 on 2009-05-29
> **Dragonbite said:**
> Oh, I was afraid I was the only person noticing this after upgrading from Hardy! 

Which page has Rofko's first post?

I think aidanb  is talking about this post.

> **Rofko said:**
> Okay, some reading suggests this is a problem with ipv6 in the latest kernel. you need to disable ipv6. 

this page discusses it and suggests a solution.

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

i have to confess my ignorance and hesitance when it comes to attempting something like this. anyone else want to give it a try?


This didn't work for me but i guess it may work for others.

If it doesn't work you can upgrade your kernel with kernelcheck as I mentioned on page 4.

---

### Post by Dragonbite on 2009-05-29
> **MasterPoulos89 said:**
> I think aidanb  is talking about this post.




This didn't work for me but i guess it may work for others.

If it doesn't work you can upgrade your kernel with kernelcheck as I mentioned on page 4.

Thanks, I'll have to try it out when I get home.

---

### Post by javahollic on 2009-05-29
Ahh, I am not a alone, 85 pings on the wall 85 pings alive, then kaput.  Fortunately (and strangely) I have a 9.04 laptop that works a treat.  64bit? BelkinG? add myself to the list for future info.

---

### Post by Mars73 on 2009-05-29
> **javahollic said:**
> Ahh, I am not a alone, 85 pings on the wall 85 pings alive, then kaput.  Fortunately (and strangely) I have a 9.04 laptop that works a treat.  64bit? BelkinG? add myself to the list for future info.

After updating to the latest kernel, installing linux backports, disabling ipv6, using nm or wicd I still got the disconnects.
I got fed up with it and installed 8.10 amd64 and everything runs smooth again.
With 9.04 I couldn't watch 10 mins of movie on my xbox downstairs, streaming it from the pc upstairs with 9.04. It uses samba.
With 8.10 it runs superb for a day now. I haven't installed any updates to 8.10 (300 waiting) as I wanted to see if this one works. I'm afraid it kills it again. I suspect the whole problem lies in the kernel, but that is just guessing from my part.
I still use 9.04 on my laptop where it seems to work okay.
I'll check this thread regularly to see if there is any progress on it (although it seems some of you have fixed it, it didn't work for me).
(BelkinG and 64bits as well over here)

---

### Post by MasterPoulos89 on 2009-05-29
I wanna take back what I said earlier about it not being a problem for me anymore. Although my wireless may disconnect a little less it is still too often. 

One thing I did realize from other posts is that IPV6 is built into the kernel and that makes it harder to disable or at least changes the method you need to use. 

Even if you think you disabled IPV6 it may still be enabled even if the post says for Jaunty.

If you think you have IPV6 disabled you may not so to find out type this in terminal.

ip a | grep inet6

If you get any reply at all (like, 1/28 bla bla) it is enabled.
If you get no reply at all then it is disabled.

With IPV6 enabled your Internet first searches a site for IPV6 capabilities and if not supported it goes to the IPV4 protocol. This adds an unnecessary delay.

IPV6 is a better protocol to use for the sites that support it which at the moment is almost none. So until Internet 2 comes out to secure and enslave the world :frown: IPV6 is not necessary.

The following is the method that worked for me to disable IPV6 and might help with this annoying wireless problem.

type in terminal:

sudo gedit /etc/sysctl.conf

and add the line:

net.ipv6.conf.all.disable_ipv6=1

to the end.

Then reboot and then type in terminal:

ip a | grep inet6

If any response then it did not work for you. If no response then you finally disabled IPV6.

Hope this solves it.

Edit: sad to say that while writing this post I got disconnected. Guess IPV6 isn't the problem. At least without IPV6 you can browse the web a little faster when you do have connection:).

---

### Post by Rofko on 2009-05-30
mine has been connected for over 24 hrs non stop after installng the backports. I think i have just got lucky with the drivers with my wireless card compared to other people. are people still getting the reason=3 for disconnect with dmesg? i am getting something strange with my wireless not being ready when the machine boots up. I have some swearwords I want to share but I'll save it...

---

### Post by MasterPoulos89 on 2009-05-30
> **Rofko said:**
> mine has been connected for over 24 hrs non stop after installng the backports. I think i have just got lucky with the drivers with my wireless card compared to other people. are people still getting the reason=3 for disconnect with dmesg? i am getting something strange with my wireless not being ready when the machine boots up. I have some swearwords I want to share but I'll save it...


I did find the same Reason:3 from dmesg. Not to much effective support for that error online.

You must have a different driver as you said. I have RT2500 as I mentioned earlier what driver to you have so we know what works and what doesn't.

If any one needs to know what driver your Internet Interfaces use you type this in terminal:

sudo lshw -class network

look for Wireless interface and where it says product it should tell you your driver.

It could help if people said the driver they had and if they get disconnected or not.

Edit: Make sure to first install linux-backports-modules-jaunty then post driver results

---

### Post by knappers on 2009-05-30
I installed the backports and the timeouts increased to make it absolutely useless, I booted into windows and still got the same thing and even connecting to some silly persons unprotected router as well, so it was either the wifi card or maybe the router,I uninstalled backports andI reset the router yesterday evening and up to now crossed fingers i haven't been disconnected, you know whats going to happen now that i've said that :p
but it's the stabelist it's been for the past week anyway.

---

### Post by Azmaedra on 2009-05-31
My problem is a little different than the ones posted above, but when I log in and ubuntu (9.04) is completely loaded to the desktop, my wireless (which I have set to automatically connect, and has the password given to me when I set it up [a bunch of letters and numbers]) asks for access to the keyring. I type in the password every time, but there is no option for anything like 'save choice for future logins.' Also, whenever I log on the resolution goes back to a very small number which makes even the simplest of tasks very difficult because not all of the choices in windows (such as apply, or reset) can even be seen. I change it every time, but it always goes back upon reboot. (My graphics driver doesn't have the specifications to use the display applet, so it goes to the NVIDIA X Server Settings instead.

P.S. I started using Ubuntu yesterday, I've been sick of windows for a long time.

---

### Post by MasterPoulos89 on 2009-05-31
> **Azmaedra said:**
> My problem is a little different than the ones posted above, but when I log in and ubuntu (9.04) is completely loaded to the desktop, my wireless (which I have set to automatically connect, and has the password given to me when I set it up [a bunch of letters and numbers]) asks for access to the keyring. I type in the password every time, but there is no option for anything like 'save choice for future logins.' Also, whenever I log on the resolution goes back to a very small number which makes even the simplest of tasks very difficult because not all of the choices in windows (such as apply, or reset) can even be seen. I change it every time, but it always goes back upon reboot. (My graphics driver doesn't have the specifications to use the display applet, so it goes to the NVIDIA X Server Settings instead.

P.S. I started using Ubuntu yesterday, I've been sick of windows for a long time.


I don't think this is the right thread for that but I'll solve all your problems here anyway.

For the keyring the way I got around that is I left the keyring blank. It has nothing to do with your connection to your router so I think its just being too over protective anyway.

To remove your keyring password go to applications/accessories/passwords and encryption keys. Then Click the passwords tab and delete what ever is in there. Then when you try reconnecting to your router it should ask you to make a keyring pass again. Just leave it blank.

On to your resolution problem. type in terminal:

gksu /usr/bin/nvidia-settings

Choose your screen display size click apply then click "Save to X Configuration File". That solves that one.

All done.

---

### Post by MasterPoulos89 on 2009-05-31
OK.....back to this topic. I know I posted quit a bit in this thread without solving the problem but I'm just trying to solve this. Its annoying me.

I believe I solved this now once and for all. For me anyway. Installing linux-backports-modules-jaunty seems to only of worked for Rofko. Some may call Rofko lucky and others may hate him for being so lucky. I'm ganna try to even everything out. If the backports don't help you you could try this.

I disabled my password from my router and enabled Mac Address Filtering. This only allows the Mac Addresses you specify.

First to access your router type your gateway into firefox's address bar. Log in. Then I went to Wireless tab then Wireless Network Access and from there I selected enable and typed in my wireless cards Mac Address which you can obtain from typing in terminal:

ifconfig

Mine was labeled HWaddr. Then disable your wireless security password. if you have more then one wireless computers add there Mac Address too.

This proses will probably be a little different on your router.

Post your results so we know if this is solved or not.

---

### Post by MasterPoulos89 on 2009-06-01
No one has replied so I don't if anyone else tested this method but I will now confirm that using the Mac Address Filtering does not cause any problems for my wireless in Ubuntu.

I've read on other posts that wpa/wpa2 had caused problems for Ubuntu in the past. I guess that is all it was.

Also I used to get a lower signal then one of my neighbours and now with Mac Address Filtering I get the same.....sometimes at least.

I guess no security at all will also work but is obviously not recommended.

If others have the same success as me then this post should be marked as solved.

---

### Post by Mars73 on 2009-06-01
> **MasterPoulos89 said:**
> No one has replied so I don't if anyone else tested this method but I will now confirm that using the Mac Address Filtering does not cause any problems for my wireless in Ubuntu.

I've read on other posts that wpa/wpa2 had caused problems for Ubuntu in the past. I guess that is all it was.

Also I used to get a lower signal then one of my neighbours and now with Mac Address Filtering I get the same.

I guess no security at all will also work but is obviously not recommended.

If others have the same success as me then this post should be marked as solved.

Well I've posted in here too but not with a solution either.
I've gone back to 8.10 with the standard kernel it came with (installed the other updates but not the kernel and NM) and it's now stable for the last 3 days. I've been able to stream movies without any problems to my xbox.
It's weird that the connection would be more stable if you use mac filtering. I guess I could try it with a live-CD.
For now I'm perfectly happy with 8.10 on my desktop upstairs and on my laptop 9.04 works also good.

---

### Post by venator260 on 2009-06-02
Installing the linux-backports-modules-jaunty package has given my card some improvement. I went from having 30-40 percent connection strength to 75-85 percent connection strength. My card uses the ath9k driver. The relevant output of lshw -C network is: 

```
*-network:0             
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:e5:fb:78:a6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless configuration: broadcast=yes driver=ath9k ip=192.168.2.2 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```

Hopefully this can be of some help to someone.

---

### Post by m.musashi on 2009-06-03
This all sounds similar to my issue. I have a iMac G5 and it's been buggy with wifi for a while. With Jaunty it seemed to finally work but now it won't connect at all. It keeps trying and then asks for the wpa password again (issue 2 from the first or second page of this thread).

Funny thing is when it asks again for the wpa password if I check the show password box it show a totally different and wrong password. I replace it with the right one and try again and same thing. It asks for the password again and has the wrong one.

I think the problem is related to wpa since it will connect just fine to an open network. EDIT: sorry. That's not true anymore. Seems it won't even connect to an open network now.

Several people said that installing the backports module fixed the problem. Does anyone have info on what exactly I need to do to do that? I couldn't find any real directions on the various links I followed.

Thanks.

---

### Post by MasterPoulos89 on 2009-06-03
> **m.musashi said:**
> This all sounds similar to my issue. I have a iMac G5 and it's been buggy with wifi for a while. With Jaunty it seemed to finally work but now it won't connect at all. It keeps trying and then asks for the wpa password again (issue 2 from the first or second page of this thread).

Funny thing is when it asks again for the wpa password if I check the show password box it show a totally different and wrong password. I replace it with the right one and try again and same thing. It asks for the password again and has the wrong one.

I think the problem is related to wpa since it will connect just fine to an open network. EDIT: sorry. That's not true anymore. Seems it won't even connect to an open network now.

Several people said that installing the backports module fixed the problem. Does anyone have info on what exactly I need to do to do that? I couldn't find any real directions on the various links I followed.

Thanks.


Any time you know the name of the package you want to install you go to terminal and type: "Sudo apt-get install (name of package).

For Jaunty backports you type in terminal:

sudo apt-get install linux-backports-modules-jaunty

If that doesn't work and you still can't even connect to unsecured networks then I don't what what the problem could be.

If you can connect to unsecured networks and its only your wpa password giving you problems you can always just dodge the problem by enabling Mac Address Filtering as I mentioned above.

---

### Post by m.musashi on 2009-06-03
> sudo apt-get install linux-backports-modules-jaunty

If that doesn't work and you still can't even connect to unsecured networks then I don't what what the problem could be.

Okay, tried that and things seemed even worse. Of course I had tried a number of other fixes including installing a new kernel so I may have goofed things up. I have done a new, clean install and I'm back to square one. Wifi "seems" to work but never connects. I'll try the backports again.

EDIT: Okay, installing the backports had no effect. Everything as before. I can see networks but when I try to connect it tries for a while and then asks for the password again (it's not the wrong one). It won't even connect to open networks. Definitely a step backwards from Intrepid which worked off and on. I think I need to just buy a USB wifi that is known to work well with Linux.

> If you can connect to unsecured networks and its only your wpa password giving you problems you can always just dodge the problem by enabling Mac Address Filtering as I mentioned above.

No, that was my mistake. It used to be that I could connect to open networks but after upgrading to Jaunty that no longer worked.

---

### Post by Gausian on 2009-06-04
Im using the Intel 4965agn card and have had some troubles as well with disconnections.

After trying many different things, my solution alhtough not 100% effective, is to force WPA2 and AES security.  Do not mix WPA/WPA2 or TKIP/AES.

I still occasionally get disconnected, but not nearly as often and my throughput has increased quite a bit as well.

---

### Post by MasterPoulos89 on 2009-06-04
> **m.musashi said:**
> Okay, tried that and things seemed even worse. Of course I had tried a number of other fixes including installing a new kernel so I may have goofed things up. I have done a new, clean install and I'm back to square one. Wifi "seems" to work but never connects. I'll try the backports again.

EDIT: Okay, installing the backports had no effect. Everything as before. I can see networks but when I try to connect it tries for a while and then asks for the password again (it's not the wrong one). It won't even connect to open networks. Definitely a step backwards from Intrepid which worked off and on. I think I need to just buy a USB wifi that is known to work well with Linux.



No, that was my mistake. It used to be that I could connect to open networks but after upgrading to Jaunty that no longer worked.


At this point I don't know too much but I would suggest looking at your interfaces file. Type in terminal:

sudo gedit /etc/network/interfaces

It should look like this:

auto lo
iface lo inet loopback

One of my laptops had more lines by default and wouldn't connect at all and I made it look like the above and it worked as it should. If that doesn't work I'm out of ideas.

---

### Post by MasterPoulos89 on 2009-06-04
> **Gausian said:**
> Im using the Intel 4965agn card and have had some troubles as well with disconnections.

After trying many different things, my solution alhtough not 100% effective, is to force WPA2 and AES security.  Do not mix WPA/WPA2 or TKIP/AES.

I still occasionally get disconnected, but not nearly as often and my throughput has increased quite a bit as well.



In your situation I suggest disabling password protection and enable Mac Address Filtering as I mentioned Above.

I have not been disconnected once since I did so. Why not give it a try?

---

### Post by Gausian on 2009-06-04
well i would like to maintain a bit of security on my wifi.  i live in the middle of a big city, with people all around.  mac spoofing is too easy to do nowadays.

i can live with the occasional disconnect is it means my network is relatively secure.

i thought that using the security combo of WPA2 and AES could help others having these issues, as it has worked much better than all the other combinations for me.

Im think that this problem is buried in WPA settings of the Gnome network manager, and not drivers, since many different hardware have issues and some have even had success with wicd instead.

---

### Post by MasterPoulos89 on 2009-06-04
I didn't realise that Mac Address Filtering would be less secure. If anything I would of thought it to be more secure. I don't know much about security.

As far as the source of the problem, It could be a problem with network manager, but whatever it is I don't know how to address it so I'm happy switching to Mac Address Filtering.

I guess if others do not want to do so then this problem is not solved.

---

### Post by m.musashi on 2009-06-04
> **MasterPoulos89 said:**
> At this point I don't know too much but I would suggest looking at your interfaces file. Type in terminal:

sudo gedit /etc/network/interfaces

It should look like this:

auto lo
iface lo inet loopback

One of my laptops had more lines by default and wouldn't connect at all and I made it look like the above and it worked as it should. If that doesn't work I'm out of ideas.

Thanks for trying. I've had lots of issues trying to run Ubuntu on an iMac so it's not an entirely new problem. However, after the upgrade to Jaunty it worked real well for about a day then nothing. I thought maybe the issues with the broadcom cards was solved but now I think it's actually worse. Not sure why it worked at first. I even did a new, clean install thinking it might work again for a bit but it didn't. Very odd.

---

### Post by m.musashi on 2009-06-04
> **MasterPoulos89 said:**
> I didn't realise that Mac Address Filtering would be less secure. If anything I would of thought it to be more secure. I don't know much about security.

Yeah, I used to think that too until someone explained it to me. Basically, mac filtering will prevent accidental connections but anyone wanting to hack your network won't have any problem. Also, without an encrypted connection you are sending a lot of info in the clear which could be intercepted. Chances are most people aren't trying but you never know.

---

### Post by shortridge11 on 2009-06-08
> **MasterPoulos89 said:**
> I didn't realise that Mac Address Filtering would be less secure. If anything I would of thought it to be more secure. I don't know much about security.

As far as the source of the problem, It could be a problem with network manager, but whatever it is I don't know how to address it so I'm happy switching to Mac Address Filtering.

I guess if others do not want to do so then this problem is not solved.

i would not recommend using mac filtering for security purposes.  All someone would have to do is sniff out a mac and change theirs to that one, and they'd be on your network.

---

### Post by shortridge11 on 2009-06-08
I'm having the same problem with wireless, I've got backports installed, newest kernel, even newest bios update as was pushed out a few days ago.  I'm running 9.04 on a Dell Studio XPS 1340, here's my basic info

I'm connecting to:

* Encryption: WPA Radius with TKIP key exchange
* Authentication: 802.1x with PEAP and MSCHAPv2
* SSID: xwireless

(it's a college campus)


This is my wireless card
Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Here is my basic wireless interface info

```
xxxxxx@xxxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"xwireless"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=30 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
xxxxxx@xxxxxxxxx:~$ sudo lshw -C network
[sudo] password for xxxxxx: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: xx:xx:xx:xx:xx:xx
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=xxx.xxx.xxx.xxx latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

running
2.6.28-11-generic i686
on
Description: Ubuntu 9.04


Let me know if i should post any more information.

Also, I've noticed i only have this problem when i'm connecting to a wpa enterprise network.  When i'm connecting to my wpa personal network at home i don't have any problems.  What types of networks are you all connecting to?

---

### Post by MasterPoulos89 on 2009-06-10
I connect to my home router. My home router gives my problems with WPA. I don't know why you only get problems from enterprise networks. I guess different hardware and drivers give slightly different problems.

---

### Post by shortridge11 on 2009-06-10
after extensive testing on my home network, i now realize the wireless disconnects on pre-shared key wpa (personal) as well, not just on wpa enterprise.

---

### Post by Mars73 on 2009-06-15
> **shortridge11 said:**
> after extensive testing on my home network, i now realize the wireless disconnects on pre-shared key wpa (personal) as well, not just on wpa enterprise.

A few weeks ago I tried without security, different channels, newer kernels etc etc and got disconnects whatever I did. I've returned to 8.10 3 weeks ago and the connection has since then not been disconnected.
Not much of an answer but there's something not okay with Jaunty, at least for my desktop upstairs, my laptop seems to work fine though.
I'll check regularly to see if there's any breakthrough

---

### Post by Lumb on 2009-06-15
I've also been having this problem. Will try changing to WPA2 and AES and see how it goes.

Edit: Nope, still persists.

---

### Post by npallett on 2009-06-17
I'm running Ubuntu Jaunty 9.04 on a HP Pavillion with a Broadcom 4318 Wireless Interface connecting to my router via WPA2, using the "b43" module and the "b43-firmware" package from the cafuego repository.

I have been suffering wireless disconnections as follows:

running the stock Jaunty kernel 2.6.28-11-generic - results in frequent wireless disconnections.

I enabled the "jaunty proposed" repository for updates, and tried the following kernels with interesting results as follows:
 
running the kernel 2.6.28-12-generic - no disconnections, works fine.

running the kernel 2.6.28-13-generic - frequent disconnections

I'm sticking with the 2.6.28-12-generic kernel for now as it seems reliable, and even my bluetooth usb dongle (Broadcom with ID 0a5c:200a) works fine after upgrading the "bluez" packages to 4.40

Hope this information helps others, and I would be interested to know what is changing between the above kernel versions, that causes wireless to break.

---

### Post by rbond on 2009-06-28
Posting in case this helps someone. I have been following a few wifi related threads because I had problems with wifi after upgrading to Jaunty.

In the past I had manually setup my wifi WPA settings in the /etc/network/interfaces file. Then I started using the Gnome Network Manager. My manual settings did not cause a problem until I upgraded to Jaunty. Just for the heck of it I removed the manual settings from my file and it fixed the problems that I had. 

I know that for some people this is a kernel issue, but for me it turned out to be a problem with Gnome Network Manager not liking my config settings.

If you are having problems and you had previously manually configured settings, back up your current copy and  try to revert to only auto settings such as this....

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface wlan1 inet dhcp

auto wlan1

```Hope this helps someone.

Forgot to note this: For the newbies - the eth1 and wlan1 values may be different on your machine. Use the network interface names for your machine.

---

### Post by lopezg on 2009-06-29
The problem is intermittent for me, so I can't be 100% certain, but replacing NetworkManager with WICD through the Synaptic Package Manager seems to have worked for now.

---

### Post by mana8000 on 2009-07-01
Not sure if this has been mentioned before on this thread (my apologies ahead of time)... if not then i'll share the following info... I have had this wifi issue (losing connection after a few minutes/hours) even though my icon shows I am still connected...since the last distro version (8.10 I believe) and also found no luck in fixing it in Jaunty Jackalope until now....  It seems like this has so far been the only fix that works on my computer... (HP Pavilion notebook dv9000t) It's simple really... what i did was go into **Synaptics Package Manager** and in the quick search field, type in **Wicd** and do a search for it... like me, you should only have one option come up.  Click on the the checkbox to select it and hit APPLY to install it.  When you do that, you will get a message that it conflicts with a network manager that is already installed on your computer and needs to be removed in order to install Wicd.... Click ok to remove the network manager already on your computer and replace with Wicd.  This is why we are installing it through the Synaptics Package Manager and not the Add/Remove Applications option.  Wicd conflicts with the network manager already installed on your computer.  Once it is done installing... you will notice that your original network icon next to the clock (or wherever you customized it to show) has disappeared.  That is normal, it freaked me out too when I saw that.  To get your internet Wifi/wired connection going again go to **APPLICATIONS** then **INTERNET** and scroll down to where it says **Wicd NETWORK MANAGER** and select it.  From here you will need to reconfigure your connection (eg. select your broadcasting router, enter your WEP key, etc.) also under preferences, I have the following boxes checked off... ***Always show wired interfaces and Automatically reconnect on connection loss*** that's it.... your internet should be up and running by now.  

This has been working for me for about a little over 3 days nonstop and still have my internet connection even after watching several videos on hulu and you tube.  I got the WICD install idea from the following thread and give credit to "walkerk" for leading me to the solution.  I know it's an older post (August 3, 2007), but I gave it a shot anyway on Jaunty Jackalope and it worked. 

[http://ubuntuforums.org/showthread.php?t=479348](http://ubuntuforums.org/showthread.php?t=479348)

also, for more info on WICD... visit...

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Also, please note that I cannot give the exact specifics on what it is that WICD fixed or replaced, it just worked for me.  It became obvious, at least on my machine that there is a serious issue with the standard gnome network manager that automatically installs upon a clean install of Ubuntu.  If you want certain technical data output from some log file on this issue from my machine; reply with some suggestions on how to retrieve and i'll be more than happy to post it for you and hopefully a fix could be found without having to install WiCD.  Also, please note that what worked for me, may not work for you... Just a word of caution to those highly dependent on the Ubuntu side of their PC. :p

---

### Post by greenjumper on 2009-07-04
I was using Wicd before upgrading to Jaunty because I found it much more reliable then. After upgrading to Jaunty I thought that I would give Network Manager another go because a lot of wireless problems were supposed to have been fixed. It seemed to work fine for a week or two, but recently it has been disconnecting every few minutes so I have gone back to Wicd and will see what happens. It doesn't have as nice an interface as Network Manager - but if it works......!

---

### Post by SemenSemenych on 2009-07-04
I have the same problem. Wifi stops transmitting any data, but staying in connect with AP. I looked "iwconfig" and noticed that speed drops from 54M to 5,5M, or 2M and then data stops. 
```
sudo iwconfig wlan0 rate 54M
```
helps for a while, but it all happens again and again. 
I tried different versions of kernels, different versions of wireless card drivers, wicd, network manager. Problem persists. 
I have MSI Wind with RTL8187SE wireless adapter. The only solution that i found, it's a simple script like this:
```
#! /bin/bash
while [ 1 ]; do
   iwconfig wlan0 rate 54M
   sleep 5s
done
```
And start it from root. It seems to me that speed drops and never return to normal automatically. This problem was on old analog modems, when it fallbacks and never fallforward. 
May be someone can suggest any other solution?

---

### Post by kellyhardinguk on 2009-07-04
Been having wifi disconnects along similar lines to posts here on my Aspire One (as posted here: [http://ubuntuforums.org/showthread.php?p=7562556](http://ubuntuforums.org/showthread.php?p=7562556) ).

Will give the Wicd suggestion a try. 

Seems kernel 2.6.31-rc1 from mainline doesn't fix this either, neither did .30 from mainline, <strike>gonna see if .29 from mainline does</strike>, nope doesn't, lose wifi entirely with .29 and .30 kernels, and no change with .31. Can't find a 2.6.28-12 kernel in the repositories either?

Now to try Wicd I think and/or madwifi drivers.

Kelly

---

### Post by bretcolin on 2009-07-04
Linux mint 7 is really good with wifi built in, and its based on jaunty. I know thats wicked lame advice but I'm not an expert in wifi.

---

### Post by kellyhardinguk on 2009-07-04
Downloaded and compiled/installed madwifi-hal-0.10.5.6 and wifi so far seems not to drop out or disconnect, speed is a little slow, but i do tend to get poor signal sometimes when upstairs compared to downstairs (where router is).

So far over 100Mb transfered by SFTP and no stalled connection (with ath5k driver itd get to about 20-35Mb and stall/drop/reconnect/drop).

So, madwifi-hal seems to be fix to this problem perhaps?

Hmm, maybe I spoke to soon... just got Currupted MAC on input :/ but connection didn't drop out, so that might be a router/range issue (nothing in dmesg).

---

### Post by greenjumper on 2009-07-05
I can report that since changing to Wicd my computer has been connected for 20 or so hours without dropping the connection. I may just be imagining it, but the internet seems to be faster as well....
It's definitely a massive improvement over Network Manager

---

### Post by knappers on 2009-07-06
Well I took the plunge Saturday and backed up all my stuff and and reinstalled Jaunty from the magazine cd, had windows on part of the disk and wanted to get rid of it totaly, anyway seeing as i had got my scanner to work and all the other bits that need a little tweek to get going and hopefully solve the disconnecting that started from after the upgrade.
 
It was a damn lot quicker to do than the original upgrade from 8.10 to 9.04 all evening I remember.
 
30 min and i was back in business, apart from the wifi card not doing anything :mad:.
Installed fwcutter created a wifi connection and guess what, it said it was already installed, no driver b43xx.
 
I was about to have a brown stain moment, but a couple of reboots later and it all suddenly appeared, woopee!!
 
And it hasn't dropped the connection yet :p.

---

### Post by knappers on 2009-07-08
It's Wednesday night and still no wifi  drop outs for me and the wife hasn't complained either, so I guess the total reinstall has done it for me.

---

### Post by XYZ1 on 2009-07-13
> **pieguy said:**
> I just put 9.04 on my laptop and it keeps dropping wireless connection.  And it WONT reconnect unless I shutdown and start.  9.04 is not on par or better then previous version.  Regression.

edit: christ, now it wont even connect anymore after shutdown...

I have exactly the same problem with an HP nc6400 and 9.04 64Bit.
I'm not very familiar with Linux and Ubuntu so I can't tell you if another version of Ubuntu is working...

In most cases the disconnect only happens if I try to download something.

---

### Post by glubbdrubb on 2009-07-13
I have been following this thread for a while now waiting for a solution.
My problem was quite similar to the others listed here. I would loose a connection with out any notification (although sometimes it did let me know) and reconnecting could take up to 2 minutes.

I have found a configuration that works for me:

I am using 2.6.28-13 (32 bit)

I installed linux-backports-modules-jaunty

I installed WICD (which replaced Network Manager automatically)

Then I restarted the PC

I have been using this configuration for about 3 days now and I have not had one cut-off since.

Good luck in getting yours to work...

---

### Post by Dragonbite on 2009-07-13
> **glubbdrubb said:**
> I have been following this thread for a while now waiting for a solution.
My problem was quite similar to the others listed here. I would loose a connection with out any notification (although sometimes it did let me know) and reconnecting could take up to 2 minutes.

I have found a configuration that works for me:

I am using 2.6.28-13 (32 bit)

I installed linux-backports-modules-jaunty

I installed WICD (which replaced Network Manager automatically)

Then I restarted the PC

I have been using this configuration for about 3 days now and I have not had one cut-off since.

Good luck in getting yours to work...

Does WICD have any visual difference than Network Manager?  My Jaunty is causing me enough trouble I'm thinking of downgrading to Hardy!

---

### Post by glubbdrubb on 2009-07-13
If what you mean by that is that it looks different, then yes. But it is just as good if not better. Try these changes before you format.

---

### Post by Dragonbite on 2009-07-13
> **glubbdrubb said:**
> If what you mean by that is that it looks different, then yes. But it is just as good if not better. Try these changes before you format.

So far it's working nicely, haven't dropped the connection yet.  It just took a while to connect in the first place, longer than Network Manager usually but this is also the first time connecting so there may have been some factors in that.  Hopefully it'll connect quicker in the future.

Thanks!

---

### Post by Dragonbite on 2009-07-14
Just a quick update. After using WICD for a little while I found that I was able to maintain a stronger connection in parts of the house where normally I would lose signal (even under Hardy, openSUSE, Fedora and everybody else).

Now I can surf the net from bed! woo hoo!

Thanks guys!

---

### Post by glubbdrubb on 2009-07-14
Do you think that this issue could be added to the  ["Known Jaunty Wireless/Ethernet workarounds"]("http://ubuntuforums.org/showthread.php?t=1176117") thread?

---

### Post by bubbhasdance on 2009-07-14
Will someone please explain to me how to do any of this when my wired and wireless connections aren't working? I'm about to downgrade to Hardy, this is so frustrating.

---

### Post by martinbaselier on 2009-07-14
Use a different pc to download the things you need.

---

### Post by bubbhasdance on 2009-07-14
I do not have another pc, and the things I need to do (install from terminal, etc.) I can only do in Ubuntu. But alas, I downgraded to 8.04, and things seem exactly the same. Back to Windows, I suppose.... :( I've done all I can do.

---

### Post by glubbdrubb on 2009-07-15
On  the other PC (which I presume you are posting your replies from) you just need to download the .deb files. If you google the wicd and linux-backports-modules-jaunty .deb files you should beable to install it with out a problem. But if your wired connection is not working then you have problems that this thread won't be able to fix.

---

### Post by Dragonbite on 2009-07-15
> **glubbdrubb said:**
> On  the other PC (which I presume you are posting your replies from) you just need to download the .deb files. If you google the wicd and linux-backports-modules-jaunty .deb files you should beable to install it with out a problem. But if your wired connection is not working then you have problems that this thread won't be able to fix.

I just used synaptic, looked for WIDC and installed. I don't know or think I have linux-backports-modules-jaunty repository set up. Could this be done by default?

---

### Post by glubbdrubb on 2009-07-15
no, you just need to do this

```
sudo apt-get install linux-backports-modules-jaunty
```

and hope your connection lasts so it will download in time.

---

### Post by Dragonbite on 2009-07-15
> **glubbdrubb said:**
> no, you just need to do this

```
sudo apt-get install linux-backports-modules-jaunty
```

and hope your connection lasts so it will download in time.

Last night I was on for a few hours and only had one drop-off when I started, otherwise it's been MUCH better than Network Manager.

---

### Post by glubbdrubb on 2009-07-15
I am glad wicd is working for you.

This may be unrelated, but I have had a few system crashes (requires full restart) since I installed the back ports. It is probably just firefox being buggy though...

---

### Post by bubbhasdance on 2009-07-15
Completely reinstalled 9.04 (downgraded to 8.04 first, nothing worked at all in there), wireless was on and off (better than nothing), so quickly changed to WICD, seems to be working fine now, and a bit faster, maybe? :) thanks guys, you saved me from Windows.

---

### Post by glubbdrubb on 2009-07-16
Ah yes, I do like the smell of Windows dying in the morning...

---

### Post by Mars73 on 2009-07-16
> **glubbdrubb said:**
> Ah yes, I do like the smell of Windows dying in the morning...

:-)
Windows died long ago over here, too bad at my work it's still alive.
Although I use Ubuntu on my work-laptop.

9.04 works wonderful on my laptop (HP 6830s) but not so good on my HP 7600 desktop upstairs, at least the wireless part (belkin USB g).
I've gone back to 8.10 and kernel 2.6.27-11. With any newer kernels it's back to bad connection, loosing connections and low reception/power even if I put the bitrate at 54Mbps. Most notable on my Xbox/XBMC watching movies/avi's, with higher kernels and 9.04 it stutters like hell, with 8.10 and 2.6.27-11 it's smooth.
I've seen so many threads about this, surely someone has the answer. It's not enviromental problems because when I start ubuntu with a lower kernel it plays fine, no router/wifi has been moved. One minute later I restart with a newer kernel, it's bad. Would love to use 9.04 upstairs.
Also are there any security risks with using an older kernel? (I update eveything else except the kernel).

---

### Post by glubbdrubb on 2009-07-16
Have you tried using Wicd with a newer kernel? I wonder if it would be possible to update only part of the kernel or back-date part of it. You would probably have to recompile it yourself.

---

### Post by glubbdrubb on 2009-07-16
OK, now I have a conundrum. I want the functionality of Network-Manager but with the "integrity" of WICD. I want to create a bridge connection but I don't know how with out network-manager.

Help

---

### Post by 3dgimp on 2009-07-22
> **glubbdrubb said:**
> I have been following this thread for a while now waiting for a solution.
My problem was quite similar to the others listed here. I would loose a connection with out any notification (although sometimes it did let me know) and reconnecting could take up to 2 minutes.

I have found a configuration that works for me:

I am using 2.6.28-13 (32 bit)

I installed linux-backports-modules-jaunty

I installed WICD (which replaced Network Manager automatically)

Then I restarted the PC

I have been using this configuration for about 3 days now and I have not had one cut-off since.

Good luck in getting yours to work...

Worked perfectly first time. For anyone with the same issue, just do this:

```
sudo apt-get install linux-backports-modules-jaunty
```
And when that's done:
```
sudo apt-get install wicd
```
And then restart your machine.

Couldn't be simpler.

---

### Post by glubbdrubb on 2009-07-23
Well, I have since removed the linux Juanty back-ports and my wireless behaviour has not changed. Either its actuall install fixed something or it had nothing to do with the solution. Wicd seems to have done the job.

But I am still having majour system stability issues... I am looking forward to the next kernel relese. Anybody know when it is coming out?

---

### Post by Dragonbite on 2009-07-23
I just tried [[COLOR="Blue"]Dream Linux[/COLOR]]("http://www.dreamlinux.com.br/"), which includes Wicd and broadcom drivers and it worked with my wireless on the LiveCD session out of the box!

---

### Post by Hoom@n on 2009-07-24
I have the same problem mentioned in first posts, but not common when I'm (very) near the router.(I don't have such a problem like this in Windows & signal strength is about 35% when I have this problem in Ubuntu)
I'm running 9.04(not updated) & I tested 8.10 live disk and it was same.
This topic was too big to read, please help me to find the solution. (I try to read this topic completely, very soon!)

---

### Post by glubbdrubb on 2009-07-24
Try by simply installing Wicd.

```
sudo apt-get install wicd
```

Restart your PC

If that does not fix it the install the back ports:

```
sudo apt-get install linux-backports-modules-jaunty
```

Restart

That should work now.

---

### Post by Hoom@n on 2009-07-24
> **glubbdrubb said:**
> Try by simply installing Wicd.

```
sudo apt-get install wicd
```

Restart your PC

If that does not fix it the install the back ports:

```
sudo apt-get install linux-backports-modules-jaunty
```

Restart

That should work now.
Thanks a lot!
But, please tell me what is "Wicd" and what is "back ports".

---

### Post by glubbdrubb on 2009-07-24
WICD is the alternative to Network-Manager.

I am not actually sure what the back ports are though... anybody else know?

But did the modifications work?

---

### Post by Hoom@n on 2009-07-24
> **glubbdrubb said:**
> WICD is the alternative to Network-Manager.

I am not actually sure what the back ports are though... anybody else know?

But did the modifications work?
Thanks for your help.
I prefer to update my Ubuntu, see what happens to [this]("http://ubuntuforums.org/showthread.php?p=7671988#post7671988"), read this all pages of this topic and then decide what to do. But as it may take time a lot, I may do what you told in middle of doing those things!
Again, thank you for your help.

---

### Post by glubbdrubb on 2009-07-29
OK, I updated to the latest kernel today and now the wireless won't connect at all. I tried older kernels and they don't work either. I tried different combinations of kernels and wicd/network-manager and they have not worked either.

Please help someone

EDIT:
Ok, after fidling around and making my wifi unprotected it worked.
I also realised it was  a lot more reliable when I improved my signal reception.

---

### Post by geogur on 2009-08-19
i can`t get my wifi to connect at all , can someone fix ubuntu so this will go away ?

---

### Post by chenxiaolong on 2009-08-19
Can somebody help me? I have a Broadcom BCM4312 Revision 1 wireless card using the wl driver (because the b43 driver doesn't support this card). It disconnects all the time, whether I use WPA, WPA2, or WPA and WPA2 together. It connects fine on WEP and insecure networks. I'm sure it's not the router's problem because it connects fine on another laptop using a BCM4307 (also using wl). The card connects fine in Debian and Sidux. I hope this problem gets worked out soon.

EDIT: The wireless connects fine after entering the network password 11 times (really ridiculous).

---

### Post by glubbdrubb on 2009-08-20
It seems Network-Manager has been having issues with the later kernals when it comes to protected networks. Try wicd like suggested before.

So try:

```
sudo apt-get install wicd
```

It will uninstall network-manager and install wicd. Hopefully that will work. 

If this problem only started when you upgraded to the latest kernal then downgrade to the previos kernal that worked.

You can edit which kernals you use by using the Start-up Manager under the System Menu.

---

### Post by Dragonbite on 2009-08-20
Is this going to be fixed with Karmic?

---

### Post by chenxiaolong on 2009-08-20
I've tried Wicd before. I tried the version in the Ubuntu repository and the Wicd repository and they both don't work. It gets stuck at "Validating Authentication" and it never connects. I tried compiling wl.ko from source and it still doesn't work. If I can't get it to work, I'll install Ubuntu 9.10.

---

### Post by glubbdrubb on 2009-08-20
THe problem is that it only affects a small proportion of users and it is probably a slightly different problem for each of us.

What we need is a simple way to diagnose the problem, with clear "markers" to identify exact cause of the problem.

That way finding a solution would very easy and fixing the bugs even easier.

---

### Post by chenxiaolong on 2009-08-20
I tried installing the latest kernel in Ubuntu Jaunty from the Ubuntu Kernel PPA, but wl wouldn't compile. So I installed Ubuntu 9.10 Karmic and it worked flawlessly after enabling the STA driver in the Hardware Drivers dialog. I don't know why it wouldn't work in Jaunty. I'm going to use Fedora 11 until Ubuntu 9.10 is released.

---

### Post by glubbdrubb on 2009-08-21
I have been thinking about moving to Fedora until Karmic is ready. I have been having majour stability issues of late with kernal panics and system freezes which require hard restarts. I don't really know how to debug or trace the problem. Do you know which thread I should ask about this?

---

### Post by geogur on 2009-08-21
don`t do wicd i did and lost my lan line , it dose not work!

---

### Post by geogur on 2009-08-21
> **Dragonbite said:**
> Is this going to be fixed with Karmic?

nice :guitar:Zandros has a awsome wifi we need some of that here .

---

### Post by glubbdrubb on 2009-08-21
If wicd broke something then simply Re-install network-manager, and that will uninstall wicd.

---

### Post by Dragonbite on 2009-08-21
> **geogur said:**
> don`t do wicd i did and lost my lan line , it dose not work!

You didn't happen to be running Kubuntu, are you?

I know somebody who did that with Kubuntu and it removed network manager and then couldn't connect to the internet to get wicd.

I'm thinking of trying Karmic and see if the issue is still there (as well as the Intel issue and the annoying beeps when shutting down).

---

### Post by chenxiaolong on 2009-08-21
I suggest you don't install Fedora, especially if you have a Broadcom card. The new kernel in the repo-2.6.29.6-217.2.8.fc11.x86_64-gets a lot of kernel panics and the broadcom-wl driver in the RPMRusion repo isn't compiled for this kernel yet. Also, if you use VMware, you will need a patch to install it on this kernel. Very aggravating.

---

### Post by chenxiaolong on 2009-08-21
Shoot. I replied to the wrong thread. Sorry.

---

### Post by glubbdrubb on 2009-08-22
Next time, chenxiaolong, you can just edit your post - so you don't have to post another one.

I think I may just take a look at Karmic myself. I will have to see how much data I have left on my adsl....

---

### Post by Dragonbite on 2009-08-22
> **glubbdrubb said:**
> Next time, chenxiaolong, you can just edit your post - so you don't have to post another one.

I think I may just take a look at Karmic myself. I will have to see how much data I have left on my adsl....

I think you get Karmic from 9.04 and type ```
update-manager -d
``` and you'll see > New Distribution release '9.10' is available.

---

### Post by w_1_n_d on 2009-08-22
man atleast you guys get a connection. My wireless card can't even connect to a secure wireless connection, even after i input the security code. Sooooooooo annoying i use a atheros 5006ex card. :O:O:guitar:

---

### Post by glubbdrubb on 2009-08-24
Did you try the suggestions mentioned previously?

---

### Post by w_1_n_d on 2009-08-24
i tried them all. :(

---

### Post by John RG on 2009-09-02
I have an old IBM T43 laptop. Had no problems with Ubuntu 8.04, upgraded via 8.10 (didn't stay long, only a few hours to download next upgrade) to 9.04. Almost immediately had dropout problems and came here.

Installed WICD using package manager which asked me to uninstall Network Manager. Didn't do anything else mentioned in this thread. So far (touch wood, hold lucky rabbit foot etc) I've had no more problems.

Cheers,

John

---

### Post by glubbdrubb on 2009-09-02
Just a word of caution. "Upgrading" may not always be the beast idea. A fresh install may help you avoid a lot of issues.

---

### Post by Joshag on 2009-09-04
Broadcom 4813
Having started at page 1 and read all the way to the end I realized I should have cheated and gone right to the "Scooby Doo" ending. 

Tried backports, different kernels, and about every trick in this thread. 

Result: Got lucky for about 2 days after applying backports then the connection drops started again. Even during the days with steady connections browsing was slooooow.
It was only after I switched to WICD did I finally get both steady connections and speed.

Good luck to all...........

---

### Post by chenxiaolong on 2009-09-04
Wicd doesn't show any wireless networks for me. I'm using openSUSE 11.1 in the meantime until Ubuntu 9.04 is released.

EDIT: Sorry. Typo. Meant 9.10

---

### Post by glubbdrubb on 2009-09-05
> **chenxiaolong said:**
> Wicd doesn't show any wireless networks for me. I'm using openSUSE 11.1 in the meantime until Ubuntu 9.04 is released.

I think you mean untill 9.10 is released.

---

### Post by psychlic on 2009-09-05
Hi glubbdrubb / all

I've been following this thread with interest as I have the same problem.  I used WICD on Intrepid and it solved the wireless connectivity problems I had then.  I don't want to install it now though, because it doesn't support my Huawei 3G USB dongle.  It's pretty frustrating :(

All the best


psychlic

---

### Post by glubbdrubb on 2009-09-05
Alas, the immaturity of WICD shows through.

I have found though that I can connect with out any problems with the latest kernel 2.6.28-15. I have moved back to network-manager because WICD was bugging out.

I have read that are some really good improvements in the 2.6.31 release, which I am looking forward to.

---

### Post by Dalle85 on 2009-09-15
Hey there...

I've been through most of this thread as I've been experiencing a similar issue with my wireless after upgrading to Jaunty (not sure if it was the upgrade itself or a later update). I have an Intel 4965AGN wireless adapter and have had regular connection "dropouts" for the last few months! It doesn't really disconnect from the network as much as just stops! The signal strength is still strong but there is no connection. I can't reliably replicate the bug, it just happens at random intervals.

I've tried just about any solution suggested on every thread out there; 

- installed "backport" which caused disconnection within a few minutes after boot which could only be resolved by restarting

- disabled ipv6 which made the browsing a bit faster (surprise) but didn't do anything to my disconnections 

- installed WICD and got fed up with that interface (nm is just better IMHO)

- messed around with all the different settings in iwconfig and just messed up my connection even more

- tried ndiswrapper which wouldn't even claim the adapter

- messed around with my router despite every other component (5 different components, two of which running Ubuntu 8.04) working perfectly and got blacklisted for 30 minutes by my ISP (apparantly, they don't like changing MAC-addresses)

Anyway, after much trial and error I found out that the solution to my specific problem was to change the security setting on my router from WPA/WPA2 PSK mixed mode to WPA2 PSK mode only. This somehow, magically remedied all my problems... So as others have described (here and elsewhere) the problem seems to lie somewhere within the WPA-authentication process!

Anyway - hopefully, this can be of some help to other users with similar issues as this is an incredibly irritating bug!

*** Update 1 ***: Started loosing my connection again after about a day, so seems like changing to WPA2-only DIDN'T work

*** Update 2 ***: Solved it, but the solution isn't exactly elegant - Upgraded to Karmic Alpha 6... That fixed the issue

---

### Post by glubbdrubb on 2009-09-24
I have found that improving my signal streangth has made a big difference to the reliabilty of the connection. From  40 - 60% to 70 - 80% was all that I needed to improve my connection.

---

### Post by chenxiaolong on 2009-09-24
What do you mean by changing the signal strength? The signal strength is determined by how close you are to the router, so how would you change it.

---

### Post by glubbdrubb on 2009-09-24
I am using a USB wifi card, so I got an extention cord which improved the signal streangth.

---

### Post by chenxiaolong on 2009-09-24
Ohhhhhh. I wish internal cards had an invisible one of those. :)

---

### Post by yknivag on 2009-09-24
I get this too, have ever since I upgraded.

The following appears every two minutes in my debug log:

```

gavin@elbow:/var/log$ tail -f debug
Sep 24 22:17:49 elbow NetworkManager: <debug> [1253827069.002287] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 22:17:55 elbow NetworkManager: <debug> [1253827075.001391] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 
Sep 24 22:19:49 elbow NetworkManager: <debug> [1253827189.004298] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 22:19:54 elbow NetworkManager: <debug> [1253827195.000698] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 
Sep 24 22:21:49 elbow NetworkManager: <debug> [1253827309.002605] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 22:21:55 elbow NetworkManager: <debug> [1253827315.001318] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 
Sep 24 22:23:49 elbow NetworkManager: <debug> [1253827429.004948] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 22:23:55 elbow NetworkManager: <debug> [1253827435.008025] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 
Sep 24 22:25:49 elbow NetworkManager: <debug> [1253827549.004167] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 22:25:55 elbow NetworkManager: <debug> [1253827555.001256] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 

```

and this every 15 minutes in daemon.log

```

Sep 24 22:19:09 elbow NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Sep 24 22:19:09 elbow NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 

```

when it fails it does this:

```

Sep 24 21:47:18 elbow NetworkManager: <debug> [1253825239.000231] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:EC:45:88 (pelvis) 
Sep 24 21:49:07 elbow NetworkManager: <debug> [1253825347.001502] periodic_update(): Roamed from BSSID 00:0F:66:EC:45:88 (pelvis) to (none) ((none)) 
Sep 24 21:49:14 elbow kernel: [13253.464731] wlan0: deauthenticated
Sep 24 21:49:15 elbow kernel: [13254.464067] wlan0: direct probe to AP 00:0f:66:ec:45:88 try 1
Sep 24 21:49:15 elbow kernel: [13254.465997] wlan0 direct probe responded
Sep 24 21:49:15 elbow kernel: [13254.466008] wlan0: authenticate with AP 00:0f:66:ec:45:88
Sep 24 21:49:15 elbow kernel: [13254.469145] wlan0: authenticated
Sep 24 21:49:15 elbow kernel: [13254.469156] wlan0: associate with AP 00:0f:66:ec:45:88
Sep 24 21:49:15 elbow kernel: [13254.473536] wlan0: RX ReassocResp from 00:0f:66:ec:45:88 (capab=0x431 status=0 aid=1)
Sep 24 21:49:15 elbow kernel: [13254.473545] wlan0: associated
Sep 24 21:49:25 elbow kernel: [13264.205360] wlan0: deauthenticated
Sep 24 21:49:26 elbow kernel: [13265.204073] wlan0: direct probe to AP 00:0f:66:ec:45:88 try 1
Sep 24 21:49:26 elbow kernel: [13265.205994] wlan0 direct probe responded
Sep 24 21:49:26 elbow kernel: [13265.206005] wlan0: authenticate with AP 00:0f:66:ec:45:88
Sep 24 21:49:26 elbow kernel: [13265.209086] wlan0: authenticated
Sep 24 21:49:26 elbow kernel: [13265.209097] wlan0: associate with AP 00:0f:66:ec:45:88
Sep 24 21:49:26 elbow kernel: [13265.213567] wlan0: RX ReassocResp from 00:0f:66:ec:45:88 (capab=0x431 status=0 aid=1)
Sep 24 21:49:26 elbow kernel: [13265.213577] wlan0: associated
Sep 24 21:49:30 elbow kernel: [13269.065892] wlan0: disassociating by local choice (reason=3)

```

Manually reconnecting almost always works, but it really shouldn't do it. Should it really be roaming in and out every two minutes?  And what causes it to disconnect?  It worked perfectly on Hardy, not at all on Intrepid and now so-so on Jaunty.

---

### Post by glubbdrubb on 2009-09-25
As we have suggested, try WICD.

Also, try increasing the Group Key Renewal time in the WPA settings in the wireless router.

---

### Post by yknivag on 2009-09-25
> **glubbdrubb said:**
> As we have suggested, try WICD.

I've tried WICD in the past.  To be honest I'd rather eat my eyeballs than use it again. IMHO, the inconvenience of having to reconnect the wireless every now and again is not worth the hassle.

> **glubbdrubb said:**
> Also, try increasing the Group Key Renewal time in the WPA settings in the wireless router.

The Key Renewal Time is set to 900 seconds (15 minutes) which explains why it goes through the re-auth every 15 minutes.  It doesn't explain the "roam off"/"roam on" behaviour every 120 seconds.

---

### Post by glubbdrubb on 2009-09-26
When was the last time you used WICD? It is pretty good now.

As long as you don't need certain functionality (such as creating a PPPoE connection on your PC) It works quite well.

---

### Post by windom on 2009-09-26
I had terrible problems trying to connect to WPA APs. It seems most any setup (in my case) could connect to WEP but it's not is very good secutity scheme. I spent *many* hours working with my laptop and finally got it working. The following points are more conceptual than specific so may help only the more experienced but out-of-the-box wireless support is embarrassingly poor. Please note before flaming me that this is meant as an observation and not a value judgement. I work untold hours on this because I wanted to use Ubuntu rather than another OS.

1) make sure your AP is set up correctly. We have to be thorough

2) make sure all references to your wireless nickname in the /etc directory tree is consistent. Use something like 'grep -r wlan *' to find them

3) I use wicd for a net manager. It's seems to mesh with wpa_supplicant better than Networkmanager (strictly my own opinion)

4) Use the best driver. This may mean a lot of experimenting. I have a BCM4311. I used ndiswrapper (with several different windows driver versions), wl, and b43. b43 clearly out performed the others

5) Undoing changes that were made using failed schemes is as important as making the correct changes. If you are not very experienced administrating linux, it may mean fresh installs or even undoing fresh installs in some portion to implement what you want

6) Use wicd and make sure /etc/network/interfaces makes reference only to the loopback interface. Some people add lines to this files and get a working interface but they are probably not using wicd

This list may not mean much to the newbie but it should help the more experienced.

windom

---

### Post by glubbdrubb on 2009-09-27
Thanks wisdom.

I think we need to make something that will be a little easier for new readers of this thread. Something concise and reletively simple should be served up.

We should not make them read through this whole discussion.

---

### Post by tjwilli on 2009-10-11
> **glubbdrubb said:**
> I have been following this thread for a while now waiting for a solution.
My problem was quite similar to the others listed here. I would loose a connection with out any notification (although sometimes it did let me know) and reconnecting could take up to 2 minutes.

I have found a configuration that works for me:

I am using 2.6.28-13 (32 bit)

I installed linux-backports-modules-jaunty

I installed WICD (which replaced Network Manager automatically)

Then I restarted the PC

I have been using this configuration for about 3 days now and I have not had one cut-off since.

Good luck in getting yours to work...
I installed linux-backports-jaunty (I already had wicd installed) and so far, so good! It seems as though I can connect more easily, and although I haven't be on that long yet, I seem to be getting much better throughput even when the signal is fairly low.

I'm on an Acer Aspire 4530, Ubuntu 9.04, kernel 2.6.28-15 (generic)

Thanks so much!

---

### Post by glubbdrubb on 2009-10-12
Hey, that's what we are here for!

I have since upgraded to the Karmic beta and I now seem to be having a bit of a repeat performance. My connection is now really slow.

I will start a similar thread when Karmic is released officially.

Let the process start again.

---

### Post by mclavey on 2009-10-12
I have had a similar porblem for the last month or so...interment wireless.
I have a HP dv7 which is 64 bit ...but I am using 32 bit Ubuntu 9.04, kernel 2.6.28-15 (generic)

I also did the backport which helped some ... then wicd which made it work very well.

---

### Post by thesubydude on 2009-10-15
awesome thread.

i installed wicd. haven't had any issues since (Xfingers)

was able to work through the night last night w/out a drop.

great rest of the week to you all.

-sd

---

### Post by glubbdrubb on 2009-10-20
Something needs to be done about Network Manager.
I am do not know if similar problems occure in other distro's, so perhaps this is just an Ubuntu issue.

I do not know where a bug should be filed, or if this even counts as a bug, but when replacing Network Manager with an alternative network applet(I don't know if this is the terminoly) fixes a problem, then it would seem that network manager is lacking in some way.

What should we do?

---

### Post by Dragonbite on 2009-10-20
> **glubbdrubb said:**
> Something needs to be done about Network Manager.
I am do not know if similar problems occure in other distro's, so perhaps this is just an Ubuntu issue.

I do not know where a bug should be filed, or if this even counts as a bug, but when replacing Network Manager with an alternative network applet(I don't know if this is the terminoly) fixes a problem, then it would seem that network manager is lacking in some way.

What should we do?

I seem to remember something showing up in the Fedora forum like this.  I don't remember the details, I just remember thinking this isn't an Ubuntu-only issue.

---

### Post by glubbdrubb on 2009-10-20
Thanks, I will take a look...

---

### Post by Rofko on 2009-10-20
Wow, I can't believe it - I was on this thread back when it was fresh from the womb, as it were... I see it is now reaching full maturity and the problem still hasn't been fixed! Eventually I bought a USB wifi card and that fixed the issue for me, but for one reason or another, which may or may not be that I have broken this usb card, I am back to using my internal intel wifi... or I would be if it didn't cause the connection to drop every few minutes and then refuse to reconnect. I would prefer not to have to remove and replace network manager, for some reasons that people have mentioned above in passing. I will try the backports, which I remember briefly alleviated to problem last time (fresh install since then), but I really hope that a permanent fix is on the way very soon for this - this actually almost forced me to abandon ubuntu at one point, and I bet lots of floating voters have been lost over this, as it is a VERY common wifi card.
Good luck everyone

EDIT: BACKPORTS DID NOT WORK! :'(

---

### Post by glubbdrubb on 2009-10-21
Try Karmic. It comes out in a few days.

---

### Post by houstonbofh on 2009-10-21
> **glubbdrubb said:**
> Try Karmic. It comes out in a few days.
Bad news...

[http://ubuntuforums.org/showthread.php?t=1295243](http://ubuntuforums.org/showthread.php?t=1295243)

---

### Post by glubbdrubb on 2009-10-21
The trick to fixing these wireless faults seems to be being able to distinguish between driver/module/kernel issues and network manager bugs.

---

### Post by glubbdrubb on 2009-10-21
> **houstonbofh said:**
> Bad news...

[http://ubuntuforums.org/showthread.php?t=1295243](http://ubuntuforums.org/showthread.php?t=1295243)

Well, lets not judge it yet. That is only one thread (so far) and it is still in beta.

---

### Post by CheshireMac on 2009-11-08
I'm having the same issue, on three different platforms (Ubuntu, Windows, and OS X). It always drops at the same time, it seems to happen when someone tries to download something or just over time.  I tried Wicd but it does the same thing. I thought maybe it was my computer causing the others to crash, and maybe it is, but I can't figure it out.

---

### Post by chenxiaolong on 2009-11-08
Well if it doesn't work on all three platforms, then you should contact the manufacturer or get a new card.

---

### Post by Dragonbite on 2009-11-23
My system runs a Broadcom wireless and I was flabergasted that when I tried Feodra 12 LiveCd, it automatically detected my wireless card and after putting in the key I was on the internet.

Since then I have installed Fedora 12 and the Broadcom has been working like a charm.  I have not had a single drop yet.

The key, from what I've heard, is the [[COLOR="Blue"]OpenFWWF[/COLOR]]("http://www.ing.unibs.it/openfwwf/") driver that Fedora includes. It is open source and I really hope Ubuntu starts including it in their releases.

I've heard it doesn't work for everybody, but this is an older system and I am practically giddy that it works.

---

### Post by lampak on 2010-01-16
For me it's got even worse since now it usually hangs up. Completely, so I can't even move the cursor. It seems related to the disconnection problem - on the still screen on the bar there's usually the icon which appears when ubuntu tries to connect to the network. I'd blame linux wifi drivers. 

I've just tried lucid alpha 2 live cd - crashed after 10 minutes :(

---

### Post by I am Matt Jones on 2010-01-18
I was having disconnects at first, now my iwl3945 refuses to connect 75% of the time, when it does connect it refuses to obtain an IP address. I found a work around on my system. 

First I logged onto the system as Root to test the wireless and it works properly. I thought it might be a permission problem on one of the network config files so I created a new profile on my system and the wireless works perfectly and flawlessly, even coming out of hibernation and standby. The problem is specific to to my profile. My system always seems to try to obtain the same address 192.168.1.2 on my profile, on the new profile it is receiving a new ip 192.168.1.8
The following code is ran from the new profile, with working wifi. This might give some of you an idea to try, it might give some of you gurus an idea to suggest to the rest of us to pin down the problem or fix it.

```
 &#65279;&#65279;Dell Lattitude D820
Ubuntu 9.10
2.6.31-16-generic i686

Intel Corporation PRO/Wireless 3945ABG [Golan]
=========================================================================
wlan0     Link encap:Ethernet  HWaddr 00:18:de:83:03:3a  

          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::218:deff:fe83:33a/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:108531 errors:0 dropped:0 overruns:0 frame:0

          TX packets:65206 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:147806157 (147.8 MB)  TX bytes:7578410 (7.5 MB)

=========================================================================

lo        no wireless extensions.



eth2      no wireless extensions.



vboxnet0  no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11abg  ESSID:"NETGEAR"  

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:21:D7:6A   

          Bit Rate=54 Mb/s   Tx-Power=15 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=67/70  Signal level=-43 dBm  Noise level=-127 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.




mother@lapbook:~$ lsmod

Module                  Size  Used by

nls_utf8                1568  0 

isofs                  31620  0 

nls_iso8859_1           3740  0 

nls_cp437               5372  0 

vfat                   10716  0 

fat                    51452  1 vfat

usb_storage            52576  0 

binfmt_misc             8356  1 

joydev                 10272  0 

psmouse                56500  0 

serio_raw               5280  0 

bridge                 47952  0 

stp                     2272  1 bridge

bnep                   12060  2 

ppdev                   6688  0 

lp                      8964  0 

arc4                    1660  2 

pcmcia                 36808  0 

ecb                     2524  2 

iwl3945                77212  0 

iwlcore               112540  1 iwl3945

yenta_socket           24200  1 

rsrc_nonstatic         11644  1 yenta_socket

dell_wmi                2564  0 

nvidia               9586440  44 

parport                35340  2 ppdev,lp

mac80211              181076  2 iwl3945,iwlcore

dell_laptop             8128  0 

pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic

irda                  189564  0 

led_class               4096  2 iwl3945,iwlcore

dcdbas                  7292  1 dell_laptop

btusb                  11856  2 

crc_ccitt               1852  1 irda

snd_hda_codec_idt      59844  1 

snd_hda_intel          26920  2 

snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel

snd_hwdep               7200  1 snd_hda_codec

snd_pcm_oss            37920  0 

snd_mixer_oss          16028  1 snd_pcm_oss

snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

snd_seq_dummy           2656  0 

snd_seq_oss            28576  0 

snd_seq_midi            6432  0 

snd_rawmidi            22208  1 snd_seq_midi

snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi

snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

iptable_filter          3100  0 

snd_timer              22276  2 snd_pcm,snd_seq

ip_tables              11692  1 iptable_filter

snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

cfg80211               93052  3 iwl3945,iwlcore,mac80211

x_tables               16544  1 ip_tables

snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               7264  1 snd

snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

vboxnetadp             78536  0 

vboxnetflt             85032  0 

vboxdrv               121352  1 vboxnetflt

dm_raid45              84228  0 

xor                    15620  1 dm_raid45

ohci1394               29900  0 

ieee1394               86596  1 ohci1394

video                  19380  0 

output                  2780  1 video

tg3                   109600  0 

intel_agp              27484  0 

agpgart                34988  2 nvidia,intel_agp


dmesg | grep 'wlan0'

[   29.577071] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   39.776808] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   40.049900] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[   40.051757] wlan0: authenticated

[   40.051761] wlan0: associate with AP 00:1f:33:21:d7:6a

[   40.054403] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=5)

[   40.054408] wlan0: associated

[   40.055991] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[   40.056926] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[   40.058735] wlan0: authenticated

[   40.058739] wlan0: associate with AP 00:1f:33:21:d7:6a

[   40.061327] wlan0: RX ReassocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=5)

[   40.061332] wlan0: associated

[   51.656031] wlan0: no IPv6 routers present

[ 6613.149232] wlan0: no probe response from AP 00:1f:33:21:d7:6a - disassociating

[ 6843.101055] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[ 6844.849805] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[ 6844.851643] wlan0: authenticated

[ 6844.851649] wlan0: associate with AP 00:1f:33:21:d7:6a

[ 6844.854258] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=3)

[ 6844.854265] wlan0: associated

[ 6844.855962] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[ 6855.008057] wlan0: no IPv6 routers present

[15127.944060] wlan0: no probe response from AP 00:1f:33:21:d7:6a - disassociating

[16166.214465] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[16167.995444] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[16167.997278] wlan0: authenticated

[16167.997284] wlan0: associate with AP 00:1f:33:21:d7:6a

[16167.999739] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=3)

[16167.999747] wlan0: associated

[16168.003297] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[16178.328033] wlan0: no IPv6 routers present

[16612.460041] wlan0: no probe response from AP 00:1f:33:21:d7:6a - disassociating

[16844.097808] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[16845.867120] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[16845.868997] wlan0: authenticated

[16845.869001] wlan0: associate with AP 00:1f:33:21:d7:6a

[16845.871421] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=6)

[16845.871425] wlan0: associated

[16845.873784] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[16855.968032] wlan0: no IPv6 routers present

[17306.992033] wlan0: no probe response from AP 00:1f:33:21:d7:6a - disassociating

[17537.180850] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[17538.996739] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[17538.998585] wlan0: authenticated

[17538.998588] wlan0: associate with AP 00:1f:33:21:d7:6a

[17539.001108] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=6)

[17539.001113] wlan0: associated

[17539.002681] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[17549.548030] wlan0: no IPv6 routers present

[17889.252125] wlan0: deauthenticating by local choice (reason=3)

[17889.402077] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[17889.876840] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[17905.066801] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[17906.834256] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[17906.836387] wlan0: authenticated

[17906.836392] wlan0: associate with AP 00:1f:33:21:d7:6a

[17906.838857] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=6)

[17906.838864] wlan0: associated

[17906.841434] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[17917.648071] wlan0: no IPv6 routers present

[19874.552071] wlan0: no probe response from AP 00:1f:33:21:d7:6a - disassociating

[20101.368845] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[20103.116530] wlan0: authenticate with AP 00:1f:33:21:d7:6a

[20103.118361] wlan0: authenticated

[20103.118364] wlan0: associate with AP 00:1f:33:21:d7:6a

[20103.120899] wlan0: RX AssocResp from 00:1f:33:21:d7:6a (capab=0x1 status=0 aid=7)

[20103.120903] wlan0: associated

[20103.122587] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[20113.812032] wlan0: no IPv6 routers present



lshw -C network

[sudo] password for matuoh: 

  *-network               

       description: Wireless interface

       product: PRO/Wireless 3945ABG [Golan] Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:0c:00.0

       logical name: wmaster0

       version: 02

       serial: 00:18:de:83:03:3a

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.8 latency=0 multicast=yes wireless=IEEE 802.11abg

       resources: irq:29 memory:dcfff000-dcffffff

  *-network

       description: Ethernet interface

       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:09:00.0

       logical name: eth2

       version: 02

       serial: 00:15:c5:c0:4e:e9

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair

       resources: irq:30 memory:dcef0000-dcefffff

  *-network DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: vboxnet0

       serial: 0a:00:27:00:00:00

       capabilities: ethernet physical

       configuration: broadcast=yes multicast=yes



wlan0     Scan completed :

          Cell 01 - Address: 00:1F:33:21:D7:6A

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=68/70  Signal level=-42 dBm  

                    Encryption key:off

                    ESSID:"NETGEAR"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=000000002eb8f183

                    Extra: Last beacon: 563308ms ago

                    IE: Unknown: 00074E455447454152

                    IE: Unknown: 010882848B962430486C

                    IE: Unknown: 030101

                    IE: Unknown: 2A0107

                    IE: Unknown: 2F0107

                    IE: Unknown: 32040C121860

                    IE: Unknown: DD090010180205F0000000

                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




```

```
I will edit the post with code from profile with non working wifi in a few minutes.
```

---

### Post by y2kprawn on 2011-01-15
> **ubuser_7 said:**
> Yea, I tried a few of them, but I havent disable my ipv6 yet. Another thing I noted is that its difficult to reproduce this bug. Like I am running fine for a day now, with very similar situations. 

however as t0mppa mentioned, no pointing ranting here. we should provide as much info/help we can in the bug reports.
I have Just set up a desktop with an internal wireless card and an external usb wireless, and now my Acer Aspire 1810 TZ laptop, all configs have the same issue. This thread started  May 2nd, 2009 , wow. And this is me changing from Windows 7. I used 8.04 as well and had hell with Wireless. Can anyone let me know if they have come across something that definitely works ?

Pleeeease :) ?

---

### Post by lampak on 2011-01-16
One of the ubuntu upgrades since then solved the problem for me. And since the thread died out I thought for others as well. 

But it seems it didn't :(

---

### Post by bayvista on 2011-01-31
As I have this problem on Lucid (10.04), how did you create a new profile? I'll try this.

---

### Post by DarkTide on 2011-03-25
I wanna take back what I said earlier about it not being a problem for  me anymore. Although my wireless may disconnect a little less it is  still too often. 

One thing I did realize from other posts is that IPV6 is built into the  kernel and that makes it harder to disable or at least changes the  method you need to use. 

Even if you think you disabled IPV6 it may still be enabled even if the post says for Jaunty.

If you think you have IPV6 disabled you may not so to find out type this in terminal.

---

### Post by DarkTide on 2011-04-05
Well I took the plunge Saturday and backed up all my stuff and and  reinstalled Jaunty from the magazine cd, had windows on part of the disk  and wanted to get rid of it totaly, anyway seeing as i had got my  scanner to work and all the other bits that need a little tweek to get  going and hopefully solve the disconnecting that started from after the  upgrade.

---

