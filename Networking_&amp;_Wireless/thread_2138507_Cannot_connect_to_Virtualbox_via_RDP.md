---
title: "Cannot connect to Virtualbox via RDP"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by arthoc on 2013-04-24
Hello,
I've set up Windows 8 x64 in Virtualbox and assigned the VM to the "Bridge adapter" on "virbr0". The IP was gathered via $ ifconfig. Furthermore, I've enabled RDP (including from Non-MS-Machines) in W8's settings. The network in W8 is listed as "Unidentified access" w/ "Limited access". Using the "wlan0"-settings the network is identified, yet it makes no difference for the actual problem:
I cannot access the VM via RDP, tried Remmina as well as WinConn. $ ping works, however.

Can anyone help me? I'm running Ubuntu 12.10 x64.

Greetz

---

### Post by arthoc on 2013-04-25
Oh my god, I feel like totally derpy right now.

It turned out that installing the actual RDP-plugin for VirtualBox is kinda helpful in terms of using the actual RDP-features...

e.g:
[LIST=1]
[*]DL and install VirtualBox 4.2.12 Oracle VM VirtualBox Extension Pack | [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
[*]Set adapter to NAT in settings
[*]Start VM
[*]Check if it's working via $ netstat -an | grep <your port> (in my case, 3389)
[*]Have fun
[/LIST]

Greetz

---

