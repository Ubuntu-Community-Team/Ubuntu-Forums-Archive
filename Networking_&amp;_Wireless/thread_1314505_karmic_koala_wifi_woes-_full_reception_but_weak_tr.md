---
title: "karmic koala wifi woes- full reception but weak transmission"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Dave Noobie on 2009-11-04
Hi people,

Okay... So, I'm using a D-Link DWA-510 pci card and I'm connecting to a D-link DIR-300 AP. Before upgrading I was using 9.04 without a hitch. Since upgrading my connection appears fine, network manager tells me 77% signal strength and yet I have fluctuating speeds, from 52mb/s to sub 5kb/s or none at all on broadband. It almost feels like it's stalling. I was hoping someone with more experience could look over the details and tell me if I'm missing something.

uname - mr
```

2.6.31-14-generic i686

```

iwconfig wlan0
```

wlan0     IEEE 802.11bg  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          [COLOR=Red]Link Quality=52/70[/COLOR]  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
There was another post mentioning Link Quality not being /100 as a possible cause and suggested this was a kernel isssue. Could this have any bearing?


lspci -nn | grep RaLink
```

02:01.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]

```

lsmod | grep rt61
```

rt61pci                20576  0 
crc_itu_t               1852  2 udf,rt61pci
rt2x00pci               7900  1 rt61pci
rt2x00lib              29756  2 rt61pci,rt2x00pci
eeprom_93cx6            1916  1 rt61pci

```

Any suggestions would be greatly appreciated. :D

---

### Post by 00ber n00b on 2009-11-04
I also get 70/70 link quality now.

---

### Post by 00ber n00b on 2009-11-04
I have also noticed that it defaults to 36Mb/s on my system and if I change it to 54Mb/s it is less stable.  Maybe you can try 

sudo iwconfig wlan0 rate 36M

---

### Post by Monker1980 on 2009-11-19
Dave, ever get to the bottom of this?

---

### Post by tacantara on 2009-11-19
> **00ber n00b said:**
> I have also noticed that it defaults to 36Mb/s on my system and if I change it to 54Mb/s it is less stable.  Maybe you can try 

sudo iwconfig wlan0 rate 36M


I've been experiencing the same sluggish internet speed since upgrading to Karmic.  I applied the tip you suggested, and noticed the difference.

---

### Post by cloakable on 2009-11-20
Also, try:
> sudo iwconfig wlan0 power off

It'll switch off power management on the device. I was having similar problems to you until I did that. Now I'm connecting fine, even at 54Mb/s speeds.

Just need to find a way to make that persistent over reboots and suspends.

---

### Post by tacantara on 2009-11-20
> **cloakable said:**
> Also, try:```
sudo iwconfig wlan0 power off
```


It'll switch off power management on the device. I was having similar problems to you until I did that. Now I'm connecting fine, even at 54Mb/s speeds.

Just need to find a way to make that persistent over reboots and suspends.

I tried the command that you recommended, but I got the following error message

```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```Apparently this isn't an issue caused by using Karmic, as I see you're using it as your OS.  Could it be something to do with Network Manager (i.e. should I switch to another network management tool - I can't remember the name of the other network tool that everyone seems to like)?

---

### Post by CoyoteDen on 2009-11-20
It's not just the RALink cards. My laptop has a BCM4322 (Broadcom STA driver). The receive appears to be fine, but transmit power is nonexistant. I can scan and see both my b/g/n and a/n SSIDs from out in the parking lot :P but the AP never even sees the laptop until I'm right next to it. If I sit on top of my AP, I *might* get it to associate on the b/g/n SSID. 

Under WIndows 7. the same machine has slight problems with the a/n-band dropping off, but the b/g/n-band is rock solid.

My numbers are something like this:

          > 
eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Now this part is really funny:

> root@trickster:/proc/net# iwlist eth2 txpower
eth2      2 available transmit-powers :
      0 dBm      (1 mW)
      25 dBm      (255 mW)
          Current Tx-Power:32 dBm      (1496 mW)

Over 1 watt of TX power for wifi? I can feel my brain cooking, and still no connection...

---

### Post by veroxii on 2009-12-02
> **cloakable said:**
> Also, try:


It'll switch off power management on the device. I was having similar problems to you until I did that. Now I'm connecting fine, even at 54Mb/s speeds.

Just need to find a way to make that persistent over reboots and suspends.

Thanks. It seems to work for me.

And to persist it over reboots I did the following:

At the top of /etc/network/if-pre-up.d/wireless-tools I changed the file to be:

```

IWCONFIG=/sbin/iwconfig
IF_WIRELESS_POWER=off

```I then also had to link that file into the if-up.d directory, since networkmanager doesn't support if-pre-up.d:

```

cd /etc/network/if-up.d
sudo ln -s /etc/network/if-pre-up.d/wireless-tools

```Now iwconfig reports power management:off for me after reboots.

Hope it helps!
-V

---

### Post by james_fried on 2010-07-16
> **veroxii said:**
> Thanks. It seems to work for me.
And to persist it over reboots I did the following:


Thanks to veroxii for the information on how to persist the "ifconfig power off" setting over reboots - very helpful! :D

I used your solution on Lucid to fix the error I was getting in my kernel log resulting from power manager not working correctly with my wireless card:

```

kernel: [ 1067.384294] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).

```

The bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456977"), I just thought it might be helpful to tie the two things together.

Cheers!

J

---

