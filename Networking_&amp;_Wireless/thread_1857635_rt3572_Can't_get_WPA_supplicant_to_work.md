---
title: "rt3572: Can't get WPA_supplicant to work"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by ohmysql on 2011-10-10
I just installed an rt3572sta driver, and I can't get the wpa_supplicant to work. Here are a few relevant lines from the syslog:

```
Oct 10 17:14:14 cool1-ubuntu wpa_supplicant[849]: Association request to the driver failed
Oct 10 17:14:14 cool1-ubuntu NetworkManager[808]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 10 17:14:14 cool1-ubuntu kernel: [31107.272402] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Oct 10 17:14:14 cool1-ubuntu kernel: [31107.272785] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Oct 10 17:14:14 cool1-ubuntu kernel: [31107.272996] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Oct 10 17:14:15 cool1-ubuntu NetworkManager[808]: <warn> (ra0): link timed out.
Oct 10 17:14:19 cool1-ubuntu wpa_supplicant[849]: Authentication with 00:16:b6:b3:a0:10 timed out.
Oct 10 17:14:19 cool1-ubuntu NetworkManager[808]: <info> (ra0): supplicant connection state:  associating -> disconnected
Oct 10 17:14:19 cool1-ubuntu NetworkManager[808]: <info> (ra0): supplicant connection state:  disconnected -> scanning

```

When I installed rt3572, I changed the config.mk to look like this:
```

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

Any ideas? I'm using a Cisco AM10.

I'm able to scan for networks, but the system just repeatedly asks for my password. I'm not sure what wpa_supplicant needs from the card to function. But I know I have gotten the card to work in windows before with our router. Don't make me go back to Microsoft, I'm begging you! :)

OMS

---

### Post by praseodym on 2011-10-10
Do you use Wicd with the supplicant? In that case deactivate the network-manager in "autostart" and login again. Maybe uninstalling th NM helps, too.

---

### Post by ohmysql on 2011-10-10
> **praseodym said:**
> Do you use Wicd with the supplicant? In that case deactivate the network-manager in "autostart" and login again. Maybe uninstalling th NM helps, too.

Good question. I don't use Wicd. Is that a suggestion, though?

---

### Post by praseodym on 2011-10-10
Give it a try (includes the "Add-On" from one of the developers for more and several encryption templates):


```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose "ra0" as interface name and "wext" as driver.

---

### Post by ohmysql on 2011-10-10
> **praseodym said:**
> Give it a try (includes the "Add-On" from one of the developers for more and several encryption templates):


```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```Choose "ra0" as interface name and "wext" as driver.

Hmm, it says I have a bad password. I'm almost positive my password is correct. Here is the message from syslog around that time:

```
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.617137] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880823] RTMP_TimerListAdd: add timer obj ffffc9000dc4b638!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880832] RTMP_TimerListAdd: add timer obj ffffc9000dc4b6b0!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880838] RTMP_TimerListAdd: add timer obj ffffc9000dc4b728!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880845] RTMP_TimerListAdd: add timer obj ffffc9000dc4b5c0!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880851] RTMP_TimerListAdd: add timer obj ffffc9000dc4b458!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880856] RTMP_TimerListAdd: add timer obj ffffc9000dc4b4d0!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880861] RTMP_TimerListAdd: add timer obj ffffc9000dc15940!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880866] RTMP_TimerListAdd: add timer obj ffffc9000dc045f8!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880871] RTMP_TimerListAdd: add timer obj ffffc9000dc04678!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880875] RTMP_TimerListAdd: add timer obj ffffc9000dc15ad0!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880881] RTMP_TimerListAdd: add timer obj ffffc9000dc15850!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.880887] RTMP_TimerListAdd: add timer obj ffffc9000dc15a50!
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.882257] -->RTUSBVenderReset
Oct 10 22:46:31 cool1-ubuntu kernel: [  187.882381] <--RTUSBVenderReset
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.168711] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.168730] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.169298] Key1Str is Invalid key length(0) or Type(0)
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.169342] Key2Str is Invalid key length(0) or Type(0)
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.169386] Key3Str is Invalid key length(0) or Type(0)
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.169431] Key4Str is Invalid key length(0) or Type(0)
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.170274] 1. Phy Mode = 5
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.170278] 2. Phy Mode = 5
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.170283] NVM is Efuse and its size =2d[2d0-2fc] 
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.218023] phy mode> Error! The chip does not support 5G band 8!
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.218242] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.222273] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.241135] 3. Phy Mode = 9
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.262140] MCS Set = ff ff 00 00 01
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.272863] <==== rt28xx_init, Status=0
Oct 10 22:46:31 cool1-ubuntu kernel: [  188.274383] 0x1300 = 00064300
Oct 10 22:46:33 cool1-ubuntu avahi-daemon[849]: Joining mDNS multicast group on interface ra0.IPv6 with address fe80::6a7f:74ff:fee3:f64b.
Oct 10 22:46:33 cool1-ubuntu avahi-daemon[849]: New relevant interface ra0.IPv6 for mDNS.
```

---

### Post by praseodym on 2011-10-11
Uninstall the network-manager completely:

```
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo apt-get install --reinstall wicd
sudo service wicd restart
```

---

### Post by ohmysql on 2011-10-12
> **praseodym said:**
> Uninstall the network-manager completely:

```
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo apt-get install --reinstall wicd
sudo service wicd restart
```

I tried this. It said I still have a "bad password."

Now this morning I tried again and IT WORKS!!!

Do you know how to get wicd to appear on the top right hand side like Network Manager does?

I am writing you from a working AM10. I'll post again if this freezes. But I think this might just end up working!! Fingers crossed.

Like, Oh My SQL!!

PS I'll come back and mark this as solved in a few days if everything continues to work.

---

### Post by praseodym on 2011-10-12
Hm, I dont use Wicd, but you can try : Right click->Add applet or so and look if there is sth. to add.

---

### Post by ohmysql on 2011-10-12
Oh yeah, in 11.04 you don't really have applets in the same way. In fact, I'm really not sure how network manager got up there.

---

