---
title: "](*,)  Wireless under Dapper without ndiswrapper?"
date: 2006-04-06
forum: Networking &amp; Wireless
---

### Post by bettermentflux on 2006-04-06
Long time Geek, first time penguin.

Here's the situation: I have a spankin'-fresh copy of Dapper Drake 6.04 but no wireless.

I've read a million threads/articles on getting wireless, especially Broadcom caused problems, working under Linux/ubuntu, but I'm starting a new thread because the ndiswrapper suggestions seems to assume that there's no built-in support and Dapper includes drivers out of the box and does seem to recognize me card.

I'm using Dapper 6.04 for AMD64 on a Compaq R4100 Laptop with an internal Broadcom 43xx-based chipset.

My **wireless network is configured as "open"** so as not to introduce wep/wpa, hex typos or any other issues into the mix.

Here's the step-by-step approach I've used, startng with a fresh install:

[LIST]
[*]Wireless is turned on in BIOS
[*]Boot up using "noapic" (included because I'm not sure what is or isn't relevant.)
[*]The wireless connection icon on the top toolbar that was there during the Live preview is gone after install.
[*]The pretty blue wireless active light on my laptop is off.
[*]Click on Network Manager and get the message: "SIOCGIFFLAGS error: No such device"
[*]Right-click Network Manager and select "properties"
[*]The Connection Name input is blank, although "lo" is available in the dropdown. (I've alternativly left the Connection Name blank, tried the essid network name and tried a unique name with the same results.)
[*]Click on configure, and type in my password
[*]The card has been identified by Dapper as eth1 and states that it has not been configured.
[*]Highlight eth1 and choose "properties".
[*]Select "enable this connection"
[*]enter the essid (I've tried with and without quotation marks and both hex and ascii for the key type.) 
[*]Leave the WEP key blank
[*]All other tabs and settings have been left in their default states (Host name, etc)
[*]select DHCP and click "OK" to exit the properties settings.
[*]Click "activate" and the "Activating interface eth1" splash shows up.
[*]After a sizeable delay the spash goes away and the eth1 card is now listed as being active.
[*]I set the default gateway device to eth1 and click OK to close Network Manager. Another overly long pause.
[/LIST]

Open a terminal window and run iwconfig to get this. 

eth1 IEEE 802.11b/g   ESSID:"default"   Nickname:"Broadcom 4318"   Mode:Managed   **Access Point: Invalid   Bit Rate=1 Mb/s**   RTS thr: off   Fragment thr: off

Go to System Device Manager and see that Dapper has correctly identified the card as a Broadcom BCM4318 [AirForce One 54g] 802.11g and the driver in use as bcm43xx.

I've also popped in a Linksys WPC54G (also using a #@&*%@ Broadcom 43xx chipset) with almost identical results.

The fact that it can't find the access point is driving me nuts! Is this a Dapper beta issue? N00bie mistake, config problem, the Broadcom drivers, or what?

I've tried wifi-radar as well but it can't see the access point either. Signal is strong and the card/settings work fine under XP.

Hopefully I'll find a solution and document it here to help others with the same problems. Looks like a fabulous system - can't wait to get it working.

Thanks in advance.

---

### Post by Azrael on 2006-04-06
You might want to check the logs (open a terminal and look through the output of *dmesg* and/or *cat /var/log/messages*) to see if the driver is barfing any error messages.

---

### Post by bettermentflux on 2006-04-06
/var/log/messages shows the bcm43xx driver loading with no error messages.

I also edited etc/network/interfaces/ to remove all customization (leaving only lo) rebooted and had the same access point problem.

---

### Post by n0ah420 on 2006-04-06
I have the same chipset on a similiar HP laptop.  Save yourself some stress and use ndiswrapper.  Although it is possible to get the kernel driver running its a pain in the arse.  Also it exhibited some very strange behavior on my machine.  Now ndiswrapper is also not working like it should, but it is working and I am writing this email over a secure wireless connection.  Check out the following links for all the information you need to get your wireless running with ndiswrapper or built-in kernel driver:

[https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver)

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

---

### Post by shahrc on 2006-04-06
[QUOTE=bettermentflux]Long time Geek, first time penguin.

Here's the situation: I have a spankin'-fresh copy of Dapper Drake 6.04 but no wireless.

I've read a million threads/articles on getting wireless, especially Broadcom caused problems, working under Linux/ubuntu, but I'm starting a new thread because the ndiswrapper suggestions seems to assume that there's no built-in support and Dapper includes drivers out of the box and does seem to recognize me card.

I'm using Dapper 6.04 for AMD64 on a Compaq R4100 Laptop with an internal Broadcom 43xx-based chipset.

My **wireless network is configured as "open"** so as not to introduce wep/wpa, hex typos or any other issues into the mix.

Here's the step-by-step approach I've used, startng with a fresh install:

[LIST]
[*]Wireless is turned on in BIOS
[*]Boot up using "noapic" (included because I'm not sure what is or isn't relevant.)
[*]The wireless connection icon on the top toolbar that was there during the Live preview is gone after install.
[*]The pretty blue wireless active light on my laptop is off.
[*]Click on Network Manager and get the message: "SIOCGIFFLAGS error: No such device"
[*]Right-click Network Manager and select "properties"
[*]The Connection Name input is blank, although "lo" is available in the dropdown. (I've alternativly left the Connection Name blank, tried the essid network name and tried a unique name with the same results.)
[*]Click on configure, and type in my password
[*]The card has been identified by Dapper as eth1 and states that it has not been configured.
[*]Highlight eth1 and choose "properties".
[*]Select "enable this connection"
[*]enter the essid (I've tried with and without quotation marks and both hex and ascii for the key type.) 
[*]Leave the WEP key blank
[*]All other tabs and settings have been left in their default states (Host name, etc)
[*]select DHCP and click "OK" to exit the properties settings.
[*]Click "activate" and the "Activating interface eth1" splash shows up.
[*]After a sizeable delay the spash goes away and the eth1 card is now listed as being active.
[*]I set the default gateway device to eth1 and click OK to close Network Manager. Another overly long pause.
[/LIST]

Open a terminal window and run iwconfig to get this. 

eth1 IEEE 802.11b/g   ESSID:"default"   Nickname:"Broadcom 4318"   Mode:Managed   **Access Point: Invalid   Bit Rate=1 Mb/s**   RTS thr: off   Fragment thr: off

Go to System Device Manager and see that Dapper has correctly identified the card as a Broadcom BCM4318 [AirForce One 54g] 802.11g and the driver in use as bcm43xx.

I've also popped in a Linksys WPC54G (also using a #@&*%@ Broadcom 43xx chipset) with almost identical results.

The fact that it can't find the access point is driving me nuts! Is this a Dapper beta issue? N00bie mistake, config problem, the Broadcom drivers, or what?

I've tried wifi-radar as well but it can't see the access point either. Signal is strong and the card/settings work fine under XP.

Hopefully I'll find a solution and document it here to help others with the same problems. Looks like a fabulous system - can't wait to get it working.

Thanks in advance.[/QUOTE]

Hey...bro..

Your problem is also my problem..I'm using Dapper 6.06 on ACER 3002NCLI machine. When I use SMC 2635W PCMCIA card I have no problem..

I know that Breezy 5.10 does not detect Broadcom card and I installed ndiswrapper with the original win32 driver as well as the native driver, but still unable to bring up the wlan0.

Hopefully someone can help us.

---

### Post by guitarist on 2006-04-06
[QUOTE=bettermentflux]Long time Geek, first time penguin.

Here's the situation: I have a spankin'-fresh copy of Dapper Drake 6.04 but no wireless.

I've read a million threads/articles on getting wireless, especially Broadcom caused problems, working under Linux/ubuntu, but I'm starting a new thread because the ndiswrapper suggestions seems to assume that there's no built-in support and Dapper includes drivers out of the box and does seem to recognize me card.

I'm using Dapper 6.04 for AMD64 on a Compaq R4100 Laptop with an internal Broadcom 43xx-based chipset.

My **wireless network is configured as "open"** so as not to introduce wep/wpa, hex typos or any other issues into the mix.

Here's the step-by-step approach I've used, startng with a fresh install:

[LIST]
[*]Wireless is turned on in BIOS
[*]Boot up using "noapic" (included because I'm not sure what is or isn't relevant.)
[*]The wireless connection icon on the top toolbar that was there during the Live preview is gone after install.
[*]The pretty blue wireless active light on my laptop is off.
[*]Click on Network Manager and get the message: "SIOCGIFFLAGS error: No such device"
[*]Right-click Network Manager and select "properties"
[*]The Connection Name input is blank, although "lo" is available in the dropdown. (I've alternativly left the Connection Name blank, tried the essid network name and tried a unique name with the same results.)
[*]Click on configure, and type in my password
[*]The card has been identified by Dapper as eth1 and states that it has not been configured.
[*]Highlight eth1 and choose "properties".
[*]Select "enable this connection"
[*]enter the essid (I've tried with and without quotation marks and both hex and ascii for the key type.) 
[*]Leave the WEP key blank
[*]All other tabs and settings have been left in their default states (Host name, etc)
[*]select DHCP and click "OK" to exit the properties settings.
[*]Click "activate" and the "Activating interface eth1" splash shows up.
[*]After a sizeable delay the spash goes away and the eth1 card is now listed as being active.
[*]I set the default gateway device to eth1 and click OK to close Network Manager. Another overly long pause.
[/LIST]

Open a terminal window and run iwconfig to get this. 

eth1 IEEE 802.11b/g   ESSID:"default"   Nickname:"Broadcom 4318"   Mode:Managed   **Access Point: Invalid   Bit Rate=1 Mb/s**   RTS thr: off   Fragment thr: off

Go to System Device Manager and see that Dapper has correctly identified the card as a Broadcom BCM4318 [AirForce One 54g] 802.11g and the driver in use as bcm43xx.

I've also popped in a Linksys WPC54G (also using a #@&*%@ Broadcom 43xx chipset) with almost identical results.

The fact that it can't find the access point is driving me nuts! Is this a Dapper beta issue? N00bie mistake, config problem, the Broadcom drivers, or what?

I've tried wifi-radar as well but it can't see the access point either. Signal is strong and the card/settings work fine under XP.

Hopefully I'll find a solution and document it here to help others with the same problems. Looks like a fabulous system - can't wait to get it working.

Thanks in advance.[/QUOTE]


I have the exact same card (bcom 4318/AFOne 54g) and have beat my head against the bcm43xx wall for nearly a week. ](*,)  The short answer: blacklist the bcm43xx driver and install ndiswrapper.  The bcm43xx driver is still in its infancy, and it doesn't like our card very well.  Also, even if you get it working, it does not yet (or didn't then) support WEP (much less WPA) so it's not really even worth the effort unless you live in the boonies.

Just my 2 cents/weeks worth of time.

---

### Post by bettermentflux on 2006-04-06
It's really a shame. Broadcom and every major manufacturer that uses thier chips should be taken to task.

With Ubuntu et al it's really beginning to look like Linux is prepped for a larger audience, but when hardware isn't working and the answer is to recompile this, *sudo *that and *modprobe *the other... it makes for a steep learning curve.

My mother finally figured out how to set the clock on her VCR. I don't think I could have sold her on the wonders of DVD if the upgrade required that she become proficient with a soldering iron.

// end off-topic rant

---

### Post by n0ah420 on 2006-04-06
Not to feed the flames of this fire...but to its credit , linux it was not original designed for the purpose that many people have tred to place it in.  Yes is tough sometimes...but the speed at which this platform has grown in the last few years is tremendous.  For the average dekstop user Ubuntu should install and run without issue (except for the rare few and it happens to windows too).  

The point is that I am just happy it works...and if you just happen to learn something along the way then you are all the better for it.

So its OK to vent, I do it my self; but have faith that if this is something you want to do, then it will work, becuase you want it to...its just a matter of time (and loads of patience).

---

### Post by shahrc on 2006-04-07
Hi guys,

Don't mind asking, which version of ndiswrapper & driver that you guys choose to use with this card? I've been trying on **Dapper 6.06** and **Breezy 5.10** with Ubuntu *preinstalled* ndiswrapper, but failed  both.

Thx

---

### Post by shahrc on 2006-04-07
Hi guys,

Don't mind asking, which version of ndiswrapper & driver that you guys choose to use with this card? I've been trying on **Dapper 6.06** and **Breezy 5.10** with Ubuntu *preinstalled* ndiswrapper, but failed  both.

Thx  ](*,)

---

### Post by trent dillman on 2006-04-07
Haha at least it worked for some of you using ndiswrapper from the repos.

I'm using a home-brew 2.6.16 kernel and had to compile ndiswrapper from source before it would work for me.

---

### Post by n0ah420 on 2006-04-07
It has worked from repos in the past, however this time around I am using the compiled source.  Seems like the safer bet and it really takes no effort to compile it.  Just apt-get build-essential and the kernel headers, download the source, make install.  Its pretty quick.

---

### Post by apoclypse on 2006-04-07
Did you guys try taking out the bcm43xx module out? I had the same issues when I first installed ndiswrapper. Once you take out the bcm module out, it should kick up right away.

---

### Post by mjg59 on 2006-04-07
You need to install the firmware for your card. See section 2 of [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx) for instructions on how to do that - there's a package in the archive which includes the fwcutter utility now, so you don't need to download the source code.

WPA and WEP should work fine.

---

### Post by guitarist on 2006-04-07
As far as ndiswrapper goes for those of you interested in using it: I've found version 1.2 from the sourceforge site is most compatible with the bcom4318 in my 'puter.

You do have to compile it, but that doesn't take long nor is it hard.

RE: the bcm43xx driver: maybe I'll have to give it a try; it was a couple months ago the last I attempted it.

---

### Post by n0ah420 on 2006-04-07
I did blacklist the kernel module, still had issues.  My 4308 card never had issues but this 4318 card is a pain in the rear.  None-the-less, its working now so it doesn't really matter.

---

### Post by mjg59 on 2006-04-07
I should probably mention that the latest kernel (2.6.15-20) has a lot of fixes to bcm43xx support, so it should be a great deal more stable for people. There's still one or two minor issues (I occasionally need to do sudo iwlist scan before it'll associate), but other than that it works pretty much perfectly. We'd like to get as many people as possible testing it before release, in order to know how much information to provide in the installation notes.

---

### Post by bettermentflux on 2006-04-07
In [WifiDocs/Driver/Broadcom43xx]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver") it says: > If you can't get it working with a bcm4318, don't be suprised. There are some successes, but most often failure, so just resort to the ndiswrapper if you fall into this category. Hopefully updates are in the near future.

Does anyone know if this is still accurate? I've seen mention in this thread and others to updates that might make it automagically work. My preference would be to try and wrestle the BCM43xx drivers into submissions before I give in to ndiswrapper/Windows drivers.

re: *We'd like to get as many people as possible testing it before release, in order to know how much information to provide in the installation notes.*

---

### Post by n0ah420 on 2006-04-07
It automagically works if the following conditions are met:

1) The proper firmware for your device is on the machine
2) You don't use WEP or WPA
3) You have SSID broadcast turned on
4) You don't have the need to connect at 54Mbps

