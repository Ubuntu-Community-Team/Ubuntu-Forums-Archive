---
title: "Telnet auto login"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by spinderworka on 2012-09-02
Hi, everyone!
I need to write bash script rebooting router. Router is China-made and there are only two ways to sign in: web & telnet.
I tried to write this:
```
#!/bin/bash
routlog=xxx
routpass=xxx
telnet 192.168.1.1
echo $routlog
echo $routpass
reboot
```
and this:
```
#!/usr/bin/expect
telnet 192.168.1.1
expect Login:
send "xxx\n"
expect Password:
send "xxx\n"
reboot
```

But username was ignored both times.

Does anyone know how to make auto login script via telnet?

---

### Post by steeldriver on 2012-09-02
try

```
#!/usr/bin/expect [COLOR=Red]**-f**[/COLOR]
**[COLOR=Red]spawn[/COLOR]** telnet 192.168.1.1
expect [COLOR=Red][COLOR=Black]L[/COLOR][/COLOR]ogin:
send "xxx\n"
expect Password:
send "xxx\n"
reboot
```You could try quoting the "Login:" and "Password:" strings as well - although I think it's optional

---

### Post by spinderworka on 2012-09-03
Thanks for advise, but it says that spawn is unknown command
```
spawn: command not found
couldn't read file "Login:": no such file or directory
```

---

### Post by SlugSlug on 2012-09-03
pretty sure it could also be done via wget if you get the reboot html page

---

### Post by spinderworka on 2012-09-03
> **SlugSlug said:**
> pretty sure it could also be done via wget if you get the reboot html page

Interesting, how can I do it?

---

### Post by SlugSlug on 2012-09-03
login via web and find reboot page - make note of address

then something like

```
 wget --user=#### --password=#### http://192.168.0.1/reboot.html >/dev/null
```

---

### Post by spinderworka on 2012-09-03
> **SlugSlug said:**
> login via web and find reboot page - make note of address

then something like

```
 wget --user=#### --password=#### http://192.168.0.1/reboot.html >/dev/null
```

Thanks, I'll try it

---

### Post by spinderworka on 2012-09-03
hmm... Hothing happens...
Maybe it because there is soft button for reboot?

---

### Post by SlugSlug on 2012-09-03
right click that button and copy link location

---

### Post by spinderworka on 2012-09-03
Right button click took nothing, cause there was only proporsial to save image or open it in a new tab, but Chromium Developer Console helped to solve the task =)
Thank you very much!
This code:
```

#!/bin/bash
wget --user=xxx --password=xxx http://192.168.1.1/wancfg.cmd?action=reboot >/dev/null
```
actually works!

---

