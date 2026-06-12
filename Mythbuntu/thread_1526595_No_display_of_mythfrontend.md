---
title: "No display of mythfrontend"
date: 2010-07-08
forum: Mythbuntu
---

### Post by SchneiderIS on 2010-07-08
I have a Zotac Mag with the NVIDIA ION chipset, the NVIDIA drivers are apparently installed, and Mythbuntu is installed and running but when I go to run the mythfrontend nothing comes on screen.  

Here are the contents of my log:

```
Starting mythfrontend.real..
2010-07-07 19:59:56.768 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-07-07 19:59:56.769 Using runtime prefix = /usr
2010-07-07 19:59:56.770 Using configuration directory = /home/pschneider/.mythtv
2010-07-07 19:59:57.693 Empty LocalHostName.
2010-07-07 19:59:57.693 Using localhost value of FamilyRoom
2010-07-07 19:59:57.694 Testing network connectivity to '10.0.1.55'
2010-07-07 19:59:57.720 New DB connection, total: 1
```

If I run "mythfronend.real -v all" this is what I get:

```
~$ mythfrontend.real -v all
2010-07-08 06:33:25.935 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-07-08 06:33:25.936 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-08 06:33:25.937 Using runtime prefix = /usr
2010-07-08 06:33:25.937 Using configuration directory = /home/pschneider/.mythtv
2010-07-08 06:33:25.937 UPnp - Constructor
2010-07-08 06:33:25.937 MediaRenderer::Begin
2010-07-08 06:33:25.939 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2010-07-08 06:33:25.939 HttpServer() - SharePath = /usr/share/mythtv/
2010-07-08 06:33:25.940 GetIPAddressList() - Added eth0 as 10.0.1.100
2010-07-08 06:33:25.941 UPnp::Initialize - Begin
2010-07-08 06:33:25.941 UPnp::Initialize - Starting TaskQueue
2010-07-08 06:33:25.941 UPnp::Initialize - Creating SSDP Thread at port 6547
2010-07-08 06:33:25.942 MSocketDevice::setBlocking(false)
2010-07-08 06:33:25.943 MSocketDevice::setBlocking(false)
2010-07-08 06:33:25.943 MSocketDevice::setBlocking(false)
2010-07-08 06:33:25.943 UPnp::Initialize - End
2010-07-08 06:33:25.943 MediaRenderer::Creating UPnp Description
2010-07-08 06:33:25.943 MediaRenderer::Registering MythFEXML Service.
2010-07-08 06:33:25.943 MediaRenderer::Registering CMGR Service.
2010-07-08 06:33:25.944 UPnp::Start - Starting SSDP Thread (Multicast)
2010-07-08 06:33:25.944 UPnp::Start - Enabling Notifications
2010-07-08 06:33:25.944 SSDP::EnableNotifications() - creating new task
2010-07-08 06:33:25.944 SSDP::EnableNotifications() - sending NTS_byebye
2010-07-08 06:33:25.944 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
2010-07-08 06:33:25.945 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:25.946 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::upnp:rootdevice
Cache  =max-age=3600
2010-07-08 06:33:26.002 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.002 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::upnp:rootdevice
Cache  =max-age=3600
2010-07-08 06:33:26.002 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.003 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
Cache  =max-age=3600
2010-07-08 06:33:26.251 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.252 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
Cache  =max-age=3600
2010-07-08 06:33:26.252 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.252 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-07-08 06:33:26.409 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.409 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-07-08 06:33:26.409 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.409 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-07-08 06:33:26.656 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.657 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-07-08 06:33:26.657 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.657 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-07-08 06:33:26.859 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.859 MSocketDevice::close: Closed socket 19
2010-07-08 06:33:26.859 SSDP::EnableNotifications() - sending NTS_alive
2010-07-08 06:33:26.859 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-07-08 06:33:26.859 SSDP::EnableNotifications() - Task added to UPnP queue
2010-07-08 06:33:26.859 UPnp::Start - Returning
2010-07-08 06:33:26.860 MediaRenderer::End
2010-07-08 06:33:26.860 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-08 06:33:26.860 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2010-07-08 06:33:26.861 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-07-08 06:33:26.861 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBHostName' = '10.0.1.55'.
2010-07-08 06:33:26.861 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2010-07-08 06:33:26.861 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-07-08 06:33:26.862 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-07-08 06:33:26.862 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-07-08 06:33:26.862 (old)Settings::ReadSettings(/home/pschneider/.mythtv/mysql.txt) - 'DBPassword' = '********'.
2010-07-08 06:33:26.862 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-07-08 06:33:26.862 Empty LocalHostName.
2010-07-08 06:33:26.862 Using localhost value of FamilyRoom
2010-07-08 06:33:26.863 Clearing Settings Cache.
2010-07-08 06:33:26.863 MCP::DefaultUPnP() - No default UPnP backend
2010-07-08 06:33:26.864 Testing network connectivity to '10.0.1.55'
2010-07-08 06:33:26.877 MythSocket(ffffffffb57027f8:19): new socket
2010-07-08 06:33:26.877 MythSocket(ffffffffb57027f8:19): attempting connect() to (10.0.1.55:6543)
2010-07-08 06:33:26.878 MythSocket(ffffffffb57027f8:19): state change Idle -> Connected
2010-07-08 06:33:26.878 MythSocket(ffffffffb57027f8:19): state change Connected -> Idle
2010-07-08 06:33:26.878 MSocketDevice::close: Closed socket 19
2010-07-08 06:33:26.879 Clearing Settings Cache.
2010-07-08 06:33:26.896 New DB connection, total: 1
2010-07-08 06:33:26.942 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:26.943 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::upnp:rootdevice
Cache  =max-age=3600
2010-07-08 06:33:27.114 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.114 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::upnp:rootdevice
Cache  =max-age=3600
2010-07-08 06:33:27.114 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.114 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
Cache  =max-age=3600
2010-07-08 06:33:27.341 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.341 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56
Cache  =max-age=3600
2010-07-08 06:33:27.341 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.342 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-07-08 06:33:27.428 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.428 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-07-08 06:33:27.428 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.428 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-07-08 06:33:27.588 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.588 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-07-08 06:33:27.589 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.589 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-07-08 06:33:27.715 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-07-08 06:33:27.715 MSocketDevice::close: Closed socket 20
2010-07-08 06:33:27.715 SSDP::ProcessNotify ...
DescURL=http://10.0.1.100:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:d2c2cf74-df9a-4bcb-a073-5f09ab04ce56::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600

```

It then just hangs on the last output.

Does anyone have any idea what the issue might be?

---

### Post by Paul Mitchell on 2010-11-09
I got mine working by purging and re-installing mythtv-frontend.

There were errors in my .xsession-errors file complaining about the /usr/share/application/mythtv.desktop missing a semi-colon.

---

