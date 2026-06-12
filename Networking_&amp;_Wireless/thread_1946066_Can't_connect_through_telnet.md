---
title: "Can't connect through telnet"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by japhyr on 2012-03-24
I'm trying to run the command "telnet s1.runtime.heroku.com 5000". I get an error message "unable to connect to remote host: no route to host".

I have set port forwarding for the application "heroku" on port 5000, to my machine's static ip address. I am running ubuntu 11.04, on a home wireless network connected to a DSL router. I have no firewall set up

Is my next step contacting my isp to ask if they block port 5000?

---

### Post by MG&amp;TL on 2012-03-24
Something your end I'm afraid. I can connect fine to that IP on port 5000. Although nothing happens when I get there...

---

### Post by japhyr on 2012-03-24
Something on my end that I might be able to diagnose, or something I will need to ask my isp about?

This is just a test command, to diagnose problems using heroku's remote admin interface.

---

### Post by MG&amp;TL on 2012-03-24
Well, I'm not an network expert, (I'm sure one will be along shortly), but it sounds like you've got some sort of problem finding the domain. Try:

```
ping -c3 s1.runtime.heroku.com
```

---

### Post by japhyr on 2012-03-24
I can ping the domain without any problems.

---

