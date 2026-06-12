---
title: "[SOLVED] mythfilldatabase error code 512?"
date: 2007-11-27
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-27
Running mythfilldatabase from the command prompt works fine, but not when it is run automatically from myth.  Here;s the error as reported by mythweb's backend status page.


```
Last mythfilldatabase run started on 2007-11-27 02:00 and ended on 2007-11-27 02:00. FAILED: xmltv returned error code 512.
```

---

### Post by ubnewbie2 on 2007-11-27
I have googled some info that suggests it is a problem finding the config file which is stored in the .mythtv directory under the user's home.  If that is the case, and I see MANY people having this trouble, then this is a poor place to put it, as, apparently, mythtv might not be running as the user that creates the file.  In fact, on mythbuntu, I see, in addition to my user name, a user called mythtv, and I also note that some distributions run mythtv as root.  So to avoid having to copy the config file to all those user's homes, it would make sense to put the config file somewhere common, /etc, or /usr/local/mythtv perhaps.

Anyway, what user does mythbuntu run mythtv as?  I am taking a punt on the user 'mythtv' and so I have copied the xmltv config file to that user's home.  We shall see if it works tomorrow....

---

### Post by aidan_curtis on 2007-12-07
same problem here

---

### Post by superm1 on 2007-12-07
The backend runs as the 'mythtv' user.  The frontend runs as the user you have created.

If it indeed does need to be in /home/mythtv/.mythtv, let us know.

---

### Post by ubnewbie2 on 2007-12-07
Sorry, I  meant to update this thread a few days ago.  All is working.  Just put a symlink in /home/mythtv/.mythtv to point to the one in your home

```
 
cd /home/mythtv/.mythtv
sudo ln -s /home/<your_user_name>/.mythtv/au.xmltv
```

then whenever you change it, it changes in both places, and both mythtv and your own user can run mythfilldatabase correctly

---

### Post by Steve Goodey on 2008-05-17
```
cd /home/mythtv/.mythtv
sudo ln -s /home/<your_user_name>/.mythtv/au.xmltv
```

In my case instead of au.xmltv it was Antenna.xmltv

Make sure, if you copy the code example, you replace with the correct name for your xmltv file.

Regards, Steve

---

