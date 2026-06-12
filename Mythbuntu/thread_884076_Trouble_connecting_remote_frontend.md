---
title: "Trouble connecting remote frontend"
date: 2008-08-08
forum: Mythbuntu
---

### Post by Teefs on 2008-08-08
I just setup a new mythtv box and the local frontend works great, however when I try to access with a front end on another machine I get the error "Could not connect to the master backend server -- is it running? Is the IP address et for it in the setup program correct?"

It can ping the system and the "Test MySQL Connection" button works. Am I doing something wrong?

---

### Post by ian dobson on 2008-08-08
Hi,

Are you sure  you've setup the Backend IP address and the master backend address to use the IP address of your network card on the backend?

Both parameters can be configured in myth-setup.

Regards
Ian Dobson

---

### Post by Teefs on 2008-08-08
The only backend I have is the master backend and I am sure the IP address is correct. 

When I try to connect from the live cd instead of my regular Ubuntu install, I get some error about UPnP. It then prompts me to re-enter the ip address and password in the frontend. However as soon as I go to "Watch TV" or try and access the guide I get the same error.

---

