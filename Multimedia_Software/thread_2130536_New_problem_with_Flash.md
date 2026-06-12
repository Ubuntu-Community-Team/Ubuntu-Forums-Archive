---
title: "New problem with Flash"
date: 2013-03-29
forum: Multimedia Software
---

### Post by grey1beard on 2013-03-29
My wife's laptop, Sony Vaio AMD 32 bit chip, runs Ubuntu 11.10, and until yesterday we had no problems running videos on the BBC news pages(or anywhere else), but now as soon as she clicks on a video, BBC or Youtube, the screenshot attached shows what pops up.
Clicking on the bottom line then allows the video to play, but it would make life a little easier if this was not necessary.

I started hunting for solutions this evening and found an April 7th 2012 thread posted by lovinglinux, Flash 11.2.202.228, and tried solution 1(disabling hardware acceleration) but to no avail. Tried modifying the /etc/adobe/mms.cfg file, but there isn't one(yes, I can see hidden files).
I then looked at solution 2 - Downgrade Flash, but on searching for the .mozilla/plugins folder discovered that there isn't one.
Find this curious, but may be a clue !!
I then looked in the Software Centre for Flash and discovered that it isn't installed. Even more curious.

Could someone spell out my next step please ?

Many thanks,
John

PS The same pop up appeared when I launched the upload manager !

---

### Post by Yellow Pasque on 2013-03-30
> Could someone spell out my next step please?
1. Search your filesystem for libflashplayer.so
2. When you find it, delete it.
3. Install flashplugin-installer package

> It's like doing jigsaw puzzles in the dark.
If you didn't install the plugin to ~/.mozilla/plugins and you didn't use the package manager to install it, that probably means you manually dumped it somewhere in /usr, which is a bad idea for Debian/Ubuntu. Don't do that again, unless you like doing jigsaw puzzles in the dark.

---

### Post by grey1beard on 2013-03-30
> **Temüjin said:**
> 

If you didn't install the plugin to ~/.mozilla/plugins and you didn't use the package manager to install it, that probably means you manually dumped it somewhere in /usr, which is a bad idea for Debian/Ubuntu. Don't do that again, unless you like doing jigsaw puzzles in the dark.

I've completed a search, and found two copies, the first /opt/AdobeAIR/Versions/1.0/Resources/1.0/libflashplayer.so, dated 8June 2011, probably when I first set up her laptop, and the second, dated 01Nov 2011, in /usr/lib/mozilla/plugins/, as you suspected.
No memory of any such activity on my part, but willingly accept slapped wrist.

I assume that I delete both copies, then follow your instruction to install the fpplugin installer ?

John

---

### Post by grey1beard on 2013-03-30
Just noticed that the 'Move files to rubbish bin' for these files is greyed out, so I assume that I'm going to need to use Terminal to remove them ?
John

---

### Post by Yellow Pasque on 2013-03-30
You'll need root permissions to delete them, so:
```
sudo rm /opt/AdobeAIR/Versions/1.0/Resources/1.0/libflashplayer.so  /usr/lib/mozilla/plugins/libflashplayer.so
```
or start nautilus with root permissions if you prefer to use the GUI to delete them:
```
gksu nautilus
```

---

### Post by grey1beard on 2013-03-30
Happy with the cli, but thanks for spelling out the code for me.
Many thanks for your help ,
John

---

### Post by grey1beard on 2013-03-30
Not quite there yet :(

I used software centre to install the package, then restarted the laptop, then went to the BBC newspages.
If I click on a video clip, while the Adobe warning no longer appears, neither does the video - just displays a white space.
I then went to a youtube video, and the result was the same, just a white space in the video frame.
Tried a couple of times, closing the browser, then tried closing down and doing a cold boot, but so far the same result.
I then looked in the two original locations for libflashplayer.so, but couldn't see them, so I'm now going back to your first instruction, and doing a search for libflashplayer.so in the whole file system.

It's just found it in /usr/lib/flashplugin-installer/libflashplayer.so, so I await your instruction of where to put it (hehe !)

John


John

---

### Post by Yellow Pasque on 2013-03-30
So if you go to Tools -> Add-Ons in Firefox, does it show the Flash plugin?

EDIT: And you did restart Firefox if you had it open when installing the plugin, correct?

---

### Post by grey1beard on 2013-03-30
Firefox/Add-ons/Plugins shows Shockwave Flash 11.2 r202 updated 30/03/13, i.e. today.

I'm fairly sure that Firefox was closed while I was intalling the flashinstaller, and I then opened it to see if it then worked correctly.

John

---

### Post by grey1beard on 2013-03-30
would it do any harm to try installing a copy of the libflashplayer.so file in the AdobeAIR folder, as before ?
John

EDIT
I've just found an old thread of mine where I had the same problem on a 64 bit desktop pc where I was running iplayer as a 32bit.
The proffered solution was to send a copy of libflashplayer.so to /usr/lib/mozilla/plugins folder, so I'm now wondering if that would be the solution in this case.
Any harm in trying ?
EDIT 2
Tried the last idea, but it had no effect, so I've removed it.
EDIT 3
Tried the first idea but that didn't have any effect either, so again deleted it.

---

### Post by grey1beard on 2013-03-30
I've temporarily re-installed a copy of libflashplayer.so into the places where it was originally, in order that video clips will now run again, albeit with clicking on the pop-up.

The only other piece of information that I've gleaned is that the shockwave plugin uses a link to another link in order to get to the file libflashplayer.so in the mozilla/plugins folder.

I've just retraced my steps, and since replacing the file with a copy that I had, the Add-ons Manager/plugins window now shows two copies of the Shockwave plugin, with one of them carrying a warning - "*SF is known to be vunerable and should be updated*" .

John

---

### Post by grey1beard on 2013-03-30
Still searching and learning.
Since installing the flashplayer plugin as per your post #2, I now find another copy of libflashplayer.so in /usr/lib/flashplugin-installer.
This one, however, is a different copy to the others, 17.4MB compared with the others at 17.0MB.

Resume.

Add-ons manager has two shockwave plugins. 

The enabled one, which produces the grey pop-up that needs clicking on to run the video, 11.1 r102, carries the "..vunerable, should be updated" warning, but also says "Last updated 30/03/13" - this date may come from my re-install action.

The disabled one, which when enabled instead produces a blank window, is version 11.2 r202 "Last updated 30/03/13".

I have three copies of libflashplayer.so in the following locations -

1.  /opt/Adobe AIR/Versions/1.0/Resourses/  (17,047,244 bytes, and dating from 2011)
2. /usr/lib/mozilla/plugins/ (same version as above)
3. /usr/lib/flashplugin-installer/  (17,418,724 bytes, the current version)

John

---

