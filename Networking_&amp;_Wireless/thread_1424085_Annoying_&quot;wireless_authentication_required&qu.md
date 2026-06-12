---
title: "Annoying &quot;wireless authentication required&quot;"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by iClouseau88 on 2010-03-07
Hi,

I just installed Ubuntu 9.04 then immediately upgraded to 9.10. My laptop has Linksys WPC300N PCMCIA wireless adapter so during installation bcm43-fwcutter and BroadcomSTA linux driver were automatically installed. I have no problem with wired connection. However, I keep seeing the "Authentication required for wireless network connections" popped up, even though SSID and WPA/WPA2 passphrase were entered correctly initially. I hit CANCEL then Network manager shows "Wireless Network" disconnected, then the Wifi or stairstep icon appears.  When there's no cable connection, wireless works fine.  Just noticed that only 1 light (Power) shows on the card.  It just bothers me that the "wireless authentication required" screen keeps popping up and interferes with my typing.

Not sure if this problem has anything to do with keyring manager.  I did uninstall then reinstall NetworkManager and NetworkManager-gnome but problem still persists.  I would much appreciate your help.

---

### Post by lidex on 2010-03-07
This may help:
[http://art.ubuntuforums.org/showthread.php?p=8772923]("http://art.ubuntuforums.org/showthread.php?p=8772923")

---

### Post by iClouseau88 on 2010-03-07
Thank you lidex for giving me the link.  The problem was solved by the following steps:

1.  Edit wireless connection.

2.  Put a check mark beside "available to all users"

3.  Hit "Apply"

4.  Unplug internet cable

5.  Double click on SSID name

6.  Wireless connection is now established.  No more screen requiring authentication.

Steps 2 and 3 solve the problem.  Make sure there's a check mark in "connect automatically" for one's wireless connection.

---

### Post by gatesdrovme2it on 2012-02-02
I tried this but no luck.  Any other suggestions?

---

### Post by gatesdrovme2it on 2012-02-03
No, really- I'm desperate!  How can I fix this?  Anyone have any idea at all??

---

### Post by kurt18947 on 2012-02-03
> **gatesdrovme2it said:**
> No, really- I'm desperate!  How can I fix this?  Anyone have any idea at all??

These problems are oftentimes chipset specific.  Maybe start by opening a terminal and posting the output of 'lspci" for an internal adapter or 'lsusb' for a usb dongle.  The line that really matters may contain 'network controller' or 'wireless' Here is mine for example:

Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271].

If I had a problem I'd search in the Networking & Wireless forum for "Atheros AR9271+authenication required" or something along those lines and see if anyone else has had the same issue.

---

### Post by gatesdrovme2it on 2012-02-03
Kurt you are my new favorite person.  LOL.  I have only been using Ubuntu for about 4 days- I've only done DOS and Windows in the past.  The straw that broke the camel's back was an installation "endless loop" problem with Windows XP.  I've sworn off Microsoft forever.  :)

Here is the output from the command (lspci) that you mentioned:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

Again- I know nothing about this at all- but I think based on what you've said I need to search the forum for "Realtek RTL8188CE" so that is my next step.

:KS:KS:KS:KS:KS
You are a 5-star guy Kurt- thanks for your help!!!

ps- I see those little codes that people type into the terminal and get info all over the forum here.  Is there a site on the web that lists all of those that are available along with descriptions of their usage?  That might help me into my Linux experience.

---

### Post by gatesdrovme2it on 2012-02-06
bump

---

### Post by gatesdrovme2it on 2012-02-07
Nobody has a clue?  help a fellow Ubuntu user out!  I'm a total noob- but ready to learn!!!

---

### Post by gatesdrovme2it on 2012-02-07
anyone with an idea?  even if you aren't sure, just some guesses as to where i can start to troubleshoot this thing...i'm a complete Linux noob so i am eager to learn.

---

### Post by kurt18947 on 2012-02-07
Hmmm, hadn't noticed your bumps, sorry.  Which distro/version are you using? If you're using older than 11.10,I believe the first thing I'd try is to download and create a liveCD or LiveUSB of a current version of your favorite flavor (Ubuntu, Xubuntu, Lubuntu, Mint etc.).  If the chipset has kernel support it will work with a LiveCD/LiveUSB install.  I believe support for that chip set is built into the kernel starting with 11.10, not on earlier versions hence the need to build drivers.  I should be receiving an adapter with an 8188CUS chipset in the next couple days.  It'll be interesting to see how it behaves.

---

### Post by gatesdrovme2it on 2012-02-07
Thanks Kurt!!!!

I am using Ubuntu 11.10.  This is my first try at Linux and I really love it, I just have to get these few kinks worked out.  I have been at this about a week or so, and the vast majority of the time I am getting the wireless authetication issue.  However, in the last day or so I noticed that when I turn wireless "on" it will now connect.  I would think this problem will come back though, and since I didn't solve it other than to (possibly) disable selinux, I think the problem is still there.

Also i have that red triangle with an exclamation at the top of my screen but I can't seem to update.  Update manager will come up but it says no updates to install.   When I try the "check" option it goes through this long trying to download or something phase, then it says it can't connect to the repository.  Even if I am hooked up to wired internet I get this issue.