If you are one of the few who can accept these things I say go for it, otherwise save yourself some stress and use ndiswrapper.  We all know it works and works well.  That can't be said for the kernel drivers.  Sadly it will be dapper + 1 (imho) before this is sorted out.

---

### Post by bettermentflux on 2006-04-07
I wonder if this is helpful info in debugging the problem: When I tried to explicitly set the access point essid with *sudo iwconfig eth1 ap default* I recieved this error:

Interface eth1 doesn't support IP addresses
eth1      Interface doesn't support IP addresses
Error for wireless request "Set AP Address" (8B14) :  invalid argument "default".

---

### Post by bettermentflux on 2006-04-07
[QUOTE=n0ah420]It automagically works if the following conditions are met:

1) The proper firmware for your device is on the machine
2) You don't use WEP or WPA
3) You have SSID broadcast turned on
4) You don't have the need to connect at 54Mbps

If you are one of the few who can accept these things I say go for it, otherwise save yourself some stress and use ndiswrapper.  We all know it works and works well.  That can't be said for the kernel drivers.  Sadly it will be dapper + 1 (imho) before this is sorted out.[/QUOTE]

Thanks for the caveats. That's a pretty clear indication on whether it's even worth the bother.

And just to clarify #1, I take it you mean by using fwcutter to replace whatever drivers Dapper 6.04 installed by default? (which in my case, I believe, would mean using the Windows 64 drivers provided by Broadcom).

