---
title: "Local copy of /etc/hosts"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by Hooked2 on 2008-12-11
I often use the /etc/hosts file to make my ssh and scp commands compact and simple. Now however, I am on a system which I am not the administrator and only have access to my home directory. Is there a local equivalent of /etc/hosts that is stored somewhere locally? I've thought of using a alias bindings but they seems more like a hack.

---

### Post by aysiu on 2008-12-11
Maybe this?
[http://docs.hp.com/en/B9106-90011/hosts.equiv.4.html](http://docs.hp.com/en/B9106-90011/hosts.equiv.4.html)

---

### Post by jonobr on 2008-12-11
I have had the same issue before,
The only way I got around doing this was (if I recall rightly) to create a small perl script do what I needed,

```

print "enter hostname"
chomp ($host =<STDIN>);

```
And then I recall doing some if statements to match the hostname in Stdin to my an IP address.
I then used Ssh to connect.
If your interested Ill take a look around to see if I can recall again how it was done

---

### Post by jonobr on 2008-12-11
and of course an easier way to do it is to have a file named as the hostname, with ssh in it

i.e. the name of the file is my_host
in it put

ssh [email]me@xx.xx.xx.xx[/email]

so when you type the host name  it will actually execute the file,
both hacky as you mention , but work.

---

