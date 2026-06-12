---
title: "Wireshark wireless capture problem..."
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by Eremis on 2010-12-13
Hi guys,

I am trying to monitor connections on my wireless router... So I got wireshark running with:
```

kdesudo wireshark

```

I use kdesudo because I have KDE...

Then After going to the first button on the left (where you choose interface) I choose wlan0, when I click capture I can capture everything that comes and goes though my capturing laptop, but if I use something like my kindle with wireless and browse the Internet I can never see it's packets... Same thing goes with browsing the Internet with a different laptop...

Do you know what might be the issue?
Do I have to start my wireless card in "listen mode"?
If so do you know how this is done? 

Any help would be appreciated,

Thanks

---

### Post by Eremis on 2010-12-13
`

---

### Post by Eremis on 2010-12-13
I think I figured it out,

fist I have to put put wireless card into "listen" mode with:

```
airmon-ng start <interface> <channel> 
ex. airmon-ng start wlan0 6 

```



then do:
```

ifconfig

```


In this case now I can see "mon0" which is my listening interface,

Now I listen with wireshark on mon0, insted of wlan0...
Got this from this tutorial:
[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

---

