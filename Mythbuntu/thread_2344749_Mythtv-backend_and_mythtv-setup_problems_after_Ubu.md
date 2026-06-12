---
title: "Mythtv-backend and mythtv-setup problems after Ubuntu server LTS 16.04 upgrade"
date: 2016-11-28
forum: Mythbuntu
---

### Post by ransae on 2016-11-28
Hi,

Very sad news of Mythbuntu's demise. It's been good over the years. 

After years of trouble free use, here's a problem I've encountered after an LTS server upgrade. Squeezing it in before the forum's close. Hopefully someone can help.

The upgrade didn't go well. Had problems with mysql updating, which after some fluffing about, including having to reinstall the myth packages, I managed to get everything running. 

The first minor issue is that there seems to a myth upstart script lurking. When I do an update I get the following warnings:

```
[FONT=monospace][COLOR=#000000]Setting up mythtv-backend (2:0.28.0+fixes.20161125.e9d0543-0ubuntu0mythbuntu3) ...[/COLOR]
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
[/FONT]
```

The backend is starting, so the warnings are harmless, but I'd like to get rid of them. 

The second issue is more serious, and it occurs when running mythtv-setup

Before upgrading, a dialog used to appear to shut down the backend. This doesn't happen now, the setup first page appears with the option to shut down the backend. Not a problem, but it didn't do that before. I get the following terminal messages:

```
[FONT=monospace][COLOR=#000000]root@server2:/etc# mythtv-setup[/COLOR]
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
status: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
[/FONT]
```

When exiting, the setup page doesn't shut down. To exit, I have to kill the update process. 

The backend tries to start, but not cleanly. Get this status:

```
[FONT=monospace][COLOR=#000000]Nov 28 18:31:05 server2.aeran.info systemd[1]: [/COLOR][COLOR=#000000]**mythtv-backend.service: Main process exited, code=exited, status=135/n/a**[/COLOR]
Nov 28 18:31:05 server2.aeran.info systemd[1]: [COLOR=#000000]**mythtv-backend.service: Unit entered failed state.**[/COLOR]
Nov 28 18:31:05 server2.aeran.info systemd[1]: [COLOR=#000000]**mythtv-backend.service: Failed with result 'exit-code'.**[/COLOR]
Nov 28 18:31:07 server2.aeran.info systemd[1]: mythtv-backend.service: Service hold-off time over, scheduling restart.
Nov 28 18:31:07 server2.aeran.info systemd[1]: Stopped MythTV Backend.
Nov 28 18:31:07 server2.aeran.info systemd[1]: [COLOR=#000000]**mythtv-backend.service: Start request repeated too quickly.**[/COLOR]
Nov 28 18:31:07 server2.aeran.info systemd[1]: [COLOR=#FF5454]**Failed to start MythTV Backend.**[/COLOR]
[/FONT]
```

I have to reboot the box to get it running properly. The "systemctl start mythtv-backend" command doesn't work.

I've read a lot of issues when upgrading from 14.40 to 16.04, but none like this.

Any suggestions would be gratefully appreciated.

Thanks

[FONT=monospace]
[/FONT]

---

