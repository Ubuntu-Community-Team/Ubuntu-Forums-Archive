---
title: "NetworkManager Applet: what is it?"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by pooja on 2009-06-28
Hi there!

Every time I log into Ubuntu, soon after the booting process ends, a window pops up with the following message:
**Unlock Keyring**
_Enter password for default keyring to unlock_
The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring

I type in the password and it connects me to my home wireless network. However I want Ubuntu to stop asking me the password for the NM applet, I want it to connect automatically to the network, like a sort of default operation. Is it possible to do something like that?

---

### Post by mmriley159 on 2009-06-28
I hope you find out, it is happening to me. It started after I changed my login password. Now I need to sign in twice, once with a new password and then my old password.

---

### Post by Boondoklife on 2009-06-28
When you start the computer do you login or do you have it set to auto login? If the later then to get it to stop asking you, go into the networkmanager aplet and mark the wifi connection as usable by anyone. this will stop that prompt

---

### Post by pooja on 2009-06-29
[QUOTE=maletek]When you start the computer do you login or do you have it set to auto login? [/QUOTE] I have it set to auto login

[QUOTE=maletek]go into the networkmanager aplet and mark the wifi connection as usable by anyone[/QUOTE] How? System > ...?

---

### Post by b@sh_n3rd on 2009-06-29
> **pooja said:**
> I have it set to auto login

 How? System > ...?

Hi there, yes, you can go through "System > Preferences > Network Connections". Then, under the "Wireless" tab, select your connection in the list, click edit, enter your password when asked and you will see a new dialog box. In that, at the bottom check "Available to all users". I think this is enabled by default though...hope this helps...

---

### Post by frankwakeman on 2009-06-29
That's great, this worked for my Mobile Broadband dongle too, and I've been having to log in manually since I started using Linux in December.  I'd tried to the automatic login feature before, but I just didn't think to tick that 'useable by anyone' box as it didn't sound to me like it would have anything to do with the issue.

I'd also made enquiries here and on the Linux Mint forum with no solution at all, yet it's been this simple.

Thanks.

---

### Post by pooja on 2009-06-29
> **b@sh_n3rd said:**
> ... yes, you can go through "System > Preferences > Network Connections". Then, under the "Wireless" tab, select your connection in the list, click edit, enter your password when asked and you will see a new dialog box. In that, at the bottom check "Available to all users". I think this is enabled by default though...hope this helps...

Thanks a lot!

---

### Post by mmriley159 on 2009-06-29
It worked for me also. Thanks a lot.

---

### Post by Boondoklife on 2009-06-29
> **b@sh_n3rd said:**
> Hi there, yes, you can go through "System > Preferences > Network Connections". Then, under the "Wireless" tab, select your connection in the list, click edit, enter your password when asked and you will see a new dialog box. In that, at the bottom check "Available to all users". I think this is enabled by default though...hope this helps...

I know it is not enabled by default on password protected Networks, maybe for wideopen networks it is?

---

