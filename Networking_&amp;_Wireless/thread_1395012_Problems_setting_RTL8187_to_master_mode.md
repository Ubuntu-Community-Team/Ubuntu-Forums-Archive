---
title: "Problems setting RTL8187 to master mode"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by lives4him06 on 2010-01-31
When I try to set my  Realtek Semiconductor Corp. RTL8187 Wireless Adapter to master mode I get the following error.

```
$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

Is this the result of a driver or hardware incapability?

---

### Post by lives4him06 on 2010-01-31
Let me rephrase the question: am I doing something wrong, or is my hardware incapable of handling master mode.

---

### Post by chili555 on 2010-01-31
You may have to take the interface down first:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode master
```I don't have the device, but I believe that, after that step, if it won't go, then it won't go. That is, its driver doesn't support master mode.

---

### Post by lives4him06 on 2010-01-31
Thanks for the reply, I really appreciate it!

I'm still getting the same error:

> $ sudo ifconfig wlan0 down
$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by lives4him06 on 2010-02-04
It appears that you cannot set RTL8187 to master mode at this time.
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-get-rtl8187-in-master-mode-775203/#post3851328]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-get-rtl8187-in-master-mode-775203/#post3851328")

---

