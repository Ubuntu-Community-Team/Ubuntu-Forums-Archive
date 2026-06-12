---
title: "How do I set up remote desktop from Ubuntu to XP over internet?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Xyphoid on 2009-04-14
My local network contains a modem, a router, my XP desktop and my Ubuntu laptop. 

I'm trying to set up a remote connection from my laptop to my desktop through an internet connection. I can make a remote connection in my local network, but I can not make a connection from another network.
I already opened port 5900 for VNC and 3389 for RDP on my router and modem.
But every time I try to connect to the IP address (I get with [http://whatismyip.com/](http://whatismyip.com/)) with Remote Desktop Viewer or Terminal Server Client the connection fails.

Can anyone please tell me how to set up my XP desktop and Ubuntu laptop so that my laptop can make a remote connection from another network?

---

### Post by Mordac85 on 2009-04-14
I'm assuming by modem you mean a normal cable or DSL modem provided by your ISP?  Now the router, which I assume is connected to your modem on one side (WAN() and your other systems on the other (LAN).

**On the Router:**[list][*] Choose some obscure port number to use rather than the RDP default ( I normally prefix a number between 5 & 10 to the default port so I can remeber it easily)
[*] Point that port to your XP desktop's IP address
[*] Check the IP of the router's WAN connection (your ISP)[/list]
**On the XP desktop:**[list=1][*] Open regedit
[*] Set [FONT="Courier New"][COLOR="DarkRed"]HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TerminalServer\WinStations\RDP-Tcp\PortNumber[/COLOR][/FONT] to the port number you chose earlier
[*] Right-click 'My Computer' and select Properties
[*] On the Remote tab clear the top checkbox (initiate requests)
[*] Check the bottom checkbox (allow control)
[*] Hit OK/Apply and close it
[*] Reboot (of course)[/list]
Now try to connect to your system using the RDP protocol to the IP of your router, not your desktop using the port number you chose.

---

### Post by Xyphoid on 2009-04-15
Thnx Mordac85,

I'll try it this afternoon.

-edit-
I found out why it wasn't working.
I was using VNC and disabled RDP.
But Terminal Server Client works with RDP.

So:
RDP -> Terminal Server Client
VNC -> Remote Desktop Viewer

Very confusing....

So when I want to connect through another network I have to use RDP. Because I can't get
VNC to work through another network. Too bad, cause I like Remote Desktop Viewer better than Terminal Server Client.

---

### Post by Mordac85 on 2009-04-15
You can install a VNC server on your XP box and use the VNC protocol or use your VNC viewer with the RDP protocol.

---

### Post by Xyphoid on 2009-04-16
> **Mordac85 said:**
> You can install a VNC server on your XP box and use the VNC protocol or use your VNC viewer with the RDP protocol.

I already have VNC on my XP box. If I want to use VNC with the RDP protocol, I guess I have to install VNC viewer? Because I can't choose the protocol in Remote Desktop Viewer.

---

