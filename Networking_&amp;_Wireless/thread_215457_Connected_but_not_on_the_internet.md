---
title: "Connected but not on the internet?"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by GuitarHero on 2006-07-14
I installed the windows drivers for my linksys WMP54G v4.1 using ndiswrapper and he gui frontend.  It says the hardware is detected and with iwconfig, it tells me i have a 42/70, frequency, and essid are found etc.  It appears it is connecting to the network but firefox will not go online nor will any internet program.  The card uses the rt61 drivers.  It seems im so close but i dont understand why its not working.

---

### Post by MrHorus on 2006-07-14
what is the output of 'ifconfig' and 'iwconfig'?

---

### Post by GuitarHero on 2006-07-14
I cant get on the internet with it to post it, im on a different computer.  iwoconfig shows a signal quality and the correct essid and frequency.  ill post ifconfig when i get home later.

---

### Post by gratefultux on 2006-07-14
Check to make sure that your gateway and nameserver are correct.  That's what did it for me.

---

### Post by GuitarHero on 2006-07-14
i've been using dhcp, i dont have to set it do i?

---

### Post by GuitarHero on 2006-07-15
i tried setting it again and it still didnt work

---

### Post by MrHorus on 2006-07-15
What is the output of 'iwconfig' and 'ifconfig'?

---

### Post by bigken on 2006-07-15
take a look at reply 3 this could be your problem [http://www.ubuntuforums.org/showthread.php?t=215461](http://www.ubuntuforums.org/showthread.php?t=215461) ;)

---

### Post by GuitarHero on 2006-07-15
its not just firefox

---

### Post by GuitarHero on 2006-07-16
bump

---

### Post by bigken on 2006-07-16
sorry I cant help you anymore but you could also take a look at the this

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

