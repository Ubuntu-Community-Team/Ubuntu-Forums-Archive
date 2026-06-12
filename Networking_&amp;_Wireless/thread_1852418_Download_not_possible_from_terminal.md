---
title: "Download not possible from terminal"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by pavi_elex on 2011-09-30
[SIZE=2]*I am not able to download from terminal.*[/SIZE]

[SIZE=2]It wants to connect through proxy server ( 0% [Connecting to 192.168.0.1 (192.168.0.1)] ) but there is no proxy server, thats why I am not able to download any software from ubuntu software center. Same condition for synaptic package manager too.[/SIZE]

                               Please help me...

---

### Post by WasMeHere on 2011-09-30
> **pavi_elex said:**
> [SIZE=2]*I am not able to download from terminal.*[/SIZE]

It wants to connect through proxy server ( 0% [Connecting to 192.168.0.1 (192.168.0.1)] ) but there is no proxy server...

How is your computer connected to the internet? Directly (wired or wireless) or via a router, wired or wireless LAN?

'192.168.0.1' is a common address for a home local area network router.
Do you have a router? Is it properly connected to your computer and to the internet?

It will be easier to help if you *describe what you have and have done*: internet connection, operating system... and *how* you try to download software.

Good luck
Olle

---

### Post by pavi_elex on 2011-09-30
Actually it is a Local area connection and my computer is connected to ROUTER that is for broad band Internet connection. Actually there must me any file where I should edit so it will connect directly not will try to connect with 192.168.0.1

---

### Post by WasMeHere on 2011-09-30
I am rather sure that 192.168.0.1 is the address of your router, and your communication to the internet will pass through that router.

*You need to configure your router correctly*. Your internet provider should help you doing that.

Then it is almost always very easy to connect to the internet from Ubuntu. The system will do it automatically, so that you can start browsing with Firefox or some other browser, start to use an email program, a chat program or what you want to do.

*Can you connect to your router from your computer* with Firefox? What happens when you enter 192.168.0.1 into the address field (where you normally would enter an internet address). If your router responds and you log in, there will be menus that show the status of the router and the connections outward (WAN) and inward (LAN). Read the manual of the router, it will help you.

*If you cannot connect to the router, try to use another computer* to test if that computer can connect to the internet!

---

