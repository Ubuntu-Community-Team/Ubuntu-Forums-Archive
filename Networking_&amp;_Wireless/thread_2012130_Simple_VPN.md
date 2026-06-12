---
title: "Simple VPN"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by timbim on 2012-06-28
Hi All,

After a little advice here.  I do a certain amount of work with a radio station, I'm currently building up a couple of outside broadcast laptops.  Pushing various things over various ports to various servers is standard practice, with email, audio streams etc.  Occasionally we need to use networks which apply pretty aggressive port blocking for our connection home, so this becomes a problem.  To get around this, on one of our servers, we've got our OpenSSH server listening on port 443, which is always open for https.  We then tunnel the ports through that.  This is fine, but requires a certain amount of reconfiguration of the client apps to point through the tunnel rather than directly to the server in question.  Now that I'm building up some properly configured laptops, I've been thinking about better ways to do it.  From what I understand, making a VPN connection to the server over port 443 will give me the same avoidance of port blocking without the disadvantage of having to point all services into the tunnel.  I also believe that OpenSSH includes VPN support.

Am I correct in the above; and if so, how can I go about setting it all up?

Thanks,
Tim

---

