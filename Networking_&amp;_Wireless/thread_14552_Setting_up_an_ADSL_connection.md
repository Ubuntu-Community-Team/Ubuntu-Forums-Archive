---
title: "Setting up an ADSL connection"
date: 2005-02-08
forum: Networking &amp; Wireless
---

### Post by MJoshi on 2005-02-08
I connected a USB ADSL MODEM to my computer which is running Ubuntu and it is recognised as a Dynamite MODEM. I just wanted to know what I need to do to create a PPPoA connection in Ubuntu? I think this MODEM might be a generic chipset based ADSL MODEM (Alcatel?).

Do I need to download any drivers?

---

### Post by lameiro on 2005-02-08
Hi!!!!! I have the same problem I have an Alcatel speedtouch 330 Adsl Modem, can anyone help us... I am not very used in linux, I come from mandrake :) -......
see ya

---

### Post by Uuranor on 2005-02-08
For usb adsl modem you must use eciadsl driver :)
I don't remember the command... I think eciadsl-config-tk for the configuration and eciadsl-start for setting up connection.
You must use this command with root access.
If you have the possibility, I suggest you to change the modem with an ethernet ones :P

---

### Post by MJoshi on 2005-02-09
I intend to purchase an ADSL Router in the future but I would like to be able to use the ADSL MODEM with Ubuntu in the meantime.

The configuration procedure must be similar to when creating a PPPoE connection?

---

### Post by Uuranor on 2005-02-09
uhm ... you have a wizard where you set your internet preferences ... such as the username, the password, the internet provider, the modem ... and so on :)

---

### Post by az on 2005-02-09
sudo pppoeconf

---

### Post by MJoshi on 2005-02-10
The wizard is only for a PPPoE connection.  I am assuming that 'sudo pppoeconf' also does the same?

---

### Post by MJoshi on 2005-02-15
Has anyone managed to setup an Alcatel chipset MODEM with a U.K ADSL connection which uses PPPoA?

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=lameiro]Hi!!!!! I have the same problem I have an Alcatel speedtouch 330 Adsl Modem, can anyone help us... I am not very used in linux, I come from mandrake :) -......
see ya[/QUOTE]

See [here](http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo)  for a Ubuntu How-to...

HTH

a.

---

