---
title: "MyGica Mini DVB-T2 USB Stick T230 broken by software update"
date: 2020-07-11
forum: Multimedia Software
---

### Post by KJKJKJ on 2020-07-11
Today is 11th July. A software update dated 10th or 9th is highly likely to have broken my tvheadend setup using these fine USB tuners  MyGica Mini DVB-T2 USB Stick T230 

Fortunately the remedy is simple but before I found it my machine would hang during boot with blank screen, until I physically removed the USB tuners.

The remedy is to copy a firmware file to /lib/firmware with appropriate ownership and permissions

 -rw-r--r--  1 root  4.9K Jul 11 13:34 dvb-tuner-si2158-a20-01.fw
I found a copy on github.

I use xubuntu 20.04 LTS with i3 as window ,manager.

---

