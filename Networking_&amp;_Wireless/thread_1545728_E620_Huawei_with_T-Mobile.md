---
title: "E620 Huawei with T-Mobile"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by afhx on 2010-08-04
I have a E1750 Huawei dongle from T-mobile. I can get "connected" but I am unable to shift the following from the Address Bar:
www/t-zones-co-uk/apps/abcd/justest.jsp
(any entry is instantly replaced)
I have version 10.4 and have both the usb-modeswitch packages installed.I have tried to follow the suggestions in the forum, and in particular Alex French(very informative),but to no avail. However, I don't know the syntax to enter the Product/Vendor Ids into /etc/usb-modeswitch. Also, when I try to use usb_modeswitch from the command line,although I am giving Product/Vendor Ids I am getting abort messages no default product/vendor ids supplied. I can't get onto the Draisbergh site because the local library won't allow access(drug abuse!). Product code is Ox1001 and vendor id is Ox12d1. A file appears in /etc/usb_modeswitch.d.I used the E160 without problems but I has lost it. Any suggestions would be gratefully received.

---

### Post by afhx on 2010-08-18
I don't know how to reference a previous thread but the method suggested by Sola on Dec 12th 2009 [Solved Huawei 1750 3G ]works with obvious modifications for the rules directory works . Needed to do the sudo. Please ignore what I said about modications to the directory. Just follow Sola method to the letter. That way you avoid the sudo

---

