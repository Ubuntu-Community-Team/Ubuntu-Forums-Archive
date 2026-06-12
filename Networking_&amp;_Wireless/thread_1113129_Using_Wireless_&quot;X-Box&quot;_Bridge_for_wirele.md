---
title: "Using Wireless &quot;X-Box&quot; Bridge for wireless ethernet?"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by wkulecz on 2009-04-01
Given all the hassles of getting wireless ethernet to work, has anyone tried one of those ethernet to wireless bridge boxes, typically sold to add wireless network connection to an X-box or Playstation?

Presumably once you set the WiFi password using a web browser the normal ethernet driver should be able to do DHCP as if it was wired to your wireless router.

--wally.

Edit:  What with the ugly pink and yellow colors?  For April fools its not funny, just hard to read!

---

### Post by wkulecz on 2009-04-01
I was thinking of products like these as the support for 802.11n WiFi adapters seems problematic at best at present, and since my wireless router appears to have died last night, I'm looking to upgrade from G to N with gigabit on the wired side.

[http://www.linksysbycisco.com/US/en/products/WGA600N](http://www.linksysbycisco.com/US/en/products/WGA600N)

[http://www.linksysbycisco.com/US/en/products/WET610N](http://www.linksysbycisco.com/US/en/products/WET610N)

[http://www.dlink.com/products/?pid=663](http://www.dlink.com/products/?pid=663)

These run about $100 at Fry's (expect you could do better on-line) which is a price premium over the PCI, PCI-E, USB, or Cardbus adaptors that I could live with to avoid the hassles of driver compiling and recompiling after kernel updates.

In theory you'd also get full WPA2 support without ndiswrapper hassles or downgrades in security due to driver non-implimenteds.

--wally.

---

### Post by wkulecz on 2009-04-02
This could be the pain free wireless solution for Linux!

Got a Linksys WGA600N "gaming adaptor" ([http://www.linksysbycisco.com/US/en/products/WGA600N](http://www.linksysbycisco.com/US/en/products/WGA600N)) and a pair of replacement routers -- Linksys WRT610N and Airlink101 AR430W (it was only $10 on sale! and I've some WEP only devices I'd like to be able to use since draft-N doesn't support WEP so I figured I use it as a legacy access point).

After setting up the router I programmed my security settings into the game adapter using windows, set it to DHCP and rebooted it.  Unplugged it and moved the ethernet cable from it into the wired port on my Ubuntu 8.04 box and presto, Wireless secure connection.  Ubuntu thinks its doing DHCP on a wired connection, while the game adaptor does the wireless stuff!

I'm not home free as the WRT610N I got seems dead on the Internet side but Samba and all LAN/WLAN worked, just no Internet :(  

I set up the AR430W and the gaming adaptor had no issues connecting to it and now everything works although only at my old 11g speeds.  Connection seems stronger than what I was getting with my Airlink USB AWLL3055 adapter which curiously connected fine to the WRT610N but could only connect to the AR430W if I used open system.  The "joys" of wireless and Linux :(

Depending on your frustration factor vs. your cash flow, this could be the way to go.  The draft-N dual band adapter was about $100, they make one that is 802.11g that runs about $70 which is not such a great price premium over a USB or PCI adapter and downright cheap if you value your time and your chosen adapter doesn't work out of the box on Linux.

It appears that once the gaming adapter is programmed (using Windows with full manufacturer support!) for your router/access point, its just a wireless dongle that plugs into your ethernet port making device think its a wired connection.

--wally.

---

### Post by Epson_Stylus on 2009-06-29
I, after purchasing a 50 dollar incompatible (due to a new "update") Linksys adapter (WUSB54GC v3), tried out my old 802.11b WGA11B Linksys gaming adapter (I assume it has long since been set up on a windows machine) and finally got it to work.
 
I jiggled around with the channels while hoping the set up would run and it detected a wired network.  I have never set up any wireless network on this comp so assuming the adapter is set up properly, it shoud connect after plugging in the ethernet jack.  Worked reliably and at decent speeds.  
 
Makes me wonder why they just don't use gaming adapters for wireless connections in ALL computers.  
 
Ubuntu 9.04 (Jaunty) 64 bit
WGA11B Lynksys Gaming Adapter (v1.05 setup disk)
WEP connection (I believe) on Buffalo WHR-G125 Wireless Router

---