---

### Post by mjg59 on 2006-04-07
[QUOTE=n0ah420]
2) You don't use WEP or WPA
[/QUOTE]

That's just untrue. It works fine with WPA.

---

### Post by mjg59 on 2006-04-07
[QUOTE=bettermentflux]
And just to clarify #1, I take it you mean by using fwcutter to replace whatever drivers Dapper 6.04 installed by default? (which in my case, I believe, would mean using the Windows 64 drivers provided by Broadcom).[/QUOTE]

fwcutter provides firmware, it doesn't replace any drivers.

---

### Post by trubblemaker on 2006-04-07
k' I can help you get your bcm4318 driver working, I run it and have for 2 months now and have spent 3 months working on helpping people get it running, here's the 123 of how to make it work.

before we go any farther, the native driver for bcm4318 only works at 11Mbs, if that works for you read on

install the deb, 

```
apt-get install bcm43xx-firmware
```
then get you card working on an unencrypted network ** until it's working properly**
once you've installed the drivers you should get a list of networks by using
```
 iwlist eth1 scan 
```
if you do great on to the next step:

then you need you can run this script to get started, it should help prove that you can connect with the drive, slap it in a file use the good old
chmod u+x [scriptname] and it should connect you just like that:
```
#!/bin/bash
if [ "$1" == --help ] 
then
  echo "Listing of ESSID's"
  # Lists the availble ESSIDs
       iwlist  scan | grep ESSID
  echo "Likely interface: "
  # Grabs the name of the interface that succefully scanned
  iwlist scan | grep completed | sed "s/Scan\scompleted\s://g"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  echo "Usage: getit [interface] [essid]  "
  echo "Pick one of the above interface and essid's"
  echo "use the interface that had the essids"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  exit 
fi
if [ -z $2 ] ; then
        myEssid=any
else
        myEssid=$2
fi  

if [ -z $1 ] ; then
        myInterface="eth1"   # typically eth1 but may be something else
else
        myInterface=$1
fi  

echo "Bringing network down"
sudo ifconfig $myInterface down &>/dev/null                 
echo "Bringing network back up"
sudo ifconfig $myInterface up &>/dev/null
echo "Changing to $myEssid"
sudo iwconfig $myInterface essid $myEssid &>/dev/null
echo "Changing to rate to 11M"       # this isn't always necessary but helps for Broadcom 4318 cards

sudo iwconfig $myInterface rate 11M &>/dev/null     # if your having issue getting connected to a network
echo "acquiring IP"
sudo dhclient $myInterface 
```

