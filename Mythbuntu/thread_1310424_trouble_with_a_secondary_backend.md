---
title: "trouble with a secondary backend"
date: 2009-11-01
forum: Mythbuntu
---

### Post by rbtprkr on 2009-11-01
hello, I have been running a FE/BE with 8.1 on it, this was working with several remote front ends using both mythbuntu and ubuntu. I had a chance to buy another pvr 500 and built another machine to use as a secondary backend. I used info from [http://www.mythtv.org/docs/mythtv-HOWTO-6.html#modify_perm_mysql](http://www.mythtv.org/docs/mythtv-HOWTO-6.html#modify_perm_mysql) and ran 
$ mysql -u root mythconverg
mysql> grant all on mythconverg.* to mythtv@"192.168.1.%"identified by "mythtv";
mysql> flush privileges;

but replaced the ip address with mine now i cant connect to the BE from any of the remote frontends but I can connect from the FE on the FE/BE can somebody give me some direction on fixing my database?

---

