---
title: "Cant get wired connection to work on my hp laptop with ubuntu."
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by nehrbas09 on 2011-09-22
When I plug a cable into my laptop it says that I am connected but I'm at school and theyre internet requires a log in. I used sudo pppoeconf in the terminal and it says:
sorry, i scanned 2 interfaces, but Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

I got ubuntu because my computer crashed and i had win7 installed but then i lost the key so i had a generic vista which i couldnt activate so I had to install ubuntu and I really enjoy the setup its just hard to take full advantage without having internet. Any help would be great. 
thanks.

---

### Post by praseodym on 2011-09-22
Try:

```
sudo adduser $USER dip
```
Deactivate the Network-Manager in Autostart and login again. After that

```
sudo pppoeconf
```

again.

---

### Post by nehrbas09 on 2011-10-03
How do I Deactivate the Network-Manager in Autostart and login again? Im not entirely sure what that means or entails.

---

### Post by praseodym on 2011-10-03
Take out the checkbox in the menu and logout.

For testing after login:

```
sudo service network-mnager stop
sudo pppoeconf
```

From the terminal:

```
gnome-session-properties
```

---

### Post by nehrbas09 on 2011-10-04
I am still getting the same answer. what do you mean by logout and login

---

### Post by praseodym on 2011-10-04
> **praseodym said:**
> Take out the checkbox in the menu and logout.

For testing after login:

```
sudo service network-m[COLOR="Red"]a[/COLOR]nager stop
sudo pppoeconf
```

From the terminal:

```
gnome-session-properties
```
Sorry typo (correction in red)

---

