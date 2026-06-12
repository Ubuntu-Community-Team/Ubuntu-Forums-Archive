---
title: "Internet connection not working"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by 2bob on 2009-03-19
Hello everybody!
Is there anybody else who had the same problem? I can’t go on Internet under my Ubuntu 8.10. I am connected to LAN, I can see my computer into the router’s config utility from another pc on the LAN like everything is fine but Firefox and Thunderbird can’t connect to the Internet nor Synaptic. It went off suddenly – last night everything was OK and today... just nothing. Now, with Mint 6 live cd I can write to you here. Thank you!

---

### Post by ac7ss on 2009-03-19
What kind of connection are you using? (Wifi or cat5)

What is the result of a
```
$ sudo ifconfig
```
If using WiFi, what do you get from
```
$ sudo iwconfig
```

Compare these between the live disk results and the installed results.

---

### Post by 2bob on 2009-03-22
Sorry, ac7ss, I've done reinstall and everything is OK for now. Thank you very much for your time.

---

### Post by mikios on 2009-03-23
> **2bob said:**
> Hello everybody!
Is there anybody else who had the same problem? I can’t go on Internet under my Ubuntu 8.10. I am connected to LAN, I can see my computer into the router’s config utility from another pc on the LAN like everything is fine but Firefox and Thunderbird can’t connect to the Internet nor Synaptic. It went off suddenly – last night everything was OK and today... just nothing. Now, with Mint 6 live cd I can write to you here. Thank you!

Did you solve the problem yet?

I had the same 5 days ago and after a lot of search in this forum and with a lot of help of couple of guys it seems that using open dns was the best way. Go to the link below and i hope you find your way out, (if you havent found it yet).


[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by 2bob on 2009-03-26
Thanks, mikios!
I solved the problem, like I said, brute-reinstall. Impossible for me to explain is the fact that from 3 computers on the LAN only this one was without internet connection. I could use the Internet with the other two. I am testing now open dns. Once again, thank you very much!

---

