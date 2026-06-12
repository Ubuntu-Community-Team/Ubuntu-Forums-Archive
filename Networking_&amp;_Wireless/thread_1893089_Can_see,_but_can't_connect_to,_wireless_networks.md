---
title: "Can see, but can't connect to, wireless networks"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by zcacogp on 2011-12-09
Hello. 

I am having problems with wireless networking on my Thinkpad X61s. It worked fine, but I (stupidly) removed network-manager, and had to re-install it (moved the debs to it using a USB memory stick.) 

Now I can use wired networking fine but not wireless. If I click the Network Icon in the top panel I can see a lit of local wireless networks (including my own), but can't connect to any of them; if I click on one, nothing happens. The command nm-tool gives this: 

```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:16:D3:C4:54:9E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             192.168.10.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:1D:E0:1B:12:8B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BTHub3-TNNM:     Infra, 00:FE:F4:60:76:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 28 WPA WPA2
    BTHomeHub-82CB:  Infra, 00:18:F6:AE:A1:B5, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WEP
    BTHub3-9SF8:     Infra, 20:2B:C1:83:AF:F9, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Ghost:           Infra, 84:C9:B2:77:40:16, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SerifBooks:      Infra, 64:0F:28:05:26:31, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTOpenzone:      Infra, 64:0F:28:05:26:34, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    BTOpenzone:      Infra, 02:FE:F4:2A:84:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    BTFON:           Infra, 12:FE:F4:2A:84:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    BTOpenzone-H:    Infra, 02:24:17:F9:D6:BC, Freq 2442 MHz, Rate 54 Mb/s, Strength 41
    BTFON:           Infra, 02:24:17:F9:D6:BD, Freq 2442 MHz, Rate 54 Mb/s, Strength 40
    BTHub3-QN43:     Infra, 00:FE:F4:2A:84:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    BTHomeHub2-Z62T: Infra, 00:24:17:F9:D6:BB, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SKY07311:        Infra, 00:1E:74:77:1C:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 41 WPA
    Unisox:          Infra, 00:1F:33:07:0B:56, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
``` 

(It shows as 'connected' at the moment as it is connected using a network cable.) The wireless network 'Unisox' is mine. 

The command 'sudo iwconfig' gives this: 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

I feel that I am an ace away from the solution, but don't know what to do. If I look at "Additional Drivers" it lists no proprietary drivers for the system. 

All suggestions welcome - thanks. 


Oli.

---

### Post by praseodym on 2011-12-09
Hi,
two things:

The N-mode of the driver iwlagn is buggy, you can deactivate it with:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
``` 

Second: There is a bug with the country code settings (see here in "iwconfig", only 15 dBm [equals about 25 %] are shown). Which country do you live?

```
sudo apt-get install iw
iw reg get
sudo iw reg set [COLOR="Red"]DE[/COLOR]
iw reg get 
iw list
iwlist chan
```
Change DE (for Germany) to your country code

---

### Post by zcacogp on 2011-12-09
Praseodym, 

Thanks for your answer. 

I'm in the UK. I tried the first block of commands you gave me, to deactivate the N-mode, and then the second set. Various of them gave me readouts on screen - do I need to list them? 

The end result is the same as before - I can see the list of wireless networks but can't connect to any of them. (I tried logging out and logging in again and the login was slow, but still it wouldn't connect.) 


Oli.

---

### Post by zcacogp on 2011-12-09
The responses to those commands are as follows: 

iw reg get: 

```
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

iw  list: 

```
Wiphy phy0
	Band 1:
		Frequencies:
			* 2412 MHz [1] (15.0 dBm)
			* 2417 MHz [2] (15.0 dBm)
			* 2422 MHz [3] (15.0 dBm)
			* 2427 MHz [4] (15.0 dBm)
			* 2432 MHz [5] (15.0 dBm)
			* 2437 MHz [6] (15.0 dBm)
			* 2442 MHz [7] (15.0 dBm)
			* 2447 MHz [8] (15.0 dBm)
			* 2452 MHz [9] (15.0 dBm)
			* 2457 MHz [10] (15.0 dBm)
			* 2462 MHz [11] (15.0 dBm)
			* 2467 MHz [12] (15.0 dBm) (passive scanning, no IBSS)
			* 2472 MHz [13] (15.0 dBm) (passive scanning, no IBSS)
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	Band 2:
		Frequencies:
			* 5180 MHz [36] (15.0 dBm)
			* 5200 MHz [40] (15.0 dBm)
			* 5220 MHz [44] (15.0 dBm)
			* 5240 MHz [48] (15.0 dBm)
			* 5260 MHz [52] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5280 MHz [56] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5300 MHz [60] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5320 MHz [64] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5500 MHz [100] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5520 MHz [104] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5540 MHz [108] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5560 MHz [112] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5580 MHz [116] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5600 MHz [120] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5620 MHz [124] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5640 MHz [128] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5660 MHz [132] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5680 MHz [136] (15.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5700 MHz [140] (15.0 dBm) (passive scanning, no IBSS, radar detection)
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	max # scan SSIDs: 20
	Supported interface modes:
		 * IBSS
		 * managed
		 * monitor
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * new_beacon
		 * new_station
		 * new_mpath
		 * set_mesh_params
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * Unknown command (68)
		 * Unknown command (55)
		 * Unknown command (57)
		 * Unknown command (59)
		 * Unknown command (67)
		 * set_wiphy_netns
		 * Unknown command (65)
		 * Unknown command (66)
		 * connect
		 * disconnect

```

iwlist chan:

```

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

```

Thanks again. 


Oli.

---

