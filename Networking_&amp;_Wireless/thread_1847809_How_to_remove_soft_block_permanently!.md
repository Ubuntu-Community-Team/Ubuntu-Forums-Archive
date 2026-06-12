---
title: "How to remove soft block permanently!"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by kingfisher_ph on 2011-09-21
Sorry everyone because of this dump question, but i'm pretty new in Ubuntu 11.04 64bit!
This is my problem:
- Everytime i start ubuntu, i have a problem with my wireless networks. After a while searching in the internet, i find out "soft block" in "rfkill list". This is my result:
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
- Then, i keep searching and i find how to solve this problem: 
"sudo rmmod -f acer-wmi"
"sudo rfkill unblock all"
That's the result:
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

After i do 2 lines of code above in terminal, my wireless network works perfectly!! :D
However, Every time i restart my laptop, this problem occurs again!! Yeah,  I just run 2 lines of code above again, and it's ok!
- Ok!That's not the point, The point is that i have to execute 2 lines of code above each time i start my laptop. Now, i'm tired of doing it again and again!!
- Does anyone help me to remove those things permanently??!! 
Thanks you very much!!

---

### Post by wildmanne39 on 2011-09-21
Hi, we just do this:
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
if I helped you in anyway would you show your support for me becoming an ubuntu member by clicking on the red link in my signature? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by kingfisher_ph on 2011-09-21
Thanks you so much! It's really helpful!

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! am glad I could help.

---

