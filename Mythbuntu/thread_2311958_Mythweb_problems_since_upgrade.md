---
title: "Mythweb problems since upgrade"
date: 2016-01-31
forum: Mythbuntu
---

### Post by Senkoboy on 2016-01-31
```
Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name
```

I think I have the first problem fixed from the information here  [HTML]skubuntu.com/questions/256013/could-not-reliably-determine-the-servers-fully-qualified-domain-name[/HTML]

echo "ServerName localhost" | sudo tee /etc/apache2/conf-available/fqdn.conf
 sudo a2enconf fqdn


I still can't get mythweb to start, I just have a blank page.  I tried to reload mythweb from the Mythbuntu Control Center this is what I got.


```
Preparing to unpack .../mythweb_2%%3a0.27.5+fixes.20160129.6883c20-0ubuntu0mythbuntu4_all.deb ...
Unpacking mythweb (2:0.27.5+fixes.20160129.6883c20-0ubuntu0mythbuntu4) ...
Processing triggers for libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.14) ...
Setting up isc-dhcp-server (4.2.4-7ubuntu12.4) ...
/var/lib/dpkg/info/isc-dhcp-server.config: 4: /etc/default/isc-dhcp-server: Defaults: not found
dpkg: error processing package isc-dhcp-server (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up mythtv-database (2:0.27.5+fixes.20160129.6883c20-0ubuntu0mythbuntu4) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing package mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.

dpkg: error processing package mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-database; however:
  Package mythtv-database is not configured yet.

dpkg: error processing package mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Setting up mythweb (2:0.27.5+fixes.20160129.6883c20-0ubuntu0mythbuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
 * Reloading web server apache2         * 
Errors were encountered while processing:
 isc-dhcp-server
 mythtv-database
 mythtv
 mythtv-backend-master
Error in function: 
Setting up mythtv-database (2:0.27.5+fixes.20160129.6883c20-0ubuntu0mythbuntu4) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing package mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up isc-dhcp-server (4.2.4-7ubuntu12.4) ...
/var/lib/dpkg/info/isc-dhcp-server.config: 4: /etc/default/isc-dhcp-server: Defaults: not found
dpkg: error processing package isc-dhcp-server (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.

dpkg: error processing package mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
```

What is my next step?
Also in  /etc/apache2/sites-enabled/mythweb.conf  should the password be the same as ect/mythtv/config.xml  For some reason there is a different password in these files. I know the one is mysql.txt is the correct one for the database.  Should these be the same?

Thanks

---

### Post by Senkoboy on 2016-01-31
My ect/mythtv/config.xml file

```
<Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host></Host>
    <UserName></UserName>
    <Password>s4JItxUk</Password>
    <DatabaseName></DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

```

My /home/mike/.mythtv/config.xml file

```
<Configuration>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>127.0.0.1</Host>
    <UserName>mythtv</UserName>
    <Password>wh0GzEdP</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
  <UPnP>
    <UDN>
      <MediaRenderer>2f435784-6478-405a-972d-232373f96f6e</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>
```

---

### Post by Senkoboy on 2016-01-31
I edited my ect/mythtv/config.xml file, but still have a blank page when I try to open mythweb. 

```
<Configuration>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>127.0.0.1</Host>
    <UserName>mythtv</UserName>
    <Password>wh0GzEdP</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

```

I get this in my var/log/apache2 file 

[Sun Jan 31 16:17:44.091958 2016] [:error] [pid 1461] [client ::1:50275] PHP Fatal error:  Call to a member function query_col() on a non-object in /usr/share/mythtv/mythweb/includes/utils.php on line 59

---

### Post by Senkoboy on 2016-02-01
I had to edit my /etc/apache2/sites-enabled/mythweb.conf to add the database name, password, and a few other fields that were blank.   read some more information here  [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404")

This upgrade was been a learning experience to say the least.  Most of the problems I have encountered have been had by others in the past, lots of reading, googling and trying  different things.

Thanks all,  almost there.

---

