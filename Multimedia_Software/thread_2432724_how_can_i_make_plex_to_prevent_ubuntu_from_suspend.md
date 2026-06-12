---
title: "how can i make plex to prevent ubuntu from suspending while a file is in use?"
date: 2019-12-07
forum: Multimedia Software
---

### Post by ronjjjg8885 on 2019-12-07
thanks!!!

---

### Post by uRock on 2019-12-07
> **ronjjjg8885 said:**
> thanks!!!

What kind of file and in what kind of process? The more descriptive you are, the more likely you are to get help.

---

### Post by ronjjjg8885 on 2019-12-07
hi
i'm using the plex server from 'ubuntu software'
i shared the videos folder and i can now watch tv shows on tv with my choromecast and android smartphone app
after half an hour my computer sleeps and the show stops
i want to know if there is a way to make my computer know that a file is in use in plex so my computer doesn't go to sleep on these cases

do you understand?

---

### Post by uRock on 2019-12-07
Sounds like you're going to need something like the script shown here. [https://www.collindelker.com/2016/10/16/plex-linux-prevent-sleep-take2.html](https://www.collindelker.com/2016/10/16/plex-linux-prevent-sleep-take2.html)

> Systemd service
The new system uses a systemd service, which is completely different from the old sleep.d method. We can still take the approach of checking the Plex server's status webpage and parsing out the number of active sessions, but it must be run as a service. Here's what to do.

The Code```

[Unit]
Description=Inhibit suspend if Plex is streaming media
Before=sleep.target

[Service]
Type=oneshot
ExecStart=/bin/sh -c "if [ `curl localhost:32400/status/sessions 2>/dev/null | sed -n 's/.*MediaContainer size=\"\(.*\)\".*/\1/p'` -gt 0 ]; then exit 1; else exit 0; fi"

[Install]
RequiredBy=sleep.target
```
Notice the ExecStart line looks a lot like the meat of the previous sleep.d script, but condensed into a single line. This is what checks the Plex status to pull out how many "MediaContainers" are active, and if more than 0, it exits with an error code of 1.  The "RequiredBy" tag here says that the sleep target service needs this script to finish successfully (error code 0) before running.

Save the code to a file in /etc/systemd/system (use sudo for root permissions). I called it /etc/systemd/system/plexkeepawake.service. Then activate the service with:
```
systemctl enable plexkeepawake.service
```
And that's it! You could add other services in a similar way to prevent sleep while serving Samba shares, running backups, etc. by changing what's in the if-block.That bit of scripting may need editing, but should be a good starting point.

---

### Post by ronjjjg8885 on 2019-12-08
hi and thank you very much for the investment! 

personally i don't have enough knowledge for it and wonder if there is a simpler solution?

---

### Post by Tadaen_Sylvermane on 2019-12-11
Is there a reason the machine serving even can go into suspend or sleep? I know for my server i disabled that completely at the systemd level. depending on your load levels the machine running 24/7 likely shouldn't impact your power bill to much i would imagine. easiest solution.

[https://wiki.debian.org/Suspend](https://wiki.debian.org/Suspend)

> ```
[COLOR=black]sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```[/COLOR]

---

