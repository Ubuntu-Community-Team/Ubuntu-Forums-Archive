---
title: "Flashplayer for Firefox"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by Alfie on 2007-07-24
Hi all.

I`m trying to install Flash Player for Firefox.

This is what I do:
> 
sudo apt-get install flashplugin-nonfree


This gives me output that the package flashplugin-nonfree is not available, but another package is pointing to it. This could mean that the package is missing, is out of date or is only available from another source.  (I think this should be precisely translated)

On ubuntuguide.org I find the following:

> 
Note: The best way to install the Macromedia Flash Player plug-in for Mozilla Firefox is to use Firefox and visit Adobe.com: Version test for Adobe Flash Player. Then you will see a note about firefox missing a plugin for flash. Click this note and follow any steps that firefox tells you to follow. Normally firefox installs this plugin automatically when you click "install now".
 

This doesn help me either.

Anyone want to tell me how this can be done?

---

### Post by ajgreeny on 2007-07-24
have you got the medibuntu repositories activated on your system, as that is where you will find the flash plugin etc.  Go to [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php) for the medibuntu repos, install them as the site tells you and try apt again.

---

### Post by Alfie on 2007-07-24
I installed the medibuntu repositories as described on that site.
> 
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list


> 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


Then I did the sudo apt-get install flashplugin-nonfree again.

Still the same....

---

### Post by aysiu on 2007-07-24
This will help:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Gremlinzzz on 2007-07-24
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.

---

### Post by Alfie on 2007-07-25
> 
alf@alf-laptop:~/Desktop$ tar -xvzf install_flash_player_9_linux.tar.gz
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so


So far so good.

> 
alf@alf-laptop:~/Desktop$ sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/


Nothing happens when I hit enter. So, I try one more time:

> 
alf@alf-laptop:~/Desktop$ sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
mv: cannot stat `install_flash_player_9_linux/libflashplayer.so': No such file or directory


> 
alf@alf-laptop:~/Desktop$ sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/


Nothing happens. Flash still not installed....? FF restarted...

---

### Post by Commodore Guff on 2007-07-25
Just shooting in the dark here, but could it be that your Ubuntu installation is 64-bit?

---

### Post by aysiu on 2007-07-25
What do you mean by "nothing happens"?

When you entered that command, you asked Ubuntu to move the libflashplayer.so file from the install_flash_player_9_linux directory to the /usr/lib/firefox/plugins/ directory. When you do that the first time, you should just go back to the next line: ```
alf@alf-laptop:~/Desktop$
``` That means the command was successful. When you did it the second time, it was trying to move a file that was no longer there... because you'd already moved it.

Can you post the output of these commands? ```
cd /usr/lib/firefox/plugins
ls
```

---

### Post by Alfie on 2007-07-25
Ok. Didn`t realize what the commands did.

> 
alf@alf-laptop:~$ cd /usr/lib/firefox/plugins
alf@alf-laptop:/usr/lib/firefox/plugins$ ls
flashplayer.xpt            libtotem-mully-plugin.so
libflashplayer.so          libtotem-mully-plugin.xpt
libtotem-basic-plugin.so   libtotem-narrowspace-plugin.so
libtotem-basic-plugin.xpt  libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.so     libunixprintplugin.so
libtotem-gmp-plugin.xpt


And about my installation. Ok - I am a newbie. How do I know if I got a 64 bit? I`ve got a laptop if that`s got something to say,  :-k

---

### Post by aysiu on 2007-07-25
Can you post the output of this command? ```
uname -m
```

---

### Post by Alfie on 2007-07-25
> 
alf@alf-laptop:/$ uname -m
x86_64


Ok - seems like I have a 64 bit. Does that mean I dowloaded the wrong version?

---

### Post by aysiu on 2007-07-25
> **Alfie said:**
> Ok - seems like I have a 64 bit. Does that mean I dowloaded the wrong version?
You have the wrong version *for the instructions we gave you earlier*, but you do not have the wrong version of Ubuntu if your operating system installation worked, as it appeared to.

This should help you:
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by Alfie on 2007-07-25
Thanks a lot.

I followed the describtions and downloaded / installed a 32-bit version. The script also asked me if I wanted to install Flash and Java. I confirmed both. I also downloaded and installed the gtk-qt-engine package even though I believe this is also done by the script.

Then to be sure, I restarted my computer and visited Youtube to check. It still doesn`t work.

