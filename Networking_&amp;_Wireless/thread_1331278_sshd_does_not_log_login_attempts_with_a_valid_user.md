---
title: "sshd does not log login attempts with a valid user"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by tr1978 on 2009-11-19
I have disabled password authentication on my sshd service, so that it's only possible to log in with a private key.

The problem is that if I try to log in with no key, or wrong key, it does not get logged in auth.log. Trying to log in with an invalid user gets logged, but not with my valid user.

The reason this is a problem, is that fail2ban can't detect and ban someone that is trying to log in with my own username. (I know there is a very small possibility that someone guesses my username, but its still a little annoying)

I have tried to change loglevel to verbose, but that didn't help.

Does anyone know a solution for this?

---

### Post by Lars Noodén on 2009-11-19
I see in the authorization log only a single message for each denial : "Connection closed by *xx.yy.zz.aa*"

I tried changing the LogLevel setting in sshd_config from INFO to ERROR, FATAL, and VERBOSE.  None appear to register more than the above, which was with the default, INFO. 

There might be simple solution, but it's not jumping up right now. 

Some work-arounds might be to launch sshd via xinetd and use the log-on-fail options.

---

### Post by tr1978 on 2009-11-24
Hey, thanks for the effort!

Anyway, I found a solution. 

Added the following line to the filter:
^%(__prefix_line)sConnection from <HOST> .*$


Which takes care of the problem, but also means that if I make 3 successful logins within a 10 min period, i will also get banned. :D But hey, I can live with that.

---
Tr1978

---

### Post by Lars Noodén on 2009-11-25
Ok.  Glad you found a work-around.  If you have time and interest look at xinetd.  That can log failed attempts and make it harder to lock yourself out.  ;)

---

### Post by daveysan on 2009-12-02
Hi Tr1978

Can you tell me where this filter should go? I presumably don't just place it somewhere in the sshd_config file. Where is the filter? (Sorry if these are simple questions).

I am currently using fail2ban with ssh user/passwords (on a non standard port) but plan to migrate to keys shortly, to satisfy my paranoia. It looks like your solution will be the icing on the cake :p

---

### Post by tr1978 on 2009-12-02
The filter file for sshd is here:

/etc/fail2ban/filter.d/sshd.conf

Just add your rules below the ones already defined.
(And restart fail2ban ofcourse ;) )

---

### Post by daveysan on 2009-12-02
Wow! Thanks for the speedy reply :KS What a great solution. I just need to make sure I don't lose my keys ... :o

---

