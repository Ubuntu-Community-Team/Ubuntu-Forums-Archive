---
title: "Mysql-Gammu gammu-smsd[3429]: Error code: 1054, Error: Unknown column 'Signal' in 'fi"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by arturo322 on 2011-02-12
I seemed to configure my gammu and changed the version indicated version on my gammu table from 10 to 11 to match the version of my sql, upon starting my gammu-smsd the error


gammu-smsd[3429]: Error code: 1054, Error: Unknown column 'Signal' in 'field list'
gammu-smsd[3429]: Error code: 1054, Error: Unknown column 'Signal' in 'field list'
gammu-smsd[3429]: Error code: 1054, Error: Unknown column 'Signal' in 'field list'


kept on repeating on an infinite loop

---

### Post by arturo322 on 2011-02-12
BTW 

Device               : /dev/ttyUSB0
Manufacturer         : huawei
Model                : unknown (E1552)
Firmware             : 11.608.10.00.00
IMEI                 : 353143034056318
SIM IMSI             : 515020303139038

im using a gsm broadband as GSM modem
Huawei(E1552)

---

### Post by illidancuk on 2011-05-30
I've same error with you... 

It's caused by [B]
        0001380: Not compatible with MySQL 5.5    
        MySQL 5.5 introduced keyword SIGNAL and it clashes with field name in our table.    [/B]

Ref : [https://bugs.cihar.com/view.php?id=1380](https://bugs.cihar.com/view.php?id=1380)

but i can't solve it. i hope someone tell to me how to fix this... thank's

---

### Post by misteryfan on 2011-06-01
is there a column/field named Signal in phones table?
if not alter your phones table to add a column Signal with option like this 
  [FONT=Verdana]
[/FONT]ALTER TABLE phones ADD COLUMN Signal INT NOT NULL DEFAULT 0;
****

---

