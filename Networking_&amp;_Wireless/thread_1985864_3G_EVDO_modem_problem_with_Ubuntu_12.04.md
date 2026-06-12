---
title: "3G EVDO modem problem with Ubuntu 12.04"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by surja on 2012-05-23
a 3G modem (EVDO CDMA brand - Captitel, device id - 1c9e:9e00) worked well with 11.04 and 11.10. With 12.04, it is detected in lsusb, but does not show up in Network Manager. I have to configure this modem from Network Manager but saving its username and password and then in subsequent times, click the name of the modem for it to connect. But it does not show up in Network Manager.
Tried some workarounds posted in these forums but none of them are permanent solutions. Personally it is extremely irritating that something which worked with a previous versions breaks with the new one. It seems like there is a serious problem with 3G USB modems in 12.04 in general, especially those which worked previously, but even after a month there seems to be no working solution.

---

### Post by fantab on 2012-05-24
Is it being detected as a storage device or a Modem... post the output of *lsusb*.

Sometimes it takes time for USB modem to show up in Network Manager after its plugged in, so be patient until it shows up. If it does not then it is probably being detected as a storage device and not modem. 

Check to see if **usb-modeswitch** is installed... if not install it. It is actually pre-installed by default. Try removing it and then reinstall.

---

### Post by surja on 2012-05-24
> **fantab said:**
> Is it being detected as a storage device or a Modem... post the output of *lsusb*.

Sometimes it takes time for USB modem to show up in Network Manager after its plugged in, so be patient until it shows up. If it does not then it is probably being detected as a storage device and not modem. 

Check to see if **usb-modeswitch** is installed... if not install it. It is actually pre-installed by default. Try removing it and then reinstall.

this is the output of 'lsusb':
surja@surja-Lenovo-G570 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai 
Bus 002 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 004: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 008: ID 1c9e:9e00 OMEGA TECHNOLOGY

1c9e:9e00 is the modem's device id.
Reinstallation of usb-modeswitch does not make a difference.

---

### Post by fantab on 2012-05-24
Okay... have you tried this [link]("http://duopetalflower.blogspot.in/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html")?

Didn't you solve this [**here**]("http://ubuntuforums.org/showthread.php?p=11919130")

---

### Post by surja on 2012-05-27
> **fantab said:**
> Okay... have you tried this [link]("http://duopetalflower.blogspot.in/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html")?

Didn't you solve this [**here**]("http://ubuntuforums.org/showthread.php?p=11919130")

that link is for Ubuntu 10.04. This modem started working automatically in Ubuntu 10.10 and worked perfectly in 11.104 and 11.10. The problem started with 12.04.

I did think that it was solved, but following the steps in that post, it works sometimes and not always. It is not a permanent fix and in my opinion something that worked so well in the past should not have stopped working in the new distro. Hard to tell what is really the problem and which package is responsible for this.

---

