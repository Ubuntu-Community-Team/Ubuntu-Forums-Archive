---
title: "NX installation problem."
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by destiriser on 2011-09-27
When install nxserver:
```
# dpkg -i nxserver_3.5.0-8_amd64.deb
NX> 704 ERROR: Initialization failed. Cannot open file: /usr/NX/etc/server.cfg.
NX> 704 ERROR: No such file or directory. Please try to fix the problem by
NX> 704 ERROR: running: /usr/NX/scripts/setup/nxserver --install.
dpkg: b&#65533;&#65533;d przetwarzania nxserver (--install):
 podproces zainstalowany skrypt post-installation zwr&#65533;ci&#65533; kod b&#65533;&#65533;du 1
Wyst&#65533;pi&#65533;y b&#65533;&#65533;dy podczas przetwarzania:
 nxserver
# /usr/NX/scripts/setup/nxserver --install
NX> 700 Installing: server at: wto wrz 27 18:36:33 2011.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 WARNING: Found file: /usr/NX/etc/keys/node.localhost.id_dsa.
NX> 700 WARNING: Skipping generation keys for NX users authentication.
NX> 723 Cannot start NX statistics:
NX> 709 NX statistics are disabled for this server.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: http://www.nomachine.com/kb
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices

Server keys

The initial login between client and server happens through a DSA key 
pair, i.e. a couple of specially generated cryptographic keys, called 
the private key and the public key, which allow you to establish a 
secure connection, by means of SSL encryption, between NX client and 
NX server. 

The public part of the key-pair is provided during the installation 
of the server, while the private part of the key-pair is distributed 
together with the NX Client. This ensures that each NX client is able 
to authenticate to the server and to start the procedure for autho-
rizing the user and negotiating the session. 

If you want to create a virtual private network (VPN) instead, you 
need to generate a new DSA key-pair and distribute the private part 
of the key-pair to those NX clients you want authenticated to the NX 
server. More information on how to generate and distribute a new DSA 
key-pair is available at:  

http://www.nomachine.com/ar/view.php?ar_id=AR01C00126

Creating Users

NX is configured to allow access from any system user, as long as 
valid credentials are given to the user for the SSH login. NX pro-
vides an alternative authorization method, allowing system admin-
istrators to determine which users are given access to the NX fun-
ctionalities. This works by implementing a separation between the 
system password and the NX password, so that, for example, it is 
possible to forbid remote access to the system by any other means 
except via NX and use the NX tools to implement effective accounting 
of the system resources used by the user, or to share NX passwords in 
an external database.

To activate the NX user and password DBs, you will have to edit the
NX server configuration file by hand or use the NX Server Manager 
Web tool available for download on the NoMachine Web site at:

http://www.nomachine.com/download-manager.php

Session Shadowing and Desktop Sharing

The session shadowing functionality allows you to share NX sessions 
running on the node. The desktop sharing functionality instead, gives 
access to the native display of the X server as if you were in front 
of the monitor. By default you can access sessions in interactive mode 
and upon authorization of the session owner. You can modify this beha-
viour by tuning the server configuration according to your needs, for 
example by allowing access to sessions in view-only mode, or connecting
to either a suspended session or the local display via the Desktop 
Manager login window.

Load Balancing

NX Advanced Server provides support for multi-node capabilities and 
load balancing. In its current implementation, NX server can only 
manage accounts on the host machine, so to grant access to the node 
running remotely, you will need to create the user account directly 
on the remote node host by issuing the NX node commands as root user.
You will also need to add the NX Server public DSA Key to the node to 
allow this server to connect to the node running on the remote host. 

Documentation

For further information on how to manage the configuration of your 
NX system, please refer to the System Administrator's Guide available 
on the NoMachine Web site at:

http://www.nomachine.com/documentation/admin-guide.php

The NoMachine Team.


NX> 700 Bye.

```install.log:
```

NX> 700 Starting: install node operation at: wto wrz 27 18:15:33 2011.
NX> 700 Autodetected system 'debian'.
NX> 700 Install log is '/usr/NX/var/log/install'.
NX> 700 Creating configuration in /usr/NX/etc/node.cfg.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/node-debian.cfg.sample' '/usr/NX/etc/node.cfg'.
NX> 700 Result: OK.
NX> 700 Running: cat /usr/NX/scripts/init/nxsensor > /etc/init.d/nxsensor.
NX> 700 Result: OK.
NX> 700 Running: chmod +x /etc/init.d/nxsensor.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxsensor S99nxsensor.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxsensor S99nxsensor.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxsensor S99nxsensor.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxsensor K01nxsensor.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxsensor K01nxsensor.
NX> 700 Result: OK.
NX> 700 Inspecting local CUPS environment.
NX> 700 Generating CUPS entries in: /usr/NX/etc/node.cfg.
NX> 700 Running: ln -sf /usr/NX/bin/nxspool /usr/lib64/cups/backend/nx.
NX> 700 Result: OK.
NX> 700 Replacing: /usr/NX/etc/node.cfg.
NX> 700 Running: /bin/cp -f /usr/NX/etc/node.cfg.tmp /usr/NX/etc/node.cfg.
NX> 700 Result: OK.
NX> 700 Deleting temporary file.
NX> 700 Running: /bin/rm -f /usr/NX/etc/node.cfg.tmp.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/bin/nxuexec'.
NX> 700 Result: OK.
NX> 700 Running: chmod 555 '/usr/NX/bin/nxuexec'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/bin/nxuexec'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxkeyadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxkeyadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxkeyadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxtmpperm.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxtmpperm.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxtmpperm.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxtmpperm.sh'.
NX> 700 Result: OK.
NX> 700 CUPS support is disabled.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxuseradd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxuseradd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxuseradd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxuserdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxuserdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxuserdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: /usr/NX/bin/nxnode --validate.
NX> 700 Result: OK.
NX> 700 Running: /bin/mv '/usr/NX/etc/node.lic.sample' '/usr/NX/etc/node.lic'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/etc/node.lic'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0400 '/usr/NX/etc/node.lic'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxlicense.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxlicense.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxlicense.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/tmp/.ICE-unix'.
NX> 700 Result: OK.
NX> 700 Running: chmod 01777 '/tmp/.ICE-unix'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/tmp/.X11-unix'.
NX> 700 Result: OK.
NX> 700 Running: chmod 01777 '/tmp/.X11-unix'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxmountadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxmountadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxmountadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxmountdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxmountdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxmountdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxmountdel.sh'.
NX> 700 Result: OK.
NX> 700 Installation of version: 3.5.0-6 completed.
NX> 700 Showing file: /usr/NX/share/documents/node/cups-info
NX> 700 Bye.


NX> 700 Installing: server at: wto wrz 27 18:15:40 2011.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Running: adduser --system --disabled-password --home /usr/NX/home/nx nx.
NX> 700 Output: Ostrze&#65533;enie: Podany katalog domowy /usr/NX/home/nx ju&#65533; istnieje.
Dodawanie u&#65533;ytkownika systemowego "nx" (UID 108)...
Dodawanie nowego u&#65533;ytkownika "nx" (UID 108) w grupie "nogroup"...
adduser: Ostrze&#65533;enie: katalog domowy "/usr/NX/home/nx" nie nale&#65533;y do w&#65533;a&#65533;nie tworzonego u&#65533;ytkownika
Katalog domowy "/usr/NX/home/nx" ju&#65533; istnieje. Nie zostanie skopiowany z "/etc/skel"..
NX> 700 Result: OK.
NX> 700 Running: usermod -p '*' nx .
NX> 700 Result: OK.
NX> 700 Command: echo '/usr/NX/bin/nxserver' | /usr/bin/chsh nx.
NX> 700 Zmieniam pow&#65533;ok&#65533; logowania dla nx
Wpisz now&#65533; warto&#65533;&#65533; lub wci&#65533;nij ENTER by przyj&#65533;&#65533; warto&#65533;&#65533; domy&#65533;ln&#65533;
        Pow&#65533;oka logowania [/bin/false]: .
NX> 700 Result: OK.
NX> 700 Running: ssh-keygen -q -t dsa -N '' -f '/usr/NX/etc/keys/node.localhost.id_dsa'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/passwords.db.sample' '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/passwords.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/passwords.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/administrators.db.sample' '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/administrators.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/administrators.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/guests.db.sample' '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/guests.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/profiles.db.sample' '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/profiles.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/profiles.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/profiles.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/users.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/users.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -fp '/usr/NX/home/nx/.ssh/restore.id_dsa.pub' '/usr/NX/home/nx/.ssh/default.id_dsa.pub'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/keys'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/keys/node.localhost.id_dsa'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/home/nx'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0700 '/usr/NX/home/nx'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/var'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/var/db'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/closed'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/running'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/failed'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/passwords.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/users.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/administrators.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/profiles.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: touch /usr/NX/etc/nodes.db.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/etc/nodes.db.
NX> 700 Result: OK.
NX> 700 Running: touch /usr/NX/etc/nodes.db.lock.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/etc/nodes.db.lock.
NX> 700 Result: OK.
NX> 700 Running: touch /usr/NX/var/db/broadcast.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/var/db/broadcast.
NX> 700 Result: OK.
NX> 700 Creating configuration file: /usr/NX/etc/server.cfg.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/server-debian.cfg.sample' '/usr/NX/etc/server.cfg'.
NX> 700 Result: OK.
NX> 700 Running: /usr/NX/bin/nxserver --validate.
NX> 700 Result: OK.
NX> 700 Running: /bin/mv '/usr/NX/etc/server.lic.sample' '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0400 '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: /usr/NX/bin/nxserver --validatenode.
NX> 700 Result: OK.
NX> 700 Running: cat /usr/NX/scripts/init/nxserver > /etc/init.d/nxserver.
NX> 700 Result: OK.
NX> 700 Running: chmod +x /etc/init.d/nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver K01nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver K01nxserver.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx '/usr/NX/var/db/stat'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -p '/usr/NX/home/nx/.ssh/default.id_dsa.pub' '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 700 Result: OK.
NX> 700 Cannot start NX statistics: NX> 701 NX statistics are disabled for this server.
NX> 700 Running: /bin/mv -f /usr/NX/etc/server.cfg.tmp /usr/NX/etc/server.cfg.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: http://www.nomachine.com/kb
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices
NX> 700 Bye.


NX> 700 Installing: server at: wto wrz 27 18:36:33 2011.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Running: adduser --system --disabled-password --home /usr/NX/home/nx nx.
NX> 700 Output: Ostrze&#65533;enie: Podany katalog domowy /usr/NX/home/nx ju&#65533; istnieje.
Dodawanie u&#65533;ytkownika systemowego "nx" (UID 108)...
Dodawanie nowego u&#65533;ytkownika "nx" (UID 108) w grupie "nogroup"...
adduser: Ostrze&#65533;enie: katalog domowy "/usr/NX/home/nx" nie nale&#65533;y do w&#65533;a&#65533;nie tworzonego u&#65533;ytkownika
Katalog domowy "/usr/NX/home/nx" ju&#65533; istnieje. Nie zostanie skopiowany z "/etc/skel"..
NX> 700 Result: OK.
NX> 700 Running: usermod -p '*' nx .
NX> 700 Result: OK.
NX> 700 Running: usermod -p '*' nx .
NX> 700 Result: OK.
NX> 700 Command: echo '/usr/NX/bin/nxserver' | /usr/bin/chsh nx.
NX> 700 Zmieniam pow&#65533;ok&#65533; logowania dla nx
Wpisz now&#65533; warto&#65533;&#65533; lub wci&#65533;nij ENTER by przyj&#65533;&#65533; warto&#65533;&#65533; domy&#65533;ln&#65533;
        Pow&#65533;oka logowania [/bin/false]: .
NX> 700 Result: OK.
NX> 700 WARNING: Found file: /usr/NX/etc/keys/node.localhost.id_dsa.
NX> 700 WARNING: Skipping generation keys for NX users authentication.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/passwords.db.sample' '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/administrators.db.sample' '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/guests.db.sample' '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -f '/usr/NX/etc/profiles.db.sample' '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0400 '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: touch '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -fp '/usr/NX/home/nx/.ssh/restore.id_dsa.pub' '/usr/NX/home/nx/.ssh/default.id_dsa.pub'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/keys'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/keys/node.localhost.id_dsa'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/home/nx'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0700 '/usr/NX/home/nx'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/var'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/var/db'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/closed'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/running'.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx:root '/usr/NX/var/db/failed'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/passwords.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/passwords.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/users.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/users.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/guests.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/administrators.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/administrators.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0600 '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/profiles.db'.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/profiles.db.lock'.
NX> 700 Result: OK.
NX> 700 Running: touch /usr/NX/etc/nodes.db.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/etc/nodes.db.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/etc/nodes.db.lock.
NX> 700 Result: OK.
NX> 700 Running: touch /usr/NX/var/db/broadcast.
NX> 700 Result: OK.
NX> 700 Running: chown nx /usr/NX/var/db/broadcast.
NX> 700 Result: OK.
NX> 700 Running: chown nx:root '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: chmod 0400 '/usr/NX/etc/server.lic'.
NX> 700 Result: OK.
NX> 700 Running: /bin/rm -f /usr/NX/etc/server.lic.sample.
NX> 700 Result: OK.
NX> 700 Running: /usr/NX/bin/nxserver --validatenode.
NX> 700 Result: OK.
NX> 700 Running: cat /usr/NX/scripts/init/nxserver > /etc/init.d/nxserver.
NX> 700 Result: OK.
NX> 700 Running: cat /usr/NX/scripts/init/nxserver > /etc/init.d/nxserver.
NX> 700 Result: OK.
NX> 700 Running: chmod +x /etc/init.d/nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver S99nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver K01nxserver.
NX> 700 Result: OK.
NX> 700 Running: ln -sf ../init.d/nxserver K01nxserver.
NX> 700 Result: OK.
NX> 700 Running: chown -R nx '/usr/NX/var/db/stat'.
NX> 700 Result: OK.
NX> 700 Running: /bin/cp -p '/usr/NX/home/nx/.ssh/default.id_dsa.pub' '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 700 Result: OK.
NX> 700 Cannot start NX statistics: NX> 701 NX statistics are disabled for this server.
NX> 700 Running: /bin/mv -f /usr/NX/etc/server.cfg.tmp /usr/NX/etc/server.cfg.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxcookiegen.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxhost.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxdpyinfo.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chown root:root '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod 744 '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 Running: chmod u+s '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 700 Result: OK.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: http://www.nomachine.com/kb
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices
NX> 700 Bye.
```


Or may someone say how to install freeNX? I have problems too.

---

### Post by e79 on 2011-09-27
Have you installed all 3 packages as written on their site ?

> **Note**: Installation of NX Server for Linux  requires the                   download and installation of three packages: client, node and server. The client is needed because                   it ships libraries used by the node. The node is needed because it ships tools needed by the server.                   Furthermore, the SSH server daemon (SSHD) needs to be up and running on each of the NX Node machines                  since NX relies on the mechanism provided by the SSH subsystem for handling user authentication.                   

[http://www.nomachine.com/download-package.php?Prod_Id=3501](http://www.nomachine.com/download-package.php?Prod_Id=3501)

Have you tried installing it using 'sudo' ?

---

### Post by destiriser on 2011-09-27
Yes, I installed these packages as written on the site.

I installed them logged on root.

I know how to install that (i did that many times), but I installed freenx and then I unproperly uninstalled the no machine's nx and now after uninstalling packages via aptitude and removing folders and files I have this error.

So now I want to install no machine's nx or freenx

---

