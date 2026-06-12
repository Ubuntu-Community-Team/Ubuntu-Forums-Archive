---
title: "Set sound volume on startup"
date: 2009-07-06
forum: Multimedia Software
---

### Post by thegentleman on 2009-07-06
Hello,

I searched the forums and asked Google. Only the latter came up with a hit that came somewhat close to what I want.

What I want, is to default the volume to 50% on startup. Sometimes I log off my machine leaving the volume at 100% which is rather uncool when starting up again.

The hit from Google led to stackoverflow ([http://stackoverflow.com/questions/414894/set-ubuntu-sound-volume-on-boot](http://stackoverflow.com/questions/414894/set-ubuntu-sound-volume-on-boot)), but the author admitted it wasn't a great solution, since the opening sound (the tribal drums) wasn't affected by the script. One user suggests to set the levels when shutting down, but I'm not sure how I should do this.

Please note I'm relatively new to scripting and Ubuntu altogether. Perhaps you could assist me in getting this done.

Thank you

---

### Post by wojox on 2009-07-06
What app plays sounds on your system?

---

### Post by thegentleman on 2009-07-06
ALSA.

I'm saying it's ALSA because I *think* it does. In what way can I verify this?

---

### Post by thegentleman on 2009-07-07
I solved my issue with the following:

Adjust the volume to the desired level
Open a terminal and type the following command 
```
sudo alsactl store
```

Next, edit the following file: /etc/init.d/alsa-utils
Search for the phrase 
```
stop)
```

below that should exist a line which looks like this:
```
store_levels "$TARGET_CARD" || EXITSTATUS=1
```

Comment out that line (place a # in front)
Save your file and you're done.

By taking these steps you stored your desired settings once and prevented the system to overwrite these settings when shutting down. I tested it, and it works. These settings are loaded before the tribal drums.

---

### Post by nachocual on 2009-09-08
I've done everything you said and it works, because the sound that plays at gdm start is the right volume.

But when I enter my session the volume goes back to the level it was before rebooting.

If I run
```
sudo /etc/init.d/alsa-utils restart
```
it goes to the desired level, so the changes are working.

So I supose gnome is saving the volume level for my user somewhere. Any ideas?

---

