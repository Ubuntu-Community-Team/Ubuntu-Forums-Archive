---
title: "Wireless asks for keyring password every boot."
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Azmaedra on 2009-05-31
When I log into Ubuntu (9.04) the wireless connection asks for permission to access the default keyring, which it says is locked. Every time I log in, the message is displayed, and if I ignore it, there's no internet connection. I guess what I'm asking for here is help on how to make the keyring be accessed automatically. (without asking for the password every time I start Ubuntu)

---

### Post by urbietorbi on 2009-06-02
this worked for me:

Get "Network Connections" from 
1) System>Preferences>Network Connections
or
2) Right Click on the "Blue Bars" Wireless Signal Icon, top Bar next to Sound Icon.

Next, in the Network Connections 'Window' click on the "Wireless" Tab, then Select your Connections and Click on the "Edit" Button.
Finally, at the bottom of the "Editing Wireless Connection", Check the "Available to all users" Box and Choose "Apply".

got it from here:

[http://ubuntuforums.org/showthread.php?t=1129346](http://ubuntuforums.org/showthread.php?t=1129346)

---

### Post by Azmaedra on 2009-06-02
That worked, thanks. :)

---

### Post by uupreti on 2009-06-02
Wow that helped me too. Thanks for raising question and quick answer.

---

### Post by ulli.winter on 2009-06-24
great!
I've been searching for a solution to this for quite a long time.... :)

---

### Post by ddrichardson on 2009-06-24
Hi all, I write the system documentation for Internet & Networking and have been considering adding this information - can anyone confirm that this works with automatic login?

---

### Post by fishtek on 2009-07-29
Thanks and yup it does work for auto login, just enabled it!

---

### Post by ddrichardson on 2009-07-30
Thanks, it appears automatic login is to be removed in Karmic though.

---

