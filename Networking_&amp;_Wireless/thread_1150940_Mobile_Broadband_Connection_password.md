---
title: "Mobile Broadband Connection password"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by agharbeia on 2009-05-06
Using Jaunty I managed to plug in my Vodafone Mobile Connect Huwawe K3520 USB device to be greeted with the wizard through which I chose Egypt as my country and Click Vodafone as my provider and establish a connection to the Internet (which I'm using now)

However, when the computer is restarted, either with the device plugged in or having been removed and replugged it, then I'm prompted to enter my Master Keyring password, and with this entered successfully, followed by a prompt for the GSM connection password.

Entering the password which was automatically populated by the wizard in the previous round doesn't work. You could see the password through the connection properties in Network Manager. (note: the password and the username are both "internet", for Vodafone Egypt)

Only Deleting the connection from Network Manager, replugging the device and having the wizard do its job again am I able to connect. Doing this every time isn't something I'd like to leave my friend live with.

Any suggestions?

---

### Post by GeorgeVita on 2009-05-20
Hi **agharbeia**

please try the following:

delete every connection, restart, plug in the modem, add the new connection and when asked for "Master Keyring password" leave the fields blank and continue. The system will prompt you to "Use unsafe area for Passwords". Accept it too. If any other password asked just continuew without entering something. Say "Allow always" to the possible question about using the Network Manager the keyring!

Regards,
George

---

### Post by agharbeia on 2009-05-20
Thank you, George
I had contacted my friend to see if the issue persists, and he said it was solved on its own. I don't know if he did what you recommended, though.

---

