---
title: "Upgrade 10.04-&gt;10.10 Big disappointment !"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Spetsnaz84 on 2010-12-05
Hi all,

I had been using Ubuntu 10.04 LTS on my HP Mini 110 and I was really happy about it: everything was working well and life was good.

Then I decided (stupid me) to upgrade to the newest version of Ubuntu.

I must say the results are disappointing: 
- My wireless was initially very slow (using the STA driver). I then switched to the b43 driver but it seems unstable (losing association with my access point). FYI I have the 4312 chip.
- My bluetooth has worked but for some reason now it does not work anymore. Sometimes Ubuntu even says I have no bluetooth support ! 
- Even stranger: in my taskbar the bluetooth icon is grey (as if it is disabled), but when i click on it I can only 'disable' it, implying it is enabled (the list of my known bluetooth devices is empty though). When I click on this disable button.... my wireless will disassociate !! Really, I am telling the truth !
When I re-enable bluetooth... my wireless comes up again ! I see some USB (bluetooth on usb?) error traces.

Anyway, I had become very positive about Ubuntu and I feel really stupid to have 'upgraded'.. I hope you guys can help me with this.

Thank you very much.

---

### Post by northd_tech on 2010-12-05
Do you still have your LiveCD for Ubuntu 10.04 LTS?  You might also consider installing Ubuntu Ultimate Edition 2.7 which is based on Ubuntu 10.04.1 LTS (and what I'm currently using on this and about 3 other laptops, after the updates were recently discontinued for Ubuntu 9.04 recently).  I disliked both Ubuntu 9.10 and 10.10 and stuck with 9.04 as long as I reasonably could, but I've been burned by the "newest, best-est thing" many times before.

[http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/](http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/)

You can check out UE2.7 with the LiveDVD before installing.

I've been able to successfully re-install "backwards upgrades" over an existing** ext4** Linux install partition and not lose very much (if any) of the original Linux stuff (even the desktop background stayed the same).  The installer deleted the conflicting packages when/if they were found, but unfortunately I didn't write down the exact steps when I did this (about 3 or more times on my nephew's laptop trying to get his 64-bit wireless working with various 64- and 32-bit versions of Linux).

As I recall, after running "Install" from the LiveCD/DVD just like normal, I clicked** manual partitioning** for Gparted, and chose NOT TO FORMAT (UNCHECKED box) the **ext4** Linux partition.  This threw 2-3 warnings as I recall, and then partway through the Hard Disk "partitioning" it asked if I wanted to "import" any user accounts after a message about uninstalling certain Linux packages.   I just clicked my old username on the **ext4** Linux partition, and everything-ish was still there after a restart with my "new" or "new old" Linux OS.

I would be sure to use the FEBE plugin to backup my Firefox settings first, and I would burn all my email stuff from Thunderbird to CD/DVD first.  It would also be a lot safer tranfser/copy all crucial data and programs to an external hard disk or DVD first if you don't have tape backup or something like that.

Edit:  I'm running a Broadcom 4321AG wireless with the proprietary "STA" driver, and I think it only took me 2 restarts and a few minor tweaks to get wireless [mostly] "out of the box" with Ultimate Edition 2.7 64-bit.  I would bet that 32-bit would just work fine from my experience with my nephew's laptop running Ubuntu.  If you have a reliable cabled ethernet connection, I'd consider giving a re-install a try.

Have you searched here for a HOWTO on how to re-install Ubuntu over an existing Linux install?   I would think there should be something (but unfortunatley, I didn't write down the steps that I followed a while back).

---

### Post by Spetsnaz84 on 2010-12-05
Hi,

Some important extra information:
I have just switched the wireless driver from bt43 to STA and now I don't have this weird bluetooth <-> wireless issue.
I guess I will stick to sta for now but I have found it to be much slower than the bt43.

---

### Post by northd_tech on 2010-12-05
I'm not seeing the slow STA driver problem with my Broadcom 4321AG/4328, but I disabled IPv6 long ago and maybe 1-2 other minor "adjustments" last year when I was seeing slower connections.  Mine just tested at nearly 19.35 Mbps download and 0.81 Mbps upload to both Los Angeles and Dallas, TX using a wireless router/cable modem at this testing page here:

[http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/)

You might want to watch the thread below- there is a new Broadcom 4313 module "work in progress," but I couldn't get it to build for me earlier tonight due to an error (I was going to test the module with my 4321AG wireless for the forum member Axx83).  It doesn't mention your 4312 or my 4321AG specifically though on that thread.

[http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)

eta:  I have since upgraded to Lucid Lynx 10.04.1 LTS, so I may no longer have IPv6 disabled and might be running the "default" settings for a Broadcom 4328, rev 03 (according to lspci).

---

### Post by Spetsnaz84 on 2010-12-05
I will keep an eye on it but it does not seem useful to me.
So far I have to choose between
STA: unacceptable slow, high latency, packet loss even but does not interfere with bluetooth

OR

b43: fast but unstable and prevents bluetooth from working.
FYI: I read some read errors regarding to bluetooth in dmesg


[   26.325104] usb 5-2: new full speed USB device using uhci_hcd and address 6
[   26.449097] usb 5-2: device descriptor read/64, error -71
[   26.677107] usb 5-2: device descriptor read/64, error -71
[   26.893103] usb 5-2: new full speed USB device using uhci_hcd and address 7
[   27.017126] usb 5-2: device descriptor read/64, error -71
[   27.244166] usb 5-2: device descriptor read/64, error -71
[   27.460120] usb 5-2: new full speed USB device using uhci_hcd and address 8
[   27.596223] Skipping EDID probe due to cached edid
[   27.880123] usb 5-2: device not accepting address 8, error -71
[   27.989269] usb 5-2: new full speed USB device using uhci_hcd and address 9
[   28.400100] usb 5-2: device not accepting address 9, error -71
[   28.400166] hub 5-0:1.0: unable to enumerate USB device on port 2



Anyway, my current plan is to probably downgrade back to 10.04 if I don't get this fixed very soon. Or maybe trying a clean install of 10.10.

---

