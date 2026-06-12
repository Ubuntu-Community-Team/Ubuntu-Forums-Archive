---
title: "how to disable saving password in networkmanager vpn setup?"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by phatypus on 2011-05-21
Hello.  When I create an VPN (openvpn certificate/TLS) using the networkmanager, it forces me to save the certificate password. I'd really prefer to enter the certificate password manually every time I start the VPN.  Anyone know how to change the behaviour of network manager so that it behaves this way?

Thanks.

(ubuntu 10.10)

---

### Post by kelly11 on 2011-05-24
the dialer you have that contain option to save the pasword check again :confused:

---

### Post by phatypus on 2011-05-24
I figured it out.  Create your openvpn VPN in the networkmanager and enter a password (it doesn't have to be the correct password), and "Apply".

Now go to System > Preferences > Passwords and Encryption Keys.  Select the "Passwords" tab, find and delete the "VPN cert-pass secret" for your openvpn VPN.  From now on you will be prompted for the certificate password when you start that particular VPN.

---

### Post by derekshaw on 2011-08-24
> **phatypus said:**
> ...Now go to System > Preferences > Passwords and Encryption Keys.  Select the "Passwords" tab, find and delete the "VPN cert-pass secret" for your openvpn VPN.  From now on you will be prompted for the certificate password when you start that particular VPN.

Well, this only works 'til the user checks the box "save password in keyring" in the "Authenticate VPN" dialog that comes up.

To actually DISABLE saving the password, one would need a way to prevent the password from getting saved by the user.

This is actually what I need -- to prevent my users from taking the path of least resistance and checking that box, or finding any other way of saving the password in the keyring.

---

### Post by hgefwag on 2011-10-17
This works for me on Ubuntu 11.10:

1. rm ~/.gnome2/keyrings/*
2. Log out and then log in
3. sudo bash
4. cd ~/.gnome2/keyrings
5. chown root *

From now on you will be prompted for the certificate password each time you start vpn connection

---

### Post by derekshaw on 2011-10-18
The big drawback to this kluge is that my users will be unable to save the myriad necessary but unimportant passwords, like the wifi paraphrase for the coffee shop that serves as their road-office.

What we need is the ability to exclude specific passphrases from being stored, and preventing the users from defeating this exclusion, without breaking the ability to store passwords in general.

The user must be required to enter the passphrase (it must be excluded from network manager storing it in the key ring) for the VPN, but not prevented from storing the vast number of low-value paraphrases required for normal daily operations. It must be a root-level privilege to remove the exclusion from the network manager.

---

