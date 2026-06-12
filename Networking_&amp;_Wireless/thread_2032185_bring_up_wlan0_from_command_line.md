---
title: "bring up wlan0 from command line"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by icegood on 2012-07-23
How to do subj?
tried like [there]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/command-line-to-bring-up-wlan0-520367/")
doesn't work because 
```

Could not connect to wpa_supplicant - re-trying

```[That one ]("http://ebixio.com/blog/2011/09/15/how-to-make-wpa_cli-talk-to-wpa_supplicant-in-ubuntu/comment-page-1/#comment-10764")not valid anymore. WTF???

Tried also like [there]("http://ircanswers.com/ubuntu/292318/bring-wlan0-reconnect-command-line")
Doesn't work or i did smth wrong.
==========
How many other bugs will i discover today???

---

### Post by Zorael on 2012-07-24
Hm, I think the Upstart networking init scripts *should* emit signals to trigger scripts in **/etc/network/if-up.d/** and **if-pre-up.d/**. Those directories should should include symlinks to **/etc/wpa_supplicant/ifupdown.sh**; are those missing?

Secondly, are there any interesting error messages in **/var/log/syslog**?
```
$ grep wpa_supplicant /var/log/syslog
```

You could also try to start it manually and see if it simply freaks out.
```
$ sudo wpa_supplicant -usBP /run/sendsigs.omit.d/wpasupplicant.pid -O /var/run/wpa_supplicant
```

---

