---
title: "Need some help with BSNL - net gear - internet"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by cannon_dt on 2009-01-28
Hi experts,
I need you to ratify/certify my internet set up, let me know if I am
doing the right thing.
1. I have a bsnl UT300R2U modem
2. I got a net gear WGR614 wireless g router.
The only reason I have the router is to stream music/videos to my PS3.
Other than that it is nothing much. 

So here is my set up
My modem --> Router
My laptop --> Ethernet port of the router.

Now on my Ubuntu settings, I have set to automatic (ie) DHCP, no
static IP. (using edit connections --> Wired --> Auto et0 --> ipv4
setting set to DHCP (Automatic).
On my router, after having a conversation with BSNL (who told me that
their IP and DNS have changed to 192.168.1.10 and DNS is now set as
Pref DNS 218.248.240.24 and Alt DNS 218.248.255.145), I updated my net
gear router with all these settings (I did not go the "get
automatically from ISP" route which is what I had initially).

Now with all this in place I think
1. My internet connection sucks, I dont think I am getting good speeds
even though I am having a 512 line (supposedly fast!)
2. Connection with sites keep breaking up ever so often.

Can you please review my settings and help me here? I am tired of going
to BSNL and Net Gear both of whom shrug me off saying they dont
support linux. That is nonsensical as far as I can see, can you please
help me here.

After a lot of "googl"ing and "forum"ing, I also realized that there could be some tweaks in the interfaces file. Currently it reads as

auto lo
iface lo inet loopback

Should this be changed? My n/w config says Auto eth0 is what is being used, should that figure here?

Can someone please help me here, this is really frustrating and what I really need to know if some setting are being done wrongly by me?

Thanks,
Ananth

---

