---
title: "How to change wireless network priority?"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by vacco on 2010-10-09
OK, so I have NetworkManager connecting automatically to the wireless network in my apartment, and to the wireless network at campus (eduroam).
My problem is that the university have its network available multiple places around town, which means it also covers my apartment.

Now, when I boot my computer at home, NetworkManager automatically connects to eduroam instead of my home network (despite stronger signal from my home network whose router is around 1 meter away).

Windows has a network management tools which allow me to select priority of the different wireless networks configured. Is there any way to do this in Ubuntu?
I have looked in System-->Preferences-->Network connections (translated on the fly as my UI is not in English atm), but there are no priority options there.

---

### Post by arthur_8200 on 2012-04-09
Hi,

I am using Ubuntu 12.04 and I also need wlan priority.

Maybe we should make an feature request?


Regards,
Arthur

---

### Post by jawilljr on 2012-04-09
There is a way to force Network Manager to use only a certain Access Point.

At the terminal type "iwconfig" without the quotes.

Below is mine:

```
wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: [color=red]C0:C1:C0:38:4F:32[/color]   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4349  Invalid misc:109   Missed beacon:0
```

The red portion is the MAC Address of my router, higlight those on yours then copy.

Now go into Network Manager->Edit Connections->Wireless Tab and highlight your Connection->Edit BUtton

Now paste the MAC Address into the BSSID field of your connection.

Now Network Manager will only connect to that Access Point. Later you will have to add a connection with that MAC Address.

Hope this helps.

[Here is more info](http://askubuntu.com/questions/40038/how-can-i-force-network-manager-to-associate-to-a-specific-access-point)

Jerry

---

### Post by 8200 on 2012-04-10
Hi Jerry,


thank you for this hint!

In my case it's not a solution.
At home I share my mobile broadband connection via. wifi (ad-hoc) to my other notebooks. Then when I'm at work my notebook is sometimes in adhoc-mode altough there is the work-wifi.

There just the need of setting wlan prioritys.

A bug request is here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366780](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366780)

Regards,
Arthur

> **jawilljr said:**
> There is a way to force Network Manager to use only a certain Access Point.

At the terminal type "iwconfig" without the quotes.

Below is mine:

```
wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: [color=red]C0:C1:C0:38:4F:32[/color]   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4349  Invalid misc:109   Missed beacon:0
```

The red portion is the MAC Address of my router, higlight those on yours then copy.

Now go into Network Manager->Edit Connections->Wireless Tab and highlight your Connection->Edit BUtton

Now paste the MAC Address into the BSSID field of your connection.

Now Network Manager will only connect to that Access Point. Later you will have to add a connection with that MAC Address.

Hope this helps.

[Here is more info](http://askubuntu.com/questions/40038/how-can-i-force-network-manager-to-associate-to-a-specific-access-point)

Jerry

---

### Post by stilllife on 2012-11-15
up

---

### Post by mac-duff on 2013-09-22
Hi there,
I am having the exact same problem with the eduroam and my home network but I guess no one has figured something out without installing another tool right?
The strange thing is that even the dBI doesnt import anything :(

Thaks
mac

---

### Post by oldos2er on 2013-09-23
Please start a new thread, this one's quite old.

---

