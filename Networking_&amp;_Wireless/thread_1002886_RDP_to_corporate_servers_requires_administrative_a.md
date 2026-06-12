---
title: "RDP to corporate servers requires administrative access?"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Fr33d0m on 2008-12-05
Using XP I can RDP into anything on the corporate network (both our own servers and the ones at the corporate offices).

Using Intrepid, I can RDP into our own servers but the servers at the corporate office say that I must have administrative access.  I can get the server's login prompt, but no matter what, it says I must have administrative access.

Does anyone have any ideas on what I would need to do to get the corporate servers to allow me in?  I'm conducting a trial run to see if we can move to Ubuntu for the corporate network and this is one hurdle I definitely need to solve.

---

### Post by jmoorse on 2008-12-07
3 things:

1. Are your Corp. servers Server 2008?
2. You are logging in with your domain account right (username@domain)?  Not trying to log in locally to the servers?
3. Try the rdesktop app as another test

---

