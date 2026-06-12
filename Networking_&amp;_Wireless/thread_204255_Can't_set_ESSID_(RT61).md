---
title: "Can't set ESSID (RT61)"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by neilc on 2006-06-26
Hi All,

I've searched the forum and been googling for hours, but I'm just not having any joy with this. 

I can do a scan and it finds my network. I can see that the problem is my ESSID isn't set, but I can't set the ESSID no matter what I try.

Below is some output.

Any help *really* appreciated with this one. I'm a Linux newbie, so simple explanations and small words would help ;) 

TIA, Neil

```

root@neil-desktop:/etc# iwlist ra0 scan

ra0	scan completed
	cell 01 - Address 00:0C:F6:19:FF:F9
	Mode: Managed
	ESSID: "Sitecom"
	Encryption key: off
	Channel: 11

root@neil-desktop:/etc# iwconfig

lo	no wireless extensions

eth0	no wireless extensions

ra0	RT61 Wireless ESSID:""
	Mode: Auto Frequency:11 Mhz Bitrate: 54mb/s
	RTS thr: off Fragment thr: off
	Encryption key: off
	Link Quality=0/70 Signal Level:-121dBM Noise level:-111 dBm
	Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0	no wireless extensions

root@neil-desktop:/etc# iwconfig ra0 essid Sitecom
root@neil-desktop:/etc# iwconfig

lo	no wireless extensions

eth0	no wireless extensions

ra0	RT61 Wireless ESSID:""
	Mode: Auto Frequency:11 Mhz Bitrate: 54mb/s
	RTS thr: off Fragment thr: off
	Encryption key: off
	Link Quality=0/70 Signal Level:-121dBM Noise level:-111 dBm
	Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0	no wireless extensions

```

---

### Post by tonyr on 2006-06-26
Under System->Administration->Networking->Wireless Connection->Properties, what
does it say? Anything?  Is the interface name there and correct?  Is it Enabled?
Is the Network Name(ESSID) field empty?

---

### Post by neilc on 2006-06-26
Its not enabled and all entries are blank. This is deliberate...

If I set *anything* using the gui or modify /etc/network/interfaces the whole system crashes and then locks up on reboot.

This is a known problem (took me 4 or 5 re-installs to find that out, mind!) 

Since finding it, I've been following [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

But it doesn't say anything about setting the ESSID.

I've obviously googled this, and I found something that said you need to set the key before iwconfig will let you change the ESSID, but setting

iwconfig ra0 key open

doesn't seem to have any effect ](*,)

---

### Post by tonyr on 2006-06-26
The brute force way is to edit **/etc/network/interfaces**, find the section for your
device, and add the line
```

wireless-essid <your-ssid>

```

In mine the section looks like this (ra0 is the device for RT2500 chipset):
```

auto ra0
iface ra0 inet dhcp
wireless-essid <my-ssid>

```

You may not need to have the **dhcp** line if you are not using **dhcp** for
address assignment.

---

### Post by neilc on 2006-06-26
As I said, any attempt to do this in /etc/network/interfaces results in an unrecoverable crash on bootup :(

---

### Post by tonyr on 2006-06-26
Did you read [this]("http://www.ubuntuforums.org/showthread.php?t=132980") thread in your searches?

---

### Post by neilc on 2006-06-26
Yes, as I said two posts back, that is the guide that I have been following. ](*,) 

Thanks for trying to help tho.

---

### Post by tonyr on 2006-06-26
OK OK so I can't read.

This is a known bug, reported at malone:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35474]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35474")
There are some workarounds suggested in the comments, but no real solution until a new driver is
available, from what I saw.

