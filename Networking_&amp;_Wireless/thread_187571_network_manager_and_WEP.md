---
title: "network manager and WEP"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by phonebox on 2006-06-03
Network Manager won't let me connect to my home wlan when its configured with a WEP key. (I know I should be using WPA, but other stuff I have can only use WEP).

Looking at /var/log/syslog, it gets into the state of associating but then seems to timeout and disconnects:

```

Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): State: SCANNING -> ASSOCIATING 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): wpa_driver_wext_associate 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Setting authentication timeout: 10 sec 0 usec 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): EAPOL: External notification - portControl=ForceAuthorized 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: cmd=0x8b06 len=8 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: cmd=0x8b1a len=15 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: cmd=0x8b15 len=20 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: new AP: 00:00:00:00:00:00 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): BSSID 00:00:00:00:00:00 blacklist count incremented to 5 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): State: ASSOCIATING -> DISCONNECTED 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): EAPOL: External notification - portEnabled=0 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): EAPOL: External notification - portValid=0 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 37 33 2d 31 00 00 00 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: cmd=0x8b15 len=20 
Jun  3 17:53:53 localhost NetworkManager: <information>^Iwpa_supplicant(5236): Wireless event: new AP: 00:00:00:00:00:00 
Jun  3 17:54:06 localhost NetworkManager: <information>^Iwpa_supplicant(5236): ted to 6 
Jun  3 17:54:06 localhost NetworkManager: <information>^Iwpa_supplicant(5236): State: DISCONNECTED -> DISCONNECTED 

```

This doesn't happen if I turn off the WEP - it connects then.

I've removed all the interfaces from /etc/network/interfaces, removed and resinstalled it, and restarted dbus and networking multiple times, but the same thing still happens.

If anyone could shed some light on this, much appreciated.

---

### Post by Thund3rstruck on 2006-06-03
I'm having the exact same thing. My network works fine if I disable WEP but it will not accept my key no matter what. I've tried 128-bit and 64-bit and even translated both into HEX manually and still no luck. As a matter of fact, the network manager will not even see my network until I turn off WEP

---

### Post by laroetman on 2006-06-03
[QUOTE=Thund3rstruck]I'm having the exact same thing. My network works fine if I disable WEP but it will not accept my key no matter what. I've tried 128-bit and 64-bit and even translated both into HEX manually and still no luck. As a matter of fact, the network manager will not even see my network until I turn off WEP[/QUOTE]

Yea, mine is doing the same thing too.  Any solutions would be great!  I'm pretty new to this as well.  I am unable to get it to work with WEP or WPA (which is my goal).

---

### Post by SyvanX on 2006-06-04
My wireless was working perfectly with ndiswrapper, then i updated to dapper and WEP was broken.

I have 2 cards, one using wlan-ng and the other using ndiswrapper and they both cannot set a wep key, i've also tried setting it via the command line and it fails there as well.  For some reason it isn't accepting the key.  connecting to an unsecured network works just fine.

I would appreciate any help as well.

---

### Post by awaldram on 2006-06-04
Don't want to add a me too but that's the case

changed my network to wpa just to get it working 
also in my case wont connect to non-encrypted netork same problem.

this is the case for my prism2 (hostap) and prism54 (prism54) cards with both 2.6.15-23 ans custom 2.6.16 so I believe this is a wpa_supllicant issue (manualy using wpa_supplicant gives the same issue.)

Yet gnome network can connect fine so it's not a driver problem as such.

But gnome netorks about as mouch use as a chocolate fireguard on a laptop that roams (plus no wpa)

and Network Manager at present is practicaly unusable.

---

### Post by phonebox on 2006-06-04
Not sure if this is the real reason, but I was looking through the forum and found a thread which seemed to imply that NM didn't work with 'shared key' WEP.

So I booted into WinXP on the same machine and used wireless to connect to the router and changed the authentication from 'shared key' to 'open' (I left everything else the same inc the actual 128-bit WEP key). Then i rebooted into Ubuntu and NM asked for the WEP key, and then the gnome keyring password, and it connected fine.

