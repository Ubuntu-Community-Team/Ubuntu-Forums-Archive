---
title: "Samba and encrypted home dir"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by potam on 2009-11-01
Hello all,

I have noticed, that if I create an usershare within my encrypted home directory, any clients on the network can't connect to it. I have permission errors in the log. When I create it outside the encrypted home, it works. Is there any other workaround?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
have you encrypted the folder cos i think you can do it through smb.conf

---

### Post by potam on 2009-11-01
> **headvampyre@hotmail.co.uk said:**
> have you encrypted the folder cos i think you can do it through smb.conf

I checked require my password to log in and decrypt my folder setting during the install. I attached my current smb.conf file.

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
i think i found problem im gonna modify smb.conf

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
what os's do you use and waht type of server are you trying to setup ?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
try this i have added a share for the homes and done a few mods to it this should work  also if u want ill copy mine so u can test that

---

### Post by potam on 2009-11-01
Same permission error.

BTW, I have Ubuntu 9.10, 64 bit desktop, samba is 2:3.4.0-3ubuntu5

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
ah there has been loads of probs with samba and karmic so youll probly have to wait it out id also try a later version i think 2.4.3 is out and have you got a running firewall cos i had probs with that b4 so i disabled it

---

### Post by potam on 2009-11-01
I also noticed that connecting with anonymous user can't access the share located in the encrypted home, but with my account I can.

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
try settin up a share just for the anonymous user also these could be useful

in a terminal type
sudo apt-get install webmin swat

they should install if not just google them

---

### Post by potam on 2009-11-01
I Googled a lot, and here is the thing:
Since I made my total home folder encrypted nobody else will ever access it. Nor another user, nor the nobody user. I can not, and will not be able to create anonymously accessible share ever.

Workaround:
Create a regular directory /home/shares. Set it's group to "sambashare", so everyone in the sambashare group can create folders within. Chmod the dir to 775. Create your user share in this directory. Then add some quota, and all done.

---

