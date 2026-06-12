---
title: "Asus 1000he  + Natty 11.04 Slow wireless"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Lybic on 2011-04-18
Hello, 

I just installed Natty 11.04 on my 1000he, I am currently having an issue with slow wireless speeds. I'm not quite sure what to do, I have searched but there is not much I could find, if anyone can help to point me in the right direction I would appreciate the help.

Thanks

Edit: wired internet speeds are very slow as well, my desktop is on the same network and the interwebs are still fast.

---

### Post by lorado on 2011-04-25
Hey. I have the same prob...
Acer Aspire 5742G with WiFi Card Atheros AR9287.
The auto-connect works good, but the connection is very slow. I have to stay near the router, when i want to get full speed....in my bedroom is download speed max 20kb\s...with Maverick i've had max. 600 kb\s in my bedroom....
i have tried to install the windows driver through ndiswrapper, but it doesn't work

P.s. sry for my english ^^

---

### Post by jon4248 on 2011-04-25
I had this problem as well, I found a workaround via google;

add/create ath9k.conf in  /etc/modprobe.d/

```
sudo gedit /etc/modprobe.d/ath9k.conf
```add:
```

options ath9k nohwcrypt=1

```
save and then reboot, wireless should now be faster..it worked for me.

---

### Post by lorado on 2011-04-25
I found the same, but only for one session (i had to type "sudo modprobe ath9k nohwcrypt=1" after the boot). 

Thank you [B]jon4248.
[/B]It works.

---

### Post by Lybic on 2011-04-25
Thank you Jon, this seems to have fixed my problem.
Seems to have held up past reboot as well, not sure why i had such difficulty finding this. feel kinda noobed now. lol

---

### Post by jon4248 on 2011-04-25
> **Lybic said:**
> Thank you Jon, this seems to have fixed my problem.
Seems to have held up past reboot as well, not sure why i had such difficulty finding this. feel kinda noobed now. lol

ahaha n00b, j/k..lol...it took me a while to find it as well..keep in mind its just a work around, hopefully it will be fixed officially soon...hwcrypt sounds important.

---

