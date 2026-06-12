---
title: "Network Proxy working in Backtrack 5, not in Ubuntu 10.4"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by hydrox24 on 2011-06-02
I have two USBs running live linux distros.
The first USB runs ubuntu 10.4 (as you can probably tell from the title)
The second USB runs backtrack linux 5 on gnome.

Now I can easily boot from either of these USBs at school, but the difficulty comes when I try to connect to our schools proxy server that we get Internet through.
I use the "network proxy" settings GUI to configure both (they are essentially identical) and set it up to look something like the following:
[ATTACH]193943[/ATTACH]
The only blurred thing is part of the name of the proxy server (the blurred part is the name of my school)
Now under backtrack, this setup works perfectly and I am fully able to access the Internet, however under ubuntu, Firefox complains of not being able to connect to the proxy server and chrome says similar.
I really don't know where to start in terms of debugging or solving this so any differences between BT5 and ubuntu 10.4 you think might be the cause, please just say.

Keep in mind that it is possible that there are security restrictions on MAC addresses and other things that BT might be spoofing or hiding or something.

Thanks, I really enjoy linux and its community :D

---

### Post by giodamelio on 2011-06-12
You could try looking in the firefox settings and setting a manual proxy setting. Goto Edit --> Preferences --> Advanced --> Network --> Settings and set the proxy settings manually.
    If there is some type of mac filtering, you could try to find the windows(I assume) machine's mac then spoof it on your ubuntu system. To spoof your mac, simply use ifconfig to find the name of your network interface then subsitute your interface name in the following commands. 
```

ifconfig <network interface> down
ifconfig <network interface> hw ether 00:11:22:33:44:55
ifconfig <network interface> up

```

Hope that helps, giodamelio

---

