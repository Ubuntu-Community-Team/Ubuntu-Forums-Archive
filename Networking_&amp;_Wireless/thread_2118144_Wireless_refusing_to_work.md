---
title: "Wireless refusing to work"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by Utterlybewildered on 2013-02-20
Hello, first post here, but it's all problems that need some resolving.

I downloaded Ubuntu 10.04 onto my Dell laptop 32bit, it runs ok, and I downloaded version 10.04 because initially attempting to install and use version 12.04 wasn't allowing any wireless connection to the internet so reverted to the older version 10.04.  This worked well for a while until ubuntu decided to update itself when I went to make a cuppa and when I returned 5 minutes later version 12.04 of Ubuntu had appeared and been automatically installed.  Now wireless will not work again, and even ethernet will not work.  So I'm on windows 7 until this is fixed.

Firstly I would love to know why there is no wireless available.

When looking further into the wireless issue I checked the driver for wireless and it has been discovered that on my laptop Broadcom STA proprietary Wireless Driver needs to be activated (for Ubuntu only as with Windows all is working fine) but the activate button was blanked over and could not be clicked on.

Is this Broadcom info relevant? 

Thirdly, I like Ubuntu, it's quick and quite simple to use, but as a reaction to these difficulties experienced and investigated into when trying Ubuntu, why is it so hard to try and be using Ubunto online? From my searching this is an ongoing trouble with Ubuntu.

Lastly, I'm not expert and do not understand all the technical talk, please can any replies be as though you're talking to a 5-year old please or my brain hurts! :redface:

---

### Post by mozgren on 2013-02-24
> **Utterlybewildered said:**
> Hello, first post here, but it's all problems that need some resolving.

I downloaded Ubuntu 10.04 onto my Dell laptop 32bit, it runs ok, and I downloaded version 10.04 because initially attempting to install and use version 12.04 wasn't allowing any wireless connection to the internet so reverted to the older version 10.04.  This worked well for a while until ubuntu decided to update itself when I went to make a cuppa and when I returned 5 minutes later version 12.04 of Ubuntu had appeared and been automatically installed.  Now wireless will not work again, and even ethernet will not work.  So I'm on windows 7 until this is fixed.

Firstly I would love to know why there is no wireless available.

When looking further into the wireless issue I checked the driver for wireless and it has been discovered that on my laptop Broadcom STA proprietary Wireless Driver needs to be activated (for Ubuntu only as with Windows all is working fine) but the activate button was blanked over and could not be clicked on.

Is this Broadcom info relevant? 

Thirdly, I like Ubuntu, it's quick and quite simple to use, but as a reaction to these difficulties experienced and investigated into when trying Ubuntu, why is it so hard to try and be using Ubunto online? From my searching this is an ongoing trouble with Ubuntu.

Lastly, I'm not expert and do not understand all the technical talk, please can any replies be as though you're talking to a 5-year old please or my brain hurts! :redface:

I loaded Ubuntu 12.10 dualboot with windows 7 on my dad's old Dell Inspirion laptop.  The printer works now, with CUPS, but have to go to Windows to surf the net.   Sad to say he doesn't want the wired connection, has given up with Ubuntu and only boots it when I'm there and can point him to his MsWord docs for printing.

---

### Post by Utterlybewildered on 2013-03-04
> **mozgren said:**
> I loaded Ubuntu 12.10 dualboot with windows 7 on my dad's old Dell Inspirion laptop.  The printer works now, with CUPS, but have to go to Windows to surf the net.   Sad to say he doesn't want the wired connection, has given up with Ubuntu and only boots it when I'm there and can point him to his MsWord docs for printing.

Thanks for your reply mozgren, yes it's getting to the stage that there's little point in continuing with ubuntu if it's so faulty and no signs of it's repair or even how to fix it. Sad really because ubuntu in use for the main is good and fast, but if there's basics that aren't working why bother.  Surprising nobody has come up with an answer.

