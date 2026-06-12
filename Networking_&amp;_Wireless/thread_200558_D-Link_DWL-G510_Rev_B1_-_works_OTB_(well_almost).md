---
title: "D-Link DWL-G510 Rev B1 - works OTB (well almost)"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Watchin on 2006-06-20
Just installed the Dlink DWL-G510 rev b1 wireless PCI card into my Ubuntu 6.06 system, and it worked Out Of The Box !!!

You do have to remove/disable the ethernet interface (I just pulled the NIC). 
and play with the network monitor and Network Control panel to get things 
configured.

If you set up your wireless without encryption (in the access point) first then the setup will
go smoothly to tell you if you got everything running rightly. I'd then go back and set the access point
to WPA/TKIP with a passphrase, apply/reset the access point (or router). Then do the Network Manager
click phase to set the password appropriately.

Note on the 510 - It comes up as interface ath0 not eth0 

Tips,
a) configure with the Network Monitor applet 
right click in panel, 
->add to panel,
double click icon,
enter ath0 in name,
click configure
click on Wireless connection
click on Properties
click on Enable this connection
DO NOT enter SSID
DO NOT enter the wep key (whatever you're using)
Connection settings configuration -> DHCP
click OK
wait for it.....
click on Default Gateway and select ath0
wait for it ....
click OK until all the windows are gone

check the /etc/network/interfaces per [ this note]("http://ubuntuforums.org/showpost.php?p=1081895&postcount=6") so the Network Manager will take care of the password stuff 
Be sure to restart everything as it says.

then click on the Network Control icon (next to the clock)
select your network SSID 
enter the password again
enter a password to protect the saved passwords (can be anything)
the little thingy will spin and you should be there....

b) when installing the card, I'd recommend you install it above the sound card.
In my case it work only when installed just below the video card with NO Nic card 
installed. (several reboots and trial / error to find that).

Have fun !!!

edit - rather than add replies to this list I'm updating it as I go along. 
6/21 - added note on turning off ipv4 and resetting the  Network monitors so it configures on the fly at startup

---

### Post by Watchin on 2006-06-20
Well it appears that it did work OTB, until I did an upgrade....ARGH.

Now I've back to square one, reinstall 5.10 and try it all again (much more carefully).

Why do I put myself through this agrevation???

---

### Post by ShinjiLeery on 2006-06-21
Hi,
I use this topic beacuse i have a DWL-510 too. With breezy all works with ndiswrapper & windows driver (rtl8180) but in Dapper i have this problem. 
Dapper has a driver in the kernel to use this wireless card, infact after the installation if i do a iwconfig i have this response:

```
wlan0      IEEE 802.11b link.  ESSID:"XXXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not associated
          Bit Rate=11 Mb/s    Sensitivity=80/85
          Retry:on      Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-255 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I work with a restricted key so i insert the R. key in the interface file in this way:

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
wireless-essid XXXXXX
wireless-key restricted XXXXXXX
wireless-channel 11
```

in this way the system freezes at boot. If i use the comand:

```
sudo iwconfig wlan0 key restricted XXXX
```

ubuntu freeze in the same way.
There's a problem with the restricted keys?

tnx. :cool:

---

### Post by Watchin on 2006-06-21
Well I'm reloaded and stable again... 

I found a clue to my problems,
I needed to turn off IPV6 because  my router didn't support it and
caused the connection to reject and never connect again. It worked
once because I had first done a fixed IP addr, then changed to DHCP.

So I created an /etc/modprobe.d/bad_list file containing 
alias net-pf-10 off
per the instructions/discussion in [ this thread.]("http://www.ubuntuforums.org/showthread.php?t=87798") <-ShinjiLeery try this with the default drivers, I got the same thing you did until I turned of 
WEP/WPA and turned off IPV6 (??why do we have a default that is only used in <20% of the nodes on the net?)


The kernel mode drivers and modules as supplied in Dapper seem to work 
just fine (in non-WPA/WEP mode).

Now I'm off to get the security stuff working. Another black hole we enter...](*,)

---

### Post by ShinjiLeery on 2006-06-21
[QUOTE=Watchin]Well I'm reloaded and stable again... 

I found a clue to my problems,
I needed to turn off IPV6 because  my router didn't support it and
caused the connection to reject and never connect again. It worked
once because I had first done a fixed IP addr, then changed to DHCP.

So I created an /etc/modprobe.d/bad_list file containing 
alias net-pf-10 off
per the instructions/discussion in [ this thread.]("http://www.ubuntuforums.org/showthread.php?t=87798") <-ShinjiLeery try this with the default drivers, I got the same thing you did until I turned of 
WEP/WPA and turned off IPV6 (??why do we have a default that is only used in <20% of the nodes on the net?)


The kernel mode drivers and modules as supplied in Dapper seem to work 
just fine (in non-WPA/WEP mode).

Now I'm off to get the security stuff working. Another black hole we enter...](*,)[/QUOTE]

I tried to turned off ipv6 but i have the same problem, when i insert the key restricted the whole system halt. I can't turned off the WEP key beacuse i'm not the only one who uses the access point. 
Is that possibile that with breezy & ndiswrapper all works and with dapper ther's a going back?  ](*,) 

I start to think that Dapper has more problem than breezy at this time ...

---

### Post by Watchin on 2006-06-21
You don't have to turn off the WEP, just don't enter the key into the configuration page on the network monitor application. Wait until the 
NetworkManager applet asks you for it then enter it...

I'm installing this on Dapper (6.06 LTS) so it should work for you.

---

### Post by ShinjiLeery on 2006-06-22
[QUOTE=Watchin]You don't have to turn off the WEP, just don't enter the key into the configuration page on the network monitor application. Wait until the 
NetworkManager applet asks you for it then enter it...

I'm installing this on Dapper (6.06 LTS) so it should work for you.[/QUOTE]

Done. But i have the same, problem... The system freeze about ten second after i insert the key. It's the same behaviour that i see without the Network manager... What can i do? ](*,)

---

