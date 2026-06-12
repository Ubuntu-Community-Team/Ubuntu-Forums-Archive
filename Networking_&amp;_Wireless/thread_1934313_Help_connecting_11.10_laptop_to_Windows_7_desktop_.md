---
title: "Help connecting 11.10 laptop to Windows 7 desktop over WAN"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by sethbuntu on 2012-03-01
I just wiped my laptop and put 11.10 Ubuntu on it. When I select Windows network, I get "Unable to Mount Location. Failed to retrieve share list from server" I'm sure this has been asked before, but I can't find my specific situation. Thanks for your help all!

---

### Post by Paddy Landau on 2012-03-02
I presume you are using Nautilus?

In order to access Windows shares, you need to install Samba, which emulates the Windows network.

Please check that you have installed samba, system-config-samba, smbclient and nautilus-share. You may have to reboot.

Run Samba and set up your machine. You may have to reboot again.

---

