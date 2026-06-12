---
title: "ProFTPd generate too many localhost connections"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by boshkash1151 on 2013-06-28
Almost every second I get the following log section in proftpd system log


```

Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): AuthOrder in effect, resetting auth module order
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): connected - local  : 1.2.3.4:1111
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): connected - remote : 111.222.333.444:2211
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): FTP session opened.
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching PRE_CMD command 'USER user123' to mod_exec
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching PRE_CMD command 'USER user123' to mod_rewrite
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching PRE_CMD command 'USER user123' to mod_tls
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching POST_CMD_ERR command 'USER user123' to mod_exec
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching POST_CMD_ERR command 'USER user123' to mod_delay
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): dispatching LOG_CMD_ERR command 'USER user123' to mod_log
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): mod_tls/2.4.3: scrubbing 1 passphrase from memory
Jun 18 22:04:30 nc proftpd[10048] localhost (111.222.333.444[111.222.333.444]): FTP session closed.

```



where 111.222.333.444 is the external ftp server ip and 1.2.3.4 is the internal server ip.


Could anyone explain the reason behind those logs and how to stop them

---

### Post by boshkash1151 on 2013-07-02
any ideas ?

---

