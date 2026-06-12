---
title: "Remote Desktop"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by cadspark on 2011-05-28
Hi

I have a laptop running Ubuntu 11.04 (wireless) that I want to remote desktop into 2 desktop pc's (one pc is running XP Pro and the other is running Ubuntu 11.04)

All of the above are networked - I can remote desktop into the xp box ... but am unable to remote desktop into the ubuntu box

I have tried just about everything I can find on google - hoping someone will be able to help

Thanks

George

---

### Post by spiky001 on 2011-05-28
On the ubuntu box have you enabled remote desktop System/preferences/remote desktop?

---

### Post by cadspark on 2011-05-28
Hi

yes ... System Preferences -> Remote Desktop 
I have enabled 'Other users to view desktop' and 'Other users to control desktop'

For Security i have enabled 'confirm each access to this machine'

---

### Post by spiky001 on 2011-05-28
Do you have the firewall running on the machine if so turn it off see what happens,

---

### Post by cadspark on 2011-05-28
I haven't enabled any firewall .... I thought ubuntu came with the firewall disabled as default

is there an easy way of checking if it is enabled ?

---

### Post by spiky001 on 2011-05-28
get gufw from synaptic manager. I cant remember if the port is blocked and you have to allow acsess in

---

### Post by cadspark on 2011-05-28
Spiky

thanks for your help .... remote desktop sorted

Hopefully gufw will sort out my Samba issues too ..... if not keep your eye out for the next thread  ;)

---

### Post by spiky001 on 2011-05-28
Just for an update i use Remmina desktop over ssh it is faster as well they are in Package manager as well

---

### Post by cadspark on 2011-05-28
Thanks

I already had Remmina installed but connecting over VNC (which is hopelessly slow) will try it 
over SSH

George

---

