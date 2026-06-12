---
title: "mythrename.pl giving error"
date: 2009-11-14
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-11-14
when I try to run from the master backend ```
mythrename.pl --link /var/lib/mythtv/recordings/readable-recordings/
```
I get the follwing errors:
This host not configured for myth.
(No RecordFilePrefix defined for dell in the settings table.)

Someone suggested I needed to copy a ~/.mythtv/config.xml from a successfully connecting mythfrontend machine and paste it into the master backends user that runs mythtv home dir. I have checked the config.xml and it's the same on all my frontends and the backend. I have looked at teh root config.xml on the master listed here:

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.5</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>qWDt7YiQ</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

and the user that runs mythtv config.xml also listed here:

root@dell:~# cat /home/daniel/.mythtv/config.xml
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>024fe8e4-0b22-4a14-8279-344dbe26b7c9</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.5</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>qWDt7YiQ</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>
 
and I can't figure out what's wrong. can anyone help?

---

### Post by ian dobson on 2009-11-14
Hi

Looks as if the setting "RecordFilePrefix" is not set for your host dell.

Mybe have a look in your settings table.

Regards
Ian Dobson

---

### Post by dannyboy79 on 2009-11-14
if I new how to mess around in the mysql table I would do that but I have no idea what I am doing in there. if you could point me to a guide I would be most appreciative.

---

### Post by dannyboy79 on 2009-11-23
bump

---

