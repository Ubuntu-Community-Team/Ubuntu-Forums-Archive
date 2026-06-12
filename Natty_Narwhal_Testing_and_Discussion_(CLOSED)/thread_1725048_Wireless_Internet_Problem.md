---
title: "Wireless Internet Problem"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by H0lyGanGs7eR on 2011-04-09
Hello, after upgrade I have problem with my wireless connection. I use the driver rt73usb and my internet is really slow now. I had this problem before, but I solved it with writting this
```
sudo iwconfig wlan0 power off
```
Any solutions?

---

### Post by H0lyGanGs7eR on 2011-04-09
Nothing???

---

### Post by donniezazen on 2011-04-09
You are not alone buddy. Natty has been selective when it comes to wifi. My netbook (Lenovo Ideapad s10e) works perfectly but i tried everything but nothing worked on my laptop (Dell Inspiron E1505).

---

### Post by geojorg on 2011-04-09
Same issue here last week and solved using connman instead of network-manager

sudo apt-get install connman

---

