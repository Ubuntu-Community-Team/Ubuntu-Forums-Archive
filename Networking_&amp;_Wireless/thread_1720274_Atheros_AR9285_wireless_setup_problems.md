---
title: "Atheros AR9285 wireless setup problems"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by 8ER on 2011-04-03
hi all, i am new to Linux
sorry for any bad english

I'm running Ubuntu Studio 10.10 on a HP presario cq71 with Atheros AR9285

ethernet connection works fine but i have some issues with wireless connection. 

I have tried to setup wireless via ***system -->administration --> network***. In the *configuration* button under *connection settings* i chose DHCP. It seems that wireless has been enabled but once i unplug Ethernet i can't connect. (wlan button on router is on)

1.the command ***iwlist*** scan gives me:
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
2.the command ***iwconfig*** gives me:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

does "ESSID:off" means that wireless is disabled? if so how can i enable it? 

I've read something about "*linux-bacports-modules*" do i need to install them? Do i have to install Atheros Drivers?

please help
thanks

---

### Post by I'mGeorge on 2011-04-03
do the following 
```

sudo ifconfig wlan0 up
iwlist wlan0
sudo iwconfig wlan0 essid "routers_essid" (if you wanna connect to the wireless route)
sudo dhcpcd wlan0

```

or you could just install wicd and wicd-gtk for a more easier graphical way to connect to wireless networks
```
sudo apt-get install wicd wicd-gtk
```

---

### Post by 8ER on 2011-04-03
it worked, thanks alot! :P[COLOR=#000000]
[/COLOR]

---

