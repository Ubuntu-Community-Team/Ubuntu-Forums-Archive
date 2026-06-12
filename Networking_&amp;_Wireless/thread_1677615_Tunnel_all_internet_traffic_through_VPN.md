---
title: "Tunnel all internet traffic through VPN"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by tghasemi on 2011-01-29
I've configured my PPTP VPN server using this guide: [http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html") and everything seems to be fine. My clients are able to connect to the network and they have access to my local network but the internet traffic doesn't go through the VPN connection ! on my mac client there is an option that I can check to send the traffic over the VPN connection and it works with my current settings on the server, but on windows clients (tried with win xp) once the connection is established the internet connection doesn't work anymore ! the only reason i'm setting up this server is to be able to use my office's ip address in other places but no luck so far .. any idea how i can fix this ? as i said before my mac client works fine after checking the option to send the traffic over vpn but there is no such option on windows ..
Thanks

---

### Post by YesWeCan on 2011-01-29
You are asking a Windows question.

I use OpenVPN for what you are doing which is ssh based rather than pptp and is arguably better. For internet gateway redirect the OpenVPN client on Windows has to be run as administrator so that it has authority to change the routing table.

Perhaps your are having an authority issue or perhaps you are having a "Windows won't let you do it" issue.

---