If you got to [https://launchpad.net/distros/ubuntu/+bugs]("https://launchpad.net/distros/ubuntu/+bugs")
and enter **rt61** in the search box, you'll see about 5 bug reports.  I only looked at one of them.

---

### Post by neilc on 2006-06-27
Thanks TonyR. Wasn't getting at you - I do appreciate the help. I'm just very, very frustrated trying to get this working.

Originally I was using Fedora Core 4, tried everything to get the rt2x00 drivers working in it (including recompiling the kernel more times than I can count), then tried upgrading to Fedora Core 5 (with the same lack of success). Moved to Ubuntu and was thrilled when it automatically detected the card - really thought I was close to getting it all working. Have since re-installed Ubuntu 5 or 6 times, and spent *hours* playing with configs, all to no avail.

Its just a hobby, but man is it frustrating at times!

---

### Post by tonyr on 2006-06-27
I hear you.  I'm trying to help someone else with an external usb drive mounting
problem that defies solution, no forum references, no google references, no nuthin'.

Good luck.

---

### Post by salanet on 2006-07-07
I've the same problem.... It seems that can't read the configuration file...

---

### Post by tonyr on 2006-07-07
> **salanet said:**
> I've the same problem.... It seems that can't read the configuration file...

Which file?

---

### Post by Barrakketh on 2006-07-07
In my experience, configuring the RT61 via the interfaces file is an excercise in futility.

This is how I got mine working.  Download the drivers from [Ralink's site](http://www.ralinktech.com/supp-1.htm).  Currently, the direct link to the most recent drivers is [here](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz).

Unpack the archive.  Enter the Module directory.  Copy the *.bin files (contains the card's firmware) and rt61sta.dat to /etc/Wireless/RT61STA/

Open rt61sta.dat with "vim -b" (I think gedit will work, but I used vim).  Instructions on configuring this file can be found in the readme contained within the Module directory.  Here's what you should need to get the card running (note: this is from memory, and a couple of these could be the default).  I'll be adding some inline comments after a # mark, but these aren't in the file, just added to make things easier to read).

```
SSID=000D0B04EDDA  #sets ESSID, self-explanatory
NetworkType=Infra  #Infrastructure/managed mode.
WirelessMode=0     #0 is for mixed b/g networks.  3 is for a/b/g.  1, 2, and 4 are for B, A, and G only, respectively.
Channel=0          #0 is for autoselecting the channel
AuthMode=WPAPSK    #Self explanatory, I'm using WPA-PSK.  Other options include OPEN, WPA2PSK, WPANONE (for Adhoc), WPA, and WPA2.
EncrypType=AES     #^ with AES :)  Other options are NONE, TKIP, and WEP.
WPAPSK=foobar      #Enter your key here
```

Good luck.  One thing I'll mention about the chipset/driver is that sometimes if my router is rebooted before I bring the interface down it'll sometimes lock the system on restarting the networking script.  The RT2x00 project is going to be adding support for the RT61 chipset into their driver, so when the rewrite is complete we'll hopefully have a more stable driver.  For now, I can say I've been happy with the stability of the driver aside from the situation I mentioned.

---

### Post by donnysrx on 2006-07-07
> **Barrakketh said:**
> In my experience, configuring the RT61 via the interfaces file is an excercise in futility.

yeah I found the same, its the networking gui that causes the crashing( do all your editing and setup work using a text editer). I had a go at getting rt61 driver going a couple of weeks ago and got very close( had flashing LEDs on the card and everything, just couldnt quite get it to communicate though). the wireless card i've got is a edimax which needs the rt61 driver, OH noticed earlier today there has been a new driver release the other week

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

I tried these drivers too but wasnt successful;) .

Anyway getting ready to have another go, thats why i found this thread.

Well good luck, and keep any from that networking gui, it doesnt like this chip set

---

### Post by Barrakketh on 2006-07-07
> **donnysrx said:**
> I had a go at getting rt61 driver going a couple of weeks ago and got very close( had flashing LEDs on the card and everything, just couldnt quite get it to communicate though). the wireless card i've got is a edimax which needs the rt61 driver
The guide I wrote above might work.  Initially I compiled the RT61 driver from Ralink's web site, which was something of a pain (a typo in the script, and needing to change the type of linebreaks used, among other things that needed fixing).

I had only installed it into one directory for one of my kernels...normally a kernel update would require me to rebuild the driver.  Then I noticed that the card still worked after a reboot.  After running updatedb then using locate to find the driver (rt61.ko) I noticed that the driver was installed for each kernel, and dpkg was able to find the driver in the kernel packages.

Running strings on the driver can show you what files it requires...I'm not sure why there isn't a package in the repository for these.  Anyway, here's what you'll see:
```
$ strings /lib/modules/2.6.15-25-k7/kernel/drivers/net/wireless/rt2600/rt61.ko | egrep -i '/etc/Wireless/RT61STA'
/etc/Wireless/RT61STA/rt2561.bin
/etc/Wireless/RT61STA/rt2561s.bin
/etc/Wireless/RT61STA/rt2661.bin
/etc/Wireless/RT61STA/rt61sta.dat
```

So, it seems that you only need the *.bin and rt61sta.dat file copied to the right place (and configured).  Those (included with Ralink's open source driver...the one that was tricky to get compiled) are available from their site.

I managed to get my adapter working, which is a Linksys WMP54G v4.

---

