---
title: "SSH Issues"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by philipballew on 2011-11-16
I want to ssh into a desktop remotely but the network the desktop is hooked up to wont allow for any ports to be opened? will it be completely impossible to be able to ssh into the desktop then? Or does anyone know or a non-standard work around to set up.

---

### Post by kingoddball on 2011-11-16
Is your router/modem blocking incoming connections?

Google up your router brand and see if there is a PDF manual to unblock incoming on port 22.

Also, are you trying to log in remotely (outside network)?

You need to: (if you don't know :) )

Know your IP and if it is a Statis IP ([www.whatsmyip.org](www.whatsmyip.org))
Set your router to port forward port 22 (or the port you want) to Ubuntu.
Have your server/ubuntu as a Static IP (ie: 192.168.1.800).

Then:

ssh [email]root@xx.xxx.xxx.xx[/email] (your networks IP [not internal/192.168.x]).

---

### Post by David006 on 2011-11-16
If the target site (remote desktop) has a firewall, router (with inbuilt firewall), or software firewall (on the PC) - then by default outbound connections (from that PC) will be allowed, BUT any inbound connections (to that PC) will be BLOCKED.

Any workaround that can defeat this is high-end hacking, and quite illegal.


What are you asking?

Do you need to know how to allow a port to be available to allow remote access?

Is there (perhaps) no firewall or router, as by default (out of the box) Linux will not allow inbound SSH connections?

---

### Post by Dangertux on 2011-11-16
> **philipballew said:**
> I want to ssh into a desktop remotely but the network the desktop is hooked up to wont allow for any ports to be opened? will it be completely impossible to be able to ssh into the desktop then? Or does anyone know or a non-standard work around to set up.


Yes there is a way -- however if you are not the owner of the network, and the network administration is not allowing remote connections to SSH we really can't support subverting that security measure. I suggest researching reverse ssh connections, client to client ssh connections with a middle man and nohup.

---

### Post by CharlesA on 2011-11-16
> **Dangertux said:**
> Yes there is a way -- however if you are not the owner of the network, and the network administration is not allowing remote connections to SSH we really can't support subverting that security measure. I suggest researching reverse ssh connections, client to client ssh connections with a middle man and nohup.
What DT said.

Are your the owner of the network?

You will not get any support for trying to bypass network security here.

---

### Post by philipballew on 2011-11-17
no, not trying to bypass anything like that. Just seeing if there is an easy way to get ssh running if I can not have any ports opened. It is at the college i go to. I assume it is impossible?

---

### Post by CharlesA on 2011-11-17
> **philipballew said:**
> no, not trying to bypass anything like that. Just seeing if there is an easy way to get ssh running if I can not have any ports opened. It is at the college i go to. I assume it is impossible?
Highly unlikely you'd get it working if they have it locked down.

---

