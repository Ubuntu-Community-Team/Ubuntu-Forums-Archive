---
title: "Can't connect WUSB300N with WPA2"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by cjsegninir on 2010-02-21
Hello everyone,
 
This is my first post in the community, because it is my first approach to Linux. As you can imagine I have thousands of problems, but right now I'd be happy if I can get the wifi working. I have tried many things I've read in this and other forums, but there came a a point where everything was out of my Linux understanding.
 
First of all, my wireless adapter is a Linksys WUSB300N. As per my research, there is no Linux driver for it, so I installed the windows one with ndiswrapper (after many many tears!). Initially it works, since I can see the available networks and so on. The problem is that everytime I restart, it is not available so I have to repeat some of the ndiswrapper steps. Most likely, I'm doing something wrong (Did I tell you I'm a total noob?) or I need a simple script, but I don't know how to do it.
 
The second problem is that my home network has a WPA2 security protocol. I know I could just change it for WEP, but geek vein doesn't allow me to. I was reading some threads on how to connect to WPA2, but sincerely, I could not understand them.
 
Summarizing, if I'm not going too far, I'm asking you to explain step by step (Like you will teach your little 5 years old son) how to solve both problems. 
 
Thanks a lot!!!
Best regards,
C.S.
 
PS: Please take in account I don't have internet access in the Linux PC without the Wifi. Therefore, I cannot download anything from the repos. I have to come to the windows Laptop, download it, and then take it to the PC. Thanks again!

---

### Post by northd_tech on 2010-02-21
> **cjsegninir said:**
> Hello everyone,
 
First of all, my wireless adapter is a Linksys WUSB300N. As per my research, there is no Linux driver for it, so I installed the windows one with ndiswrapper (after many many tears!). Initially it works, since I can see the available networks and so on. The problem is that everytime I restart, it is not available so I have to repeat some of the ndiswrapper steps. Most likely, I'm doing something wrong (Did I tell you I'm a total noob?) or I need a simple script, but I don't know how to do it.
 
The second problem is that my home network has a WPA2 security protocol. I know I could just change it for WEP, but geek vein doesn't allow me to. I was reading some threads on how to connect to WPA2, but sincerely, I could not understand them.
 
The first one is actually really easy to fix.  Open a Terminal window (go to Applications > Accessories > Terminal) -it is waaay down at the bottom.

Enter this command in that terminal window so that we can edit a configuration file (spelling, capitalization, and punctuation matter much more in UNIX/Linux than in Windows):

```
gksu gedit /etc/modules
```Add this to the bottom of whatever is already in that file in the "gedit" text editor that just opened up:

```
#The following line will load the "ndiswrapper" module for wireless Windows driver support at startup
ndiswrapper

```Be sure to save that file, and then exit the "gedit" editor.

To try something on your 2nd problem, enter this while you've still got the terminal window open (or else open a new one if you closed it already):