keys to the script setting the rate to 11M.

If you get an invalid access point then the key to clearing this up is
```
sudo iwconfig [interface] ap any
```
admittedly this points to a bug in the firmware or driver (i get it on boot if I don't run a config script) 

If this all works then you need to add a pre-up script to your interface in 
```
/etc/network/interfaces
```
add [COLOR="Red"]this line[/COLOR] to your interfaces file:
```


iface eth1 inet dhcp
     [COLOR="Red"]pre-up /path/to/file/network_Startup_script[/COLOR]

```

in  /path/to/file/network_Startup_script my script looks like this:
```

#!/bin/bash
ifconfig eth1 up
if [ `iwlist scan 2> /dev/null | grep [COLOR="Red"]ubc[/COLOR] | wc -l` -ge 1 ]   [COLOR="Red"] # this looks for my usual essid at school and connects to it if it's present, ** change ubc to your usual essid ** [/COLOR]
then
        myEssid=[COLOR="Red"]"ubc"  [/COLOR]
else
        myEssid="any" # finds any open essid and connects to it
fi
        myInterface="eth1"   # typically eth1 but may be something else

iwconfig $myInterface essid $myEssid &>/dev/null
#sudo iwconfig $myInterface ap any &>/dev/null  # uncomment if you have issues with invalid access point issues
# EDIT for kernels < 2.6.15-23 us 11M for newer kernels use 36M
#iwconfig $myInterface rate 11M # &>/dev/null     # necessary part of script for bcm4318 driver and usually bcm4306
iwconfig $myInterface rate 36M # &>/dev/null     # 


```
and that is all you should need to get connected, you may run into issues if you haven't blacklisted your ndiswrapper,  to do black list ndiswrapper run:
```
 echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist 
```
need help? post here I'll monitor and try and help, for more help check the howto's in my signature or view [this forum]("http://ubuntuforums.org/showthread.php?t=114922&page=1")

Cheers

---

### Post by bettermentflux on 2006-04-07
[QUOTE=trubblemaker]k' I can help you get your bcm4318 driver working, I run it and have for 2 months now and have spent 3 months working on helpping people get it running, here's the 123 of how to make it work.

before we go any farther, the native driver for bcm4318 only works at 11Mbs, if that works for you read on

install the deb, 

```
apt-get install bcm43xx-firmware
```

snip[/QUOTE]

I can't wait to try this. Assuming this works, we'll all owe you a debt of gratitude.

I do have one unusual issue that complicates things that someone here may be able to help with: I don't have access to the Internet other than through wireless (router is inaccesible, office isn't wired). Until I get wireless up and running, I've been bouncing back and forth between ubuntu and an XP partitions.

Is there an alternative I can use to *apt-get* where I can download under Windows, reboot and install under Ubuntu? Alternativly, is is possibly availible through the Live CD?

Ditto for the *make *command, which isn't installed by default and is required in order to get ndiswrapper going?

You never realize how dependant you are on Internet access until you don't have it.

Thanks in advance.

---

### Post by trubblemaker on 2006-04-07
yeah I had that issue, here's the fix, download the [deb from Cauego's repository]("http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.0-0ubuntu5_all.deb") onto a cd then you can move it to your computer, move to the folder that contains the file and install it with
```
dpkg install bcm43xx-firmware_1.0-0ubuntu5_all.deb
```
I might also copy the web page, to that cd so you can read the instruction at the same time.  If you are on a dual boot, on the upside you could go the fw-cutter route as the windows driver tells you the exact driver file it's using althought that method is more complicated than using the deb.....
NOTE: the current dapper release does come with everything but the firmware, so you shouldn't need to do anything else but install the firmware with the deb, or bcm-fwcutter.

you could repeat this process for ndiswrapper and make but they may have unmet dependencies, I don't believe their are any dependencies for this .deb but I'm not sure,

---

### Post by bettermentflux on 2006-04-07
After installing the firmware and manually running through the steps within the scripts, I am VERY close. It recognizes the card, finds the access point - the only thing it won't do is grab an IP.

I get *no DHCPOFFERS recieved*

>< this close. Any suggestions?

---

### Post by trubblemaker on 2006-04-07
ok what's the output of 
dmesg
  --> look for bcm43xx related stuff
iwlist eth1 scan
  --> shows the networks you can see and if encryption is on
  --> compare the rates you see here to the rate listed below
iwconfig
  --> shows your current setup
  --> tell me if you are binding to an access point
  --> tel me what your rate is
ifconfig 
  --> tells me if other things might be interfering

make sure you are running the steps in order
1.) iwconfig eth1 rate 11M 
2.) sudo dhclient eth1

---

### Post by massivevoid on 2006-04-07
trubblemaker

On "1.5. Installing ndiswapper", the light for my wireless card didn't came on. I even tried "sudo modprobe ndiswrapper". No luck. 

Also, I checked to see if the wireless card was in "Networking", it isn't. :confused: 

Yesterday I tried a different guide similar to yours and I had everything install correctly. Wireless network card was shown in "Networking"... but when I type in "sudo modprobe ndiswrapper", the light came on for a few seconds and went away.

14e4:4318 (rev 02)

---

### Post by drachir on 2006-04-07
[QUOTE=bettermentflux]I can't wait to try this. Assuming this works, we'll all owe you a debt of gratitude.

I do have one unusual issue .......[/QUOTE]

I am testing Dapper 6.04 on a Compaq Presario 64. Everything works fine except for my Wifi. W/exact same chipset. I am willing to try anything to get it to work. I tried ndiswrapper but to no avail ](*,) . 

I will try bettermentflux example and post what I find.. 

BTW I have a Compaq Presario v2000 ( v2104cl ) W/Turion 64. Ubuntu rocks on my computer. Everything works well except for the Wifi. Good job on Dapper!

---

### Post by trubblemaker on 2006-04-08
[QUOTE=massivevoid]trubblemaker

