---
title: "how to change logo via vlc RC"
date: 2016-06-20
forum: Multimedia Software
---

### Post by peter253 on 2016-06-20
Hello, I am using vlc 2.2.3 with RC (remote control) but I have no luck to change overlay logo image.


Commands like /bin/echo -n "pause" | nc -U /user/vlc.sock works ok but commands I tried for logo change are not working:


/bin/echo -n "@logo logo-file /user/logo2.png" | nc -U /user/vlc.sock
/bin/echo -n "@name logo-file /user/logo2.png" | nc -U /user/vlc.sock
/bin/echo -n "--logo-file /user/logo2.png" | nc -U /user/vlc.sock




Any idea how to change logo via RC please?

---

