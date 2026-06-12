---
title: "the swamp of wireless security acronyms"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by chconnor on 2010-11-11
Hi - i'm threading through the byzantine array of wireless security acronyms, trying to understand some of the basics. Please shun me if this is an inappropriate place to ask about this.

It's seem to be implied out on the 'net that setting up a RADIUS server (or some other 802.1x / "enterprise" auth-server setup, not that i understand the esoteric overlap of all those terms either), protects you from more attacks than using WPA2-AES with PEAP and no auth server. True, or my misunderstanding?

If true: since PEAP can be used with or without an authentication server (i think?), and since the point of PEAP is that you don't have to install certificates on clients (?), I'm baffled as to what magic the RADIUS setup (WPA2-AES with PEAP and a RADIUS server) could possibly be imparting, and why the wireless AP couldn't perform the same function... e.g. why routers don't just run a magic RADIUS server on-board and work the same mysterious mojo so we can all stop fretting about fantastical geeks driving by our houses at night.

Clearly i'm missing something fundamental.

Another notion that could use disabusing, if incorrect, and a question:

* My understanding is that hole196 is a vulnerability with or without the auth server (or is it just with 802.1x/enterprise/auth-server setups?), but that it requires someone with inside access (i.e. a user must by authenticated already to use the exploit) and thus isn't really an issue in terms of securing a wireless network with trusted users.

* If end-to-end TLS/SSL/SSH from me to a server on the internet is essentially secure, why can't the connection between my computer and a wireless access point use the same mechanism? Is it really so processor-intensive with modern equipment that we can't just have the AP-equivalent of "https" and do away with the 200 other acronyms and giant security holes? I'm ready to believe that, i guess i'm just surprised.

Thanks for any input,
-c

---

