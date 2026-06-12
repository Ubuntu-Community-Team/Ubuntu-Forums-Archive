---
title: "AirData 150 Driver Issue PLZ HELP!"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by Dominator19 on 2010-12-31
Hallo everyone.. I am new to this forum and im not gonna lie i only joined cuz of my problem..

i own this wifi USB card AirData 150 S2 and i think RaLink is the manufacturer but the only problem is i cannot get it to work in Ubuntu..

No i dont have any experience in Ubuntu...windows was always my choice but i decided a change in course...

i would really appreciate it if someone could guide me through the installation and/or configuration needed to make the damn thing work. 

thanx in advance

Alex

---

### Post by chili555 on 2010-12-31
Please open Applications > Accessories > Terminal and, with the device plugged in, run and post:```
lsusb
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by Dominator19 on 2011-01-01
i tried what you said and thanx for the reply but this is what i get

root@ubuntu:~# lsmod | rt2
/usr/lib/ruby/1.8/rt/rtparser.rb:155:in `parse_table_data': RT: different column size (RuntimeError)
    from /usr/lib/ruby/1.8/rt/rtparser.rb:179:in `parse_body'
    from /usr/lib/ruby/1.8/rt/rtparser.rb:85:in `parse'
    from /usr/bin/rt2:147
root@ubuntu:~# 

any ideas?

---

### Post by chili555 on 2011-01-01
> root@ubuntu:~# lsmod | rt2First, for security reasons, you should never log in as root, only as an ordinary user. You can temporarily gain administrative privileges with sudo. Second, the command was:```
lsmod | [COLOR="Red"]grep[/COLOR] rt2
```What about the other command?

---

