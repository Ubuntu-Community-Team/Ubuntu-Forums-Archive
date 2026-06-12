---
title: "System-config-samba crashes"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by timczer on 2010-05-27
When I run from the command line, I get this output:

Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 82, in __init__
    self.samba_data = sambaParser.SambaParser(self)
  File "/usr/share/system-config-samba/sambaParser.py", line 185, in __init__
    self.parseFile ()
  File "/usr/share/system-config-samba/sambaParser.py", line 228, in parseFile
    section = SambaSection (token.value)
  File "/usr/share/system-config-samba/sambaParser.py", line 49, in __init__
    raise Error ("section %s already defined" % (name))
NameError: global name 'Error' is not defined

I have removed and re-installed and get the same crash.  I googled this and did not come up with much.

Does anyone know what I can do to make this work?

---

### Post by RJRM on 2011-01-30
Hello.

I had that problem, with the same output. It's about the samba parser (python)

I have checked my smb.conf in /etc/samba and I found that I had a section duplicated (it was printers). I think system-config-samba crashes when there are two or more sections with the same name.

When I removed the section duplicated, I was able to start system-config-samba without any problem.

I know your post was written several months ago, but I found it when I was searching for solutions, so I tell you my experience if it could be useful. Your problem could be the same or not.

---

### Post by Cincinnatux on 2011-06-10
Thanks for sharing this discovery, as it helped me when I ran into this problem just today.  There are so many details involved with networking that it can be ulcer-generating to track them all down when the network fails.  I dunno how my config file ended up with duplicate entries, but such was the case.  Anyhow, thanks to your post, I was able to identify this mistake, at least.  :) 

> **RJRM said:**
> 

I have checked my smb.conf in /etc/samba and I found that I had a section duplicated (it was printers). I think system-config-samba crashes when there are two or more sections with the same name.

When I removed the section duplicated, I was able to start system-config-samba without any problem.


---

