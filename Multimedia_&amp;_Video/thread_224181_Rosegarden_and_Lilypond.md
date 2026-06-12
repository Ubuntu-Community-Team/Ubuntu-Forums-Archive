---
title: "Rosegarden and Lilypond"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by jsmanness on 2006-07-27
Hi Everyone,

I just installed Ubuntu several days ago and I have had success getting JACK, ALSA, and other programs working.  The only two programs that have been giving me problems are Rosegarden and Lilypond.  I am able to download from the Synaptic Package Manager and it says that I successfully installed the programs, but when I look for the two applications, neither of them are there under Applications>Sound & Video.  I have been reading the threads trying to find an answer to this but I can't seem to figure this one out.

Anyone's help would be appreciated!

Jon M.

PS - Thank you to whomever made the Ubuntustudio website!  It got my laptop ready to go!

---

### Post by Hanj on 2006-07-27
Sometimes applications don't add themselves to the menu properly. Did you try launching the programs from a terminal? 

In case you don't know how to do it: choose Applications>Accessories>Terminal and type rosegarden (I would guess that's the command, you can always use the tab key to auto-complete and find out the name of the command). If this works, you can add it to the Gnome menu yourself using the Alacarte menu editor.

---

### Post by goodmanbrown on 2006-07-27
Just in case you haven't noticed this already...

The "rosegarden" package in the Ubuntu repos intalls Rosegarden 2, which is ancient.  You will probably want Rosegarden 4, which you can get by installing the "rosegarden4" package in Synaptic.

That little quirk left me confused the first time I did an "apt-get install rosegarden"

---

### Post by greenstar on 2006-07-27
1. Open Application->Accesories->Alacarte Menu Editor
2. Click on the category you want the icons in. 
3. File->New Entry
4. Fill in the lines appropriately.

Example:

Name: Rosegarden
Comment: Whatever-you-want-here
Command: rosegarden
Icon: Location-of-icon-file-here

Hint: look in /usr/share/pixmaps, /usr/share/icons & /usr/bin/name-of-app for the icon that goes with the app in question.


If you don't find it there, you can google for a suitable icon image. 

For example:
To find an icon for Rosegarden:
1. Go to [http://www.google.com]("http://www.google.com/") enter "rose" then click [COLOR=black]images[/COLOR] just above the place where you enter search terms. Then choose the image that best suits your needs. I would use the blue rose image at [http://shop.butterflywisper.com/glycerin_soap_mrose1.shtml](http://shop.butterflywisper.com/glycerin_soap_mrose1.shtml) because it has a simple, clear picture with a solid white background. 

2. I would then right click on the image and select "Save Image As..." then I'd clean up the filename from "rose_blueLt1_small.jpg" to something simpler like "rose.jpg" and save to the Desktop. 

3. Next, I open the image in GIMP. 

4. Once in GIMP, I click Image->Scale Image then I enter 64 in the dimension (Width or Height) that is the largest and hit enter. This should automatically scale the smaller dimension to the new size which is proportionally smaller than the new size of the larger dimension. Then click "Scale". 

5. Next click File->Save as... click "Select File Type (By Extension)" and choose "X PixMap image" from the list and click save, then close GIMP.

6. Open a terminal Applications->Accesories->Terminal and enter:
```
sudo cp ~/Desktop/rose.xpm /usr/share/pixmaps
``` 
7.Then open up Alacarte Menu Editor again, and select the category on the left you put Rosegarden into, then double click the rosegarden entry on the right when the list appears.

8. Click the Icon box and when the dialog box opens, be sure you're in /usr/share/pixmaps, if not, browse there with the Browse button on the top right. once in /usr/share/pixmaps Click on the rose.png icon, then click "OK", the icon should now be visible on the rosegarden entry. Click close on the rosegarden entry.

9. You should now see the icon with the rosegarden entry in Alacarte. Then click close on Alacarte. Check your menu, if you see the entry, but no icon, then do the following in Terminal:
```
killall gnome-panel
``` to refresh the menu.

Hope this helps,
Greenstar

---

### Post by jsmanness on 2006-07-27
Thank you everyone.  Rosegarden and lilypond are working just fine now!  A special thanks to greenstar for the simple directions to adding an app. to the menu editor!

---

### Post by greenstar on 2006-07-27
> **jsmanness said:**
> Thank you everyone.  Rosegarden and lilypond are working just fine now!  A special thanks to greenstar for the simple directions to adding an app. to the menu editor!

You're welcome.:D I can't speak for everyone, but it's gratitude such as yours that motivates me to help others. Thanks for the appreciation. 

Greenstar

---

