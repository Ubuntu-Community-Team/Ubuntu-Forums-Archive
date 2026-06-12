---
title: "Strange artifacts with Xorg on powerbook"
date: 2008-12-23
forum: Multimedia Software
---

### Post by nebopolis on 2008-12-23
I'm having a rather odd problem with an older Powerbook that I just installed ubuntu on. I was able to install ubuntu with no problems, but once I booted it X had a "painterly" effect (jittering blocks of the screen moving back and forth, up and down making it impossible to read text.) The graphics card is a Ati rage mobility M3 agp 2x according to the xorg.conf, and it is using the "ati" driver. I tried changing the driver to vesa or vga, but that did not solve the problem. Graphics work fine in text mode, so I am suspecting a xorg configuration problem. 

Xorg.conf: [http://pastebin.com/m149c0602](http://pastebin.com/m149c0602) 
/var/log/Xorg.0.log: [http://pastebin.com/m752ce8c6](http://pastebin.com/m752ce8c6)
Screenshot:[http://orangutanpotato.com/images/1223081100c.jpg](http://orangutanpotato.com/images/1223081100c.jpg)

---

