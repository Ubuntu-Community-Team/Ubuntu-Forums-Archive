---
title: "Can Not Connect To Subsonic Server After Recent Update"
date: 2012-05-09
forum: Multimedia Software
---

### Post by Precipitous on 2012-05-09
I use an incredible media streaming application named [Subsonic]("http://www.subsonic.org/pages/index.jsp") to stream my music collection from my home computer running Ubuntu 12.04 to my computer at work (running Windows 7). I have been using Subsonic for a few years and have always found it to be amazingly stable and configurable... 

Suddenly over the last few days I am no longer able to connect to the Subsonic server from any computer running Ubuntu 12.04. This includes trying to connect to it on the same computer it is is running on. It does not matter whether I use the local IP address, the public IP address or a registered DNS host name. The result is always the same: a generic time-out message from whatever web browser I am running. Connecting from a Windows client works perfectly... Since this just started happening a few days ago I am assuming it is because of a recent update to Ubuntu. Unfortunately I do not know where to even begin looking for the cause or solution.

Has anyone else experienced the same issue? Does anyone have an idea as to what may be going on? Any help would be greatly appreciated.

---

### Post by kostkon on 2012-05-09
Aren't there any logs you can check? Your system logs and any log files that subsonic creates.

---

### Post by Precipitous on 2012-05-10
> **kostkon said:**
> Aren't there any logs you can check? Your system logs and any log files that subsonic creates.
Unfortunately no. The Subsonic server is running fine, so its logs don't show anything. When I attempt to go to its address the web browser times out as if it were trying to go to a non-existent location. The Subsonic server does not really have anything to log...

In case it helps diagnose the problem - I ran a virtual install of Windows XP on the computer running the Subsonic server using VirtualBox, then tried to connect from within it. Unfortunately I got the same result using both the local and public IP addresses...

---

### Post by Precipitous on 2012-06-14
Problem ended up being caused by iplist/ipblock. Somehow the whitelist settings had gotten wonked....

---

