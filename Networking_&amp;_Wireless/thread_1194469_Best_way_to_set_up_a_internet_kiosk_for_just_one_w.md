---
title: "Best way to set up a internet kiosk for just one web site"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by fparri on 2009-06-22
I have been assigned the task to set up a pc to be used by some colleagues at work to browswe our local intranet. This is the only page which they should see and the only activity that pc should be used for.

Is there a way to implement a locked down ubuntu so that is starts with firefox on that page and doesn't let people do anything else? :)

---

### Post by tmht on 2009-06-23
You may want to explore a firewall.  Depending on how your network is set up you could block all non 192.168.x.x traffic and *might* do the trick. 

[https://help.ubuntu.com/9.04/keeping-safe/C/firewall.html](https://help.ubuntu.com/9.04/keeping-safe/C/firewall.html)

Are they accessing [http://internaldomain.local](http://internaldomain.local) or [http://192.168.x.x](http://192.168.x.x) ?

---

### Post by fparri on 2009-06-24
It's a web site on the 192.168.x.x. Thanks a lot :)

Actually I was thinking at something more 'closed', with no feature other than a web browser, so gnome menus should not be accessible, too. Is this possibile (=where with possibile I mean easily feasible ;) ?

---

### Post by tmht on 2009-06-24
I'd go with a striped down version such as *box (openbox, blackbox,etc) and then setup a user with only permission to run the webbrowser all other permissions denied.

THen do the firewall stuf so they can't get out of the intranet.

---

