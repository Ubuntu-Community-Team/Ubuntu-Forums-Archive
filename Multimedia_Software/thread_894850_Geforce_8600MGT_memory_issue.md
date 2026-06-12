---
title: "Geforce 8600MGT memory issue"
date: 2008-08-19
forum: Multimedia Software
---

### Post by madsleeper on 2008-08-19
Hello!

This is not really a problem I have, but is it a bit strange...
I've got a Dell Inspirion 1720 Laptop with a Geforce 8600M GT graphics card. I'm using ubuntu Hardy 8.04 with kernel 2.6.24-21. Graphics driver is 173.14.12 (currently up to date) installed via envy wiithout any problems. Anything is working fine so far...

BUT: nvidia x server settings and for example doom3 show that there were 512 MB dedicated graphics memory. I am absolutely sure that my card only has 256 MB on it. So I guess that there are used another 256 MB of system RAM... (nvidia driver on parallel installed Windows also says that there are 256 MB dedicated).
So is there any other possibility to check this and eventually turn this supposed additional use of system RAM off? 

As I said, not really a problem, but kind of strange, so it would be nice if anybody had an answer for me :)

Thanks!

---

### Post by madsleeper on 2008-08-20
Absolutely nobody an idea? :(

---

### Post by spoons on 2008-08-20
There should be an option in the BIOS for TurboCache, check that.

---

### Post by madsleeper on 2008-08-20
I already checkd BIOS, nothing to find there. Damn :( I'm using up to date BIOS revision A09, if this should help anyone :)

---

### Post by tuxxy on 2008-08-20
It should tell you in GPU tab in nvidia-settings, search for it in synaptic if you not already installed it, or type in terminal

```
sudo apt-get install nvidia-settings
```

---

### Post by madsleeper on 2008-08-20
Already installed and it tells me 512 MB which is definitivly incorrect (BIOS, Windows driver, my brain and laptop bill tell me :))
And there is no option to change it anyway.

---

