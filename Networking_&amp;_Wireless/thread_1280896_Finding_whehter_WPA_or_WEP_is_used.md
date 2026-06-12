---
title: "Finding whehter WPA or WEP is used"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by shreyas_pathak on 2009-10-02
Hello folks, 

It's been 2 months since i shifted to Ubuntu and they have been both frustrating and happy times (animation n stuff)

I was playing around with the iwconfig and iwlist tools....and was curios to know....how does one find out what security is used by the access point we are connnected to...

I ran the ```
iwlist wlan0 auth
``` command and got this

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Authentication algorithm :
        open

Also, i ran the ```
sudo iwlist wlan0 encryption
``` and got the following:

wlan0     2 key sizes : 40, 104bits
          4 keys available :
        [1]: ####-####-## (40 bits)
        [2]: off
        [3]: off
        [4]: off
          Current Transmit Key: [1]
          Security mode:open

How does one decide which encryption is being used by the access point?

Also, what is the security mode: open thing

Thanks guys for helping me out ....

---

### Post by Brandon Williams on 2009-10-03
The output from 'iwlist wlan0 auth' is showing you the authentication capabilities of the interface. Similarly, 'iwlist wlan0 scan' will list the access points that are broadcasting and show you their security setting.

Alternatively, if you use network manager (by default, you do), then you can run 'nm-tool' and it will list a summary of all this information, including the security mode for each AP and the security modes supported by your interface (among other things).

---

