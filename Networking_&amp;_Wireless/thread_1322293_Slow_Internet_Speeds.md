---
title: "Slow Internet Speeds"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by zachHH on 2009-11-10
Under Ubuntu, I am using the RTL8187b wireless card, which now works out of the box from Ubuntu 8.04+. However, I am experiencing slow download and internet download speeds using my wireless connection, fractions of those on my windows computers.

My router is the WRT54G, able to output 54mbs, (and I have comcast high speed) however, when I run 
```
sudo iwlist rate
```

I get 
```
wlan0     unknown bit-rate information.
          Current Bit Rate=24 Mb/s

```

This is getting frustrating! Any help?

Thanks!

---

### Post by Edutron on 2009-11-11
I seem to have the same problem: in XP I get 5 Mbs, and in Ubuntu it ranges from 1 to 4 Mbs.

I have found many people suggesting that if Internet goes slow (terribly slow) you should disable IPv6. I don't think this will solve your problem, since you say you still have a fraction of the speed you had.

However, I think the following helped in my case (previously I had only 1 Mbs):
- Right click on the Wireless Network Connection icon => Edit connections => Wireless
- Select your network and click on edit.
- Ipv4 tab => Method: Automatic (DHCP) adresses only.
- In the DNS servers field, introduce your ISP DNSs. Look for them on Google or, if necessary, call your ISP and ask.


I do not know if this will really improve your situation. If somebody else knows about this problem, please contribute. Everything I've found until now just recommends to disable IPv6.

---

### Post by oldgeekster on 2009-11-11
Just jumping in here to say this complaint seems to be common with Karmic Koala at this point. I have another computer running 9.01 on the same network, connected in the exact same fashion, and it is perfectly "snappy".  I'm keeping the older one (same manufacturer) on Karmic and patiently installing every available update until this problem is finally squashed.  The bug(s) result in incredibly slow DNS Lookups and will eventually be taken care of - but as of the latest update, (which moved me to Firefox 3.5.5 about an hour ago), the slow DNS lookups continue.

Funny, if you do a forums search for "slow dns lookups" you can see similar complaints in the early days of Jaunty and beyond. :)

---

### Post by zachHH on 2009-11-12
> I seem to have the same problem: in XP I get 5 Mbs, and in Ubuntu it ranges from 1 to 4 Mbs.

I have found many people suggesting that if Internet goes slow (terribly slow) you should disable IPv6. I don't think this will solve your problem, since you say you still have a fraction of the speed you had.

However, I think the following helped in my case (previously I had only 1 Mbs):
- Right click on the Wireless Network Connection icon => Edit connections => Wireless
- Select your network and click on edit.
- Ipv4 tab => Method: Automatic (DHCP) adresses only.
- In the DNS servers field, introduce your ISP DNSs. Look for them on Google or, if necessary, call your ISP and ask.


I do not know if this will really improve your situation. If somebody else knows about this problem, please contribute. Everything I've found until now just recommends to disable IPv6. 

As you stated, I tried this, but with no improvement.:D darn.

> Just jumping in here to say this complaint seems to be common with Karmic Koala at this point. I have another computer running 9.01 on the same network, connected in the exact same fashion, and it is perfectly "snappy". I'm keeping the older one (same manufacturer) on Karmic and patiently installing every available update until this problem is finally squashed. The bug(s) result in incredibly slow DNS Lookups and will eventually be taken care of - but as of the latest update, (which moved me to Firefox 3.5.5 about an hour ago), the slow DNS lookups continue.

Funny, if you do a forums search for "slow dns lookups" you can see similar complaints in the early days of Jaunty and beyond. :smile:

Thank for the replies, i guess ill just have to tough it out and wait until a fix (hopefully), because many are suffering from this problem, its not only me ;).

---

### Post by jcgs on 2010-03-31
Has anyone got around to having a look at this problem? I seem to be having similar symptoms, slow download speeds, but nothing to do with DNS lookups, as far as I can tell.

Would be good to get it fixed, updates seem to be taking ages atm.

---

### Post by beekr on 2010-03-31
What happens when you type in the following ? :

```


sudo iwconfig wlan0 rate 54M


```

---

### Post by misiu369 on 2011-03-06
I'd like to kidnap this thread. ;)

I'm trying to connect to an AP that has weak signal and, as far as I understand, lowering the bitrate should increase sensitivity. However, it seems "rate" setting doesn't work.

All other settings seem to work. Iwlist doesn't list possible txpower settings, but both iwlist and iwconfig show current txpower properly. However, even iwconfig doesn't show any info on bitrate.

```

# iwlist wlan0 rate 
wlan0     unknown bit-rate information.

# iwlist wlan0 txpower 
wlan0     unknown transmit-power information.

          Current Tx-Power=20 dBm  	(100 mW)

# iwconfig wlan0 rate 1M

# iwconfig wlan0 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

This is a USB wifi card. The driver is rtl8187, kernel 2.6.35-25-generic, ubuntu x64.

**Is there any way to get the bitrate control working?**
Any help would be greatly appreciated. ;)

---

