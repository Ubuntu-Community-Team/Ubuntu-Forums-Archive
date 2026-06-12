---
title: "Can't play any flash movies"
date: 2009-08-29
forum: Multimedia Software
---

### Post by danp824 on 2009-08-29
Hi, I'm having a problem playing flash movies in Firefox.  Some websites (like Youtube) will only play sound, and not video, while some websites simply won't play the movie at all, and I simply get a black screen.  I installed all the plugins that Firefox prompted me to, but it didn't help.

I imagine I need some package from Synaptic, but which one(s) do I download?

Thanks!  :)

---

### Post by argos3016 on 2009-08-29
Try making a new firefox profile:
firefox -ProfileManager 
And create a new profile
Goes good?

---

### Post by Rev2010 on 2009-08-29
Uninstall the Flash plugin that you have currently. Then follow the instructions for getting the Medibuntu repositories on this page:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After you do the "add GPG" part go to Adobe's website and run the .deb version they have there to install the Flash plugin again. Then go to System -> Administration -> Software Sources and click on the Third-Party Software tab and make sure the Medibuntu boxes are checked. It will prompt you to reload so do so. Then run the update manager and it will alert you that there is a newer version of Flash available, install it.

At least this is what got it working 100% for some systems I've installed it on.


Rev.

---

### Post by privatejarhead on 2009-08-29
have you tried installing the .deb package from the flash website? or maybe opening up terminal and entering "sudo install ubuntu-restricted-extras"?

---

### Post by danp824 on 2009-08-29
LOL, ok... 

Rev2010:  How do I uninstall the plugins I have?  I don't even know what they were - it was just a bunch of letters and numbers that firefox told me I had to install.  You know the drill - a window pops up and says "you must install these plugins", and I click "ok."  How do I figure out which ones they were and uninstall them?

argos:  How do I get to Profile Manager?

privatejarhead:  I couldn't find the .deb package on the flash website. Where is it?

---

### Post by Rev2010 on 2009-08-29
> **danp824 said:**
> LOL, ok... 

Rev2010:  How do I uninstall the plugins I have?

Click on Applications then Add/Remove. Make sure you have "All" selected on the left and also Show: All Available Applications on the right. Look for Adobe Flash in the list and see if it's checked. If it is uncheck it and click apply changes. If for some reason it's not checked then go into Synaptic Package Manager and type flash into the search field, see if it's installed. If so, right click and select Remove Completely.

The .deb package on the Adobe site is clear as day to choose. Use the drop here:

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

to choose which version you want. Select the .deb for Ubuntu package, download it, and double click on it.


Rev.

---

### Post by ChrisWebb on 2009-08-29
I don't know if this affects you, but I had a similar problem - I couldn't get any flash enabled sites to work properly - YouTube for example wouldn't indicate an error, but the flash plugin would not appear.

The solution for me was simple - my home folder had 750 permissions (i.e. no access for "other" accounts). Switching this to 755 permissions did the trick.

Check your home folder permissions by typing
```
ls /home
```into a terminal prompt and if required change the permissions:
```
chmod 755 /home/user
```I should point out that my home folders use the Ubuntu standard ownerships (user:user).

Hope this helps someone, if not you!

---

### Post by stefcep on 2009-08-29
have you tried this

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I also installed mozilla-mplayer plug-in from synaptic, mplayer itself and the w32codecs (not sure if needed, but I put it in anyway)

---

### Post by rethinkme.net on 2009-08-30
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I followed the above steps and it worked great! Thanks.

---

### Post by Oldhacker on 2009-08-31
YouTube was working for me but some other flash sites were not.
Following your instructions YouTube and the other sites now work.

Thank you

---

### Post by blur xc on 2009-08-31
> **Oldhacker said:**
> YouTube was working for me but some other flash sites were not.
Following your instructions YouTube and the other sites now work.

Thank you

to make it work better, right click the youtube video or whatever flash content, click settings, and uncheck the enable hardware acceleration check box.  After doing that, I get good quality youtube hd fullscreen videos, and flash game sites like teagames.com works perfect too.  Very fast frame rates...

BM

---

