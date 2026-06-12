---
title: "How to boot with NIC setup"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2006-02-25
I've configured my computer to be able to connect to the internet with WPA on a wireless USB adapter. I always have to enable it with the terminal window. Can anyone please tell me how to automatically do this during boot-up. I have to sudo modprobe ndiswrapper to get it to work in the terminal than sudo dhclient to get connected to the internet. Can I automate this? Thanks in advance.

---

### Post by Lambert on 2006-02-25
There should be instructions on this page so it starts at boot.

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by Floppyjoe on 2006-02-25
The last posts hyperlink was no help. My installation is getting flaky now. Can't reboot or turn off the computer without holding in the button. I think I'll need to reinstall.

---

### Post by jamesr on 2006-02-25
Post the output of
cat /etc/modules

I think you will have to add a reference to ndiswrapper

---

