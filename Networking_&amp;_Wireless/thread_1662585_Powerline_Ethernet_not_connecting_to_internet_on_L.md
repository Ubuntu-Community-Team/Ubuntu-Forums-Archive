---
title: "Powerline Ethernet not connecting to internet on Linux"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by chridgely on 2011-01-08
Hello, I have just installed Ubuntu two days ago to see that I cant connect to the internet with my powerline av ethernet adapters. I do not understand why though because it is plug and play with everything else I have. When I plug in the ethernet cable the connection panel does not list any connections. It just says, "Disconnected". In the edit connections it says, "Auto Eth0" which i think means that ubuntu is recognizing that I have an onboard ethernet port. 

I really have no idea what to do because on my linux machine, I am unable to download any drivers due to lack of internet. Any help is appreciated. I hope we can resolve this quickly.

Motherboard:

[B]GIGABYTE GA-MA770T-UD3 AM3 AMD 770 ATX AMD Motherboard 
[/B]*[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451)*

Processor:

[B]AMD Athlon II X4 635
[/B]*[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103702](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103702)*

---

### Post by PatchesTheCaveman on 2011-01-08
Go to Applications > Accessories > Terminal, then type the following and press Enter:
```
ifconfig -a
```

Copy/paste what appears into a reply to this thread.

---

### Post by kerry_s on 2011-01-08
> **chridgely said:**
> Hello, I have just installed Ubuntu two days ago to see that I cant connect to the internet with my powerline av ethernet adapters. I do not understand why though because it is plug and play with everything else I have. When I plug in the ethernet cable the connection panel does not list any connections. It just says, "Disconnected". In the edit connections it says, "Auto Eth0" which i think means that ubuntu is recognizing that I have an onboard ethernet port. 

I really have no idea what to do because on my linux machine, I am unable to download any drivers due to lack of internet. Any help is appreciated. I hope we can resolve this quickly.

Motherboard:

[B]GIGABYTE GA-MA770T-UD3 AM3 AMD 770 ATX AMD Motherboard 
[/B]*[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451)*

Processor:

[B]AMD Athlon II X4 635
[/B]*[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103702](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103702)*


you need to make sure the plugs are on the same circuit.
1 plugs into your router/modem the other to your internet device/computer, make sure the lights light up(if yours has lights, mine do) the units should be plugged straight into the wall if possible, but i've used mine through extension cords with out problems. try replugging the 1 at the router then the 1 at your computer, some times they lose each other.

i have these, there old, but have been working perfect for years.
[http://www.amazon.com/NETGEAR-XE102-Wall-Plugged-Ethernet-Bridge/dp/B0002IHP58/ref=pd_sim_e_5](http://www.amazon.com/NETGEAR-XE102-Wall-Plugged-Ethernet-Bridge/dp/B0002IHP58/ref=pd_sim_e_5)

---

