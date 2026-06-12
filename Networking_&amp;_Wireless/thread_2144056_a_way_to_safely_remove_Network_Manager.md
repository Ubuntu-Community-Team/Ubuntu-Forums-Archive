---
title: "a way to safely remove Network Manager"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by clearski on 2013-05-10
Hello, everyone.

I'm looking for a way to safely remove Network Manager. I've already* disabled* it and the network is running fine.

I am not sure if 

```
sudo apt-get remove network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome
```

is safe for the system and won't cause any problems.

Thank you.

---

### Post by chili555 on 2013-05-11
> **clearski said:**
> Hello, everyone.

I'm looking for a way to safely remove Network Manager. I've already* disabled* it and the network is running fine.

I am not sure if 

```
sudo apt-get remove network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome
```

is safe for the system and won't cause any problems.

Thank you.Looks good to me. You might also remove all the configurations files with:```
sudo apt-get remove [COLOR="#FF0000"]--purge[/COLOR] network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome
```How are you connecting without NM? Are you sure it's not running?```
ps aux | grep etwork
```

---

### Post by clearski on 2013-05-11
> **chili555 said:**
> Looks good to me. You might also remove all the configurations files with:```
sudo apt-get remove [COLOR=#FF0000]--purge[/COLOR] network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome
```

That did it really well. I had to manually delete the directory /etc/NetworkManager, but that was all.

> **chili555 said:**
>  How are you connecting without NM? Are you sure it's not running?

```
ps aux | grep etwork
```

I had /etc/network/interfaces configured, including a DHCP server and DNS resolver. I also made a backup and some tests before.

It was nice to use Network Manager, it worked very well since I installed Ubuntu, but there's more fun without it. :)

```

ps aux |grep etwork
username     3084  0.0  0.0   4428   828 pts/1    S+   18:02   0:00 grep --color=auto etwork
```

Thank you!

---

### Post by chili555 on 2013-05-11
Awesome. It looks like you are all set!

---

