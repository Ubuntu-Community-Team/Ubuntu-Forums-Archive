---
title: "mythfilldatabase 0.27 can't connect to mysql server"
date: 2013-11-15
forum: Multimedia Software
---

### Post by childsey01 on 2013-11-15
Have started a new Ubuntu 13.10 install and have attempted three times now to install and setup mythtv (obtained from software centre). Each time in between I did a full purge of both myth and mysql. Can't get past the initial backend set up screen (EDIT: oh wait I now just got past the first screen but same result from the second -- myth doesn't follow good UI design principles I had the save, next and cancel buttons mostly off the screen and I couldn't see which was which - it sure doesn't help their method of highlighting the screen drops a bit in unity but I can see it fine with gnome - no fault of unity, more of myth for overriding display manager decisions - anyway eough of that rant)

running myth-setup
  Database configuration 1/2: MythTV could not connect to the database.
  Hostname:         childsDT01
  Port:                 3306
  Database name:  mythconverg
  User:                mythtv
  Password:          mythtv

restarted backend and ran mythfilldatabase
  ...
  N  Using configuration directory = /home/paul/.mythtv
  ...
  N  Empty LocalHostName
  I  Using localhost value of childsDT01
  E  Unable to connect to database!
  E  Driver error was [1/2003]:
  QMYSQL: Unable to connect
  Database error was:
  Can't connect to MySQL server on 'childsDT01' (111)

I tried out a few quick stupidity checks:

echo $HOSTNAME
  childsDT01

nano /etc/mysql/my.cnf
  ...
  [mysqld]
  user        = mysql
  pid-file    = /var/run/mysqld/mysqld.pid
  socket     = /var/run/mysqld/mysqld.sock
  port        = 3306
  ...
  bind-address        = 127.0.0.1

nano /etc/mythtv/config.xml
  <Configuration>
    <Database>
      <PingHost>1</PingHost>
      <Host>localhost</Host>
      <UserName>mythtv</UserName>
      <Password>mythtv</Password>
      <DatabaseName>mythconverg</DatabaseName>
      <Port>3306</Port>
    </Database>
    ...
  </Configuration>

home/mythtv/.mythtv/config.xml is a link to the same
home/paul/.mythtv/config.xml is the same with the exception that there is the additional dummy tag: <LocalHostName>my-unique-identifier-goes-here</LocalHostName> and the Host tag is set as childsDT01

They're all pretty much the sme settings as I had on my old box.

During my early tests I could find no sign of mysqld.sock on my machine, but it's there now

I couldn't at first but after messing around for a bit I can logon to mysql fine now both as root with: ```
mysql -u root
``` and as mythtv with ```
mysql -u mythtv -p
``` and using the password mythtv. Have carried out the grant all privileges to mythtv command.

Pretty much running out of ideas and exhausted from days of forum searching.

---

### Post by childsey01 on 2013-11-22
bump

---

### Post by childsey01 on 2013-12-05
bump again

---

