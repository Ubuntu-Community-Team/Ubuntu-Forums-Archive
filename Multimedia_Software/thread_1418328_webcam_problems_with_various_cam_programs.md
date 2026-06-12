---
title: "webcam problems with various cam programs"
date: 2010-02-28
forum: Multimedia Software
---

### Post by hihihi100 on 2010-02-28
Hi there:

the problem concerns an eyeshot integrated webcam:

My laptop has an incorporated webcam i am trying to make work, to no effect so far.

I have tried several pieces of software, such as Camorama, but when I try to use it, an error message appears:

"Could not connect to video device (/dev/video0). Please check connection

I have also tried Camera Monitor, but:

"Another instance of Camera Monitor is already running!

This line appears everytime I click on the Camera Monitor icon.

Any guess? tip?


K, dont call me an idiot yet... It seems need some drivers... what I read on the laptop right next to the "eye" of the cam is eyeshot. Now, what ubuntu-compatible driver should I download? Is there any site where I can find the drivers in a .deb package instead of a .zip one?

Thanks

---

### Post by fchristophersen on 2010-03-14
I had the same problem. It has something to do with file .cameramonitor.pid in your home directory. It is created when camera monitor is run, and deleted when it is closed. Perhaps your computer was not properly shutdown, so it wasn't erased. Just delete it manually, and the error message should disappear.

---

### Post by Marric on 2012-05-30
Camera Monitor - Ubuntu 12.04 Update:

If the message appears again after deleting cameramonitor.pid
then edit the following file
```
sudo gedit /usr/share/pyshared/cameramonitor/utils.py
```

Look for this function
```
**# Check if the process with pid is running**
def pid_running(pid):
...
```

and replace it with
```
# Check if the process with pid is running
def pid_running(pid):
      if os.path.isdir('/proc/' + str(pid)):
            with open('/proc/' + str(pid) + '/comm') as fd:
                  cmd = fd.read()
                  return cmd.strip() == 'cameramonitor'
      else:
            return False

```

---

### Post by Marric on 2012-08-12
My suggestions in the first post are not working anymore.

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

### Post by Marric on 2013-02-16
[http://ubuntuforums.org/showthread.php?t=2043616](http://ubuntuforums.org/showthread.php?t=2043616)
> **Marric said:**
> Another solution is to edit the cameramonitor file
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

