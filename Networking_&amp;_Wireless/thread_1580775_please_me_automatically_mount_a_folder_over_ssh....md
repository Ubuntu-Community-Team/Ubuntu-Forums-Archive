---
title: "please me automatically mount a folder over ssh..."
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by hopelessone on 2010-09-23
Hi,

I'm following: [http://www.hanckmann.net/?q=node/37](http://www.hanckmann.net/?q=node/37)

To automatically mount a folder over ssh..

everything seems ok[I think?!]
It dosent mount on reboot...
if i take 1 line from the file /etc/init.d/sshfs ```
sudo sshfs erg_office_1@10.1.1.2:/home/erg_office_1/MYOB /home/erg_parts_1/MYOB -o allow_other
``` it asks me for passwords and mounts ok..

what things can i do to get this solved?
Thanks..

[edit] actually if i run the script iget this msg:```
erg_parts_1@ubuntu:~$ sudo /etc/init.d/sshfs start
Starting script sshfs (mount)
erg_office_1@10.1.1.2's password: 
read: [COLOR="Red"]Connection reset by peer[/COLOR]
erg_parts_1@ubuntu:~$ 

```

---

### Post by hopelessone on 2010-09-23
redid again..
dunno what i did but workin now...

---

