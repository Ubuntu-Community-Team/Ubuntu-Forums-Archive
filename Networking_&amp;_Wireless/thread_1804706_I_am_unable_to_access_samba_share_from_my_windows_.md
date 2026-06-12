---
title: "I am unable to access samba share from my windows machine"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2011-07-15
I am unable to access samba share from my windows machine. I am getting the following error, pls look at the snapshot..

---

### Post by sikander3786 on 2011-07-15
Can you ping the Samba box from your Windows machine, successfully?

Are there any firewalls involved? If yes, they've been configured properly?

---

### Post by karthick87 on 2011-07-15
I am able to ping the samba box from the windows machine. And no firewalls were involved..

---

### Post by Morbius1 on 2011-07-15
Please post the output of each of the following commands:
```
testparm -s
net usershare info --long
smbtree
```

---

### Post by karthick87 on 2011-07-15
Do you want me to excute the above commands in samba server?

---

### Post by Morbius1 on 2011-07-15
yes

---

### Post by karthick87 on 2011-07-15
Please find the outputs of the above commands in the given link,

[http://paste.ubuntu.com/644775/](http://paste.ubuntu.com/644775/)

---

### Post by Morbius1 on 2011-07-15
Let's get rid of the easy ones first:

[1]Change these parameters:
```
security = SHARE
encrypt passwords = No

```To this:
```
security = user
encrypt passwords = Yes
```And add one more to the [global] section:
```
map to guest = Bad User
```[2] You have the wrong syntax on all your hosts deny / allow parameters. There is no wild card "*" it's simply a space. So for example this:
> hosts deny = 172.29.26.*, 172.29.30.*Becomes:
> hosts deny = 172.29.26. , 172.29.30. Save your smb.conf and restart samba:
```
sudo service smbd restart
```You have a couple of other parameters that I've never seen before so let's see how far this gets you before we do anything else.

---

### Post by karthick87 on 2011-07-15
By the way i have to tell you one thing before we start digging for the solution. I can access samba share from all my windows machines except one machine..

I badly need to access samba share from that windows machine. I will change the configuration as refered by you in your previous post and i will update you the result tonight..

---

### Post by Morbius1 on 2011-07-15
If you can access that server from all your machines except 1 despite having "encrypt passwords = No" and despite having all the errors reported by testparm then I truly don't know what the problem is and have no clue how to fix it.

---

### Post by karthick87 on 2011-07-15
Is it possible to find the cause atleast?

---

### Post by nm_geo on 2011-07-16
You know I had a similar problem on a XP desktop.. I had shares turned on but believe it or not I did not have the Windows Client enable .. Checked that baby and it found my Ubuntu shares. i had yanked my samba around terribly but it was the XP .. Go figure

---

### Post by karthick87 on 2011-07-16
Yeah thankyou. The problem has been resolved and now it is working fine now.

---