### Post by praseodym on 2011-12-09
Which channel do you want to use? With deactivated N-mode try channel 1-11

---

### Post by zcacogp on 2011-12-09
praseodym, 

Thanks again. It's on channel 11. 


Oli.

---

### Post by zcacogp on 2011-12-09
praseodym, 

SOLVED! Thanks. A restart seems to have me happily connected; simply logging out and in again can't have been enough. 

Thanks for your help - it's appreciated! 


Oli.

---

### Post by zcacogp on 2011-12-09
Update: While this has solved the networking problem, it also seems to have made the computer shutdown very slow. 

Is this relevant, or just co-incidental? 

Anything I can do about it? 

Thanks again, 


Oli.

---

### Post by praseodym on 2011-12-09
Try:

```
sudo depmod -a
sudo update-initramfs -u
sudo shutdown -r now # this reboots from terminal
```

---

### Post by zcacogp on 2011-12-10
praseodym, 

Thanks again. 

I tried those and it hasn't made any difference; shutting down still takes 5 or 6 minutes (could be as little as 5 seconds or so before.) 

Can I look up some log files and see what is taking the time? 

(Alternatively, can I 'repair' the installation using the installation disk? Would this be an easier way forward?) 

Thanks again for your help. 


Oli.

---

### Post by praseodym on 2011-12-10
Check the files:

/var/log/syslog
/var/log/dmesg
/var/log/Xorg.0.log

---

### Post by zcacogp on 2011-12-10
praseodym, 

Thanks. The files are large; too large for me to copy the contents as text in here, and too large to be accepted as attachments to the message either. I've uploaded them to sendspace, and they are here: 

/var/log/syslog
[http://www.sendspace.com/file/phsrgx](http://www.sendspace.com/file/phsrgx)

/var/log/dmesg
[http://www.sendspace.com/file/t78zct](http://www.sendspace.com/file/t78zct)

/var/log/Xorg.0.log
[http://www.sendspace.com/file/ug8zl4](http://www.sendspace.com/file/ug8zl4)

I hope this works ... let me know whether it does or doesn't. Or if you'd rather I made them available in some other way. 

I don't know much about these things, but there are a lot of entries in /var/log/syslog concerning Network Manager - is this relevant?

Thanks again for your help. 


Oli.

---

### Post by praseodym on 2011-12-11
There are a lot of "CIFS-errors". Any SAMBA services activated?

---

### Post by zcacogp on 2011-12-11
praseodym, 

There were, but I have just turned them off (uninstalled Samba) and rebooted and it hasn't made any difference. It does however access Samba shares on another machine, and these are auto-mounted in fstab. 

It used to shut down quickly until I re-installed Network Manager, which is when it became slow. I didn't change the Samba configuration when I did this, so I wouldn't expect Samba to be causing the problem. 

Here's fstab from the slow machine (the Samba client) should it be relevant: 

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0b5b1d8e-eef1-4323-938c-3fe81aea73f2 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda8 during installation
UUID=d66f229b-2de1-4d82-b65c-62ba3c33ace1 none            swap    sw              0       0

/dev/sda5 /media/Horatio ntfs-3g defaults,locale-en_GB.utf8 0 0

/dev/sda6 /media/Ieuan ntfs-3g defaults,locale-en_GB.utf8 0 0

//desktop/Helena /media/Helena cifs credentials=/etc/samba/users,noexec 0 0

//desktop/Ianthe /media/Ianthe cifs credentials=/etc/samba/users,noexec 0 0

//desktop/cdrom /media/cdrom cifs credentials=/etc/samba/users,noexec 0 0

```

Thanks again for your help. 


Oli.

---

### Post by zcacogp on 2011-12-11
praseodym, 

Thanks for your help. I've started a new thread on this topic; this one is marked as 'Solved' and is in 'Wireless and Networking', neither of which seem quite correct! 

New thread is here: 

[http://ubuntuforums.org/showthread.php?p=11530935#post11530935](http://ubuntuforums.org/showthread.php?p=11530935#post11530935)

Thanks again for your input. 


Oli.

---

### Post by zcacogp on 2011-12-15
praseodym, 

It turns out that this is a known issue, and there are quite a number of threads about it. 

One of them is here: 

[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

... with a solution which worked for me. 

Thanks again for your help. 


Oli.

---

### Post by rabarrett on 2012-06-08
I'm completely new to linux.  I just installed, everything was working fine except when I clicked on my wireless network, instead of asking me for a password, it did nothing.  I searched around, found this post, and thought "that sounds similar to my problem, I'll try it."

Problem is, I have a different driver than the one listed [so I just substituted it] and I got some error messages when I did the 2nd command above (but pressed on like a brave chap).  (It was my first time using command line.)

My driver was ipw2200.

Now, instead of seeing my network and having nothing happen when I click... well, I don't see my any wireless now.

I hoped that maybe I uninstalled the driver and now I could reinstall it, but when I go to "additional drivers" it doesn't find any.

Any help getting my wireless driver reinstalled and working is much appreciated.  (My hardwire is working fine.)

I'm running ubuntu 12.04, fresh install on my laptop.

> **praseodym said:**
> Hi,
two things:

The N-mode of the driver iwlagn is buggy, you can deactivate it with:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
``` 

Second: There is a bug with the country code settings (see here in "iwconfig", only 15 dBm [equals about 25 %] are shown). Which country do you live?

```
sudo apt-get install iw
iw reg get
sudo iw reg set [COLOR="Red"]DE[/COLOR]
iw reg get 
iw list
iwlist chan
```
Change DE (for Germany) to your country code

---

