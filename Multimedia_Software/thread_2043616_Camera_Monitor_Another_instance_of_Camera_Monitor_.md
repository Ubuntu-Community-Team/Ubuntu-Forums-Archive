---
title: "Camera Monitor: Another instance of Camera Monitor is already running!"
date: 2012-08-16
forum: Multimedia Software
---

### Post by Marric on 2012-08-16
The problem is that the **.**cameramonitor.pid file in the home directory is not deleted every time at shutdown or reboot.

The solution is to delete the file with a script at startup.
```
sudo gedit /etc/rc.local
```Paste the following
```
rm /home/USER/**.**cameramonitor.pid
```Replace USER with your username

The script then looks like this
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rm /home/USER/**.**cameramonitor.pid

exit 0
```

---

### Post by EnergeticSoul on 2013-02-01
Didn't work for me. I mean when I tell it to run, it runs but it never loads on my screen, then when I try again, five minutes later, the same message pops the above solution intends to solve pops up again. Any ideas?

I just thought that this would be good to post here since this topic is among the first page of results in Google and how the problem is so similar that if a solution is to be found in this topic that people with the same persistent problem would quickly and easily be able to solve their issue.

My apologies if I am mistaken.

---

### Post by Marric on 2013-02-15
Another solution is to edit the cameramonitor file
```
gksu gedit /usr/bin/cameramonitor
```at line 110 change utils.pid_clean() to utils.pid_delete()
```
    # Callback: exit
    def exit_callback(self, widget):
        gtk.main_quit()
        utils.pid_delete()
        return
```

---

