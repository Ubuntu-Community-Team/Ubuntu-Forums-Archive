---
title: "New frontend hanging"
date: 2008-06-01
forum: Mythbuntu
---

### Post by yonkiman on 2008-06-01
Hi,

I've been running mythbuntu 8.04 successfully on a PC for weeks.  I'm now trying to get a new front end (my AppleTV) to talk to it.  I config'ed the ATV frontend to look at the PC's IP address (192.168.1.104), gave it the MySQL password, etc.  But when I launch the front end on the ATV, it hangs here:

user@atvmythbuntu:~$ mythfrontend.real
2008-06-01 12:01:09.492 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 12:01:10.043 XScreenSaver support enabled
2008-06-01 12:01:10.044 DPMS is active.
2008-06-01 12:01:10.060 **Empty LocalHostName.**
2008-06-01 12:01:10.060 **Using localhost value of atvmythbuntu**
2008-06-01 12:01:10.061 Testing network connectivity to 192.168.1.104
2008-06-01 12:01:10.138 New DB connection, total: 1

I can ping 192.168.1.104 and it's there.  Maybe it's a problem with "**Empty LocalHostName.**"?  Since the frontend doesn't launch anymore I don't know how to get into the config menu to debug...

Any ideas?

---

### Post by superm1 on 2008-06-01
> **yonkiman said:**
> Hi,

I've been running mythbuntu 8.04 successfully on a PC for weeks.  I'm now trying to get a new front end (my AppleTV) to talk to it.  I config'ed the ATV frontend to look at the PC's IP address (192.168.1.104), gave it the MySQL password, etc.  But when I launch the front end on the ATV, it hangs here:

user@atvmythbuntu:~$ mythfrontend.real
2008-06-01 12:01:09.492 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 12:01:10.043 XScreenSaver support enabled
2008-06-01 12:01:10.044 DPMS is active.
2008-06-01 12:01:10.060 **Empty LocalHostName.**
2008-06-01 12:01:10.060 **Using localhost value of atvmythbuntu**
2008-06-01 12:01:10.061 Testing network connectivity to 192.168.1.104
2008-06-01 12:01:10.138 New DB connection, total: 1

I can ping 192.168.1.104 and it's there.  Maybe it's a problem with "**Empty LocalHostName.**"?  Since the frontend doesn't launch anymore I don't know how to get into the config menu to debug...

Any ideas?
Wipe your ~/.mythtv/config.xml and ~/.mythtv/mysql.txt and give it one more run.

If it still doesn't go, then try mythfrontend.real -v all

---

### Post by yonkiman on 2008-06-02
> **superm1 said:**
> Wipe your ~/.mythtv/config.xml and ~/.mythtv/mysql.txt and give it one more run.

Same result...

> If it still doesn't go, then try mythfrontend.real -v all

It still hung - I'll try it again tonight and post the log.

---

### Post by yonkiman on 2008-06-07
> **superm1 said:**
> Wipe your ~/.mythtv/config.xml and ~/.mythtv/mysql.txt and give it one more run.

If it still doesn't go, then try mythfrontend.real -v all

Thanks for the suggestions!  I tried deleting the files; it failed the same way.  It fails with "mythfrontend.real -v all", here's the results of that command:

