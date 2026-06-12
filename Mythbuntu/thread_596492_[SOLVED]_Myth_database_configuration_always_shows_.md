---
title: "[SOLVED] Myth database configuration always shows up"
date: 2007-10-29
forum: Mythbuntu
---

### Post by barcesat on 2007-10-29
Hi,

i installed mythbuntu ok and the frontend strted and i began configure it without any problems until i pressed something (probably) and now i can't open myth backend setup or the frontend without seeing the screen to configure the database.

I can't get past it!

what have i might done? and what should i do?

thanks in advance,

ziv

p.s
i've started to translate mythbuntu to hebrew - cause it's really really good :)

---

### Post by faffaz on 2007-10-29
Check if the mythtv password for mysql is the same, if not this can i happen. In that case you will need to reset myql root password!

---

### Post by drarmi on 2007-10-29
strange ... I got the same problem. It happened just now. I have been running mythbuntu without any problems since it was release. I did nothing it just stopped working. The box forze up and when i rebooted it I got this problem.

---

### Post by drarmi on 2007-10-29
> **drarmi said:**
> strange ... I got the same problem. It happened just now. I have been running mythbuntu without any problems since it was release. I did nothing it just stopped working. The box forze up and when i rebooted it I got this problem.

I played around for a bit ... 
the error I got was "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"

At the end I tried to free space on the harddrive ... and now it works

---

### Post by barcesat on 2007-11-02
I solved it thanks to you guys!

i installed phpmyadmin and logged on into it using the root username and my password (which i defined earlier).
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
then i went to Privileges and chose to edit mythbuntu username.
i resetted its password through a form there and saved.

It worked :)

---

### Post by laga on 2007-11-03
> **barcesat said:**
> 
then i went to Privileges and chose to edit mythbuntu username.
i resetted its password through a form there and saved.


I'd recommend that you tell the rest of the system that password, too. Run *sudo dpkg-reconfigure mythtv-common* and enter it there.

---

### Post by amr2205 on 2007-11-04
> **barcesat said:**
> I solved it thanks to you guys!

i installed phpmyadmin and logged on into it using the root username and my password (which i defined earlier).
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
then i went to Privileges and chose to edit mythbuntu username.
i resetted its password through a form there and saved.

It worked :)

Thanks, it works for me too!  \\:D/

---

