---
title: "mythbuntu-control-centre problem..."
date: 2016-05-28
forum: Mythbuntu
---

### Post by Pieter_Meiring on 2016-05-28
Opened mythbuntu-control-centre.
Hit plugings button.
Selected enable plugins and MythBrowser.
Hit apply.
 
Error message comes up:
"The Plugins plugin is not fully filled out.Please complete it before proceeding."

Similar error occurs with trying to enable libdvdcss.

What am I doing wrong!!??

---

### Post by Pieter_Meiring on 2016-05-28
Tried running mythbuntu-control-centre  with --debug flag set.
No relevant output prior to error message coming up.

---

### Post by Pieter_Meiring on 2016-05-29
Problem (partially) soled by a complete reinstall of mythbuntu (16.01).
"Plugins plugin not complete was still there on initial startup but was careful not to do anything until I went through and completed the standard backend and frontend setups.
Trying mythbuntu-control-centre then worked ok for enabling plugins but NOT for "install libddcss" which seems to be expecting the old format packages and looks for an "install-css.sh" file. The latest libdvd-pkg package does things differently...

Hence: There is still a bug in mythbuntu-control-centre that needs fixing...

---

### Post by iry100fan on 2016-05-30
I am also having issues with the Mythbuntu Control Center...

[LIST]
[*]I also get the message "Exception in applyStateToGUI of plugin Plugins" "Disabling Plugin." when first starting it up. 
[*]Under "MySQL Configuration" screen.  If I test the backend connectivity (which passes) and then click on "Apply", the control center locks up. 
[*]I am unable to add or remove any plugins.  Changing plugin settings and clicking on the "Apply" button brings up the "Apply Settings" confirmation dialog but the "Apply" button is disabled 
[/LIST]

I have tried re-installing Mythbuntu 16.04 a few times and these problems appear consistently.

Thanks.

---

### Post by Frederico_Zenozzog on 2016-06-01
I've been driven crazy by mythbuntu/16.01/mythtv 0.28 over the last week or so; the issues you report, mythfilldatabase crashing, EPG not filling, [remote frontends not working]("http://ubuntuforums.org/showthread.php?t=2326359")....

Long story short, it came down to the bind-address in /etc/mysql/my.conf being ommitted. Once that was corrected everything started behaving itself.

---

### Post by dsfatwork on 2016-06-02
I had the same problem with the control center in a new 16.04 mythbuntu install.  I could not assign a password to mythweb.  The error that came up indicated an issue in plugins.py, something about the mythweb_password_combobox.  Looking through the file (usr/share/mythbuntu/plugins/python/plugins.py) I noticed that mythweb_password_combobox was really mythweb_password_combobox1 and only two (line 139 and 145) were still mythweb_password_combobox.

I changed these to mythweb_password_combobox1 and that fixed my problem.

---

