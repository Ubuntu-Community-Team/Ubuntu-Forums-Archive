---
title: "Flash crashes FF"
date: 2010-06-26
forum: Multimedia Software
---

### Post by KrawieC on 2010-06-26
Hi  I've got annoying problem. After i've instaled newest version of Adobe Flash Player, i have problem with his normal working. AFP crashes YT, Vimeo and all things conected with FLash.  I've tried open FF in terminal, and i got that error:  ```
The program 'firefox-bin' received an X Window System error. This probably reflects a bug in the program. The error was 'BadValue (integer parameter out of range for operation)'.   (Details: serial 85104 error_code 2 request_code 53 minor_code 0)   (Note to programmers: normally, X errors are reported asynchronously;    that is, you will receive the error a while after causing it.    To debug your program, run it with the --sync command line    option to change this behavior. You can then get a meaningful    backtrace from your debugger if you break on the gdk_x_error() function.)
``` Flas Player ver. ->10.1.53.64-1lucid1.    Do you have any idea whats's going on?

---

### Post by lovinglinux on 2010-06-27
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

BTW, does it crash in normal view or in fullscreen?

---

### Post by KrawieC on 2010-06-27
File: /usr/lib/adobe-flashplugin/libflashplayer.so      Version:Shockwave Flash 10.1 r53      It crashes in normal view.

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> File: /usr/lib/adobe-flashplugin/libflashplayer.so      Version:Shockwave Flash 10.1 r53      It crashes in normal view.

Does it crash when viewing all flash content or just videos? Does it crash all the time or occasionally?

Check if you have libmoon installed and remove it. 

Also try these commands:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Restart the browser.

---

### Post by KrawieC on 2010-06-27
It crashes all the time when I'm using YT, and other video stuff based  on Flash. I don't have instaled libmoon. This catalog that you suggested  to make it's already existed, and after I've typed those commands  nothing happened int terminal, but I restarted the browser, and YT again  crashed the browser.

---

### Post by lovinglinux on 2010-06-27
If you can at least open a YouTube page without playing the video or a flash web site, right-click on the flash content, select "Settings", then untick "Enable hardware acceleration".

See if that helps.

---

### Post by KrawieC on 2010-06-27
Ok, I've watched 2 movies and browser didn't crash, but there is one problem :D The video looks like photo slide show, one frame per 30 sec.

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> Ok, I've watched 2 movies and browser didn't crash, but there is one problem :D The video looks like photo slide show, one frame per 30 sec.

Do you have the latest driver for your video card? To check go to "System >> Administration >> Hardware Drivers".

---

### Post by KrawieC on 2010-06-27
> **lovinglinux said:**
> Do you have the latest driver for your video card? To check go to "System >> Administration >> Hardware Drivers".

Yes, I have. Also strange thing is that a music in video goes normal, witout any carshes.

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> Yes, I have. Also strange thing is that a music in video goes normal, witout any carshes.

Check if you have effects enabled. You should be able to do that from "System >> Preferences >> Appearance >> Visual Effects".

---

### Post by KrawieC on 2010-06-27
I disabled effects and video looks fine, but again FF crashed ...

---

### Post by lovinglinux on 2010-06-27
Please post the result of the command below:

```
ls /usr/lib/mozilla/plugins
```

---

### Post by lovinglinux on 2010-06-27
Try this:

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Then re-enable effects. If you still get slow frame rate, try to enable hardware acceleration again.

---

### Post by KrawieC on 2010-06-27
```
flashplugin-alternative.so             libtotem-gmp-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-mully-plugin.so
libtotem-cone-plugin.so                libtotem-narrowspace-plugin.so

```Ok, I'm going to try this version of Flash, but Do I have to uninstall previous version?

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> Ok, I'm going to try this version of Flash, but Do I have to uninstall previous version?

That command will uninstall and reinstall the same version. Some people have success after doing that.

If that doesn't help, try to start firefox in safe mode:

```
firefox -safe-mode
```

---

### Post by KrawieC on 2010-06-27
I typed first command and terminal says 

```
Package flashplugin-nonfree it is not instaled, so it can no be deleted.

