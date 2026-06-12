---
title: "How do I install samba 3.0.6"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by ttallos on 2006-02-20
I have backup software called retrospect. Retrospect needs samba 3.0.6
I looked at my version with synaptic and it said samba 3.0.14a-6ubuntu1 
can I upgrade to 3.0.6 easily like apt get synaptic or something.

---

### Post by Robgould on 2006-02-20
I may be wrong.  I'm sure someone will correct me if I am.  Ubuntu does not as a rule update packages between releases.  You can get some from the "backports" repo.
 
 [http://www.ubuntuforums.org/forumdisplay.php?f=47]("http://www.ubuntuforums.org/forumdisplay.php?f=47") 
 
If backports does not carry your update, you need to update Ubuntu to get the newer version.  If you update from Breezy to Dapper you will get updates in pakcage versions.  To get MySQL 5.0 I had to update to Dapper.
 
The other alternative it to build what you want from source.  The only problem with that is that now you will have software that is not part of the ubuntu packaging system, so it will not be maitned by them.  This means that you could have dependency issues now or in the future and that future updates will not be applied to this software automatically.
 
I hope this helps you.

---

### Post by Robgould on 2006-02-20
I looked here:
 
[http://www.ubuntuforums.org/showthread.php?t=121505]("http://www.ubuntuforums.org/showthread.php?t=121505")
 
Does not look like backports will help you.

---

### Post by knalle on 2006-02-20
[QUOTE=ttallos]I have backup software called retrospect. Retrospect needs samba 3.0.6
[/QUOTE]

in what way does it need samba 3.0.6, as a package dependecy?

---

### Post by ttallos on 2006-02-20
Thanks for all the replies I am having great connectivity with the windows machines and I created a share using the home folder that works great the main problem is that I am having an error with my backup software called retrospect....Retrospect says to use it you must be running samba 3.0.6 my windows machines work just fine but I keep getting this error message when trying to use the backup software. Insufficient permissions. I think upgrading to dapper might do the trick Ill try that and repost as soon as I figure it out. All I want to do is have the my documents folder backup automatically to my network share. It seems to be harder than I thought anybody out there know any software that would work? Ill be back.....

---

### Post by ttallos on 2006-02-21
The fix was instead of messing with samba (cause I need a stable system) I just found backup software that worked with the existing system. Backup4all 3. Thanks for all the replies.

---

### Post by Robgould on 2006-02-21
Glad you got it working.

---

