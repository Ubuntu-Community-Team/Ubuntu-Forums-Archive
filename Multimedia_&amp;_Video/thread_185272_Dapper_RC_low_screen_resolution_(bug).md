---
title: "Dapper RC low screen resolution (bug?)"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by honeydew on 2006-05-31
Im currently installing(as we speak) Dapper RC. I have a nvidia 5600 xt or fx (cant remember off hand).  It loaded up the desktop fine but the default resoultion was 640x480.  Im unable to change this in the resolution area.  This made it slightly difficult to install ( had to use the alt key to drag the window around in order to see the whole picture).  I imagine this could make life hard on someone who is wishing to install but dose not know alot about hotkeys or how to use the system.  Im 88% done.. I look forward to the dapperness my box is about to recieve =]  good work guys.

---

### Post by bruce89 on 2006-05-31
Mine defaulted to 1024x768, instead of 1280x1024.
```
sudo dpkg-reconfigure xserver-xorg
```
should fix it.  Follow the instructions.  Then you press Shift-Backspace to restart X.

---

### Post by honeydew on 2006-05-31
ahh thanks.. works peachy

---

### Post by ejos on 2006-06-01
I get this bug too when installing Ubuntu Dapper. I have a ViewSonic VA702b and I fix it by simply plugging in the HorizSync and VertRefresh values in my xorg.conf file. For me, HorizSync is 30-82, VertRefresh is 50-85. It seems that these values missing is the actual reason for the gross default resolution.

---

### Post by clparker on 2006-06-01
This is a known problem w/ Xorg. Back when ubuntu was using xfree86, this wasn't so much a problem, but many times we have to manually plugin refresh rates. 

Sucks, I know...

---

### Post by boxubi on 2006-06-02
For me changing from the DVI to standard video connection on my video card fixed this problem.

---

