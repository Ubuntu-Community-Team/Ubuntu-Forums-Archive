---
title: "Manually turn on Wireless on Ubuntu 10.04"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by dhoenisch on 2010-05-03
Hi all.  I just purchased an Acer Aspire One Model ZG8, and I immediately installed the full blown Ubuntu 10.04 since I don't like the netbook interface of it.  Anyhow, everything works absolutely beautifully, except that I have to activate the wireless every time.  Not a big deal for me, but the person I purchased this for is not going to be able to remember to do this every time she goes to use it.  There is a switch to turn the wireless off and on, but no matter what I do to the switch, the wireless light stays off.  In Windows, it was on, so I'm just assuming that Ubuntu isn't able to turn that LED on.  But, like I said, the wireless does work if I right-click on the network connections icon and check Enable Wirless.  Anyone know how I can leave that permanently enabled?

Thanks,
Dan

---

### Post by Animal X on 2010-05-03
> **dhoenisch said:**
> Hi all.  I just purchased an Acer Aspire One Model ZG8, and I immediately installed the full blown Ubuntu 10.04 since I don't like the netbook interface of it.  Anyhow, everything works absolutely beautifully, except that I have to activate the wireless every time.  Not a big deal for me, but the person I purchased this for is not going to be able to remember to do this every time she goes to use it.  There is a switch to turn the wireless off and on, but no matter what I do to the switch, the wireless light stays off.  In Windows, it was on, so I'm just assuming that Ubuntu isn't able to turn that LED on.  But, like I said, the wireless does work if I right-click on the network connections icon and check Enable Wirless.  Anyone know how I can leave that permanently enabled?

Thanks,
Dan
when you open Preferences>Network Connections....can you see under wireless if the entries are showing auto?(i am noobish, so help may be slow until the cavalry gets here, lol)

---

### Post by dhoenisch on 2010-05-03
Thanks for the reply.

Yup, the one I currently have on there is set to auto.  And when I reboot the machine and right-click on the network icon next to the speaker icon, and check Enable Wireless, it does automatically connect to it.  It's more a matter of having to turning the wireless on every time I boot up.  

The wireless network it is currently on is a hidden network, so not sure if that has anything to do with it, but I would think the wireless adapter should still at least be enabled.  

Dan

---

### Post by Animal X on 2010-05-03
right on, i dont have much experience with this, mine always worked, but im searching and found a few pages, heres one:
[http://ubuntuforums.org/showthread.php?t=969125](http://ubuntuforums.org/showthread.php?t=969125)

---

### Post by dhoenisch on 2010-05-03
Nope, that didn't work.  I still had to enable the wireless after I rebooted.  I'm assuming it has to be something with this PC and the new version of Ubuntu.  I upgraded my home PC from 9.10 to 10.04, and the wireless is automatically on.  I tried another PC here at work using a fresh install and wireless is enabled automatically, so it's definitely a setting missing for this particular laptop through Ubuntu 10.04.  At least I would think so.  Sorry, I've only been a Linux user for only a year, and have been a Windows/PC tech for 14, so I tend to think in Windows terms.  I hope this makes sense...

Dan

---

### Post by Animal X on 2010-05-03
> **dhoenisch said:**
> Nope, that didn't work.  I still had to enable the wireless after I rebooted.  I'm assuming it has to be something with this PC and the new version of Ubuntu.  I upgraded my home PC from 9.10 to 10.04, and the wireless is automatically on.  I tried another PC here at work using a fresh install and wireless is enabled automatically, so it's definitely a setting missing for this particular laptop through Ubuntu 10.04.  At least I would think so.  Sorry, I've only been a Linux user for only a year, and have been a Windows/PC tech for 14, so I tend to think in Windows terms.  I hope this makes sense...

Dan


yeah i was just noticing quite a few posts encountering similar issues with the ubuntu upgrade, predominately seems to be with drivers....sorry i wasnt much better help, but here is one more link i found, dunno if its any good:


[http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)



i gotta wonder if its driver issue or a config file type thang, good luck.

---

### Post by dhoenisch on 2010-05-03
No, no, I appreciate the effort.  I learn more and more as I work out "issues," so I appreciate you stirring me in the right direction.  Although the second link also didn't work, one of the posts I saw in it was about a legacy driver, so now I need to figure out what the wireless card is and see if it is a driver issue that won't allow it to automatically enable itself upon boot-up.  That might also explain why I don't get a wireless LED and why that switch is inactive.  

Dan

---

### Post by Animal X on 2010-05-03
> **dhoenisch said:**
> No, no, I appreciate the effort.  I learn more and more as I work out "issues," so I appreciate you stirring me in the right direction.  Although the second link also didn't work, one of the posts I saw in it was about a legacy driver, so now I need to figure out what the wireless card is and see if it is a driver issue that won't allow it to automatically enable itself upon boot-up.  That might also explain why I don't get a wireless LED and why that switch is inactive.  

Dan
ah yes, "lspci" command then , right?-to figure out what wireless card. Good luck, I'll keep watching here to see how it goes.

---

### Post by dhoenisch on 2010-05-03
Ahh, see, you did help with that command.  If it helps, the wireless card in my netbook is the Atheros Communications Inc. Ar5001 Wireless Network Adapter.  It's giving me something to search on now, though some folks simply cannot get it to work.  I guess I'm already ahead of others out there.  I just can't get it to be turned on upon boot-up.

Thanks again,
Dan

Any other replies are much appreciated.

---

### Post by ajgreeny on 2010-05-03
Right click on the network manager icon in your panel and choose "Edit Connections" then to the wireless tab.  Click on the wireless connection and choose Edit.  After entering the password you will see a window with two small tick boxes top and bottom left for "Connect automatically" and "Available to all users".  Make sure both are selected and that should do it for you.

---

### Post by dhoenisch on 2010-05-03
Nope, I still have to manually turn the wireless on.  

Hey, nice thing about 10.04, rebooting takes just seconds :)