```
sudo apt-get install wireless-tools
```If you want to read about Linux wireless on a rainy day, here is some documentation on that (but don't worry about it right now):

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

If that terminal gives you any error messages, please copy/paste them and post them here.  If it seems successful, you can just paraphrase what the results were (or else copy/paste those here too).

Now while it isn't as good as WPA2, you might consider using the first version of WPA if your wireless router supports it (it is a LOT better than WEP), but you don't need to give up on WPA2 just yet.

Also, we should probably find out what version of ubuntu and kernel you are running- these terminal commands should tell us that part:

```
cat /etc/lsb-release

uname -a
```

edit:  Here is an old thread about that WUSB300N:

[http://ubuntuforums.org/showthread.php?t=530772](http://ubuntuforums.org/showthread.php?t=530772)

From this question, it sounds like ndiswrapper is/was the only option:

[https://answers.launchpad.net/ubuntu/+source/ndiswrapper/+question/60322](https://answers.launchpad.net/ubuntu/+source/ndiswrapper/+question/60322)

---

### Post by northd_tech on 2010-02-21
Here are some old threads about getting WPA encryption under ndiswrapper- there are 3 other packages that need to be installed besides just ndiswrapper.  These don't look updated for WPA2 that I read in a quick scan, though.

**HOWTO: Automated WPA Encryption with ndiswrapper drivers ** 
[http://ubuntuforums.org/showthread.php?t=31418](http://ubuntuforums.org/showthread.php?t=31418)

**How to get Ndiswrapper with wpa_supplicant working  **
[http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Ndiswrapper_with_wpa_supplicant_working](http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Ndiswrapper_with_wpa_supplicant_working)

---

### Post by cjsegninir on 2010-02-21
Thanks for your fast reply northd_tech
 
Regarding the first question, its obviously solved. I knew it had to be simple, but I didn't know how... 
 
For the second, The wireless-tools was already installed and here is the output of the codes you asked me to run:
 
```
 DISTRIB_ID=UBUNTU
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=Karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10" 
```
 
and
 
```
 Linux casa-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux 
```
 
I also tried some stuff from the second post (Specifically, **How to get Ndiswrapper with wpa_supplicant working).**
 
I created the wpa_supplicant.conf file for WPA2-Personal (As defined in [http://www.thinkwiki.org/wiki/Wpa_supplicant](http://www.thinkwiki.org/wiki/Wpa_supplicant))
 
It looks like this
 
```
 *ctrl_interface=/var/run/wpa_supplicant*
*ctrl_interface_group=0*
*ap_scan=1*
*network={*
*ssid="****"*
*proto=RSN*
*key_mgmt=WPA-PSK*
*pairwise=CCMP TKIP*
*group=CCMP TKIP*
*psk="*************"*
*} *
```
 
Then I ran
 
```
 **sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext **
```
 
and the output was 
 
```
 *CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS *
*Trying to associate with 00:1e:e5:4b:a6:a3 (SSID='casa' freq=2437 MHz)*
*Association request to the driver failed*
*Associated with 00:00:00:00:00:00*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS *
*Trying to associate with 00:1e:e5:4b:a6:a3 (SSID='casa' freq=2437 MHz)*
*Association request to the driver failed*
*Associated with 00:00:00:00:00:00*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS* 
```
 
And repeated forever and ever...
 
At the end, I'm still in the same place... Is there any step missing?
 
Thanks in advance!
Cheers,
C.S.

---

### Post by northd_tech on 2010-02-21
> **northd_tech said:**
> ... there are 3 other packages that need to be installed besides just ndiswrapper.  These don't look updated for WPA2 that I read in a quick scan, though.

This was covered [briefly] on one of those two threads, but I think you probably need to install wpasupplicant (if you didn't already) and ndiswrapper-tools.

I believe (not certain) that these terminal commands should do that for you:

```
sudo apt-get install wpasupplicant

sudo apt-get install ndiswrapper-utils
```That first "wpasupplicant" command might over-write what you did for the WPA stuff that you just posted about, so you might want to save a backup copy of all that first (or a bookmark/link/note to where you found it)

Here is a bunch more documentation about ndiswrapper and WPA (more for other readers).  It's been over a year since I used ndiswrapper much, and every so often these questions come up and we all get a refresher course.  There are many threads here about "ndiswrapper" but some of that information is pretty old now and may not apply or be necessary anymore.

WPA Howto
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

ndiswrapper-utils
[http://ubuntuforums.org/showthread.php?t=7160](http://ubuntuforums.org/showthread.php?t=7160)

**sudo apt-get install ndiswrapper-utils**
[http://ubuntuforums.org/showthread.php?t=244094](http://ubuntuforums.org/showthread.php?t=244094)

Ndiswrapper documentation
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

edit:  Also that's a 32-bit version of Karmic Koala 9.10 ubuntu, with a 2.6.31-14-generic kernel (which is an older but pretty stable one).  I think the kernels are up to 31-19 now (but 31-15 and 31-16 were buggy on a relative's Toshiba Satellite laptop for me).  Sometimes a newer kernel will work better with your hardware, but VERY often the newer version works worse (or not at all), so I wouldn't hurry to upgrade that part if everything else works pretty well.

---

### Post by northd_tech on 2010-02-21
> **cjsegninir said:**
> 
I created the wpa_supplicant.conf file for WPA2-Personal (As defined in [http://www.thinkwiki.org/wiki/Wpa_supplicant](http://www.thinkwiki.org/wiki/Wpa_supplicant))
 
It looks like this
 
```
 *ctrl_interface=/var/run/wpa_supplicant*
*ctrl_interface_group=0*
*ap_scan=1*
*network={*
*ssid="****"*
*proto=RSN*
*key_mgmt=WPA-PSK*
*pairwise=CCMP TKIP*
*group=CCMP TKIP*
*psk="*************"*
*} *
```Then I ran
 
```
 **sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext **
```and the output was 
 
```
 *CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS *
*Trying to associate with 00:1e:e5:4b:a6:a3 (SSID='casa' freq=2437 MHz)*
*Association request to the driver failed*
*Associated with 00:00:00:00:00:00*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS *
*Trying to associate with 00:1e:e5:4b:a6:a3 (SSID='casa' freq=2437 MHz)*
*Association request to the driver failed*
*Associated with 00:00:00:00:00:00*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys*
*CTRL-EVENT-SCAN-RESULTS* 
```And repeated forever and ever...
 
At the end, I'm still in the same place... Is there any step missing?
 
That page looks to me like it is specific for Fedora Linux (Red Hat) and Gentoo Linux.  Ubuntu likely needs different configuration- all "penguins" are not alike, even if they "look" the same. ;)

It is possible that the Ubuntu Advanced Package Tool (the "apt" part of that apt-get command) will set up the configuration for you.

I didn't find a lot of information on that USB wireless though.  Maybe we should see if you have some easier options built in to that computer.  Can you open another terminal and post the results of these commands here?

```
lspci

lsusb

lsmod

sudo lshw -C network

ifconfig

iwconfig
```

The results of those will be pretty long- you will want to copy/paste (or maybe save them to a USB stick if you need to post from a different computer).  "Kate" or "gedit" are 2 good text editors to use to paste the results and then save the file as something like "WUSB300Nerrors1.txt" to the USB drive.  Kate should be under Applications > Accessories (in the middle, but above that terminal).

---

### Post by cjsegninir on 2010-02-21
> **northd_tech said:**
> This was covered [briefly] on one of those two threads, but I think you probably need to install wpasupplicant (if you didn't already) and ndiswrapper-tools.
 
I believe (not certain) that these terminal commands should do that for you:
 
```
sudo apt-get install wpasupplicant
 
sudo apt-get install ndiswrapper-utils
```That first "wpasupplicant" command might over-write what you did for the WPA stuff that you just posted about, so you might want to save a backup copy of all that first (or a bookmark/link/note to where you found it)
 

 
Wpasupplicant was already installed.
 
> **northd_tech said:**
> Here is a bunch more documentation about ndiswrapper and WPA (more for other readers). It's been over a year since I used ndiswrapper much, and every so often these questions come up and we all get a refresher course. There are many threads here about "ndiswrapper" but some of that information is pretty old now and may not apply or be necessary anymore.
 
WPA Howto
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
 
ndiswrapper-utils
[http://ubuntuforums.org/showthread.php?t=7160](http://ubuntuforums.org/showthread.php?t=7160)
 
**sudo apt-get install ndiswrapper-utils**
[http://ubuntuforums.org/showthread.php?t=244094](http://ubuntuforums.org/showthread.php?t=244094)
 
Ndiswrapper documentation
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 

 
I browsed through them. Changed my wpa_supplicant.conf to match the WPA how to, and installed the ndiswrapper-utils and the ndisgtk.
 
> **northd_tech said:**
> It is possible that the Ubuntu Advanced Package Tool (the "apt" part of that apt-get command) will set up the configuration for you.
 

 
It did nothing, since it didn't install anything new.
 
> **northd_tech said:**
>  
I didn't find a lot of information on that USB wireless though. Maybe we should see if you have some easier options built in to that computer. Can you open another terminal and post the results of these commands here?
 
```
lspci
 
lsusb
 
lsmod
 
sudo lshw -C network
 
ifconfig
 
iwconfig
```
 
The results of those will be pretty long- you will want to copy/paste (or maybe save them to a USB stick if you need to post from a different computer). "Kate" or "gedit" are 2 good text editors to use to paste the results and then save the file as something like "WUSB300Nerrors1.txt" to the USB drive. Kate should be under Applications > Accessories (in the middle, but above that terminal).
 
The results are in the attached file (wpa_supplicant.txt).
I'm also attaching another file (error.txt) with the output of the wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -d
 
Hope we can get it solved :cry:
Thanks a lot for your time and support
Regards,
C.S.

---

### Post by UBUSHEP on 2010-02-21
Have you ever seen that movie Pi? Remember where Saul is afraid to go continue his research into pi, afraid he'll have another stroke? That's the feeling I get staring at my laptop running Koala, trying to get it on my WPA2 AES network (SSID being broadcast).

---

### Post by northd_tech on 2010-02-21
Hi again.  I just got back from dinner with the family and read those  files.  I think the filenames are reversed, but no big deal- I can tell  the difference in the output.

This part gives me some hope in  "wpa_supplicant.txt":

> 00:14.0 Bridge: nVidia Corporation  MCP51 Ethernet Controller (rev a1)My NVIDIA nForce  [cabled] ethernet connection has worked "out of the box" with every  single version of Linux that I have tried on this laptop (meaning that  it just automatically worked).

Have you tried hooking up a CAT5  or CAT6 network cable to that computer yet (which appears to have an  NVIDIA MCP51 bridge for ethernet, sound, C51G [GeForce 6100] video,  etc.).

As far as the WUSB300N, I'm not sure whether the bolded  one is that USB wireless interface in the **lsusb** output:

> Bus  001 Device 005: ID 13b1:0029 Linksys 
Bus 001 Device 003: ID  0458:7012 KYE Systems Corp. (Mouse Systems) WebCAM USB2.0
Bus 001  Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device  003: ID 03f0:5511 Hewlett-Packard DeskJet F300 series
**Bus 002  Device 002: ID 04f2:0210 Chicony Electronics Co., Ltd **
Bus 002  Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubMaybe  we need to search a little for "Chicony Electronics 04f2:0210" devices  and see what else we can find out about that.

The interesting  parts of **lsmod** now are:

Module                  Size  Used  by
ndiswrapper           184572  0 
forcedeth              54152   0 

That "forcedeth" module looks like the same one that my  NVIDIA nForce ethernet interfaces uses (that just automatically works  "out of the box" in my HP laptop).

I think we should probably  have some more "usb" or "80211" modules (associated with those 2) loaded  though, and I'm not seeing them in that new file "wpa_supplicant.txt"

I  will quote these parts of that same file here for reference on this  thread:

> **sudo lshw -C network**

  *-network  DISABLED      
       description: Wireless interface
        physical id: 1
       logical name: wlan0
       serial:  00:1c:10:e8:e9:77
       capabilities: ethernet physical wireless
        **configuration: broadcast=yes driver=ndiswrapper+netmw245  driverversion=1.56+Linksys**, A Division of Cisc link=no multicast=yes  wireless=IEEE 802.11g
-------------------------------------------------------------------------------
**iwconfig**

lo         no wireless extensions.

eth0      no wireless extensions.

wlan0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed   Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit  Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B    Fragment thr=2346 B   
          Power Management:off
           Link Quality:0  Signal level:0  Noise level:0
          Rx invalid  nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive  retries:0  Invalid misc:0   Missed beacon:0
There is  some interesting stuff in the other file "error.txt" that makes it look  like the wlan0 wireless interface is trying to connect for a while and  then gives up.   I'll post some snippets of what I noticed below:

> State:  DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate:  operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL:  External notification - portEnabled=0
EAPOL: External notification -  portValid=0
[B]State: DISCONNECTED -> SCANNING
Starting AP  scan (broadcast SSID)
Trying to get current scan results first  without requesting a new scan to speed up initial association[/B]
Received  1612 bytes of scan results (6 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting  BSS from priority group 0
[B]Try to find WPA-enabled AP
0:  00:1a:2b:15:2c:96 ssid='Comtrend' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
    skip - SSID mismatch
1: 00:1e:e5:4b:a6:a3 ssid='casa' wpa_ie_len=28  rsn_ie_len=24 caps=0x11
   selected based on WPA IE
   selected  WPA AP 00:1e:e5:4b:a6:a3 ssid='casa'
Trying to associate with  00:1e:e5:4b:a6:a3 (SSID='casa' freq=2437 MHz)[/B]
[COLOR=Red]**Cancelling  scan request**[/COLOR]
WPA: clearing own WPA/RSN IE
Automatic  auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected  cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP  WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00  50 f2 04 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: set AP RSN IE -  hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02  01 00 00 0f ac 02 0c 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA:  using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set  own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2  02 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured -  skip key clearing
wpa_driver_wext_set_drop_unencrypted
**State:  SCANNING -> ASSOCIATING**
wpa_driver_wext_set_operstate:  operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
[B]Association  request to the driver failed
Setting authentication timeout: 5 sec 0  usec[/B]
EAPOL: External notification - EAP success=0
EAPOL:  External notification - EAP fail=0
EAPOL: External notification -  portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
EAPOL:  disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
**RTM_NEWLINK,  IFLA_IFNAME: Interface 'wlan0' added**
Wireless event: cmd=0x8b06  len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
**RTM_NEWLINK,  IFLA_IFNAME: Interface 'wlan0' added**
Wireless event: cmd=0x8b04  len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
**RTM_NEWLINK,  IFLA_IFNAME: Interface 'wlan0' added**
Wireless event: cmd=0x8c07  len=93
...
State: DISCONNECTED -> SCANNING
Starting AP scan  (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL:  startWhen --> 0
EAPOL: disable timer tick
[COLOR=Red]**^CCTRL-EVENT-TERMINATING  - signal 2 received**[/COLOR]
[B]Removing interface wlan0
State:  SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate  0->0 (DORMANT)[/B]
WEXT: Operstate: linkmode=-1, operstate=5
No  keys have been configured - skip key clearing
EAPOL: External  notification - **portEnabled=0**
EAPOL: External notification - **portValid=0**
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
[B]No  keys have been configured - skip key clearing
Removed BSSID  00:1e:e5:4b:a6:a3 from blacklist (clear)
Removed BSSID  00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request[/B]
Cancelling  authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
It  looks like ndiswrapper is trying to work that "wlan0" connection and is  seeing 2 wireless networks- "Comtrend" and "casa" but the WPA is not  allowing the authentication for whatever reason.  Also "casa" shows to  be at a frequency of **2437 MHz**, so ubuntu is at least seeing that  wireless router.

There are several flavors of WPA security- can  you go into the wireless router setup and see exactly what options that  your router gives you?  Often, Linux will give you more security options  that the wireless router will.

Have you tried disabling WPA and  running an unsecured "open" network just to see if that WUSB300N will  connect under wlan0- I suspect that it will from the way those text  files look.

This is probably just a configuration error (but I  haven't used ndiswrapper for a long time).

Just as a thought-  what versions of the wireless driver files are you using?  Can you see  the properties or choose "edit" from System > Administration >  Windows Wireless Drivers to see what is actually loaded?  I have seen  where ndiswrapper is extremely picky about which files you use (64-bit  XP vs. 32-bit XP vs. 64-bit Vista vs. 32-bit Win7, etc.)

Looking  at Linksys' website, there is only one hardware version of that WUSB300N  (so that is a lucky thing):

[http://www.linksysbycisco.com/US/en/support/WUSB300N/download](http://www.linksysbycisco.com/US/en/support/WUSB300N/download)

[http://www.linksysbycisco.com/US/en/support/WUSB300N](http://www.linksysbycisco.com/US/en/support/WUSB300N)

Are  you able to locate the actual driver files from your working XP, Vista, or Win7 in  Device Manager and copy those to a USB drive?  Perhaps if you take the  .INF and .SYS files directly from the working Windows location and plug  those into ndiswrapper we will have better luck.  (I'm considering the  same thing to test my ubuntu for better speed with ndiswrapper).

Again, that shows to be a 32-bit Karmic Koala 9.10 ubuntu, so you will want 32-bit versions of the Windows driver files for that WUSB300N.

edit:  On that "Chicony electronics" thing, I don't find 04f2:0210 in a quick search, but there were hits at these 2 websites:

[https://fedorahosted.org/hwdata/browser/usb.ids?rev=9fe002b2873ddc29b8c01768f9b93095012c3491](https://fedorahosted.org/hwdata/browser/usb.ids?rev=9fe002b2873ddc29b8c01768f9b93095012c3491)

[http://www.wireless-driver.com/knowledge/tips/list-of-usb-ids.htm](http://www.wireless-driver.com/knowledge/tips/list-of-usb-ids.htm)

---

### Post by cjsegninir on 2010-03-07
Hi [northd_tech]("http://ubuntuforums.org/member.php?u=938429"),
I was out for a while, but yesterday I finally came and checked the computer again.
At the end I couldn't find a solution, so simply changed the security from WPA2 to WPA. I didn't make any change and it worked!
Apparently there is no support for WPA2 yet, but the WPA instructions you gave me above worked perfectly.
Thanks a lot
Regards.

---

