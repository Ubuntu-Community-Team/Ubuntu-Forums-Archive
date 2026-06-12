---
title: "Playing flash files in Hardy"
date: 2009-04-29
forum: Multimedia Software
---

### Post by melopsittacus on 2009-04-29
Hi!

I have been struggling for some time in order to play videos downloaded from Google. 

* In Firefox they play fine, however saved videos cannot be opened with Firefox: it just shows the download dialog.
* mplayer keeps complaining that it cannot find codec 0xA for sound (even after installing Windows codecs from Medibuntu)
* built in movie player finds an internal stream error
* gnash just cannopt load movies

Is there any really working solution for this? If not, is it at least possible to clean up all the garbage of Medibuntu?

---

### Post by nucleuskore on 2009-04-29
[LIST=1]
[*]Uninstall flash player
[*]Download and install flash player deb from here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
[/LIST]

---

### Post by Danial on 2009-04-29
> **nucleuskore said:**
> [LIST=1]

[*]Download and install flash player deb from here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
[/LIST]

I am sorry for jumping into this post but I am seeking help for same. 
I have downloaded the tar.gz and also deb packages but unable to install either one of those.  This may be the easiest thing to do, however, I am unable to accomplish <user error>.  On Adobe download site, installation instruction said: 
# Save the .tar.gz file to your desktop and wait for the file to download completely.
# Unpackage the file. A directory called install_flash_player_10_linux will be created.
# In terminal, **navigate to this directory** and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

I am just unable to get to that directory (saved to desktop) using cd command.  If anyone can walk me thru, please.  And once again I apologize for rudely jumping into this thread.

Danail

---

### Post by melopsittacus on 2009-04-29
> **nucleuskore said:**
> [LIST=1]
[*]Uninstall flash player
[*]Download and install flash player deb from here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
[/LIST]

Thanks for the tip, Nucleuskore, I will try that. Does it play flash files downloaded from youtube without problem for you?

---

### Post by melopsittacus on 2009-04-29
> **Danial said:**
> I am sorry for jumping into this post but I am seeking help for same. 
I have downloaded the tar.gz and also deb packages but unable to install either one of those.  This may be the easiest thing to do, however, I am unable to accomplish <user error>.  On Adobe download site, installation instruction said: 
# Save the .tar.gz file to your desktop and wait for the file to download completely.
# Unpackage the file. A directory called install_flash_player_10_linux will be created.
# In terminal, **navigate to this directory** and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

I am just unable to get to that directory (saved to desktop) using cd command.  If anyone can walk me thru, please.  And once again I apologize for rudely jumping into this thread.

Danail

Does not

```
cd ~/Desktop
```

work?

---

### Post by Melcar on 2009-04-29
For stand alone flash animations I just use swfdec.  For movies, I never had problems with Totem, Mplayer, VLC, and Dragon Player.  Just make sure you have all the codecs from ubuntu-restricted-extrasc and the restricted codec packs from medibuntu.

---

### Post by Danial on 2009-04-29
> **melopsittacus said:**
> Does not

```
cd ~/Desktop
```

work?

It Sure did... Thanks a lot for help
I admit it was a User Error... 
but learning have to start from somewhere

Danial

---

### Post by nucleuskore on 2009-04-30
> **Danial said:**
> I am sorry for jumping into this post but I am seeking help for same. 
I have downloaded the tar.gz and also deb packages but unable to install either one of those.

Easy to install the deb. Just double click on it, and then click Install package in the dialog box.

> **melopsittacus said:**
> Thanks for the tip, Nucleuskore, I will try that. Does it play flash files downloaded from youtube without problem for you?

I wouldn't be suggesting something I haven't tried myself :)

---

