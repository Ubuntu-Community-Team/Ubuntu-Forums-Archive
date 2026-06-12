---
title: "Remote Mythfrontend not starting"
date: 2011-04-15
forum: Mythbuntu
---

### Post by GooKing on 2011-04-15
Probably a simple one for someone.

I've got a combined front/back working fine, and am now trying to get an additional frontend.

I've used the backend setup to allow other front ends, installed the new frontend with the same version, and configured with the SQL username, which seemed to work. 

However, when I start mythfrontend, it hangs - it's running in system monitor, but nothing on screen, just desktop.

Managed to get a verbose log:
(sorry: didn't know what was important, so it's a bit big!)

```
2011-04-15 18:28:26.399 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-04-15 18:28:26.400 (old)Settings::ReadSettings(settings.txt) - No such file
2011-04-15 18:28:26.400 Using runtime prefix = /usr
2011-04-15 18:28:26.400 Using configuration directory = /home/jonathan/.mythtv
2011-04-15 18:28:26.400 UPnp - Constructor
2011-04-15 18:28:26.400 MediaRenderer::Begin
2011-04-15 18:28:26.401 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2011-04-15 18:28:26.410 HttpServer() - SharePath = /usr/share/mythtv/
2011-04-15 18:28:26.414 GetIPAddressList() - Added eth0 as 10.0.2.10
2011-04-15 18:28:26.414 UPnp::Initialize - Begin
2011-04-15 18:28:26.415 UPnp::Initialize - Starting TaskQueue
2011-04-15 18:28:26.415 UPnp::Initialize - Creating SSDP Thread at port 6547
2011-04-15 18:28:26.415 MSocketDevice::setBlocking(false)
2011-04-15 18:28:26.416 MSocketDevice::setBlocking(false)
2011-04-15 18:28:26.416 MSocketDevice::setBlocking(false)
2011-04-15 18:28:26.416 UPnp::Initialize - End
2011-04-15 18:28:26.416 MediaRenderer::Creating UPnp Description
2011-04-15 18:28:26.416 MediaRenderer::Registering MythFEXML Service.
2011-04-15 18:28:26.416 MediaRenderer::Registering CMGR Service.
2011-04-15 18:28:26.416 UPnp::Start - Starting SSDP Thread (Multicast)
2011-04-15 18:28:26.416 UPnp::Start - Enabling Notifications
2011-04-15 18:28:26.416 SSDP::EnableNotifications() - creating new task
2011-04-15 18:28:26.416 SSDP::EnableNotifications() - sending NTS_byebye
2011-04-15 18:28:26.417 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=6c2d9c1b-a023-4909-809f-7b7ec895a388
2011-04-15 18:28:26.426 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.428 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:28:26.624 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.625 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:28:26.625 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.625 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:28:26.714 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.715 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:28:26.715 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.715 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:28:26.829 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.829 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:28:26.829 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.830 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:28:26.940 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.941 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:28:26.941 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.941 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:28:26.958 MSocketDevice::close: Closed socket 27
2011-04-15 18:28:26.959 SSDP::EnableNotifications() - sending NTS_alive
2011-04-15 18:28:26.959 SSDP::EnableNotifications() - Task added to UPnP queue
2011-04-15 18:28:26.959 UPnp::Start - Returning
2011-04-15 18:28:26.959 MediaRenderer::End
2011-04-15 18:28:26.959 (old)Settings::ReadSettings(settings.txt) - No such file
2011-04-15 18:28:26.959 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2011-04-15 18:28:26.960 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2011-04-15 18:28:26.960 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBHostName' = '10.0.2.13'.
2011-04-15 18:28:26.960 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2011-04-15 18:28:26.961 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2011-04-15 18:28:26.961 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBPassword' = 'h6tV3477'.
2011-04-15 18:28:26.961 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2011-04-15 18:28:26.961 (old)Settings::ReadSettings(/home/jonathan/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2011-04-15 18:28:26.961 (old)Settings::ReadSettings(./mysql.txt) - No such file
2011-04-15 18:28:26.961 Empty LocalHostName.
2011-04-15 18:28:26.961 Using localhost value of diningroom1
2011-04-15 18:28:26.961 Clearing Settings Cache.
2011-04-15 18:28:26.962 MCP::DefaultUPnP() - No default UPnP backend
2011-04-15 18:28:26.962 Testing network connectivity to '10.0.2.13'
2011-04-15 18:28:26.963 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:26.964 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:28:26.969 MythSocket(a390ce0:27): new socket
2011-04-15 18:28:26.969 MythSocket(a390ce0:27): attempting connect() to (10.0.2.13:6543)
2011-04-15 18:28:26.970 MythSocket(a390ce0:27): state change Idle -> Connected
2011-04-15 18:28:26.970 MythSocket(a390ce0:27): state change Connected -> Idle
2011-04-15 18:28:26.970 MSocketDevice::close: Closed socket 27
2011-04-15 18:28:26.970 Clearing Settings Cache.
2011-04-15 18:28:26.979 New DB connection, total: 1
2011-04-15 18:28:27.027 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.027 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:28:27.127 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.128 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:28:27.128 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.128 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:28:27.231 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.231 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:28:27.231 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.231 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:28:27.243 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.243 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:28:27.244 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.244 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:28:27.279 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.279 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:28:27.280 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.280 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:28:27.321 MSocketDevice::close: Closed socket 32
2011-04-15 18:28:27.322 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:28:27.322 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:30:49.535 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.536 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:30:49.536 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.536 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:30:49.536 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.536 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:30:49.537 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.537 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:30:49.537 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.538 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:30:49.538 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.538 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:30:49.538 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.539 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:30:49.539 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.539 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:30:49.539 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.540 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:30:49.540 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.540 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:30:49.541 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:30:49.541 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:31:55.103 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.104 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:31:55.202 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.202 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:31:55.202 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.202 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:43e1a419-85fa-48ce-989f-2832f85850a8
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8
Cache  =max-age=3600
2011-04-15 18:31:55.353 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.354 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:43e1a419-85fa-48ce-989f-2832f85850a8
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8
Cache  =max-age=3600
2011-04-15 18:31:55.354 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.354 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:31:55.469 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.469 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:31:55.470 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.470 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:31:55.502 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.503 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:31:55.503 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.503 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:31:55.663 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:31:55.663 SSDP::ProcessNotify ...
DescURL=http://10.0.2.13:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:35:49.824 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.831 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:35:49.831 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.832 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:35:49.832 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.832 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:35:49.832 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.832 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:35:49.832 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.832 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:35:49.832 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.833 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:35:49.833 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.833 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:35:49.833 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.833 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:35:49.834 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.834 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:35:49.834 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.834 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:35:49.834 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:35:49.835 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:40:50.070 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.091 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:40:50.091 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.092 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:40:50.092 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.092 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:40:50.092 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.092 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:40:50.093 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.093 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:40:50.093 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.093 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:40:50.093 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.093 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:40:50.094 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.094 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:40:50.094 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.094 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:40:50.094 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.094 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:40:50.095 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:40:50.095 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:45:07.427 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:07.461 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:07.463 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:07.463 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:07.463 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:07.463 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:07.682 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:08.670 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:08.894 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:09.430 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:09.431 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:09.431 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:09.431 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:09.431 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:09.431 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:09.603 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:11.616 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:11.720 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:13.435 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:13.435 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:13.435 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:13.435 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:13.435 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:13.435 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:14.599 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:15.464 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:15.740 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:19.438 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:19.439 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:19.439 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:19.439 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:19.439 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2011-04-15 18:45:19.439 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2011-04-15 18:45:19.515 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:21.556 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:21.816 MSocketDevice::close: Closed socket 32
2011-04-15 18:45:50.338 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.339 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:45:50.339 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.339 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:45:50.339 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.339 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:45:50.340 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.340 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:45:50.340 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.340 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:45:50.341 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.341 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:45:50.341 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.341 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:45:50.342 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.343 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:45:50.343 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.343 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:45:50.343 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.343 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:45:50.346 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:45:50.346 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:50:50.605 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.616 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:50:50.623 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.623 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:50:50.623 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.623 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:50:50.623 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.624 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:50:50.624 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.624 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:50:50.624 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.624 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:50:50.624 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.624 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:50:50.625 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.625 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:50:50.625 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.625 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:50:50.625 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.625 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:50:50.625 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:50:50.626 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:55:50.873 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.873 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 18:55:50.873 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.873 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 18:55:50.873 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.874 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 18:55:50.874 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.874 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 18:55:50.875 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.875 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 18:55:50.875 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.875 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 18:55:50.875 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.876 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 18:55:50.876 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.877 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 18:55:50.877 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.877 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 18:55:50.877 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.878 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 18:55:50.878 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:55:50.878 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
2011-04-15 18:57:57.836 ===============================================================================
2011-04-15 18:57:57.836  URI (type) - Found: 16 Entries - 16 have been Allocated. 
2011-04-15 18:57:57.836    		USN (unique id)		 | Expires	 | Location
2011-04-15 18:57:57.851 -------------------------------------------------------------------------------
2011-04-15 18:57:57.851 upnp:rootdevice
2011-04-15 18:57:57.851  * 		uuid:43e1a419-85fa-48ce-989f-2832f85850a8::upnp:rootdevice	 | 2038	 | [http://10.0.2.13:6547/getDeviceDesc](http://10.0.2.13:6547/getDeviceDesc) 
2011-04-15 18:57:57.859  * 		uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice	 | 1830	 | [http://10.0.2.10:6547/getDeviceDesc](http://10.0.2.10:6547/getDeviceDesc) 
2011-04-15 18:57:57.860  * 		uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.860  
2011-04-15 18:57:57.860 urn:schemas-microsoft-com:service:OSInfo:1
2011-04-15 18:57:57.860  * 		uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.860  
2011-04-15 18:57:57.860 urn:schemas-mythtv-org:service:MythTv:1
2011-04-15 18:57:57.860  * 		uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-mythtv-org:service:MythTv:1	 | 2038	 | [http://10.0.2.13:6547/getDeviceDesc](http://10.0.2.13:6547/getDeviceDesc) 
2011-04-15 18:57:57.860  * 		uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1	 | 1830	 | [http://10.0.2.10:6547/getDeviceDesc](http://10.0.2.10:6547/getDeviceDesc) 
2011-04-15 18:57:57.860  
2011-04-15 18:57:57.860 urn:schemas-upnp-org:device:InternetGatewayDevice:1
2011-04-15 18:57:57.860  * 		uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.860  
2011-04-15 18:57:57.860 urn:schemas-upnp-org:device:MediaRenderer:1
2011-04-15 18:57:57.860  * 		uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:device:MediaRenderer:1	 | 2038	 | [http://10.0.2.13:6547/getDeviceDesc](http://10.0.2.13:6547/getDeviceDesc) 
2011-04-15 18:57:57.861  * 		uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1	 | 1830	 | [http://10.0.2.10:6547/getDeviceDesc](http://10.0.2.10:6547/getDeviceDesc) 
2011-04-15 18:57:57.861  
2011-04-15 18:57:57.862 urn:schemas-upnp-org:device:WANConnectionDevice:1
2011-04-15 18:57:57.862  * 		uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.862  
2011-04-15 18:57:57.862 urn:schemas-upnp-org:device:WANDevice:1
2011-04-15 18:57:57.862  * 		uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.862  
2011-04-15 18:57:57.862 urn:schemas-upnp-org:service: WANDSLLinkConfig:1
2011-04-15 18:57:57.862  * 		uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.862  
2011-04-15 18:57:57.862 urn:schemas-upnp-org:service:ConnectionManager:1
2011-04-15 18:57:57.862  * 		uuid:43e1a419-85fa-48ce-989f-2832f85850a8::urn:schemas-upnp-org:service:ConnectionManager:1	 | 2038	 | [http://10.0.2.13:6547/getDeviceDesc](http://10.0.2.13:6547/getDeviceDesc) 
2011-04-15 18:57:57.862  * 		uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1	 | 1830	 | [http://10.0.2.10:6547/getDeviceDesc](http://10.0.2.10:6547/getDeviceDesc) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
2011-04-15 18:57:57.863  * 		uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 urn:schemas-upnp-org:service:WANPPPConnection:1
2011-04-15 18:57:57.863  * 		uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 uuid:43e1a419-85fa-48ce-989f-2832f85850a8
2011-04-15 18:57:57.863  * 		uuid:43e1a419-85fa-48ce-989f-2832f85850a8	 | 2038	 | [http://10.0.2.13:6547/getDeviceDesc](http://10.0.2.13:6547/getDeviceDesc) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
2011-04-15 18:57:57.863  * 		uuid:442f2812-238e-47b4-8ebc-de7e18c0150f	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
2011-04-15 18:57:57.863  * 		uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388	 | 1830	 | [http://10.0.2.10:6547/getDeviceDesc](http://10.0.2.10:6547/getDeviceDesc) 
2011-04-15 18:57:57.863  
2011-04-15 18:57:57.863 uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
2011-04-15 18:57:57.864  * 		uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.864  
2011-04-15 18:57:57.864 uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
2011-04-15 18:57:57.864  * 		uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472	 | 1673	 | [http://10.0.2.1:2869/upnp/dslppp.xml](http://10.0.2.1:2869/upnp/dslppp.xml) 
2011-04-15 18:57:57.864  
2011-04-15 18:57:57.864 -------------------------------------------------------------------------------
2011-04-15 18:57:57.864  Found: 21 Entries - 21 have been Allocated. 
2011-04-15 18:57:57.864 ===============================================================================
2011-04-15 18:58:27.320 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.321 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:58:27.493 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.493 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::upnp:rootdevice
Cache  =max-age=3600
2011-04-15 18:58:27.493 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.494 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:58:27.666 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.666 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388
Cache  =max-age=3600
2011-04-15 18:58:27.667 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.667 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:58:27.692 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.693 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2011-04-15 18:58:27.693 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.693 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:58:27.746 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.746 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2011-04-15 18:58:27.747 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.747 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 18:58:27.932 MSocketDevice::close: Closed socket 32
2011-04-15 18:58:27.932 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 18:58:27.932 SSDP::ProcessNotify ...
DescURL=http://10.0.2.10:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:6c2d9c1b-a023-4909-809f-7b7ec895a388::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2011-04-15 19:00:51.155 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.155 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::upnp:rootdevice
Cache  =max-age=1800
2011-04-15 19:00:51.155 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.155 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8
Cache  =max-age=1800
2011-04-15 19:00:51.155 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.156 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age=1800
2011-04-15 19:00:51.156 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.156 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-microsoft-com:service:OSInfo:1
USN    =uuid:8c929c5f-28f3-478c-ae2d-00507f2608f8::urn:schemas-microsoft-com:service:OSInfo:1
Cache  =max-age=1800
2011-04-15 19:00:51.156 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.156 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f
Cache  =max-age=1800
2011-04-15 19:00:51.156 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.156 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age=1800
2011-04-15 19:00:51.157 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.157 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:442f2812-238e-47b4-8ebc-de7e18c0150f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age=1800
2011-04-15 19:00:51.157 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.157 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472
Cache  =max-age=1800
2011-04-15 19:00:51.158 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.158 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age=1800
2011-04-15 19:00:51.158 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.158 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service: WANDSLLinkConfig:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service: WANDSLLinkConfig:1
Cache  =max-age=1800
2011-04-15 19:00:51.158 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2011-04-15 19:00:51.158 SSDP::ProcessNotify ...
DescURL=http://10.0.2.1:2869/upnp/dslppp.xml
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANPPPConnection:1
USN    =uuid:f68988d9-b7e6-4c7e-b805-cd9d76c37472::urn:schemas-upnp-org:service:WANPPPConnection:1
Cache  =max-age=1800
```

---