```
2008-06-06 22:22:24.369 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-06 22:22:24.369 UPnp - Constructor
2008-06-06 22:22:24.369 MediaRenderer::Begin
2008-06-06 22:22:24.370 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2008-06-06 22:22:24.371 HttpServer( 6547 ) - SharePath = /usr/share/mythtv/
2008-06-06 22:22:24.371 UPnp::Initialize - Begin
2008-06-06 22:22:24.371 UPnp::Initialize - Starting TaskQueue
2008-06-06 22:22:24.371 UPnp::Initialize - Creating SSDP Thread at port 6547
2008-06-06 22:22:24.372 UPnp::Initialize - End
2008-06-06 22:22:24.372 MediaRenderer::Creating UPnp Description
2008-06-06 22:22:24.372 MediaRenderer::Registering CMGR Service.
2008-06-06 22:22:24.373 UPnp::Start - Starting SSDP Thread (Multicast)
2008-06-06 22:22:24.373 UPnp::Start - Enabling Notifications
2008-06-06 22:22:24.373 SSDP::EnableNotifications() - creating new task
2008-06-06 22:22:24.373 SSDP::EnableNotifications() - sending NTS_byebye
2008-06-06 22:22:24.373 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
2008-06-06 22:22:24.374 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.374 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::upnp:rootdevice
Cache  =max-age=3600
2008-06-06 22:22:24.508 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.509 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::upnp:rootdevice
Cache  =max-age=3600
2008-06-06 22:22:24.509 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.510 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
Cache  =max-age=3600
2008-06-06 22:22:24.657 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.657 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
Cache  =max-age=3600
2008-06-06 22:22:24.658 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.658 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-06 22:22:24.869 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.869 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-06 22:22:24.870 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.870 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-06 22:22:24.887 SSDP::EnableNotifications() - sending NTS_alive
2008-06-06 22:22:24.887 SSDP::EnableNotifications() - Task added to UPnP queue
2008-06-06 22:22:24.887 UPnp::Start - Returning
2008-06-06 22:22:24.888 MediaRenderer::End
2008-06-06 22:22:24.893 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.894 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-06 22:22:24.907 XScreenSaver support enabled
2008-06-06 22:22:24.908 DPMS is active.
2008-06-06 22:22:24.909 Empty LocalHostName.
2008-06-06 22:22:24.909 Using localhost value of atvmythbuntu
2008-06-06 22:22:24.910 MCP::DefaultUPnP() - No default UPnP backend
2008-06-06 22:22:24.910 Testing network connectivity to 192.168.1.104
2008-06-06 22:22:24.917 MythSocket(82b2050:11): new socket
2008-06-06 22:22:24.917 MythSocket(82b2050:11): attempting connect() to (192.168.1.104:6543)
2008-06-06 22:22:24.918 MythSocket(82b2050:11): state change Idle -> Connected
2008-06-06 22:22:24.918 MythSocket(82b2050:11): state change Connected -> Idle
2008-06-06 22:22:24.939 New DB connection, total: 1
2008-06-06 22:22:24.973 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:24.974 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::upnp:rootdevice
Cache  =max-age=3600
2008-06-06 22:22:25.148 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.149 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::upnp:rootdevice
Cache  =max-age=3600
2008-06-06 22:22:25.149 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.150 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
Cache  =max-age=3600
2008-06-06 22:22:25.377 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.378 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98
Cache  =max-age=3600
2008-06-06 22:22:25.378 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.379 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-06 22:22:25.554 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.555 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-06 22:22:25.555 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.556 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-06 22:22:25.681 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:25.682 SSDP::ProcessNotify
DescURL=http://192.168.1.105:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:c5f7caeb-c55d-4ec9-a6b6-39d0d1e8cd98::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-06 22:22:47.679 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.680 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:13814000-1dd2-11b2-9fff-0016b6a7924f::upnp:rootdevice
Cache  =max-age = 126
2008-06-06 22:22:47.681 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.681 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =uuid:13814000-1dd2-11b2-9fff-0016b6a7924f
USN    =uuid:13814000-1dd2-11b2-9fff-0016b6a7924f
Cache  =max-age = 126
2008-06-06 22:22:47.682 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.682 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:InternetGatewayDevice:1
USN    =uuid:13814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:device:InternetGatewayDevice:1
Cache  =max-age = 126
2008-06-06 22:22:47.683 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.683 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:Layer3Forwarding:1
USN    =uuid:13814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:service:Layer3Forwarding:1
Cache  =max-age = 126
2008-06-06 22:22:47.685 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.685 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =uuid:23814000-1dd2-11b2-9fff-0016b6a7924f
USN    =uuid:23814000-1dd2-11b2-9fff-0016b6a7924f
Cache  =max-age = 126
2008-06-06 22:22:47.686 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.686 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANDevice:1
USN    =uuid:23814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:device:WANDevice:1
Cache  =max-age = 126
2008-06-06 22:22:47.687 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.687 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
USN    =uuid:23814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1
Cache  =max-age = 126
2008-06-06 22:22:47.689 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.689 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =uuid:33814000-1dd2-11b2-9fff-0016b6a7924f
USN    =uuid:33814000-1dd2-11b2-9fff-0016b6a7924f
Cache  =max-age = 126
2008-06-06 22:22:47.690 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.690 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:WANConnectionDevice:1
USN    =uuid:33814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:device:WANConnectionDevice:1
Cache  =max-age = 126
2008-06-06 22:22:47.691 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.692 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANEthernetLinkConfig:1
USN    =uuid:33814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:service:WANEthernetLinkConfig:1
Cache  =max-age = 126
2008-06-06 22:22:47.692 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-06 22:22:47.693 SSDP::ProcessNotify
DescURL=http://192.168.1.1:2869/IGatewayDeviceDescDoc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:WANIPConnection:1
USN    =uuid:33814000-1dd2-11b2-9fff-0016b6a7924f::urn:schemas-upnp-org:service:WANIPConnection:1
Cache  =max-age = 126
```

