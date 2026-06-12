---
title: "my internet stopped working well"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by xchicax on 2009-06-19
hey,

i have an asus eee1000ha and ubuntu 9.04 - the notebook remix. i had it for a few months, and had no problems with the wireless, besides the fact that sometimes the wireless will request a passwored for a wep network in a middle of a session (while already being connected to the network), and minor temporary diffuclties connecting that will solve themselves with a reboot of the computer and the router.

in the last few days my internet has been acting strange. it will connect for a few minutes, and then suddenly stop working, or downloads suddenly become extremely slow, and get stuck a lot (checking to see if there are new updates can take half an hour). reboot doesn't help at all. i use both epiphany and firefox, and the problem presists with both browsers. my internet works just fine on my roommate's windows computer, so i know it is the ubuntu that is slipping. through the whole time, the ubuntu seems to think it is connected to the wirless, but it is just not functioning properly. my internet is a wep wirless, so i don't know if the problem is only with encrypted networks or generally speaking.

i haven't used ubuntu for a while so i am a little rusty. detailed instructions will be appreciated.

---

### Post by papangul on 2009-06-20
If you are sure that quality of service provided by your isp is ok and that your roommate is not jamming the bandwidth then possible solutions are:

1. Disable ipv6:
In terminal type> sudo gedit /etc/modprobe.d/blacklistand add 'blacklist ipv6' to the end of the file.

2. Install WICD network manager:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

2. Set opendns as your dns server:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by cariboo on 2009-06-20
ipv6 support is compiled in the kernel in Juanty. You may want to try [this]("http://ubuntuforums.org/showpost.php?p=7059555&postcount=24") to disable it.

---

### Post by xchicax on 2009-06-21
the link to the ipv6 doesn't work so i didn't manage to disable it. i tried switching to wicd, which made the situation only worse. switching to open dns didn't help either.

---

### Post by vaikz on 2009-06-26
Like cariboo907 said, disable ipv6 on kernel parameters. all you need to do is open the /boot/grub/menu.lst and add ¨¨ipv6.disable=1¨ on the kernell parameter. it works for me. And also I&#7743; using wicd and opendns and no problem on my internet connection. But what really improves on my internet connection is by disabling the IPV6 on the kernel parameters.

Hope this will help.

---

