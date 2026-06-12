---
title: "How to share directory from command line?"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by redss on 2012-10-03
On ubuntu 10.04 I know how to share the /media folder by right clicking the /media folder in nautilus, going to sharing options and click "share this folder".

How can I do that from a command prompt in terminal?

---

### Post by bab1 on 2012-10-03
> **redss said:**
> On ubuntu 10.04 I know how to share the /media folder by right clicking the /media folder in nautilus, going to sharing options and click "share this folder".

How can I do that from a command prompt in terminal?

The basic command starts with ```
net usershare
```

Look at the man pages (the sub section usershare)```
man net
```

The first part of that subsection looks like this```
 USERSHARE
       Starting  with  version 3.0.23, a Samba server now supports the ability
       for non-root users to add user-defined shares to be exported using  the
       "net usershare" commands.

       Members  of  the UNIX group "sambashare" can create user-defined shares
       on demand using the commands below...

```

---

### Post by redss on 2012-10-04
Exactly what I was looking for. Thanks!

---

### Post by marinara on 2012-10-06
i'd like to write this into the wiki.  Is this documented anywhere?  what other steps to get this working, like installing samba do i need to do for lubuntu?

---

### Post by redss on 2012-10-06
Well I installed samba and smbfs first, then net usershare command

---

### Post by bab1 on 2012-10-06
> **marinara said:**
> i'd like to write this into the wiki.  Is this documented anywhere?  what other steps to get this working, like installing samba do i need to do for lubuntu?

What is it that you want to document?  If it is usershares, the man pages have all of the info for the net command.  This forum has many threads that reference usershares.  Of course Samba.org also has a forum and documentation. 

Here is a [**_[COLOR="Blue"]google search of ubuntuforums[/COLOR]_**]("https://www.google.com/search?q=usershares+site%3Aubuntuforums.org&btnG=Go!#q=usershares+site:ubuntuforums.org&hl=en&prmd=imvns&ei=Sm1wUOS5JKKDiwLK8YDIAQ&start=10&sa=N&bav=on.2,or.r_gc.r_pw.r_qf.&fp=1491d37767182070&biw=1104&bih=635") using the keyword: usershares.

Here is the same [**_[COLOR="Blue"]search but of samba.org[/COLOR]_**]("https://www.google.com/search?q=usershares+site%3Aubuntuforums.org&btnG=Go!#hl=en&sclient=psy-ab&q=usershares+site:samba.org&oq=usershares+site:samba.org&gs_l=serp.3...326819.330507.0.330793.9.9.0.0.0.0.273.1183.0j8j1.9.0.les%3B..0.0...1c.1.lhnyvr1woHU&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=1491d37767182070&biw=1104&bih=635") for the keyword: usershares.

---

