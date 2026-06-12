---
title: "wpa, no dhcp lease"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by dakira on 2006-01-11
Hi,

I configured the WiFi interface on my desktop computer the exact same way I did on my laptop. After I rebootet the computer I had a connection to the AP. The only problem is... I don't get a DHCP lease. I get one on the wired card no problem, but not on the WiFi. The card is a Netgear 311T with Atheros chipset (madwifi).

Here are some configuration files:
/etc/default/wpasupplicant
```

# /etc/default/wpasupplicant
ENABLED=1
OPTIONS="-w -i ath0 -D madwifi -B"

```

/etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="TheSSID"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        psk=<<HEX>>
}

```

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# LAN
iface eth0 inet dhcp

# WiFi
auto ath0
iface ath0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

The connection itself should be okay. The network monitor gives me a good looking connection icon and:
```

root@here# wpa_cli status
Selected interface 'ath0'
bssid=xx:xx:xx:xx:xx:xx
ssid=TheSSID
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS

```

I hope anyone know a solution to this problem ;(

Cheers
dakira

---

### Post by marcantonio on 2006-01-11
What AP are you using?

Also, it takes wpa_supplicant about 30 seconds or so, in my case, to actually authenticate to my AP.  Maybe running it as a preup command is not giving it enough time to connect and DHCP is timing out.  Can you run ```
dhclient ath0
``` after your sure you have authenticated to the AP?  What happens if you configure a static address?

Just trying to see if it is passing traffic after auth'd.

---

### Post by firecat53 on 2006-01-11
I had to use a static IP with madwifi and wpa. It's been awhile, so I don't remember if there have always been issues with that, but look at some of my older posts for all my config files and whatnot to get it working. 

Good luck!
Scott

---

### Post by dakira on 2006-01-11
[QUOTE=marcantonio]What AP are you using?[/quote]
Linksys WRT54GS

> Also, it takes wpa_supplicant about 30 seconds or so, in my case, to actually authenticate to my AP.  Maybe running it as a preup command is not giving it enough time to connect and DHCP is timing out.  Can you run ```
dhclient ath0
``` after your sure you have authenticated to the AP?

As said, it connects to the AP no problem.. takes a blink of an eye to connect. I also tried dhclient manually with no effect (of course I killed all possibly existing instances of dhclient before I did that).

> What happens if you configure a static address?
Works without a problem. It's just dhcp that doesn't work. And only with the WiFi interface.

If you have any more suggestions I'd be happy to try them.

dakira

---

### Post by marcantonio on 2006-01-11
Well, as firecat53 said, I've had this issue before.  It wasn't with madwifi, it was the AP (a D-Link), which is why I asked about your AP.  A firmware upgrade on my AP fixed that issue.  Did you check Linksys?

---

### Post by dakira on 2006-01-12
[QUOTE=marcantonio]Well, as firecat53 said, I've had this issue before.  It wasn't with madwifi, it was the AP (a D-Link), which is why I asked about your AP.  A firmware upgrade on my AP fixed that issue.  Did you check Linksys?[/QUOTE]

The point is: it WORKS with ipw drivers on my notebook and everywhere else. It just doesn't work on my Desktop with madwifi. I'm gonna install new (custom linux) firmware anyway sometime in the future. But I DO have the current "official" Linksys firmware.

Someone else in a German forum pointed out that this MIGHT be an issue with either madwifi or wpa_supplicant. The funny thing is: You can patch EITHER madwifi OR wpasupplicant to get dhcp working. People are not sure, yet, which of them is responsible for the problem. But it definitely seems to be a problem with the versions supplied with Ubuntu.

Here's a link to the problem description and both of the patches:
[http://sourceforge.net/mailarchive/message.php?msg_id=13050256](http://sourceforge.net/mailarchive/message.php?msg_id=13050256)

Cheers
Matthias

---

### Post by dakira on 2006-01-23
Okay folks, I solved that problem. As I mentioned before, others figured out it was an incompatibility between madwifi and wpasupplicant. That appears to be true, as patching wpasupplicant solved my problem.

So if you have an Atheros based chipset (i.e. you use madwifi) and want to use wpasupplicant without being forced to use static IPs there is a solution now.

The problem is described in the [madwifi mailinglist]("http://sourceforge.net/mailarchive/message.php?msg_id=13050256").

I'll explain in short, what you need to do. If you want details just contact me.
[LIST]
[*]get the sources for wpasupplicant and linux-resticted-modules through *apt-get source*
[*]patch driver_madwifi.c from wpasupplicant as suggested [here]("http://hostap.epitest.fi/bugz/show_bug.cgi?id=63"). Its only one line. You can change it manually
[*]compile wpasupplicant and replace the existing binaries with the new ones. Beware that coompilation depends on the madwifi sources (which is why you have to get the linux-restricted-modules sources which contain madwifi). You have to make a config file and tell it where to find the madwifi sources.
[/LIST]
If you need more details, just ask. I might even write a Wiki contribution with detailed instructions if there is any demand.

peace out
dakira

---

