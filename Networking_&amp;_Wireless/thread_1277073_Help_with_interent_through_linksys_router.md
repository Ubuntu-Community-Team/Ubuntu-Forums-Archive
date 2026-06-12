---
title: "Help with interent through linksys router"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by pspgeek1993 on 2009-09-27
Ok i have ubuntu installed and i can connect to my linksys router and cannot get the internet. Any help would be greatly appreciated

---

### Post by t0mppa on 2009-09-28
If you can connect to your router, then I'd guess it's either a routing issue or a DNS issue.

Try pinging 74.125.79.99, if you can reach that, then your DNS settings and if you cannot reach it, then you should check your routing.

---

### Post by ApEkV2 on 2009-09-28
Can you connect with the internet with other computers?
If you can't, get into your router and check if you have an internet IP address.
Sometimes the connection between the home network and the hub site go down, although this usually doesn't last more than 8 hrs.

---

### Post by kevdog on 2009-09-28
Steps to confirum:

1. Can you ping your router? (192.168.1.1)
2. Can you connect to the configuration screen on your router ([http://192.168.1.1)?](http://192.168.1.1)?)
3. Can you lookup a dns address: nslookup google.com
4. As stated above this is usually a routing or dns related issue.

---

### Post by grturner on 2009-09-28
have you confirmed that you actually have internet running to the linksys router and the settings are working?

---

### Post by hockeytux on 2009-09-28
I had a problem with a LinkSys Router as well when I moved. It actually said on the package 'For Windows and Mac' (it came with the new phone/internet connection) and I had no other option of choosing a different router.

I couldnt get it to work either but solved it by configuring everything with an older laptop running Windows XP. Then I unplugged the ethernet cable from the laptop and put it into the Ubuntu desktop and everything worked rightaway.

---

