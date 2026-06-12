---
title: "how to find find authentication packets?"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by fzgillani on 2009-02-09
Hi,
I am a new ubuntu user. can anyone here help me in solving this question?
we want to run tcp-dump to figure out what packets belong to the
authentication and what belongs to just the homepage. (the homepage is just a website through which we want to authenticate)

please reply.

---

### Post by japju on 2009-02-09
> **fzgillani said:**
> Hi,
we want to run tcp-dump to figure out what packets belong to the
authentication and what belongs to just the homepage. (the homepage is just a website through which we want to authenticate).


Your question is too generic to answer. Authentication packets of what? If HTTPS, the data is encrypted by the time it hits the wire so you are out of luck unless you know the keys and have suitable tools to decrypt the data.

Anyway, why is this necessary? I.e. what do you really want to do/find out vs. how to do something....

Why do you care about the low level details?

Jari

---

### Post by fzgillani on 2009-02-09
actually I am trying to calculate the authentication details of sim when it is conected to OpenID server through internet.

I have to use traffic shaper i.e. Kaunet to shape the packets.

Now here i want to just see the authentication packets so as i can shape it later.

here is my question again, How can i see the authentication packets in tcpdump or in wireshark? as wireshark is more easy to handle.

anyways thanks for ur conceren.

---

