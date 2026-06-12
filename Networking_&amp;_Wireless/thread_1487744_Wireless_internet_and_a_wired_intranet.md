---
title: "Wireless internet and a wired intranet"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by gatordude on 2010-05-19
I have my internet connection via a wireless USB adapter and that works fine. Recently I connected my pc (Ubuntu 9.10) through a wired switch to my modified xbox so I can watch my videos in my office. I can share my content with my xbox (except for the items on my external USB HD's - I am working on that and will post that question elsewhere) but when I have my PC's wired connection plugged into the switch I can not surf the web or check email. It gets stuck at resolving host and then times out. If I disconnect the pc from the switch it sometimes connects  before it times out. Usually it is quicker if I reboot without the wired intranet connection.

Any ideas?

---

### Post by gatordude on 2010-05-24
Yes it is that simple. Many thanks to SteveGYBE on the Fedora forums.

Here is the fix.

If your Internet access is via wlan0, you will need the default route to direct traffic there instead.

You can achieve this by deleting the existing default route and adding the route via your wireless card using the "route" command. However, it may be easier to achieve this in other ways. Do you use DHCP to configure your adapters or set them manually?

If you use NetwokManager to configure eth0, there is a nice feature which enables you to disable this connection from being used as the default route. You can find it by:
Right-clicking on the NetworkManager Icon in the notification area on the Panel, and selecting "Edit Connections..."
On the Network Connections dialog, select "System eth0" on the "Wired Connections" tab and click "Edit...".
On the "Editing System eth0" panel, select the "IPV4 Settings" tab and click the "Routes..." button.
At the bottom of the panel "Editing IPV4 routes for System eth0", check the box "Use this connection only for resources on its network".
Use "OK" and "Apply" buttons to save your setting and close the dialogs. Phew!

---

