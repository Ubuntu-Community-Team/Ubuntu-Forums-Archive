---
title: "strange boot"
date: 2011-01-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-01-10
when I boot natty it boots to a black screen with a narrow purple band at the top ( about the size of a panel) , I think this should be the login screen but I'm not sure . The only thing that works is alt>sysreq>b  , no virtual terminals and no alt>sysreq>k . If I boot in recovery mode and choose safe graphics mode and let it boot to low graphics mode and then immediately reboot , it boots to my normal desktop . I am using the Nvidia driver (current) from the repos and classic desktop . It has been doing this for several days and I update everyday hoping something will fix it . I can't see what is going bad in the first boot because I can't get it to give me a text boot . Ideas anyone ?

---

### Post by Harry33 on 2011-01-10
> **ronacc said:**
> when I boot natty it boots to a black screen with a narrow purple band at the top ( about the size of a panel) , I think this should be the login screen but I'm not sure . The only thing that works is alt>sysreq>b  , no virtual terminals and no alt>sysreq>k . If I boot in recovery mode and choose safe graphics mode and let it boot to low graphics mode and then immediately reboot , it boots to my normal desktop . I am using the Nvidia driver (current) from the repos and classic desktop . It has been doing this for several days and I update everyday hoping something will fix it . I can't see what is going bad in the first boot because I can't get it to give me a text boot . Ideas anyone ?

Perhaps something about xserver-xorg-core / xserver-common?

---

### Post by ronacc on 2011-01-10
I think it may be more of a timing issue , when I boot into low graphics it says that my nvidia driver is activated and in use and the next boot goes to my normal highres desktop , its like the driver don't start up in time on a cold boot , since I can't get a terminal with ctrl>alt>Fn or kill the screen with alt>sys>k it seems like the xserver isn't running . I' try reinstalling  xserver-xorg-core / xserver-common and the driver and also blacklisting nouveau  .

---

### Post by oneindelijk on 2011-01-10
Can you post a dmesg ?

---

### Post by ronacc on 2011-01-10
I'm not seeing anything in dmesg or any of my logs that looks like it might have anything to do with this .

---

### Post by oneindelijk on 2011-01-10
And in the system logs ?

---

### Post by ronacc on 2011-01-10
I only found one thing interesting in the logs ```
Jan 10 14:55:33 ron-desktop2 modem-manager: (tty/ttyS9): port's parent platform driver is not whitelisted
Jan 10 14:55:33 ron-desktop2 modem-manager: (tty/ttyS0): could not get port's parent device 
``` I only posted a little bit of the mesg because it goes on for many lines,from ttys0>ttys31 that may explain why no term .
. I changed set gfxpayload to =text in grub.cfg to dump plymouth and that seems to have helped , have rebooted 3 times now without blackscreening .

---

### Post by oneindelijk on 2011-01-10
> **ronacc said:**
> I only found one thing interesting in the logs ```
Jan 10 14:55:33 ron-desktop2 modem-manager: (tty/ttyS9): port's parent platform driver is not whitelisted
Jan 10 14:55:33 ron-desktop2 modem-manager: (tty/ttyS0): could not get port's parent device 
``` I only posted a little bit of the mesg because it goes on for many lines,from ttys0>ttys31 that may explain why no term .
. I changed set gfxpayload to =text in grub.cfg to dump plymouth and that seems to have helped , have rebooted 3 times now without blackscreening .

:-D
Waaw, out of my league, haha
I believe ttyS0 refers to COM1 or something, right ?

I believed I could maybe help out, but it turns out I should find easier problems to solve ;-)
(or acquire more in depth knowledge of linux)

---

### Post by ronacc on 2011-01-10
yes ttys0 and ttys1 uaualy refer to com0 and 1 why it is running through 32 of them I don't know .

---

### Post by cariboo on 2011-01-10
I've seen the same symptom during shutdown, I've always thought it was a problem with plymouth.

---

### Post by ronacc on 2011-01-10
since I haven't got the foggiest Idea whats causing it , I'll accept your guess :D

---

