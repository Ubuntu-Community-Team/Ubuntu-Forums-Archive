---
title: "Mtyhbuntu frontent Ubuntu Server backend?"
date: 2009-07-12
forum: Mythbuntu
---

### Post by Mephi on 2009-07-12
Hi Guys,

I'm looking at building a myth frontend and installing the backend on my ubuntu server, so I don't have to have any extra boxes running 24/7

One of the concerns I have is that I'll need to keep the myth versions in sync as the myth developers seem to have a tendancy of changing the database schemas. 

Do they (mythbuntu & Server) use the same repositories? Or should I point my server at different repositories for the myth backend packages?

Cheers,

Mephi

---

### Post by ian dobson on 2009-07-12
Hi,

I'm running ubuntu 8.10 on my backend (running myth-backend from the fixes repositry 0.21) and mythbuntu on my frontend running the VDPAU backports without any problems.

As long as you run the same version 0.21 in my case, you shouldn't see any protocol different errors.

Regards
Ian Dobson

---

