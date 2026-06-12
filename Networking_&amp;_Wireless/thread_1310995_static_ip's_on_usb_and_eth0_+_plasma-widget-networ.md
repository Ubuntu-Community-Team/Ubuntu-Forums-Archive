---
title: "static ip's on usb and eth0 + plasma-widget-networkmanagement"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by woefulwabbit on 2009-11-02
Ok, this is starting to get me really annoyed.

I know I can remove network manager and solve all my problems with /etc/network/interfaces however I lose the plasma widget's nice capability of detecting and configuring my usb0 connection automatically when I plug in and out an embedded development board I'm working on.

So I'm giving plasma-widget-networkmanagement a chance again after my 9.10 upgrade. If everything works fine, I don't have to do "ifdown usb0; ifup usb0;" everytime I restart the dev board.

The first thing I've found is that i need to network manager to manage eth0, which means removing the eth0 lines from /etc/network/interfaces. This is because network-manager will *wipe out* my dns servers and domain from /etc/resolv.conf once it is started, so the dns servers have to be configured for an eth0 connection.

So I create an eth0 connection and a usb0 connection in "Network Connections" with static ips and the dns server/domain for the eth0 connection. From the widget icon in the system tray, I can select my eth0 and usb0 configured connection and everything works fine.

Here lies next problem, when I plug out and plug in the usb0 device, or when I restart Kubuntu, network-manager will immediately connect to "auto eth0" and "auto usb0" (which are configured to use DHCP) instead of the connections I have configured. I have to manually switch to my static configurations EVERYTIME. I've checked the configurations and I've no way to disable "auto eth0" and "auto usb0", or to set my static configurations to default. I can enable "Connect automatically" for both connections but neither will connect automatically. I looked at ~/.kde/share/config/networkmanagementrc and ~/.kde/share/apps/networkmanagement and found nothing that can disable "auto xxxx" or set my connections to default.

Am I missing something?

---

