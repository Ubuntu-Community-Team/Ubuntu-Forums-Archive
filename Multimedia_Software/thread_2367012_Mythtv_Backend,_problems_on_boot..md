---
title: "Mythtv Backend, problems on boot."
date: 2017-07-24
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2017-07-24
Whenever I reboot my server mythtvbackend service shows this, and i get channel unavailable on every channel. 

```
[FONT=monospace][COLOR=#000000]systemctl status mythtv-backend.service  [/COLOR]
[COLOR=#54FF54]**&#9679;**[/COLOR][COLOR=#000000] mythtv-backend.service - MythTV Backend[/COLOR]
   Loaded: loaded (/lib/systemd/system/mythtv-backend.service; enabled; vendor preset: enabled)
   Active: [COLOR=#54FF54]**active (running)**[/COLOR][COLOR=#000000] since Fri 2017-07-21 19:55:26 MST; 2 days ago[/COLOR]
     Docs: https://www.mythtv.org/wiki/Mythbackend
 Main PID: 2138 (mythbackend)
    Tasks: 38
   Memory: 33.3M
      CPU: 28min 39.909s
   CGroup: /system.slice/mythtv-backend.service
           &#9492;&#9472;2138 /usr/bin/mythbackend --quiet --syslog local7

Jul 24 17:36:04 failbox mythbackend[2138]: mythbackend[2138]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: failbox(1d31760) as a client (events: 0)
Jul 24 17:36:04 failbox mythbackend[2138]: mythbackend[2138]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to WatchingLiveTV
Jul 24 17:36:04 failbox mythbackend[2138]: mythbackend[2138]: I TVRecEvent mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 10
Jul 24 17:36:04 failbox mythbackend[2138]: mythbackend[2138]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
Jul 24 17:36:04 failbox mythbackend[2138]: [COLOR=#FF5454]**mythbackend[2138]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000**[/COLOR][COLOR=#000000][/COLOR]
Jul 24 17:36:04 failbox mythbackend[2138]: [COLOR=#FF5454]**mythbackend[2138]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](10434F80-0): SetChannelByString(13-3): Failed to ini**[/COLOR][COLOR=#000000][/COLOR]
Jul 24 17:36:04 failbox mythbackend[2138]: [COLOR=#FF5454]**mythbackend[2138]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 13-3. Reverting to kState_None**[/COLOR][COLOR=#000000][/COLOR]
Jul 24 17:36:04 failbox mythbackend[2138]: mythbackend[2138]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from WatchingLiveTV to None
Jul 24 17:36:09 failbox mythbackend[2138]: mythbackend[2138]: I MythSocketThread(75) mainserver.cpp:7629 (connectionClosed) Playback sock(1d31760) 'failbox' disconnected
Jul 24 17:36:09 failbox mythbackend[2138]: mythbackend[2138]: I MythSocketThread(55) mainserver.cpp:7629 (connectionClosed) Monitor sock(1d32ff0) 'failbox' disconnected
[/FONT]
```

After restarting the service everything is normal. I am using hdhomerun on the network. Is there a way I can sort this out so it works when reboot. For now I'm setting an @reboot flag in root crontab to restart the service at boot after it's initial start.

---

### Post by deadflowr on 2017-07-24
Moved to *Multimedia Software*

Is this myth from 16.04?
Maybe look at this page:
[https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration]("https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration")
Maybe look at the delay the backend until tuners are initialized section.

---

### Post by Tadaen_Sylvermane on 2017-07-25
Yes, 16.04 LTS with the HWE stack. The only thing having to do with network timers isn't relevant as I don't use NetworkManager on my Ubuntu server installation. I will keep the service starting with the @reboot in the root crontab for now. Maybe I can add a sleep or something to delay the start till network is finally up. I think this may be happening because my server is also doing dhcp and dns. If dhcp isn't up then the hdhomerun on the network isn't available till after that.

*EDIT* When I thought of the DHCP server I changed something and it worked. For others running dhcp on the mythtv-backend server change this...

```

[FONT=monospace][COLOR=#000000][Unit][/COLOR]
Description=MythTV Backend
Documentation=https://www.mythtv.org/wiki/Mythbackend
After=mysqld.service network.target
[/FONT]
```[FONT=monospace]

to this...

[/FONT]```

[FONT=monospace][COLOR=#000000][Unit][/COLOR]
Description=MythTV Backend
Documentation=https://www.mythtv.org/wiki/Mythbackend
After=mysqld.service network.target isc-dhcp-server.service
[/FONT]
```[FONT=monospace]

in the /lib/systemd/system/mythtv-backend.service file. Adjust isc-dhcp-server.service to whatever dhcp server service you are using.[/FONT]

---

