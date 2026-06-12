---
title: "WPA and DHCP - Some hints and some questions"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by wannaswitch on 2006-06-04
Well, I've been mucking around with WPA, DHCP, MadWifi, and my D-Link DI-524 802.11g wireless ethernet adapter, and this is what I found.

First off, this particular ethernet card uses the Atheros chipset, which is supported by the MadWifi drivers. Those drivers come with Breezy Badger. After an agony of messing around with Ndiswrapper and various .INF and .SYS files, I discovered I didn't need any of that, I just needed what I already had. All I had to do in order to bring up the card was type:

```
sudo ifconfig ath0 up
```

Obviously "ath0" is my card, working with MadWifi. Now, my wireless router (also a D-Link) has a DHCP server, as many do, and a place to put in the SSID. In order to find the access point, the SSID on ath0 has to match the SSID specified in the router config. So the next step was:

```
sudo iwconfig ath0 essid [color=green]MySSID[/color]
```

And then to make sure the access point was found, I typed **iwconfig** again to make sure that the values of SSID and Accesspoint under ath0 were non-null. That worked. Next step: get an IP address through DHCP.

```
sudo dhclient ath0
```

Now, it's important to mention that before I tried to do this, I disabled all security on my router, leaving it open. I just wanted to see if I could get a DHCP lease. I could. So, brilliant, I could ping the router, access it's web configuration utility, and surf the Internet through Firefox. But my network was wide open and WEP is not good enough. I wanted to enable WPA. I set my router's encryption to WPA-PSK, and put in a passphrase. Applying that change severed my connection to the router, because I wasn't yet authenticated under the new security measure.

So then I opened [color=blue]/etc/pwa_supplicant.conf[/color] and added the following lines:

```
network={
        ssid="[color=green]MySSID[/color]"
	scan_ssid=1
 	#psk="[color=green]MyPassphrase[/color]"
        psk=[color=green]Passphrase in Hex Format*[/color]
	key_mgmt=WPA-PSK
	proto=WPA
}
```

*** NOTE:**  The passphrase in hex format I obtained by typing: 
```
pwa_passphrase [color=green]MySSID MyPassphrase[/color]
```

Now, I started WPA_Supplicant by typing:

```
sudo wpa_supplicant -i ath0 -D madwifi -c /etc/wpa_supplicant.conf -Bw
```

This starts the WPA_Supplicant service running in the background, using ath0, the MadWifi drivers, and the configuration settings I put in [color=blue]/etc/wpa_supplicant.conf[/color] (see above). The first time you do this, you might want to run WPA_Supplicant with the **-dd** switch as well, for extra debugging information. Once it ran, I wanted to check the status of the WPA_Supplicant service, so I typed:

```
sudo wpa_cli status
```

and the return messages said:

```
Selected interface 'ath0'
bssid=[color=green]MyAccessPointMAC[/color]
ssid=[color=green]MySSID[/color]
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
ip_address=192.168.0.101
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS
```

Good to go. Then, after some time, I decided to reboot. I wanted to make sure that everything would start up the same way the next time, without me having to do it all manually, so I made sure [color=blue]/etc/default/wpasupplicant[/color] contained the following:

```
ENABLED=1
OPTIONS="-i ath0 -D madwifi -c etc/wpa_supplicant.conf -w"
```

When the system came back up, I could not connect to the DHCP server on my router. I couldn't even ping it. I kept getting the message:

```
The network is unreachable.
```

Well, now I was stuck, because I wanted to disable WPA_Supplicant and just try to reconnect to the router without security... but the router was configured for WPA, and since I couldn't access it's configuration utility, I was shut out of it! Luckily I had another computer hard-wired to the router, and I was able to use that computer to disable WPA. Once I disabled WPA_Supplicant on my Ubuntu system, by typing:

```
sudo wpa_cli terminate
```

I was once again able to get a DHCP lease from my router. So, I concluded that dhclient was not working through a WPA-protected connection. Solution? A static IP address. I configured this in my router, associating it with the MAC address of my ethernet card (ath0). Now, to make this work, I had to go into [color=blue]/etc/network/interfaces[/color], which originally looked like this:

```
auto lo
iface lo inet loopback

iface ath0 inet dhcp
	wireless "[color=green]MySSID[/color]"

auto ath0
```

and I made it look like this:

```
auto lo
iface lo inet loopback

iface ath0 inet static
	wireless "[color=green]MySSID[/color]"
	address 192.168.0.101
	broadcast 192.168.0.255
	netmask 255.255.255.0
	gateway 192.168.0.1

auto ath0
```

Needless to say, 192.168.0.101 was the static IP address I reserved for myself in the router configuration. Then, in order to avoid rebooting, I simply brought down ath0 and then brought it back up:

