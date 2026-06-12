---
title: "madwifi &quot;ioctl: No such device&quot;"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2009-03-30
Hi all.
I'm trying to get the madwifi drivers to with my atheros controlled builtin wifi card on my laptop. My laptop is an Acer extensa 5220.

I am currently using Ibis. (But will be updating to Jaunty soon).


Following the installation docs for madwifi was simple enough.
I ran 'make' and 'make install', and the drivers installed without error.

I then installed the ath_pci module with modprobe.

However, I don't seem to have a wireless interface.

I tried 'ifconfig up ath0' and 'wifi0', and I got back:

```

ath0: ERROR while getting interface flags: No such device

```

I tried 'wlanconfig ath0 create wlandev wifi0 wlanmode sta', and I get back
```
wlanconfig: ioctl: No such device
```

iwconfig returns:

```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

pan0      no wireless extensions.

```

How do I create the device and get wifi working?

Thanks

---

### Post by mondeoscotch on 2009-05-27
I'm stocked in the same place.
Exactly the same driver. I've got it installed without errors but now can't bring that interface up. 
It's been 2 months since you post it. Please write if you made any progress.

---

### Post by romant on 2009-08-12
Hej,

I had the same problem, but the solution is that u should check your /etc/modprobe.d/madwifi.conf or any other blacklist file (they usually start with blacklist). Then unblacklist the module u wanna use. For me it was ath5k. It was blacklisted.

---

