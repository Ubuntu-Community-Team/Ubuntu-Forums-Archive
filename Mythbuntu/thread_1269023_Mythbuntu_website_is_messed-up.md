---
title: "Mythbuntu website is messed-up"
date: 2009-09-17
forum: Mythbuntu
---

### Post by scovel on 2009-09-17
The Mythbuntu site is messed-up.  Download of the Direct 9.04 keeps stalling.  Clicking on the torrent gives an error:

```
**Warning**: The MySQL server is running with the --read-only option so it cannot execute this statement query: INSERT INTO watchdog (uid, type, message, severity, link, location, referer, hostname, timestamp) VALUES (0, 'php', '<em>The MySQL server is running with the --read-only option so it cannot execute this statement\nquery: INSERT INTO watchdog (uid, type, message, severity, link, location, referer, hostname, timestamp) VALUES (0, &amp;#039;page not found&amp;#039;, &amp;#039;files/mythbuntu-9.04-desktop-i386.iso.torrent&amp;#039;, 1, &amp;#039;&amp;#039;, &amp;#039;http://www.mythbuntu.org/files/mythbuntu-9.04-desktop-i386.iso.torrent&amp;#039;, &amp;#039;http://www.mythbuntu.org/downloads&amp;#039;, &amp;#039;76.28.30.210&amp;#039;, 1253226105)</em> in <em>/srv/mythbuntu.org/www/includes/database.mysql.inc</em> on line <em>172</em>.', 2, '', 'http://www.mythbuntu.org/files/mythbuntu-9.04-desktop- in **/srv/mythbuntu.org/www/includes/database.mysql.inc** on line **172**
```


Clicking on the MD5SUMS gives the same problem.  

In general its in sad shape.

Sean

---

### Post by tgm4883 on 2009-09-17
Fixed, thanks for the report

---

