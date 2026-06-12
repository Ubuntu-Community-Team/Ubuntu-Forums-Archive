---
title: "Banshee crash"
date: 2015-12-06
forum: Multimedia Software
---

### Post by AC1969 on 2015-12-06
Hi,
I am using Ubuntu 15.10, 64 bit, and running Banshee 2.6.2.
All work fine for some time, but then suddenly it crahes, with the below log messages.
It did happen in the middle of a song, after running fine for approx 20 minutes.
My music collection is on a mounted (NFS) NAS drive.

```
Unhandled Exception:
Mono.Upnp.UpnpDeserializationException: The type description version number could not be parsed: 6b.
  at Mono.Upnp.TypeInfo.Parse (System.String typeDescription, System.String& domainName, System.String& type, System.Version& version) [0x00000] in <filename unknown>:0 
  at Mono.Upnp.DeviceType.Parse (System.String deviceType) [0x00000] in <filename unknown>:0 
  at Mono.Upnp.Client.ClientServiceEvent (Mono.Ssdp.ServiceArgs args, System.Action`1 deviceHandler, System.Action`1 serviceHandler) [0x00000] in <filename unknown>:0 
  at Mono.Upnp.Client.ClientServiceRemoved (System.Object sender, Mono.Ssdp.ServiceArgs args) [0x00000] in <filename unknown>:0 
  at Mono.Ssdp.Client.OnServiceRemoved (System.String usn) [0x00000] in <filename unknown>:0 
  at Mono.Ssdp.Client.CacheServiceRemoved (System.String usn) [0x00000] in <filename unknown>:0 
  at Mono.Ssdp.Internal.ServiceCache.Remove (System.String usn, Boolean fromTimeout) [0x00000] in <filename unknown>:0 
  at Mono.Ssdp.Internal.ServiceCache.TimeoutHandler (System.Object state, System.TimeSpan& interval) [0x00000] in <filename unknown>:0 
  at Mono.Ssdp.Internal.TimeoutDispatcher.TimerThread (System.Object state) [0x00000] in <filename unknown>:0 


```

Any advise on what this could cause, and how to fix it?

PS. The full log file is 30KB, exceeding the 19.5KB site limit. I will attach it in compressed format.
[ATTACH]266004[/ATTACH]
Thanks,
Arnaud

---

