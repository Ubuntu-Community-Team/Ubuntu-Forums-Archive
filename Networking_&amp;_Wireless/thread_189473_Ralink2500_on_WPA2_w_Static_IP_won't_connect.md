---
title: "Ralink2500 on WPA2 /w Static IP won't connect"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by sulu on 2006-06-05
Hey there,

I've only yesterday changed from Windows to Ubuntu but i can't get my Wlan to work. (WMP54G [Ralink2500] on Linksys WRT54GS /w WPA2 PSK (aes) and Static IP's)

The Card is detected properly as ra0 and it even finds the Network in the Kwifi Manager but I can't get it to connect to my Lan.
I've pretty much searched through the forums and google and tried out various howtos, configuring the Supplicant and that wireless-install script from the forums but i seem unable to get it to work.

I hope there's someone out there with a similiar setup who would have some clues in linux-newbie comprehensive mode? =D

Thanks a lot in advance.

---

### Post by sulu on 2006-06-05
I think I'm getting closer now.

Here are the files I have changed and the IFconfig and iwconfig.

**ifconfig**
eth0      Protokoll:Ethernet  Hardware Adresse 00:13:D4:30:90:E7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Basisadresse:0xe000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:63464 (61.9 KiB)  TX bytes:63464 (61.9 KiB)

ra0       Protokoll:Ethernet  Hardware Adresse 00:12:17:83:48:AA
          inet Adresse:192.168.5.100  Bcast:192.168.5.255  Maske:255.255.255.0
          inet6 Adresse: fe80::212:17ff:fe83:48aa/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44743 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:1791270 (1.7 MiB)
          Interrupt:66



**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WlanDo"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-74 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**/etc/wpa_supplicant.conf**
ctrl_interface=/var/run/wpla_supplicant
eapol_version=1
ap_scan=1
network={

ssid=WlanDo
scan_ssid=1
proto=RSN
keymgmt=WPA-PSK
pairwise=CCMP
group=TKIP CCMP
psk=Ófº#Îa!1{KM$OFu{"Åðp|òÖ*ÕÔP«ŒýW'R*x8:oÒIdÒ³UŠ±kMÔ~)ó7{ácÌŠwéDžI

}


**/etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

iface ra0 inet static
pre-up /usr/sbin/wpa_supplicant -D wext -i ra0 -c /etc/wpa_supplicant.conf -Bw; sleep 8; post-down killall -q wpa_supplicant auto ra0
address 192.168.5.100
netmask 255.255.255.0
gateway 192.168.5.1

#auto ra0

**/etc/default/wpasupplicant**
Enabled=1

---

### Post by sulu on 2006-06-05
does anyone have an idea? :confused: :confused: :confused:

---

### Post by sulu on 2006-06-06
Hey!

I've kept trying to change around the settings a bit with configurations ive found here on the forums but i don't seem to get any closer. 

The Ralink Rt2500 is a quite common card, isn't there anyone out there who's got some experience with getting it to work? 

Also can anyone confirm that the Ralink Rt2500 driver that comes with Ubuntu doesnt support WPA?

---

### Post by polo_step on 2006-06-06
[QUOTE=sulu]
Also can anyone confirm that the Ralink Rt2500 driver that comes with Ubuntu doesnt support WPA?[/QUOTE]

[FONT="Courier New"]I saw in another thread the claim that there is no official WPA wireless support in 6.06 *at all.*  I do hope this is an error and if so that someone will correct it.

Sorry your question isn't getting any action here.

I have an RT2500 PCI in my notebook and require WPA/AES, so I'm keeping an eye on this in case I ever make the move to Ubuntu in the notebook, which won't happen without more coherent wireless support.[/FONT]

---

### Post by queenorych on 2006-06-21
As I understand it rt2500 does not work with wpasupplicant.  The rt2500 has its own implimentation of wpa.  You must disable wpasupplicant, and follow the howto on the rt2500 site.

---

### Post by jml on 2006-06-21
queenorych is right.  wpa_supplicant does not support thr rt2500 chipset.  Yuo need an application called raconfig which is available from thr rt2500 web site, I don't have the link.  You need to remove wpa_supplicant from your system, along with the include ra-link drivers.  Then install the rt2500 driver and raconfig.  To be honest, I was never able to get it to work.  I gave up and got a card with the Ateros chep set and that works.  

6.06 still does not support WPA with a graphical front end, even with an Atheros based card.  For my laptop, I've moved to Mandriva 2006.  works very well.  Kanotix 2005-4 also supports WPA supplicant.  Hope this helps.

Joe

---

### Post by queenorych on 2006-06-21
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) is the home page for rt2500.  I havn't tried it, but the rt2x00, the new rt2500 (still early in development) is supposed to support wpasuppliment.

From what I hear, wpa is supported quite well with the rt2500 driver, though you have to get through a text only command line interface.

On a side note, A good number of people are having trouble getting the rt2500 to conenct to even an unsecured network.  I suspect the premptive kernel, or the cvs driver that was included with dapper.   I'm not sure if wpasuppliental is loaded, but that could be a problem.  If I were you I'd try the new cvs rt2500, then if that doesn't work, then the rt2x00.  It's pretty easy to compile (see readmes).

Good luck, and be sure to report back when you get it working!

---

### Post by wieman01 on 2006-06-24
Hello, 

Would you want to try this? I went through the same stuff, so this thread may help...

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")


I used NDiswrapper with Linksys (wusb54g v4) and WPA2/AES/PSK plus static IP. It works fine (also for ipw2200 by the way).

---

