---
title: "Setting free HDD space"
date: 2010-12-12
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-12
As I recall there's a setting in mythtv somewhere to define the amount of HDD space to be kept free. A backend function, IIRC.

I don't seem to be able to find it. Any help, anyone?

---

### Post by GuiGuy on 2010-12-16
> **GuiGuy said:**
> As I recall there's a setting in mythtv somewhere to define the amount of HDD space to be kept free. A backend function, IIRC.

I don't seem to be able to find it. Any help, anyone?

It seems mythtv is not auto-expiring recordings. Permissions seem correct, the files in /var/lib/mythtv/recordings are not orphans, and the HDD is full. There are no other significant files on the HDD that would cause it to fill up. Recordings go back six months or more.

Short of a clean re-install, any suggestions?

Thanks.

---

### Post by Senkoboy on 2010-12-16
> **GuiGuy said:**
> As I recall there's a setting in mythtv somewhere to define the amount of HDD space to be kept free. A backend function, IIRC.



I think the setting is in the backend setup, don't remember where. Can you delete the old recordings from the frontend?

---

### Post by GuiGuy on 2010-12-16
> **Senkoboy said:**
> I think the setting is in the backend setup, don't remember where. 

I think it has changed in 0.24. The only option I see is is to "General > Miscellaneous Settings" > Storage Group Disk Scheduler", which offers two options:

[LIST=1]
[*]Balanced Free Settings
[*]Balanced Disk I/O
[/LIST]

1) is the recommended setting.


> Can you delete the old recordings from the frontend?

Probably, but I am unsure on the impact on the database, given it has indexed the files. Oddly, however, I cannot see them in the Media Library > Recordings option.

---

### Post by thatguruguy on 2010-12-16
I've had the occasional weird instance when deleting a program from the frontend doesn't actually delete the file.  I've found that making deletions from mythweb seems to work reliably, however.

---

### Post by GuiGuy on 2010-12-17
> **thatguruguy said:**
> I've had the occasional weird instance when deleting a program from the frontend doesn't actually delete the file.  I've found that making deletions from mythweb seems to work reliably, however.

My problem is that there are no recordings listed, yet none of the 2000 plus mpg files in /var/lib/mythtv/recordings are orphans. That is, they have an entry in the database.

My question is, I suppose, why doesn't mythtv auto-expire recordings?

I'm going to do a clean install over the weekend.

Regards

---

### Post by utar on 2010-12-17
> **Senkoboy said:**
> I think the setting is in the backend setup, don't remember where. Can you delete the old recordings from the frontend?

No, it's in frontend settings.

I'm not in front of my Myth box at the moment but I think it is under TV / Settings / General

---

