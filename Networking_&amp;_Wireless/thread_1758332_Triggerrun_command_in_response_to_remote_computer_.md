---
title: "Trigger/run command in response to remote computer ping/packet/request"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by ephestione on 2011-05-14
Scenario: I have a ubuntu server, to which I want to send backups from my Win7 machine through rsnapshot. I configured the cwrsync server on windows already, BUT, while I currently trigger backups locally via CobianBackup and send them to a samba share on the server (the server is always on anyway), by running rsnapshot on the server through crontab, I would risk that the windows 7 machine is turned off in that moment.

So somehow I need the windows machine to "call" the ubuntu server telling it's awake, and trigger it into running rsnapshot, so then finally windows can act as rsync server.
I thought about using the system/exec commands in PHP trough Apache (then wget said php file from windows), but then I would be running the command as www-data, and that's not good.
I also don't want to write the credentials in clear either to use a single ssh command from windows, nor inside the PHP to run system() with the correct user's privileges.

So, unless I am missing an alternative route (I also thought about watching a samba folder, and have windows create a file in that folder, as soon as the file is created the command is executed, then crontab deletes the file at midnight... but it's WAY too far fetched... or have a bash script check via ping if windows is reachable and only then run rsnapshot, but then I would need to run said script quite often until it finds the pc reachable, and after that make sure it does't repeat again for that day), is there a way to achieve what I'm looking for?

I am at my wit's end, at least for the upcoming 30 minutes :D

---