So it seems either:
1: NM doesn't like 128-bit WEP 'shared key' but 128-bit WEP 'open' authentication is fine.
2: Booting into WinXP and using the wireless there and then rebooting into Ubuntu (not powering off and then restarting, just restarting from WinXP) does something to the wireless card.

BTW this was all done on a dell inspiron 8600 with intel 2200 wireless (using ipw2200 v1.1.1) with dapper. Also, i entered the WEP key in hex.

EDIT: Just tried it with a cold boot and it works fine as well. So it seems to be the 'shared key'/'open' authentication solution.

---

### Post by monkeyhelper on 2006-06-04
I see the same symptoms when using network manager and attempting to use WEP.  I have the Intel 2200 chipset also.  The network manager authenticates correctly when there is no encyption on my wireless network, however fails when WEP is enabled.  I have successfully made wpa_supplicant authenticate from the command line but when using network manager I see timeouts for wpa_supplicant in the syslog output.

When authenticating with wpa_supplicant on the command line I used the following config :

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="yournetwork"
        key_mgmt=NONE
        auth_alg=SHARED
        wep_key0="somekey"
        wep_tx_keyidx=0
}

Then executed :

wpa_supplicant -c /etc/wpa-wep.conf -d -i eth1 -D wext

It wouldn't work unless I added the auth_alg=SHARED line in the configuration.    My guess is that when wpa_supplicant is invoked from the network manager it isn't setting the auth_alg correctly.  Could someone try the above example on the command line to see if they see the same results ?

To check the status of the wpa_supplicant connection - use :
wpa_cli
status

---

### Post by andy101 on 2006-06-04
Does it work if you try setting it using iwconfig?

Mine won't work unless I use iwconfig to set the essid and then set the wep key. and I seem to have to do that every boot.

---

### Post by laroetman on 2006-06-04
[QUOTE=phonebox]Not sure if this is the real reason, but I was looking through the forum and found a thread which seemed to imply that NM didn't work with 'shared key' WEP.

So I booted into WinXP on the same machine and used wireless to connect to the router and changed the authentication from 'shared key' to 'open' (I left everything else the same inc the actual 128-bit WEP key). Then i rebooted into Ubuntu and NM asked for the WEP key, and then the gnome keyring password, and it connected fine.

So it seems either:
1: NM doesn't like 128-bit WEP 'shared key' but 128-bit WEP 'open' authentication is fine.
2: Booting into WinXP and using the wireless there and then rebooting into Ubuntu (not powering off and then restarting, just restarting from WinXP) does something to the wireless card.

BTW this was all done on a dell inspiron 8600 with intel 2200 wireless (using ipw2200 v1.1.1) with dapper. Also, i entered the WEP key in hex.

EDIT: Just tried it with a cold boot and it works fine as well. So it seems to be the 'shared key'/'open' authentication solution.[/QUOTE]

I just tried this, and it works for me too.   SO, WEP with Open key works, but WEP with Shared key does not work, and WPA does not work.  This is driving me crazy!  ](*,)   I've read forum upon forum trying to figure this out, and no luck.  :(  At least you guys got me this far.  Thanks!  :-D

---

### Post by monkeyhelper on 2006-06-05
I have raised a bug in launchpad for this :

[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/48473](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/48473)

---

### Post by andersonmanly on 2006-06-06
I have an HP-DV1000 with the intel 2200 wireless card. I've been experiencing the same difficulty, but found a workaround by clicking "Connect to another wireless network...", entering essid and wep key (WEP 64/128-bit Hex). Not sure why this works. My suspicion is that gnome-network-manager is not communicating with the stored keyring.

---

### Post by anton.b on 2006-06-07
It seems that different drivers have different levels of issues with gnome-network-manager. My acx card doesn't work no matter what type of security (even none) I use. My suspicion is that it has something to do with the drivers. The acx drivers doesn't support WPA and if gnome-network-manager wants to try and connect via WPA first every time, it is obviously not going to work. Anyway, hope the launchpad bug solves the problems :)

