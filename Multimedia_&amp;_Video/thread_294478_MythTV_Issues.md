---
title: "MythTV Issues"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by mlw4428@gmail.com on 2006-11-06
For some reason I get this message everytime I try to watch TV:

2006-11-06 17:31:16.718 Connected to database 'mythconverg' at host: localhost
2006-11-06 17:31:16.744 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-11-06 17:31:16.744 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

Myth's Frontend says it couldn't connect to the backend (running on the same machine). My backend settings are for it to run on 127.0.0.1

I'm running Edgy and am using this guide:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

---

### Post by jaymode on 2006-11-06
The backend probably is not running. 

Try:
sudo /etc/init.d/mythtv-backend restart

---

### Post by superm1 on 2006-11-07
If that doesn't get you up and running,

query the logs at **/var/log/mythtv/mythbackend.log** for anything related to why the backend is dying.

---

