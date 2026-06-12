---
title: "outgoing ip address"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by marjenni on 2012-05-08
Hi,
   we seem to have got our networking settings screwed up.

Our outgoing ip address was wrong, and I have fixed it by putting this line in the code:

curl_setopt($curlSession, CURLOPT_INTERFACE, "xxx.xxx.xxx.xxx");
(Where xxx.xxx.xxx.xxx is the correct ip address).

I would rather fix it in the networking config, but can't see what is wrong.

any ideas on where to start?

---

### Post by marjenni on 2012-05-09
a little more info:

Our server has multiple ip addresses assigned to it, and when we ping it, we see the ip address we would expect.

 However, payments to sagepay from the server are failing because we are passing through the wrong ip address. The ip address that is being passed through is one that is assigned to the server, but not the ip address seen when pinging.

---