Dan

---

### Post by Nalleman on 2010-05-12
I have the same problem. I have an aspire one A0531h

---

### Post by dhoenisch on 2010-05-12
I never was able to figure it out.  What I'm thinking is it has somehting to do with the physical WLAN switch not being activated within the software.  It really is no big deal to have to activate it every time, if only I'd remember.  On my main laptop, the wireless is active the moment I turn it on, but on this little guy, I start getting a little angry at it until I remember that I forgot that I turned it on.  Anyhow, that laptop was purchased for my mom for Mother's Day, and she has no problems remembering to turn it on manually like I did.  I'm just hoping that an update comes out sometime that will fix it since I can't find any other fix for it.
 
Dan

---

### Post by dpmcalli on 2010-05-16
I have this very same problem. Like you if I right click the network icon and tell it to "enable wireless" it all comes up ok and automatically connects to the access point. I just cant figure out how to automatically enable the card.

Any suggestions? Did either of you ever get this working?

---

### Post by iixdotbe on 2010-06-05
I'm glad I found this thread.  I am having the exact same problem.  I'm hoping for a resolution as the people using these netbooks will have trouble remembering to enable wireless each time.  I'm working on 20 Acer Aspire One ZG5 (AOA 110) netbooks.  And my users are going to be 300+ 8-12 year old kids at an elementary school.

We originally had XP Home on them for last school year and we weren't really happy with it.  This summer I decided to put Ubuntu on and do away with XP.  This is the one issue that is really holding the setup back though.  I installed 10.04 Netbook Remix first and had the same problem.  Plus I thought the changes to the interface were unnecessary so I went to the standard 10.04 desktop edition.  Everything works perfectly but the enable wireless issue.

The Asipre One ZG5 netbooks have the Atheros AR5BXB63 network adapter in them.  The wireless hardware switch is also unusable which I agree with dhoenisch is the root of this problem.

I will bookmark this thread and keep an eye on it.  Thanks.

---

### Post by spiroxlii on 2010-06-05
I'm having the exact same issue with a Sony Vaio VGN-SZ230P laptop.  I am dual-booting between Windows XP and Xubuntu 10.04 (Lucid Lynx).  The wireless card (Intel 3945ABG) and the wireless switch/led function normally in Windows, but I have to right-click on the Network Manager icon and select "Enable Networking" every time I boot into Xubuntu.  Once I manually enable networking, the laptop has no problem automatically joining my wireless networks at home and work (WPA2 and WEP, respectively).

This is just a minor annoyance, but it's an annoyance nonetheless.  I will report back here if I find a solution!

---

### Post by spiroxlii on 2010-06-10
I got tired of trying to make Network-Manager work properly, so I completely uninstalled it and replaced it with another graphical network management program called WICD.

You can do this from the console, but for those of you who prefer clicking on stuff, I just used Synaptic Package Manager to uninstall the package called "Network-Manager," then I found and installed a package called "wicd." Each of those operations will remove and/or install the right additional packages for this to work.

