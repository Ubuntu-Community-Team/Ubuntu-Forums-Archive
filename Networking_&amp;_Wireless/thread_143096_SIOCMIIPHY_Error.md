---
title: "SIOCMIIPHY Error"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by spidoman on 2006-03-11
I followed the Wired Troubleshooting guide, and I hit an error on the first step

after inputting "sudo mii-tool eth0"
I get the error SIOCGMIIPHY on eth0 failed: Operation not supported.

Other steps seem to go well, I get no errors in ifconfig, and I am able to ping the router, even able to go into Firefox, and access the router. but I am unable to ping internet addresses by both number and word.  I have compared network settings to another computer running the same version of Ubuntu, and the network settings are identical.

---

### Post by ranf on 2006-03-13
The mii-tool man page has a short explanation of the error messages.
```
man mii-tool
```
then type:
```
/SIOCGMIIPHY
```

The slash `/' is the search command in man and less.

You can't even ping by IP? That's bad. Post the output of `ifconfig' and `route'.

---

