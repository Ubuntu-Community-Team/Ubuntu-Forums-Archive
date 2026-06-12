---
title: "How to configure media sharing in ubuntu 20.04 without being logged in?"
date: 2020-06-08
forum: Multimedia Software
---

### Post by capistrano on 2020-06-08
I love that UPnp/DLNA Media Sharing is now built into Ubuntu 20.04 (it's using Rygel under the hood and I know actually came in 19.10 but I've just upgraded from 18.04). However, it appears that I need to be logged into my account for this service to be active.  I have an Ubuntu box I use primarily as a media PC and it'd be great if I didn't have to leave it logged in all the time. 

So my question is, can I configure my system so that Media Sharing/Rygel is started automatically at boot time?

---

### Post by TheFu on 2020-06-08
Yes.

[LIST=1]
[*]Install rygel and the few dependencies.
[*]Create a new userid and group for rygel.  
[*]Make it so that userid has file and directory access to the media files you want shared. 
[*]Manually setup the /etc/rygel.conf file as needed on your system. Probably should make a backup with the original contents BEFORE any modifications .. say /etc/rygel.conf.2020.06
[*]Create a systemd unit file to control start, stop, status requests in the "normal" systemd way. Something like this:
```
[Unit]
Description=Rygel DLNA server
After=syslog.target

[Service]
User=rygel
Group=rygel
ExecStart=/usr/bin/rygel

[Install]
WantedBy=multi-user.target
```
[*]sudo systemctl enable rygel
[*]sudo systemctl start rygel
[/LIST]

That should work, but I haven't tested it.
If you need help understanding how to allow files owned by you userid to also be managed by rygel: [https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965) It is all about having members of the same group provided access and new files/directories created being automatically using the group. Objects "moved" into the directory tree don't have their group ownership changed, a copy/rsync is needed to create a "new" object.  This is standard Unix stuff that has worked this way 40+ yrs.

---

### Post by Tadaen_Sylvermane on 2020-06-08
I don't know anything about 20.04 and Rygel. I'd stick with something I know for sure works as a service. Minidlna. Idiot proof to configure and has a service file already when installed. Short of it not making it to 20.04 I'd say that is probably the safest bet.

---

### Post by capistrano on 2020-06-09
Thanks, guys, for the answers but it's not really what I'm looking for. I am specifically asking about having the Ubuntu 20.04 integrated Rygel running without needing to be logged in. Previously I had Twonky Server set up in this way but I wanted to switch to the integrated Media Sharing feature now that it's part of Ubuntu.

---

### Post by TheFu on 2020-06-09
> **capistrano said:**
> Thanks, guys, for the answers but it's not really what I'm looking for. I am specifically asking about having the Ubuntu 20.04 integrated Rygel running without needing to be logged in. Previously I had Twonky Server set up in this way but I wanted to switch to the integrated Media Sharing feature now that it's part of Ubuntu.

Which is exactly what my post does.

---

### Post by capistrano on 2020-06-09
Sorry, I see that now. I think when I saw Step 1 being Install Rygel I thought you were not using the shipped package but I guess I can just skip that step in Ubuntu 20.04 as it's already installed.

---

