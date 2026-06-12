---
title: "Problems with mediainfo"
date: 2012-08-10
forum: Multimedia Software
---

### Post by Tangled_Kid on 2012-08-10
Please excuse me if I'm in the wrong place, & feel free to re-direct me to the right place...

I have a Bitnami web server setup running "Ubuntu Linux 10.04 LTS 64bits".

I have need to use mediainfo as we process videos on the file & I would like to use this to detect if videos need rotating before processing.

I have installed mediainfo OK, & when I run mediainfo <filename> from the command line it works just fine, however when I run the command from within my PHP script…

exec("mediainfo <filename>")

… I see the following error reported in the error_log…

/usr/bin/mediainfo: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/bin/mediainfo)
/usr/bin/mediainfo: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/bin/mediainfo)
/usr/bin/mediainfo: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libzen.so.0)
/usr/bin/mediainfo: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libzen.so.0)

Can anyone please help me understand why this is happening?

Thanks in advance,

T

---

### Post by Tangled_Kid on 2012-08-28
Got this sorted in the end, by copying the binaries around.  Can't remember the details, otherwise would post theme here.

---

