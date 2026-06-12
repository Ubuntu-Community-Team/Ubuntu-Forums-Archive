---
title: "Reboot / Resume Networking after Hibernate"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by Crosility on 2011-10-10
This title has appeared on many, but none pertain to my problem.
Actually, in a sense, I feel I may have created my own problem, to fix another problem.

So.. here we go.

I am running eth0.
I am dual booting windows vista sp2.
I am on a laptop.
Wired internet works perfectly switching from ubuntu and windows if the ip is static in my linksys 4200 router.
Wired internet does not work in ubuntu, if I have a static ip on the router when switching from windows to ubuntu. But does work when switching from ubuntu to windows.

Therefore, I solved my need for a static IP when running ubuntu by changing the mac address in ubuntu for my eth0 connection. Then changing the static ip in my router. Success. I can switch between windows and ubuntu flawlessly. Ubuntu has a static ip, windows a dynamic. Just what I needed.

Problem that has now occurred:
I hibernate often, (2 hours of non-use).
Internet would typically resume, and that was nice.
Now.. my internet does not resume, I either need to restart my computer or.. manually fix it another way.

Here's what I did to achieve static ip:

> >> sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback^ That is what comes up in a document.
I added:
> auto eth0
iface eth0 inet dhcp
    hwaddress ether xx : xx : xx : xx : xx :dc (There is no spacing.. just stupid smiley faces)My hwaddress of my card is actually db. I changed to dc for ubuntu. And it works.

This seems to work when I come back from hibernation:
> >> sudo /etc/init.d/networking restart
But, I would rather have it do it without my need to type that in.

So, coming to other ubuntu users, who may notice what the problem may be.
Thank you for any help, I'm free to provide further information.

---

