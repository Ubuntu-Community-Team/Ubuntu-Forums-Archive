---
title: "files unreachable in apache"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by hormiguero on 2011-12-11
I have set up Ubuntu 11.10 with Apache, MySQL, PHP5, Wordpress, etc...  When I access the wordpress login page from my network PCs - even directing the browser to the external IP, all works fine.  I have the Ubuntu machine in the DMZ so an associate can access it and work with me on web page design.  When he accesses it from his home, he gets the login page, but objects and files referenced using the host name of the Ubuntu PC are not found.  When he tries to log in, he gets "file not found" from the browser (Chrome or firefox) because the files requested internally are prefaced by the pc host name.  The Ubuntu PC host name is resolved by my PCs fine.  He has the same problem trying to work locally on my network...  Saying this another way for clarity...

My network is accessed by XXXX.XXXXX.NET/wordpress/wp-login

wordpress login page appears without pretty formatting

type in login info & pw and get   file not foound

Address in browser shows UBUNTUHOST/wordpress/wp-admin          rather than
                                      XXXX.XXXXX.NET/wordpress/wp-admin

Obviously I'm missing something in some config file, but am totally thrown off that it works from MY PCs but when my friend tries from his place OR on my network (wired or wireless) he gets the file not found and no formatting or pix.  He has tried with both MAC and PC from home, and MAC on my network.  I have searched for two days on the net and tried MANY fixes without results....    H E L P !!

---

### Post by hormiguero on 2011-12-12
I'm not sure whether I fixed it or only a workaround...  Added lines in Wordpress wp-admin to point to site and wp-home URL...  Now Wordpress no longer uses UBUNTUHOST as the site url, rather uses the dyndns host name...   SOLVED (but I have no hair left](*,)  )

---