So far because of the situation here ubuntu has now been uninstalled, in the last ditch hope that reinstallation might clear the slate and a new installation sort things out, and the earlier version 10.04.4 is now installed, which in itself is different to look at than version 10.04 although that isn't a problem just unexpected how much change that is so easy enough got used to.  But, STILL no wifi! Wired ethernet connection does work, with apps installed to do it.  But why of WHY no wifi??????? 

Total mystery, with with nobody able to come up with an answer can see a lot of people going elsewhere where wifi is important.  Come on ubuntu get it together!!!

---

### Post by varunendra on 2013-03-04
> **Utterlybewildered said:**
> 
Total mystery, with with nobody able to come up with an answer can see a lot of people going elsewhere where wifi is important.  Come on ubuntu get it together!!!

Utterlybewildered,

Certain parts of these forums have so high number of new threads that it is usual for threads to go out of the first page or even out of a search result after a few hours. If that happens with one of your threads without answers or 'useful' answers, feel free to bump it after 24 hours.

Now regarding the original issue, I may *try* to help if you could post output of -
```
lspci -nnk | grep -iA2 net
```
Enter the above command in a terminal and post back its output here. You may just copy-paste it in the terminal (with your mouse) to avoid typing errors.

---

### Post by mörgæs on 2013-03-05
If you still care for a solution I have moved the post to a forum where it's more likely to attract answers.

---

### Post by Utterlybewildered on 2013-03-06
> **varunendra said:**
> Utterlybewildered,

Certain parts of these forums have so high number of new threads that it is usual for threads to go out of the first page or even out of a search result after a few hours. If that happens with one of your threads without answers or 'useful' answers, feel free to bump it after 24 hours.

Now regarding the original issue, I may *try* to help if you could post output of -
```
lspci -nnk | grep -iA2 net
```
Enter the above command in a terminal and post back its output here. You may just copy-paste it in the terminal (with your mouse) to avoid typing errors.

Will indeed bump, thanks O:)

I'll go and try it in a while and post back later today

---

### Post by Utterlybewildered on 2013-03-06
> **mörgæs said:**
> If you still care for a solution I have moved the post to a forum where it's more likely to attract answers.

Thanks for that, wasn't really sure where to post so took my best guess :)

---

### Post by mörgæs on 2013-03-06
Another (low-tech) idea is to begin with a fresh install of 12.10. Since you have been struggling with this for a week I believe a reset is worth trying. 10.04 has less than two months life time left anyway, so no point in troubleshooting.

---

### Post by kurt18947 on 2013-03-06
I believe Broadcom activation requires a wired connection.  I've been successful avoiding Broadcom devices so far so no experience.   If your wired connection isn't working either, oh boy.  I suspect you're a candidate for a 'buy something known to work out of the box' solution.  I have a couple adapters that work 'out of the box' for me.  Trendnet TEW-649UB and Netgear WNA1100.  You have to be careful with Netgear, a lot of their USB WiFi adapters DON'T work out of the box - some seem like a real PITA but the WNA1100 has been okay.  I also have a Trendnet TEW424UB v3.x which is big and ugly and slow but has been plug 'n' play since Ubuntu 9.10 I think.   There was a version 2.x which looks the same but was not plug 'n' play.  I've used the slow Trendnet when I needed an internet connection to download drivers for a faster adapter or other hardware.

---

### Post by varunendra on 2013-03-06
> **kurt18947 said:**
> I believe Broadcom activation requires a wired connection.  I've been successful avoiding Broadcom devices so far so no experience.   If your wired connection isn't working either, oh boy..
Actually, most often it is as easy as downloading the [linux-firmware-nonfree]("http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download") package on another computer > copy it to the Ubuntu machine > double-click to install it > Done! :)

The one I linked above is for precise (12.04), one may have to change the version according to his/hers.

---

### Post by Utterlybewildered on 2013-03-06
> **varunendra said:**
> Utterlybewildered,

