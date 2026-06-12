---
title: "mythbuntu frontend crashes to desktop on startup"
date: 2009-07-20
forum: Mythbuntu
---

### Post by waltm on 2009-07-20
I have a frontend installation that was working fine till this weekend.  I ran out of disk space and after cleaning up some log files the frontend will no longer fully load.
I ran 'mythfrontend -v important' and the results are posted below
```
htpc@htpc-desktop:~$ mythfrontend -v important
2009-07-20 16:56:22.926 Using runtime prefix = /usr
2009-07-20 16:56:22.926 Configuration::Load - Error parsing: /home/htpc/.mythtv/config.xml at line: 1  column: 1
2009-07-20 16:56:22.926 Configuration::Load - Error Msg: unexpected end of file
2009-07-20 16:56:23.457 Empty LocalHostName.
2009-07-20 16:56:23.457 Configuration::Load - Error parsing: /home/htpc/.mythtv/config.xml at line: 1  column: 1
2009-07-20 16:56:23.457 Configuration::Load - Error Msg: unexpected end of file
2009-07-20 16:56:23.465 New DB connection, total: 1
2009-07-20 16:56:23.468 Closing DB connection named 'DBManager0'
2009-07-20 16:56:23.529 New DB connection, total: 2
2009-07-20 16:56:23.543 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-07-20 16:56:23.543 Enabled verbose msgs: important
2009-07-20 16:56:24.390 Could not open settings file /home/htpc/.mythtv/mysql.txt for writing
2009-07-20 16:56:24.446 Switching to wide mode (MePo-wide)
mythtv: could not connect to socket
mythtv: No such file or directory
2009-07-20 16:56:24.478 lirc_init failed for mythtv, see preceding messages
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
2009-07-20 16:56:25.012 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-20 16:56:25.113 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.198:5060 NAT address 192.168.0.198
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/htpc/.mythtv/themes/MePo-wide
Destroying SipFsm object 
Segmentation fault
htpc@htpc-desktop:~$ 

```

can anyone walk me through what might be happening?

Thanks

---

### Post by crez79 on 2009-07-20
```
Configuration::Load - Error parsing: /home/htpc/.mythtv/config.xml at line: 1  column: 1
```Looks like something is wrong with this file. Open it up and see if it looks normal. 

It should look something like this:
```

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>letters and numbers here</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>yourhostnamehere</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>yourpasswordhere</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>
```Check the permissions of /home/htpc/.mythtv/mysql.txt to make sure it is writable too. It looks like it isn't happy with the permissions.

I don't know if these are causing your problems, but they sure aren't helping. I think myth doesn't have all the settings it needs to run properly.

---

### Post by waltm on 2009-07-21
Thanks for the tips.  It looks like the config.xml file is empty (0 bytes).  Is there a way to have myth setup automatically re-generate this file with default settings?

---

### Post by crez79 on 2009-07-21
I don't know how to recreate it, but if you have another frontend you can copy it from there, or check /root/.mythtv/config.xml to see if there is a copy there. Keep in mind you will need to adjust the permissions of the copied file so non root can read and writh it.

Try

```
sudo cp /root/.mythtv/config.xml /home/htpc/.mythtv/config.xml
sudo chmod 644 /home/htpc/.mythtv/config.xml
```see if that helps.

---

### Post by waltm on 2009-07-21
Thanks, I have replace the config.xml file and mythbuntu is able to write to it when it tries to load.  It is still crashing to desktop tho with the following 
```
htpc@htpc-desktop:~$ mythfrontend -v important
2009-07-21 16:56:47.422 Using runtime prefix = /usr
2009-07-21 16:56:47.599 Empty LocalHostName.
2009-07-21 16:56:47.608 New DB connection, total: 1
2009-07-21 16:56:47.639 Closing DB connection named 'DBManager0'
2009-07-21 16:56:47.767 New DB connection, total: 2
2009-07-21 16:56:47.819 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-07-21 16:56:47.819 Enabled verbose msgs: important
2009-07-21 16:56:50.570 Switching to wide mode (MePo-wide)
mythtv: could not connect to socket
mythtv: No such file or directory
2009-07-21 16:56:50.608 lirc_init failed for mythtv, see preceding messages
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
2009-07-21 16:56:51.909 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-21 16:56:52.274 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.198:5060 NAT address 192.168.0.198
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/htpc/.mythtv/themes/MePo-wide
Destroying SipFsm object 
Segmentation fault
htpc@htpc-desktop:~$ 

```

full logs are at [http://mythbuntu.pastebin.com/f6f105f81](http://mythbuntu.pastebin.com/f6f105f81) if that helps at all.

---

### Post by waltm on 2009-07-22
I replaced the theme folder and eliminated one error but it still crashes to desktop.

```
htpc@htpc-desktop:~$ mythfrontend -v important
2009-07-22 17:29:05.592 Using runtime prefix = /usr
2009-07-22 17:29:05.768 Empty LocalHostName.
2009-07-22 17:29:05.778 New DB connection, total: 1
2009-07-22 17:29:05.782 Closing DB connection named 'DBManager0'
2009-07-22 17:29:05.813 New DB connection, total: 2
2009-07-22 17:29:05.818 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-07-22 17:29:05.818 Enabled verbose msgs: important
2009-07-22 17:29:07.459 Switching to wide mode (MePo-wide)
mythtv: could not connect to socket
mythtv: No such file or directory
2009-07-22 17:29:07.481 lirc_init failed for mythtv, see preceding messages
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
2009-07-22 17:29:09.364 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-22 17:29:09.578 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.198:5060 NAT address 192.168.0.198
SIP: Cannot register; proxy, username or password not set
Floating point exception
htpc@htpc-desktop:~$ 

```

---

