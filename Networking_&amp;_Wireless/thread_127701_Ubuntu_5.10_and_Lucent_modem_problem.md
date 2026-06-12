---
title: "Ubuntu 5.10 and Lucent modem problem"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by KOLE on 2006-02-09
I have Ubuntu 5.10 (kernel 2.6.12.9) and I installed Lucent modem driver with command 
dpkg -i ltmodem-2.6.12-9-386_8.31b1_i386.deb

Installaton was sucesfull, and after that I did all what's written in readme file.

I started System-Administration-Networking, Autodetect modem and it was detected in /dev/modem. I filled username and password and activated connection. Modem dials number and connection sound is the same as in Windows, but when it needs to finish connecting it stops for about 10 seconds and redial. Then it's same. I tried to connect to same provider from Windows and it works normally.

Does anyone know how to fix this?

---

### Post by ddtmsa on 2006-02-09
From what you are describing, it sounds like you have a fully functional modem driver for you modem. 

It sounds like you are having software problems with your ISP; have you set up any proxies properly, is your username and password correct ...

---

### Post by brainkilla on 2006-02-09
Try the command chgrp on /etc/ppp/pap-secrets and /etc/ppp/chap-secrets, I couldn't connect until I have changed group access for these files... If your username is kole, than your default group will be kole too, therefore perform the following magic:

sudo chgrp kole /etc/ppp/pap-secrets (do the same for chap-secrets file). 

And download gnome-ppp from windows and install it - it'll give you much nicer graphical interface to dial-up networking than the default app you're using.

---

### Post by ddtmsa on 2006-02-09
[QUOTE=brainkilla]And download gnome-ppp from windows and install it - it'll give you much nicer graphical interface to dial-up networking than the default app you're using.[/QUOTE]

I don't have a lucent modem but an Intel one. So far, I've only been able to go online with the "default app". I've played with gnome-ppp and the ppp-config options, but I've not been able to persuade either to let me online. 

Going through the system -> administrator -> networking route works every time for me .... don't know why, and until it breaks, don't give a s**t!

---

### Post by KOLE on 2006-02-10
[QUOTE=brainkilla]Try the command chgrp on /etc/ppp/pap-secrets and /etc/ppp/chap-secrets, I couldn't connect until I have changed group access for these files... If your username is kole, than your default group will be kole too, therefore perform the following magic:

sudo chgrp kole /etc/ppp/pap-secrets (do the same for chap-secrets file).[/QUOTE]
Still same :(

---