After you've changed network managers, you should see the wicd tray icon instead of the network-manager tray icon when you log on next.  You should be able to pick your wireless network and enter your encryption key fairly easily.  So far, it has worked for me after three restarts.

---

### Post by b k on 2010-06-10
Hi, there may be one or a combination of several factors that results in one not being able to auto connect to your wireless network.

If you have already tried post #10 of this thread and failed to resolve your problem and you still prefer to have [COLOR=Red]both[/COLOR] auto login to user account as well as auto login to your wireless network, you need to consider if your Keyring password/passwords are corrupted (or there is a bug in the Keyring password program?).

[COLOR=Red]Please read posts #9 to #11 of this link [http://ubuntuforums.org/showthread.php?t=1495220](http://ubuntuforums.org/showthread.php?t=1495220) (I presume involving corrupted Keyring passwords) to see if it helps[/COLOR].

I used to have a similar problem when I configured to auto login to my user account upon boot up (but _I did not ever_ enter any Keyring passwords).

At that point in time, I found that the password for the wireless network connection could not be properly saved (Go to *System* > *Preferences* > *Network Connections* > *Wireless* , left click on your wireless name and select edit) even though it was previously entered.
I then configured for manual login to user account at boot up (Go to *System* > *Administration* > *Login Screen* and unticking/unchecking Log in as xxxxxx automatically and checking Show the screen for choosing who will log in) and mysteriously my wireless network automatically connected each time [COLOR=Blue]after manual login to my user account.[/COLOR]

Hope the info is helpful and please provide some feedback to benefit other readers..

Good luck

---

### Post by Delicious Docsy on 2010-07-05
> **ajgreeny said:**
> Right click on the network manager icon in your panel and choose "Edit Connections" then to the wireless tab.  Click on the wireless connection and choose Edit.  After entering the password you will see a window with two small tick boxes top and bottom left for "Connect automatically" and "Available to all users".  Make sure both are selected and that should do it for you.

worked a treat, thanks!

---

### Post by BobC1955 on 2010-07-07
I am a newbie to Ubuntu and after upgrading my son's netbook to Ubuntu 10.04 (to resolve a sound issue after a large corrupted update with Ubuntu 8.04) I have experienced a very similar problem.
The wireless worked ok initially, but had to be within about 6 feet of the wireless router - not much help for a netbook (its a Toshiba NB100) so I tried to check all the settings.
It appears that I need the correct driver for the wireless card (it is an Atheros AR5001 card). I used the help section on the netbook to check the issue (typed "sudo lshw -c network" in the Terminal and got as part of the message "Network unclaimed").
My concern is that there are so many drivers for Atheros which ore out there - which will have to be manually downloaded - and which seem to be for windows machines, that I don't wish to make the situation even worse.
Incidentally the wired connection works fine - but that's not much use for a netbook!
It seems that there are more unresolved "bugs" with Ubuntu than there are with windows!
The situation is unresolved and I woudl appreciate help (in simple terms)

---

### Post by mukesh mahi on 2010-08-25
hi there...I have installed ubuntu 10.04 in my laptop (compaq presario cq 40)...in my laptop its not enabling the wireless...while I have tried it with another vaio laptop and its working there...I have tried even with the ubuntu 9.10...its not working in this also...I have installeed it inside windows...I have tried even full installation of ubuntu...in that case also its not working...please help me turning on the wireless as this is the way I connect to the internet...

---

### Post by wewa on 2010-09-09
I have 3 Compaq Presario A900 series notebooks with Atheros chips and they have all kinds of weird problems.
Tried 3 different brand and models of routers (netgear, buffalo, G, N) to make sure to rule that out.

