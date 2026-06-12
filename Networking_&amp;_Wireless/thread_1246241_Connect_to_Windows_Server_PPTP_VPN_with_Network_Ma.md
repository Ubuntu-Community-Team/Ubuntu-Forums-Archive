---
title: "Connect to Windows Server PPTP VPN with Network Manager"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by cecil_T on 2009-08-21
I've had many problems getting VPN to work through Network Manager in various Ubuntu versions.  I now have a solid working connection through it just by getting the config set properly.  Here is my setup, I'm hoping it will help some people.

Goal: Connect to Windows Server 2003 VPN using Network Manager via PPTP in Ubuntu Jaunty.

Steps:
[LIST=1]
[*]Install “network-manager-pptp” package and dependencies
[*]Reboot computer (this is important, nothing will work until you reboot)
[*]Click on Network Manager icon, go to “VPN Connections” then “Configure VPN”
[*]Click “Add”, select “PPTP”, then click “Create”
[*]Fill in the following information:
[/LIST]

[INDENT]VPN SETTINGS:
-- Add/Edit Main Dialog --
Connection name: [VPN Connection] *
Gateway: [vpn.example.com]
User name: [username] **
Password: [password]
NT Domain: [company domain] **
-- Advanced button --
PAP: UNcheck
CHAP: UNcheck
MSCHAP: UNcheck
MSCHAPv2: check
EAP: UNcheck
Use Point-to-Point Encryption (MPPE): check
Security: 128-bit
Allow stateful encryption: UNcheck
Allow BSD data compression: check
Allow Deflate data compression: check
Use TCP header compression: check
Send PPP echo packets: UNcheck
-- IPv4 Settings tab --
Method: Automatic (VPN) addresses only
DNS Servers: [enter DNS servers on the destination network]
Search Domains: [domain].local ***[/INDENT]

Note - you will get a popup from the Keyring manager or whatever, I just click "Always allow".  You may see it once or twice and then it should be fine.

* - whatever you want here, this is just the name of the connection

** - Filling out the "NT Domain" slot with the domain name works for me, I don't need to put domain\username in the username slot.  The "NT" part threw me off because it's not technically an NT domain (Windows 2003 domain).

*** - You may need to add text to the "Search Domains" box depending on how the destination network is setup with DNS, etc.  In my case it's [domain].local to resolve hosts on the destination network.

---

### Post by extraspecialbitter on 2009-08-28
This worked flawlessly.  Thanks for writing it up.

---

### Post by pag747 on 2009-08-28
Awesome ... thanks so much!!

---

### Post by markomb on 2009-09-13
Thank you for the instructions. It works... I can connect to the VPN. However, I cannot see/connect computers in the network of my company. I left the Search Domains and DNS Servers fieds empty, could this be the reason? Where can I find this data?

---

