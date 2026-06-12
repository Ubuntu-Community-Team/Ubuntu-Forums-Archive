---
title: "Bad connection between Ubuntu machines?"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by mar_ar on 2012-12-12
I moved from **win.7 **to **Ubuntu** (Unity) on all my machines and really like it.
There is just one issue I just can't solve.

I have **3** machines at home - a **desktop** (with no monitor, keyboard and mouse connected) and **two laptops**.

The desktop is connected by a cable to the router and the laptops are connected with a solid wireless connection.

The **connection **quality inside the local network and outside is **very bad **- when comparing the same computers with the same network with win. 7:

_- using shared folder_ - I shared some folder (using the OS menus) from the desktop with the laptops. I can access the files in the folder but the connection is very slow. for example - trying to play a video file in the folder make the player to stuck again and again.
in my win.7 days I use to play movies on the laptops all over the home using a shared folder.

_- remote controlling by ssh_ -X is very slow and not usable

_- remote controling by the default tools the came with the OS_ - very slow and not usable

_- remote controlling by NX + SSH_ - if nothing is running on the desktop the connection is bad but still can be usable. running some download or even Dropbox sync on the desktop make it too slow.

The way of working with some "server" and the laptops is very critical to my tasks.
With win.7 I could RDP to the desktop and work on it like I'm working on the computer itself. Same with shared folders.

**How can I change the experience? **

---

### Post by SeijiSensei on 2012-12-12
Do all the machines have IP addresses in the same network "subnet," like 192.168.1.1-254?

What kind of ping times do you get between the Ubuntu box and the router?  Between the Ubuntu box and the wifi machines?

Do you have another Ethernet cable you can try?  Is the cable you're using badly crimped or bent?  Try a different port on the router.  Same problems?

If you have another Ethernet cable, try connecting one of the laptops with it and turn off its wireless card.  How well does that machine communicate with the Linux box?

---

