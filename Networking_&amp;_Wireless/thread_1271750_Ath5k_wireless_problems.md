---
title: "Ath5k wireless problems"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by Trudiewudy on 2009-09-21
Hello,

After I installed the last updates yesterday, I (again) had the problem that my wireless didn't work. I always had to use madwifi to get it working, and still hadn't gotten the grasp of how exactly I got things to work. After doing some research on the internet, I read somewhere that a newer kernel version did support my wifi-card. So I updated to a newer kernel version. 
After the kernel update, I can scan for wireless networks, and it says I'm connected to my network.
But... When I try to go on the internet it keeps saying I'm not connected. I can't ping websites either. What I can do is connect to my router and ping my router. With other devices I can go online wireless, so I think the problem is in my configuration in ubuntu.

I'm not at home right now, so I can't give you the output of iwconfig, ifconfig etc. But if you tell me which commands would be of help to you, I'll put them online in a couple of hours.

I really hope someone can help me with my wireless problem!

Kind regards,

Trudiewudy

---

### Post by MaindotC on 2009-09-21
Try following the directions in the [Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).

---

### Post by Trudiewudy on 2009-09-21
I tried to follow the Wireless Troubleshooting, but nothing I learned from that helped me any further. My card is being recognized and it is associated with ath_pci drivers.

I noticed that when I use iwconfig it says that the logical name of my device is ath0, but when I use lshw it says 'logical name: wifi0'. I am associated with my router and can ping locally as well as my router, but when I try to ping an external ip-adres it doesn't return.

---

### Post by MaindotC on 2009-09-21
Post output of:
```

ifconfig
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf

```

---

