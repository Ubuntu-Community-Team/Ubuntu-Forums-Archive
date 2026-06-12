---
title: "Dual DVI with 7600GT"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by hppyfngy on 2007-02-20
I need to enable both my dvi outputs on my 7600GT.  Only have one working now (and it's being converted to analog.)  


Dunno how...:confused:

---

### Post by hppyfngy on 2007-02-23
bump?

C'mon, Nobody???

---

### Post by tseliot on 2007-02-23
Let's try to get your 1st monitor to work via DVI.

Install the Nvidia driver and try this command:
```
sudo nvidia-xconfig --use-display-device=DFP
```
then turn off your computer, remove the DVI to VGA adapter and plug the DVI cable without the adapter.

Then turn on your computer.

If the monitor works fine, plug in the 2nd monitor and type:
```
sudo nvidia-settings
```

and enable the 2nd monitor using twin view

---

### Post by hppyfngy on 2007-02-24
Worked fine.  You're the man Alberto.  

Thanks for Envy too.

---

