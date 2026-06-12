---
title: "IP blocking"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by maddtechwf on 2013-03-13
I was reading an article talking about IP blocking to improve speed on Youtube videos.

The command give was this :
```
udo ipfw add reject src-ip XXX.XXX.XXX.XXX/24 in
```

I tried this command but it did not work.  Can anyone tell me what the command is that I will need to use to achieve the same results.

---

### Post by TK999 on 2013-03-13
That command by itself will not do much, as you are supposed to substitute an IPv4 address in there. What does the resource you saw this on say about that?

---

### Post by maddtechwf on 2013-03-13
No, this is all it says.

sudo ipfw add reject src-ip 173.194.55.0/24 in
sudo ipfw add reject src-ip 206.111.0.0/16 in



 You can check the rules were added by using this command:


 sudo ipfw list

---

### Post by Hadaka on 2013-03-13
Hi, you can do the same and more with the 
built in firewall.  ufw
to check if its on or off   do...
```
sudo ufw status
```

here is a good document/tutorial on it.
ufw is usually used on servers...but will also do the same
for single stand alone home/computer

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
have fun !

---

### Post by maddtechwf on 2013-03-13
So after looking at the document that you attached, I came up with this.  Would this be correct?

```

sudo ufw enable
sudo ufw deny from 173.194.55.0 to any port 24
sudo ufw deny from 206.111.0.0 to any port 16

```

---

### Post by Hadaka on 2013-03-13
Hi, it;s correct if you intended to block that IP address
to the specified port 

to block the IP at any port simply leave off the port
as was shown in the doc.  like this....
```

sudo ufw deny from 207.46.232.182
```
i have just started playing with it so am no expert.
pretty much read the doc.  play and see what happens
when something breaks...thats when you learn :P
have fun !

---

### Post by TK999 on 2013-03-14
You might be better off with just plain iptables, without flashy frontends ;):
```

sudo iptables -I INPUT -s 173.194.55.0/24 -j DROP && sudo iptables -I INPUT -s 206.111.0.0/16 -j DROP

```

---