Sorry I don't know what is relevant info to tell you about my problem.  If you need me to run any codes from terminal I will.

Thanks!!!!!

Dave

---

### Post by kurt18947 on 2012-02-07
Bear in mind that I am no kind of expert, just somebody who's been blundering around this stuff for a while so bear that in mind. A couple things come to mind.  One is to try WiCD in place of NetworkManager applet. Some people have reported better luck with WiCD. It  can be found in the repositories.  Make sure both Network Manager and WiCD are on available on your machine before uninstalling NetworkManager.  You cannot have both network managers enabled at the same time and it's awkard to find yourself with no GUI network manager. It is possible to configure networks via the command line but that is beyond my abilities though there are tutorials online.  How do you read the tutorials if you can't get online?  Uh oh. 

Another thing to try might be to be sure backports is enabled so any new drivers are installed.  You can check in update-manager. One of the tabs will show backports and has a checkbox to enable or disable. I should get my new adapter Thursday. I'll let you know how I make out. 

Re the triangle with exclaimation mark, if update manager doesn't install updates, you can try two things.  I prefer Synaptic Package Manager to Ubuntu Software Center. When logged onto an account with sudo authorization, I check "mark all updates" See what if anything will be downloaded.then click "apply" if things look reasonable.   The other method is via command line. Open a terminal and type "sudo apt-get update" enter sudo password when requested and wait for it up update. Once updated, you can type "sudo apt-get upgrade", you probably won't need to type a password then see if the updates were just installed.  This might also help with your wireless problems if updated drivers are available but not being downloaded for whatever reason.

---

### Post by gatesdrovme2it on 2012-02-09
Thank you a bunch for all of that info.  I installed WicD and it seems cool- and I think I managed to un-install Network Manager via Synaptic Package Manager.  There were two different entities marked "Network Manager" but only one could be un-installed so that is the one I chose.  It's too early to tell if this is working but I'm excited to give it a spin around the block.

I can't seem to find backports anywhere.  Where exactly in Update Manager are they, and can I also find them in Synaptic Package Manager?

I used SPM to do the "mark all updates" and none were marked.  I also did it from the terminal and nothing was installed.  So maybe there really are none.

Thanks so much for all of your help Kurt- I appreciate you!

---

### Post by kurt18947 on 2012-02-09
> **gatesdrovme2it said:**
> 
<snip>
I can't seem to find backports anywhere.  Where exactly in Update Manager are they, and can I also find them in Synaptic Package Manager?

I used SPM to do the &quot;mark all updates&quot; and none were marked.  I also did it from the terminal and nothing was installed.  So maybe there really are none.

Thanks so much for all of your help Kurt- I appreciate you!

I hope it works for you.  I have Precise open here, Oeneric may be somewhat different.  I find backports in Update Manager -> Updates -> 4th check box.  It's labeled Unsupported updates (precise-backports). 
[B]
Update:[/B]  I received the RTL-8188CUS adapter (Edimax EW-7811Un).  I did not find it to be plug & play. The adapter was recognized but would not connect to a WPA2 system. The adapter was recognized, the blue light was on steady but when I went to connect the light stayed on steady rather than flashing and after perhaps 20 seconds I was again prompted to the network encryption key.  Network Manager and iwconfig both said I was connected but no ping or other indication of a functioning network connection.

I wanted to try an unencrypted connection but did not find a way to do that with the Verizon ActionTec router. I blacklisted the built-in drivers and downloaded the driver from RealTek's site and ran 'install.sh'.  It was a painless process and the adapter works, suspends and resumes. Speed according to speedtest.net is not as good as RTL-8192SU adapters.  So for me the built-in driver seems not up to snuff but the RealTek driver works.  I'll have to see how big a pain rebuilding the driver due to kernel updates is.  I may investigate dkms.

---

### Post by gatesdrovme2it on 2012-02-17
That's really unfortunate that the adapter did not work.  It would be nice to have a fresh solution to these issues.  I am struggling with both my Lenovo S100 and my HP mini.  Neither wired nor wireless connections work reliably.  

I have installed wicd but being so new to linux it has been a struggle to figure out how to disable Ubuntu's network manager.  I am guessing issues like this are what drive people back to windows?  I'm really not eager to do that but progress is awfully slow just trying to get an internet connection.

Are there any resources that you, Kurt, or anyone else reading this thread might be able to steer me toward to help me resolve the network issues?  I still have the red triangle at the top of my screen but can never seem to update my machine whether my internet connection is working or not- wired or wireless.  At times I can download huge files via P2P- season-long TV show torrents.  But I can't update any software on my machine.

Please, if I am missing something here would someone fill me in?  If Ubuntu was this hard I can't imagine anyone would use it.  And keep in mind this is on two totally different machines.  

Help please- anyone?

---

### Post by gatesdrovme2it on 2012-02-17
" I have Precise open here, Oeneric may be somewhat different.  I find  backports in Update Manager -> Updates -> 4th check box.  It's  labeled Unsupported updates (precise-backports)."

I still can't find this, or anything remotely resembling this.  What is "precise"?

---

### Post by MDH40 on 2012-12-13
Delete wireless network.
Reconnect.

---

