---
title: "Changes to the EPG in the UK - Channel numbers not assigning correctly to channels!"
date: 2008-09-08
forum: Mythbuntu
---

### Post by db260179 on 2008-09-08
For DVB-T UK users.

The powers to be have changed the EPG code - thus when scanning for channels in mythtv-setup, all the channels will come up bigger numbers i.e.

BBC ONE = 44556, BBC TWO = 55540 etc etc

Please use this sql script to keep the right order of channel numbers to the right channel.

Goto the terminal and type.

mysql -u*sqluser* -p*sqluserpass* mythconverg < chan_numbers_update.sql > output.tab

Please change the script if your channels are not there. (its just a text file)

---

### Post by Andrew U.K. on 2008-10-05
Hi 
I copy and paste* mysql -u*sqluser* -p*sqluserpass* mythconverg < chan_numbers_update.sql > output.tab* in the terminal and the response is no such file or directory. 

So should I create one if so how?

Cheers
Andrew

---

### Post by db260179 on 2008-10-05
Extract my attachment channelscript.zip in your home folder. Run a terminal, then type

mysql -u*sqluser* -p*sqluserpass* mythconverg < chan_numbers_update.sql > output.tab

*sqluserpass and *sqluser you will find in /etc/mysql/my.cnf i.e -umythtv -ppassword

---

### Post by Andrew U.K. on 2008-10-06
Thanks

---

### Post by DesG on 2008-10-06
I have changed the file for those who are in Northern Ireland (some different channel names)

Cheers, Des.

---

