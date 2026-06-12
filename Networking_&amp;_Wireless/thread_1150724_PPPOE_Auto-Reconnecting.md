---
title: "PPPOE Auto-Reconnecting"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Gharchkhor on 2009-05-06
My connection drops sometimes and since my bandwidth is free at nights I do my downloads when i'm sleep and i don't like to wake-up and see the line was dropped just 3 minutes after i went to bed and i wasn't there to reconnect it.

I remember there was a line which i could add to the end of a file and that was doing the trick very well but i've lost my bookmarks and can't find it anywhere on the web now. care to help? :)

---

### Post by echoforever on 2009-12-12
Hello,
You may have fixed the problem by now. For those facing the same problem, edit /etc/ppp/peers/dsl-provider file and the following line:
persist

---

