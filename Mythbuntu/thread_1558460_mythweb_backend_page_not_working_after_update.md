---
title: "mythweb backend page not working after update"
date: 2010-08-22
forum: Mythbuntu
---

### Post by benlyboy on 2010-08-22
Hi all

Last night I did an update on my mythbuntu 10.04 LTS . Now I find that the backend page of myth web is blank. I also seem to have lost all thumbnails from the recorded programs page.

The only clue I have is that this info that appears at the top of the blank backend page.

```

Warning at /usr/share/mythtv/mythweb/modules/status/handler.php, line 35:
file_get_contents([http://127.0.0.1:6544):](http://127.0.0.1:6544):) failed to open stream: Connection refused

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:148)
```

Anyone know what this means and how to fix it...?


Thanks

---

### Post by benlyboy on 2010-08-23
just bumped this in the hope someone can help....please :-)

---

### Post by tgm4883 on 2010-08-23
What is the output of 
```
dpkg -l mythweb
```

---

### Post by benlyboy on 2010-08-23
thanks for the reply

here is that output

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythweb        0.23.0+fixes25 Web interface add-on module for MythTV


```

---

### Post by benlyboy on 2010-08-25
bumped this as i still really need some help....

---

### Post by benlyboy on 2010-08-26
ok great news 

I kept up with updates since i lost my mythweb  back page and there were 6 more waiting tonight after installing theses all is working again.

I guess what updates take away, updates can give back...

---

