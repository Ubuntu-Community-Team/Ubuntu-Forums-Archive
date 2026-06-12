---
title: "Make bulk changes using APIs"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Serverperformer on 2010-02-15
You can make bulk changes to the devices using the API
 
[LIST=1]
[*]Ensure that the BVE API is running (from the Traverse Controller in    Windows or etc/bveapi.init start on Unix)
[*]From a Windows command prompt or a Unix shell (type the following commands):
  telnet localhost 7661
login zyrion zyrion
Device.List "deviceName=*"
Test.List "deviceName=xyz", "testName=*"
Test.Suspend "testName=VirtMemUsed", "deviceName=compaq*"

Device.delete "deviceName=*"
Quit
[/LIST]

---

