---
title: "Syncrhonizing 3 Servers over IP"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by fkasmani on 2012-10-18
Hello,

I'm setting up a medical server for a hospital that has doctors located  in 3 different locations, meaning there would be 3 servers (1 in each  location). All 3 servers would just have the following software:
[LIST]
[*]Ubuntu Server 12.04 minimal
[*]MySQL, PHP 5, Apache
[*]The medical software which would read/write to the MySQL database
[*]Remote admin apps like Nagios & Webmin
[*]Rsync for backup (rsync-over-ssh) as a cron job
[/LIST]
and the doctors at each location would access patient & billing data from their respective servers.

What I'd like is, that each of these servers all have synchronized info  (especially the mySQL database's) - let's say on an hourly basis each of  these servers synchronize data to a common remote server and the data  is then brought down to each of the servers.

I know an easier way would be to have the medical app running on a  remote web server, but since this is medical that we're talking about  and knowing how common it is in our area for the net to go gown, I  wouldn't like a web based scenatio.

Is such a setup possible?
Would this be the right way to do things or is there a better way to this?

Would really appreciate views and comments (or how to set this up) on this.

---

### Post by fkasmani on 2012-10-19
Just some extra info:
I'm looking at something similar to what I've drawn at [i49.tinypic.com/2lm0xnq.png]("http://i49.tinypic.com/2lm0xnq.png") 
 So maybe on an hourly basis there's a cron-job (from each of the nodes) doing an rsync-over-ssh  to the server in the data center and then it's brought down to each  node. Each doctor at each site will have a different mySQL database  dedicated to his practice,but at the end of it all, all 3 servers have  the same data.

---

### Post by papibe on 2012-10-19
Hi fkasmani.

Please take this with a grain of salt, as although I use rsync extensively, I don't consider myself much of an expert on MySQL.

IMHO rsync is not the right tool to sync the databases for the following reasons:
[LIST]
[*]A database can not be safely copied/rsynced unless is stopped. You'll risk getting a corrupted copy if you rsync over a live database.
[*]rsync won't be very efficient since you don't need file replication, but content replication (i.e., as in INSERTS, REPLACE, etc).
[/LIST]
Even if you take a bit safer approach as to make a dump (using mysqldump) and sync that, I think wouldn't be practical to rsync the whole dump.

The last rsync trick I can think of would be to rsync only the binary logs. That way you would be transferring only the changes. Once on the server you could apply the changes to the data center database.

**Nevertheless**, I think the best solution would be to consider using proper MySQL replication features. There are some advance techniques that you might look into. 'Circular Replication' comes to mind.

I hope this points you in the right direction.
Regards.

---

### Post by fkasmani on 2012-10-19
> **papibe said:**
> Hi fkasmani.

Please take this with a grain of salt, as although I use rsync extensively, I don't consider myself much of an expert on MySQL.

IMHO rsync is not the right tool to sync the databases for the following reasons:
[LIST]
[*]A database can not be safely copied/rsynced unless is stopped. You'll risk getting a corrupted copy if you rsync over a live database.
[*]rsync won't be very efficient since you don't need file replication, but content replication (i.e., as in INSERTS, REPLACE, etc).
[/LIST]
Even if you take a bit safer approach as to make a dump (using mysqldump) and sync that, I think wouldn't be practical to rsync the whole dump.

The last rsync trick I can think of would be to rsync only the binary logs. That way you would be transferring only the changes. Once on the server you could apply the changes to the data center database.

**Nevertheless**, I think the best solution would be to consider using proper MySQL replication features. There are some advance techniques that you might look into. 'Circular Replication' comes to mind.

I hope this points you in the right direction.
Regards.
Papibe, thanks for this. It's really an eye opener.

---

### Post by ahallubuntu on 2012-10-19
I've not tried syncing three separate servers and not tried syncing MySQL databases, but my initial idea would be to have one master server and database and have the other two access the MySQL server over the internet.  Yes, of course, the performance of that could be terrible.  I'm not sure how much data would be coming out of it to know.  If you have fast internet connections, though, it may be acceptable to use a single database.  Not sure, but that would greatly simplify your task.  Only one server to back up and maintain, etc.  And no sync issues.

In that scenario, you could host a VPN server on the main server and have the other two servers connect as clients to it - then the clients would get secure access to the database.

Speaking of which, no matter what you do, you need to be *VERY* careful about security when dealing with medical data.  If you are in the US (?), there are HIPAA laws to worry about, for one.  If you setup Webmin, it had better be over a private secure LAN (or over VPN) and not on a public-facing server!  Some of these management tools are cool and frighteningly easy to setup but can also be security  nightmares if not managed properly.  If you are not yourself an expert on these issues, I'd probably hire someone to audit what you are doing before you put it into place to make sure you have overlooked security issues.

---

