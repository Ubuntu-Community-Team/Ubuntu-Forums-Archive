---
title: "Squid3 Permissions"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by Laera_Loris on 2013-09-01
Hi guys, my name is Laea Loris and I run a Squid3 proxy on my Amazon EC2. Now, I want to configure the server so that anyone with his IP can use the proxy. How do I do that?

---

### Post by SeijiSensei on 2013-09-01
You're kidding, right?  You want to let people you don't know use your proxy?  What happens when someone discovers it and begins downloading child pornography through it?

You must be a very trusting person in real life, but trusting all of the hundreds of millions of Internet users is a recipe for disaster.

If you want to let a designated set of people use your proxy, then set up [authentication]("http://wiki.squid-cache.org/Features/Authentication") and require them to log in with a password.

---

