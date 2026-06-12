---
title: "Folder sharing issue"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by navodaya05 on 2011-10-12
when sharing a folder I am getting a error message 

Samba's testparm returned error 1: Traceback (most recent call last):
  File "/usr/bin/testparm", line 43, in <module>
    import samba
  File "/usr/lib/python2.6/dist-packages/samba/__init__.py", line 45, in <module>
    from samba._ldb import Ldb as _Ldb
ImportError: /usr/lib/libgensec.so.0: undefined symbol: _dcerpc_binding_handle_data


I have installed samba4 as well as samba3

---

### Post by garvinrick4 on 2011-10-12
Do not need samba 4 remove it.
Samba works out of box.
If you want a GUI package to make shares.
```
sudo apt-get install system-config-samba
```
Make you shares by path if you want to share.
Documents.
Share is made with path by example: 
/home/username/Documents
If want to make a new directory.
```
sudo mkdir /home/username/Share
```

---

