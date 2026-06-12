---
title: "mythweb cant acces through LAN IP"
date: 2010-05-29
forum: Mythbuntu
---

### Post by sperwer on 2010-05-29
Hi i may have messed up mythweb/apache.
I was able to acces mythweb on [http://192.168.x.x/mythweb](http://192.168.x.x/mythweb)
but somehow it only responds on
[http://127.0.1.1/mythweb](http://127.0.1.1/mythweb)

What have i messed up?
And can you give me a hint to fix it.
EDIT
Before being able to contact mythweb as in the above situation I have to do:
/etc/init.d/apache2 restart
Resulting in this output:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Best regards
Sperwer

---

