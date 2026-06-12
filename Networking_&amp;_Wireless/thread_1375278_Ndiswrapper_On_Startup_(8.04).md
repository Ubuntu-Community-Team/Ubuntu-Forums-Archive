---
title: "Ndiswrapper On Startup (8.04)"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Burky on 2010-01-07
I'm currently using Ndiswrapper for my wireless usb card that uses the RTL8187B Chipset on Ubuntu 8.04. To get myself to connect I have to run "sudo modprobe ndiswrapper" everytime. Is there a way I can connect automatically?

---

### Post by Twitch6000 on 2010-01-07
> **Burky said:**
> I'm currently using Ndiswrapper for my wireless usb card that uses the RTL8187B Chipset on Ubuntu 8.04. To get myself to connect I have to run "sudo modprobe ndiswrapper" everytime. Is there a way I can connect automatically?

I forget where,but there is a config file you can edit and put that command in.

---

### Post by Burky on 2010-01-07
Do you know where I can find this?

---

### Post by bkratz on 2010-01-07
> **Burky said:**
> Do you know where I can find this?





I believe it would be

sudo gedit /etc/modules

put there, but I am no expert by any means!

---

### Post by Burky on 2010-01-07
> **bkratz said:**
> I believe it would be

sudo gedit /etc/modules

put there, but I am no expert by any means!

I attempted to put "sudo modprobe ndiswrapper" there, but it didnt work. Thanks though. Any other others thoughts?

---

### Post by Burky on 2010-01-08
I got this to work by simply putting "ndiswrapper" at the end of /etc/modules.

---

### Post by bkratz on 2010-01-08
Glad to hear it, I was going to write you back suggesting this after further reading in the threads, but you figured it out, feels better that way.

---

### Post by Burky on 2010-01-08
My problem was that I was putting "modprobe ndiswrapper" instead of just "ndiswrapper".

---

### Post by bkratz on 2010-01-08
> **Burky said:**
> My problem was that I was putting "modprobe ndiswrapper" instead of just "ndiswrapper".

That is what I thought after further reading. Thanks for the confirmation

---

### Post by Burky on 2010-01-08
No problem. Thanks for telling me where to put it.

---

