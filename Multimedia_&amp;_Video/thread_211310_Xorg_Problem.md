---
title: "Xorg Problem"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by RavenNight on 2006-07-08
I wanted to try out planet-penguinracer and discovered that it ran at a snails pace, it was actually hard to navigate the menus. After trying several other 3D games I decided to get some drivers for my GFX card. My Compaq Evo N400C has, according to lspci, an ATI Rage Mobility P/M AGP 2x. So off I went to follow several guides on how to install the fglrx drivers. Checked all the recommended settings and on reboot it failed spectacularly, now it fails to boot x, so I'm left with command line, the error says that device couldn't be found. CAn someone tell me how to reset the xorg.conf to its orginal? Is my card even supported? If not where can I get drivers? Thanks!

---

### Post by tseliot on 2006-07-08
Here's the guide:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

try with 
```
sudo dpkg-reconfigure xserver-xorg

```
and select the "ati" driver. Press ENTER whenever you don't know the answer to the other questions.

Then:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by RavenNight on 2006-07-08
You are an utter god, thanks very much! It boots great! Must have muffed up one of the options by accident, I'll go stand quietly in the corner now, thanks!!!

---

