---
title: "Connect via Remote Desktop Viewer?"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2009-12-09
I can't connect from my notebook to my wife's netbook using Remote Desktop Viewer.  

I can find my own network name address or whatever it's called.  I can also find my IP address and I know what hers is.  I can send her my VNC name that I get from System>Preferences>Remote Desktop>Desktop Preferences......but there's no way I can find her VNC information on her netbook.

We're both running Ubuntu 9.10.

I need to know exactly how to do it.

---

### Post by rogerdean on 2009-12-10
Me too... the help files don't quite give me enough. If one knows the IP, what exactly should be typed in the Host box?
Many thanks!

BTW, for those of us with limited bandwidth, there's a new version of the viewer software which gives options for jpeg compression and colour depth setting, making things much faster. I can't find any packages for Karmic (I don't think they're built, although the developer is asking for help setting up a PPA), but the ones for Lucid seem to work fine on Karmic. You don't need to update the server package

[http://mirrors.kernel.org/ubuntu/pool/main/g/gtk-vnc/libgtk-vnc-1.0-0_0.3.10-2ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gtk-vnc/libgtk-vnc-1.0-0_0.3.10-2ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/v/vinagre/vinagre_2.29.1-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/v/vinagre/vinagre_2.29.1-0ubuntu1_i386.deb)

---

### Post by rogerdean on 2009-12-10
oh yes, and the new version also does 'reverse connections', for getting around tricky firewalls. very good work

---

### Post by tlcstat on 2009-12-11
open a terminal and type
vncviewer -fullscreen 192.168.1.100:0 (replace the 192.168.1.100 with your remote Ip). You will need to append the :0
If you don't have vncviewer installed. apt-get install vncviewer.
You should have Remote Desktop setup on the other machine.
If you successfully connect Press F8 for exit and options.
Thats it.

---

### Post by rogerdean on 2009-12-13
Thanks very much, I'll try that
Cheers

---

