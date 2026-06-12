---
title: "PPPOE setup"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by raja34766 on 2012-06-08
I want to configure pppoe on ubuntu 11.10. I used that sudo pppoeconf command. I know that "start when boot" option doesnt work. But when I configure pppoe setup with userid and password it works. And when I turn off the computer and then turn on and type the command "pon dsl-provider" to turn on the connection it fails. I think it deletes everything I configured when I turn off my machine. I have to configure pppoe everytime I turn on my computer. How can I fix this problem permanently so that I can use pppoe connection like I use on windows xp.
I don;t want to connect pppoe when I turn on my PC.

Thank you in advance...

---

### Post by steeldriver on 2012-06-08
it's a while since I've used PPPoE but have you tried setting it up via the Network Manager applet (Edit Connections -> DSL -> Add) and leaving the 'Connect automatically' box unchecked?

---

### Post by raja34766 on 2012-06-09
It didn't work

---

### Post by raja34766 on 2012-06-10
Please someone help me with this. Everytime I turn on my computer I have to configure my PPPOE connection...

---

### Post by amusis on 2012-06-10
have you see the files network/interfaces ? to create a pppoe connection with wifi i have change it. Maybe when you reboot, the pc delete what pppoeconf has created in this file.
or something in your modem.
or in the linux installation.

---

### Post by raja34766 on 2012-06-11
[LEFT]I am not using a Wi-fi connection. I am using a PPPOE connection. What should I do? 
[/LEFT]

---

### Post by spandey on 2012-06-11
Are you using your modem in Bridge mode or PPPoE mode?

---

### Post by raja34766 on 2012-06-11
PPPOE mode...

---

### Post by amusis on 2012-06-11
> **raja34766 said:**
> [LEFT]I am not using a Wi-fi connection. I am using a PPPOE connection. What should I do? 
[/LEFT]

  i use my wifi problem like example. i have used pppoeconf on wlan but it didn't work because it didn't write the information in the /etc/network/interfaces. maybe you have the same problem.your pppoeconf write information in a tmp(but why?) file and when you reboot it is gone. try to look in this file, before and after you use pppoeconf. 
it must look like this:
```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```i'm not a professional user, so maybe i'm saying b***** , but it can be a start.
[http://qref.sourceforge.net/Debian/reference/ch-gateway.en.html](http://qref.sourceforge.net/Debian/reference/ch-gateway.en.html)
you can see here too.

---

### Post by raja34766 on 2012-06-12
Yea thats right I tried to edit that file from terminal but when I try to do that it says you don't have permission to edit this file. i also think that it saves my configurations in a tmp file which it removes after i turn off my PC. 
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
i found the solution on this site but it didn't work as I couldn't save the file....

---

### Post by amusis on 2012-06-12
to edit a file in /etc folder(and other) you must be root
so
```
sudo gedit /etc/network/interfaces
```or what you use to edit text files, and when it ask you insert the password.

---

### Post by jmore9 on 2012-06-12
did you try " sudo gedit /blah/blah/blah/file "

---

### Post by spandey on 2012-06-13
If you have your Modem in PPPoE mode then your modem has all the details to logon to DSL network. You just need to connect to Modem using Ethernet(wired) to Wireless. 

If that's true then remove all pppoeconf details:
```

sudo rm /etc/ppp/peers/dsl-provider
```

Then open  interfaces 
```

sudo gedit /etc/network/interfaces

```

make sure the line iface has dhcp not manual

```

iface eth0 inet dhcp
```

Now you will get internet by default in next boot..

---

### Post by raja34766 on 2012-06-19
When I start my computer while booting it says "Configuring networking connection" then it says "Waiting up to 60 seconds more for network configuration" after that ubuntu starts but without any network configurations. Everytime I have to setup my PPPOE connection by the command PPPOE

---

