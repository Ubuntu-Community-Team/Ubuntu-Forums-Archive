---
title: "connect to a VPN in Linux"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by veronym on 2012-08-08
[FONT="Courier New"]Hi all,

I'm connecting to my company network via **MS Windows VPN client**.
Is there a way to connect to such a VPN in Linux?

How do I proceed in Windows:
In the "Network connections" control panel, I select 
"Create a new connection" task.
"New Connection Wizard" starts.
On the second page of the wizard, I select 
"Connect to a private network, such as your workplace network".
On the third page of the wizard, I select:
"**Virtual Private Network connection**".

**Properties of the connection** are set as follows:
"Security" tab: Advanced Settings button
Advanced Security Settings dialog is set as follows:
- Maximum strength encryption (disconnect if server declines)
- Protocols allowed: Microsoft CHAP Version 2 protocol.
- Checkbox "For MS-CHAP based protocols, use my Windows logon and pwd" checked.

"Networking" tab: type of VPN is set to "PPTP VPN". 
PPP Settings dialog: all checkboxes are checked.

Thanks a lot,

Veronym
[/FONT]

---

### Post by albandy on 2012-08-08
Network icon --> vpn connections --> configure vpn
then select "add" and configure your vpn parameters

---

