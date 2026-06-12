---
title: "Plex wont start"
date: 2023-10-30
forum: Multimedia Software
---

### Post by mitchell2345 on 2023-10-30
Hi i just upgraded my plex server to the latest version and now Plex fails to start.  I cant really find any logs on what the issue is.  any ideas:

```
mitchell@mythtv:/usr/lib/plexmediaserver$ sudo systemctl status plexmediaserver
× plexmediaserver.service - Plex Media Server
     Loaded: loaded (/lib/systemd/system/plexmediaserver.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2023-10-30 08:56:39 CDT; 1min 50s ago
    Process: 8060 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" || /bin/mkdir -p "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" (code=exited, status=0/SUCCESS)
    Process: 8062 ExecStart=/bin/sh -c  export PLEX_MEDIA_SERVER_INFO_VENDOR="$(grep ^NAME= /etc/os-release | awk -F= "{print \$2}" | tr -d \" )";  export PLEX_MEDIA_SERVER_INFO_MODEL="$(uname -m)";  export PLEX_MEDIA_SERVER_INFO_PLATFO>
   Main PID: 8062 (code=exited, status=255/EXCEPTION)
        CPU: 104ms

Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Scheduled restart job, restart counter is at 3.
Oct 30 08:56:39 mythtv systemd[1]: Stopped Plex Media Server.
Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Start request repeated too quickly.
Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Failed with result 'exit-code'.
Oct 30 08:56:39 mythtv systemd[1]: Failed to start Plex Media Server.
mitchell@mythtv:/usr/lib/plexmediaserver$ sudo systemctl status plexmediaserver
× plexmediaserver.service - Plex Media Server
     Loaded: loaded (/lib/systemd/system/plexmediaserver.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2023-10-30 08:56:39 CDT; 1min 33s ago
    Process: 8060 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" || /bin/mkdir -p "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" (code=exited, status=0/SUCCESS)
    Process: 8062 ExecStart=/bin/sh -c  export PLEX_MEDIA_SERVER_INFO_VENDOR="$(grep ^NAME= /etc/os-release | awk -F= "{print \$2}" | tr -d \" )";  export PLEX_MEDIA_SERVER_INFO_MODEL="$(uname -m)";  export PLEX_MEDIA_SERVER_INFO_PLATFO>
   Main PID: 8062 (code=exited, status=255/EXCEPTION)
        CPU: 104ms

Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Scheduled restart job, restart counter is at 3.
Oct 30 08:56:39 mythtv systemd[1]: Stopped Plex Media Server.
Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Start request repeated too quickly.
Oct 30 08:56:39 mythtv systemd[1]: plexmediaserver.service: Failed with result 'exit-code'.
Oct 30 08:56:39 mythtv systemd[1]: Failed to start Plex Media Server.

```

---

### Post by TheFu on 2023-10-30
Have you tried manually running the server using the userid and command in the systemd unit file for plex?  Then you can see any errors/warnings dumped to a terminal.  Also, you might enable the debug mode on the server when starting it, which should dump more details than anyone needs.

I stopped using Plex a few years ago - switched the Jellyfin for better privacy and the ability to more easily record OTA TV - but whenever plex refused to start, it was almost always one of these things:

[LIST]
[*]Out of space in /var/
[*]Corrupted Plex DB.  I'd restore from the most recent backup that worked.
[*]incorrect file/directory permissions in a media directory.
[/LIST]
In that order.

BTW, Jellyfin is 100% F/LOSS and doesn't phone home for every keystroke like Plex does.  Both servers have issues.  I didn't like that Plex didn't work with Vorbis/ogg music.  Of course, Jellyfin has issues too. The good news is that the same media directories can be shared by both and they won't conflict with each other.  I ran both Plex and Jellyfin servers for over 6 months using the same media directories, before deciding.  One of the key issues for me was that I really disliked the Plex clients. During playback, subtitles were covered by OSD prompts .... so if I needed more time to read the captions, pausing prevented that from being possible. There were some other issues and the terrible privacy. Of course, we are all different in what level of hassles we are willing to stand over privacy/convenience choices.

---