I thought it was just Atheros, but looks like Intel and Broadcom also have issues: [http://www.google.com/search?q=atheros+intel+broadcom+10.04](http://www.google.com/search?q=atheros+intel+broadcom+10.04)

Why is wi-fi compatibility in Ubuntu 10.04 so bad?
Do they not test before they release?
Doesn't canonical use wi-fi notebooks themselves during development?
Maybe they're on desktops...
:(

UPDATE: today's news makes it sounds like Broadcom is going to be the one to find, when buying in the future, if developers utilitze it:
[http://www.osnews.com/story/23786/BREAKING_BROADCOM_OPEN_SOURCES_WIRELESS_DRIVERS](http://www.osnews.com/story/23786/BREAKING_BROADCOM_OPEN_SOURCES_WIRELESS_DRIVERS)

---

### Post by utilitytrack on 2010-09-11
to **wewa**

> [I]Why is wi-fi compatibility in Ubuntu 10.04 so bad?
Do they not test before they release?
Doesn't canonical use wi-fi notebooks themselves during development?[/I]

I think it's no sense to speak here on this topic. 
If you get some troubles with network subsystem and wish to get help, I suggest to open new thread and describe what's your problems.

---

### Post by aaronklep on 2010-09-18
> **ajgreeny said:**
> Right click on the network manager icon in your panel and choose "Edit Connections" then to the wireless tab.  Click on the wireless connection and choose Edit.  After entering the password you will see a window with two small tick boxes top and bottom left for "Connect automatically" and "Available to all users".  Make sure both are selected and that should do it for you.

This worked great on Ubuntu 10.04.  **THANKS!**

---

### Post by schmickey on 2010-09-19
NONE of the solutions listed in this thread works for me and I have an Intel Advanced-N 6200 card which is natively supported in the kernel.  This isn't a driver issue -- it is a bug in Network Manager on laptops.  I don't even have a physical switch for my wi-fi, so it has nothing to do with that.  Wi-Fi is not disabled in Windows when I shut it down, so it's not that either.

The solution is to find a way to get Network Manager to automatically enable Wireless on boot-up.  Why they wrote it to automatically have wireless disabled on boot makes no sense.  It is not greyed out... it is simply unchecked.  The issue for this thread is having to manually right-click the icon and check "enable wireless" every time we boot.  Why?  Makes ZERO sense.  I never use ethernet, it's a laptop.

Anybody?  Is there some .config file entry I can add for this?

I never had this issue with previous releases, only Lucid.  I'm running the AMD64 on an Acer 1830T-3721.... Core i5-430UM.  I'm wondering if this is an ACPI issue.  The HM55 chipset has aggressive power management but I have not done anything to manipulate power since I installed Lucid.  All I have done is make-install the driver for the Atheros Gigabit ethernet card, which works fine.  But I was having this wireless issue before I did that.. and it continues.

Now before it is suggested again, I did try WICD.  I uninstalled Network Manager, installed WICD and had no networking of any kind after that.  I ended up re-installing Lucid all over again.

I did edit the connection as suggested above.  No problem with that.  As soon as I do the right-click and enable wireless, it connects.  Fine.  But I still have to enable wireless manually on every boot.

This must be a widespread issue since this thread has been viewed over ELEVEN THOUSAND times since it was created. (and still not marked as solved).

---

### Post by Lifer999 on 2010-09-20
As a work-around you may want to put a command in your /etc/rc.local file.  Any commands in this file will be run just after system boot up.

Next time you reboot but before you've activated wireless networking, open a terminal and type the command:

sudo ifconfig eth1 up

but change "eth1" to your wireless card's device name.  If you don't know the device name type in the command:

nm-tool

to list all your network devices.

Once you know the command that will activate your wifi, then place that command (minus the "sudo") at the bottom of your /etc/rc.local file and it should activate on every boot up after that.

---

### Post by schmickey on 2010-09-20
> **Lifer999 said:**
> As a work-around you may want to put a command in your /etc/rc.local file.  Any commands in this file will be run just after system boot up.

Next time you reboot but before you've activated wireless networking, open a terminal and type the command:

sudo ifconfig eth1 up

but change "eth1" to the name of your wireless card's device name.  If you don't know the device name type in the command:

nm-tool

to list all your network devices.

Once you know the command that will activate your wifi, then place that command (minus the "sudo") at the bottom of your /etc/rc.local file and it should activate on every boot up after that.

The "ifconfig wlan0 up" will turn on my wireless light but it does NOT enable wireless in Network Manager.  I still have to right-click the icon and enable wireless manually.  It's a silly and annoying bug.  I could see setting it up this way if eth0 had a connection at boot-up, but otherwise it makes no sense unless you're booting up on battery power and might want to conserve power.

---

### Post by yifangt on 2010-09-24
> **schmickey said:**
> There it is folks!  **Solution** (at least for me it is).

**Kudos to Lifer999!**

Wireless (wlan0) now enabled on every boot.

I'm surprised it took 26 posts to get this. (Also, I should have known to try this myself... my bad.)
My wireless connection is still greyed. I have tried all the suggestions above, specially **sudo ifconfig wlan0 up. **Still did not work. I am desperate to get a solution to this. Thanks a lot!

---

### Post by Lifer999 on 2010-09-25
> **yifangt said:**
> My wireless connection is still greyed. I have tried all the suggestions above, specially **sudo ifconfig wlan0 up. **Still did not work. I am desperate to get a solution to this. Thanks a lot!

Just to clarify,

Have you verified that "wlan0" is your wireless card's device name? If not then open a terminal and enter the command:

nm-tool

to list all network devices and look for the device with type of 802.11

Second, be sure to remove the "sudo" when putting the command into your /etc/rc.local file.

hth.

---

### Post by bbott on 2010-10-04
This problem is in all Linux distributions, not just Ubuntu. As far as I can tell the Linux Kernel update includes a new WiFi interface to accomodate people who want  to use laptops on planes. The new interface allows the radio to be switched on or off, but instead of defaulting to on it defaults to 'off' this has meant that many users now find they can't use WiFi on Linux. A silly update pandering to those who use computers whilst flying. 
I've not found a good work around, the problem is that some WiFi cards don't reply to queries from  rfkill, this means that they aren't recognised and wireless is disabled. 
This problem has been about for over a year now and the Linux developers don't appear to know how to deal with it.
If someone out there does know I'll be pleased to use the fix.

---

### Post by bbott on 2010-10-05
Hi found a reference to the rfkill module
[http://www.linuxhq.com/kernel/v2.6/27/Documentation/rfkill.txt](http://www.linuxhq.com/kernel/v2.6/27/Documentation/rfkill.txt)
tells all there is to know about rkill and why it's there, but no solution to wireless not being enabled!

---

### Post by ecowan on 2010-10-05
Here's what works for me...

I have an IBM T60 with a built-in wifi.
My home network is hidden and uses WPA with PSK.

I installed and upgraded kubuntu 10.4.
I switched to Synaptic to manage my software packages.
I installed Wicd and removed Network Manager to get wifi to work at all.

In Synaptic to Repositories I added ...
deb [http://backports.debian.org.debian-backports](http://backports.debian.org.debian-backports) lenny-backports main
I selected Wicd and using Packages/Force version.. installed 1.6.2.2.

A reboot brought up the Wicd icon in the system tray.

Now Wicd works properly. It remembers my network and connects automatically. This also works on my kids' Ubuntu laptop.

I have two laptops for my kids as well as my own. Network Manager was useless, and Wicd 1.7.0 required a lot of fiddling to get a connection after each boot.

I have Kubuntu Karmic on one laptop. Somehow an upgrade brought in Wicd 1.6.2.2 which worked just as you'd expect. But that version doesn't show up if you look in the Ubuntu Karmic repositories. I only found it in Debian.

I hope some of this gets bumped up to the quality assurance people and the developers. Meanwhile I must remember not to Mark All Upgrades.

- Erny

---

### Post by bbott on 2010-10-06
Hi, I spent  5.99 on a manual for my Acer travelmate 4201. I hoped that the toggle for wireless might be explained. To my suprise the manual showed the bluetooth and wireless switches on the front of the laptop. I've never had to use them in the past 4 years, but when I pressed it he presto wireless is on permenantly. If you have an Acer and can't get wireless have a look at the front of the laptop. 
The best 5.99 I've ever spent.

---

### Post by dcommini on 2010-10-07
> **spiroxlii said:**
> I got tired of trying to make Network-Manager work properly, so I completely uninstalled it and replaced it with another graphical network management program called WICD.

You can do this from the console, but for those of you who prefer clicking on stuff, I just used Synaptic Package Manager to uninstall the package called "Network-Manager," then I found and installed a package called "wicd." Each of those operations will remove and/or install the right additional packages for this to work.

After you've changed network managers, you should see the wicd tray icon instead of the network-manager tray icon when you log on next.  You should be able to pick your wireless network and enter your encryption key fairly easily.  So far, it has worked for me after three restarts.

This worked perfectly for me! After two weeks of no internet on my acer I finally got it working in just a matter of minutes after changing over to wicd. (Well, I wasn't working on my computer for those two weeks... the military keeps me busy, but after all the looking I did this worked like a charm!)

---

### Post by ksanger on 2010-11-08
Using a Toshiba Portege R705.  Just installed ubuntu 10.04 using WUBI.  No wireless connections found, wireless enabled. 

Entered SSID (wireless network name) and WPA WPA2 password and sellect all users.

System Preferences (Startup Applications) (Network Manager) is enabled with the command "nm -applet --sm-disable"  Don't know what this does yet.

The shell command "sudo lshw -C network" results in an Eithernet Connection which is disconnected and a Wireless Connection that is Disabled.  Even though network manager wireless is enabled.

Product: WiMAX/wiFi Link 6050 Series
Vendor: Intel Corporation
physical ID: 0
logical name: wlan0
plus more info on the device.

Any help would be appreciated.  I don't know what else to try.  I've rebooted once prior to setting the SSID and the password.  I also have dual boot to Win7 and only one common partition as we installed using WUBI.

---

### Post by readability on 2010-11-28
try placing;
```
nmcli nm wifi on
```
in */etc/rc.local* using;
```
sudo nano /etc/rc.local
```
-make sure to add the line **before** *exit 0* in the file.
-this will instruct network manager to enable wifi on every login
-solved issue on Acer Aspire One 721, Ubuntu 10.10 x64

([looks like]("http://ubuntuforums.org/showthread.php?t=1563463") nmcli is only available in 10.10, I'd imagine you could accomplish the same thing using dbus-send in other versions)

---

### Post by ksanger on 2010-11-28
Sorry I have this running now.  Required loading the correct driver as 10.04 did not include drivers for Intel 6250 WiFi.  Then I needed to delete the wireless connection as I entered it in by hand and when the new driver loaded it must have been confused between the detected network and the entered network with the same name.  Once I deleted the entered network, with the correct driver, and rebooted it found my network and I'm in.

---

### Post by snoopy1 on 2010-12-29
> **readability said:**
> try placing;
```
nmcli nm wifi on
```
in */etc/rc.local* using;
```
sudo nano /etc/rc.local
```
-make sure to add the line **before** *exit 0* in the file.
-this will instruct network manager to enable wifi on every login
-solved issue on Acer Aspire One 721, Ubuntu 10.10 x64

([looks like]("http://ubuntuforums.org/showthread.php?t=1563463") nmcli is only available in 10.10, I'd imagine you could accomplish the same thing using dbus-send in other versions)

Thanks so much!  This solution worked perfectly for me!

---

### Post by opasnost on 2011-02-05
Snoopy this also worked for me too. Using Aspire one 721

after suspending or hibernating though the wireless would be again disabled. I'm sure some of you guys are having the same problem. It took me some time but I created a script to solve this problem

Try this first in terminal

```
rfkill unblock wifi
```then

```
nmcli nm wifi on
```then wait for a bit your wireless should now be enabled...wait some more and it should connect wirelessly to the network

if that worked go ahead and follow the steps below

create a file in /ect/pm/sleep.d       name it for example     enable-wireless.sh
then make it executable using 
```
sudo chmod +x /etc/pm/sleep.d/enable-wireless.sh
```now open it using

```
sudo gedit

```then put this script in there

```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)        
    rfkill unblock wifi
    sleep 1    
    nmcli nm wifi on
        ;;
    *)
        ;;
esac
exit $?
```save and try suspending and hibernating. I'm still sort of a noob at this so sorry for the unorthodox instruction maybe someone can clean this up. I hope it helps though;)

I am running an aspire one 721-3922 using 10.10 64 bit

---

### Post by Cold Man 1 on 2011-04-08
Okay, this took me about 3 painstaking days to figure out so i hope it helps everyone else :) Follow the steps.....

1) make sure the physical switch on your computer is set to the 'on' positions or this won't work.

2) Connect to the internet via a lan cable then go to terminal and type this in....
           ```
sudo apt-get install rfkill
```

3) reboot. 
    a) [OPTIONAL] Go to your bios and reset it to its default settings. Only try this if it doesn't work initially

4) open terminal again and type in 
```
rfkill unblock all
```

5) your wifi should be enabled!

                             ENJOY

---

### Post by jalirious on 2011-05-09
[http://forums.linuxmint.com/viewtopic.php?f=53&t=57937](http://forums.linuxmint.com/viewtopic.php?f=53&t=57937)

Fixed for me on 10.04 64bit, acer aspire 5742, 9/5/11.

---

### Post by hearthand on 2011-07-28
Ok-I had this problem too this is what just fixed it.

1, attach directly to the internet with the cable.
2, open the search and find the update package installer
3, run this and install all the updates, reboot
4, when the system reboots, click the idle wireless network icon on the top navigation bar, uncheck enable wireless then recheck it.
 my system downloaded new drivers and installed them, then the internet worked fine.

---

### Post by william80 on 2012-01-08
hi can someone please guide through to set up my wireless connection, im runing ubuntu netbook edition(10.04), runing it off a live usb stick, my computer is acer aspire one d257. can anyone please help im  a huge fan linux. thanks in advance

---

