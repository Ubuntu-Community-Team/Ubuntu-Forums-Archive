---
title: "Colours missing in s-video"
date: 2009-05-17
forum: Multimedia Software
---

### Post by aja_tus on 2009-05-17
I upgraded from 8.04 to 9.04 and lost colours in TV. I was using two xorg.conf files with 8.04, one for DFP and one for TV and started X using either one. The files still work except that colours are missing in TV. I have tried all kinds of settings in nvidia-settings GUI: separate X-screen with the other display enabled/disabled, twinview etc. I often got a picture to the TV but not with colours. 
I browsed through a lot of forum threads but none seem to have a similar problem. 
I have in xorg.conf "SVIDEO" and "PAL-B" (I am in Europe) and they seem to be executed when looking at Xorg.0.log. I have nvidia-glx-180.44 which came with the upgrade. In 8.04 I had nvidia-glx-new. 
I have only a vague idea of the different display modes and of the parameters involved. Any guide available which explains these parameters and their allowed values? For example the use and format of "metamodes".

---

### Post by andrewc6l on 2009-05-17
Here's a couple links for the nvidia options:

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=174&p_created=1101836147&p_sid=pLG8Z2yj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTMsMTMmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eCBjb25maWc*&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=174&p_created=1101836147&p_sid=pLG8Z2yj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTMsMTMmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1saW51eCBjb25maWc*&p_li=&p_topview=1)

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html)

---

### Post by aja_tus on 2009-05-22
I still have this problem. I purged nvidia-glx-180 and installed nvidia-glx 71 but no help. Then moved to nvidia-glx-96 and then to nvidia-glx-173.
I think I'll try a clean installation next.
I have a 7600 GT and ASUS M2N-E.
This does not seem to be an xorg.conf problem because immediately after boot a M2N-E logo appears in colour in DFP but in TV it is gray. Nvidia driver could be in false mode (NTSC?) but I don't know how to set it right.

---

### Post by aja_tus on 2009-05-23
It's a bit funny, the connector was not fully inserted. Still I'm glad I found it before doing installation.

---

