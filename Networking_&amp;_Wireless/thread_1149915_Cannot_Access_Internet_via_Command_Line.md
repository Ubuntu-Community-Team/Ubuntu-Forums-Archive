---
title: "Cannot Access Internet via Command Line"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by RobRocker7 on 2009-05-05
Howdy Everyone,

Problem: I am trying to access a remote server using SSH, but cannot connect through the terminal. using a ping on google.com does not return any successful packets.

My company has an ISA proxy setup.

I have NTLMaps and my network proxy setup correctly (i assume) so that Skype, Firefox and the package manager work correctly.

What I have done:

[LIST]
[*]Added export http_proxy='http://127.0.0.1:5865' to ~/.bashrc (I have also tried my network's ISA proxy)
[*]Added proxy settings under Network Proxy and "Apply System-wide" These settings have been set to 127.0.0.1:5865
[/LIST]
I am confused on what I can try next to get this to work. Im also writing a Python web app that needs to ping an external API. I am developing locally and the firewall catches the response and doesn't send it.

Thanks,
-Robert

---

