---
title: "New headless 12.04 install"
date: 2012-12-24
forum: Mythbuntu
---

### Post by dannyboy79 on 2012-12-24
I have a very old dell dimension 8200 with only 256MB of RAM. It's my MythTV backend (PVR-350 and PVR-500) and file server for my home. It currently runs Mythbuntu 10.04.4 with MythTV 0.23.1+fixes just fine. I made it so no window manager starts up, it's purely command line.

I want to finally upgrade it to 12.04 and either MythTV .25 or .26 but wondering the best route to do it as I want it to be very streamlined. Is it possible to use a mini ubuntu iso and then just add mythbuntu repos and mythtv .25 or .26 without a fuss? Can I setup mythtv backend with out X running? What other packages will I need to install besides mythbuntu repos and then mythbackend, won't that grab all dependencies? I mostly admin the system thru command line or over ssh.

---

### Post by nickrout on 2012-12-24
> **dannyboy79 said:**
> I have a very old dell dimension 8200 with only 256MB of RAM. It's my MythTV backend (PVR-350 and PVR-500) and file server for my home. It currently runs Mythbuntu 10.04.4 with MythTV 0.23.1+fixes just fine. I made it so no window manager starts up, it's purely command line.

I want to finally upgrade it to 12.04 and either MythTV .25 or .26 but wondering the best route to do it as I want it to be very streamlined. Is it possible to use a mini ubuntu iso and then just add mythbuntu repos and mythtv .25 or .26 without a fuss? Can I setup mythtv backend with out X running? What other packages will I need to install besides mythbuntu repos and then mythbackend, won't that grab all dependencies? I mostly admin the system thru command line or over ssh.yes you can start with the server or mini iso. i am pretty sure X is a dependency of the backend but of course you don't have to run it once you have done mythth-setup. 

if you wantba light  distro with total control try arch or gentoo ;).

---