On "1.5. Installing ndiswapper", the light for my wireless card didn't came on. I even tried "sudo modprobe ndiswrapper". No luck. 

Also, I checked to see if the wireless card was in "Networking", it isn't. :confused: 

Yesterday I tried a different guide similar to yours and I had everything install correctly. Wireless network card was shown in "Networking"... but when I type in "sudo modprobe ndiswrapper", the light came on for a few seconds and went away.

14e4:4318 (rev 02)[/QUOTE]

K if your on dapper you need to balcklist the native driver before ndiswrapper will work, where you using a dapper tutorial you need to run 
```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist 
```
and that should help, other wise if you are using a broadcom I encourage you to follow the directions above for the native driver, also look over the turial in my signature the second one, it's rock solid for dapper ndiswrapper

[QUOTE=drachir]I am testing Dapper 6.04 on a Compaq Presario 64. Everything works fine except for my Wifi. W/exact same chipset. I am willing to try anything to get it to work. I tried ndiswrapper but to no avail ](*,) . 

I will try bettermentflux example and post what I find.. 

BTW I have a Compaq Presario v2000 ( v2104cl ) W/Turion 64. Ubuntu rocks on my computer. Everything works well except for the Wifi. Good job on Dapper![/QUOTE]
UBUNTU KICKS ***, also give one of the tut's in my signature a look for more info.

---

### Post by cdsboy on 2006-04-08
just for the record Linksys WPC54G works great with ndiswapper : P

---

### Post by trubblemaker on 2006-04-08
for the record so does broadcom,

---

### Post by dawg on 2006-04-09
WTF!  ive been reading and reading and reading about my broadcom wireless card trying to soak up everything on getting it to work but to no avail.  I installed the bcm43xx firmware, the wireless light lit up and then nothing.  set the bit rate to "11M" as suggest on this thread and at wiki.  i did an iwlist eth0 scan and bam it found my router.  i did a restart and eth0 scan would bring back no results.  then i decided to change my datarate to 54 and still nothing.  ive changed it back to 11 and i keep getting 54.  my iwconfig eth0 looks something like this.

eth0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
           Mode:Managed Frequency=2.437 Ghz  Access Point:  Invalid
           Bit Rate=54 Mb/s   Tx-Power=19 dBm
           RTS thr:off      Fragment thr:off

the ap any command does nothing i still get the same output.  any suggestions?

---

### Post by trubblemaker on 2006-04-09
sudo iwconfig eth1 ap any  --> works to fix the invalid access point
but setting the essid is a better method of fixing issue try
```

sudo iwconfig eth1 rate 11M
sudo iwconfig eth1 essid any
sudo dhclient eth1

```

---

### Post by dawg on 2006-04-09
i did what you suggested and whenever i restart my datarate reverts to 54g.  i still get an invalid access point and "sudo dhclient eht0" brings back nothing.  i try using sudo iwconfig eth0 scan and the scan brings back no results.

just deactivated eth0 under admin/networking and the wireless light turned off.  did a sudo modprobe bcm43xx and nothing happened.  i could have sworn that would turn it back on.  could it possibly be a conifguration in networking that is conflicting with what i do in terminal?

---

### Post by mjg59 on 2006-04-09
Try upgrading your kernel. In 2.6.15-20 the rate automatically defaults to 11M.

---

### Post by dawg on 2006-04-09
doesn't flight 6 already have that kernel?

---

### Post by plush on 2006-04-09
I used be able to get my broadcom based Apple Extreme card up and running using similar instructions, but now I get:

> master@ubuntu:~$ sudo ifconfig eth0 up
[COLOR="Red"]SIOCSIFFLAGS: Cannot allocate memory[/COLOR]
master@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:<too big>

master@ubuntu:~$


---

### Post by mjg59 on 2006-04-09
[QUOTE=dawg]doesn't flight 6 already have that kernel?[/QUOTE]

No.

---

### Post by dawg on 2006-04-09
i did a fresh reinstall of flight 6 thinking i might have screwed it up by installing other apps like wifi radar and network manager.  i followed the instructions here and installed the firmware deb.  i made the chmod script and that seemed to have worked flawlessly, but my network_Startupscript didn't, i'll have to figure it out.  now my wireless LED is on and here is my out up mario@linbox:~$ iwlist eth0 scan
eth0      No scan results
mario@linbox:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off

sit0      no wireless extensions.


then, if i go to **SYSTEM/ADMINISTRATION/NETWORKING**, eth0 is inactive.  so i ofcourse activate it.  when i do so here's what i get.

mario@linbox:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"gr8"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=54 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off

sit0      no wireless extensions.

i don't know how i was able to get an iwlist scan and find my router the first time, but now, i can't even get that.  right now my router is unsecure set to 11M.  i entered the ESSID and set it to pick up an ip.  any ideas?

---

### Post by trubblemaker on 2006-04-09
k (with your wireless card sounds like yours is eth0) run the script posted on [this page]("http://ubuntuforums.org/showthread.php?t=156328&page=3")

it best if you run the scipt changing the eth1 to eth0 and [ubc] to your essid. the reason for it as a script is the commands need to be run in order after bringing up the interface.  I know the rate gets stuck I don't know why, the network manager does get out of sync sometimes if you use commandline.  I'm sorry I don't know how to tell you the gui instructions as you seem to want to use the gui.... maybe someone will translate for me.

---

### Post by trubblemaker on 2006-04-09
GOOD NEWS there is a report of a bcm4306 driver running at 54Mbs, only down side is it looks like static routing only.  Will post more news as I get details.

---

### Post by dawg on 2006-04-09
yeah, i 've used your script.  i just dont know what i did the last time that i got it to work.  i will continue to work on it.

---

### Post by trubblemaker on 2006-04-09
its a matter of ifconfig eth0 down, ifconfig eth0 up.
don't scan or really do anything before changing the rate. and if you so get the access point --->invalid
```
sudo iwconfig eth1 ap any
``` will fix it.

---

### Post by trubblemaker on 2006-04-09
what is in your /etc/networking/interfaces file?
I noticed the the networking manager is changing the bit rate back to the incorrect bit rate.

Maybe until it gets up and running leave the network manager out of this.  I think it's automotically setting things to setting that don't work for you.

---

### Post by dawg on 2006-04-09
ok, the etc/networking/interfaces is empty.  i know i made it.  simple sudo gedit /etc/networking/interfaces makes it right?  then all i have to do is add what you have with eth0 being my interface and gr8 being my essid.