---

### Post by unclben on 2006-06-15
I also have an IPW2200 card. Using network-manager, I can easily connect to unencrypted networks. Unfortunately, I can't connect to encrypted networks of any kind. I've tried WEP open, WEP shared, and WPA-PSK; none of them will connect.

I'm doing all this testing on the LiveCD, if that makes any difference.

---

### Post by deathshadow on 2006-06-18
I've been struggling with similar issues in Xubuntu for a couple days now - ever since I upped to Dapper. 

Out of box my RA2500 based el-cheapo "Ark" adapter was recognized, and I could connect without WEP, or in WEP Open.... but not WEP shared (which I have to use because of a win98 laptop that needs to connect, which doesn't work with WEP open, and the wireless router is too old to even KNOW what WPA is)... 

Thing is, this is EXACTLY the same problem I had before with previous versions of ubuntu... the normal fix, editing /etc/network/interfaces to include the line:

wireless-key restricted xxxxxxxxx

didn't work... but, if I set up the key using the system>Networking panel, then ran from a terminal:

iwconfig ra0 key restricted

It came right up!!! ok, we're on to something... So digging through the docs to find a way to make this permanant, I noticed on this page:
[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)

the following line:
wireless-key XXXXXXXXXX open|restricted (if using shared/restricted setting add this line)

AHA!!! THEY REVERSED THE FRACKING ORDER FROM WHAT PREVIOUS VERSIONS USED!!!!!

so, just set up the network with the system>Networking panel, edit /etc/network/interfaces so the wireless-key line has restricted at the END of the line, not between wireless-key and the password like previous versions (and how every existing online help page for older versions say to do it)... Reboot (or reset the device) and it should come right up.

Silly {censored} question, but is it too damned much to ask that the Networking panel have a {censored} checkbox to add/remove the 'restricted' keyword from the appropriate line?

---

### Post by dereknet on 2006-06-21
I'm having very similar problems with network manager completely failing for wireless connections. My current setup consists of a laptop with a Lucent 802.11b MiniPCI card that connects fine when I uses the Gnome networking config or WifiRadar. When I attempt to connect with NM I time out the DHCP request for some reason. I've attempted both HEX / ASCII for my 64 bit WEP password (I'm using an old airport basestation). NM works great when I plug in my wired ethernet connection, but otherwise any wireless conectivity must be manually done using WifiRadar.


Any suggestions....?? This sucks especially when I've dumped XP and gone Ubuntu  full time! thanks!

```
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): Wireless event: new AP: 00:60:1d:f1:12:3f 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): State: ASSOCIATING -> ASSOCIATED 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): Associated with 00:60:1d:f1:12:3f 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 30 30 2d 31 32 00 0a df 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): WPA: Association event - clear replay counter 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): EAPOL: External notification - portEnabled=0 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): EAPOL: External notification - portValid=0 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): EAPOL: External notification - portEnabled=1 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): EAPOL: SUPP_PAE entering state S_FORCE_AUTH 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): EAPOL: SUPP_BE entering state IDLE 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): Cancelling authentication timeout 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): Removed BSSID 00:60:1d:f1:12:3f from blacklist 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): State: ASSOCIATED -> COMPLETED 
Jun 21 16:49:08 localhost NetworkManager: <information>^Iwpa_supplicant(3477): CTRL-EVENT-CONNECTED - Connection to 00:60:1d:f1:12:3f completed (auth) 
Jun 21 16:49:09 localhost NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1 
Jun 21 16:49:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun 21 16:49:16 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jun 21 16:49:21 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Jun 21 16:49:35 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Jun 21 16:49:49 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 21 16:49:53 localhost NetworkManager: <information>^IDevice 'eth1' DHCP transaction took too long (>45s), stopping it. 
Jun 21 16:49:56 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jun 21 16:49:56 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth1 
Jun 21 16:49:56 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jun 21 16:49:56 localhost NetworkManager: <debug info>^I[1150933794.897658] real_act_stage4_ip_config_timeout (): Activation (eth1/wireless): could not get IP configuration info for 'Base Station Ellis', asking for new key. 
Jun 21 16:49:56 localhost NetworkManager: <information>^IActivation (eth1) New wireless user key requested for network 'Base Station Ellis'. 
Jun 21 16:49:56 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jun 21 16:49:56 localhost dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Jun 21 16:49:56 localhost dhclient: send_packet: Network is unreachable
Jun 21 16:49:56 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jun 21 16:49:56 localhost NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth1 
Jun 21 16:49:56 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth1 
```

---

### Post by anton.b on 2006-06-22
I'm sorry to say but this is definitely **not** the same problem. You get associated with your access point without problems whereas the rest of us doesn't get connected at all.
The only piece of advice I can give you is to try and edit /etc/network/interfaces manually, restart the computer and see if the network does come up now. If that doesn't work either, you have a configuration issue somewhere in your network but if it does work, you at least know NM is causing some problems for you as well. In that case, you could file a separate bug report on your issue.

---

### Post by jradvan on 2006-06-22
[QUOTE=deathshadow]
wireless-key restricted xxxxxxxxx
[/QUOTE]

This worked for me. I had the same problem - WEP/shared on a Dell D600 with ipw2200BG on ubuntu 6.06.  Changing the line to 
wireless-key restricted nnnnnnnnnnnnnnnnnnnnnnnnn
fixed it.  Changing it to
wireless-key nnnnnnnnnnnnnnnnnnnnnnnnn restricted
did NOT fix it.

---

### Post by deathshadow on 2006-06-24
[QUOTE=jradvan]This worked for me. I had the same problem - WEP/shared on a Dell D600 with ipw2200BG on ubuntu 6.06.  Changing the line to 
wireless-key restricted nnnnnnnnnnnnnnnnnnnnnnnnn
fixed it.  Changing it to
wireless-key nnnnnnnnnnnnnnnnnnnnnnnnn restricted
did NOT fix it.[/QUOTE]

I just figured out it seems to vary depending on what chipset the wlan is... it seems the RT2500 driver that comes with ubuntu reverses that line, while every other driver out there that uses 'restricted' to indicate a shared key do it the way it worked for you on your intel chipset... (JOY!) 

Fun thing is, I can tell the RT2570 USB wireless I have for my G3 iBook has the same exact problem connecting to my AP, but won't take EITHER way of adding the word restricted, but DOES come up when I do:

iwconfig ra0 key restricted

So I just made a launcher to do that in my XFCE menu. (running Xubuntu there) Not a great solution, but it works.

---

### Post by unclben on 2006-07-31
I thought it might be useful to post an update about my IPW2200BG on Dapper. I did a clean Dapper install a few weeks ago, and just used the standard network manager to connect to the plethora of unencrypted networks (which have always worked just fine) in my apartment building.

I heard some rumblings in the forums about how the last kernel update was supposed to improve wireless functionality (for at least some cards), so I figured 'what the heck?' and installed network-manager-gnome. I logged out, logged back in, and all kinds of wireless networks (open, WEP, WPA) now work automagically! w00t!

---

### Post by haloedrain on 2006-09-14
I was thinking I probably had the same problem as you guys were saying here, I can connect just fine to a wired network but for the most part I cannot connect to a wireless network with a WEP shared key.  On occasion I can manage to connect by going to "Connect to other wireless network" and entering the network name, key etc., but that works maybe 5% of the time.  When it does it asks me for a new keyring password.

I am not the network manager, this is a campus network, so I can't really change the type of encryption and test stuff to see if it works under other conditions, but since it has worked before I don't think it's the driver.

However, the "restricted" thing doesn't seem to apply here, despite everything being similar--the word "restricted" doesn't appear anywhere in the file?

I'm pretty new to linux so I have *no idea* where to look now.  It seems like it might be something to do with getting things into/out of the keyring??  But I don't know what/where that is.

---

