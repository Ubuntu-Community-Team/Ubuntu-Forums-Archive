---
title: "wusb11v4 sees router cannot authenticate wep"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Questor_ix on 2010-01-17
I'm getting rather bewildered.

I followed these instructions to setup my wusb11 driver using ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

But when I try to ifup the interface, I get:

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.

iwconfig shows that no essid is assigned, even though I have specified one in /etc/interfaces.

Then if I go through the desktop gui Preferences -> Network to setup my wireless connection, /etc/interfaces does not seem to change but iwconfig then reports the essid is assigned.

Anyway, on my default taskbar there is a wireless icon.  Clicking on that shows the wireless access points in the area.  I see my own.  When I try to connect to it, it prompts for my wep key.  I enter the key, it thinks, and then acts as if I'd entered the wrong key.

Specifically of course, I'd like this to get fixed so that I can happily surf the net again, etc.

But I also I'm wondering why it seems that there is a disconnect between /etc/interfaces and Preferences->Network.  If I type in a WEP key in the gui, I would think that it should appear in /etc/interfaces.

I'm definitely a Ubuntu wireless newbie, and not very experienced at Ubuntu anyway.

Anything you might say to clear up my fog a bit would be appreciated.  

Thank you

---

### Post by Questor_ix on 2010-01-28
For anyone having wep authentication problems in Ubuntu, this is what I learned.  Either switch to wpa or filter by mac address.

---

### Post by Kadai on 2010-01-29
I have the very same problem.

I'm able to connect to WPA networks with no problem at all, but when I try to connect to a WEP one (with a Shared Key) Network-Manager just keeps asking for the key once and once again.

The issue here is that it does used to work in the past. I have completely discarded any hardware issue because I can see all other networks and even connect to any using WPA.

And, as far as I know, this is a software-related issue, because after using "sudo iwlist auth" I got the next in console:

```
kadai@XXXXXXX:~$ sudo iwlist auth
[sudo] password for kadai:           
lo        no authentication information.

eth0      no authentication information.

eth1      Authentication capabilities :
                WPA                    
                WPA2                   
                CIPHER-TKIP            
                CIPHER-CCMP            
          Current WPA version :        
                WPA2                   
          Current Key management :     
                PSK                    
          Current Pairwise cipher :    
                none                   
          Current Pairwise cipher :
                none
          Current TKIP countermeasures : no
          Current Drop unencrypted : yes
          Current Authentication algorithm :
                open
          Current Receive unencrypted EAPOL : no
          Current Roaming control : no
          Current Privacy invoked : no


pan0      no authentication information.

wmaster0  no authentication information.

wlan0     Authentication capabilities :
                WPA
                WPA2
                CIPHER-TKIP
                CIPHER-CCMP
          Current Authentication algorithm :
                open


kadai@XXXXXXX:~$

```

Listed there are two wireless devices.
An internal bradcom wireless card, and a rt73usb wireless one.

I have been searching for a solution for this issue this week, but not luck around. While this is not a critical issue, is yet annoying specially because outside home, everyone else does uses WEP networks and it does make Kubuntu completely useless on connectivity field when needed.

If someone knows where is is a tracker for this, or how to fix this (not using the change to a WPA network) I'll be really grateful.

Thanks in advance.

---

### Post by Mikeinnc on 2010-07-06
I am also having the same problem and it really seems to be a huge issue with Ubuntu, when I read various forums on the Internet. I installed 10.04 and was able to sucessfully set up a WEP connection, including PPTP vpn, at work. Then I came home and connected to my WPA network at home without any problems. When I went back to work, it will NOT authenticate to the WEP network. I come home - and it connects immediately. Windows machines connect to the WEP network with no problems - and there has been no change to the network settings. On the WEP network it constantly asks - about every minute or so - for the key. Entering it make no difference. I have tried just about everything to no avail. All the various help areas appear to show me that everything appears to be OK - but the card will not authenticate. I know the card works - it connects via WPA (which *should* be more complex!) This is a deal breaker for me. If I can't connect, what use is Linux?

