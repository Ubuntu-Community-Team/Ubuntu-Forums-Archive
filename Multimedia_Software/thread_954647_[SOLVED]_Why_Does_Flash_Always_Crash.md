---
title: "[SOLVED] Why Does Flash Always Crash?"
date: 2008-10-21
forum: Multimedia Software
---

### Post by joey-elijah on 2008-10-21
Less an "agony" more a curiosity - Why, in firefox, does flash crash firefox every few times it's used?

Every 4/5 youtube videos and et voila! - CRASHTASTIC occurs. 

Is this just me?

---

### Post by billgoldberg on 2008-10-21
> **joey-elijah said:**
> Less an "agony" more a curiosity - Why, in firefox, does flash crash firefox every few times it's used?

Every 4/5 youtube videos and et voila! - CRASHTASTIC occurs. 

Is this just me?

Because you're not up to date.

In a terminal do this:

```
sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
```

Now, remove the libflashplayer.so file from /home/username/.mozilla/plugins

Then go here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

And download the ubuntu .deb file.

Double click to install it.

No more crashes.

---

### Post by joey-elijah on 2008-10-21
i didn't have a 'plugins' folder in my home/joey/.mozilla and after looking through the different folders there are (songbird, thunderbird, fennec etc) i didn't find a libflashthingy.so 

installed the deb, though this is what i remember doing first time around... hmm. 

many thanks though!

---

### Post by joey-elijah on 2008-10-22
just to let everyone/anyone know - this did the trick!

---

### Post by eternalnewbee on 2008-10-22
Now, remove the libflashplayer.so file from /home/username/.mozilla/plugins

I don't have such a folder...

---

### Post by eternalnewbee on 2008-10-22
What to do?

---

### Post by nufros on 2008-11-21
> **billgoldberg said:**
> Because you're not up to date.

In a terminal do this:

```
sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
```

Now, remove the libflashplayer.so file from /home/username/.mozilla/plugins

Then go here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

And download the ubuntu .deb file.

Double click to install it.

No more crashes.


Thank you very much!! No more crashes \\:D/

---

