---
title: "Ubuntu server samba set the password for XP logon"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by gogogadget on 2009-05-17
Hi

I have just started to network mt windows XP laptop (Ugh) and my ubuntu desktop machine. I have a device connected to my desktop that windows will need access to. I am using Samba, the ubuntu is set up as server and the XP is the client. I can see the server and when I want to explore the upuntu machine a logon window appears. I tried logging in but after entering my ubuntu username and password nothing happens. I get no error message, simply the logon screen returns.
Do I have to setup a password on the ubuntu machine or different username or is it something else?

I look forwards to a simply reply

thanks Andrew

---

### Post by swerdna on 2009-05-17
> **gogogadget said:**
> ..........Do I have to setup a password on the ubuntu machine or different username or is it something else?...........
You must add a Linux user to the Samba User Database on the Ubuntu machine. Then whenm asked for credentials while browsing from windows, supply the creds you just added to the Samba user database.

Open a console window and enter this command: ```
sudo smbpasswd -a name
```
where "name" is the username of an existing Linux user. Then answer the password questions. 

Luck

---

### Post by gogogadget on 2009-05-17
Thanks for your prompt reply

it worked perfectly

thanks again Andrew

---

