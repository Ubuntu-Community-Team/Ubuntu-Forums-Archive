---
title: "Ubuntu will not detect wireless networks whatsoever"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by fight2survive on 2010-10-02
I just downloaded and installed ubuntu netbook 10.4 on my samsung n130 netbook...love it, except for one little thing: it won't detect any wireless networks. this is how i connect to the internet at home so using an ethernet cable is not an option...
i tried putting in "ifconfig wlan0 up" in the terminal, but all it gives me is "permission denied"..
i looked at previous threads on the subject and couldn't find anything that could solve my situation. Please help me out, i want to make the total switch from windows to ubuntu and i'd really like to be able to fully use it...
thanks a lot

---

### Post by Hakunka-Matata on 2010-10-02
> i tried putting in "ifconfig wlan0 up" in the terminal, but all it gives me is "permission denied"..


start your command line with 'sudo' followed by your command

e.g. 'sudo ifconfig wlan0 up'

---

### Post by shaneg-nz on 2010-10-02
yeah you need "sudo" 
although i would guess it would already be up..

have you tried running this off a live cd first to see if wireless was working?
also ifconfig by itself should show wlan0 and the hardware address.

also quite a few other things that can be tried if these fail..

sudo nano /var/lib/NetworkManager/NetworkManager.state

and check to see if they are all true

---

### Post by Hakunka-Matata on 2010-10-03
[http://art.ubuntuforums.org/showthread.php?t=1383446]("http://art.ubuntuforums.org/showthread.php?t=1383446")

This thread might help, Good Luck.

---

### Post by fight2survive on 2010-10-03
alright, i got it to work by downloading and installing the realtek driver, although it's still not working very well. i cannot load pages on firefox or chromium half the time, same when i try to download updates for ubuntu... and i keep losing connection to my wireless network (have to restart the computer to get it back)...
help? :-/

---