```
sudo ifconfig ath0 down
sudo ifconfig ath0 up
```

and restarted WPA_Supplicant:

```
sudo wpa_supplicant -i ath0 -D madwifi -c /etc/wpa_supplicant.conf -Bw
```

And here I am to tell you about it. It's probably a bit sloppy, and I know it's a bit different from what some of you did (getting rid of the **lo** loopback references from [color=blue]/etc/network/interfaces[/color], or using Network Manager... but this is what worked for me.

Now my question is, does anybody know how to get DHCP to work with WPA_Supplicant?

---

### Post by lcg on 2006-06-05
[QUOTE=wannaswitch]Now my question is, does anybody know how to get DHCP to work with WPA_Supplicant?[/QUOTE]
There is nothing special about WPA(-PSK) and DHCP. In fact, that's what I used with Breezy in combination with ifplugd.
With Dapper, I went the network-manager route. Is there any reason you don't want to use network-manager?

HTH,
Lars

---

### Post by Mr_Cynical on 2006-06-05
So the passphrase has to be in HEX format. That's what I've been doing wrong!

---

### Post by Kimmo_S on 2006-07-05
[QUOTE=lcg]With Dapper, I went the network-manager route. Is there any reason you don't want to use network-manager?[/QUOTE]

EDIT: I am using Dapper.  Being a new user to these forums and seeing Dapper mentioned, I immediately assumed that this was the Dapper - not Breezy - section of the forum.

I'd love to hear, after days of frustration on many separate occassions, how does one go the network manager route?

My machine is an IBM Thinkpad T22, my card is an Atheros PCMCIA card (manufactued by SMC) that works fine on another linux system in the same machine.  I have an ADSL modem/router/firewall/AP in the next room.

What should I have in /etc/network/interfaces if I want to use a wired eth0 when I am not using the WLAN, but want it to switch to the WLAN immediately when I insert the card?  Network manager has been pouting up to this point until I commented out everything except the two lines related to loopback device in /etc/network/interfaces

Now nm-applet tries in vain to get an IP address for eth0.  There is no place to give it the static one it should have, because after I put one into /etc/network/interfaces, nm-applet goes sullen again.  I don't really know if network-admin and network-manager are meant to cooperate or be used alternatively.

Where should I put my WPA configuration?  There has been this far no mention of WPA in either network-admin or nm-applet.  I had /etc/wpa_supplicant.conf some time ago, and I could start WPA connection to my AP by hand, set the routes up by hand and have it working until reboot. Now I removed /etc/wpa_supplicant.conf to start from a clean slate, because there was much confusion in Debian Etch's directions for setting up WPA, and that is where a link points from Dapper's Wiki.

---

### Post by Kimmo_S on 2006-07-06
EDIT: I am using Dapper. Being a new user to these forums and seeing Dapper mentioned, I immediately assumed that this was the Dapper - not Breezy - section of the forum.

Now I am able to use NM to connect to different wireless networks.  WPA works fine and if WLAN was my only way to connect, everything would be just beautiful.

The greatest but not the only obstacle in getting it to work was to use the left mouse button after everything else was working.  Earlier it had only shown the wired network and did pretty much nothing.  Then suddenly the wireless network appeared below it.

I basically avoid clicking the applets with left mouse button, because most of the time that has been by accident, and I specifically hate it when System monitor starts by clicking the system monitor applet.

Problem remains.  If everyrthing was perfect, I'd have a choice between two locations.  Let's call them "home" and "work."

 - At work, there is only a wired LAN, with address (and DNS server addresses, this is important) obtainable via DHCP.
 - At home, there is a wired LAN, with static IP addresses, static gateway address and two DNS servers different from the ones at work.  The old network-admin had the wired LAN covered, with the exception that DNS servers obtained via DHCP at "work" always override manually typed in DNS servers accessible from home LAN.
 - At home, there is also WLAN, with IP, DNS and gateway obtained via DHCP.  I'd like the WLAN card be the default gateway device, using its DNS servers, when the card is inserted.  And after the card is removed, the system should go back to using the DNS servers and gateway address of the wired LAN.

Only one question remains.  How will I go on doing this?

---

### Post by cblanquer on 2006-07-15
Hi,

I just made it work, no hexadecimal key was necessary using some additional parameters to set TKIP.
I chose WPA with TKIP to set up my windows partition and my pocket PC accesses as well.

Instead of wpa_supplicant.conf contents:
> network={
        ssid="MySSID"
	scan_ssid=1
 	#psk="MyPassphrase"
        psk=Passphrase in Hex Format*
	key_mgmt=WPA-PSK
	proto=WPA
}


I set up with:
> network={
        ssid="MySSID"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk="MyPassPhrase"
}

...where MySSID and MyPassPhrase are of course my own ones.
I hope this helps as well. :)

---