---

### Post by Kadai on 2010-07-06
> **Mikeinnc said:**
> I am also having the same problem and it really  seems to be a huge issue with Ubuntu, when I read various forums on the  Internet. I installed 10.04 and was able to sucessfully set up a WEP  connection, including PPTP vpn, at work. Then I came home and connected  to my WPA network at home without any problems. When I went back to  work, it will NOT authenticate to the WEP network. I come home - and it  connects immediately. Windows machines connect to the WEP network with  no problems - and there has been no change to the network settings. On  the WEP network it constantly asks - about every minute or so - for the  key. Entering it make no difference. I have tried just about everything  to no avail. All the various help areas appear to show me that  everything appears to be OK - but the card will not authenticate. I know  the card works - it connects via WPA (which *should* be more complex!)  This is a deal breaker for me. If I can't connect, what use is  Linux?

Well, I do not posted my solution to this problem because I did not remembered this post.

But, a way to solve the issue is to install WICD and have it be the network manager.
(If you use something like KDE4.x, it might be knetworkmanager)

You should be able to do something like this to have it:
```
sudo apt-get install wicd wicd-client
```

It will install the wicd manager, and then uninstall the old manager you had installed.

Of course, I recommend precaution on doing this, but just to check that you have all the required and do not end up requiring a re-install.

So far I have not get problems with wicd, and it works like a charm everywhere.

---

