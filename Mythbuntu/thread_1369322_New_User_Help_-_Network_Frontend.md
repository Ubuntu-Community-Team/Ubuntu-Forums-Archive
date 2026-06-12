---
title: "New User Help - Network Frontend"
date: 2009-12-31
forum: Mythbuntu
---

### Post by colin-nz on 2009-12-31
Hi all,

I have been trying for a few days on and off trying to get Mythbuntu working with separate front and back ends.

I am trying in VMWare just to prove the concept... so far without success. I know I (probably) won't get video working in VMWare, just trying to get music going first.

Have tried fresh installs of Mythbuntu 9.10... have tried following:

Frontend/backend install, worked 'locally'
Then tried a separate Frontend to connect to the backend...
Then tried 'live front end CD' on two separate PCs
Then tried another virtual front end...

Changed all sorts of settings in between...

Then thought I would start over...

Fresh Frontend/Backend combination - works and plays music.
Then set the MySQL option in MythbuntuControlCenter.
Build a new virtual Frontend only...

Still for the life of me can't get the thing working...

I can connect to the mysql on the front/backend virtual box via mysql -u mythtv -p -h 192.168.1.117 and can view various table contents OK.

But when I start mythtvfronend it just doesn't show...

Running mythfrontend.real -v all gives the details at the end of this message...

I am not a super Linux user... and don't know where else to look... thought I would ask out of frustration :-)

Hopefully someone can spot the problem.

Regard
Colin

---------------------
Output below... it just hangs on the last line.
 mythfrontend.real -v all
2010-01-01 13:21:29.104 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-01-01 13:21:29.127 (old)Settings::ReadSettings(settings.txt) - No such file
2010-01-01 13:21:29.127 Using runtime prefix = /usr
2010-01-01 13:21:29.127 Using configuration directory = /home/colin/.mythtv
2010-01-01 13:21:29.127 UPnp - Constructor
2010-01-01 13:21:29.127 MediaRenderer::Begin
2010-01-01 13:21:29.128 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2010-01-01 13:21:29.128 HttpServer() - SharePath = /usr/share/mythtv/
2010-01-01 13:21:29.129 UPnp::Initialize - Begin
2010-01-01 13:21:29.129 UPnp::Initialize - Starting TaskQueue
2010-01-01 13:21:29.129 UPnp::Initialize - Creating SSDP Thread at port 6547
2010-01-01 13:21:29.345 MSocketDevice::setBlocking(false)
2010-01-01 13:21:29.345 MSocketDevice::setBlocking(false)
2010-01-01 13:21:29.345 MSocketDevice::setBlocking(false)
2010-01-01 13:21:29.345 UPnp::Initialize - End
2010-01-01 13:21:29.345 MediaRenderer::Creating UPnp Description
2010-01-01 13:21:29.345 MediaRenderer::Registering MythFEXML Service.
2010-01-01 13:21:29.345 MediaRenderer::Registering CMGR Service.
2010-01-01 13:21:29.345 UPnp::Start - Starting SSDP Thread (Multicast)
2010-01-01 13:21:29.346 UPnp::Start - Enabling Notifications
2010-01-01 13:21:29.346 SSDP::EnableNotifications() - creating new task
2010-01-01 13:21:29.346 SSDP::EnableNotifications() - sending NTS_byebye
2010-01-01 13:21:29.346 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=aaa9fa67-aa7f-44cb-b91a-875b58207abe
2010-01-01 13:21:29.346 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.346 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::upnp:rootdevice
Cache  =max-age=3600
2010-01-01 13:21:29.481 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.481 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::upnp:rootdevice
Cache  =max-age=3600
2010-01-01 13:21:29.481 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.481 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
Cache  =max-age=3600
2010-01-01 13:21:29.705 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.705 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
Cache  =max-age=3600
2010-01-01 13:21:29.705 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.705 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-01-01 13:21:29.838 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.839 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-01-01 13:21:29.839 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.839 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-01-01 13:21:29.987 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.988 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-01-01 13:21:29.988 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:29.988 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-01-01 13:21:30.199 MSocketDevice::close: Closed socket 19
2010-01-01 13:21:30.199 SSDP::EnableNotifications() - sending NTS_alive
2010-01-01 13:21:30.199 SSDP::EnableNotifications() - Task added to UPnP queue
2010-01-01 13:21:30.199 UPnp::Start - Returning
2010-01-01 13:21:30.199 MediaRenderer::End
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(settings.txt) - No such file
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = '192.168.1.117'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPort' = '6543'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'qgkq5D4p'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBHostName' = '192.168.1.117'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBPassword' = 'qgkq5D4p'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(/home/colin/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-01-01 13:21:30.200 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-01-01 13:21:30.201 Empty LocalHostName.
2010-01-01 13:21:30.201 Using localhost value of mythbuntu-frontend
2010-01-01 13:21:30.201 MCP::DefaultUPnP() - No default UPnP backend
2010-01-01 13:21:30.201 Testing network connectivity to '192.168.1.117'
2010-01-01 13:21:30.208 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.209 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-01-01 13:21:30.209 MythSocket(9995c50:19): new socket
2010-01-01 13:21:30.209 MythSocket(9995c50:19): attempting connect() to (192.168.1.117:6543)
2010-01-01 13:21:30.210 MythSocket(9995c50:19): state change Idle -> Connected
2010-01-01 13:21:30.210 MythSocket(9995c50:19): state change Connected -> Idle
2010-01-01 13:21:30.211 MSocketDevice::close: Closed socket 19
2010-01-01 13:21:30.211 Clearing Settings Cache.
2010-01-01 13:21:30.219 New DB connection, total: 1
2010-01-01 13:21:30.241 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.241 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::upnp:rootdevice
Cache  =max-age=3600
2010-01-01 13:21:30.260 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.261 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::upnp:rootdevice
Cache  =max-age=3600
2010-01-01 13:21:30.261 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.261 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
Cache  =max-age=3600
2010-01-01 13:21:30.436 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.437 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe
Cache  =max-age=3600
2010-01-01 13:21:30.437 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.437 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-01-01 13:21:30.665 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.665 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-01-01 13:21:30.665 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.665 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-01-01 13:21:30.842 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.842 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-01-01 13:21:30.842 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.842 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-01-01 13:21:30.970 MSocketDevice::close: Closed socket 20
2010-01-01 13:21:30.970 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-01-01 13:21:30.970 SSDP::ProcessNotify ...
DescURL=http://192.168.1.114:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:aaa9fa67-aa7f-44cb-b91a-875b58207abe::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600

---

### Post by colin-nz on 2010-01-03
Update:
Now installed backend onto existing ubuntu 9.10.

Tried to connect from Virtual Frontend and also the Mythbuntu Live CD on a laptop.

Seems to still hang in the same place as in the original post... on different back and front ends, so not sure what is going on.

Any help appreciated.

Regards
Colin

---

