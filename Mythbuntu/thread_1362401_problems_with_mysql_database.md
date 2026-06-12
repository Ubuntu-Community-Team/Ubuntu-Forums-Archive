---
title: "problems with mysql database"
date: 2009-12-23
forum: Mythbuntu
---

### Post by dano1 on 2009-12-23
am using jya's repos for .22 and last update killed myth. when updating looks like i have a myysql error updating mythbackend and says try "sudo dpkg-reconfigure mythtv-database"

when run i get this:

dan@dan-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
dan@dan-desktop:~$ 

I've noticed this before when updated but this time when opening myth frontend i get an error along the lines of we speak protocal version 55, backend speaks 54 or something to that effect-sorry i didn't save the logs-and reloaded a working image.

I also get no ouptput in mysql.err or mysql.log

any help appreciated. 
TIA, danny

---

### Post by OffAxis on 2009-12-23
> when opening myth frontend i get an error along the lines of we speak protocal version 55, backend speaks 54

There was an update that was applied to the frontend and not (yet) to the backend.

Restart your backend.

```

sudo service mythtv-backend restart
```

versioning should synchronize.

---

