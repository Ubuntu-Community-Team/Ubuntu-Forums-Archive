---
title: "Troubles with an ADSL connection (pppOe and ethernet)"
date: 2005-01-12
forum: Networking &amp; Wireless
---

### Post by liron on 2005-01-12
Hello

My name is Liron and I have been having some troubles with attempting to get the latest release of the Ubuntu LiveCD connected to the Internet. I'll try to be as descriptive as possible but since I'm fairly unaquinted with the command line and manual configuration there are bound to be some things which I'm going to miss out on - let me know if you need more information from me such as command line output, etc.

I have an Samsung ADSL modem connected to a Realtek ethernet card and use pppOe to connect to the internet. The card is identified properly by Ubuntu and set to eth0.

Running pppoeconf brings up no problems, I answered all of the questions propted and it went through successfuly. After running the configuration and typing "sudo pon dsl-provider" no errors were given.

For some reason, though, I cannot make a visible connection; I can load no websites and pinging returns a "host not found" error. Running ifconfig shows nothing out of the ordinary, listing all of my devices and no errors (eth0, eth1, ppp0e and lo - eth1 is a busted onboard netwoek card and pppoeconf correctly identified eth0 as the interface to connect to pppOe, I doublechecked this in the dsl-provider file in /etc/ppp/peers). Syslog shows no errors.

I have gone over many configuration manuals (for debian) and have searched this forum a dozen times, unfortunately nothing seems to help me find an answer; I have no idea how to even start troubleshooting this.

My main box is running Mandrake10 with no connection problems. I like the Ubuntu desktop and would really like to go for a full installation, but the thought of not being able to connect to the Internet is enough to make me quite hessitant.

I'd appreciate it someone could help point me in the right direction to begin troubleshooting this, I'd love to be able to install Ubuntu!

Thanks in advance, 
Liron

---

### Post by hardcandy on 2005-01-12
Does the modem itself have a setup screen to allow access? Some modems have a setup screen you access via web browser and typing in an address.

---

### Post by liron on 2005-01-12
Not that I know of, I've managed to connect with this setup/modem to various distributions such as Mandrake and SuSE, I don't recall ever needing to set up the modem for access. With the Ubuntu LiveCD, both the "Lan" and "Link" lights are lit, I assume this means that everything is alright hardware-wise.

---

### Post by cpinto on 2005-01-12
[QUOTE=liron]Hello

My name is Liron and I have been having some troubles with attempting to get the latest release of the Ubuntu LiveCD connected to the Internet. I'll try to be as descriptive as possible but since I'm fairly unaquinted with the command line and manual configuration there are bound to be some things which I'm going to miss out on - let me know if you need more information from me such as command line output, etc.

I have an Samsung ADSL modem connected to a Realtek ethernet card and use pppOe to connect to the internet. The card is identified properly by Ubuntu and set to eth0.

Running pppoeconf brings up no problems, I answered all of the questions propted and it went through successfuly. After running the configuration and typing "sudo pon dsl-provider" no errors were given.

For some reason, though, I cannot make a visible connection; I can load no websites and pinging returns a "host not found" error. Running ifconfig shows nothing out of the ordinary, listing all of my devices and no errors (eth0, eth1, ppp0e and lo - eth1 is a busted onboard netwoek card and pppoeconf correctly identified eth0 as the interface to connect to pppOe, I doublechecked this in the dsl-provider file in /etc/ppp/peers). Syslog shows no errors.

I have gone over many configuration manuals (for debian) and have searched this forum a dozen times, unfortunately nothing seems to help me find an answer; I have no idea how to even start troubleshooting this.

My main box is running Mandrake10 with no connection problems. I like the Ubuntu desktop and would really like to go for a full installation, but the thought of not being able to connect to the Internet is enough to make me quite hessitant.

I'd appreciate it someone could help point me in the right direction to begin troubleshooting this, I'd love to be able to install Ubuntu!

Thanks in advance, 
Liron[/QUOTE]
 Have you tried pinging a known IP address? If you can ping it, then you must update /etc/resolv.conf with your ISP's DNS server addresses.

---

### Post by liron on 2005-01-12
I tried updating /etc/resolv.conf with both my ISP's primary and secondary DNS addresses (beforehand I had 10.0.0.2 in there), that didn't make any difference, unfortunately :(

---

### Post by hardcandy on 2005-01-12
Occam's Razor- is the ethernet cable plugged in properly in the correct sockets? Then "sudo adsl-start". 
Next- /etc/ppp/pppoe.conf- does it have the correct device listed, i.e ETH=eth0 and
USER=your login for the ADSL provider (usually your email address)
Any firewall running on your computer? If so, stop it and see if you can connect. You need to have it running once you get a connection. 
Check /etc/ppp/pap-secrets and that it has the correct password for your ISP. Also, check /etc/ppp/chap, make sure it has the "secret" as well. Most DSL ISP's use chap. 
Then try rebooting. (Heck, it works in Windows!  :D )

---

### Post by liron on 2005-01-12
hardcandy - I'm trying this out with the LiveCD, so rebooting isn't going to do me much good ;)
I've already checked all the configuration files in /etc/ppp in order to make sure that they contain the proper information, which they do - this is what is making this so confusing. The login and password are proper, although I have noticed that there is no space for me to actually fill in my provider NAME, is this normal? On Mandrake and Windows I remember needing this in order to establish a connection, and not just the DNS and username/password.

Thanks for all your help, guys! :)
Liron

---

### Post by feralert on 2005-01-28
A friend of mine is having similar problems trying to connect with the LiveCD, he uses PLC to connect to the internet and gets his IP and DNS servers via DHCP.

He run 'pppoeconf' -that i recommend you to try out- and he manages to get an ip but no luck with the dns servers. We've tried to put an ip address on firefox' address bar and it loads the page, but nothing if we try with a web page name.

Anyone knows whats going on? Any clue?

Thanks.

---

