---
title: "Cannot install mysql server to use with amarok"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by waltervalderrama on 2007-01-02
Hi everybody. I need your valuable help. I cannot install mysql-server. This is what i get after
sudo aptitude install mysql-server

It seems like a dependency problem. Like mysql-server depends on mysql-server-5.0  and this last one depends on the first!!!!!!!!!!!!!

I don't know whats up, how can I install mysql-server. Ahhh, after installation is completed (i dont think so), i tried to start mysqld but get the same error




* Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error al procesar mysql-server-5.0 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de mysql-server:
 mysql-server depende de mysql-server-5.0; sin embargo:
  El paquete mysql-server-5.0 no está configurado aún.
dpkg: error al procesar mysql-server (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 mysql-server-5.0
 mysql-server
andre@walter:/etc/mysql$ cd /etc/init.d/
andre@walter:/etc/init.d$ ./mysql
mysql          mysql-ndb      mysql-ndb-mgm
andre@walter:/etc/init.d$ ./mysql status
open: Permission denied
 * MySQL is stopped.
andre@walter:/etc/init.d$ sudo ./mysql start
 * Starting MySQL database server mysqld                                 [fail]



:-k :-k :-k :-k

---

