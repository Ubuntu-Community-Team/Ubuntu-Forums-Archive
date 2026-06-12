---
title: "Windows 7 PC can't connect to Ubuntu Server/SambaH"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by calelettus on 2009-12-27
I set up Samba on a 9.10 Ubuntu server and can access the shares I set using my Ubuntu workstations with no problem. However, my Windows 7 Pro workstation can't authenticate to the server. I tried setting the local security policy as outlined by others:

Control Panel - Administrative Tools - Local Security Policy
Local Policies - Security Options
Network security: LAN Manager authentication level
Send LM & NTLM responses
Minimum session security for NTLM SSP
Disable Require 128-bit encryption 

and that didn't work. The error is "Unknown login name or password" but they are correct. They work in Linux. Any suggestions? Thanks.

---

