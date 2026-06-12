---
title: "Can't connect faster than 54Mbit to 802.11n"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by bthoward on 2013-05-28
I remember that we had this issue a while back when disable_11n was in place but that had been fixed for me on this system and at some point it has returned.

Laptop is a Sony Vaio VPCZ12CGX running Ubuntu 13.04 and when connecting with an access point that has provided up to 270+Mbit connections before I only get 54Mbit connections now.  

brett@lappy:~$ lspci | grep "Centrino"
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

I've also attached the information from a recent run of of a script that gives information on wireless stuff....

I've tried unloading my modules and reloading them with several different options (mainly just changing the 11n_disable parameter)...  You'll see some of that happening at the end of my dmesg...

Anyway any ideas or help would be greatly appreciated!

Thanks

~Brett

---

### Post by chili555 on 2013-05-28
> [58885.993230] iwlwifi 0000:02:00.0 wlan0: [COLOR="#FF0000"]disabling HT as WMM/QoS is not supported by the AP[/COLOR]
[58885.993234] iwlwifi 0000:02:00.0 wlan0: [COLOR="#FF0000"]disabling VHT as WMM/QoS is not supported by the AP[/COLOR]What do you make of this?

I suspect it's a setting in the router that's holding you back. I use the same driver and get N speeds easily.> wlan0     IEEE 802.11abgn  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:D7:19:41:54:xx   
          [COLOR="#FF0000"]Bit Rate=180 Mb/s[/COLOR]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:376  Invalid misc:51   Missed beacon:0


---

### Post by ahallubuntu on 2013-05-28
~

---

### Post by chili555 on 2013-05-28
> **ahallubuntu said:**
> Make sure you are using WPA2 with AES if you use any sort of wireless security.  Otherwise, you'll be limited to 54Mbps.I believe this suggests he *is* using AES:> wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"howard5g"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008907f428
                    Extra: Last beacon: 16ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="#FF0000"]Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK[/COLOR]If either of you can confirm or deny, I'll be grateful.

---

### Post by bthoward on 2013-05-28
> **chili555 said:**
> What do you make of this?

```
[58885.993230] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[58885.993234] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
```

I suspect it's a setting in the router that's holding you back. I use the same driver and get N speeds easily.

I know that I've connected to this AP with over 54 Mbit before with WMM and QoS turned off before however when I turned these features on in the AP I now can connect at 270Mbit.  Transfer rates are greatly improved!  Went from 2.2MB/sec to around 10MB/sec.

WMM is Wifi Multimedia and its a method of performing QoS over Wifi.  Essentially allows you to prioritize certain types of traffic over others.  I had this disabled in the access point because I do all my QoS stuff in my firewall.  I have 3 different subnets (not including the WAN port) and all traffic between them is prioritized to not starve things that are crucial.  Its a bit over the top for a home network but when you have VoIP phones, crashplan backups, and a myth box that does 3 HD recordings at a time to an iSCSI NAS it doesn't hurt.  QoS in the firewall totally fixed the issue of the phone going to crap when people would start up torrents. ;)

Still wish I could get faster speeds with WMM off but for now I'll take it.

~Brett

---

### Post by bthoward on 2013-05-28
> **chili555 said:**
> I believe this suggests he *is* using AES:If either of you can confirm or deny, I'll be grateful.

Yes using AES.

---

### Post by chili555 on 2013-05-28
>  I have 3 different subnets (not including the WAN port) and all traffic between them is prioritized to not starve things that are crucial. Its a bit over the top for a home network but when you have VoIP phones, crashplan backups, and a myth box that does 3 HD recordings at a time to an iSCSI NAS it doesn't hurt. QoS in the firewall totally fixed the issue of the phone going to crap when people would start up torrentsA *bit* over the top?? Yikes!

In any event, I'm glad it's working. I've been studying the whole *11n_disable* issue for a while now and I'm glad to add your data to my collection.

---

### Post by bthoward on 2013-05-28
Just tested again using NFS rather than SMB to transfer files and over a 180Mbit connnection I just pulled files across at 15MB/sec.  I still have power saving turned on at the moment.  Not sure if turning that off would help or not but for now thats acceptable.

~Brett

---

### Post by chili555 on 2013-05-29
> **bthoward said:**
> Just tested again using NFS rather than SMB to transfer files and over a 180Mbit connnection I just pulled files across at 15MB/sec.  I still have power saving turned on at the moment.  Not sure if turning that off would help or not but for now thats acceptable.

~BrettIt's easy enough to change:```
sudo iwconfig wlan0 power off
```In this context, 'power' means power saving.

---

