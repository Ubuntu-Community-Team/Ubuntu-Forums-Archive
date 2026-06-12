---
title: "Mythtv db sys drive"
date: 2009-02-09
forum: Mythbuntu
---

### Post by zf3636 on 2009-02-09
Hi I have few questions I need help with I would like to backup my system drive to my 2nd drive what steps do i take to make this possible and would this backup procedure backup my config settings ie channel settings,tv guide settings, sound settings,directory settings. I would also like to know how to access Mythweb I have created a username and password, can any one explain the best power save option to use rather than a complete shutdown thanks.

---

### Post by ian dobson on 2009-02-09
Hi,

1) You can backup your database using:-
mysqldump -u"user" -p"password" --all-databases --opt | bzip2 > /data/backup-sql.bz2

replace "user" and "password" with you database user/password

2) In a webbrowser enter [http://ip.of.you.backend/mythweb/](http://ip.of.you.backend/mythweb/)

3) Not sure about power saving. If I need a low power box I just underclock as far as I can, use a flash drive/usb stick to boot the OS and all data commes from my main server(my backend server runs 24/7).

Regards
Ian Dobson

---

### Post by ian dobson on 2009-02-09
Hi,

1) You can backup your database using:-
mysqldump -u"user" -p"password" --all-databases --opt | bzip2 > /data/backup-sql.bz2

replace "user" and "password" with you database user/password

2) In a webbrowser enter [http://ip.of.your.backend/mythweb/](http://ip.of.your.backend/mythweb/)

3) Not sure about power saving. If I need a low power box I just underclock as far as I can, use a flash drive/usb stick to boot the OS and all data commes from my main server(my backend server runs 24/7).

Regards
Ian Dobson

---

