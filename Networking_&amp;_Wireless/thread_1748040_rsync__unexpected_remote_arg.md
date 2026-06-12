---
title: "rsync : unexpected remote arg"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by lowrider2025 on 2011-05-03
I'm having a problem with rsync.I'm using public/private keys for authentication.

situation:
- command is run from (server2) where backups are stored
- both the backupserver & the webserver are configured in the firewall to allow ssh communication on port 2222
- sshd_config: AllowGroups rsyncer - AllowUsers rsyncer
- rsyncer uses /bin/bash shell
- rsyncer has on server1: read rights on /usr/share/joomla15/public_html folder, on server2: write rights on /home/rsyncer/backups/joomla
- authorized_keys on server1 contains from="server2ip"

command executed on server2:
rsync -avvvz -e --progress "ssh -p 2222 -i /home/rsyncer/rsyncer.prv" rsyncer@server1:/usr/share/joomla15/public_html/xmlrpc /home/rsyncer/backups/joomla

700 /home/rsyncer - owner: rsyncer:rsyncer
700 /home/rsyncer/.ssh - owner: rsyncer:rsyncer
600 /home/rsyncer/.ssh/authorized_keys - owner: rsyncer:rsyncer

gives the following error:
unexpected remote arg: rsyncer@server1:/usr/share/joomla15/public_html/xmlrpc
rsync error: syntax or usage error (code 1) at main.c(1222) [sender=3.0.7]

Could someone tell me what also to lookout for ?

Thanx

---

### Post by lowrider2025 on 2011-05-03
just found the solution browsing the net. You have to specify the user in the ssh statement. This works:
rsync -avvvz -e "ssh -p 2222 -i /home/rsyncer/rsyncer.prv **-l rsyncer**" rsyncer@server1:/usr/share/joomla15/public_html/xmlrpc /home/rsyncer/backups/joomla

---

