---
title: "No network connection"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by jonjmill on 2010-01-31
I am new to Ubuntu, and I have just installed version 9.10 on my desktop PC. I need help walking through the steps to connect to my computer to my home network. Right now, I have no connection and cannot detect any of the hardware when running Ubuntu. When I switch over to my Windows XP partition, everything works fine. Please help!

---

### Post by mongr31 on 2010-01-31
what happens when you run this command from the terminal?

```

ifconfig eth0

```

---

### Post by jonjmill on 2010-01-31
I forgot to specify that I am trying to connect through the wireless card in my computer.

---

### Post by dinutu on 2010-01-31
> **jonjmill said:**
> I forgot to specify that I am trying to connect through the wireless card in my computer.

well them most probably you do not have wireless card driver installed, what computer do you have?

---

### Post by mongr31 on 2010-01-31
What type of wireless card is it? Is it built-in or is it usb?

---

### Post by jonjmill on 2010-01-31
No brand name...built it myself.

---

### Post by jonjmill on 2010-01-31
It's built in.  Buffalo WLI2-PCI-G54S

---

### Post by mongr31 on 2010-01-31
Looks like you're going to need ndiswrapper: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by jonjmill on 2010-01-31
I went through all the steps for ndiswrapper. Now the connection is trying to be established however, I am continuously prompted for the password to access the connection.  I know the password is correct, I enter it, it tries to connect for a while, then I am prompted to enter the password again.

---

