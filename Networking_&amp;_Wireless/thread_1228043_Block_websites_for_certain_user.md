---
title: "Block websites for certain user"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by fela on 2009-07-31
I'd like to, just as an experiment to see if it's possible, block connections to/from a certain URL/IP for a certain user, but still have other users on the system able to access it.

Is this possible and if so what's the best way?

thanks :)

---

### Post by gettinoriginal on 2009-07-31
Never tried it, but found [this]("http://ubuntuforums.org/archive/index.php/t-82807.html").  :P

---

### Post by fela on 2009-07-31
> **gettinoriginal said:**
> Never tried it, but found [this]("http://ubuntuforums.org/archive/index.php/t-82807.html").  :P

Thanks, I'll try it :)

EDIT: that was kind of not really what I'm looking for. I still want the user to be able to access the internet, just block certain websites.

---

### Post by atera on 2010-11-02
Hi! I have the same question.. Did you get any answer? :)

---

### Post by fela on 2010-11-02
I didn't unfortunately :(

---

### Post by atera on 2010-11-02
Oh, thanks anyway =) I looked around and found this how-to-do: [http://www.ehow.com/how_6475521_block-websites-ubuntu.html](http://www.ehow.com/how_6475521_block-websites-ubuntu.html). I haven't tried it yet, but it seems easy. The question is whether it will block just some users or all users. At least I feel optimistic, there seem to be solutions for almost everything you want to do in ubuntu ^_^

---

### Post by SeijiSensei on 2010-11-03
You could set up a transparent proxy with Squid, then add rules to the "access control lists" that Squid supports.  You'd need to write two rules, one identifying the user's IP address and another identifying the site to be blocked.  Squid allows you to construct multi-rule criteria, so you can tell it to deny access to a specific URL from a specific IP address.

If you want to block a specific person, you'd need to add authentication to Squid.  Your users will probably not like that very much.

There's a lot of material on the Internet about building transparent Squid proxies. You might start [here](http://wiki.squid-cache.org/).

---

