---
title: "Trouble with second frontend"
date: 2010-05-31
forum: Mythbuntu
---

### Post by hylsan on 2010-05-31
Im trying to get a second frontend to work but cant get it to work.
The problem Ive got now is that it wont connect to my backend, it tries to connect to 127.0.0.1. Ive changed all mysql.txt-files to point to the right backend and in the frontend Ive also entered the right IP.

Ive read a couple of other threads about it but cant get a answer to this one...

Running mythbuntu 9.10.

---

### Post by ian dobson on 2010-05-31
Hi,

Could it be that the frontend is using the config.xml file?

```

<Configuration>
<UPnP>
<UDN>
<MediaRenderer>6454c683-52a8-48c7-a57d-fa66da460984</MediaRenderer>
</UDN>
<MythFrontend>
<DefaultBackend>
<DBHostName>localhost</DBHostName>
<DBUserName>mythtv</DBUserName>
<DBPassword>yourpassword</DBPassword>
<DBName>mythconverg</DBName>
<DBPort>0</DBPort>
</DefaultBackend>
</MythFrontend>
</UPnP>
</Configuration>

```

you may even find the skeleton of this file in '/usr/share/doc/mythtv-backend/contrib'

Hope this helps
Ian Dobson

---

### Post by AlecJ on 2010-05-31
Just a point, but have you enabled "master backend roll" on the mySQL configuration page in mythbuntu control centre on the backend?
This caught me out the first time.

---

### Post by laffinet on 2010-05-31
There's also a setting in the backend setup which you need to change..

From memory it's under "General".

You need to enter the backend IP here too, not the default 127.0.0.1

---

### Post by hylsan on 2010-06-01
Thanks now it works...kind of (mythweb dont work).

The xml's were right, but it helped changing "master backend roll" and changing the IP in backend-setup. I already changed one of the IP's but there were a second place (on the same page) that needed to update aswell.

Thanks!

---

