---
title: "wlan needs password everytime"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by falkenberg_cph on 2006-06-12
Hi
Every time i reboot my laptop the wlan needs the password for wpa-psk. Its a pretty long code, and its really anoying. Cant i get rid of this feature.

---

### Post by popkid on 2006-06-12
[QUOTE=falkenberg_cph]Hi
Every time i reboot my laptop the wlan needs the password for wpa-psk. Its a pretty long code, and its really anoying. Cant i get rid of this feature.[/QUOTE]

Are you using network manager? If so, are you sure it's not the default keyring password it is asking for? This doesn't have to be the same as your wpa-psk password, you can make it anything you like.

pK

---

### Post by falkenberg_cph on 2006-06-12
Thanks for the reply. It is the keyring i meant. Unfortunatly i tried fixing the problem with keyring manager. Now i have deleted the keyring, and wlan doesnt ask for it anymore, but is unable to logon.

This is so confusing. how do i recreate a keyring. I tried making one in keyring manager, but it dosnt seem to have any effect on anything.

How do i get rid of it again, once i have recreated it. :x 

I hope you can help me, this stinks.
Carsten

---

### Post by popkid on 2006-06-12
[QUOTE=falkenberg_cph]Thanks for the reply. It is the keyring i meant. Unfortunatly i tried fixing the problem with keyring manager. Now i have deleted the keyring, and wlan doesnt ask for it anymore, but is unable to logon.

This is so confusing. how do i recreate a keyring. I tried making one in keyring manager, but it dosnt seem to have any effect on anything.

How do i get rid of it again, once i have recreated it. :x 

I hope you can help me, this stinks.
Carsten[/QUOTE]

if you just deleted the keyring in /tmp/

then if you go through the process of re-connecting to the network again, i.e. pick the "connect to other wireless network" option and re-enter your details it should ask for a keyring password again when you put in the wpa-psk pass key...

pK

---

### Post by falkenberg_cph on 2006-06-12
hmmm. it doesnt. If i try to connect to my router, it asks for the password, but not the keyring. It just "searches" for the net for some time, then returns to the password verification.

I guess i must have deleted more than just the temp file.

Carsten

EDIT: i have just been looking on some other threads about "reset keyring". One advice was to ctrl-H in home folder to show hidden files, and find a special file there (cant remember the name exactly). My home folder contains no hidden files.

---

### Post by falkenberg_cph on 2006-06-13
it must be possible somehow to completely reset keyring

---

### Post by jmodigb on 2008-07-07
Running ear os, my password was not accepted at all.  So, I went into Applications..Accessories..Passwords and Encryption Keys and deleted the login keyring.  Then created a new one named default.  Connecting to my wireless access point no longer requires a password for nm-applet.

---

