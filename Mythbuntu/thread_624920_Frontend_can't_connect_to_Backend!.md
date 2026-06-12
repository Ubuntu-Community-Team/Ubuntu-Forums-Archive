---
title: "Frontend can't connect to Backend!"
date: 2007-11-27
forum: Mythbuntu
---

### Post by root_tux_linux on 2007-11-27
Hi

I installed Mythubuntu...
Rebootet PC...

And now... Error Message like: "Cant Connect To Backend Server, wrong IP blablabla".

I checked backend & frontend settings

both has localhost btw 127.0.0.1 but  i cant still connect :(

Help!

---

### Post by uopjohnson on 2007-11-27
Was it working before you rebooted?
Is your backend running?
```
sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/mythtv-backend start
```
will restart it.
Is your mysql running?
```
sudo /etc/init.d/mysqld stop
sudo /etc/init.d/mysqld start
```
will restart it.

---

### Post by murchball on 2007-11-28
Are your backend and frontend on the same machine? If not, the 127.0.0.1 address is not valid.

---

### Post by root_tux_linux on 2007-11-28
Hi

1. Frontend and Backend are on the same pc

2. mysql and mythbackend are running

3. if i chance the  path for recordings to /var/lib/mythtv/recordings (orginal path) the frontend can connect to backend oO

---

### Post by superm1 on 2007-11-28
Then that means wherever your recordings are, the permissions aren't appropriate.

the folder must be owned by the username **mythtv** so that the backend can write to it

---

### Post by root_tux_linux on 2007-11-29
O.k. i'll test it :)

Thx

---

