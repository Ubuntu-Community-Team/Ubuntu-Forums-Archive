---
title: "My automatic dongle"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by HannuMR on 2012-11-26
12.04/Huawei e367.

First make Startup-menu in terminal:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

Now it is under Stop-button.

Make txt-file and save it in Home with these commands:

sleep 4s; nmcli nm wwan on
sleep 5s; nmcli nm wwan on
sleep 6s; nmcli nm wwan on
sleep 7s; nmcli nm wwan on
sleep 8s; nmcli nm wwan on
sleep 9s; nmcli nm wwan on
sleep 10s; nmcli nm wwan on
sleep 11s; nmcli nm wwan on
sleep 12s; nmcli nm wwan on
sleep 13s; nmcli nm wwan on

Go to Home, find that file > Properties > Rights > Allow run like application.
Go to Startup-menu, and add the same file for startup.
Reboot PC.

Hope you understand my english.

---

