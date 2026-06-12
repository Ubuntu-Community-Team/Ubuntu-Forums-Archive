---
title: "can't play live tv or record"
date: 2009-02-01
forum: Mythbuntu
---

### Post by itlarson on 2009-02-01
I have installed mythubuntu 8.10 and run mythtv-setup.  Scaning for chanels goes fine and there is schedule info, but when I try to play live tv it just kicks me back to the menu.  Scheduled recordings show up like they should, but when I try to play them, it says "recording not found".  Is mythtv not accessing my dvb tuners?  or is it something else?****

---

### Post by klc5555 on 2009-02-02
> **itlarson said:**
> I have installed mythubuntu 8.10 and run mythtv-setup.  Scaning for chanels goes fine and there is schedule info, but when I try to play live tv it just kicks me back to the menu.  Scheduled recordings show up like they should, but when I try to play them, it says "recording not found".  Is mythtv not accessing my dvb tuners?  or is it something else?****

The scheduled recordings "show up like they should"? If you have the default storage directory set up as it ought to be in the backend setup, but either a) myth doesn't seem to be able to write mpg files to these storage directories (with livetv kicking you back to the menu), or b) there are actual mpg files going into the recording directory or directories when you have scheduled them to record, but you can't then access these recordings, the problem is usually some combination of owner/group missettings on one or more of the storage directories and/or misset permissions one or more of these directories. 

Each directory in the storage group should have its owner and group both set as "mythtv" (not, say, "root", as generally happens with a newly added mount point). Permissions on each directory should probably be 775 or 776. (Some people will use the wide-open 777). And, your own username needs to be added to the mythtv group, which usually happens the first time you run mythbuntu control center from the frontend after install, but may not have. 

Usually straightening these things out, particularly on a multi-drive system that may not have been set up in its entirety by Mythbuntu alone, gets recording/viewing working again.

Cheers!:)

---

### Post by Mister.Vash on 2009-02-02
"my dvb tuners?"  Are you using the pchdtv HD-5500?  If not, what card are you using?

---

### Post by itlarson on 2009-02-02
The first post got it-  My storage directory was accesible to root only.  Thanks for the help.  

P.S.- I am using the pchdtv 5500.

---

### Post by Mister.Vash on 2009-02-03
Glad it's working - I had the same type of issue, the fix was on the analog side, setting the v4l recording profiles to 720x480 or lower.

---

