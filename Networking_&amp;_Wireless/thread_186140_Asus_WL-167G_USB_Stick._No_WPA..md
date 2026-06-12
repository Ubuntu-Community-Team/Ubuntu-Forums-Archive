---
title: "Asus WL-167G USB Stick. No WPA."
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Tobbz on 2006-06-01
HI All.

So, i just finished installing Dapper, and was hoping that WPA would be supported on my Asus USB stick, but no.
The stick is supported by dapper, and it uses the default rt2500 driver.

System->Administration->Networking sees the stick/wirelesscard, and the AP, but there is no WPA option. Only WEP.

NetworkManagerApplet sees my wireless network, and sees my USB stick, but again, there is no option to use WPA.

I have install wpasupplicant,

Here is my  /etc/wpa_supplicant.conf
```

network={
        ssid="access"
        #psk="xxx"
        psk=lotsandlotsofnumbers
        key_mgmt=WPA-PSK
        proto=WPA
}

```

my iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"access"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-48 dBm  Noise level:-198 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

and my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid "access"
pre-up iwconfig rausb0 mode Managed
pre-up iwpriv rausb0 wpapsk "xxx"
pre-up ifconfig rausb0 up

```

What could be wrong? Any tips/pointers?

Has anybody out there gotten WPA to work with the Asus WL-167G? PLEASE let me know. 

TIA

Best regards

---

### Post by Sod75 on 2006-07-02
I've just spend quite some time on exactly the same issue(see subj), unfortunately with the exact same result....no go.
If you've found something meanwhile i would be grateful if you could share it with me...

---

### Post by ndiswapped on 2006-10-24
have you come across and tried this yet:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

(see section 2.2 on "WPA info")

let us know what happens...

---

### Post by jhp-dk on 2006-12-15
Hi, 
I'm new to the linux world and when i was surfing this forum before buying a wireless usb adapter i saw your thread in which you say the ASUS wl-167g is found and automaticly installed...  :confused: 
My computer didn't install my adapter when I installed Ubuntu????

any suggestion which driver will be the best?

---

### Post by murrayc on 2007-01-18
> **jhp-dk said:**
> Hi, 
I'm new to the linux world and when i was surfing this forum before buying a wireless usb adapter i saw your thread in which you say the ASUS wl-167g is found and automaticly installed...  :confused: 
My computer didn't install my adapter when I installed Ubuntu????

any suggestion which driver will be the best?

I'm having the same problem. This bug seems relevant:
[http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53221](http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53221)

---

### Post by guyjohnston on 2007-02-01
I find that it's relatively easy to get WPA working with Network Manager and the KNetWorkManager frontend. The GNOME frontend doesn't seem to let you use WPA.

---

