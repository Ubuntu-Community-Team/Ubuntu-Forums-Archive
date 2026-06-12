---
title: "Wireless in 9.04"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by aakar on 2009-06-12
last night  i upgraded to ubuntu 9.04 since then i m facing a problem of being getting disconected from wifi
.......i m tired of by clicking again and again ...........can nybody plz tell me a possible solution ...
such problem was not there on the previous version of ubuntu i was using...

thnx in advance

---

### Post by PreviousN on 2009-06-12
Hi. Which version *are* you using? And, can you please post the output of dmesg (from a terminal?). Err. Apparently I missed out which version you were using. Anyways, what version did you upgrade from? 

Open Applications --> Accessories --> Terminal. Then type:
```
 dmesg 
```

Also, any information about your wireless card will be helpful. Are you using a dongle or an internal one? If internal, please post the output of "lspci", if a dongle, please post the output of lsusb. 

Finally, you may want to check out this guide: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Thanks.

---

