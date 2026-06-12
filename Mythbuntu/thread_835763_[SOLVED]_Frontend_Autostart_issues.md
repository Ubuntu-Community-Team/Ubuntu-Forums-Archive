---
title: "[SOLVED] Frontend Autostart issues"
date: 2008-06-20
forum: Mythbuntu
---

### Post by driedsponge on 2008-06-20
I'm running a frontend and trying to get it to play nicely with a wireless network.  So far the setup has been great, and I have had relatively few issues.  My problem is that the wireless adapter takes a second or two longer to authenticate than mythfrontend takes to start up, so on initial startup, mythfrontend doesn't see the backend server.  If I exit out of that and restart the frontend, everything works great.  

My question, i guess, is how do I set a delay in the start of the frontend on 8.04 so that it gives teh wireless card time to connect to the network?

---

### Post by jlagrone on 2008-06-20
I don't know if there is any specific way build into mythbuntu to do this, but the following should work.

create a "delaymythtv" script

```
sudo nano /usr/bin/delaymyth.sh
```

Then something along the following should work (change the number after "sleep" to change the delay - it should be in seconds)

```

#!/bin/sh
sleep 10
/usr/bin/mythfrontend

```

Now, you'll want to make that script executable ...

```
sudo chmod +x /usr/bin/delaymyth.sh
```

Mythtv starts via a file in ~/.config/autostart/ I believe it is mythtv.desktop but I don't have access to my machine at the moment to confirm.  From the terminal, ls /.config/autostart/ will list the files, there should only be one and that is the one you want, but assuming the mythtv.desktop is correct, this is what you will want to do

backup the file, just to be safe
```
cp ~/.config/autostart/mythtv.desktop ~/mythtv.desktop.bak
``` 

edit mythtv.desktop (you may or may not need sudo to do this, I don't remember)
```
nano ~/.config/autostart/mythtv.desktop
```

it should look something like this

```

[Desktop Entry]
Encoding=UTF-8
Name=something ....
Comment=something ...
Exec=something ....
Icon=
Type=Application 

```

You'll want to change the Exec line to the following

```
Exec=/usr/bin/delaymyth.sh
```

Then Ctrl+x to exit and y(es) to confirm changes.  (if it won't let you, re-run the command above with sudo)

If for whatever reason this doesn't work or you just want to remove it

```
sudo rm /usr/bin/delaymyth.sh
sudo rm ~/.config/autostart/mythtv.desktop
sudo cp ~/mythtv.desktop.bak ~/.config/autostart/mythtv.desktop

```

---

### Post by driedsponge on 2008-06-21
That's it.  Thanks, works much better.  I changed the Sleep command to 5 seconds, but other than that, the startup has no issues anymore.

---

### Post by angelsguitar on 2010-01-22
Thanks, this script solved the problem on my Mythbuntu 9.10 frontend/backend

---

