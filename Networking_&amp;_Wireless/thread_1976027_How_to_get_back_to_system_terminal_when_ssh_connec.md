---
title: "How to get back to system terminal when ssh connection is not used after a long time?"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by AnuragSatish on 2012-05-08
[FONT="Comic Sans MS"][I]Hi,

Can anyone tell me on how to get back to the system's terminal mode when we ssh to remote host terminal and have not used it for a long time. The system hang's in the terminal and doesn't come out, so then I close the terminal and open a new one.

Instead of doing this, is there a way to get back to the original terminal of our system.

Regards,
Anurag
[/I][/FONT]

---

### Post by SlugSlug on 2012-05-08
You might be better off using screen

screen /usr/bin/task


and then later recall it via

screen -r

---

### Post by alperyilmaz on 2012-05-08
I second SlugSlug's suggestion. screen is much better and elegant solution.

if you are not insterested in using screen, then you can add the following line to your /etc/sshd_config

TCPKeepAlive yes

---

### Post by AnuragSatish on 2012-05-08
TCPKeepAlive yes

worked!!

Can u guys tell me on how to xecute that screen command---

screen /usr/bin/task

task means my ssh connection to the host?

Regards,
Anurag

---

### Post by SlugSlug on 2012-05-08
ssh into server


then use screen to exec commands you would be using eg

screen tailf /var/log/auth.log


you can then close ssh session and return later by 

ssh server

screen -r

---

