---
title: "Flash woes"
date: 2018-03-12
forum: Multimedia Software
---

### Post by charlie_bravo2 on 2018-03-12
I have a brand new clean install of Ubuntu 17.10.  I prefer to not use chrome, and wish to use Firefox exclusively.  I have run the command to install Flash found several other places in these forae, and it seems successful, in that when I check the Firefox plugins list, I see:

Shockwave Flash 13.1.2.3
Shockwave Flash 13.1. r2
libfreshwrapper-flashplayer.soapplication/x-shockwave-flash (Shockwave Flash: swf),
application/futuresplash (FutureSplash Player: spl)

Looks good so far, but when I access certain sites that depend on Flash (miniclip.com in particular), I get the following response:

Failed to load "libpepflashplayer.so"
Freshwrapper is a translation layer which needs
PPAPI plugin backend.  Ensure your system have
"libpepflashplayer.so" available.
Paths tried:
/opt/google/chrome/PepperFlash/libpepflashplayer.so
/opt/google/chrome-beta/PepperFlash/libpepflashplayer.so
/opt/google/chrome-unstable/PepperFlash/libpepflashplayer.so
/usr/lib/adobe-flashplugin/libpepflashplayer.so
/usr/lib/pepperllashplugin-nonfree/libpepflashplayer.so
/usr/lib/PepperFlash/libpepflashplayer.so
/usr/lib64/PepperFlash/libpepflashplayer.so
/usr/lib/chromium-browser/PepperFlash/libpepflashplayer.so
/usr/lib64/chromium-browser/PepperFlash/libpepflashplayer.so
/usr/lib/chromium/PepperFlash/libpepflashplayer.so
/usr/lib64/chromium/PepperFlash/libpepflashplayer.so
/opt/chromium/PepperFlash/libpepflashplayer.so
/usr/lib/pepperflashplugin-installer/libpepflashplayer.so



Not exactly what other information would be helpful here, nor am I exactly sure what to try next.


Thanks in advance!

---

### Post by monkeybrain20122 on 2018-03-12
How did you install flash? Your version is vastly outdated. The current version is 28.xxxx Get rid of your version first and then install the current version from the repository:

```

sudo sed -i.bak "/^# deb .*partner/ s/^# //" /etc/apt/sources.list
sudo apt update
sudo apt install adobe-flashplugin
```


**Edited**: It looks a like dodgy site, the kind that spread viruses, malware and adware around. This is probably what flash is only good for nowadays so I really don't get why you want to go there,--and with a totally outdated version of flash to boot.  I went on a 18.04 test partition and a test Firefox profile, on a machine I am planning to give away, so I don't care.

---

### Post by charlie_bravo2 on 2018-03-13
Ran the commands you shared.  Symptom changed.  I open windows with Flash content, click on Allow Content, and get the following results.  Do you have any ideas?

---

### Post by monkeybrain20122 on 2018-03-13
Flash just crashes. In Firefox, go to Tools > Add-ons > Plugins  which version of flash does it say? If it is 28.xxx it is the right version. Then close firefox and delete the hidden folder .adobe in your home and try again, may be your old version has corrupted some settings.

```
rm -r ~/.adobe
``` (note the "." in front)

---

### Post by charlie_bravo2 on 2018-03-14
I like when my problems aren't easy to fix.

As you suggested, I checked my version of Flash in PlugIns in Firefox, and the version is the same as before.  Closed Firefox and ran the command you suggested.  received a  "Directory not found" message.  Then changed directories to root  (cd /) and ran: ```
sudo find -name .adobe
``` Got told permission was denied for '.run/user/1000/gvfs', but I don't think that's an indicator of an issue, but otherwise, there was no result.  I doubt that there is no .adobe, though I suspect it might have a different name.  Suggestions?

---

### Post by monkeybrain20122 on 2018-03-14
Did you remove your flash 13? You probably can't delete .adobe because flash is still running.

And why do you need sudo for the find command? You can see it if you just open your file manager and choose "show hidden" from menu or press ctrl+h. You can delete it by hand.

---

### Post by Yellow Pasque on 2018-03-14
> libfreshwrapper-flashplayer.soapplication/x-shockwave-flash (Shockwave Flash: swf)

You should remove freshplayer. It is no longer needed since Adobe has reversed course and offers updates for NPAPI.

---

### Post by charlie_bravo2 on 2018-03-15
> **monkeybrain20122 said:**
> Did you remove your flash 13? You probably can't delete .adobe because flash is still running.

And why do you need sudo for the find command? You can see it if you just open your file manager and choose "show hidden" from menu or press ctrl+h. You can delete it by hand.

When I ran find without sudo, I got several "permission denied" messages for particular folders.  I ran "sudo find" I got no permission denied messages.  Trying to be thorough in my search.

Charlie

---

