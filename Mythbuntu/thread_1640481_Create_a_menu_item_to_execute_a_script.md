---
title: "Create a menu item to execute a script?"
date: 2010-12-07
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-12-07
Since I updated to 10.10 my remote has been pretty retarded but I've found a way to get it working well enough.  Basically, any time I reboot I have to enter this command (screen /dev/ttyUSB0 9600) in the terminal to get my remote to start working again.  I would now like to save this command as a script and then create a menu item in Mythfrontend to execute the script.  This way if my wife or I have to reboot we can simply use the keyboard to select the menu item and then have our remote working again.  This is what I did.

1. Created a file called fixremote and stored it in my home directory. I put that command in the file.
2. sudo chmod +x fixremote
3. sudo chown [myusername] fixremote
4. sudo chgrp [myusername] fixremote
5. I then edited /usr/share/mythtv/themes/defaultmenu/main_settings.xml and added the following:

    <button>
        <type>SETTINGS_GENERAL</type>
        <text>Fix Remote</text>
        <action>EXEC /home/[myusername]/fixremote</action>
    </button>

For some reason though it doesn't work.  Nothing appears to happen.  Is there something I'm missing?  The menu item does appear in the settings menu but that's as far as it goes.

Steps 3 and 4 may not have been necessary but they were owned by root root and so I thought maybe that was preventing the script from executing.

---

### Post by thatguruguy on 2010-12-07
Have you tried running mythfrontend from a terminal to see what is happening?

What happens when you just double-click on the script?

---

### Post by nickrout on 2010-12-07
probably need to put the full path to the screen conmmand in the script, as it is probably executed without a full PATH statement.

But you would be FAR better putting this in a bootup script. like /etc/rc.local.

```
nick@media:~$ cat /etc/rc.local
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

exit 0

```

---

### Post by Meph1st0 on 2010-12-07
I didn't try running mythfrontend in a terminal.  I'll have to give that a try when I get home.  The script works if I double click on it using thunar file manager.

I've actually tried putting it in the rc.local file but for some reason that doesn't work either.  However, as you suggested I might have to include the full path to the screen command.  If I can get it working that way then maybe I'll reattempt the rc.local file again.

umm...would you by chance know the full path to the screen command?

---

### Post by nickrout on 2010-12-08
I could tell you but it's better to teach you a new trick :)

```
which screen
```

---

