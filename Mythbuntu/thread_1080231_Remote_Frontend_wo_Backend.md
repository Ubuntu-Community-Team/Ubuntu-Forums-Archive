---
title: "Remote Frontend w/o Backend"
date: 2009-02-25
forum: Mythbuntu
---

### Post by janoschbln on 2009-02-25
The Situation:
MythTV Backend on 192.168.0.102 aka mars is a Mythbuntu machine.
Windows machine on 192.168.0.106 is running a VirtualBox VM with a Mythbuntu Frontend without backend.

The Problem:
When I start mythfrontend on my virtual machine and go to TV, it says that it cannot connect to the master backend.

Configuration on mars (Backend):
in /etc/mysql/my.conf I set the bind-address value to 192.168.0.102 --- is that right?
using the setup of mythtv backend I set both backend locations to "mars".
I called in mysql
```
GRANT ALL ON mythconverg.* TO 'mythtv'@'192.168.0.106' IDENTIFIED BY 'C1RFOKIE';
FLUSH PRIVILEGES;
```

Configuration on the frontend:
/etc/mythtv/mysql.txt
```
DBHostPing=yes
DBUserName=mythtv
DBPassword=C1RFOKIE
DBName=mythconverg
DBType=QMYSQL3
```
the same in ~/.mythtv/mysql.txt

~/.mythtv/config.xml
```

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>832ce51a-c88e-4182-9802-f02704cf6a29</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>mars</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>C1RFOKIE</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

Testing database connection via my frontend machine:
mysql -h mars -u mythtv -p -D mythconverg
works, I can connect to the database.

ping mars and nslookup mars are working, too. It gives me the correct IP address.

telnet mars 6543 works as well, the backend is responding.

I also tried using the MythTV-Player for Windows with the given settings and it works, I can watch TV. So why doesn't it work with the MythTV frontend on my virtual machine? Any suggestions?

Thanks in advance ...
Jan

---

### Post by GordonEndersby on 2009-02-25
As I realised yesterday.
In the setup for the combined front/backend you need to make sure the ip address is not 127.0.0.1 otherwise when your new frontend tries to connect to the backen it gets the loopback adress from the database rather than the true ip address of the backend.

Gordon

---

### Post by Cuppa-Chino on 2009-03-04
> **GordonEndersby said:**
> As I realised yesterday.
In the setup for the combined front/backend you need to make sure the ip address is not 127.0.0.1 otherwise when your new frontend tries to connect to the backen it gets the loopback adress from the database rather than the true ip address of the backend.

Gordon

Hmm, that is exactly my problem but when I try to modify the addresses on my combo fe/be then my fe on that pc cannot connect anymore.
which order did you change the settings?

is this the way to do it?
kill Frontend processes
kill Backend processes
backend-setup or gedit conf file ??
frontend-setup or gedit conf file ??
restart backend
restart front ?

any help would be appreciated

---

### Post by Boppy3125 on 2009-03-04
You probably just need to add its own server name/address to the hosts.  Try pinging mars from a terminal on mars.  I am pretty sure I ran into that one.

---

