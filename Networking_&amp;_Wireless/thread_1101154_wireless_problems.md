---
title: "wireless problems"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by urd on 2009-03-20
hi, i have a problem whit my wireless connection, i recently installed ubuntu on my laptop, and the wireless connection range was to low, i try to solve it installing wicd, but now i can't connect to mi network who is password protected and wep encription

i have a realtek rtl8781b card 

what can i do??

thanks

---

### Post by wildgeo on 2009-03-20
Have you tried to set up the IP configuration? I'm not that so expose to Linux but we used have an experiment on networking a Linux computer. The we do is we configure the IP of each computer. I forgot what are the steps that we done on the lab sorry. I wish that would helped.

---

### Post by MaindotC on 2009-03-20
What happens when you try to connect to your network? Does it prompt you for the password?

---

### Post by urd on 2009-03-20
> **strAlan said:**
> What happens when you try to connect to your network? Does it prompt you for the password?
i have wired connectiom, but wirelles i alredy setup my password, but when i try to start wireless, the message show that the computer autenticate the password, but never connect to the network

---

### Post by MaindotC on 2009-03-20
Are you certain that your wireless card supports WPA, WPA2, or WEP?  Can you check the ubuntu hardware compatibility list for your wireless card?

---

### Post by urd on 2009-03-20
> **strAlan said:**
> Are you certain that your wireless card supports WPA, WPA2, or WEP?  Can you check the ubuntu hardware compatibility list for your wireless card?

the card works perfect in windows, the problem is with linux!! :S

---

### Post by MaindotC on 2009-03-21
Your card may or may not support those standards based on the driver compatibility. Can you please do as I asked and check the [Ubuntu Hardware Compatibility List](https://wiki.ubuntu.com/HardwareSupport/)?  I believe all Realtek cards are fully supported in kernel 2.6 and above, but I had one that wouldn't work in 2.6.24-22-generic so I had to upgrade to 8.10 that uses a higher kernel.

When you enter the password, can you ensure you're not including a space?  Click the box that shows the password in plain text.

---

### Post by urd on 2009-03-21
> **strAlan said:**
> Your card may or may not support those standards based on the driver compatibility. Can you please do as I asked and check the [Ubuntu Hardware Compatibility List](https://wiki.ubuntu.com/HardwareSupport/)?  I believe all Realtek cards are fully supported in kernel 2.6 and above, but I had one that wouldn't work in 2.6.24-22-generic so I had to upgrade to 8.10 that uses a higher kernel.

When you enter the password, can you ensure you're not including a space?  Click the box that shows the password in plain text.

yes is compatible, is a toshiba satellite a2 series, and i try to check the password, even try to put the password between "" ...so i doesn't now what to do :S ... i'm to new with ubuntu :(

---

### Post by MaindotC on 2009-03-21
Can you remove the network encryption and try connecting just to make sure that works?

---

