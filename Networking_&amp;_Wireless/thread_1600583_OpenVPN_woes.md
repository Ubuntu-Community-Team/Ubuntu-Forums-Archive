---
title: "OpenVPN woes"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by canoemoose on 2010-10-19
Hi all,
I have OpenVPN set up on my server at home to allow me into my home network when I'm away from home.  When I set it up, I tested it using my friend's wifi so I know it works on a local geographic scale.
Now I'm away from home, the TLS handshake fails to complete within 60 seconds.  I assume it's timing out, as I can tracepath to the server on port 1194 successfully.  From reading the OpenVPN documentation, I thought that adding "tls-timeout=120" to the client's config file would double the time allowed, but the handshake still fails with the same error message:
```
Tue Oct 19 10:45:17 2010 us=930956 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Oct 19 10:45:17 2010 us=931012 TLS Error: TLS handshake failed
```

Why is the option not being read correctly from the file - does it need to be in the server's config file also?

---

### Post by canoemoose on 2010-10-20
It turns out that adding the option to the server's config file solved the problem.

---

### Post by mike214 on 2012-01-18
Thank you so much! That error was driving me completely crazy.

---

