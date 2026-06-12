---
title: "Adobe Acrobat Reader crashes in VNC session using Trust Tahr (14.04.5 LTS)"
date: 2017-01-04
forum: Multimedia Software
---

### Post by trivedia on 2017-01-04
When I try to open Adobe Acrobat Reader ('acroread') in a remote VNC session (please see 'Technical Details for VNC Session' below), I can barely see the frame of reader before it crashes. I am unable to debug the matter any more because there is neither any error message nor can I find any relevant log files to look at. I see this problem on Trusty Tahr (14.04.5 LTS) and not only Precise Pangolin (12.04.5 LTS), which is what I used before upgrading and where this issue did not exist. 

Technical Details for VNC Session
====================
+ VNC Server started using 'vnc4server' on desktop running Trusty Tahr (14.04.5 LTS)
(I have tried FVWM ('fvwm2') and Gnome ('gnome-session') as the desktop environment for the VNC server, configured in  ~/.vnc/xstartup as can be seen in attachments xstartup.fvwm.txt and xstartup.gnome.txt, respectively.)
+ Remote VNC session started using 'ssvnc' using laptop running Trusty Tahr (14.04.5 LTS)

---

### Post by ajgreeny on 2017-01-04
Is it essential for you to use the Adobe Acrobat Reader or will any PDF application work for you?
There are many available in Ubuntu that should work without crashing, but I assume you need some function that is not available in them such as form filling.

---

### Post by trivedia on 2017-01-05
It is not essential for me to use Adobe Acrobat Reader and for now I have switched to Evince. However, I have become familiar with Adobe Acrobat Reader, even if not as much for the functionalities, but its look and feel. Therefore, while I can transition to something else, I thought it would be good to explore and see if there is a solution.
Thank you for your response.

---

