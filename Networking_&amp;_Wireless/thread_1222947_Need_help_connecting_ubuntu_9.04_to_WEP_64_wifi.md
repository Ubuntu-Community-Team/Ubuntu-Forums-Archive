---
title: "Need help connecting ubuntu 9.04 to WEP 64 wifi"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by webster922 on 2009-07-25
Hello, yesterday I installed ubuntu 9.04 to my ps3 using the specific ps3 ppc install. Now I need help connecting to my wifi. My wifi is WEP encrypted 64 bits, 10 hex digits. Ubuntu can find the wifi but never connects. It asks for my password, and after typing the password in, the same message comes back up saying that I need the password for access. I have triple checked to make sure everything is correct, along with different combinations of the ssid, essid, mac address, shared key, etc, but it still doesn't work. Any help is appreciated.

---

### Post by MentatGhola on 2009-08-07
I have a similer problem.  I don't even see a 64 bit passphrase WEP option.  when I use the default 40/128 passphrase wep option I cannot connect.

---

### Post by izizzle on 2009-08-07
Try installing WICD and connecting from it. It is in the repos.

---

### Post by webster922 on 2009-08-22
Well I found the problem. When ubuntu starts up, the wifi is not running for some reason even though your green wifi light is probably on. The way to get wifi running is by disconnecting from wifi, waiting for the disconnected message to appear, then turning wifi back on. The wifi indicator should turn from solid green (after startup when it is not working) to off to blinking green when it is working. This is inconvient to do everytime I use ubuntu, but hopefully there will be a fix in 9.10. And even though there is no option for 64 bit wep, I can confirm that this works. Hope this helps everyone having trouble.

---