Certain parts of these forums have so high number of new threads that it is usual for threads to go out of the first page or even out of a search result after a few hours. If that happens with one of your threads without answers or 'useful' answers, feel free to bump it after 24 hours.

Now regarding the original issue, I may *try* to help if you could post output of -
```
lspci -nnk | grep -iA2 net
```
Enter the above command in a terminal and post back its output here. You may just copy-paste it in the terminal (with your mouse) to avoid typing errors.

Hi, thank you here is the result from the terminal :)

welshybabe@ubuntu:~$ lspci - nnk / grep -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file

---

### Post by Utterlybewildered on 2013-03-06
> **mörgæs said:**
> Another (low-tech) idea is to begin with a fresh install of 12.10. Since you have been struggling with this for a week I believe a reset is worth trying. 10.04 has less than two months life time left anyway, so no point in troubleshooting.

Thanks, just not really sure of the benefit if there's no internet connection at all with version 12.10

---

### Post by varunendra on 2013-03-06
> **Utterlybewildered said:**
> Hi, thank you here is the result from the terminal :)

welshybabe@ubuntu:~$ **lspci - nnk [COLOR="#FF0000"]/[/COLOR] grep -iA2 net**
Usage: lspci [<switches>]
...blah-blah-blah...
Oops!! A tiny mistake you made there..

The symbol before 'grep' is NOT forward slash (/). It is 'Pipe' symbol (**|**) which is located above 'Enter' key on my US-104 type keyboard, on the same key that types backslash (\). With shift, it will type the pipe symbol that is in the command.

Just copy-paste using your mouse if that confuses you :)

---

### Post by mörgæs on 2013-03-06
> **Utterlybewildered said:**
> Thanks, just not really sure of the benefit if there's no internet connection at all with version 12.10

It's very unlikely that the wired connection does not work. You can try in a live boot.

---

### Post by Utterlybewildered on 2013-03-06
> **varunendra said:**
> Actually, most often it is as easy as downloading the [linux-firmware-nonfree]("http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download") package on another computer > copy it to the Ubuntu machine > double-click to install it > Done! :)

The one I linked above is for precise (12.04), one may have to change the version according to his/hers.


Thanks, have tried the link but it didn't work, the wireless did SAY it was connected but the internet still didn't work from it being installed, although I suspect it was because it was for 12.04 which isn't currently being run. I attempted a look around the website where that link is to but had no idea what I was looking at there, is there a version for 10.04.4 at all?

---

### Post by Utterlybewildered on 2013-03-06
> **Utterlybewildered said:**
> Thanks, have tried the link but it didn't work, the wireless did SAY it was connected but the internet still didn't work from it being installed, although I suspect it was because it was for 12.04 which isn't currently being run. I attempted a look around the website where that link is to but had no idea what I was looking at there, is there a version for 10.04.4 at all?


Here is the Terminal result using the correct symbol, sorry :)

Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
welshybabe@ubuntu:~$

---

### Post by Utterlybewildered on 2013-03-06
> **mörgæs said:**
> It's very unlikely that the wired connection does not work. You can try in a live boot.

The wired connection did indeed not work with 12.04 which is why the reversion to 10.04.4, but I've no idea what a live boot is and how it's different from just booting up from pushing the laptop on button?

---

### Post by mörgæs on 2013-03-07
You only observations is that it did not work in an *upgraded* 12.04. You have not tried a live boot, which is Buntu running from a CD of USB stick.

---

### Post by varunendra on 2013-03-07
> **Utterlybewildered said:**
> Here is the Terminal result using the correct symbol, sorry :)

Usage: lspci [<switches>]

Unfortunately, this one again is a wrong usage. Like I said, just copy-paste the following (copy-paste it to a text file, take it to the ubuntu machine, copy-paste again in a terminal) -
```
lspci -nnk | grep -iA2 net
```

The output should be something like -
```
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e048]
	Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
	Kernel driver in use: atl1c

```

---

