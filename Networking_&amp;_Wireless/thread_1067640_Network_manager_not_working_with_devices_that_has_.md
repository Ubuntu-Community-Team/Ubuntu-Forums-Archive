---
title: "Network manager not working with devices that has own driver"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by maddis on 2009-02-12
I tried to keep the title as informative yet short as possible.

What I ment is that I have couple network devices that Linux does not support directly (there are no drivers in the kernel for them). I have drivers for them and I'm able to get the network working manually. I'm also able to change the configuration with the network manager although I have to use dhcp since the roaming - mode won't do anything.

The problem now is that if I start the system without network cables connected and then reconnect the cables, the system won't get new IP in a long time. I havent' waited how long it takes, but it takes way longer than when the network manager is working correctly. In that cased the network manager starts looking new address as soon as I connect the network cable.

Now the network manager complains 'No networking connection' although it can show both interfaces in 'manual configuration' - mode. Also, if I manually say ifup/down for the interface it get's new IP right away.

I also added both interfaces to udev just in case that's the problem, but it didn't do any difference. 

Driver module is listed in /etc/modules - file.

Any idea how do I get the network manager to work with those interfaces or at least request IP from dhcp lot faster than what it currently does?

When starting with network cables connected there are no problems. Both interfaces work right away.

Edit: 
I also noticed that startup takes lot longer when network cable is not connected. I started without splash and saw that Configuring network... takes quite long and also the NTP stop/start after it. I've configured that dhcp-server provides NTP information too. I haven't noticed similar slowing down with another unit that has network device that Ubuntu/Linux supports directly.

Some measurements. In unit that has ubuntu supported network, when connecting the network cable unit gets new ip in 10 seconds (this one also doesn't slow down in bootup if the network cable is not connected). In the unit mentioned earlier it takes from two up to near four minutes to get ip once the cable is connected.

---

