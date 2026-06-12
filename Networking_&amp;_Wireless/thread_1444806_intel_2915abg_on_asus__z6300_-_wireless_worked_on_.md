---
title: "intel 2915abg on asus  z6300 - wireless worked on 9.04 but no joy in 9.10"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by thane1 on 2010-04-01
Floundered my way through network manager, then wicd, then network manager in 9.04 and got wireless working, although I'm still not exactly sure how.  Now that I've switched to 9.10 however, I'm at a total loss as to, what has prevented me from enabling wireless support.  Router linksys wrt-54g, asus z6300 with intel 2915abg wireless card.  Kernal is 32 bit 2.6.31-20-generic-pae with all updates done.  Some terminal outputs as follows - exact except for x'ing out the MAC address data:(many thanks in advance)
twoblade@twoblade-laptop:~$ nm-tool 

NetworkManager Tool 

State: disconnected 

- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            skge 
  State:             unavailable 
  Default:           no 
  HW Address:        00:13:D4:1B:B5:68 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


- Device: eth1 ----------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ipw2200 
  State:             disconnected 
  Default:           no 
  HW Address:        00:0E:35:85:17:B4 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 


twoblade@twoblade-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

twoblade@twoblade-laptop:~$ lsmod | grep ipw2200 
ipw2200               140228  0 
libipw                 43148  1 ipw2200 
lib80211                6432  2 ipw2200,libipw 
twoblade@twoblade-laptop:~$ dmesg | grep ipw2200 
[   10.677004] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq 
[   10.677009] ipw2200: Copyright(c) 2003-2006 Intel Corporation 
[   10.677118] ipw2200 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   10.677226] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection 
[   10.677278] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw 
[   11.063022] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels) 
twoblade@twoblade-laptop:~$ iwlist 
Usage: iwlist [interface] scanning [essid NNN] [last] 
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
twoblade@twoblade-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

eth1      Scan completed : 
          Cell 01 - Address: 00:14:BF:1C:66:2C 
                    ESSID:"" 
                    Protocol:IEEE 802.11g 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=99/100  Signal level=-22 dBm  
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    Extra: Last beacon: 5912ms ago 

twoblade@twoblade-laptop:~$ sudo modprobe ipw2200 
twoblade@twoblade-laptop:~$ dmesg | grep ipw 
[   10.677004] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq 
[   10.677009] ipw2200: Copyright(c) 2003-2006 Intel Corporation 
[   10.677118] ipw2200 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   10.677226] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection 
[   10.677278] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw 
[   11.063022] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)

---

### Post by chili555 on 2010-04-01
Looks perfect to me, except you haven't asked it to connect to your access point yet. Is this telling us that the router's SSID is hidden?> eth1 Scan completed :
Cell 01 - Address: 00:14:BF:1C:66:2C
[COLOR="Red"]ESSID:""[/COLOR]
Protocol:IEEE 802.11g Have you clicked the Network Manager icon and selected 'Connect to Hidden Wireless Network?'

I also don't like this:> eth1 unassociated ESSIDff/any
Mode:Managed Channel=0 Access Point: Not-Associated
[COLOR="Red"]Bit Rate:0 kb/s[/COLOR] Please do:```
sudo iwconfig eth1 rate 54M
```Post back and let us know.

---

### Post by thane1 on 2010-04-02
Yes my essid is hidden.  Entering sudo iwconfig eth1 rate 54M as requested didn't lead to any visible output in Terminal.  Also left clicking on the network manager icon shows "Wireless Networks" with a grayed out "disconnected" below it.  Thanks.

---

### Post by thane1 on 2010-04-02
This is just weird.  I tried the sudo iwconfig eth1 rate 54M again with again no output coming back.  So I restarted the laptop to restart the network connection and now I don't have and cannot add a wireless connection listing in network manager under the Wireless heading.  However I now have a new connection in wired showing ( called ifupdown (eth1) and if I highlight it, the edit and delete options are grayed out.

---

### Post by chili555 on 2010-04-02
From my previous post:> Have you clicked the Network Manager icon and selected 'Connect to Hidden Wireless Network?'Please see attached. Is that option available? Did you try?

