---
title: "Could not connect to master backend"
date: 2008-02-06
forum: Mythbuntu
---

### Post by dmiller2 on 2008-02-06
I have Mythbuntu installed on a DELL 2400.

when i try to watch TV i got a error message "Could not connect to the master backend server -- is it running ? Is the IP adress set for it in the setup program correct?"

front and back -end in on the same machine.

Tanks

---

### Post by softdel on 2008-02-07
Hi, try opening a terminal and typing 
```
sudo mythbackend
```

I have been using myth for over a year, so lets start from the top, shall we?

---

### Post by dhjohnson on 2008-02-07
It sounds like your myth box has an IP address other than the one you specified during initial setup.  You may have also lost connectivity.  If you have a combined frontend/backend, you shouldn't need to specify an IP address other than 127.0.0.1.

---