### Post by Mikeinnc on 2010-07-08
Thanks Kadai. I took your advice and actually reinstalled Lucid from scratch. I then installed wicd; uninstalled Network Manager and I agree - it appears to be a lot better. I then connected to my wired network at home - absolutely no problem. I then also connected to my own WPA-PSK (hidden SSID) wireless network at home with no problems - and even to my neighbour's WPA-PSK network (yes, I do know the password as I set it up!). So far so good and I'm feeling really confident. So then I come into work where the network is WEP protected (yes, I know that's not good but it is old; about to be replaced with 802.1X authentication and we then use a vpn to connect so that secures it)....and the problem is exactly the same. "Validating authentication" and then 'Not connected - Bad password". I have tried just about every WEP combination in wicd - WEP Hex; WEP Passphrase; WEP Shared. The passphrase is 12345 (hardly a secret - and hardly likely to be entered incorrectly!) and I wonder if this is an issue. I've tried entering it as hex - 3132333435; with single quotes; double quotes...just about every combination. It tries to connect and always ends up with 'bad password'. I've looked at the wicd log and the only possible clue is it says that it 'might be better to use dhcpcd instead of dhclient' but this option is greyed out for me. It appears that there is a far more fundamental problem with WEP - maybe at the driver level? I did run an update on my v10.04 via my wired connection - could there be a bug in the updates? This USED to work when I first installed 10.04 a few weeks ago- I could connect at work and then connect via vpn and it worked fine. Now it is hopeless! If my suspicions are correct, when I go home this evening, I'll connect to my WPA network with no problems. What IS going on? (oh, and in case you ask, colleagues are currently authenticating with Macs and Windows machines so the passphrase IS correct and HASN'T changed.) The laptop is an IBM ThinkPad R40 and the wireless card is an Intel Centrino IPW2100 3B Mini PC Adapter. There must be an answer to this problem - as I said before, there appear to be so many comments on the 'net that I cannot be unique (and it doesn't appear to be machine or adapter specific, which suggests a configuration / application problem?).

Thanks for ANY clues you can give me.....

Mike

---

### Post by Mikeinnc on 2010-07-08
I should have added this to my previous post - apologies. I've changed the name of the network to 'XXXX' for obvious reasons.;)

2010/07/09 10:07:03 :: Connecting to wireless network XXXX
2010/07/09 10:07:03 :: iwconfig eth1
2010/07/09 10:07:03 :: attempting to set hostname with dhclient
2010/07/09 10:07:03 :: using dhcpcd or another supported client may work better
2010/07/09 10:07:03 :: /sbin/dhclient -r eth1
2010/07/09 10:07:04 :: ifconfig eth1 0.0.0.0 
2010/07/09 10:07:04 :: /sbin/ip route flush dev eth1
2010/07/09 10:07:04 :: ifconfig eth1 down
2010/07/09 10:07:04 :: ifconfig eth1 up
2010/07/09 10:07:04 :: wpa_cli -i eth1 terminate
2010/07/09 10:07:04 :: attempting to set hostname with dhclient
2010/07/09 10:07:04 :: using dhcpcd or another supported client may work better
2010/07/09 10:07:04 :: /sbin/dhclient -r eth0
2010/07/09 10:07:04 :: ifconfig eth0 0.0.0.0 
2010/07/09 10:07:04 :: /sbin/ip route flush dev eth0
2010/07/09 10:07:04 :: ifconfig eth0 down
2010/07/09 10:07:04 :: ifconfig eth0 up
2010/07/09 10:07:04 :: ifconfig eth0
2010/07/09 10:07:04 :: Putting interface down
2010/07/09 10:07:04 :: ifconfig eth1 down
2010/07/09 10:07:04 :: ifconfig eth1
2010/07/09 10:07:04 :: Releasing DHCP leases...
2010/07/09 10:07:04 :: attempting to set hostname with dhclient
2010/07/09 10:07:04 :: using dhcpcd or another supported client may work better
2010/07/09 10:07:04 :: /sbin/dhclient -r eth1
2010/07/09 10:07:04 :: Setting false IP...
2010/07/09 10:07:04 :: ifconfig eth1 0.0.0.0 
2010/07/09 10:07:04 :: Stopping wpa_supplicant
2010/07/09 10:07:04 :: wpa_cli -i eth1 terminate
2010/07/09 10:07:04 :: Flushing the routing table...
2010/07/09 10:07:04 :: /sbin/ip route flush dev eth1
2010/07/09 10:07:04 :: iwconfig eth1 mode managed
2010/07/09 10:07:04 :: Putting interface up...
2010/07/09 10:07:04 :: ifconfig eth1 up
2010/07/09 10:07:06 :: iwconfig eth1
2010/07/09 10:07:06 :: enctype is wep-passphrase
2010/07/09 10:07:06 :: Attempting to authenticate...
2010/07/09 10:07:06 :: ['wpa_supplicant', '-B', '-i', 'eth1', '-c', '/var/lib/wicd/configurations/001956e98c10', '-D', 'wext']
2010/07/09 10:07:06 :: ['iwconfig', 'eth1', 'essid', '--', 'XXXX']
2010/07/09 10:07:06 :: iwconfig eth1 channel 11
2010/07/09 10:07:06 :: iwconfig eth1 ap 00:19:56:E9:8C:10
2010/07/09 10:07:07 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:08 :: iwconfig eth1
2010/07/09 10:07:08 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:09 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:10 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:10 :: iwconfig eth1
2010/07/09 10:07:11 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:12 :: WPA_CLI RESULT IS SCANNING
2010/07/09 10:07:13 :: iwconfig eth1
2010/07/09 10:07:13 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:14 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:15 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:15 :: iwconfig eth1
2010/07/09 10:07:16 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:17 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:18 :: iwconfig eth1
2010/07/09 10:07:18 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:19 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:20 :: iwconfig eth1
2010/07/09 10:07:20 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:21 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:22 :: iwconfig eth1
2010/07/09 10:07:22 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:23 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:24 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:25 :: iwconfig eth1
2010/07/09 10:07:25 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:26 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:27 :: iwconfig eth1
2010/07/09 10:07:27 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:28 :: WPA_CLI RESULT IS SCANNING
2010/07/09 10:07:29 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:30 :: iwconfig eth1
2010/07/09 10:07:30 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:31 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:32 :: iwconfig eth1
2010/07/09 10:07:32 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:33 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:34 :: iwconfig eth1
2010/07/09 10:07:34 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:35 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:36 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:37 :: iwconfig eth1
2010/07/09 10:07:37 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:38 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:39 :: iwconfig eth1
2010/07/09 10:07:39 :: WPA_CLI RESULT IS SCANNING
2010/07/09 10:07:42 :: iwconfig eth1
2010/07/09 10:07:42 :: WPA_CLI RESULT IS ASSOCIATING
2010/07/09 10:07:43 :: wpa_supplicant authentication may have failed.
2010/07/09 10:07:43 :: connect result is Failed
2010/07/09 10:07:43 :: exiting connection thread
2010/07/09 10:07:43 :: Sending connection attempt result bad_pass

---

### Post by Mikeinnc on 2010-07-10
I think I may have found the problem! I set up a spare wireless AP today with the same parameters as the one at work - SSID SNAP WEP authentication password 12345. The same problem - was unable to authenticate. However, in a blinding flash, I remembered that when I set the password - 12345 - on the wireless AP, it gave me four 10 digit hex KEYS (my caps). I changed the key on the WEP details for the SNAP network to the first key - E235485511. It worked!!! I then checked on-line for a 'WEP key generator' and found that the pass-phrase 12345 would ALWAYS generate the self-same keys. So this seems to be the problem - the WEP networks actually require the Hex key that is generated when you enter a 'normal' pass-phrase. In my case, it wanted key #1 - the one I have shown above. Now I accept that I may have been staring this in the face for a while as WICD (and Network Manager) actually asks for the WEP key and I - and I suspect many other people with the same problem - have been entering the WEP "pass-phrase" instead. BUT - my home WPA-PSK network also asks for the 'pre-shared key' and when I type in my everyday common English passphrase - it works!! There is clearly no consistency here! For WEP, I MUST NOT type in the normal ASCII passphrase, but for WPA I MUST type in the normal ASCII passphrase......... Come on guys - no wonder I'm ****** confused!:confused:

---

### Post by Mikeinnc on 2010-08-02
Well, I have just about given up. Try as I may, I cannot get the internal wireless NIC to authenticate to my work WEP based access point. I've also tried an old but trusted Cisco PCMCIA 802.11b wireless card - it also fails to authenticate. However, a Linksys WUSB54GC USB adapter works perfectly straight out of the box! The wireless system at work uses a professional Cisco AP (I'm not certain of the model/type). If I bring the laptop home and "build" a "similar" WEP based network - same address range, authentication type and passwords - on my Linksys WRT300N AP that is running DD-WRT software, ALL of the adapters associate and authenticate perfectly! So, having tried self flagellation and decided it hurts, I'll just stick with the USB adapter and continue to be somewhat suspicious that it is a kernel / driver issue...since it always used to work withe earlier versions! I'm disappointed, though - I still see what appears to be a lot of chatter on different forums that I'm not the only person who is suffering like this. Someone, somewhere must have a clue what has changed......or am I just too optimistic?

---

### Post by malkdude on 2010-09-08
Hi all,

I am having some issues with connecting to a WEP also, using both nm-applet (network manager) and wicd. However, when I went to KDE instead of GNOME, and used knetworkmanager, and selected the key to be HEX/ASCII, things worked out fine.

Comparing with network manager, I noticed that it lets you enter a HEX key, but it doesn't provide you with the choice of entering an ASCII key. I believe moreover that previous versions allowed for one to input an ASCII key...

This might be the cause of your problem too, though I am not sure. I am currently looking for some workarounds in gnome.

Please note that this only happened with one WEP set up router, but I wasn't having problems with other routers. This is probably because whoever set up that particular router may have written his key in ASCII format.

Cheers,
I'll post some more if I find out how to fix it...

---