---

### Post by thane1 on 2010-04-02
Thanks chili555;
Just finished off a fresh start and a report of what I'd done.  This morning have just reinstalled 9.10 and all available updates, since I didn't like the look of whatever I did to the wireless last night.  Should I try network manager or install wicd?  I'm still using nm at this point.  Asus Z6300 with Intel PRO/Wireless 2915ABG [Calexico2]
Wireless would be on eth1
Router linksys wrt54g using wpa2 personal with essid and encryption key
Fixed ip addresses on all computers in house except laptop, which I've run on dhcp since my isp says it requires dhcp and mtu of 1024 (I would however prefer to run laptop on static if possible.
Will only run laptop via router to access web but not other computers

I did have wireless working in 9.04 in the past after a lot of fumbling, although I'm not sure exactly how I did it.

To answer your last question, yes I did try that with no success.  Have just reentered my wireless info in new 9.10 installationn's network manager with a network name (not the ssid), wireless security of wpa & wpa2 personal, password (my router's wpa shared key entered in ascii and not in hex), mode infrastructure, bssid left blank, mac address - my router address, mtu of 1024, ipv4 settings method is automatic (DHCP), and I'm not sure if I need to enter anything in the ipv4 routes, since my isp settings are already entered in the router (so I haven't entered anything there.)
To be on the safe side I then did a sudo /etc/init.d/networking restart and got an ok on that.  I just tried to connect to a hidden network in network manager with the network name (not the ssid), wpa2 and my encryption key.  No joy I'm afraid. ???

---

### Post by thane1 on 2010-04-02
Have just seen one of the neighbour's wireless networks show up in the nm window, so I know nm is at least ackowledging the presence of valid networks.

---

### Post by thane1 on 2010-04-02
Got it -- sort of...  I entered my ssid in place of the name I used for network name and it worked.  However even though this is a hidden network, does that not pose a security risk with wardriving?  I would have thought the ssid could be scanned by anyone in the local area with the right knowledge/equipment.  My 9.04 wireless instl'n had a separate profile name showing as I recall (maybe that was on wicd).

---

### Post by chili555 on 2010-04-02
> I've run on dhcp since my isp says it requires dhcp and mtu of 1024 (I would however prefer to run laptop on static if possible.What is it we used to say down in East Texas? Tell me another tall tale! The TCP/IP protocol executed by Linux is no different than that used by Windows or Mac. Moreover, it is the router that gets an IP address from your cable or DSL modem, so the ISP sees the router, not your Ubuntu laptop. 

Now, I am quite sure that your ISP wants the router set up to get a dynamic IP address from the ISP, but there is no way that I know of, that they know or care what computers are connected to the router. The MTU specification is questionable, as well. I'd take it up to 1492 and see what, if anything happens.

By the way, are you aware that your Linksys WRT54G router runs Linux?> I just tried to connect to a hidden network in network manager with the network name (not the ssid)What is the difference between the network name and the ESSID? I am not aware of any.> I would have thought the ssid could be scanned by anyone in the local area with the right knowledge/equipment.It can, hidden or not. You have a firewall in the router, you use WPA2, you have a firewall in the laptop and you run as a user and not root. A determined hacker, given enough time, can get through all of that. However, why??

There are unencrypted networks in my neighborhood as well as easily cracked WEP networks. Even more insecure, most of them run Windows! If the hacker is willing to put weeks and months into the job, why not just go straight to the bank; that's where the real money is.

The only truly secure computer is turned off, detached from the network and locked in a safe...guarded by machine guns...and buried in the Mojave desert...maybe.

---

### Post by thane1 on 2010-04-02
Many thanks chili555 for your help!  I will try bumping up the mtu and I'll also play with static ip to get that working.

---

### Post by chili555 on 2010-04-02
> **thane1 said:**
> Many thanks chili555 for your help!  I will try bumping up the mtu and I'll also play with static ip to get that working.I am very confident it will be fine. Then you will know a lot about the wunnerful folks in Customer Support down at the good ole ISP.

---

