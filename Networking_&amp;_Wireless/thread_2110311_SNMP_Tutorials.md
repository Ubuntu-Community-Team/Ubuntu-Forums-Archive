---
title: "SNMP Tutorials"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-29
Does anyone know of any good SNMP tutorials?  I've used everything from PRTG, MRTG (I don't even remember how I found that considering it's ol), SolarWind, bmon, ifstat, iptrap, speedometer, ntop, top, atop, etc.  But I need something a little more customized, I'm working on making my own realtime graphs, but I need to tap into SNMP and the MIBS to really get what I need.  But 9 of the last 10 tutorials I went through really were not good, most were made by a company that does monitoring already like ManageEngine or Cacti's tutorial.  

DOes anyone have any ideas? :popcorn:

---

### Post by jonobr on 2013-01-30
Hello

Im a bit confused about the request, whether its a question about recommendations of software (you menion most of the ones recommended by forum members) or an understanding of how SNMP works.

I guess you are polling mibs and are able to extract the information from the target device that you need using either V1 V2 or V3.

Once you know what target Mib your looking for then you would usually pop that mib into say MRTG or manageengine to monitor that mib on a given interval.

So again, I am hoping you can clarify the question,
is it that you dont know how to get the mibs,
you dont know what mibs to look for , your mib polling is not working or you want to monitor a specifc Mib but are having trouble defining it in the software.

---

### Post by psyllex on 2013-01-30
> **jonobr said:**
> Hello

Im a bit confused about the request, whether its a question about recommendations of software (you menion most of the ones recommended by forum members) or an understanding of how SNMP works.

I guess you are polling mibs and are able to extract the information from the target device that you need using either V1 V2 or V3.

Once you know what target Mib your looking for then you would usually pop that mib into say MRTG or manageengine to monitor that mib on a given interval.

So again, I am hoping you can clarify the question,
is it that you dont know how to get the mibs,
you dont know what mibs to look for , your mib polling is not working or you want to monitor a specifc Mib but are having trouble defining it in the software.

I hope I can clarify the question too!  I was asking if anyone knew of any tutorials that basically are in depth and walk one through the process of choosing which MIBS for what information etc.  At this point I've scanned over the list of MIBS but since I truly do not know what I'm looking at or for, this is what I need help with.  I understand SNMP to a point, enough to set up the conf files and get it running for Cacti.  But beyond that it's all a mystery.  I've gotten the SNMP book from O'reily, the Cacti 0.8 book as a section on SNMP in it, but I tend to do better with walkthrough tutorials so that was why I was asking.

---

### Post by jonobr on 2013-01-30
Hello


Its tricky when you dont know what your looking for and you need to find them but they are all gobbly gook.

What I recommend is search oids in the company of the target device.

EG [Cisco]("http://tools.cisco.com/Support/SNMP/do/BrowseMIB.do?local=en&step=2") do a good job of outlining their mibs.

Its been a while since I dealt with opmanager from manageengine ( you mentioned those guys) but you could get the MIB inform from the vendor, load it into your MIB walker and you could lcick on them and see what they did , some are obvious in their names, and some not so.

Again, if you could let us know what you need to poll, and the device your polling maybe i could help

---

