---
title: "Frontend settings altered after changing network card"
date: 2010-05-28
forum: Mythbuntu
---

### Post by Gizmonty on 2010-05-28
I just changed from a wired network between my Mythbuntu backend and frontend to a wireless setup. The network connection is fine but all of my settings in this frontend have been lost.

I presume that the backend is identifying the frontend by network settings and that changing these leaves it unable to identify the frontend. The IP address is unchanged so I presume it is the MAC address of the network adapter (or something else) that is used to identify the frontend.

I imagine there is a field in the backend database that stores this value that I can modify to correct this problem. Does anyone know what it is? Or am I overcomplicating this and missing a much more obvious way.

---

