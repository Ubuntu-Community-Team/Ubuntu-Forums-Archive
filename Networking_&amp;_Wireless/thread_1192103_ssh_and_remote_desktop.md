---
title: "ssh and remote desktop??"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2009-06-19
can someone tell me how to make a ssh server or a good ssh program for linux???? and please tell me how to do a remote desktop from a outside connection???? i can do it in my own router but i dont know how to do a out side connection i could if it told me what port it runs off of???

---

### Post by MKdx on 2009-06-19
To install it
```
sudo apt-get install ssh
```

And this is how you access to the remote machine
```
ssh username@ipaddress
```

And if you have a router, you would probably need to [_forward port_]("http://portforward.com/routers.htm") 22.

---

### Post by xenosaga456 on 2010-06-25
wow thanks thats really simple but how can i configure it?

---

### Post by CharlesA on 2010-06-25
> **xenosaga456 said:**
> wow thanks thats really simple but how can i configure it?

You can try this:

```
man ssh
```

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by pricetech on 2010-06-25
Don't forget to back up your configuration file /etc/ssh/sshd_config before you make any changes.

---

