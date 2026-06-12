---
title: "HELP!  Real Player not installing!"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by gibsongirl on 2007-04-23
I am very new to Linux, I download real player, and it won't install. I get this error.  

*Couldn't display "/home/gibsongirl/Desktop/RealPlayer10GOLD.bin"*. (italics mine.)

I thank you for your help.  :)

---

### Post by RomeReactor on 2007-04-23
Hi. Open a terminal (Applications-->Accessories-->Terminal) and enter

```
cd Desktop
```

then

```
sudo chmod +x RealPlayer10GOLD.bin
```

to make the file executable; and to install it

```
./RealPlayer10GOLD.bin
```

---

### Post by gibsongirl on 2007-04-24
:) Thank you so much for all your help!

---

