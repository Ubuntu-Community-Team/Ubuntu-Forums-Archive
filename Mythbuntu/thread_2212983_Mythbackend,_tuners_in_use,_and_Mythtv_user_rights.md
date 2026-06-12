---
title: "Mythbackend, tuners in use, and Mythtv user rights."
date: 2014-03-24
forum: Mythbuntu
---

### Post by drifting on 2014-03-24
Hi Chaps.

I have been running mythbuntu for quite a few years, but since my last update to 12.04 I have had this really odd problem in that the backend autostarts, but all the tuners end up in use? If I stop the backend, and then start it as me, all the tuners spring back into life? And the rest of Myth, recordings, schedules,playback all work fine.

Bit confused as it seems to be a permissions problem? Compared my tuners rights with a friends myth system and they are the same. Did read somewhere about an upstart job for the backend start up, but that was really beyond my knowledge.

So in essence can anyone point me in the right direction on trying to fix this.

Regards Paul.

---

### Post by Kirboosy on 2014-03-24
Is there anything interesting in the service logs for the Mythbackend?

---

### Post by diyhouse on 2014-03-24
Paul,.. Have you seen this posting,..

[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

I had issues with my 0.27 system not starting and all tuners showing an error...

This script fixed it for me,... it may be of use to you

Just a thought....

---

### Post by tgm4883 on 2014-03-24
> **diyhouse said:**
> Paul,.. Have you seen this posting,..

[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

I had issues with my 0.27 system not starting and all tuners showing an error...

This script fixed it for me,... it may be of use to you

Just a thought....

That should be the one that is shipped with the packages.

I wonder if it's a race condition. If you stop and start the backend using the regular method after a reboot (eg. sudo service mythtv-backend restart) does it work?

---

### Post by drifting on 2014-03-24
Hi all
TGM I tried what you suggested and it still says tuners are unavialable. Stop the service, just type mythbackend, enter my password and away it all goes. No sudo involved in the last part, so it seems I have permissions?

Here is what I have in the upstart conf file.



# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#should die within 5 seconds, but we don't want data loss, so set it to 30
#before we send SIGKILL
kill timeout 30

#if we crash, but not quickly
respawn
respawn limit 2 3600

#because we're daemonizing to avoid logging to upstart log
expect fork

pre-start script 
    [ -x /usr/sbin/mysqld ] || exit 0
    for i in `seq 1 30` ; do
       /usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping >/dev/null && exit 0
       sleep .5
    done
end script

script
	test -f /etc/default/locale && . /etc/default/locale || true
	LANG=$LANG exec /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
end script


Regards Paul

---

### Post by tgm4883 on 2014-03-24
> **drifting said:**
> Hi all
TGM I tried what you suggested and it still says tuners are unavialable. Stop the service, just type mythbackend, enter my password and away it all goes. No sudo involved in the last part, so it seems I have permissions?

Here is what I have in the upstart conf file.



# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#should die within 5 seconds, but we don't want data loss, so set it to 30
#before we send SIGKILL
kill timeout 30

#if we crash, but not quickly
respawn
respawn limit 2 3600

#because we're daemonizing to avoid logging to upstart log
expect fork

pre-start script 
    [ -x /usr/sbin/mysqld ] || exit 0
    for i in `seq 1 30` ; do
       /usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping >/dev/null && exit 0
       sleep .5
    done
end script

script
	test -f /etc/default/locale && . /etc/default/locale || true
	LANG=$LANG exec /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
end script


Regards Paul

Is this a Mythbuntu install, or a Ubuntu+mythtv install? What is the current ownership on your tuners? What is the output of the following two commands

```
groups mythtv
groups <YOUR USER>
```

---

### Post by philip7 on 2014-03-25
I had a similar problem with a fresh Mythbuntu install a few weeks ago, I updated the kernel to the latest version and it resolved the problem.

---

### Post by drifting on 2014-03-27
This was a Mythbuntu install.  Although the original DB way back when was a standard Myth one.

paul@MicroServer:~$ groups mythtv
mythtv : mythtv dialout cdrom audio video
paul@MicroServer:~$ groups paul
paul : paul adm cdrom sudo dip video plugdev mythtv sambashare lpadmin

I do have 4 tuners, but here is the perms for frontend0
paul@MicroServer:/dev/dvb/adapter0$ ls -l
total 0
crw-rw----+ 1 root video 212, 0 Mar 24 16:58 demux0
crw-rw----+ 1 root video 212, 1 Mar 24 16:58 dvr0
crw-rw----+ 1 root video 212, 3 Mar 24 16:58 frontend0
crw-rw----+ 1 root video 212, 2 Mar 24 16:58 net0


Regards Paul.

---

### Post by drifting on 2014-05-09
BUMP
Any more thoughts on this anyone? Before I consider doing a clean install and wiping it all. Not ideal losing everything, but if it solves, so shall it be.

Paul

---

### Post by blm-ubunet on 2014-05-09
Can you explain what the password part is when there is no sudo involved?
> Stop the service, just type mythbackend, enter my password and away it all goes


Try
sudo -H -g mythtv -u mythtv /usr/bin/mythbackend -v all

Does the config.xml file in /home/mythtv/.mythtv/ match or symlink to the one in /home/paul/.mythtv/ ?
Or do these both symlink to the (fallback) one in /etc/mythtv/ ?

---

### Post by drifting on 2014-05-11
Hi thanks for replying.

The password was a mistake on my part, what I was doing was stopping the backend 
sudo service mythtv-backend stop
Then I would type
mythbackend
This would bring all my tuners back to not recording (ready for use) rather than the Not connected if I left it to autostart.
Tried the command you suggested, same end result.

And yes my 3 config.xml files differ:-

etc/mythtv

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <!--
Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
        <DBHostName>127.0.0.1</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>gdRP8KAs</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

home/Paul
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>c8caa856-9def-4a70-85a2-46574c281e03</MediaRenderer>
    </UDN>
  </UPnP>
  <LocalHostName>server</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>10.0.0.10</Host>
    <UserName>mythtv</UserName>
    <Password>gdRP8KAs</Password>
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

home/mythtv
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <!--
Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>127.0.0.1</Host>
    <UserName>mythtv</UserName>
    <Password>gdRP8KAs</Password>
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

Thanks Paul

---

### Post by blm-ubunet on 2014-05-11
Quick assumption check..
This computer with user "paul" & IP=10.0.0.10 is the same machine ? 
and is the master backend ?
Do you have mysql server running on another computer listening on external IPs ?

Those two files are in /home/<user>/.mythtv/config.xml right ??

Forget about copy in /etc/mythtv for a moment..

The user="paul" has host IP=10.0.0.10.
The BE user="mythtv" has IP set to 127.0.0.1 (localhost).

The user="paul" has set <localhostname> which makes all dB settings become tied to that hostname.
The BE user (mythtv) has default empty localhostname.

So when you ran "mythtv-setup" it ran as user="paul" & with localhostname="server" so your tuner cards are on a host named "server"..they don't exist in default empty localhostname profile.

I guess you also have modified mysql (my.cnf) file "--bind-address=" to let mysql listen on external IP addresses.

As the user <paul> works then could change /home/mythtv/.mythtv/config.xml to match or symlink it to working master in user="paul":
```
cp /home/mythtv/.mythtv/config.xml /home/mythtv/.mythtv/config.xml.bak
rm /home/mythtv/.mythtv/config.xml
ln -s /home/paul/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
```
you'll need sudo in front of these cmds.

---

### Post by drifting on 2014-05-14
> **blm-ubunet said:**
> Quick assumption check..
This computer with user "paul" & IP=10.0.0.10 is the same machine ? 
and is the master backend ?

Correct


Do you have mysql server running on another computer listening on external IPs ?

Yes, but it's role is nothing to do with Myth

Those two files are in /home/<user>/.mythtv/config.xml right ??

Correct

Forget about copy in /etc/mythtv for a moment..

The user="paul" has host IP=10.0.0.10.
The BE user="mythtv" has IP set to 127.0.0.1 (localhost).

Correct


The user="paul" has set <localhostname> which makes all dB settings become tied to that hostname.
The BE user (mythtv) has default empty localhostname.

Correct

So when you ran "mythtv-setup" it ran as user="paul" & with localhostname="server" so your tuner cards are on a host named "server"..they don't exist in default empty localhostname profile.

Yes, believe I did, but that was ages ago. This was about 5 upgrades back, been running Myth a long while.

I guess you also have modified mysql (my.cnf) file "--bind-address=" to let mysql listen on external IP addresses.

Nope :- bind-address		= 127.0.0.1


As the user <paul> works then could change /home/mythtv/.mythtv/config.xml to match or symlink it to working master in user="paul":
```
cp /home/mythtv/.mythtv/config.xml /home/mythtv/.mythtv/config.xml.bak
rm /home/mythtv/.mythtv/config.xml
ln -s /home/paul/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
```
you'll need sudo in front of these cmds.

And that sorted it !  thank you so much.

---

