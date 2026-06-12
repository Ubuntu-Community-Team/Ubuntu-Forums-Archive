---
title: "Cant Update ubuntu"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by vajeen on 2009-05-27
I'm currently using ubuntu 9.04 it went well until recenty
when i tried to update the systen it gave me the follwoing error massage,and i cant update it
Could not download all repository indexes

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message

---

### Post by lindsay7 on 2009-05-27
Go to System/administration/software sources and try another download server.

---

### Post by x33a on 2009-05-27
post the output of
```
cat /etc/apt/sources.list
```

and the full output of

```
sudo apt-get update
```

and please embed the output in code.

---

### Post by vajeen on 2009-07-03
they didnt help brothers....i changed the server but when i tried to update the result was same..

---

### Post by superprash2003 on 2009-07-04
do you get the same error? are you able to open websites?

---

### Post by vajeen on 2009-07-04
yes i get the same error.but i can open websites.

---

### Post by superprash2003 on 2009-07-06
go to system->admin->software sources , and try choosing a different server

---

