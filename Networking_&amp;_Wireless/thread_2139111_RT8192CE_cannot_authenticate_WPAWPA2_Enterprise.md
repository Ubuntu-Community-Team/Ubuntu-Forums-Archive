---
title: "RT8192CE cannot authenticate WPA/WPA2 Enterprise"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by pskeshu on 2013-04-26
Ubuntu 13.04

I'm not able to connect to my campus internet which uses WPA/WPA2 Enterprise security with PEAP and MSCHAPv2. I'm able to connect with the same user ID and password in Windows, so incorrect ID/pass is not an issue. 

When I try to connect, network manager log shows that authentication times-out after 3 tries. I was able to connect to the same network previously using Linux Mint and KaliOS without an issue.

Any help is greatly appreciated.

---

### Post by varunendra on 2013-04-26
Please follow the "Wireless Script" link in my signature, follow the instructions there and post back the diagnostics report here. Of course run the script when you are in campus and trying to connect.

---

### Post by pskeshu on 2013-04-26
> **varunendra said:**
> Please follow the "Wireless Script" link in my signature, follow the instructions there and post back the diagnostics report here. Of course run the script when you are in campus and trying to connect.

I've run the script. Here is the the output - [http://paste.ubuntu.com/5605319/](http://paste.ubuntu.com/5605319/)

---

### Post by varunendra on 2013-04-26
Please try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y
```

This will be a temporary change and will be lost on reboot. We can make it permanent if it helps. However, if it doesn't, please try one of these :
[LIST]
[*]Using 'iwlist scan' command, identify the access point with strongest signal. Then in Network Manager, try binding its mac address with the ssid (fill the access point's mac address in the "BSSID" field > save > exit > retry to connect). Or,
[*]Try installing and using wicd instead of Network Manager.
[/LIST]


I'm suspecting an infamous bug in Network Manager which causes it to keep roaming across one access point to another where multiple ones are present with the same name (ssid). Refer to the 'dmesg' output part of your diagnostics report to understand this.

---

### Post by Mirdan on 2013-04-27
Hi guys,

According to this page [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476) (it solved the problem for me):

. Find your file     /etc/NetworkManager/system-connections/[SSID_OF_YOUR_NETWORK]
. With root permissions, open it and find the line "system-ca-certs=true". Just replace the "true" by "false".
. Save the file. Try to reconnect. And have fun :)

---

### Post by fredferrao on 2013-04-29
> **Mirdan said:**
> Hi guys,

According to this page [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476) (it solved the problem for me):

. Find your file     /etc/NetworkManager/system-connections/[SSID_OF_YOUR_NETWORK]
. With root permissions, open it and find the line "system-ca-certs=true". Just replace the "true" by "false".
. Save the file. Try to reconnect. And have fun :)


Perfect, this works for me!!

---

### Post by yeez on 2013-05-01
> **varunendra said:**
> Please try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y
```

This will be a temporary change and will be lost on reboot. We can make it permanent if it helps. However, if it doesn't, please try one of these :
[LIST]
[*]Using 'iwlist scan' command, identify the access point with strongest signal. Then in Network Manager, try binding its mac address with the ssid (fill the access point's mac address in the "BSSID" field > save > exit > retry to connect). Or,
[*]Try installing and using wicd instead of Network Manager.
[/LIST]


I'm suspecting an infamous bug in Network Manager which causes it to keep roaming across one access point to another where multiple ones are present with the same name (ssid). Refer to the 'dmesg' output part of your diagnostics report to understand this.
Thanks! That worked great! Been searching to fix this for a few days.

---

### Post by varunendra on 2013-05-01
> **yeez said:**
> Thanks! That worked great! Been searching to fix this for a few days.

Thanks for taking time to provide feedback!
It would be more useful to us if you can point out specifically which of the solutions worked for you, as the post contains three.

And if you are using 13.04 and the problem returns, you may wish to try Mirdan's solution. In any case, we very much appreciate the feedback. :)

---

### Post by Pepe Lebuntu on 2013-06-12
> **varunendra said:**
> Thanks for taking time to provide feedback!
It would be more useful to us if you can point out specifically which of the solutions worked for you, as the post contains three.

And if you are using 13.04 and the problem returns, you may wish to try Mirdan's solution. In any case, we very much appreciate the feedback. :)

Hi varunendra. I'm having the same problem on my Lenovo X121e. Is there any way you could help me?

---

### Post by varunendra on 2013-06-15
> **Pepe Lebuntu said:**
> Hi varunendra. I'm having the same problem on my Lenovo X121e. Is there any way you could help me?

Hi!
Sorry I couldn't reply soon, was stuck in some personal matters. Hope it is not too late to respond (would be super cool if you already found a fix though :P)

If still on it, please show us which card you have and if there is a driver loaded for it -
```
lspci -nnk | grep -iA2 net
```
..along with a detailed description of the exact problem you are having (wireless problems are very often subjective, although symptoms may look same, the reasons and fixes may differ).

Thank you!

---

### Post by Pepe Lebuntu on 2013-06-16
> **varunendra said:**
> Hi!
Sorry I couldn't reply soon, was stuck in some personal matters. Hope it is not too late to respond (would be super cool if you already found a fix though :P)

If still on it, please show us which card you have and if there is a driver loaded for it -
```
lspci -nnk | grep -iA2 net
```
..along with a detailed description of the exact problem you are having (wireless problems are very often subjective, although symptoms may look same, the reasons and fixes may differ).

Thank you!

Hi mate,

It SEEMS to have worked itself out. But if it comes back, I'll let you know. Sorry!

---

