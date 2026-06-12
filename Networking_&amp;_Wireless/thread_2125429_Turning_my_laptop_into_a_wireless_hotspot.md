---
title: "Turning my laptop into a wireless hotspot"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-03-14
I bought a Hawking USB adaptor so I could connect my Nintendo DS to my computer, by turning my computer into a router.  I need to do this because my router is using WPA2, but my DS only supports WEP (and I'm unwilling to downgrade because WEP is far too insecure).

Basically, I'm looking for a way to accomplish this but on Linux (the page says it works with non-Windows OSes, but doesn't explain how to set it up):
[http://wiki.answers.com/Q/Can_you_turn_your_computer_into_a_wireless_access_point_without_a_wireless_router_for_your_Nintendo_ds](http://wiki.answers.com/Q/Can_you_turn_your_computer_into_a_wireless_access_point_without_a_wireless_router_for_your_Nintendo_ds)

Can anyone help me with this?  Thanks!

---

### Post by annevleeshouwers on 2013-07-30
I know it has been a while since you posted but I have also kind of been looking for this. I figured it out this afternoon and I hope it can be of some use to you. 
Though I work on a laptop with a built in wifi/network card I assume it works kind of the same. 

I used the program ap-hotspot with the basic configuration.
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install ap-hotspot
After that I removed the last 5 lines from /etc/hostapd-hotspot.conf
If you need a more detailed guide you can check [http://littleprogrammingadventures.blogspot.nl/2013/07/set-up-wireless-hotspot-for-ds-in.html#more](http://littleprogrammingadventures.blogspot.nl/2013/07/set-up-wireless-hotspot-for-ds-in.html#more)
Like I said it is with a buit in network card and ubuntu but I suspect it is pretty much the same. 
Let me know if it works :)

---

