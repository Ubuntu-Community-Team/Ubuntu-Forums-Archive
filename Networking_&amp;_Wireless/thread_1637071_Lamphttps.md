---
title: "Lamp/https"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by adamjkok on 2010-12-04
I already have a LAMP server on 10.04, but I have a small problem: by default, all new VHOSTS are HTTP, and I need to create a closed-membership forum for the exchange of secret internal information over HTTPS. I don't really care about self-signed certificates, most members of my organization are technically-oriented enough to accept a certificate in Firefox and I'll inform them of the issue in advance so they know to expect it. The point of having HTTPS is simply to prevent known proxy servers from intercepting sensitive information (the ones we know are known to redirect insecure Google searches and block Google preference changes, who knows if insecurely-submitted passwords are intercepted?).

---

### Post by SeijiSensei on 2010-12-04
You can create a virtual host that listens on port 443 and uses certificates.  Note that you can usually have just one secure virtual host per IP address.  There are lots of tutorials about how to do this; I just found [this one]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html") from a Google search.  Looks pretty comprehensive.

---

