---
title: "Ubuntu 10.10 and Intel 2200bg Mini-PCI"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by BenSeager on 2011-01-15
I'm an experienced Windows user but a complete newbie when it comes to  Linux.  I've got an old laptop and thought I'd try it out.  I chose  Ubunutu because it seems to be the one which will work out of the box  most of the time - allowing me to learn how to use LInux relatively  easily.

The good news - almost everything works!

The bad news - the only thing that doesn't is the wireless connection.

The laptop has an Intel 2200bg Mini-PCI WLAN card.

Using the default network applet in Ubuntu and WICD network manager I  can see available networks but when I try to connect to mine it either  will not connect because it fails security authentication (WPA2-PSK)  because of a bad password (yes I've checked that I've typed it  correctly!) or because it cannot obtain an IP address (it only does this  if I disable security to test the connection).

Any help greatly appreciated!

---

### Post by chili555 on 2011-01-15
My Intel 2200ABG wouldn't do WPA; that's why I replaced it with a 2915ABG and not without some trouble! Let's query yours. Please open Applications > Accessories > Terminal and do:```
sudo iwlist eth1 auth
```Is your network the dreaded mixed WPA ***and*** WPA2 mode? You will probably have better luck with only WPA2 assuming your card can do it.

---

### Post by BenSeager on 2011-01-15
Hi,

Here is the result
```

eth1      Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        Unknown
          Current Key management :
        Unknown
          Current Pairwise cipher :
        WEP-104
        Unknown
          Current Pairwise cipher :
        WEP-104
        Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : no
          Current Privacy invoked : no
```

---

### Post by BenSeager on 2011-01-15
Hi,

Here is the result.  The router should be configured to only WPA, so unless the router is playing silly-buggers it shouldn't be mixed.

```
eth1      Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        Unknown
          Current Key management :
        Unknown
          Current Pairwise cipher :
        WEP-104
        Unknown
          Current Pairwise cipher :
        WEP-104
        Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : no
          Current Privacy invoked : no
```

---

### Post by chili555 on 2011-01-15
Awesome. You have one of the newer cards with updated firmware. How about this?> Is your network the dreaded mixed WPA and WPA2 mode? You will probably have better luck with only WPA2 assuming your card can do it. 

---

### Post by BenSeager on 2011-01-15
OK.  I've set the network's security to mixed-mode (WPA and WPA2) but still no joy.  It is still failing at the authentication stage.

---

### Post by chili555 on 2011-01-15
No. I am trying to say ***NOT*** to use mixed mode; select one or the other, not both.

---

### Post by BenSeager on 2011-01-15
Yeah, sorry I misread.  I've tried mixed-mode, WPA, WPA2 and WEP.  Still nothing.  I've just tried connecting to an unsecured network and it seemed to establish the connection ok.

---

### Post by chili555 on 2011-01-15
There is one more thing to try:```
sudo ifconfig eth1 down
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
sudo ifconfig eth1 up
```Any improvement? If so, we can make the module parameter permanent easily.

---

### Post by BenSeager on 2011-01-17
Thanks for your reply.

I tried that, and I get the following:

<code>
SIOCSIFFLAGS: Permission denied</code>

Should I uninstall WICD and/or Network Manager before attempting this?

---

### Post by chili555 on 2011-01-17
You have installed Network Manager *AND* Wicd? That's a lot of hands on the steering wheel, isn't it? I suggest you uninstall Wicd and try again. It may take a reboot. My 2200ABG worked perfectly with NM.

---

### Post by BenSeager on 2011-01-18
I don't have them both installed at the same time.  I just tried one, and then the other.  I'll give it a go with NM.

Just as a side note - I reinstalled the OS, and the card, and it will now connect to the network but drops the connection after about 10 seconds. Progress?

---

### Post by chili555 on 2011-01-18
It certainly is progress; you can connect now, however briefly. Please try the commands here:```
sudo ifconfig eth1 down
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
sudo ifconfig eth1 up
```Now does it drop?

---

### Post by BenSeager on 2011-01-18
No joy.  It still drops the connection between 10 and 30 seconds after connecting.  What shall I try next?

I've dealt with a *similar* problem with this card in Windows - and a solution is to turn off the card's automatic power management.  How do I fiddle with the power settings in Linux?  Intel are kind enough to provide a Windows application for doing this but nothing for Linux.

---

### Post by chili555 on 2011-01-18
Duplicate.

---

### Post by chili555 on 2011-01-18
Duplicate.

---

### Post by chili555 on 2011-01-18
> a solution is to turn off the card's automatic power management. Please try:```
sudo iwconfig eth1 power off
```If it works, we can make it permanent.

---

### Post by BenSeager on 2011-01-18
Again, no joy.

I've tried turning up the transmit power using


```
sudo iwconfig eth1 txpower 30mw
```

but I'm not sure that I'm doing that correctly, or if that is actually making any changes.

---

### Post by chili555 on 2011-01-18
What does this tell us?```
iwconfig
sudo iwlist eth1 scan
```

---

### Post by BenSeager on 2011-01-18
OK.

iwconfig gives:


```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"BenAndBeth"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: E8:BE:81:73:EE:DC   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Running the scan command, gives a list of the closest networks.  The details for the one I'm trying to connect to is shown below:
```
eth1      Scan completed :
          Cell 01 - Address: E8:BE:81:73:EE:DC
                    ESSID:"BenAndBeth"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-26 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 280ms ago
```

