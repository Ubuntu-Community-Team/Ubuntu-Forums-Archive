---
title: "Wifi connection drops randomly, keeps asking for my password"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2011-08-23
I installed Ubuntu PPC 10.04 on my eMac. It works great, but the wifi is a bit spotty.

I'll post the details of the wifi card if they are needed, but since I can't get internet on it I'll need to copy over the outputs with a flash drive. I would imagine I need to post the output of lspci and dmesg, but what other files or outputs of commands do I need to post? Erring on the side of more info of course. 

My home access point shows two bars. It takes about one minute to connect, and it will keep a connection for about 30 seconds but then the connection will drop randomly (shows the trying to connect animation on the applet) 

When it tries to reconnect, it asks for the password for some reason, sometimes multiple times. Why does it do this?

Not sure if the signal strength meter is accurate. How can I get an output of the raw signal strength numbers? Updating at maybe five times a second?

After I installed OpenWRT on my linksys router (which I have since given away) I have found that there are a lot of hardware variables I can tweak to tune performance. Transmit power, etc. Is there a way to tweak hardware variables for various wireless cards in Ubuntu in order to tune performance?

Thanks!!

---

### Post by praseodym on 2011-08-23
Hello,

can you post the following outputs:

```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan #which network is yours
lsmod
route -n
cat /etc/resolv.conf
```

---