i do have a /etc/network/interfaces file and i have something like this

#the loopback network interface
auto lo
iface lo inet loopback

#the primary network interface 
iface eth1 inet dhcp
       pre-up /mario/network_Startup_script *****i think it should be /home/mario/network_Startup_script

iface eth0 inet dhcp
wirless-essid gr8

---

### Post by llamakc on 2006-04-09
The file is /etc/network/interfaces, not /etc/networking/interfaces. I have it working for me finally.

```

0000:00:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Belkin: Unknown device 7000
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at dfffe000 (32-bit, non-prefetchable) [size=8K]

```

...using the blacklisting of ndiswrapper, unloading and reloading the bcm43xx module, getting the 1.0-ubuntu5 version of the bcm43xx-firmware deb, and setting the rate to 11M. 

Many thanks to trubblemaker and all of the tips. This post brought to you by 2.6.15-20-k7,  bcm43xx-firmware version 1.0-0ubuntu5, and a few beers.

---

### Post by trubblemaker on 2006-04-09
K you have the startup script on the wrong interface, as your posts show your interface for wireless is eth0 so remove the eth1 entry altogether and move the script so that it's attached to the eth0. (unless you have wired access on eth1 and want it to auto configure at boot.  This will **really slow down **your boot time though so I'd use a startup script or remove it altogether and manually start it when needed.) Also hence for whenever I say interface to you I mean eth0 as that's your wireless nic.

---

### Post by dawg on 2006-04-09
i did as you said and it looks like my startup script isnt working.  now my iwconfig shows my datarate at 1M. i think im going to quit for the night.  thanks for your help

---

