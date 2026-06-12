---
title: "DHCP fails - but it's not necessary"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by BobSongs on 2005-12-10
Greetings

Each time Edubuntu starts it says:

```
Starting DHCP server... [**[COLOR="Red"]fail[/COLOR]**]
```

My Linksys Router is not set to DHCP. I disabled it in the Router's setup in order to host my own website on this box (192.168.1.100). Since it fails and I'm able to surf the web, use instant messaging and host my website, I don't suppose there's a way to disable the DHCP server without causing too many problems, would there?

And could someone point me to a posted tutorial? I haven't located one.

Thanks.

---

### Post by ketilkn on 2005-12-10
How about trying to remove DHCPD?

```
sudo apt-get remove dhcpd
```

---

### Post by BobSongs on 2005-12-10
:rolleyes:

Duhhh. Hyuk, hyuk. #-o

I'll give it a whirl.

Thanks. I guess that's why I wear this Ubuntu newbie purple badge of shame, eh? ;)

---