### Post by jawilljr on 2011-10-12
> **ohmysql said:**
> Oh yeah, in 11.04 you don't really have applets in the same way. In fact, I'm really not sure how network manager got up there.

You need to add Wicd to systray's whitelist...[here is one way to do it](https://bugs.launchpad.net/wicd/+bug/761326/comments/2)

Jerry

---

### Post by ohmysql on 2011-10-13
Very helpful, now that's working - I now have wicd in the tray. Thanks!

I wonder why wpa_supplicant wasn't working. But in any case, this workaround is working.

---

### Post by ohmysql on 2011-10-17
This has totally stopped working on 11.10. I'm now getting a "Bad Password" error on wicd and network manager still isn't playing with the WPA supplicant. HELP!

---

### Post by praseodym on 2011-10-18
Uninstall the NM again?

---

### Post by ohmysql on 2011-10-18
Oh, yes, sorry, that last post was confusing. Thank you.

When I upgraded, I'm aware that the system automatically installed NM again. Obviously wicd stopped working. I then uninstalled NM, "bad password." I uninstalled wicd, reinstalled NM. WPA_supplicant wasn't working. I then realized I hadn't uninstalled network-manager-pptp, so I reinstalled wicd. "Bad password."

Well, I just got a series of updates from Canonical (they seem to focus on updating the graphics as far as I can tell, not fixing bugs, but I'll keep working on this).

---

### Post by ohmysql on 2011-10-20
Dang, still no luck.

---

### Post by praseodym on 2011-10-20
Dou you have blanks and/or strange letters in your key? How long is the key? Please show the outputs of:

```
sudo iwlist scan [COLOR="Red"]#which is your network here?[/COLOR]
iwconfig
```

---

### Post by ohmysql on 2011-10-20
> **praseodym said:**
> Dou you have blanks and/or strange letters in your key? How long is the key? Please show the outputs of:

```
sudo iwlist scan [COLOR=Red]#which is your network here?[/COLOR]
iwconfig
```

Great questions.

The key is 40 characters long. And yes, there are spaces in it. The only other strange characters would be an apostrophe and a period. It is working for my sister's ubuntu, and other wireless cards, but still, it could be the space, ', or . that is throwing things off.

Here is the output of your commands:

```
sudo iwlist scan #which is your network here?
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:E7:F9:FC:B6
                    Protocol:802.11b/g/n
                    ESSID:"SONYABLADE"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=0/100  Signal level=-101 dBm  Noise level=-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: 00:16:B6:B3:A0:10
                    Protocol:802.11b/g
                    ESSID:"2325"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=-21 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

The latter is our network.

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3071STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` Thank you for your persistence. I have a feeling we're getting close.

OMS

---

### Post by praseodym on 2011-10-21
Which ESSID is it? "SONYABLADE" or "2325"? Anyway: Set up a wpa_supplicant config file:

```
sudo touch /etc/wpa_supplicant/wpa_supplicant.conf       #create the file
sudo chmod 600 /etc/wpa_supplicant/wpa_supplicant.conf   #read only for root
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
Insert:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1

ap_scan=1

network={
        ssid="[COLOR="Red"]YourESSID[/COLOR]"
        scan_ssid=1
        key_mgmt=NONE
        wep_tx_keyidx=0
        wep_key0="[COLOR="Red"]Your-Key[/COLOR]"
[COLOR="Lime"]        auth_alg=SHARED
        priority=2[/COLOR]
}
```
If the encryption is "WEP-shared" add additionally the green lines, otherwise not.
Restart your connection:

```
sudo /etc/init.d/networking restart
```

---

### Post by ohmysql on 2011-10-21
> **praseodym said:**
> Which ESSID is it? "SONYABLADE" or "2325"? Anyway: Set up a wpa_supplicant config file:

We're 2325. Also, it's a WPA2 connection. A lot of the code you gave me said "wep" - will that still work for a WPA2 encryption?

Also, when I put in the code you suggested, I put in the password as is, spaces and ' and . and everything. Is that the way I should've done it?

> ```
sudo touch /etc/wpa_supplicant/wpa_supplicant.conf       #create the file
sudo chmod 600 /etc/wpa_supplicant/wpa_supplicant.conf   #read only for root
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```Insert:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1

ap_scan=1

network={
        ssid="[COLOR=Red]YourESSID[/COLOR]"
        scan_ssid=1
        key_mgmt=NONE
        wep_tx_keyidx=0
        wep_key0="[COLOR=Red]Your-Key[/COLOR]"
[COLOR=Lime]        auth_alg=SHARED
        priority=2[/COLOR]
}
```If the encryption is "WEP-shared" add additionally the green lines, otherwise not.
Restart your connection:

```
sudo /etc/init.d/networking restart
```

Ok, I did what you said - I didn't include the green lines because we use WPA2. So far this doesn't seem to have worked. Let me know if the config file is right for WPA2 and if I need to put the key in binary before pasting it in the file.

OMS

---

### Post by praseodym on 2011-10-21
Oh, sorry, for WPA2 it needs to be:

```
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
Change the complete file to:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1

ap_scan=1

network={
        ssid="YourESSID"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=TKIP
        psk="YourKey"
}
```

Start the debug-mode with:

```
sudo killall wpa_supplicant
sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d > wpadebug.txt
```
Stop the debugger after ca. 30 seconds wich "CTRL+C" and upload the file wpadebug.txt

---

### Post by ohmysql on 2011-10-21
Three questions for you:


[LIST=1]
[*]For the PSK, should I type out our wireless password, or use wpa_passphrase? FYI For this try I used wpa_passphrase to find the binary version of our password, and that's what I put in PSK.
[*]I'm assuming I should do sudo /etc/init.d/networking restart before I kill the wpa_supplicant. The system says I should use sudo service wicd restart - is that better?
[*]When I did sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d > wpadebug.txt I got:
```
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
```Let me know if that's bad :)
[/LIST]
This file I'm attaching doesn't contain my passphrase does it? Well, anyway, I've attached it here. I hope this helps.

Let me know if you'd like me to try the same thing with Network Manager too. I'm using wicd as instructed.

OMS

PS The file was too large to attach so I pastebinned it here:

[http://pastebin.com/Pp3nwcNi](http://pastebin.com/Pp3nwcNi)

> **praseodym said:**
> Oh, sorry, for WPA2 it needs to be:

```
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```Change the complete file to:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1

ap_scan=1

network={
        ssid="YourESSID"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=TKIP
        psk="YourKey"
}
```Start the debug-mode with:

```
sudo killall wpa_supplicant
sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d > wpadebug.txt
```Stop the debugger after ca. 30 seconds wich "CTRL+C" and upload the file wpadebug.txt

---

### Post by ohmysql on 2011-10-27
Did you get the attachment? What did you think?

Also, I was wondering - I have the password for the WPA entered in wicd and in the wpa_supplicant file. Should I delete it from wicd? Should I try network manager again?

OMS

---

### Post by praseodym on 2011-10-27
Sorry for not responding. I didnt see anything unusual in the output, maybe because Wicd was still running?! Try again with:

```
sudo service wicd stop
sudo service network-manager stop [COLOR="Red"]#if still installed[/COLOR]
sudo killall wpa_supplicant
sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d > wpadebug2.txt
```

---

### Post by ohmysql on 2011-10-27
> **praseodym said:**
> Sorry for not responding. I didnt see anything unusual in the output, maybe because Wicd was still running?! Try again with:

```
sudo service wicd stop
sudo service network-manager stop [COLOR=Red]#if still installed[/COLOR]
sudo killall wpa_supplicant
sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d > wpadebug2.txt
```

Thanks. I feel like we're really close here. I ran the stuff you said (network manager is long gone).

Here's the pastebin w/ the latest and greatest:

[http://pastebin.com/3naeDfbC](http://pastebin.com/3naeDfbC)

Here is interfaces by the way, not sure if this helps:

```
auto lo
iface lo inet loopback
```Let me know if I need to set something up with ra0.

OMS

PS In terminal it continues to say:

```
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported 
ioctl[SIOCSIWGENIE]: Operation not supported
```

---

### Post by praseodym on 2011-10-27
Add the following lines to the interfaces:

```
auto ra0
iface ra0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
and restart the network:

```
sudo ifdown ra0
sudo ifup ra0
```
The key you added to the ".conf" is in "" and in uncoded text?

---

### Post by ohmysql on 2011-10-27
> **praseodym said:**
> Add the following lines to the interfaces:

```
auto ra0
iface ra0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```and restart the network:

```
sudo ifdown ra0
sudo ifup ra0
```The key you added to the ".conf" is in "" and in uncoded text?

Let's say for the sake of argument that my wifi password was this (which it's not):

  	 	 	 	 	 	  ```
Jim carries Jane's purse wherever he is.
```
 
Then this is what my .conf file would look like:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1

ap_scan=1

network={
        ssid="2325"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=TKIP
        #psk="Jim carries Jane's purse wherever he is."
        psk=47580553bc1040e0f4a79903d1c88eea555960533e1afd68273d67bb1b08345d
}

```

Does that look good to you?

I added the two lines you suggested to /etc/network/interfaces

It's still saying I have a bad password. Let me know if my .conf file looks good. I'm going to try stopping wicd and then network manager with the new wpa_supplicant stuff. I'll let you know if I have any luck. I'm guessing I won't, so you won't hear anything. Let me know.

OMS

---

### Post by ohmysql on 2011-10-27
Do you have any thoughts as to why the wpa_supplicant isn't associating with my wireless driver? It seems to have worked temporarily in 11.04 and then stopped completely in 11.10.

I've definitely recompiled my wireless driver in 11.04. Do you know if I need to recompile wpa_supplicant?

Also, now when I do sudo ra0 ifup it says:

```
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
```

---

### Post by praseodym on 2011-10-27
There shouldnt be blanks in the key. Uncoded PW in "", Hex-form without "" as shown. How did you convert the key?

```
wpa_passphrase 2325 Jim carries Jane's purse wherever he is.
```
would be the way. As you see, blanks are not good in any case

---

### Post by ohmysql on 2011-10-27
> **praseodym said:**
> There shouldnt be blanks in the key. Uncoded PW in "", Hex-form without "" as shown. How did you convert the key?

```
wpa_passphrase 2325 Jim carries Jane's purse wherever he is.
```would be the way. As you see, blanks are not good in any case

Oh sure, it can work, you just put quotes around it, like this:

```
$ wpa_passphrase 2325 "Jim carries Jane's purse wherever he is."
network={
    ssid="2325"
    #psk="Jim carries Jane's purse wherever he is."
    psk=47580553bc1040e0f4a79903d1c88eea555960533e1afd68273d67bb1b08345d
}
```
Just to demonstrate that the system ignores the quotation marks: ```

$ wpa_passphrase 2325 yoyoyoyo
network={
    ssid="2325"
    #psk="yoyoyoyo"
    psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
}
$ wpa_passphrase 2325 "yoyoyoyo"
network={
    ssid="2325"
    #psk="yoyoyoyo"
    psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
}
```Besides, this password is working on my sister's Ubuntu laptop, and my other 11.04 ubuntu laptop. So I don't think the spaces or anything to do with the password itself is the problem.

OMS

---

### Post by praseodym on 2011-10-28
Try it like this 

```
    psk="yoyoyoyo"
    [COLOR="Red"]#[/COLOR]psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
```

instead of:

```
    [COLOR="Red"]#[/COLOR]psk="yoyoyoyo"
    psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
```

---

### Post by ohmysql on 2011-10-28
> **praseodym said:**
> Try it like this 

```
    psk="yoyoyoyo"
    [COLOR=Red]#[/COLOR]psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
```instead of:

```
    [COLOR=Red]#[/COLOR]psk="yoyoyoyo"
    psk=ba311592e5b1cd1f2b235648b1597a6104ec2280d8c4a883f72b5ac87176373c
```

Ok, I've tried it both ways.

Do I need to reset something when I change the .conf file? What I've been doing is altering the .conf file and then doing sudo /etc/init.d/networking restart

Anyway, no luck, I've tried it both ways.

But last time, I got the wpa working without a .conf file. I bet we don't need it. In fact, it should be getting the password from wicd, right? What's the point of configuring the .conf file?

I guess I could debug that way. Mostly the debugger says it's not allowing me to connect w/ the driver.

OMS

---

### Post by praseodym on 2011-10-28
Add the line

```
        wpa-driver wext
```

to the "interfaces" and try it again

---

### Post by ohmysql on 2011-10-28
> **praseodym said:**
> Add the line

```
        wpa-driver wext
```to the "interfaces" and try it again

This is my current interfaces file:

```
auto lo
iface lo inet loopback
auto ra0
iface ra0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
    wpa-driver wext
```

Thanks, I tried that, did init restart. No luck.

I don't think that kind of thing is going to work because when I debut the wpa_supplicant it claims it can't associate with the driver.

I think we'll need to tackle that part of the problem. But I'm open to other suggestions, obviously.

OMS

---

### Post by ohmysql on 2011-11-01
I'm still getting bad password messages but you know, I'm not sure but I think maybe the WPA_supplicant is now working. That's pretty magical. I just recompiled the driver (I had recompiled it before when I upgraded to 11.10) and now I'm getting completely different error messages.

Let me know what you think. Here is dmesg - only the part after I try to connect with the wireless device (the bad password error), it gives:

```
   	 	 	 	 	 	  [ 5144.967154] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5145.231052] RTMP_TimerListAdd: add timer obj ffffc9000ded2638! 
 [ 5145.231063] RTMP_TimerListAdd: add timer obj ffffc9000ded26b0! 
 [ 5145.231069] RTMP_TimerListAdd: add timer obj ffffc9000ded2728! 
 [ 5145.231075] RTMP_TimerListAdd: add timer obj ffffc9000ded25c0! 
 [ 5145.231081] RTMP_TimerListAdd: add timer obj ffffc9000ded2458! 
 [ 5145.231086] RTMP_TimerListAdd: add timer obj ffffc9000ded24d0! 
 [ 5145.231091] RTMP_TimerListAdd: add timer obj ffffc9000de9c940! 
 [ 5145.231096] RTMP_TimerListAdd: add timer obj ffffc9000de8b5f8! 
 [ 5145.231101] RTMP_TimerListAdd: add timer obj ffffc9000de8b678! 
 [ 5145.231106] RTMP_TimerListAdd: add timer obj ffffc9000de9cad0! 
 [ 5145.231112] RTMP_TimerListAdd: add timer obj ffffc9000de9c850! 
 [ 5145.231117] RTMP_TimerListAdd: add timer obj ffffc9000de9ca50! 
 [ 5145.232653] -->RTUSBVenderReset 
 [ 5145.232775] <--RTUSBVenderReset 
 [ 5145.509862] Key1Str is Invalid key length(0) or Type(0) 
 [ 5145.509898] Key2Str is Invalid key length(0) or Type(0) 
 [ 5145.509929] Key3Str is Invalid key length(0) or Type(0) 
 [ 5145.509960] Key4Str is Invalid key length(0) or Type(0) 
 [ 5145.510434] 1. Phy Mode = 5 
 [ 5145.510437] 2. Phy Mode = 5 
 [ 5145.510443] NVM is Efuse and its size =2d[2d0-2fc]  
 [ 5145.557783] phy mode> Error! The chip does not support 5G band 8! 
 [ 5145.558008] RTMPSetPhyMode: channel is out of range, use first channel=1  
 [ 5145.561903] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5145.580644] 3. Phy Mode = 9 
 [ 5145.601647] MCS Set = ff ff 00 00 01 
 [ 5145.612221] <==== rt28xx_init, Status=0 
 [ 5145.613777] 0x1300 = 00064300 
 [ 5145.910529] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5146.170094] RTMP_TimerListAdd: add timer obj ffffc9000ded2638! 
 [ 5146.170104] RTMP_TimerListAdd: add timer obj ffffc9000ded26b0! 
 [ 5146.170110] RTMP_TimerListAdd: add timer obj ffffc9000ded2728! 
 [ 5146.170115] RTMP_TimerListAdd: add timer obj ffffc9000ded25c0! 
 [ 5146.170122] RTMP_TimerListAdd: add timer obj ffffc9000ded2458! 
 [ 5146.170127] RTMP_TimerListAdd: add timer obj ffffc9000ded24d0! 
 [ 5146.170132] RTMP_TimerListAdd: add timer obj ffffc9000de9c940! 
 [ 5146.170137] RTMP_TimerListAdd: add timer obj ffffc9000de8b5f8! 
 [ 5146.170142] RTMP_TimerListAdd: add timer obj ffffc9000de8b678! 
 [ 5146.170146] RTMP_TimerListAdd: add timer obj ffffc9000de9cad0! 
 [ 5146.170152] RTMP_TimerListAdd: add timer obj ffffc9000de9c850! 
 [ 5146.170158] RTMP_TimerListAdd: add timer obj ffffc9000de9ca50! 
 [ 5146.171525] -->RTUSBVenderReset 
 [ 5146.171650] <--RTUSBVenderReset 
 [ 5146.447961] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5146.447978] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5146.448393] Key1Str is Invalid key length(0) or Type(0) 
 [ 5146.448425] Key2Str is Invalid key length(0) or Type(0) 
 [ 5146.448455] Key3Str is Invalid key length(0) or Type(0) 
 [ 5146.448486] Key4Str is Invalid key length(0) or Type(0) 
 [ 5146.448965] 1. Phy Mode = 5 
 [ 5146.448969] 2. Phy Mode = 5 
 [ 5146.448974] NVM is Efuse and its size =2d[2d0-2fc]  
 [ 5146.496404] phy mode> Error! The chip does not support 5G band 8! 
 [ 5146.496614] RTMPSetPhyMode: channel is out of range, use first channel=1  
 [ 5146.500402] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5146.519151] 3. Phy Mode = 9 
 [ 5146.540156] MCS Set = ff ff 00 00 01 
 [ 5146.550764] <==== rt28xx_init, Status=0 
 [ 5146.552279] 0x1300 = 00064300 
 [ 5146.860175] forcedeth 0000:00:07.0: irq 41 for MSI/MSI-X 
 [ 5146.860395] forcedeth 0000:00:07.0: eth0: no link during initialization 
 [ 5146.861891] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [ 5147.479159] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5147.740980] RTMP_TimerListAdd: add timer obj ffffc9000ded2638! 
 [ 5147.740991] RTMP_TimerListAdd: add timer obj ffffc9000ded26b0! 
 [ 5147.740997] RTMP_TimerListAdd: add timer obj ffffc9000ded2728! 
 [ 5147.741003] RTMP_TimerListAdd: add timer obj ffffc9000ded25c0! 
 [ 5147.741009] RTMP_TimerListAdd: add timer obj ffffc9000ded2458! 
 [ 5147.741014] RTMP_TimerListAdd: add timer obj ffffc9000ded24d0! 
 [ 5147.741019] RTMP_TimerListAdd: add timer obj ffffc9000de9c940! 
 [ 5147.741024] RTMP_TimerListAdd: add timer obj ffffc9000de8b5f8! 
 [ 5147.741029] RTMP_TimerListAdd: add timer obj ffffc9000de8b678! 
 [ 5147.741034] RTMP_TimerListAdd: add timer obj ffffc9000de9cad0! 
 [ 5147.741040] RTMP_TimerListAdd: add timer obj ffffc9000de9c850! 
 [ 5147.741045] RTMP_TimerListAdd: add timer obj ffffc9000de9ca50! 
 [ 5147.742398] -->RTUSBVenderReset 
 [ 5147.742522] <--RTUSBVenderReset 
 [ 5148.019223] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5148.019243] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5148.019624] Key1Str is Invalid key length(0) or Type(0) 
 [ 5148.019656] Key2Str is Invalid key length(0) or Type(0) 
 [ 5148.019687] Key3Str is Invalid key length(0) or Type(0) 
 [ 5148.019717] Key4Str is Invalid key length(0) or Type(0) 
 [ 5148.020228] 1. Phy Mode = 5 
 [ 5148.020233] 2. Phy Mode = 5 
 [ 5148.020238] NVM is Efuse and its size =2d[2d0-2fc]  
 [ 5148.067527] phy mode> Error! The chip does not support 5G band 8! 
 [ 5148.067749] RTMPSetPhyMode: channel is out of range, use first channel=1  
 [ 5148.071653] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5148.090527] 3. Phy Mode = 9 
 [ 5148.111665] MCS Set = ff ff 00 00 01 
 [ 5148.122264] <==== rt28xx_init, Status=0 
 [ 5148.123774] 0x1300 = 00064300 
 [ 5150.225904] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 [ 5150.226526] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 [ 5150.245666] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=11) 
 [ 5152.317513] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5152.317908] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 [ 5152.318063] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5158.904053] ra0: no IPv6 routers present 
 [ 5159.304473] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5159.304679] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 [ 5159.304827] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5166.292468] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5166.292698] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 [ 5166.292842] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5173.280469] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5173.280678] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 [ 5173.280828] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5180.268463] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5180.268677] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 [ 5180.268822] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 [ 5186.644020] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5186.903996] RTMP_TimerListAdd: add timer obj ffffc9000ded2638! 
 [ 5186.904046] RTMP_TimerListAdd: add timer obj ffffc9000ded26b0! 
 [ 5186.904057] RTMP_TimerListAdd: add timer obj ffffc9000ded2728! 
 [ 5186.904067] RTMP_TimerListAdd: add timer obj ffffc9000ded25c0! 
 [ 5186.904078] RTMP_TimerListAdd: add timer obj ffffc9000ded2458! 
 [ 5186.904087] RTMP_TimerListAdd: add timer obj ffffc9000ded24d0! 
 [ 5186.904097] RTMP_TimerListAdd: add timer obj ffffc9000de9c940! 
 [ 5186.904106] RTMP_TimerListAdd: add timer obj ffffc9000de8b5f8! 
 [ 5186.904114] RTMP_TimerListAdd: add timer obj ffffc9000de8b678! 
 [ 5186.904123] RTMP_TimerListAdd: add timer obj ffffc9000de9cad0! 
 [ 5186.904132] RTMP_TimerListAdd: add timer obj ffffc9000de9c850! 
 [ 5186.904142] RTMP_TimerListAdd: add timer obj ffffc9000de9ca50! 
 [ 5186.905526] -->RTUSBVenderReset 
 [ 5186.905648] <--RTUSBVenderReset 
 [ 5187.185973] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5187.185993] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 [ 5187.186375] Key1Str is Invalid key length(0) or Type(0) 
 [ 5187.186407] Key2Str is Invalid key length(0) or Type(0) 
 [ 5187.186437] Key3Str is Invalid key length(0) or Type(0) 
 [ 5187.186468] Key4Str is Invalid key length(0) or Type(0) 
 [ 5187.186940] 1. Phy Mode = 5 
 [ 5187.186944] 2. Phy Mode = 5 
 [ 5187.186949] NVM is Efuse and its size =2d[2d0-2fc]  
 [ 5187.234276] phy mode> Error! The chip does not support 5G band 8! 
 [ 5187.234497] RTMPSetPhyMode: channel is out of range, use first channel=1  
 [ 5187.238276] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 [ 5187.257026] 3. Phy Mode = 9 
 [ 5187.278029] MCS Set = ff ff 00 00 01 
 [ 5187.288622] <==== rt28xx_init, Status=0 
 [ 5187.290148] 0x1300 = 0006430
```


And here is the syslog (syslog.1 isn't doing much), again this is only the part where wicd is trying to connect to the wireless network:


```
   	 	 	 	 	 	  Nov  1 10:11:02 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3 
 Nov  1 10:11:03 e-ubuntu avahi-daemon[886]: Joining mDNS multicast group on interface ra0.IPv6 with address fe80::6a7f:74ff:fee3:f64b. 
 Nov  1 10:11:03 yo-ubuntu avahi-daemon[886]: New relevant interface ra0.IPv6 for mDNS. 
 Nov  1 10:11:03 yo-ubuntu avahi-daemon[886]: Registering new address record for fe80::6a7f:74ff:fee3:f64b on ra0.*. 
 Nov  1 10:11:04 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3 
 Nov  1 10:11:07 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6 
 Nov  1 10:11:12 yo-ubuntu kernel: [ 5352.816058] ra0: no IPv6 routers present 
 Nov  1 10:11:13 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15 
 Nov  1 10:11:29 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9 
 Nov  1 10:11:38 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9 
 Nov  1 10:11:47 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16 
 Nov  1 10:12:03 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
 Nov  1 10:12:10 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
 Nov  1 10:12:19 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9 
 Nov  1 10:12:27 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12 
 Nov  1 10:12:40 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18 
 Nov  1 10:12:58 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10 
 Nov  1 10:13:08 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10 
 Nov  1 10:13:15 yo-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Nov  1 10:13:15 yo-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Nov  1 10:13:15 yo-ubuntu dhclient: All rights reserved. 
 Nov  1 10:13:15 yo-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/ 
 Nov  1 10:13:15 yo-ubuntu dhclient:  
 Nov  1 10:13:15 yo-ubuntu dhclient: Listening on LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:13:15 yo-ubuntu dhclient: Sending on   LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:13:15 yo-ubuntu dhclient: Sending on   Socket/fallback 
 Nov  1 10:13:15 yo-ubuntu dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67 
 Nov  1 10:13:15 yo-ubuntu dhclient: send_packet: Network is unreachable 
 Nov  1 10:13:15 yo-ubuntu dhclient: send_packet: please consult README file regarding broadcast address. 
 Nov  1 10:13:16 yo-ubuntu avahi-daemon[886]: Interface ra0.IPv6 no longer relevant for mDNS. 
 Nov  1 10:13:16 yo-ubuntu avahi-daemon[886]: Leaving mDNS multicast group on interface ra0.IPv6 with address fe80::6a7f:74ff:fee3:f64b. 
 Nov  1 10:13:16 yo-ubuntu avahi-daemon[886]: Withdrawing address record for fe80::6a7f:74ff:fee3:f64b on ra0. 
 Nov  1 10:13:16 yo-ubuntu dhclient: receive_packet failed on ra0: Network is down 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.233737] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493305] RTMP_TimerListAdd: add timer obj ffffc9000de4a638! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493315] RTMP_TimerListAdd: add timer obj ffffc9000de4a6b0! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493321] RTMP_TimerListAdd: add timer obj ffffc9000de4a728! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493327] RTMP_TimerListAdd: add timer obj ffffc9000de4a5c0! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493334] RTMP_TimerListAdd: add timer obj ffffc9000de4a458! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493340] RTMP_TimerListAdd: add timer obj ffffc9000de4a4d0! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493345] RTMP_TimerListAdd: add timer obj ffffc9000de14940! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493349] RTMP_TimerListAdd: add timer obj ffffc9000de035f8! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493354] RTMP_TimerListAdd: add timer obj ffffc9000de03678! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493359] RTMP_TimerListAdd: add timer obj ffffc9000de14ad0! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493365] RTMP_TimerListAdd: add timer obj ffffc9000de14850! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.493371] RTMP_TimerListAdd: add timer obj ffffc9000de14a50! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.494856] -->RTUSBVenderReset 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.494978] <--RTUSBVenderReset 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.770919] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.770938] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771320] Key1Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771351] Key2Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771382] Key3Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771412] Key4Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771881] 1. Phy Mode = 5 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771884] 2. Phy Mode = 5 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.771889] NVM is Efuse and its size =2d[2d0-2fc]  
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.819475] phy mode> Error! The chip does not support 5G band 8! 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.819549] RTMPSetPhyMode: channel is out of range, use first channel=1  
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.823226] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.841976] 3. Phy Mode = 9 
 Nov  1 10:13:16 yo-ubuntu kernel: [ 5476.863108] MCS Set = ff ff 00 00 01 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5476.873698] <==== rt28xx_init, Status=0 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5476.875231] 0x1300 = 00064300 
 Nov  1 10:13:17 yo-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Nov  1 10:13:17 yo-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Nov  1 10:13:17 yo-ubuntu dhclient: All rights reserved. 
 Nov  1 10:13:17 yo-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/ 
 Nov  1 10:13:17 yo-ubuntu dhclient:  
 Nov  1 10:13:17 yo-ubuntu dhclient: Listening on LPF/eth0/50:e5:49:6a:d2:1d 
 Nov  1 10:13:17 yo-ubuntu dhclient: Sending on   LPF/eth0/50:e5:49:6a:d2:1d 
 Nov  1 10:13:17 yo-ubuntu dhclient: Sending on   Socket/fallback 
 Nov  1 10:13:17 yo-ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67 
 Nov  1 10:13:17 yo-ubuntu dhclient: send_packet: Network is unreachable 
 Nov  1 10:13:17 yo-ubuntu dhclient: send_packet: please consult README file regarding broadcast address. 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5477.188859] forcedeth 0000:00:07.0: irq 41 for MSI/MSI-X 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5477.189076] forcedeth 0000:00:07.0: eth0: no link during initialization 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5477.190582] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 Nov  1 10:13:17 yo-ubuntu dhclient: receive_packet failed on ra0: Network is down 
 Nov  1 10:13:17 yo-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Nov  1 10:13:17 yo-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Nov  1 10:13:17 yo-ubuntu dhclient: All rights reserved. 
 Nov  1 10:13:17 yo-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/ 
 Nov  1 10:13:17 yo-ubuntu dhclient:  
 Nov  1 10:13:17 yo-ubuntu dhclient: Listening on LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:13:17 yo-ubuntu dhclient: Sending on   LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:13:17 yo-ubuntu dhclient: Sending on   Socket/fallback 
 Nov  1 10:13:17 yo-ubuntu dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67 
 Nov  1 10:13:17 yo-ubuntu dhclient: send_packet: Network is unreachable 
 Nov  1 10:13:17 yo-ubuntu dhclient: send_packet: please consult README file regarding broadcast address. 
 Nov  1 10:13:17 yo-ubuntu kernel: [ 5477.783483] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:13:17 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18 
 Nov  1 10:13:17 yo-ubuntu dhclient: send_packet: Network is down 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043433] RTMP_TimerListAdd: add timer obj ffffc9000de4a638! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043444] RTMP_TimerListAdd: add timer obj ffffc9000de4a6b0! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043450] RTMP_TimerListAdd: add timer obj ffffc9000de4a728! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043456] RTMP_TimerListAdd: add timer obj ffffc9000de4a5c0! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043462] RTMP_TimerListAdd: add timer obj ffffc9000de4a458! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043467] RTMP_TimerListAdd: add timer obj ffffc9000de4a4d0! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043472] RTMP_TimerListAdd: add timer obj ffffc9000de14940! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043477] RTMP_TimerListAdd: add timer obj ffffc9000de035f8! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043482] RTMP_TimerListAdd: add timer obj ffffc9000de03678! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043486] RTMP_TimerListAdd: add timer obj ffffc9000de14ad0! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043492] RTMP_TimerListAdd: add timer obj ffffc9000de14850! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.043498] RTMP_TimerListAdd: add timer obj ffffc9000de14a50! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.044858] -->RTUSBVenderReset 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.044978] <--RTUSBVenderReset 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.322804] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.322824] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323205] Key1Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323237] Key2Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323267] Key3Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323298] Key4Str is Invalid key length(0) or Type(0) 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323771] 1. Phy Mode = 5 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323775] 2. Phy Mode = 5 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.323780] NVM is Efuse and its size =2d[2d0-2fc]  
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.376240] phy mode> Error! The chip does not support 5G band 8! 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.376465] RTMPSetPhyMode: channel is out of range, use first channel=1  
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.380237] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.398985] 3. Phy Mode = 9 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.419984] MCS Set = ff ff 00 00 01 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.430574] <==== rt28xx_init, Status=0 
 Nov  1 10:13:18 yo-ubuntu kernel: [ 5478.432115] 0x1300 = 00064300 
 Nov  1 10:13:19 yo-ubuntu avahi-daemon[886]: Joining mDNS multicast group on interface ra0.IPv6 with address fe80::6a7f:74ff:fee3:f64b. 
 Nov  1 10:13:19 yo-ubuntu avahi-daemon[886]: New relevant interface ra0.IPv6 for mDNS. 
 Nov  1 10:13:19 yo-ubuntu avahi-daemon[886]: Registering new address record for fe80::6a7f:74ff:fee3:f64b on ra0.*. 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.563236] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.563855] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.580485] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.581105] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.583064] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=11) 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.605485] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:20 yo-ubuntu kernel: [ 5480.606108] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:21 yo-ubuntu kernel: [ 5481.115116] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:21 yo-ubuntu kernel: [ 5481.116488] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:25 yo-ubuntu kernel: [ 5485.612554] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:25 yo-ubuntu kernel: [ 5485.612870] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:25 yo-ubuntu kernel: [ 5485.613026] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:28 yo-ubuntu kernel: [ 5488.784024] ra0: no IPv6 routers present 
 Nov  1 10:13:32 yo-ubuntu kernel: [ 5492.600424] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:32 yo-ubuntu kernel: [ 5492.600658] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:32 yo-ubuntu kernel: [ 5492.600804] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:36 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
 Nov  1 10:13:39 yo-ubuntu kernel: [ 5499.588412] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:39 yo-ubuntu kernel: [ 5499.588637] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:39 yo-ubuntu kernel: [ 5499.588927] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:43 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
 Nov  1 10:13:46 yo-ubuntu kernel: [ 5506.576422] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:46 yo-ubuntu kernel: [ 5506.576636] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:46 yo-ubuntu kernel: [ 5506.576787] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:51 yo-ubuntu kernel: [ 5511.093992] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:51 yo-ubuntu kernel: [ 5511.095237] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:51 yo-ubuntu kernel: [ 5511.106996] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:51 yo-ubuntu kernel: [ 5511.108240] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:52 yo-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15 
 Nov  1 10:13:53 yo-ubuntu kernel: [ 5513.172415] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:53 yo-ubuntu kernel: [ 5513.172616] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:53 yo-ubuntu kernel: [ 5513.172764] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:57 yo-ubuntu kernel: [ 5517.535744] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:57 yo-ubuntu kernel: [ 5517.536988] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:57 yo-ubuntu kernel: [ 5517.550490] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:57 yo-ubuntu kernel: [ 5517.551734] /home/yo/Desktop/Drivers/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.c:2998 assert KeyIdx < 4failed 
 Nov  1 10:13:59 yo-ubuntu kernel: [ 5519.612563] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:13:59 yo-ubuntu kernel: [ 5519.612657] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1) 
 Nov  1 10:13:59 yo-ubuntu kernel: [ 5519.613119] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360 
 Nov  1 10:14:01 yo-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Nov  1 10:14:01 yo-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Nov  1 10:14:01 yo-ubuntu dhclient: All rights reserved. 
 Nov  1 10:14:01 yo-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/ 
 Nov  1 10:14:01 yo-ubuntu dhclient:  
 Nov  1 10:14:01 yo-ubuntu dhclient: Listening on LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:14:01 yo-ubuntu dhclient: Sending on   LPF/ra0/68:7f:74:e3:f6:4b 
 Nov  1 10:14:01 yo-ubuntu dhclient: Sending on   Socket/fallback 
 Nov  1 10:14:01 yo-ubuntu dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67 
 Nov  1 10:14:01 yo-ubuntu dhclient: send_packet: Network is unreachable 
 Nov  1 10:14:01 yo-ubuntu dhclient: send_packet: please consult README file regarding broadcast address. 
 Nov  1 10:14:02 yo-ubuntu avahi-daemon[886]: Interface ra0.IPv6 no longer relevant for mDNS. 
 Nov  1 10:14:02 yo-ubuntu avahi-daemon[886]: Leaving mDNS multicast group on interface ra0.IPv6 with address fe80::6a7f:74ff:fee3:f64b. 
 Nov  1 10:14:02 yo-ubuntu avahi-daemon[886]: Withdrawing address record for fe80::6a7f:74ff:fee3:f64b on ra0. 
 Nov  1 10:14:02 yo-ubuntu dhclient: receive_packet failed on ra0: Network is down 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5521.911983] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172804] RTMP_TimerListAdd: add timer obj ffffc9000de4a638! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172814] RTMP_TimerListAdd: add timer obj ffffc9000de4a6b0! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172820] RTMP_TimerListAdd: add timer obj ffffc9000de4a728! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172826] RTMP_TimerListAdd: add timer obj ffffc9000de4a5c0! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172836] RTMP_TimerListAdd: add timer obj ffffc9000de4a458! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172841] RTMP_TimerListAdd: add timer obj ffffc9000de4a4d0! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172846] RTMP_TimerListAdd: add timer obj ffffc9000de14940! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172851] RTMP_TimerListAdd: add timer obj ffffc9000de035f8! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172855] RTMP_TimerListAdd: add timer obj ffffc9000de03678! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172860] RTMP_TimerListAdd: add timer obj ffffc9000de14ad0! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172866] RTMP_TimerListAdd: add timer obj ffffc9000de14850! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.172872] RTMP_TimerListAdd: add timer obj ffffc9000de14a50! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.174228] -->RTUSBVenderReset 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.174353] <--RTUSBVenderReset 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.457930] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.457950] CfgSetCountryRegion():CountryRegion in eeprom was programmed 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458331] Key1Str is Invalid key length(0) or Type(0) 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458363] Key2Str is Invalid key length(0) or Type(0) 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458393] Key3Str is Invalid key length(0) or Type(0) 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458424] Key4Str is Invalid key length(0) or Type(0) 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458893] 1. Phy Mode = 5 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458897] 2. Phy Mode = 5 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.458902] NVM is Efuse and its size =2d[2d0-2fc]  
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.507122] phy mode> Error! The chip does not support 5G band 8! 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.507352] RTMPSetPhyMode: channel is out of range, use first channel=1  
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.511107] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc]  
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.529857] 3. Phy Mode = 9 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.551985] MCS Set = ff ff 00 00 01 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.562579] <==== rt28xx_init, Status=0 
 Nov  1 10:14:02 yo-ubuntu kernel: [ 5522.564112] 0x1300 = 00064300 
 Nov  1 10:14:02 yo-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Nov  1 10:14:02 yo-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Nov  1 10:14:02 yo-ubuntu dhclient: All rights reserved. 
 Nov  1 10:14:02 yo-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/ 
 Nov  1 10:14:02 yo-ubuntu dhclient:  
 Nov  1 10:14:03 yo-ubuntu dhclient: receive_packet failed on ra0: Network is dow
```

---

### Post by ohmysql on 2011-11-01
Update: 

Check this out:

[http://ubuntuforums.org/showpost.php?p=11415111&postcount=5](http://ubuntuforums.org/showpost.php?p=11415111&postcount=5)

I'm not having that kind of luck on 11.10, but I'm all ears!

OMS

---

### Post by praseodym on 2011-11-01
```
[ 5187.234276] phy mode> Error! The chip does not support 5G band 8! 
[ 5187.234497] RTMPSetPhyMode: channel is out of range, use first channel=1
```
Which channel/frequency do you want to use?

---

### Post by ohmysql on 2011-11-01
I was thinking channel 11. I'm not sure how to tell - do I do route -n? Or do I plug in and do sudo iwlist scan?

OMS

---

### Post by praseodym on 2011-11-01
Check with "sudo iwlist scan" and in your router interface

---

### Post by ohmysql on 2011-11-01
> **praseodym said:**
> Check with "sudo iwlist scan" and in your router interface
 

Ok wait, hold the phone. This person says the Cisco Valet Connector is now working out of the box for them on 11.10. That means we're doing something we don't need to be doing here.

[http://ubuntuforums.org/showthread.php?p=11415167#post11415167](http://ubuntuforums.org/showthread.php?p=11415167#post11415167)

Please help me figure out what to do. I've done sudo rmmod rt3572sta, then I did sudo make uninstall, sudo make clean in the driver directory.

I then went to "Additional Drivers" and installed the Linux Lan rt2870 driver that now comes with 11.10.

What else should I do to get my driver working? So far when I do sudo iwlist scan I get:

```
wlan0     Interface doesn't support scanning : Network is down
```

This is my interfaces: 

```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
```

But when I restart my networking it says:

```
Cannot find device "wlan0"
Failed to bring up wlan0.
``` How do I need to set up the interfaces file?

OMS

---

### Post by praseodym on 2011-11-01
Remove both lines containing "wlan0", remove your wireless profile and reboot. Then set-up a new wireless profile. Check:

```
cat /etc/network/interfaces
route -n
cat /etc/resolv.conf
lsmod
iwconfig
dmesg | grep rt2
rfkill list
sudo iwlist scan
```
If you are using Wicd, try with those 2 lines.

---

### Post by ohmysql on 2011-11-01
> **praseodym said:**
> Remove both lines containing "wlan0", remove your wireless profile and reboot. Then set-up a new wireless profile. Check:
 
```
cat /etc/network/interfaces
route -n
cat /etc/resolv.conf
lsmod
iwconfig
dmesg | grep rt2
rfkill list
sudo iwlist scan
```
If you are using Wicd, try with those 2 lines.
 
How do I delete my wireless profile?

---

### Post by praseodym on 2011-11-01
In NetworkManager: Right-click->Edit, choose your profile and "remove". In Wicd (I dont use it) its similar after starting the applet.

---

### Post by ohmysql on 2011-11-02
I was going to try your changes, but I ended up trying the rt2800usb driver first and it is working! I've learned from this saga not to celebrate too early, but I am once again writing from my Cisco AM10 Valet Connector.

For some reason it uses wlan0 rather than ra0, but I am prepared to live with that. So I haven't configured interfaces at all. I'm going to mark this as solved. Solution: use rt2800usb. We'll see if the good news keeps rolling.

Thank you SO MUCH for all your help. I've learned a ton about how linux wireless networking works from all this. I was rereading old posts from when I started and just amazed that I didn't know any of the things I know now back then. Thank you.

And I think the supplicant was working at the end. But I think overall it wasn't associating with the driver very well, perhaps because I wasn't using the right driver. Anyway, this hopefully seems to be solved.

Like, oh my SQL!!

---

