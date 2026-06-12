---
title: "Cant click on flash buttons"
date: 2010-03-29
forum: Multimedia Software
---

### Post by GregFisk25 on 2010-03-29
I have tried the fix  			 				* Hit ALT+F2 and enter
* gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
* add the following line BEFORE the last line of text
* export GDK_NATIVE_WINDOWS=1

But I DONT have that file

I have searched for hours and hours.

I can rightclick on the player and get to its options, but left clicking doesnt work

Please help me.

Thanks so much

---

### Post by Icarus315 on 2010-03-29
The easiest way to get flash to function fully is to turn off visual effects.  Go to: System > Preferences > Appearance and then go to the Visual Effects tab and select "None."  You won't have any Compiz effects but flash will work fine.  This is the only reliable solution I have found for flash.  A work-around if you want to keep effects and just need the occasional left-click like to start YouTube videos is to right-click somewhere on the flash object to bring up the menu then double-left-click on the element you want to left-click and that will work that one time.  You can repeat those steps as often as you like but it is not the ideal solution.

---

### Post by GregFisk25 on 2010-03-29
My visual effects are off.  I am running netbook remix
And the right click left click didnt work at all

---

### Post by Icarus315 on 2010-03-29
Sorry then, that's whats done the trick under the Gnome desktops I've been using.  Are you even using Gnome with remix?  Perhaps that's why you don't have the other text file as well?

Edit:  Right-click then DOUBLE-left-click real fast on what you want to left-click...

---

### Post by GregFisk25 on 2010-03-29
I am not certain if I am using Gnome.  I am definately using the remix.  I only just installed it, so it is how it comes.

I am new to this.

---

### Post by kh1116 on 2010-03-29
Enter in terminal:
```
gconf-editor /apps/panel/global 
```

Find tooltips enabled... if its unchecked, check it. If not, then I dont know.

---

### Post by GregFisk25 on 2010-03-30
Tried the tooltips with no difference.
Why is something so basic so hard????

Also, I just ran an update and now firefox is called IceWeasel.  It did not change on my desktop version....

---

### Post by GregFisk25 on 2010-03-30
I found a partial workaround.
There is a site you can go to on the macromedia site that allows you to enable your camera on certain sites.
Not really good enough tho...

---

### Post by kh1116 on 2010-03-30
in the firefox address bar, type ```
about:plugins
```

copy and paste it here

---

### Post by GregFisk25 on 2010-03-30
**Shockwave Flash**

 File:  libflashplayer.soVersion:   Shockwave Flash 10.0 r45   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  **Shockwave Flash**

 File:  libflashplayer.soVersion:   Shockwave Flash 10.1 d51   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes

---

### Post by kh1116 on 2010-03-30
ok, it appears that you have two versions of flash installed: the latest stable version and a beta version. i would suggest removing one, or flash player will act strange. i couldn't get firefox to play flash videos at all yesterday when i had the same issue.

you should have an area on the portion "about:Plugins" that looks similiar to this. ```
File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
``` i would suggest trying to uninstall the beta version, although i suppose you could try removing either one if you have confidence in the beta's ability. i'm just going to give instructions on how to remove the beta. 

so find the ".so" location under "Shockwave Flash 10.1 d51" and copy down the file location. remove ```
libflashplayer.so
``` from the end of the file location and open up a terminal. ```
sudo nautilus
``` plus a space and then type the file location. 

for example, mine would be ```
sudo nautilus /var/lib/flashplugin-installer/
``` but the location for your file is probably different.

enter your command and password, and you will get a nautilus window inside a folder with a bunch of plugins. find the file named "libflashplayer.so" inside that folder and delete it.

there are ways to delete files using only terminal, but for learning how to do things yourself, sudo nautilus has always been helpful for me

---

### Post by lidex on 2010-03-30
This is a good/simple method. Go here:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
Download the "adobe_flash_installer-ubuntu.tar.gz" file to your desktop. Right-click on that file and select "Extract here". Double-click on the resulting file. Click the remove button first and let it complete. Now click the install button. Restart browser.

---

