---
title: "Mythbuntu frontend+backend at startup"
date: 2008-08-06
forum: Mythbuntu
---

### Post by Eldis on 2008-08-06
I have sasc-ng and newcs running so that I use my subscriber card and watch some encrypted channels.

The problem is mythbuntu is starting up the backend on startup and sasc-ng and newcs need to be startup at a specific order so that everything works. Namely newcs first then sasc-ng and finally the mythbackend.

I have edited the mythtv-backend startup script so that the necessary additions are there for start and stop but still in the startup procedure it must somehow use something else. Now I have to do manually: mythtv-backend stop & start so that the backend goes up the way I want.

So anything I could do here ? I'm afraid I understand relatively little about runlevels even after reading about them.

I guess even the info on how to disable mythfrontend and backend from starting automatically and adding a custom startup script somewhere somehow would be great.

---

