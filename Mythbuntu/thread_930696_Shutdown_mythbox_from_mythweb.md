---
title: "Shutdown mythbox from mythweb?"
date: 2008-09-26
forum: Mythbuntu
---

### Post by bergqvistjl on 2008-09-26
Hi, is there a way/script/php modification i can do to shutdown, (or tell mythwelcome to lock/unlock shutdown if idle) my mythbox from within mythweb?

---

### Post by bergqvistjl on 2008-09-26
anybody?

---

### Post by bergqvistjl on 2009-05-17
bump.

---

### Post by ian dobson on 2009-05-17
Hi,

There isn't a script to shutdown myth/the backend from Mythweb, but it should be possible to write a small script that calls

sudo shutdown now.

**A small tip:** 
The apache2 user needs to be in the sudoer's list to allow it to run the shutdown script.

**Warning:**
This is a security hole and wouldn't make it into the myth release.

Regards
Ian Dobson

---

