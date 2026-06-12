---
title: "Optimize database producing error - 9.04, myth 0.21"
date: 2009-04-18
forum: Mythbuntu
---

### Post by jb5 on 2009-04-18
Following yesterdays (17-April-09) updates, (both jaunty & Myth), the optimize database script now fails with the following error
```
DBI connect('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database: 
```

Just me or a bug? Any thoughts?

---

### Post by jyavenard on 2009-04-18
> **jb5 said:**
> Following yesterdays (17-April-09) updates, (both jaunty & Myth), the optimize database script now fails with the following error
```
DBI connect('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database: 
```

Just me or a bug? Any thoughts?

check your mysql password

---

### Post by jb5 on 2009-04-18
Haven't changed the DB password for a while, the perl script worked OK until yesterdays updates.

The password in the FE settings looks OK, but when I try and run the script by launching MCC from the FE and then clicking the button to optimize tables (advanced Management), a terminal opens and then closes again without running the script???

checked /etc/mythtv/mysql.txt and that has the password I have in the FE.

Anywhere else I need to check the password?

---

### Post by jb5 on 2009-04-20
Hmmm.

If I run the script as either main user or by prepending sudo, I get the same error listed above.
```
cd /usr/share/doc/mythtv-backend/contrib/
perl optimize_mythdb.pl
sudo perl optimize_mythdb.pl
```

If I open a root terminal and run the script, it runs without error??????```
sudo su
perl optimize_mythdb.pl
```

Anybody know why?

---

### Post by dnuffer on 2010-03-11
I had this same problem. It turns out that [FONT=Courier New]/root/.mythtv/config.xml[/FONT] contained invalid DB connection parameters. Once I fixed those, everything worked as expected.

---

### Post by jb5 on 2010-04-18
Hi dnuffer - Thanks for the tip, but the file you mentioned looks OK to me. :(

```

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>password</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

---

### Post by jb5 on 2010-05-16
OK - managed to fix it.

It turns out that the config.xml file in my USER account was empty!
So copied the CONTENTS of```
/root/.mythtv/config.xml
``` 
into my```
/home/${USER}/.mythtv/config.xml
```file. Sorted.

Useful commands if anybody else is struggling with this```

sudo locate config.xml |grep mythtv
sudo locate mysql.txt | grep mythtv
```
make sure all the reported files square up & go from there.

---

