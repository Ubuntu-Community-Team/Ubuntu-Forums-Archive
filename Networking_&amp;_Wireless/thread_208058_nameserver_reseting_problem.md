---
title: "nameserver reseting problem"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by silvercliff on 2006-07-02
ok so i have found out that i can only use the internet if i manually change */etc/resolv.conf* so that instead of *nameserver 192.168.1.1*, i have *nameserver xxx.xxx.xxx.xxx*, where xxx.xxx.xxx.xxx is a value i have obtained from my adsl2+ modem webcm. after a certain amount of time (not sure how long) or i restart X or ubuntu it resets.

how can i stop this?  it is very annoying having to change it so i can go onto the internet.

---

### Post by scxtt on 2006-07-02
what about setting it to what you want - then making the file read-only?

---

### Post by silvercliff on 2006-07-02
how do i make it read only?

---

### Post by scxtt on 2006-07-02
sudo chmod 444 /etc/resolv.conf

---

### Post by silvercliff on 2006-07-02
thanks, ill restart and see if it works :)

---

### Post by silvercliff on 2006-07-02
didnt work, i can still change the file using sudo, and it reset on reboot as well :(

---

