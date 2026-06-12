---
title: "Monitoring Multiple Nagios Machines on a single Browser Page"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-04
Hello,

I've installed Nagios on all 3 of my Ubuntu 12.04 Servers.  I monitor them from my Ubuntu 12.04 Desktop (or any computer with a browser).  But in order to monitor all 3 of them I have to open 3 browser windows with http://<ipaddress1>/nagios - http://<ipaddress2>/nagios - http://<ipaddress3>/nagios.  I tested out NRPE with another system and got it running on the 'monitored' Nagios machine.  But when I look at the browser page it only shows my localhost.  Not the 'monitored' machine as well.  
For my set up here is there a way to monitor servers 1-3 on the same Nagios browser page on my desktop?  I keep getting routed back to NRPE but it seems more like I'm just getting access to whether or not NRPE is installed on the remote machine...rather than actual data feedback from the remote machines.  I hope that explains it well...I want to be able to monitor 3 servers running Nagios on one browser from my desktop using the convention http://<ipaddress 1-3>/nagios.

---

### Post by tgalati4 on 2013-01-04
Is there a way to show two webpages in the same tab in any browser?  I think not.  HTTP only allows one URL per tab, so how could you have 3 different URL's be displayed in a single tab?  Perhaps there is a firefox plug-in; that would require a search.  Chrome, Firefox, and Opera have a dashboard with thumbnails, so you could set up 3 across.  It provides a quick graphical cue (red, yellow, green bars) then you can click the page to get the full view.  Firefox allows separate windows which you can then resize to 3 across.  Chrome allows you to "rip" tabs off into separate windows, which you can then resize into a panel of 3.

If all 3 servers are 24/7 then perhaps you could have one server send it's nagios data to the second server, then that server send it to the third, then monitor just the 3rd server which would have the data from all three.  

You could write a fancy script using curl to "scrape" the data from all three nagios servers and format them into a single, local HTML page in /tmp and browse that.  Perform the survey every so often.

Another option is to modify one nagios server so that its status page contains frames of the other two servers--sort of like serving up advertisements to yourself, except they would be the other two nagios dumps.

I use rwho/rwhod and ruptime to monitor several servers at once:

tgalati4@Dell600m-mint14 ~ $ apt-cache search ruptime
rwho - Clients to query the rwho server
rwhod - System status server

tgalati4@tubuntu2:~$ ruptime
Dell600m-min  up    1+03:36,     1 user,   load 1.13, 0.51, 0.44
jarhead1    down       4:12
minty4      down    9+01:55
tubuntu2      up   32+02:36,     0 users,  load 0.17, 0.17, 0.11

I wrote a zenity script that has an icon on my panel that gives this info.  You could modify the script to add a nagios link for each server.  Although if the server is down, nagios won't help much.

If you have your SMART monitor and thermal/fan monitors set to send smtp messages and some sort of uptime monitor (like rwho), what more would you need?  

All linux machines can send syslog messages to another machine.  So you could send messages to one server and poll that syslog periodically for error conditions.  That's handy for UPS's as well.

---

### Post by psyllex on 2013-01-04
> **tgalati4 said:**
> Is there a way to show two webpages in the same tab in any browser?  I think not.  HTTP only allows one URL per tab, so how could you have 3 different URL's be displayed in a single tab?  

Well I wasn't suggesting that I have 3 URL's in one browser page, that's ridiculous...what I meant was simply that I wanted the data from those 3 URLS to be displayed...in whatever format in one central location so I can view all 3 servers on a single HMTL page.  Nagios seems to be set up to handle this.  I think I may have found a way to do this I just need to do a lot with the definitions and configuration files; changing the hosts definitions and the services definitions.   I also need to do some changes to my group configurations.  My end game will be a very low latency graph of the services I'm monitoring; tracking bandwidth, latency and packetloss.  I'm going to mess with it a bit tonight and see if I can't get it working.  
Your solutions look interesting.  Initially I planned on writing some scripts to scrape data from all servers, but it looked as though Nagios already beat me there with some of their plugins.  But if my solution ends up sucking....I'll take some of your advice and see how that works.  Thanks for the pointers.

---

### Post by tgalati4 on 2013-01-05
The beauty of linux is that there are usually 10 ways to do something.  The challenge is to find the most elegant method.  For that, the forums can help.  Post some screenshots of your efforts.  My nagios setups are pretty basic and good for historical analysis, but I'm sure there are better real-time monitors.

For instance you could use a script that remotely logs into your systems and runs inotify for specific events: (set up SSL keys to allow passwordless authentication).

ssh admin@server1 netstat --timers | grep tcp
ssh admin@server2 netstat --timers | grep tcp
.
.
.

tgalati4@Dell600m-mint14 ~ $ netstat --timers | grep tcp
tcp       13      0 Dell600m-mint14.l:44949 freenas:netbios-ssn     CLOSE_WAIT  off (0.00/0/0)
tcp        8      0 Dell600m-mint14.l:45413 freenas:microsoft-ds    ESTABLISHED off (0.00/0/0)
tcp        8      0 localhost:39456         Dell600m-mi:netbios-ssn ESTABLISHED off (0.00/0/0)
tcp        0      0 Dell600m-mi:netbios-ssn localhost:39456         ESTABLISHED keepalive (6413.47/0/0)

I find that nagios has a lot of overhead for real-time statistics.  Data that is already available in several places within the kernel space--you just have to find it.

---

### Post by psyllex on 2013-01-08
> **tgalati4 said:**
> The beauty of linux is that there are usually 10 ways to do something.  The challenge is to find the most elegant method.  For that, the forums can help.  Post some screenshots of your efforts.  My nagios setups are pretty basic and good for historical analysis, but I'm sure there are better real-time monitors.

For instance you could use a script that remotely logs into your systems and runs inotify for specific events: (set up SSL keys to allow passwordless authentication).

ssh admin@server1 netstat --timers | grep tcp
ssh admin@server2 netstat --timers | grep tcp
.
.
.

tgalati4@Dell600m-mint14 ~ $ netstat --timers | grep tcp
tcp       13      0 Dell600m-mint14.l:44949 freenas:netbios-ssn     CLOSE_WAIT  off (0.00/0/0)
tcp        8      0 Dell600m-mint14.l:45413 freenas:microsoft-ds    ESTABLISHED off (0.00/0/0)
tcp        8      0 localhost:39456         Dell600m-mi:netbios-ssn ESTABLISHED off (0.00/0/0)
tcp        0      0 Dell600m-mi:netbios-ssn localhost:39456         ESTABLISHED keepalive (6413.47/0/0)

I find that nagios has a lot of overhead for real-time statistics.  Data that is already available in several places within the kernel space--you just have to find it.

Thanks for that suggestion.   I'll keep something like that in mind.  I'm checking 22 machines (once I'm all set up) so I'm not entirely sure checking each one would be time efficient but I'll definitely give a good test.  

I currently found the answer to my question initially.  I didn't bridge the NAT with my VM which is why the NRPE Server was saying the machine was down.  So I switched that within settings in VM Workstation and then threw the new IP address within the command configuration files and I was good to go. I'll throw up some of my notes from install NRPE Server and the plug-ins just in case they can be of use to anyone.  Thanks for all the help.

---

