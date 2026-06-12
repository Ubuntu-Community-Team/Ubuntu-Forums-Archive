---
title: "Unable to Install Drivers | Network Lockdown (No Wifi / Ethernet) | Ubuntu 12.04"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by sky70 on 2012-08-08
hey all,

I will get straight to the problem.

I got a laptop here namely Toshiba Satellite C850 - P5010.

The problem is neither my wired (Atheros fast ethernet AR8162 Rev.10) NOR the wireless Realtek Device 8723 is recognized by my Ubuntu 12.04 x64 (64-bit):( Giving me a totally network lockdown situation :(

I am aware of the new Realtek's wirelss chipset family 8723 creating a havoc with the linux community. Even we are able to access the drivers using the Dropbox link available across many forums **BUT the prob is >>** 
I would be requiring the essential build packages needed for compilation of the drivers which to my knowledge I cannot download unless I have a working wired connection on my new Toshiba.

I am writing this post using my old Dell laptop and though I am not new to Linux, now after a year or so have totally forgot the touch of ~nux command line skills.

Please help :(

Any suggestions appreciated..
Thanks & Regards,
Kanishk

---

### Post by sky70 on 2012-08-08
Allright guys..I was panicking I guess :D

I tried [these steps]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized")

though my wireless card has detected the wifi network but the signal strength is barely accessible. I am sitting next to my wifi router and I am getting 27% as network's strength.

Nice one Realtek :/

Thx for atleast reading this thread; no suggestions so far :/

---

### Post by blackdiamondkao on 2012-08-13
I also have the same problem with u. 
Do u have any way to solve it?

---

### Post by drpaul on 2012-08-13
The only way I have found around it is to run a virtual machine under Windows. Without some internet connection, I have been unable to get all the packages needed to compile the driver from Realtek. With a virtual machine, the internet connection is made through the Windows drivers.

---

### Post by ddrake on 2012-09-01
Hi 

 I too bought  the same brand and system - just that on installing 12.04 I found neither the wired (Atheros) nor the wireless (realtek) interfaces are recognized.

 While searching I always got the to fix the wireless mode. How about the wired (atheros) mode?  Can anyone help on the wired mode as well?

thanks in advance
DDrake

---

### Post by drpaul on 2012-09-01
The wired mode is probably AR8161. If it is, then the alx driver in the compat-wireless package would be what you need. Search around for hints.

With wireless working you shouldn't have any trouble getting all of the packages you need to generate the driver.

---

### Post by chili555 on 2012-09-01
> **drpaul said:**
> The wired mode is probably AR8161. If it is, then the alx driver in the compat-wireless package would be what you need. Search around for hints.Indeed. Search around here: [http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx](http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx)

Verify the pci.id before you proceed:```
lspci -nn | grep 0280
```

---

### Post by ddoxey on 2012-09-08
I recently purchased a Toshiba Satellite S855-S5260. This has a Realtek 8723 wireless device. I upgraded to 16GB RAM and installed a 120GB SSD. Then I installed Xubuntu 12.04 64bit (3.2.0-30-generic).

I was able to install the Realtek 8723ae module following the instructions linked to above.
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

Unfortunately, the connection was sporadic. It would work good for a while and then it would keep cycling through a connect reconnect loop. 

My /var/log/syslog was looking a bit like this:
> [FONT="Courier New"]Sep  8 06:12:21 toshidox wpa_supplicant[1098]: **[COLOR="Blue"]Trying to authenticate with 00:1d:7e:5e:0d:47 (SSID='oinker' freq=2437 MHz)[/COLOR]**
Sep  8 06:12:21 toshidox kernel: [ 1878.705014] wlan0: authenticate with 00:1d:7e:5e:0d:47 (try 1)
Sep  8 06:12:21 toshidox kernel: [ 1878.706653] wlan0: authenticated
Sep  8 06:12:21 toshidox wpa_supplicant[1098]: Trying to associate with 00:1d:7e:5e:0d:47 (SSID='oinker' freq=2437 MHz)
Sep  8 06:12:21 toshidox kernel: [ 1878.707983] wlan0: associate with 00:1d:7e:5e:0d:47 (try 1)
Sep  8 06:12:21 toshidox kernel: [ 1878.711034] wlan0: RX ReassocResp from 00:1d:7e:5e:0d:47 (capab=0x411 status=0 aid=2)
Sep  8 06:12:21 toshidox kernel: [ 1878.711037] wlan0: associated
Sep  8 06:12:21 toshidox wpa_supplicant[1098]: Associated with 00:1d:7e:5e:0d:47
Sep  8 06:12:21 toshidox wpa_supplicant[1098]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:5e:0d:47 completed (reauth) [id=0 id_str=]
Sep  8 06:12:21 toshidox NetworkManager[881]: <info> (wlan0): supplicant interface state: authenticating -> completed
Sep  8 06:12:24 toshidox NetworkManager[881]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:1D:7E:5E:0D:47 (oinker)
Sep  8 06:12:27 toshidox kernel: [ 1885.027413] **[COLOR="DarkOrchid"]rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off[/COLOR]**, try to reconnect now
Sep  8 06:12:27 toshidox kernel: [ 1885.027492] wlan0: Connection to AP 00:1d:7e:5e:0d:47 lost.
Sep  8 06:12:27 toshidox wpa_supplicant[1098]: CTRL-EVENT-DISCONNECTED bssid=00:1d:7e:5e:0d:47 reason=4
Sep  8 06:12:27 toshidox NetworkManager[881]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep  8 06:12:27 toshidox kernel: [ 1885.099419] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep  8 06:12:27 toshidox kernel: [ 1885.099434] cfg80211: Restoring regulatory settings
Sep  8 06:12:27 toshidox kernel: [ 1885.099443] cfg80211: Calling CRDA to update world regulatory domain
Sep  8 06:12:27 toshidox kernel: [ 1885.107725] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Sep  8 06:12:27 toshidox kernel: [ 1885.107734] cfg80211: World regulatory domain updated:
Sep  8 06:12:27 toshidox kernel: [ 1885.107738] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  8 06:12:27 toshidox kernel: [ 1885.107745] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  8 06:12:27 toshidox kernel: [ 1885.107752] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  8 06:12:27 toshidox kernel: [ 1885.107757] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  8 06:12:27 toshidox kernel: [ 1885.107763] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  8 06:12:27 toshidox kernel: [ 1885.107769] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  8 06:12:27 toshidox NetworkManager[881]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  8 06:12:28 toshidox wpa_supplicant[1098]: Trying to authenticate with 00:1d:7e:5e:0d:47 (SSID='oinker' freq=2437 MHz)
Sep  8 06:12:28 toshidox NetworkManager[881]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  8 06:12:28 toshidox kernel: [ 1886.107405] wlan0: authenticate with 00:1d:7e:5e:0d:47 (try 1)
Sep  8 06:12:28 toshidox kernel: [ 1886.305663] wlan0: authenticate with 00:1d:7e:5e:0d:47 (try 2)
Sep  8 06:12:29 toshidox kernel: [ 1886.505359] wlan0: authenticate with 00:1d:7e:5e:0d:47 (try 3)
Sep  8 06:12:29 toshidox kernel: [ 1886.705175] wlan0: authentication with 00:1d:7e:5e:0d:47 timed out
Sep  8 06:12:30 toshidox NetworkManager[881]: <info> (wlan0): roamed from BSSID 00:1D:7E:5E:0D:47 (oinker) to (none) ((none))
Sep  8 06:12:35 toshidox wpa_supplicant[1098]: **[COLOR="blue"]Trying to authenticate with 00:1d:7e:5e:0d:47 (SSID='oinker' freq=2437 MHz)[/COLOR]**[/FONT]



After quite a bit of experimentation and Googling about, I came to the conclusion that no one else was having this issue. My solution was to find the line in the driver C code which emits "rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now".  I found it in **rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c**.

I changed the line that reads:
> [FONT="Courier New"]if ( rtlpriv->link_info.roam_times >= 3 ) {[/FONT]
To:
> [FONT="Courier New"]if ( rtlpriv->link_info.roam_times >= 30 ) {[/FONT]

This allows a roam time of up to 60 seconds (rather than 6) before attempting reconnect.

After making the mod:
[INDENT][FONT="Courier New"]make clean
make
make install
modprobe -r rtl8723e
modprobe rtl8723e[/FONT][/INDENT]

Connection is no longer cycling on and off and I'm a happy camper. I found that it would get roam times of up to 30 seconds and then no more.

P.S. The **alx** module works great for the Atheros AR8161 Ethernet hardware.

---

### Post by chili555 on 2012-09-09
> if ( rtlpriv->link_info.roam_times >= 30 ) {Awesome! Thanks for the research and hard work. I'm sure you will have helped quite a few searchers.

Great job!

---

### Post by drpaul on 2012-09-18
Final post for me on this subject.

I was able to use my virtual install in Windows with this

[http://fractalbrain.wordpress.com/projects/ubuntu-linux-offline-install/](http://fractalbrain.wordpress.com/projects/ubuntu-linux-offline-install/)

to generate a 12.04 install that would compile and install the alx driver without messing with the 8723 driver.

I consider it a VICTORY!

Thanks to the community.

Paul

---

### Post by kiltedcameraman on 2012-11-07
I too, and trying to fix this problem.  The very first step at [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)  says
> 
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r'this gets me two messages:
E: Unable to locate package build-essential
E: Unable to locate package linux-header-'uname-r'

So what next?

Adam

---

### Post by drpaul on 2012-11-07
kiltedcameraman:

If you have no internet connection you can't use those commands. Also, the second command seems to be mistyped. The last phrase should execute the uname command and insert the proper text there.

If you have no internet connection, then you might try the procedure referenced in my previous post.

HTH

paul

---

### Post by chili555 on 2012-11-07
> **drpaul said:**
> kiltedcameraman:

If you have no internet connection you can't use those commands. Also, the second command seems to be mistyped. The last phrase should execute the uname command and insert the proper text there.

If you have no internet connection, then you might try the procedure referenced in my previous post.

HTH

paulIt is only slightly mis-formed. It will automagically find the correct package with:```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r` 
```Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by kiltedcameraman on 2012-11-07
That fixed the uname problem, but it still can't locate build-essential

---

### Post by kiltedcameraman on 2012-11-07
I have the dropbox files on both a flash drive, and the desktop at the moment.  Could that be the problem?  Where should I extract them to?

---

### Post by kiltedcameraman on 2012-11-08
Solved it.

To explain how for new users like me.

1. Downloaded the files from dropbox on another machine to a flash drive.
2. extracted to new machine right on desktop.
3. opened terminal
3a. terminal wouldn't let me change to that folder
4. Used mkdir to make new folder
5. copied contents of old folder to new folder
6. in terminal used cd to change to new folder.
7. in terminal sudo su
8. in terminal make
9. in terminal make install
10.in terminal reboot

after the reboot everything works.

---

### Post by Pedro Santana on 2013-02-12
I had a similar problem with the Realtek 8723 (no wireless after ubuntu update) and have used this information to solve the  problem. 
It's a huge relief.
Thanks to everyone that posted their suggestions and attempts.

---