I feel I am guided in the correct directions now, but maybe there still is work to do?

---

### Post by Commodore Guff on 2007-07-25
> **Alfie said:**
> Thanks a lot.

I followed the describtions and downloaded / installed a 32-bit version. The script also asked me if I wanted to install Flash and Java. I confirmed both. I also downloaded and installed the gtk-qt-engine package even though I believe this is also done by the script.

Then to be sure, I restarted my computer and visited Youtube to check. It still doesn`t work.

I feel I am guided in the correct directions now, but maybe there still is work to do?

I had some problems with that script, too.  For me, at least, it seemed as if it had some connection problems.
I'm not sure if it was the same for you or not.

---

### Post by Alfie on 2007-07-25
Yes - I noticed that there was some problems there, but since it continued I assumed that it was ok...  Did you make it work finally?

---

### Post by Commodore Guff on 2007-07-25
> **Alfie said:**
> Did you make it work finally?
In a way, yes, but probably not what you're hoping for.  I just decided that the few benefits from going with 64-bit weren't worth the incompatibilities, so I just reinstalled with a 32-bit version of Feisty.

If you really want to stick to 64-bit, it's possible that [this]("http://ubuntuforums.org/showthread.php?t=341727") could help, but it's a bit of work, and it was written for Edgy (I would hope that it would still apply to Feisty, assuming that's what you're using).

---

### Post by Alfie on 2007-07-25
> **Commodore Guff said:**
> In a way, yes, but probably not what you're hoping for.  I just decided that the few benefits from going with 64-bit weren't worth the incompatibilities, so I just reinstalled with a 32-bit version of Feisty.

Ok - I thought that this would be it. But it is no bug deal as far as I`m concerned. But what is the benefits from a 64 vs a 32? If there is only minor differences, that`s what I will do.

---

### Post by Commodore Guff on 2007-07-25
> **Alfie said:**
> Ok - I thought that this would be it. But it is no bug deal as far as I`m concerned. But what is the benefits from a 64 vs a 32? If there is only minor differences, that`s what I will do.

Well, it's possible that you'd see some minor speed benefits, and the maximum amount of memory you could use would be much higher, though 32-bit processors can still address up to 4GB of memory so the latter is not an issue for most.

---

### Post by Barney on 2007-07-27
I have tried most of the suggestions in this thread, but have not been able to get flash to work (youtube).

Dapper +Firefox 2.0.0.5 (works great); about:plugins reveals:     
File name: libflashplayer.so
Shockwave Flash 9.0 r48;   

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes [enabled]
application/futuresplash 	FutureSplash Player 	   spl 	    Yes

Suggestions?

---

### Post by Bablefish on 2007-07-27
When I installed Flash all I had to do was goto Add/Remove

---

### Post by Alfie on 2007-07-27
Yes, but do you have the 32 or 64 bit version?

---

### Post by telemetry on 2007-07-27
Well...what a journey.  i now have Flash working and can watch videos on youtube etc....  I tried everything but had almost given up.

This is what I did:

Followed instructions from this excellent site: [www.psychocats.net/ubuntu/flash](www.psychocats.net/ubuntu/flash)

But it still didn't work...the site above was only half the battle......it wasn't until I had the desperate idea of going into synaptec and marking Gnash *(another player) and its plugins for removal.  I had the notion that Gnash might be preventing flash from working and do you know what? I was right.  Once I uninstalled Gnash and its plugins, Flash now works beautifully.  Yipee!!!

I'm not sure if this helps but it's what I had to do get macromedia flash working.

all the best
robert:KS

---

### Post by Barney on 2007-07-28
"Swiftweasel" to the rescue!

I installed Swiftweasel from: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

I used the .deb for installation which, once installed, picks up everything, bookmarks, extensions, etc. and looks, acts, and feels like Firefox.

Everything being the same for both Swiftweasel & FIrefox, Swiftweasel plays flash, and Firefox doesn't............go figure.

---

