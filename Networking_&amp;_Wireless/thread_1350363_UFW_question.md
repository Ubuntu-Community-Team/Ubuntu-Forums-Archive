---
title: "UFW question"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by zongpog on 2009-12-09
Hi,

On system :

# ufw status
Status: active

To                         Action  From
--                         ------  ----
22                         DENY    Anywhere
Apache                     DENY    Anywhere
80                         ALLOW   10.206.20.0/24

As one can see, te deny from everywhere to Apache messes with rule 3, the allow to port 80.

How can I either:

1) delete rule 2 and rule 3
2) add a rule for app Apache that allows from 10.206.20.0/24

Many thanks in advance.
z


PS. No, I don't want to use another firewall. iptables is fine.

---

### Post by zongpog on 2009-12-09
Found out how to delete rule 3:

# ufw delete allow from 10.206.20.0/24 to any port 80
Rule deleted

Still cannot work out the app rule:
# ufw delete deny app apache
ERROR: Need 'to' or 'from' clause
# ufw delete deny app Apache
ERROR: Need 'to' or 'from' clause
# ufw delete deny app Apache to any port
ERROR: Wrong number of arguments

---

### Post by Fast_Wyvern on 2009-12-09
install GUFW for a grahical interface as it is easier to remove and add rules for UFW imo

---

### Post by zongpog on 2009-12-09
> **Fast_Wyvern said:**
> install GUFW for a grahical interface as it is easier to remove and add rules for UFW imo

I did anticipate you reply... :(   

Sorry, when I wrote: PS. No, I don't want to use another firewall. iptables is fine.  I also meant to cover GUIs as well.

[B]Let me add.  
i) X is not installed.  
ii) These is a headless server.[/B]

---

### Post by Fast_Wyvern on 2009-12-09
Sorry my assistance was not what you wanted

---

### Post by zongpog on 2009-12-10
Out of hope, I added the gufw to the server and Xdisplayed it back to another PC.  GUFW cannot remove the rule. One can select the rule and try and delete it but the message "error performing operation" is given.

As a workaround, I ran:
ufw allow Apache

and this dropped the deny rule so at least it is allowed. However, I think I shall steer away from ufw and use iptables directly. At least I shall have full control over what it does and I can confidently add and delete rules.

---

### Post by Iowan on 2009-12-10
Since **ufw** is (reportedly) a front end for **iptables**, I presume you should still be able to edit the iptables rules directly. Good Luck!

---

### Post by memilanuk on 2009-12-10
Hmmm... from looking at the tutorial [here]("http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/"), it looks like your syntax is a tad off...

```

# sudo ufw allow Apache
Rule added

# ufw status
Status: active

To Action From
&#8211; &#8212;&#8212; &#8212;-
22 LIMIT Anywhere
Apache ALLOW Anywhere

# sudo ufw delete allow Apache
Rule deleted

# ufw status
Status: active

To Action From
&#8211; &#8212;&#8212; &#8212;-
22 LIMIT Anywhere

```

---

