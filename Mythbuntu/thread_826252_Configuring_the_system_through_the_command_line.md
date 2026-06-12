---
title: "Configuring the system through the command line"
date: 2008-06-11
forum: Mythbuntu
---

### Post by uMuppet on 2008-06-11
Is there any way I can configure the backend/frontend through the command line?

I want to write a script to do changes anywhere on the system, including changing the TV format and Channel frequency table in the backend or Edit Keys in the front end.  Just examples.

Is there a file that holds these parameters that I can alter?  Or is it a case by case procedure?

Thanks

---

### Post by ian dobson on 2008-06-12
Hi,

Most the configuration information for MythTV is stored in a MySQL database. So you could use the mysqladmin tool to edit the setting table. 

AsI run a webserver on my backend system I just use phpmyadmin to edit SQL tables with a web browser.

Regards
Ian Dobson

---

### Post by uMuppet on 2008-06-12
I just had a dig using MySQL Query Browser and under SETTINGS I see all the adjustments for both front and backend. So I can write a script to make just about any changes I want.  Perfect.

Thanks

---

