---
title: "NetworkManager Sound Notifications"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by madjoe on 2010-05-22
I think it would be quite nice if we could configure NetworkManager to play a custom audible notification (wav file) upon establishing Internet connection and upon disconnecting from the Internet as well. Is there any workaround for this feature yet?

[IMG]http://img.youtube.com/vi/QLHKN6Dr7TU/0.jpg[/IMG]

---

### Post by madjoe on 2010-09-04
For those who would like to enable this feature, here's a workaround:

[LIST]
[*][http://bpaste.net/show/9289/](http://bpaste.net/show/9289/) -- save that as /etc/NetworkManager/dispatcher.d/99playsound and chmod +x it.

[*]Edit the last 4 lines to tell it what to do.
[/LIST]

Usecase:
If you are dealing with poor WiFi connection, downloading something and if you're afk, probably you'd like to know when your Internet connection goes offline (if you're close enough to hear a sound notification, of course).

Thanks to Seveas @ #ubuntu! =D>


99playsound:
```
#!/usr/bin/python

import os
import stat
import sys
import subprocess

# This is run as root, but mplayer should run as the user. Find the
# proc folder of nm-applet and copy its environment. Also setuid to the
# correct user so gnome-keyring accepts the connection
for d in os.listdir('/proc'):
    if not d.isdigit():
        continue
    d = os.path.join('/proc', d)
    try:
        exe = os.readlink(os.path.join(d, 'exe'))
    except OSError:
        continue
    if exe == '/usr/bin/nm-applet':
        uid = os.stat(d)[stat.ST_UID]
        env = open(os.path.join(d, 'environ')).read()
        env = dict([x.split('=', 1) for x in env.split('\x00') if x])
        os.environ.update(env)
        os.setuid(uid)
        break
else:
    # Can't find nm-applet
    sys.exit(0)

# This is called from n-m as <script> <device> <action>
if sys.argv[2] != 'up':
    subprocess.call(['/usr/bin/paplay','/home/madjoe/down.wav'])
else:
    subprocess.call(['/usr/bin/paplay','/home/madjoe/up.wav'])
```

---

### Post by Mayank Bhagat on 2011-04-01
will it work for mobile broadband . I pasted sound files in home folder and 99playsound in place but it is not working. I also didnt understand "chmod+x"
PLEASE HELP I NEED THIS.

---

### Post by patryk77 on 2011-04-01
> **madjoe said:**
> 
```
...
if sys.argv[2] != 'up':
    subprocess.call(['/usr/bin/paplay','/home/madjoe/down.wav'])
else:
    subprocess.call(['/usr/bin/paplay','/home/madjoe/up.wav'])
```

Did you replace '/home/madjoe/down.wav' and '/home/madjoe/up.wav' with your own files?

Did you save the script as /etc/NetworkManager/dispatcher.d/99playsound ?

If so, in terminal:
sudo chmod +x /etc/NetworkManager/dispatcher.d/99playsound

This sets it as an executable file, which allows it to run as a script.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for more info

---

