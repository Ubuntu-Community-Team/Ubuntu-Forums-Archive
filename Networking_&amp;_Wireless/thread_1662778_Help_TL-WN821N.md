---
title: "Help: TL-WN821N"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2011-01-08
I have a TL-WN821N which I'd like to put to use. There is no question about the wireless router, which is a Linksys WRT610N dual band. Other devices (Windows and Mac based) have no difficulties connecting and sustaining wireless "N" speeds.

My understanding is that the kernel I'm running (2.6.35-24) should support wireless "N" out of the box on the WN821N. Is that correct?

If so, it seems that it only wants to work at "G" speed, 1Mbps:

> iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"cisco_wrt610n"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:5C:58:42   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My question is, is there a way to utilize at least some of the potential of the TL-WN821N or perhaps can someone recommend a Wireless USB interface that will work under linux with a minimum of fuss?

TIA

---

### Post by PatchesTheCaveman on 2011-01-08
Have you tested your actual speed by copying a file or something?  As you can see, it's reporting 802.11bgn connectivity.  Sometimes that bit rate setting has absolutely no effect on your actual speed.

But, you can still change it to your maximum setting.  To that, first run this command:
```
sudo iwlist wlan0 rate
```

That will report all the possible rate modes on your wireless adapter.  Look for the highest one.  Since my adapter only supports 802.11g, my top speed is 54 Mb/s.  So, to set my card to run at that speed, I'd run:
```
sudo iwconfig wlan0 rate 54M
```

Do the same thing but set it to your top speed.

---

### Post by GuiGuy on 2011-01-09
> **PatchesTheCaveman said:**
>   So, to set my card to run at that speed, I'd run:
```
sudo iwconfig wlan0 rate 54M
```

Do the same thing but set it to your top speed.

That setting is an indicator only, it seems to me. I can set it rate=anything  but the transfer speeds stay ~1Mbps.

Incidentally, I got hold of a D-Link USB DW140 and DW150. The former is supposed to work out of the box as well, according to what I read. Anyway, same thing, both devices come up as being recognised "N" compliant, both report 1Mbps. Setting the rate to something higher has no effect on real transfer speeds, again suggesting "rate" is only an indicator, not a gauge. 

I checked to make sure that the USB ports are performing at USB2 speeds. They are.

Anyway, don't worry as I have given up now. 

Cheers

---

