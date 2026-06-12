---
title: "[SOLVED] Lots of trouble installing Flashplayer 10 beta"
date: 2008-05-18
forum: Multimedia Software
---

### Post by bobjenkins on 2008-05-18
Hey guys I am pretty new to Ubuntu/linux I have managed to get other things installed including flash player 9. This flash player is absolutely HORRID. 

It skips/tears/low fps when I have it open, I am attempting to watch videos on [www.gametrailers.com](www.gametrailers.com), youtube and many other sites. After a few days of constantly trying to get this to work I have read alot of other people had this problem with version9 and installing version 10 fixed it.

I am on ubuntu 8.04 . I have tried numerous many guides to install this and no luck:( Whenever I get done installing I go to firefox and type about: plugins and I still see version 9 flash player!!!

I am out of ideas:( So far I like everything better than windows. Except flash, which is a big deal for me, I would really like to try to fix this.

I am on a radeon 9800pro video card - could it be my ati drivers?
I am also using the advanced desktop effects settings compiz, is this causing a problem?

I have installed vlc, and these videos work just fine on that, as well as the standalone mplayer. 


Thank you for any response I am really at my wits end!

---

### Post by gandaran on 2008-05-18
I have tried flash 10, it works fine in youtube but doesn't work yet in the bbc webpage, so I got rid of it. it's not ready yet.
if you want to try it do this, download the file from the adobe site, extract the contents to the desktop, keep the libflashplayer.so file on desktop and delete everything else.
now go to synaptic and un-install the flash installed (flashplugin-nonfree, gnash or swfdec) next we are going to install the libflashplayer.so file in the hidden home mozilla folder, (this way you can just delete the file if you don't like flash 10)
create a new folder on desktop and rename it to **plugins**, drag the libflashplayer.so inside, now open the hidden home/user/.mozilla folder and just drag the plugins folder inside .mozzilla folder, that's all, should be working now, try the about: plugins thing for confirmation.

---

### Post by Dirty Ole on 2008-05-18
I copied the new libflashplayer.so file to /usr/lib/flashplugin-nonfree/ after renaming the original v9 file. No install-uninstall just simple file renaming, copying and if needed, deleting. (I had flashplugin-nonfree installed previously)

Also this way all the browsers have access to Flash v10.

---

### Post by bobjenkins on 2008-05-18
I have tried to put it into those folders and it always says permission denied. I have done it in the terminal (atleast I think it worked) Is there anyway to change permissions?

---

### Post by bobjenkins on 2008-05-19
I have tried this exactly like you said and its not working still, after I uninstall flashplayer it still has the flashplugin.so in the plugins folder. Did I type it wrong?

sudo apt-get remove flashplugin-nonfree 

I also tried the others and they were not installed.

When I type 

apt-get remove flashplugin-nonfree 

it says permission denied and asks me if I am root. How do I get around this?

thanks

---

### Post by gandaran on 2008-05-19
> **bobjenkins said:**
> I have tried to put it into those folders and it always says permission denied. I have done it in the terminal (atleast I think it worked) Is there anyway to change permissions?

that's one of the reasons I said to install on the home .mozilla folder, no permissions need there, you don't like the flash you just delete! easy!
for permissions to install on the file system, type **sudo nautilus** on the terminal, a root nautilus window will open up, now you can delete and copy/paste. (just a warning, sometimes files pasted on the file system in this way on ubuntu 8.04 get blocked, it's really best you use the cp or mv commands on the terminal to copy a file).
flash can be installed in the file system in /usr/lib/mozilla/plugins if you don't have the flashplugin-nonfree installed, if the flashplugin-nonfree is installed you must copy the flash file to that folder, delete the existing one first.

---

### Post by bobjenkins on 2008-05-19
Ok I have tried this method before gandaran and I was blocked while trying to manually copy and past. Then I tried the mv command.

I was not getting the file path right. Can you please help with the file path command? I have the flashplugin.so sitting on my desktop, this is what I was trying

sudo mv /home/chris/desktop/flashplugin.so usr/lib/mozilla/plugins

this is the error I have gotten
mv: cannot stat `/home/chris/desktop/flashplugin.so': No such file or directory

thanks

---

### Post by gandaran on 2008-05-19
> **bobjenkins said:**
> I have tried this exactly like you said and its not working still, after I uninstall flashplayer it still has the flashplugin.so in the plugins folder. Did I type it wrong?

sudo apt-get remove flashplugin-nonfree 

I also tried the others and they were not installed.

When I type 

apt-get remove flashplugin-nonfree 

it says permission denied and asks me if I am root. How do I get around this?

thanks

you'll have to find out where the .so file is installed, first place is the home .mozilla plugins folder, next is /usr/lib/mozilla/ plugins.
use synaptic to find if the flashplugin-nonfree is still installed, if you copied a file to that folder, that folder will still be there even after an un-install of the flashplugin-nonfree, only solution is to delete the folder.

---

### Post by gandaran on 2008-05-19
> **bobjenkins said:**
> Ok I have tried this method before gandaran and I was blocked while trying to manually copy and past. Then I tried the mv command.

I was not getting the file path right. Can you please help with the file path command? I have the flashplugin.so sitting on my desktop, this is what I was trying

sudo mv /home/chris/desktop/flashplugin.so usr/lib/mozilla/plugins

this is the error I have gotten
mv: cannot stat `/home/chris/desktop/flashplugin.so': No such file or directory

thanks

do it this way, drag the file to the home folder, paste this command in the terminal
sudo mv flashplugin.so usr/lib/mozilla/plugins

edit: 
sorry it's, sudo mv flashplugin.so /usr/lib/mozilla/plugins

---

### Post by bobjenkins on 2008-05-19
First off thanks for all the help it seemsI am getting closer.

I have uninstalled flashplugin-nonfree, removed the plugins folder from home/chris/.mozilla

Removed the plugins folder from /usr/lib/mozilla

Then I tried moving the libflashplayer.so into home/chris/.mozilla

The move worked, but when I go to about: plugins firefox still says version 9 (I restarted firefox)

Now I tried this same thing in the /usr/lib/mozilla/plugins folder, and no luck aboutplugins still says version 9

And I also tried putting a libflashplayer.so in both folders and still the same, version 9. 

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

I thought maybe I blanked out and downloaded the version 9 but the tar.gz contains the folder install_flash_player_10_linux so this is it

I really don't know what else to try? any ideas? I don't see how I can be messing this up, when I do the sudo mv command I can see the file move to the right place.

SOLVED - Had to remove a dat file in my /.mozilla/firefox folder thanks!!

---

### Post by gandaran on 2008-05-19
> **bobjenkins said:**
> First off thanks for all the help it seemsI am getting closer.

I have uninstalled flashplugin-nonfree, removed the plugins folder from home/chris/.mozilla

Removed the plugins folder from /usr/lib/mozilla

Then I tried moving the libflashplayer.so into home/chris/.mozilla

The move worked, but when I go to about: plugins firefox still says version 9 (I restarted firefox)

Now I tried this same thing in the /usr/lib/mozilla/plugins folder, and no luck aboutplugins still says version 9

And I also tried putting a libflashplayer.so in both folders and still the same, version 9. 

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

I thought maybe I blanked out and downloaded the version 9 but the tar.gz contains the folder install_flash_player_10_linux so this is it

I really don't know what else to try? any ideas? I don't see how I can be messing this up, when I do the sudo mv command I can see the file move to the right place.

be very carefull when you delete something in the file system! you shouldn't have deleted the /usr/lib/mozilla/plugins folder, just delete the flash file!
now I can only think you downloaded the wrong flash version or you still have the 9 installed, check /usr/lib/firefox/plugins and do you still have a /usr/lib/flashplugin-nonfree folder in the file system after un-installing?

---

### Post by bobjenkins on 2008-05-19
I have gotten it to work, I ran the installer that came with flash10 in the tar.gz and when it was done it said to delete a file in the mozilla folder, when I deleted that file it seemed to "refresh the about: plugins page and it works now,,

Its still a bit laggy but its definately an improvment on version 9

---