I just don't know enough linux to have a clue...

---

### Post by yonkiman on 2008-06-07
OK, looking around I found one very important thing I forgot to do:  You need to run MythTV Setup (the backend server setup) on the backend PC.  On the first screen (I think) of "General", you need to change the IP addresses from the default loopback address of 127.0.0.1 (or something like that) to the actual IP address of the backend server (in my case, 192.168.1.104).

I was SURE that would do it, but it didn't.  When I run Mythbuntu Control Centre/MythTV Configuration and click on "Test MySQL Connection", I get "Failure".  When I try to launch the front end, it hangs again.

I also read recommendations that you need to comment out the "bind-address" line in /etc/mysql/conf.d/mythtv.cnf and /etc/mysql/my.cnf.  I did that, too, but to no avail...

Looking at the logfile, it doesn't even seem to get as far before hanging as it did BEFORE these changes.  Here's the log:

```
mythfrontend.real -v all
2008-06-06 23:36:04.307 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-06 23:36:04.307 UPnp - Constructor
2008-06-06 23:36:04.307 MediaRenderer::Begin
**QServerSocket: failed to bind or listen to the socket**
2008-06-06 23:36:04.308 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2008-06-06 23:36:04.308 HttpServer( 6547 ) - SharePath = /usr/share/mythtv/
2008-06-06 23:36:04.308 MediaRenderer::HttpServer Create Error
2008-06-06 23:36:04.308 WorkerThread:Run - Exiting: HTTP_WorkerThread
2008-06-06 23:36:04.385 XScreenSaver support enabled
2008-06-06 23:36:04.385 DPMS is active.
2008-06-06 23:36:04.479 Empty LocalHostName.
2008-06-06 23:36:04.479 Using localhost value of atvmythbuntu
2008-06-06 23:36:04.480 MCP::DefaultUPnP() - No default UPnP backend
2008-06-06 23:36:04.480 Testing network connectivity to 192.168.1.104
2008-06-06 23:36:04.534 MythSocket(82ae810:7): new socket
2008-06-06 23:36:04.535 MythSocket(82ae810:7): attempting connect() to (192.168.1.104:6543)
2008-06-06 23:36:04.536 MythSocket(82ae810:7): state change Idle -> Connected
2008-06-06 23:36:04.536 MythSocket(82ae810:7): state change Connected -> Idle
2008-06-06 23:36:04.617 New DB connection, total: 1

```

I highlighted the first failure: 
[INDENT]MediaRenderer::Begin
QServerSocket: failed to bind or listen to the socket
[/INDENT]
It didn't fail there an hour ago..,

Still looking...

---

### Post by dhanes420 on 2008-07-31
Hello all,

I too, have this issue.  The remote frontend is Kubuntu 8.04 and the backend is running Fedora 8 with mythtv RPMs from atrpms.

Mythfrontend.real -v all runs, then hangs at the last line of

Cache  =max-age-3600

And then every few minutes will go through the whole connecting to the UPnP backend (using the correct IP).  No errors about database, I have entered 0000 into the PIN in the backend setup, allowed the remote to access mysql on the backend.

Any ideas?

Thanx

---

### Post by lintoon on 2008-08-19
Did you get this sorted because I am having similar issues and cannot find an answer?

---

### Post by dhanes420 on 2008-08-19
> **lintoon said:**
> Did you get this sorted because I am having similar issues and cannot find an answer?
@lintoon

Nope, still haven't found an answer.  Are you running different distros for your backend and frontend too?

---

### Post by lintoon on 2008-08-19
I got mine sorted.  I stumbled on a post which suggested port 6543 was in use so I killed the backend and restarted.

On the backend system I ran:

sudo killall mythtv-backend
then 
sudo /etc/init.d/mythtv-backend start

On the remote frontend I ran

mythfrontend

This launched setup so I confirmed my settings and clicked next a few times and now I can watch TV on my laptop on the lan. I rebooted both systems and it's still working.  Fantastic.

---

