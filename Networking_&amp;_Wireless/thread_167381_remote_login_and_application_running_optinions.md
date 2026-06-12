---
title: "remote login and application running optinions"
date: 2006-04-28
forum: Networking &amp; Wireless
---

### Post by kerry165 on 2006-04-28
Hi all,

Looking for advice here please. Have set up an Ubuntu machine for me to learn about its functionality.

One thing I need to do is login on the “server” to run apps on that system, saving comms time and data traffic. A bit like using Terminal Services on Windows/Citrix. The “terminal” in the first instance being a Windows based box.

Searching the forum implies that I have to use rlogin or one of its derivatives. Some threads include phrases like, “*no matter what you don’t activate this service*”. We all know that the only secure computer is one that is switched off and locked in a building that does not allow a human being any near the equipment. Everything else is a compromise.

The reason for this exercise, is a need to run an app from a remote site with a slow(ish) comms line. The comms link will use a hardware firewall/VPN solution and the VPN box gives the remote PC a local IP identity. Opening the app remotely (and accessing the files across the VPN link) is too slow. The test is not using a client/server app. I have tried VNC and that seems great for a single remote session. Ideal for remote admin & diagnostics.

The next test is that I am looking at performance and overhead issues for multiple remote accesses to the server.

If I take the approach (from the threads) that rlogin is a right/good approach then I looked at what the Package Manager says is available for me for rlogin. Without knowing the dependencies, I see in the list:
[COLOR="Blue"]rsh-server[/COLOR], [COLOR="Blue"]rsh-redone-server[/COLOR], [COLOR="Blue"]openssh-server[/COLOR] and [COLOR="Blue"]krb5-rsh-server[/COLOR].

[COLOR="Magenta"][B]What is the general opinion?
Do I need to install (and configure) one of these items, or a combination of them?
Should I be looking at another solution?[/B][/COLOR]

Your opinions are most welcome.

Kerry

---

