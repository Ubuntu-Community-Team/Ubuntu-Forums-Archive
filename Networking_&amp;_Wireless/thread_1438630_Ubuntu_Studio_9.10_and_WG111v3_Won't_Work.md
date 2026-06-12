---
title: "Ubuntu Studio 9.10 and WG111v3 Won't Work"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by dert on 2010-03-25
Hi folks!  I'm a total NOOB and I just finished a dual boot Ubunutu Studio 9.10 64bit/Windows 7 x64 install on a brand new i7 PC using a WD10EARS hard drive (with the new Advanced Format) and I gave myself top marks for getting by the mammoth amount of obstacles to accomplish what I have so far.

Item of note:  you can NOT do a complete install with Ubuntu Studio 9.10 using a wireless device.  The installer ONLY recognizes motherboard ethernet ports.  No worries, I moved it to the office and the LAN line and got a complete install.  I am using this in my living room though as a Media PC with MythTV and the distance requires me to use WIRELESS.

After a successful install, I was unable to get my brand new, out of box Netgear WG111v3 to establish a successful connection and I need your help.  Pardon the length of this post, I will try to organize it as best as I can but I have done a LOT of troubleshooting before posting here.  Here's what I did so far:

1.  Tested Wireless in Win7 on same PC.  Works GREAT!  Rebooted, went into Ubuntu Studio 9.10 and got no joy.
2.  [This page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB") says the WG111v3 works out of box with Karmic and I can state with 100% certainty it does NOT.
3.  Went to [this page]("http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x") (which is THE best how to out there) and followed instructions.  I discovered a bug in wpa_passphrase immediately.  I use a very complex passphrase using !#$&@ characters in the mix.  wpa_passphrase dies with various errors when it sees these characters because it thinks they're command items rather than part of the text in my key.  Try it yourself.  Create any long text string with those characters and input it to wpa_passphrase.  It dies.  Works fine with regular letters/numbers.  I had to use [this page]("http://www.xs4all.nl/~rjoris/wpapsk.html") to get the HEX value for my passphrase so I could complete my interfaces file.  On a hunch, I changed my passphrase on the router to be a simple 10 letter word all in lower case.  wpa_passphrase changed that to HEX fine, updated interfaces file, rebooted router and PC and got nothing.  So it's NOT the passphrase.
4.  Went to [this page]("http://ubuntuforums.org/showthread.php?t=732827"), which again states it works out of box but doesn't and tried all the help there.  NO JOY.
5.  Tried [here]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") too.  The help there is good when combined with #2 above but still nothing.
6.  Went to [unsupported versions of Ubuntu]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111") to try some old school tricks.  Got nothing.
7.  Found [this site]("http://ubuntuforums.org/showthread.php?t=1170354") and it has EXACTLY my problem!  I always end up with "No working leases in persistent database - sleeping." when it tries to get an IP address from the router.  As you can see, that user found no fix either.
8.  I turned off ALL security on the router and left it wide open, updated my interfaces file appropriately, rebooted everything and it still couldn't connect?

So I'm at my wits end and I really hope you guys can help me.  My error is "No working leases in persistent database - sleeping.".  I've performed all the troubleshooting above.  The adapter works fine in Win7 on the same computer.  Please help.  This is a brand new install and I have lots of time coming up so I'm 100% willing to start from square 1 and follow any instructions you have step by step.  I know we can fix this!

---

### Post by chili555 on 2010-03-25
Where are all these settings? In */etc/network/interfaces*? Is Network Manager still installed? I, and many others, have tried to write our own configurations and overpower NM and utterly failed. In my experience, it's manual or NM, but not both.

My network uses WPA2-PSK and both NM and Wicd connect immediately. I feel fairly confident that I could **remove** them and write */etc/network/interfaces* and connect. This is a classic symptom:> My error is "No working leases in persistent database - sleeping."So, what is your NM situation?

---

### Post by dert on 2010-03-25
NOTE:  I just updated my original post.  I neglected to specify this is a 64 bit system.  As we move forward, please have that in mind.

My Interfaces File:
```

auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-ssid (edited out: MY Router's SSID)
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk (edited out: My HEX Passphrase)

```

Forgive me for being daft, again I'm a NOOB, but by Network Manager I believe you're referring to the function at System/Administration/Network.  That tool is well intentioned but for wireless setup sorely lacking.  It will NOT accept ANY input in the password field.  I entered it again and again and again and saved and went to the interfaces file and interfaces did not update with any of the info from NM.  I disabled all other network devices in NM, leaving only the Netgear device which was assigned WLAN1.  Tried password entry again and it would not take from NM.  Since NM failed me, I manually edited the interfaces file above.  You know what's interesting?  If you manually edit the interfaces file and go back to NM, the password field populates with a bunch of ****** !  So it cannot write to interfaces correctly but it sure does read it well.

At any rate, if I'm mistaken about your NM reference and you're referring to another tool, please note this is an Out of Box, unmodified install.  So if NM comes out of the box, then it is definitely there and functioning as designed.

---

### Post by chili555 on 2010-03-25
> So if NM comes out of the box, then it is definitely there and functioning as designed.That's my whole point. It will not, in my experience, cooperate with *interfaces* and vice versa. Please try System > Preferences > Startup Applications and uncheck NM. Reboot and see if the behavior is improved. If it is not, you can see some clues in:```
sudo cat /var/log/syslog | grep wlan
```Post them if you are unsure. The file will be quite large, so just check and post the last ten or so lines before 'failure to communicate.'

---

### Post by dert on 2010-03-25
Ah, we were speaking two languages.  OK, the NM you were speaking about was never running.  I checked the start up items and it's not even listed, so we don't need to worry about that.  The Network tool I was speaking about the Network GUI under the System/Administration/Network menu.  I tried using that GUI to set up the interfaces file but it's non-functional and needs a bug report filed.  I'll take care of that.

Here's the syslog data you requested:
```

Mar 25 10:45:37 quadmonster kernel: [   13.927136] udev: renamed network interface wlan0 to wlan1
Mar 25 10:45:45 quadmonster kernel: [   21.847847] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Mar 25 10:45:46 quadmonster dhclient: Listening on LPF/wlan1/00:1e:2a:42:45:1b
Mar 25 10:45:46 quadmonster dhclient: Sending on   LPF/wlan1/00:1e:2a:42:45:1b
Mar 25 10:45:46 quadmonster dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
Mar 25 10:45:52 quadmonster dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
Mar 25 10:46:47 quadmonster avahi-autoipd(wlan1)[2715]: Found user 'avahi-autoipd' (UID 106) and group 'avahi-autoipd' (GID 113).
Mar 25 10:46:47 quadmonster avahi-autoipd(wlan1)[2715]: Successfully called chroot().
Mar 25 10:46:47 quadmonster avahi-autoipd(wlan1)[2715]: Successfully dropped root privileges.
Mar 25 10:46:47 quadmonster avahi-autoipd(wlan1)[2715]: Starting with address 169.254.3.212
Mar 25 10:46:52 quadmonster avahi-autoipd(wlan1)[2715]: Callout BIND, address 169.254.3.212 on interface wlan1
Mar 25 10:46:52 quadmonster avahi-daemon[1780]: Joining mDNS multicast group on interface wlan1.IPv4 with address 169.254.3.212.
Mar 25 10:46:52 quadmonster avahi-daemon[1780]: New relevant interface wlan1.IPv4 for mDNS.
Mar 25 10:46:52 quadmonster avahi-daemon[1780]: Registering new address record for 169.254.3.212 on wlan1.IPv4.
Mar 25 10:46:56 quadmonster avahi-autoipd(wlan1)[2715]: Successfully claimed IP address 169.254.3.212
Mar 25 10:52:15 quadmonster dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
Mar 25 10:52:20 quadmonster dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
Mar 25 10:52:29 quadmonster dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14

```

I removed a bunch of the repetitious DHCPDISCOVER entries since they're just redundant retries.  They're not getting through.

---

### Post by chili555 on 2010-03-25
> udev: renamed network interface wlan0 to wlan1> auto wlan1
iface wlan1 inet dhcp
Why, one wonders, is this wlan[COLOR="Red"]1[/COLOR]? Was there a different wireless device in use previously? I'm not sure that is a factor, however, inquiring minds...et al.

What does this tell us:```
sudo iwlist wlan1 scan
sudo iwlist wlan1 auth
dmesg | grep rtl8
```Thanks.

---

### Post by dert on 2010-03-25
I saw that too.  No other wireless device was ever connected.  This PC is a brand new build from a barebones kit I bought (@ $1300 price tag) and uses an XFX X58i motherboard with 2 Gigabyte ethernet ports and no on-board wireless.  I'd never seen a motherboard with 2 LAN jacks but both are recognized properly as eth0 and eth1.  Please note, Ubuntu took preference over eth1 and used that during the initial install when I wired it to the LAN.  Seems to like the 1 devices over 0 for some reason.  I'm sure that's a red herring here though.

Here is your requested info:

```

wlan1     Scan completed :
          Cell 01 - Address: 00:1A:70:74:7F:FC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"EDIT OUT:  MY ROUTER SSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000035e6d49e2
                    Extra: Last beacon: 1161ms ago
                    IE: Unknown: 000777697265646176
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 02 - Address: 00:25:9C:CC:EC:84
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Stephanie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00015c11d698a180
                    Extra: Last beacon: 1355ms ago
                    IE: Unknown: 00095374657068616E6965
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E0050F204104A0001101044000102

```

```

wlan1     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Authentication algorithm :
		open
		shared-key

```

```

[   13.214205] phy0: hwaddr 00:1e:2a:42:45:1b, RTL8187BvE V0 + rtl8225z2
[   13.235687] rtl8187: Customer ID is 0x00
[   13.235713] Registered led device: rtl8187-phy0::tx
[   13.235724] Registered led device: rtl8187-phy0::rx
[   13.235740] usbcore: registered new interface driver rtl8187

```

I edited out my SSID up there.  The other one "Stephanie" is unknown to me...is it picking up a neighbor's wifi spot???  That's neat...maybe save me some money...LOL  I would never do that.

---

### Post by dert on 2010-03-25
Well I'll be a monkey's uncle...my wireless device just came up.  It's been down for 2 days.  I didn't do anything other than run the commands you asked me to but the next thing I noticed was the network icon in the upper right hand corner come to life!  I checked the syslog and after several more dhcp failed requests, I got offered an IP Address!  WOW!

Do you think the iwlist scan did the trick???  Perhaps it needed a little "push" to find all the available access points?  That's all I can think.  I'm going to reboot the daylights out of this thing now and see if it auto-discovers and negotiates by itself.  I will report back shortly.

I can't thank you enough for your assistance.  You are wise and wonderful.

---

### Post by dert on 2010-03-25
I am fixed.  For those of you using a WG111v3 running on Ubuntu 9.10 and above on x64 systems, I advise you to follow these instructions to get a wireless connection up and running.

1.  Do NOT use the GUI available at System/Administration/Network.  It does not work for WPA/WPA2 connections.  I cannot speak to WEP or wide open connections but I suspect it's equally incapable of creating those either.
2.  Instead follow the instructions [at this site]("http://ubuntuforums.org/showthread.php?t=202834") TO THE LETTER.  If you do not place the entries in exact order you will get a FAIL message upon a network restart.  Start at step 1 as wpa supplicant is installed by default.  When editing your interfaces file, feel free to leave the lo entry as is but I would comment out the eth0[1,2 etc] entries if you're going pure wireless just to eliminate problem causes.  You may just use dhcp as I do or do as the author says and assign an IP address.  I chose not to do that initially to eliminate anything that would make the process more complicated.
3.  If wpa_passphrase errors out because you use non-standard characters, please visit [this page]("http://www.xs4all.nl/~rjoris/wpapsk.html") which performs the same calculation via HTML and will provide you with the correct HEX string to use in your interfaces file.  It SAVED ME!  I owe the author huge KUDOS.
4.  If you, like me, find yourself floundering around afterwards with no network activity.  Perform the same commands I was asked to here and you might be pleasantly surprised.  Note I performed the iwlist scan as part of my step 2 above, but for some reason I believe a 2nd iteration "pushes" the adapter to properly negotiate a connection.  The complete list of steps I was asked to do here was:
```

sudo iwlist wlan1 scan
sudo iwlist wlan1 auth
dmesg | grep rtl8

```
I would do all 3 as I cannnot determine which one brought my adapter to life.

That's it.  I wish I could tell you exactly why I'm up now...bit of a mystery I'm afraid.  With luck, you should be too with the information available here.

Blessings be upon you chili555.

---

### Post by dert on 2010-03-25
wpa_passphrase issue with non-alphanumeric characters reported as bug to launchpad - 547110.

Network GUI issue with password not being written to interfaces file reported as bug to launchpad - 547092.

---