### Post by dawg on 2006-04-10
[COLOR="Blue"]**this is what my interfaces looks like  /etc/network/interfaces**[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
     pre-up [ -f /etc/network/local-network-ok ]

iface eth0 inet dhcp
     pre-up /home/mario/network_Startup_script

[COLOR="#0000ff"]**here is what my network startup script looks like its under /home/mario/network_Startup_script **there is a lock on the icon**[/COLOR]

#!/bin/bash
ifconfig eth1 up
if [ `iwlist scan 2> /dev/null | grep gr8 | wc -l` -ge 1 ]    # this looks for my usual essid at school and connects to it if it's present,  change ubc to your usual essid  
then
        myEssid="ubc"  
else
        myEssid="any" # finds any open essid and connects to it
fi
        myInterface="eth0"   # typically eth1 but may be something else

iwconfig $myInterface essid $myEssid &>/dev/null
#sudo iwconfig $myInterface ap any &>/dev/null  # uncomment if you have issues with invalid access point issues
iwconfig $myInterface rate 11M # &>/dev/null     # necessary part of script for bcm4318 driver and usually bcm4306

[COLOR="#0000ff"]**and here is my "wireless" script and this i normally run to get my wireless to run instead of using modprobe bcm43xx**[/COLOR]


#!/bin/bash
if [ "$0" == --help ] 
then
  echo "Listing of ESSID's"
  # Lists the availble ESSIDs
       iwlist  scan | grep ESSID
  echo "Likely interface: "
  # Grabs the name of the interface that succefully scanned
  iwlist scan | grep completed | sed "s/Scan\scompleted\s://g"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  echo "Usage: getit [interface] [essid]  "
  echo "Pick one of the above interface and essid's"
  echo "use the interface that had the essids"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  exit 
fi
if [ -z $2 ] ; then
        myEssid=any
else
        myEssid=$2
fi  

if [ -z $1 ] ; then
        myInterface="eth0"   # typically eth1 but may be something else
else
        myInterface=$0
fi  

echo "Bringing network down"
sudo ifconfig $myInterface down &>/dev/null                 
echo "Bringing network back up"
sudo ifconfig $myInterface up &>/dev/null
echo "Changing to $myEssid"
sudo iwconfig $myInterface essid $myEssid &>/dev/null
echo "Changing to rate to 11M"       # this isn't always necessary but helps for Broadcom 4318 cards

sudo iwconfig $myInterface rate 11M &>/dev/null     # if your having issue getting connected to a network
echo "acquiring IP"
sudo dhclient $myInterface 

so i basically took your scripts and edited them out to match my set up.  everything look alright?

---

### Post by trubblemaker on 2006-04-10
> **dawg][COLOR="Blue"]**this is what my interfaces looks like  /etc/network/interfaces**[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
     pre-up [ -f /etc/network/local-network-ok ]

iface eth0 inet dhcp
     pre-up /home/mario/network_Startup_script

[COLOR="Red"]Great this looks bang on![/COLOR]
[COLOR="#0000ff"]**here is what my network startup script looks like its under /home/mario/network_Startup_script [/COLOR][COLOR="Red"]**there is a lock on the icon**
Lock means read only, maybe checking the permissions on it would be a good idea, you want to make sure that you can execute the script ```
chmod u+x /home/mario/network_Startup_script
```[/COLOR]


#!/bin/bash
ifconfig eth1 up
if [ `iwlist scan 2> /dev/null | grep gr8 | wc -l` -ge 1 ]    # this looks for my usual essid at school and connects to it if it's present,  change ubc to your usual essid  
then
        myEssid=[COLOR="Red"]"ubc"[/COLOR]  _**[B]# should be changed to [COLOR="Red"]gr8[/COLOR] maybe? as that is the essid your searching for above**[/B]_
else
        myEssid="any" # finds any open essid and connects to it
fi
        myInterface="eth0"   # typically eth1 but may be something else

iwconfig $myInterface essid $myEssid &>/dev/null
#sudo iwconfig $myInterface ap any &>/dev/null  # uncomment if you have issues with invalid access point issues
iwconfig $myInterface rate 11M # &>/dev/null     # necessary part of script for bcm4318 driver and usually bcm4306

[COLOR="#0000ff"]**and here is my "wireless" script and this i normally run to get my wireless to run instead of using modprobe bcm43xx**[/COLOR]


#!/bin/bash
if [ "$0" == --help ] 
then
  echo "Listing of ESSID's"
  # Lists the availble ESSIDs
       iwlist  scan | grep ESSID
  echo "Likely interface: "
  # Grabs the name of the interface that succefully scanned
  iwlist scan | grep completed | sed "s/Scan\scompleted\s://g"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  echo "Usage: getit [interface] [essid]  "
  echo "Pick one of the above interface and essid's"
  echo "use the interface that had the essids"
  echo "+++++++++++++++++++++++++++++++++++++++++++++++  "
  exit 
fi
if [ -z $2 ]  said:**
> # could be changed to gr8 for faster connection
                                                       # but you would lose the flexibility of the script i.e. using the samescript at an internet cafe for an ip
 [/COLOR]
else
        myEssid=$2
fi  

if [ -z $1 ] ; then
        myInterface="eth0"   # typically eth1 but may be something else
else
        myInterface=$0
fi  

echo "Bringing network down"
sudo ifconfig $myInterface down &>/dev/null                 
echo "Bringing network back up"
sudo ifconfig $myInterface up &>/dev/null
echo "Changing to $myEssid"
sudo iwconfig $myInterface essid $myEssid &>/dev/null
echo "Changing to rate to 11M"       # this isn't always necessary but helps for Broadcom 4318 cards

sudo iwconfig $myInterface rate 11M &>/dev/null     # if your having issue getting connected to a network
echo "acquiring IP"
sudo dhclient $myInterface 

so i basically took your scripts and edited them out to match my set up.  everything look alright?
well I think I highlighted the area's that are creating the issue try it out and let me know

---

### Post by dawg on 2006-04-10
well i had to redo the chmod command again, i had used sudo chmod which had caused that.  anyways, i also made the changes that you told me too, and nothing, its not working.  oh well, thats to bad, guess i will just cable my laptop to my router.  thanks a lot for your help.

---

### Post by bettermentflux on 2006-04-10
After using your suggestions I can get eveything to look the way it should until I try to grab an IP address. Details:

Wireless light is on at boot

checked var/log/dmesg and /var/log/messages. BCM43xx seems to load without problems and the only vaugly relevant-sounding error that I can find is: iftab_helper[3108]: segfault at 0000000000000000 rip 00002aaaaae85fc0 rsp 00007ffffff55848 error 4

ndiswrapper is not installed

*lsmod|grep -i bcm* results in

bcm43xx               1171320
ieee80211softmac   313601 
bcm43xxieee80211  375762 bcm43xx,ieee80211softmac

After changing the bit rate to 11M it DOES find the ESSID and Access Point.
*iwconfig* gives me

lo        no wireless extensions.
eth1    no wireless extensions.
sit0     no wireless extensions.
eth0     IEEE 802.11b/g  ESSID:"default"  Nickname:"Broadcom 4318" Mode:Managed  Frequency=2.412 GHz  Access Point: 00:13:46:0A:5B:32  Bit Rate=11 Mb/s  Tx-Power=18 dBm  RTS thr:off  Fragment thr:off Encryption key:off

*iwlist scan* then gives me this:

lo        Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
sit0      Interface doesn't support scanning.
eth0      Scan completed : 
Cell 01 - Address: 00:13:46:0A:5B:32
ESSID:"default"  Protocol:IEEE 802.11bg
Mode:Master  Channel:1  Encryption 
key:off  Bit Rates:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
Quality=100/100
Signal level=-79 dBm
Extra: Last beacon: 77ms ago

Everything looks good so I run *dhclient *and crossed my fingers but get:

Listening on LPF/eth0/00:14:a5:27:23:f3
Sending on   LPF/eth0/00:14:a5:27:23:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The only other thing I could think of was to explicitly state that the key was open with *sudo iwconfig eth0 key open* 

iwconfig now gave me this:

eth0  IEEE 802.11b/g  ESSID:"default"  Nickname:"Broadcom 4318"
  Mode:Managed  Frequency=2.484 GHz  Access Point: 00:13:46:0A:5B:32  Bit Rate=11 Mb/s  Tx-Power=18 dBm  RTS thr:off  Fragment  thr:off  Encryption key:0000-0000-0000-0000-0000-0000-00  Security mode:open

A re-run of dhclient gave me the same results as before. Just in case, I changed the mode from Managed to "auto" with the same results.

I double-checked the router settings and everything looks good there. Channels and ESSID are fine, DHCP and broadcast are on.

Everything looks good, so I'm not sure why I'm unable to grab an ip address. So very close.

---

### Post by bettermentflux on 2006-04-10
One thing that occured to is that I'm using ubuntu for AMD64. Not sure if that means anything in terms of drivers.

---

### Post by trubblemaker on 2006-04-11
anything in your **dmesg after attempting to get an ip**? Does your iwconfig change after scanning?
can you assign an ip in your routers rang and ping the router?
sounds like your down with your router but mine gives me headaches, always makes me click twice to save something,** make sure it's broadcasting it's essid **and not just default, it **won't pickup an ip if it's not broadcasting the essid.**
looks like everything is rocking, and ready to go
managed is fine, I don't think messing with the key is helpful, but can't rule it out

---

### Post by bettermentflux on 2006-04-11
[QUOTE=trubblemaker]anything in your **dmesg after attempting to get an ip**? [/QUOTE]
No errors

[QUOTE=trubblemaker]Does your iwconfig change after scanning?[/QUOTE]
Yes, it finds the access point correctly after a scan.

[QUOTE=trubblemaker]can you assign an ip in your routers rang and ping the router?[/QUOTE]
Have to get back to you on that.

[QUOTE=trubblemaker]** make sure it's broadcasting it's essid **and not just default, it **won't pickup an ip if it's not broadcasting the essid.**
[/QUOTE]
Checked and double-checked.

I was just going through this ([http://www.ubuntuforums.org/archive/index.php/t-25683.html]("http://www.ubuntuforums.org/archive/index.php/t-25683.html")) lengthy list of problems and came across others with a similiar "everything looks kosher but I get a **No DHCPOFFERS received ** message".

I'm looking over it again, but it appears that everyone with that particular problem either bought a new card or gave up and disappeared without a solution.

But I'll track through that forum again to see if I can glean (sp?) a solution.

btw, Thanks again for all the help. It's very much appreciated.

---

### Post by bettermentflux on 2006-04-11
Two of the users on [this page]("http://www.ubuntuforums.org/archive/index.php/t-25683.html") with the same **no DHCPOFFERS** message did, in fact, fix it by removing WEP/WPA and explicity setting wireless_keymode to "open". But ours is already set to open and to quote one of my previous posts:

> The only other thing I could think of was to explicitly state that the key was open with *sudo iwconfig eth0 key open*

iwconfig now gave me this:

eth0 IEEE 802.11b/g ESSID:"default" Nickname:"Broadcom 4318"
Mode:Managed Frequency=2.484 GHz Access Point: 00:13:46:0A:5B:32 Bit Rate=11 Mb/s Tx-Power=18 dBm RTS thr:off Fragment thr:off **Encryption key:0000-0000-0000-0000-0000-0000-00 Security mode:open**

A re-run of dhclient gave me the same results as before. Just in case, I changed the mode from Managed to "auto" with the same results.

Is that any different from the wireless_keymode that worked for user akb, or (crosing fingers) is there an untried setting I can try?

---

### Post by trubblemaker on 2006-04-11
I learned alot from that forum but it's not all the same as that anymore, if you want to get on ndiswrapper, no worries [Here's another thread I worked on for helping people]("http://ubuntuforums.org/showthread.php?t=114922") might have something I forgot, here's a [bug with a solution for 4306 driver that works reportedly at 54Mbs, but uses a static ip]("https://launchpad.net/malone/bugs/36525"). I haven't confirmed it yet myself so I'm hesitant to spread the word about it. and it may have been achieved with cutting of firmware and not the deb package that most people are now using

this points to a possible issue with attaining an ip but not, with datatransfer, 

you know when all else fails, 

```

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 rate 11M
sudo iwconfig eth1 essid any
sudo iwconfig eth1 ap any
sudo dhclient eth1

```

---

### Post by trubblemaker on 2006-04-11
don't know about key settings, I run unencrypted at both locations I use but haven't had issues with people that got it working and then moved to adding the in key, actually look through some of the previous posts in the link  posted above I think I recently got someone working on 4306 with wep but I dont' know the specific trick that worked maybe if you post their he will tell you.

---

### Post by trubblemaker on 2006-04-11
you know change the name of the essid for me change it to anything else, like troubblemaker or bettermentflux and then explicitly change to that essid. as 

```
 sudo iwconfig eth1 essid any 
```  can screw up and it certainly wouldn't hurt.

---

### Post by bettermentflux on 2006-04-11
Thanks again. Now that I have it up to the point where it recognizes the card and the access point, I can narrow down my search for a solution to the no DCHPOFFERS problem. Just did a search on these forums and came up with 253 hits. One of those has to be a solution, right? Right?

---

### Post by trubblemaker on 2006-04-11
NO don't do that, aaaaahhhh 
searching the forum?
who heard of such things, 
bettermentflux you have finally lost it.

but seroiusly, your on cutting edge my friend always take all you read with a grain of salt as the new driver's make for a different situation

---

### Post by dspring on 2006-05-25
OK, Hey, got it up to the point the light came on. Then I screwed up the eth1 now it doesn't show up in the networking interface. Got any idea how to get it back? I looked at the install driver function and it still shows driver and hardware present so ...all must not be lost? Right?

David

---

### Post by trubblemaker on 2006-05-26
k show me some output, please tell me the output from
```
/etc/modprobe.d/blacklist
ifconfig 
iwconfig 
iwlist scan

```
some this will help me get a hold of where your at, also what method did you follow to get _here_ did you follow one of the howto's?

---

### Post by dspring on 2006-05-26
Hey, this should work with the 4306 too right?
I have everything ready, blacklisted ndiswrapper, driver and firmware installed.
Questions before going further, on WEP number if it is 10 digits is is ASCI or Hexdecimal? And if one wanted to unblacklist ndiswrapper how would you reverse this just so I know the steps? Thanks for helping us newbie's. 

David

---

### Post by trubblemaker on 2006-05-26
[QUOTE=dspring]Hey, this should work with the 4306 too right?[/quote]
yep any bcm43xx
[QUOTE=dspring]
I have everything ready, blacklisted ndiswrapper, driver and firmware installed.
[/QUOTE]
and you didn't blacklist bcm43xx?
[QUOTE=dspring]
Questions before going further, on WEP number if it is 10 digits is is ASCI or Hexdecimal? 
[/QUOTE]
to be honest, **no wep until you get it working only once it's working unencrypted. **I will help you with wep after it's working unencrypted as per k.i.s.s. principle
[QUOTE=dspring]
And if one wanted to unblacklist ndiswrapper how would you reverse this just so I know the steps? [/QUOTE]
ok so that'd be undoing what you did to black list it.  if you just used the commmands from a howto, I understand why you don't know how to do that. so what the commands did was add ndiswrapper to the blacklisted drivers, it literally added 
```
blacklist ndiswrapper 
```
to a file, which one you ask? don't remember, I always look it up, I just look at what file that is used in howto to blacklist, then open that file in your favorite superuser editor and remove the text
```
blacklist ndiswrapper 
```, 

not to be a stickler but you never answered my previous post, so I can help you more when you do that.

---

### Post by clooch on 2006-05-31
I would like to thank all of you for your helpful advice. I had been trying in vain to have my bcm43xx  to play nice.  

again many thanks for all the helpful threads.

---

### Post by Similar on 2006-06-17
am i the only person alive that can't install the 43xx firmware??

I've been trying it through repo's AND with the deb file, but still doesn't work :(

---

### Post by BlackOcellaris on 2006-06-18
[QUOTE=n0ah420]I have the same chipset on a similiar HP laptop.  Save yourself some stress and use ndiswrapper.  Although it is possible to get the kernel driver running its a pain in the arse.  Also it exhibited some very strange behavior on my machine.  Now ndiswrapper is also not working like it should, but it is working and I am writing this email over a secure wireless connection.  Check out the following links for all the information you need to get your wireless running with ndiswrapper or built-in kernel driver:

[https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver)

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)[/QUOTE]


Thank you so very much :)  That second link worked for me.  I failed the first time I installed Dapper and just gave up and went back to Breezy.  I'm glad I caught your post, it fixed my problem~^^=D> =D>

---

### Post by ethanbrown on 2006-08-28
I also have a Broadcom, and have it working using ndiswrapper.  However, I had to build the newest version of ndiswrapper which is 1.23 and is available at [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) .

You'll want to remove the ubuntu version before building from source.  Be sure to install the build-essential package and linux-headers before building.

Also, check out [http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

Good luck! 

--Ethan

---

