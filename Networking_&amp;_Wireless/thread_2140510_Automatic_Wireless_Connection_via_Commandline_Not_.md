---
title: "Automatic Wireless Connection via Commandline Not Obtaining IP"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by KommaH on 2013-04-29
I'm following the instructions detailed here: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

I have created the wpa.sh script and set it to execute automatically at boot via init.d. As far as I can tell, the execution is successful. The only issue is that eth1 isn't obtaining an IP address automatically. After logging in, I have to execute the command "sudo dhclient eth1" automatically in order to be able to browse the internet.

I have tried adding eth1 to /etc/network/interfaces, but this for some reason conflicts with wpa.sh, causing the device not to appear in ifconfig at all (unless I use the -a flag).

This is my current interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


#auto eth1
#iface eth1 inet dhcp


#pre-up /etc/init.d/wpa.sh start
#post-down /etc/init.d/wpa.sh stop

```

---

### Post by KommaH on 2013-04-30
No advice from anyone? :(

---

### Post by steeldriver on 2013-05-01
I don't understand why you are trying to do it that way? it should be possible to bring up the interface automatically from /etc/network/interfaces without needing to script anything - for example here is a simple template for a WPA-PSK connection  on wlan0 with DHCP and the LAN router (192.168.1.1) providing name  resolution:

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *your-ssid*
    wpa-psk *your-passphrase*
dns-nameservers 192.168.1.1

```

---

### Post by KommaH on 2013-05-01
> **steeldriver said:**
> I don't understand why you are trying to do it that way? it should be possible to bring up the interface automatically from /etc/network/interfaces without needing to script anything - for example here is a simple template for a WPA-PSK connection  on wlan0 with DHCP and the LAN router (192.168.1.1) providing name  resolution:

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *your-ssid*
    wpa-psk *your-passphrase*
dns-nameservers 192.168.1.1

```
Thanks for the reply. However, before I was able to try this, a I encountered a new problem. When I switched from a WEP-secured WiFi network to a WPA2-secured WiFi network, the computer no longer connects to wireless. I've connected to this wireless network before using GNOME before, so I know it's not an issue with the network.

I'm using iwconfig to connect. At first, I thought I had the key wrong, but when I looked at the output for iwconfig, I noticed that the BitRate was at 0 and that I wasn't getting any lost traffic or undecryptable traffic. The computer doesn't appear to be communicating with the WPA2 network at all. dmesg and syslog give no hints as to what is wrong.

Here's the command I'm using:
```
sudo iwconfig eth1 essid test-net key s:Wireless
```

I'm at a loss for what to do. Am I forgetting a flag for iwconfig to switch to WPA2 or something? :confused:

---

### Post by steeldriver on 2013-05-01
So which is it? as far as I know, iwconfig cannot be used to connect to WPA (the 'key' field only supports WEP keys, not WPA passphrases) - the man page says:

 ```

              To set the current encryption key, just enter  the  key  in  hex
              digits  as  XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a key other
              than the current key, prepend  or  append  [index]  to  the  key
              itself (this won't change which is the active key). You can also
              enter the key as  an  ASCII  string  by  using  the  s:  prefix.
              **Passphrase is currently not supported.**

```

Perhaps you should take a step back and post your wireless hardware details - there may be known issues with it

---

### Post by matt_symes on 2013-05-01
Hi

Steeldriver is correct. You must use wpa_supplicant to connect to a wpa encrypted network.

iwconfig will not allow you to connect to it; only open and wep encrypted networks.

Kind regards

---

### Post by chili555 on 2013-05-01
> sudo iwconfig eth1 essid test-net [COLOR="#FF0000"]key s:Wireless[/COLOR]^^^This is appropriate for *WEP* with an ASCII key.> auto wlan0
iface wlan0 inet dhcp
    wpa-ssid your-ssid
    [COLOR="#FF0000"]wpa-psk your-passphrase[/COLOR]
dns-nameservers 192.168.1.1^^^And this is the method to use WPA2-PSK. It works perfectly well including in my system right here, right now.

I am unaware of any method to connect to WPA2 at the command line without calling a carefully crafted wpa-supplicant conf file. But why bother when /etc/network/interfaces is so easy.

---

### Post by KommaH on 2013-05-01
Thank you for all of the replies! I really appreciate the help!

> **steeldriver said:**
> ```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid [COLOR=#000000]*your-ssid*[/COLOR]
    wpa-psk [COLOR=#000000]*your-passphrase*[/COLOR]
dns-nameservers 192.168.1.1

```

So, is this what the block for my wireless device in my interfaces file look like this?
```

auto eth1
iface eth1 inet dhcp
    wpa-ssid test-net
    wpa-psk Wireless

```

Or, would I have to use the psk generated by putting my wireless details in wpa-supplicant?

---

### Post by chili555 on 2013-05-01
> So, is this what the block for my wireless device in my interfaces file look like this?Almost. You will need to add DNS nameservers as above. The entry for wpa-psk is the actual key that you set in the router in clear text. 

I suggest:```
auto eth1
iface eth1 inet dhcp
wpa-ssid test-net
wpa-psk Wireless
dns-nameservers 192.168.1.1 8.8.8.8
```... or any other valid DNS nameserver address(es).

---

### Post by KommaH on 2013-05-01
Alright, thanks. I'm going to try this tomorrow. I'll let you guys know how it goes!

---

### Post by KommaH on 2013-05-04
> **chili555 said:**
> Almost. You will need to add DNS nameservers as above. The entry for wpa-psk is the actual key that you set in the router in clear text. 

I suggest:```
auto eth1
iface eth1 inet dhcp
wpa-ssid test-net
wpa-psk Wireless
dns-nameservers 192.168.1.1 8.8.8.8
```... or any other valid DNS nameserver address(es).
Unfortunately, this did not work for me. Some log investigation revealed that wpa_supplicant was having trouble using the wext drivers with my wireless card, which is weird since wext was working fine with the wireless card in another ubuntu install.

After this, I gave up and installed wicd to configure the connection for me. Everything is working fine now. :)

---

