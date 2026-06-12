---
title: "Rsync and Mysql"
date: 2017-12-13
forum: Multimedia Software
---

### Post by linuxuser121317 on 2017-12-13
Good afternoon all,

I'm trying to use Rsync to automate backups for a very lightweight vanilla Lamp server.

The idea was to have a second machine with a fresh version of 16.04 installed, followed by installing apache2, mysql-server and php. (digital ocean had a good guide)

So far I have successfully backed up and restored Apache and it's contents, directories, logins and server config. Probably because it was simple enough that everything was contained in /var/www/html

I'm having a little more trouble backing up mysql-server though. 
I copied over my database directory and the "mysql" directory from /var/lib/mysql but it's not working.

Am I missing something simple?

Thanks!

---

### Post by The Cog on 2017-12-13
You cannot just copy the mysql files while the database is running - you are likely to get inconsistent data that way. You probably have to do proper database export to files, copy them and then import them: [https://dev.mysql.com/doc/refman/5.7/en/backup-methods.html](https://dev.mysql.com/doc/refman/5.7/en/backup-methods.html)

Or use mysql specific replication procedures: [https://dev.mysql.com/doc/refman/5.7/en/replication.html](https://dev.mysql.com/doc/refman/5.7/en/replication.html)

---

### Post by linuxuser121317 on 2017-12-13
Thank for the reply.

 I have some dumps going out already so I'm not worried about the data just yet, mainly the server's users, permissions and list of tables.

If I were to boot with a live CD and rsync the directories, could that perhaps work?

---

### Post by The Cog on 2017-12-13
The server's users, permissions and table descriptions are part of the database contents. They are not separate info.

If you shut the database down then I believe a copy of all the files should be successful. After all, it managers to recover from disk following a reboot. It's just copying files from a running database that is error prone. So there's no need for a live CD though that would work too - just shut the database down, copy the files with rsync, then restart it.

---

### Post by linuxuser121317 on 2017-12-13
Right very good point.  I think I figured out the mysqldump commands. I'm going to test this out and reply with what works. thank you!

---

### Post by The Cog on 2017-12-13
Remember that replication is not the same as a backup. Replicating a corrupt or wiped database doesn't help. A backup should enable you to restore from before things went horribly wrong - you need to keep historical copies too.

---

