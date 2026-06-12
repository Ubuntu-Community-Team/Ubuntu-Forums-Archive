---
title: "Ubuntu wifi not working on a old laptop"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by unitedanarchy on 2012-06-04
I don't have the laptop with me at the moment but a while ago I got my friend Ubuntu on an old laptop, And he didn't have wifi. He had a bad connection as it was so basically we tried getting the updates through his phone connected via a usb to his laptop and his phone connected to the wifi router, ALthough it was battery powered and very slow. So basically he never finished the updates because it took so long and he kept having to recharge the router giving him a bad impression of Ubuntu. Number one I want to understand and fix the problem, And number two I want to repair his image of Ubuntu. He doesn't exactly have the best history of being logical.

---

### Post by wilee-nilee on 2012-06-04
> **unitedanarchy said:**
> I don't have the laptop with me at the moment but a while ago I got my friend Ubuntu on an old laptop, And he didn't have wifi. He had a bad connection as it was so basically we tried getting the updates through his phone connected via a usb to his laptop and his phone connected to the wifi router, ALthough it was battery powered and very slow. So basically he never finished the updates because it took so long and he kept having to recharge the router giving him a bad impression of Ubuntu. Number one I want to understand and fix the problem, And number two I want to repair his image of Ubuntu. He doesn't exactly have the best history of being logical.

The wifi card needs to be identified.

```
lspci
```Will name hardware in general specific commands can isolate single hardware.

   	 	 	 	```
lspci | grep -i wireless 
```  ```
lspci | grep Broadcom
```

---

