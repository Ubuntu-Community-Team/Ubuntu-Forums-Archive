---
title: "Backend settings"
date: 2016-01-01
forum: Mythbuntu
---

### Post by Tadaen_Sylvermane on 2016-01-01
Not Mythbuntu but I figure people here will know the answer. I set my Ubuntu Server LTS installation to be a Mythtv backend. During installation it gave me the option of the server being available remotely to other computers on the network. At the time I chose no since I didn't expect to have multiple media centers running. Things have changed. I'm assuming that question during installation involved the SQL database. How do I change my backend so that it can be accessed by multiple htpcs on my lan?

*EDIT* I installed with the mythtv-backend-master package

---

### Post by aelfric55 on 2016-01-01
Easiest way is to install the mythbuntu control centre, if you haven't already done so, and do it from there.

But in general, the issue is just getting mysql to listen to tcpip instead of the local mysql socket, and binding the mysql server to the ip address of the master backend server instead of localhost or 127.0.0.1. Tcpip is not enabled in mysql by default. Lines referencing "skip-networking" should be commented out of the my.cnf file (possibly also from the mysql startup script if present),  a bind-address  line should be set in the my.cnf to your master backend's ip address. Then it ought to be ready after a mysql restart. There are innumerable crib sheets to help in this. Here's one: [https://www.percona.com/doc/percona-xtrabackup/2.3/howtos/enabling_tcp.html](https://www.percona.com/doc/percona-xtrabackup/2.3/howtos/enabling_tcp.html)

The backend will also need to be set to run on your ip address (not localhost or 127.0.0.1) in the mythtv backend setup.

---

### Post by Tadaen_Sylvermane on 2016-01-03
Searched for mysql settings and changed it. Did not know about having to reassign the ip of the backend in the mythtv-setup though. Working great now. Solved.

---

