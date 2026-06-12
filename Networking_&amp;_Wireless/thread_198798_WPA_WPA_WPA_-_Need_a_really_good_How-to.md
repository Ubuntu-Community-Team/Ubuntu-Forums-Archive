---
title: "WPA? WPA? WPA? - Need a really good How-to"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by nzruss on 2006-06-17
Hey all. 

I finally got wpa working and it was mighty simple:

I started with a fresh install of Dapper, 
Installed the network manager, 
Installed ndiswrapper, 
Rebooted.
Network manager recognized my wireless card. 
I clicked on it, it asked me for my WPA key, a simple cut and paste from the USB stick, and wa-la!!!! it worked.

Here is the expanded version:
--------------------------------

1.  Enable your universe and multiverse repositorys, by clicking > system > administration > Synaptic Package Manager. Then click the Settings tab, and select all the available repositorys. Click OK and exit.

2.  Wait a few seconds and you might get a few updates. Update your system.

3.  Click "applications > "add/remove", and in the search box type "network manager". 

3b. Look for Network manger (for gnome), then 'check' it and click "Apply". It should have a few dependencies which will install automatically.

4.  Once installed, you should see the network managers icon in your task bar. (If not, you may need to reboot (i think i did) - save this page to your desktop first)

5.  Click the new network manager icon, and you should see "wired network" and "wireless networks" if you have already installed your wireless driver, if not the ndiswrapper method is here... [http://www.ubuntuforums.org/showthread.php?t=190967](http://www.ubuntuforums.org/showthread.php?t=190967) (look below the ------- line)

6.  Your system should detect your wpa network automatically, and once selected it will ask for the pass phrase. Either type your pass-phrase, or paste the pre-shared key. 

6b. Make sure you note the first and last characters of your PSK before and after the paste. When I pasted, an exta non-ascii character appeared at the end, that I simply deleted.

You may also need to enter a password for your "key-ring", and your done.

THAT IS IT!!!!!

-----------------------------------------------------------------------
-----------------------------------------------------------------------

Below is my origional request for help. Hopefully the above helps someone too!

-----------------------------------------------------------------------
-----------------------------------------------------------------------
I cant get my Ubuntu machine to access my WPA network... Can you help?

Firstly, I've searched the forums at length and followed the WPA HowTo in the Wiki as best I can, but no luck. (BTW: That how-to needs to be better broken down)

I have a linksys wireless card that works fine on my home network when its open, but not when I set WPA. My windows machine works fine with the WPA, just not this Ubuntu machine (Dapper). I'm using NDIS Wrapper, and it works fine.

I have network manager installed, but dont have an option for entering a WPA key, only WEP. 

I've loaded wpasupplicant, and my /etc/wpa_supplicant looks like this:

```

#WPA at home
ap_scan=2

network={
       ssid=DrEvilsHome
       scan_ssid=1
       proto=WPA
       key_mgt=WPA-PSK
       pairwise=TKIP
   psk=asdfasdfdsasdfasdfasdfasdfV6qkE9h6I4BiAleoPHSHD1VzWyoMEqKLpmj9z
}

```

and my /etc/default/wpasupplicant looks like this:

```

ENABLED=1
  OPTIONS="-iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w"

```

When I do a scan (sudo iwlist wlan0 scan), I get:

 > sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:24:86:E2
                    ESSID:"DrEvilsHome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0
     Extra:wpa_ie=dd180050f20101110050f20201000050f5551000050f2020000



I'm after a really good how-to, or an application (frontend) that can take the pain out of this for me. I'm going to keep working it, and once i've got it sorted, am happy to write a full how-to or edit the wiki. 

Ive searched these and the debian forums, and tried them all. Any help appreciated........ Ive been at it 2 days...

---

### Post by shorty0927 on 2006-06-17
Do you have this saved as /etc/wpa_supplicant, or /etc/wpa_supplicant.conf?  I found that you do need to create a /etc/wpa_supplicant.conf to get the WPA to work...

```

#WPA at home
ap_scan=2

network={
       ssid=DrEvilsHome
       scan_ssid=1
       proto=WPA
       key_mgt=WPA-PSK
       pairwise=TKIP
   psk=asdfasdfdsasdfasdfasdfasdfV6qkE9h6I4BiAleoPHSHD1VzWyoMEqKLpmj9z
}

```

You also may need to use wpa_passphrase (a little tool that came with wpa_supplicant).  It's a command line tool that takes your passphrase and ssid and turn them into another format (binary?).  My WPA wouldn't work without having to do this.

```
wpa_passphrase <your ssid> <your passphrase>
```

I can't remember if this has to be done with sudo or not, but when you get the result, copy and paste it into the psk field in /etc/wpa_supplicant.conf.

---

### Post by nzruss on 2006-06-17
I got it working. I reinstalled Dapper, Installed the network manager, installed ndiswrapper, rebooted. 

Network manager recognized my wireless card. I clicked on it, it asked me for my WPA key, a simple cut and paste from the USB stick, and wa-la!!!! it worked. 

I'll write up how I got this all done tomorrow / Monday ( here ---http://www.ubuntuforums.org/showthread.php?t=190967 )

I think that all the early messing around (with scripts etc) stuffed up a few things. The clean install must have helped. 

Cheers for the tips though. 

NZR

---