```

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> I typed first command and terminal says 

```
Package flashplugin-nonfree it is not instaled, so it can no be deleted.

```

```
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-nonfree
```

---

### Post by KrawieC on 2010-06-27
I used thoes commands, but video looks the same, slide show, and I turned FF in safe mode. FF crashed with same comunicat

```
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 75367 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> I used thoes commands, but video looks the same, slide show, and I turned FF in safe mode. FF crashed with same comunicat

```
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 75367 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

What version of Firefox you are using?

---

### Post by KrawieC on 2010-06-27
Firefox 3.6.3

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> Firefox 3.6.3

I'm running out of ideas, so I would recommend trying Firefox 3.6.4 or 3.6.6, which has plugin isolation. The browser doesn't crash if the plugin fails.

You can install it by adding ubuntu-mozilla-security ppa.

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```

Then update and upgrade.

```
sudo apt-get update
sudo apt-get upgrade
```

Also, re-enable hardware acceleration and effects, otherwise it will keep the low framerate.

Let me know if flash still crashes.

---

### Post by KrawieC on 2010-06-27
I upgraded FF, now it doesn't crash, but unffortunatly Flash plugin crashes showing that screen [http://dl.dropbox.com/u/2995758/zrzut_ekranu.png](http://dl.dropbox.com/u/2995758/zrzut_ekranu.png) I don't know what should I do with this things, ehh...

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> I upgraded FF, now it doesn't crash, but unffortunatly Flash plugin crashes showing that screen [http://dl.dropbox.com/u/2995758/zrzut_ekranu.png](http://dl.dropbox.com/u/2995758/zrzut_ekranu.png) I don't know what should I do with this things, ehh...

At least the browser doesn't crash :)

Try to create a new Firefox profile. To launch the profile manager, close Firefox and start it with:

```
firefox -P
```

If that doesn't help, then try to create a new Ubuntu user (you can remove it later) and log in with that account. This way it will use default settings for everything.

---

### Post by KrawieC on 2010-06-27
OK, It works. YT doesn't crash and works fluenlty. So what was the reason thoes crashes? Do you have any idea? I use some add-ons to FF, so maybe someone develope those crashes?

---

### Post by lovinglinux on 2010-06-27
> **KrawieC said:**
> OK, It works. YT doesn't crash and works fluenlty. So what was the reason thoes crashes? Do you have any idea? I use some add-ons to FF, so maybe someone develope those crashes?

Do you have Prism or Moonlight extensions?

To recover your stuff from the old profile see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by KrawieC on 2010-06-28
Thank you very much for your advices** lovinglinux**. Now, I can use YT and it works fluently and normal! Also, I found some advices on your blog. Thanks a lot!

---

### Post by lovinglinux on 2010-06-28
> **KrawieC said:**
> Thank you very much for your advices** lovinglinux**. Now, I can use YT and it works fluently and normal! Also, I found some advices on your blog. Thanks a lot!

You are welcome. I'm glad you were able to fix it.

---

### Post by otterpkt on 2010-07-01
I had a similar problem with flash crashing.  It turned out I had an older version of flash installed under my local profile directory desktop:~/.mozilla/plugins  I removed those and followed the instructions posted earlier in this thread to install the latest flash plugin and everything worked fine.

After deleting libflashplayer.so and flashplayer.xpt from my local plugins directory I ran the following commands.  The first two were not found, but the last one installed the new flash plugin and now everything runs great.

sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-nonfree

---

### Post by texla on 2010-07-08
> **otterpkt said:**
> I had a similar problem with flash crashing.  It turned out I had an older version of flash installed under my local profile directory desktop:~/.mozilla/plugins  I removed those and followed the instructions posted earlier in this thread to install the latest flash plugin and everything worked fine.

After deleting libflashplayer.so and flashplayer.xpt from my local plugins directory I ran the following commands.  The first two were not found, but the last one installed the new flash plugin and now everything runs great.

sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-nonfree
trying this fix out... on a never ending quest to keep ff from crashing...

---

