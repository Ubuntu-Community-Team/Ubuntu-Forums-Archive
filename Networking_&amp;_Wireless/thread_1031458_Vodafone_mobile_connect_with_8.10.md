---
title: "Vodafone mobile connect with 8.10"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by jaimez30 on 2009-01-05
Hello,

I have been pottering with Ubuntu for a few months so am no expert but would like to ditch windows soon. I have a ongoing niggle with this however. I am not on broadband as I live in an  area of Italy without coverage. My solution is the vodafone mobile connect card. I have had this working with Betavine drivers before but it stopped working when 8.10 came out. 
I would like to get the VMC card working with the native 8.10 network manager and wondered if anyone had managed this?
It is detected and asks for configuration, which I do, but on completion of the setup the connection attempt just says : the card has been disconnected....almost immediately. Any guidance anyone?

---

### Post by LuigiAntoniol on 2009-03-30
There is a new Betavine VMC, but it requires a new app called **usb-modeswitch**.

[COLOR="Red"]The VMC won't even begin to install without this being installed first[/COLOR].

I have just this weekend done what you're asking and below is what I did.

_Procedure_:
Connect PC to a permanent internet connection (ADSL, T1, whatever you have in Italy), or a shared wireless connection at a friends house.
Make sure that your 3G modem is plugged into the PC.
Download and install the USB-modeswitch app from Betavine.
Download and install the VMC from Betavine.
Allow the VMC app to invoke the Synaptic package Manager to resolve dependancies.
[I was sorted out in less than 10 minutes]
Unplug the PC from the permanent connection.
Start the VMC.
Set it up for Italy (it will give you the various networks).
Select the one you want and simply connect.

**_Just a word of warning_**:
Firefox and Evolution Mail do not automatically detect this connection.
In either program, click on "File", then move down to "Work Offline" and uncheck it.

You will have to do this every time you want to go onto the internet or send and receive emails.

Good luck.

---

### Post by jaimez30 on 2009-03-30
Many thanks LuigiAntoniol:-) I will give it a try and hopefully I will be sucessful.

ciao,

james

---

### Post by LuigiAntoniol on 2009-04-02
> **jaimez30 said:**
> Many thanks LuigiAntoniol:-) I will give it a try and hopefully I will be sucessful.

ciao,

james

I did a complete system re-install just to see what the dependencies actually were.

Here's a list of dependencies I had to install:
python-twisted-web
python-twisted-words
python-twisted
python-serial
python-sqlite
python-twisted-runner
python-crypto
python-twisted-conch
python-tz
python-twisted-mail
python-zopeinterface
python-twisted-names
python-pam
python-openssl
python-twisted-news
python-twisted-bin
python-twisted-core
python-twisted-lore
python-pyopenssl
python-gnome2-extras
libgda3-common
libgda3-bin
libgdl-1-common
libgdl-1-0
libgdl-3

Please note that I installed Ubuntu_64 Intrepid Ibex and then the I straight away installed the usb-modeswitch, then the VMC.  Thereafter, I allowed the system to update.

After the first update, I "lost" the VMC and had to un-install it, then re-install it.   Fortunately, all the dependencies were already satisfied and it re-installed without issue.

I used the synaptic package manager to un-install the VMC.

---

