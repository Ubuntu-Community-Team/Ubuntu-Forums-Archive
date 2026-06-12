---
title: "Network monitoring tool on sudo machines"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by vk_rams on 2010-07-31
Here is my scenario. I have 100 ubuntu machines and I am sudoer (super user) of those machines. I am not the root user of the network and I dont have the access to routers. I have full access on those 100 machines.

The problem is I would like to know the system health, uptime, ram resources etc., all at once at one shot in a webpage. currently I am checking each and every machine individually by SSH on those machines. Please suggest me any open source tool to achieve the below things

[LIST]
[*]RAM Used Vs Free
[*]Total Uptime
[*]Number of Java Instances
[*]Checking a Speifice daemon is running
[*]How many machines are pingabble
[/LIST]

Looking for a good solution. I tried using Nagios, But unable to confiure it may be it requires root user of the network, which I am not

Thanks in Advance
Vik

---

### Post by linux18 on 2010-07-31
maybe a shell script?

---

### Post by vk_rams on 2010-08-01
I think i need to ssh in to 100 machine before getting the resource information. Is there a way to get system resource information without ssh?

---

### Post by linux18 on 2010-08-01
have a cron job run and collect all of the data you need and dump it to a file, then have the machines send you the file and cat them all together. Then you just have one large file to scroll through.

---

