---
title: "Wifi N problem"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Jzz5 on 2010-02-09
Hi all,

I'm having troubles with my wireless. I installed a dualboot (Win7/UNR) on a Samsung N135 netbook. Everything worked 'out of the box', including wireless. About a week ago I purchased a brand-new wireless router, which supports wireless N. But UNR does not connect any higher than 54MB. I can't get it to work...

The netbook uses the Atheros AR9285 card and UNR uses the ath9k driver. I tried installing the backport modules:

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

but no succes. Any ideas anyone?

output of lspci -v:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Askey Computer Corp. Device 7167
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"vuurtoren2.4G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:9C:6A:97:F5   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Any help would be appreciated...

---

### Post by Jzz5 on 2010-02-12
Bump...

---

### Post by Tim_nz on 2010-02-12
tried madwifi drivers?
tried wicd network manager?
also theres a different ath9k drivers aswell something like tarbull or something i cant remember ill try to find it they worked for me

---

### Post by Jzz5 on 2010-02-12
I tried installing the newest compat drivers, that includes the newest ath9k driver (I think). No change.

Jzz

---

### Post by beegary on 2010-02-12
Have a look at this website:
 
[http://www.voria.org/forum/](http://www.voria.org/forum/)
 
Someone may have already posted your problem, otherwise the owner of the site, Voira is very helpful. I am using his scripts for my NC10, (im using Karmic not the UNR but I dont think that should matter)

---

### Post by Jzz5 on 2010-02-12
Thanks Beegary,

a lot of info there. I performed the upgrade suggested there, but it did not solve my problem. It did solve some other problems I had. Some of them I didn't even know I had...

I posted a question there and am hoping Voira can help me. I'll keep you posted here. Still looking for a solution...

Jzz

---

### Post by YoJembo on 2010-02-13
Hey there, first time poster here. I was hunting about for a while to get some info on this and was almost about to post my own question.

I should add that I'm a Linux noob and have only been using UNR for a day on my wifey's Asus 1000H.* I must say I'm very impressed!* Atm I'm running off a 1gb SD Card (installed via unetbootin)! Bit slow to start up but great when it gets going.

Anyway, I noticed the same thing as the OP. No connection higher than 54MB. I have no solutions but some observations I'd like to add. UNR would not connect with my N router. It kept asking me for the key. When I changed it's band from N only to mixed, B+G+N, low and behold it connected. (The other available options are B, B+G and G... no G+N).

It made me wonder if UNR was actually exploiting the N band. Though I haven't really tested the range reach yet. Yet however I have another G node up the other end of the house on the LAN and cannot connect via that at all even in it's B+G mixed mode.

Now I realise that Nwireless routing seems more like a black art atm than a science, there is definately exaggerated claims made. I'm still happy getting a better range with a decent signal over the rather small increase in speed exhibited in XP Home. Maybe better drivers/firmware for UNR will surface?

Please Jzz5, how is Win7 going on the Netbook? Is it slower than the XP Home?

Regards.

---

### Post by Jzz5 on 2010-02-13
YoJembo,

Since I have only Win7 on this laptop, I can't really compare them. But Win7 is quite slow. It looks nice and, to be honest, seems to work ok. However if I had to buy another netbook, I would buy one with XP. Just a little more trust in that product. I think it will fit the netbook concept better.

But since I have installed UNR, I haven't booted into Win7. The wifi problem seems to me like a driver issue. I think it will be resolved in time, one way or another.

Greetings,

Jzz

---

