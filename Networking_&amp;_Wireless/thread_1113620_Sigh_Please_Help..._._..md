---
title: "*Sigh* Please Help... ._."
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Ryuhei on 2009-04-01
I installed Ubuntu 8.10 on my HP dv5z laptop only yesterday, and I've been having problems getting my internet working... This model uses an Atheros AR242x Wireless card. I looked up various tutorials on getting a driver to get it working but from what I've seen you need an active internet connection through Ethernet to get through the steps shown, which I also can't get to work. Here is the link to one of the tutorials: 

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

I tried skipping the wget step and instead put the driver on a disc which I transferred to my Ubuntu desktop which I downloaded through windows and then just followed the rest of the steps, but when I get to the "cd directoryname" I keep getting an error saying that the directory couldn't be found or something... for directoryname I entered the name of the file/driver/thing that I put on my desktop and I always get the same error when I type it in the the terminal with the cd command. This has been driving me nuts all day trying to get this stuff working. I really love Ubuntu even though I don't even know how to use it yet, but I'm done with windows. So please help! :(

---

### Post by freonchill on 2009-04-01
do you have the .bz2 file on your desktop or you have you already de-compressed it?

either way
from the terminal
(you start in your home)
e.g. lets assume your user is username
so /home/username/

TYPE: cd Desktop

if not decompressed
TYPE: sudo tar -jxvf compat-wireless-2.6.tar.bz2

TYPE: cd compat-wireless-2.6 (or whatever directory was created)

TYPE: make

TYPE: sudo make install

TYPE: sudo make unload 

TYPE: sudo make load

goto network manager (top right of panel)
see if wifi is an option (notice that different pop-ups appear depending on LEFT and RIGHT click on the network manager icon
if not, reboot, then check network manager again

---

### Post by Ryuhei on 2009-04-01
Oh thank you so much!! That was so much simpler than I thought, I just needed to type cd Desktop before I did the other steps, thank you!!! ^_^

---

### Post by freonchill on 2009-04-01
PS: linux is "case sensitive" so just remember

/home/username/Desktop != /home/username/desktop

---

