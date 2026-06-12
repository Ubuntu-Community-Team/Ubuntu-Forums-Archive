---
title: "Mapping the network drive"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by whhs41 on 2009-06-05
I have been using this awesome Guide:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

However I am confused as to what the sharename is supposed to be.  Here is what I want to happen.

I want the following network folder to be permanently mapped on Ubuntu to /media/haines it

Windows Server 2003
Path : \\Haines\Shared$\IT

This command:
//servername/sharename  /media/mountname  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

Is killing me.  I cannot figureout what the sharename should be.  Any suggestions?  Thanks from a noob :)

-Trevor

---

### Post by whhs41 on 2009-06-05
Any suggestions from anyone?

---

### Post by whhs41 on 2009-06-05
Got it!

[http://mixeduperic.com/Linux/Networking/how-to-map-a-windows-network-drve-in-ubuntu.html](http://mixeduperic.com/Linux/Networking/how-to-map-a-windows-network-drve-in-ubuntu.html)

---

