---
title: "Mobile broadband-Pay as you go"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by coolclassic on 2010-06-04
I have purchased a 3 mobile broadband with usb connection.

The usb doggle is recognised by my pc and knetworkmanager. So how do I connect to three and claim my air time? I have a phone number but nothing else. As I understand I need a user name, password and a Pin.

Can anyone enlighten me?

---

### Post by kevinatkins on 2010-06-04
Hi,

I'm also with Three and it works pretty well. I'm not sure about KNetworkManager but I'm pretty sure the settings will be broadly similar to the Gnome Network Manager applet.

You shouldn't need a username, password or PIN, You just need to set up the connection as follows -

Number to dial: *99#

APN: 3internet

And that should be it - billing for useage is tied to the phone number on the SIM card.

---

### Post by John Bean on 2010-06-04
I don't have one to try now but when I used 3 I simply needed to choose the "canned" network settings that Network Manager (GNOME) offered me when the dongle was recognised the first time and it connected. I'm afraid I can't remember the detail but I'm certain that the username/password it used are just fixed placeholders and the PIN isn't needed.


Edit: an answer has been supplied already while I was typing. My refreshed memory confirms the settings are those that I used to use :-)

---

### Post by coolclassic on 2010-06-04
Many thanks now working:):)

Now how do I stop the doggle being recognised as a scsi drive. I have to unmount it first before I can use it as broadband connection.

---

### Post by John Bean on 2010-06-04
> **coolclassic said:**
> Many thanks now working:):)

Now how do I stop the doggle being recognised as a scsi drive. I have to unmount it first before I can use it as broadband connection.

Have a look at the udev-extras package.

---

