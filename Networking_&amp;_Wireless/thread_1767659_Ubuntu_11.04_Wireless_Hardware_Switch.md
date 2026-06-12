---
title: "Ubuntu 11.04 Wireless Hardware Switch"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by ShadedCS on 2011-05-26
I just installed Ubuntu 11.04, from Windows XP.

Ever since I have tried it, I can only connect to the internet on a wired connection, but no wireless. 

It says "Wireless Connection disabled by hardware switch"

I'm not 100% sure what that means, has anyone else had this predicament?

Thanks
ShadedCS

---

### Post by jtingkir on 2011-05-26
same problem here, clean install, i was using 10.04 before. I thought my wireless switch on the netbook that got messed up.

---

### Post by brandlerson on 2011-05-26
This is usually due to a missing driver. Connecting to a wired network and downloading any missing/required drivers should remedy the situation.

---

### Post by ShadedCS on 2011-05-26
> **brandlerson said:**
> This is usually due to a missing driver. Connecting to a wired network and downloading any missing/required drivers should remedy the situation.

I did the driver check, and there was no drivers missing.

I downloaded a driver that was "Broadcom STA Wireless Driver", but to no avail.

Can you get drivers anywhere else?

---

### Post by josephmills on 2011-05-26
hi there could you please open your terminal (ctrl+alt+t)and type in ```
lspci -nn
``` and then ```
rfkill list all 
``` then paste that here thanks

---

### Post by xian67 on 2011-05-27
Try this post. Worked for me.
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