Just to let you know I've been fiddling and have turned power management back on, and altering ```
txpower
``` doesn't seem to make any difference.

---

### Post by chili555 on 2011-01-18
> Bit Rate:0 kb/sWhat do you make of this? Please try:```
sudo iwconfig eth1 rate 54M
```

---

### Post by BenSeager on 2011-01-19
OK, I gave that a go and then looked at iwconfig again.  The bit rate is still reporting at 0.  This made me think that it could be a hardware problem, but it works perfectly under WinXP.

Any more suggestions?  I've thought of trying another card, but I'm not sure that would be the end of the problems.  Also the design of the laptop I'm using prohibits certain cards because of their height.

I know this card *should* work out of the box with ipw2200, but could a solution be to use the Windows driver with ndiswrapper?

Thanks for all your help with this - its really appreciated.  Ihope I'm not taking up too much of your time!

---

### Post by chili555 on 2011-01-19
Before we try ndiswrapper (which I am predisposed to dislike), there is an updated ipw2200 in linux-backports-modules-wireless-maverick-generic. Can you please install it through System > Administration > Synaptic, reboot and give us your report?

---

### Post by BenSeager on 2011-01-19
I think I installed that package correctly.  I opened up the Synaptic, couldn't find anything to start with so I added the backports repository and then searched for > linux-backports-modules-wireless-maverick-generic

I selected the top one, Synaptic then told me two other packages needed to be installed. I OK'd that, let it do its business and then rebooted.

Wireless connected, and then dropped the connection after about 5 seconds.  I tried fiddling with the rate and txpower but still nothing.

---

### Post by chili555 on 2011-01-20
Have you tried different channels in your router? Perhaps you have interference on the default channel 6. I have the best luck on channel 11.

Do you have the Windows XP .inf and .sys files if you want to try ndiswrapper?

---

### Post by BenSeager on 2011-01-29
Hi,

Sorry for not replying sooner - I've been bust with work and haven't had much opportunity to mess around with my Linux box.

Anyway - switching channels worked!  I now have a stable wireless connection. It's always the simple things!

Thanks very much for your help with this, most appreciated.

---

### Post by arunsinghiiita on 2011-04-01
hi
i am using hp mini 210 and installed ubuntu 10.10 netbook.
wired internet is running but wireless is is not showing on the top. still synoptic and updates are not working with the wired also.
please help me.

Dr.Arun kr.Singh

---

### Post by arunsinghiiita on 2011-04-01
Hi
if i wants to download on synoptic after searching these are the results...........

Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/Release.gpg)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/Release.gpg)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en_IN.bz2](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.linux.duke.edu:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by chili555 on 2011-04-01
Please let us see:```
ifconfig
cat /etc/resolv.conf
ping -c3 74.125.45.99
```Thanks.

---

