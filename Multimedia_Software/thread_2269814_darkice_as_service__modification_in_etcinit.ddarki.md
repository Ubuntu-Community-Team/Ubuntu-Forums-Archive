---
title: "darkice as service  modification in /etc/init.d/darkice"
date: 2015-03-18
forum: Multimedia Software
---

### Post by majacobs on 2015-03-18
starting darkice keeps me really busy...
the solution I use now is  to set up darkice as service and because then it will not start on some pc's i created a shell script which i call in rc.local:
sleep 10; /home/darkice/./test &
exit 0

---

