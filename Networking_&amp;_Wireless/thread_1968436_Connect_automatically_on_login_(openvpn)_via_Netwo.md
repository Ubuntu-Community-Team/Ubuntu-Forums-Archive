---
title: "Connect automatically on login (openvpn) via Network Manager"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by karypid on 2012-04-29
I am using Ubuntu 12.04 LTS (64bit). I've added an OpenVPN connection via NetworkManager, which I'd like to start automatically after my Wireless connection is established. I therefore checked the "Connect automatically" checkbox in the Network Manager configuration. You can see it in the attached image.

Problem is that when I login, the wireless connection is established but the VPN connection does not start. I have to manually choose it from the network applet in order to activate it.

There is nothing wrong with my networking otherwise (meaning the wireless works with no intervention, as well as the VPN if I manually start it).

Any help will be appreciated.

---

### Post by imac_89 on 2012-04-29
I am not sure if you have come across this post yet: [http://ubuntuforums.org/showthread.php?t=1575158]("http://ubuntuforums.org/showthread.php?t=1575158")

Seems to be a round-about way of doing it and involves removing keychain passwords. I will keep looking around though.

---

### Post by karypid on 2012-04-30
Hello,

Thanks for pointing this out. It did work for me, though I did not have to do anything with my keychaing passwords. I simply added the following command to my Startup Applications:

```
nmcli con up uuid 7d5fc95e-ab22-432f-aef6-55270fe9e5e1
```

To find out the UUID I ran:

```
nmcli con list
```

Having said that, obviously this is a bug in NetworkManager...

> **imac_89 said:**
> I am not sure if you have come across this post yet: [http://ubuntuforums.org/showthread.php?t=1575158](http://ubuntuforums.org/showthread.php?t=1575158)

Seems to be a round-about way of doing it and involves removing keychain passwords. I will keep looking around though.

---

