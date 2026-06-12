---
title: "[SOLVED] Mythtv frontend &amp;amp; backend can't connect to database"
date: 2008-06-27
forum: Multimedia Software
---

### Post by tommyp on 2008-06-27
All-

After finally upgrading from gutsy to Hardy, my frontend/backend interfaces cannot connect to my running backend on the same machine.  I know it is running because I can access it through mythweb and through a mythtv viewer on a windows machine.

I get these errors:
```

Unable to connect to database!
Driver error was [1/2003]:
QMYSQL3: Unable to connect
```


Could the mythconverg password in the frontend and backend interfaces have been changed by the upgrade?  They seemed to match the ones in etc/mythtv/mysql.txt

Thanks in advance for any ideas.

---

### Post by Trollslayer on 2008-06-27
Maybe in the Mythbuntu forum? Under 3rd party projects.

---

### Post by tommyp on 2008-06-29
I figured it out.  It was not a permissions issue, but a MySQL issue.  In upgrading, I had accidentally changed the /etc/mysql/my.cnf file, so it was only listening to localhost.

To fix it, comment out the bindings line in the my.cnf file and restart mysql.  This will allow frontends and backends to access over the network.

---

