---
title: "X1300 PCI-E will not install"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Coderedman on 2008-01-25
I have tried everything. I have installed per the binary way at ubuntu wiki. I have try the auto way. I have tried envy. All I get is a blank screen flash after booting then an error. The error logs always mention either screen not found for PCI:2:0:0:1, so I add that to xorg, then it says device not found for PCI:2:0:0:0 even thought that is still in there.

Can anyone help!!!!
64bit gutsy

---

### Post by Yellow Pasque on 2008-01-25
When it freezes, you should press Ctrl+Alt+F1 and login to the terminal, Then:
```
cp /var/log/Xorg.0.log ~/Desktop
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```
Restart. If that doesn't work, boot into a failsafe graphics mode and post the log file that should now be on your desktop.

---

