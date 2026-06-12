---
title: "mldonkey: remote access with ip limitations"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by neomod on 2010-10-15
Dear Ubuntu Community,

first of all i wish to thank you with all users who decided to post their experience in solving problems here on the forum: thanks to their help my experience with ubuntu as newbie is being much more easier than what I imagined.
Please beg also my english, since it's not my first language :p.

Coming to the point, as per object, I'm playing ( read also as "messing up" :)) with mldonkey since last weeks and I have managed to get it working correctly on my home network ( behind router and firewall ).
Next step in my development plan was to enable remote access to mldonkey web interface from any external network, like for example a friend pc.
I'm aware of the "IP Access Restriction" in the mldonkey configuration file (downloads.ini) but there I can only specify an ip ( or ip-range) to allow access.

So the question is: how can I manage to disable* ip restrictions upon access, so that with a DNS-aliasing service I can access mldonkey web page virtually from anywhere?

Thanks in advance to everybody who might spend five minutes to guide my trough this problem.

(*) = maybe this is not the correct word but it explains the concept.

---

### Post by neomod on 2010-10-15
After some more tries I get the solution ( it was so simple! :o ).

To access mldonkey webserver from anywhere simple edit the "**allowed ip**" field with

```
255.255.255.255
```

( note: if you do this inside web admin page it will result in 0.0.0.0/0, which is fine too ;) )

That's it. now you can enjoy accessing your mldonkey webserver from anywhere.

[COLOR=DarkOrange]**Be Carefull: remember to setup a password for the default user of mldonkey and also remeber to implement a secure log-in to your apache webserver on localhost, just to have another ayer of security ;)**[/COLOR]

---

