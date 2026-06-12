---
title: "Cannot connect to msn"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by evan54 on 2011-03-04
Hi everyone,

found a couple of posts about  this.

The problem:
Cannot connect to msn through empathy on Maverick

Solutions I tried:
- killall telepathy-butterfly
- removing telepathy-butterfly completely
- the solution suggested here: [http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/](http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/)

Nothing has worked so far....

any ideas?

---

### Post by marl30 on 2011-03-04
Msn in Empathy seems to be working for me. I just tried it after seeing this thread. I usually use Emesene or Pidgin. If you can't get it to work, consider using one of those. There is also amsn. They are in the Software Center.

---

### Post by evan54 on 2011-03-05
hm... I really like empathy and when I tried pidgin it also didn't work.... What server and port are you using on empathy?

Mine are:
server: messenger.hotmail.com
port: 443

---

### Post by marl30 on 2011-03-06
> **evan54 said:**
> hm... I really like empathy and when I tried pidgin it also didn't work.... What server and port are you using on empathy?

Mine are:
server: messenger.hotmail.com
port: 443

How do I check for that?

I didn't have to put in any special configuration to get either of them to work. I just entered my IM details, clicked connect and they logged on.

---

### Post by evan54 on 2011-03-06
When you open empathy, click F4 or go edit->accounts and then on the msn account click advanced.

thanks,

---

### Post by marl30 on 2011-03-06
> **evan54 said:**
> When you open empathy, click F4 or go edit->accounts and then on the msn account click advanced.

thanks,

Ok, I did as you said. This is what I'm seeing:

Server: messenger.hotmail.com

Port: 1863

---

### Post by evan54 on 2011-07-04
ok... soo after a billion years I decided it's time to stop using ebuddy.com and use a real client.. Yes I could've switched to pidgin etc whatever... didn't feel like it...

So installed a fresh version of ubuntu but kept the home folder as it was and still problems existed with connecting to msn through empathy... which meant something in the /home folder was wrong. Created a new user and there things worked fine... So what I ended up doing is moving all the .files from /home somewhere else, yes I know you'll pretty much loose almost all your settings but i copied them back later, or at least the ones I new I really needed... Anyway problem solved... in a way... If anyone wants to post which files in the /home folder are related to empathy / telepathy what not it would be great to come up with a neater solution.

---

