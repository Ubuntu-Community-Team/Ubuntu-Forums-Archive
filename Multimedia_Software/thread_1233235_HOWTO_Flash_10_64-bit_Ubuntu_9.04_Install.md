---
title: "HOWTO: Flash 10 64-bit Ubuntu 9.04 Install"
date: 2009-08-06
forum: Multimedia Software
---

### Post by JordanL on 2009-08-06
For those of you having issues with flash playback (especially fullscreen) on 64bit ubuntu 9.04 give this little install script a try. It was originally written by Romeo-Adrian Cioaba, but I added some fixes to the scripting that edits the mms.cfg file to help with fullscreen playback. The compressed file contains the latest flash 10 64bit alpha plugin as well as the install script. Please note that this script will kill all instances of firefox currently running, so please don't have anything important open as it will be closed without warning. 

Download the file from [http://aifcanada.com/flash64.tar.gz]("http://aifcanada.com/flash64.tar.gz")

To install just extract the tar.gz into a folder on your desktop, open up terminal and navigate to your newly extracted folder and type
```
sudo ./flash.sh
``` and the script should only take a couple seconds to run. It does uninstall any previous flash plugin's before installing to prevent any issues. 

Im running Ubuntu 9.04 64-bit with kernel version 2.6.28-14-generic. Fullscreen flash in nearly flawless on youtube.com (oddly enough it works better in HD mode fullscreen than in standard :P )

NOTE: This is only tested to work with firefox, this won't install the plugin for other browsers!

Hope this helps everyone struggling with making flash work in 64bit. I've had very good luck with this so far though there is still room for improvement.

---

### Post by Yellow Pasque on 2009-08-06
Why are you including the actual Flash player with the script? Isn't that a waste of your host's bandwidth? Why not just use a wget in the script to download from Adobe?

Caveat1: The last time I checked, video acceleration in Flash doesn't work if you're running Compiz: [http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Caveat2: This script removes nspluginwrapper. If the old flashplugin is the only 32-bit plugin you have installed, then this is harmless. If you're using other 32-bit plugins with nspluginwrapper, they won't work after this.

---

### Post by napster2500 on 2009-08-11
Thank you! :)

Now I can finally visit the all-new grand bentley site. YouTube works great also. Thanks! :)

Ubuntu 9.04 64bit.

---

### Post by sqrlking on 2009-08-26
JordanL thank you so very much for this shell script. I spent hours trying to get the alpha to work on 9.04 64-bit, and then came across your script. It worked flawlessly.

---

### Post by bobterri73 on 2009-08-27
I am running Hardy (8.04) on a 64 bit machine.  I have been unable to download Flash Player 10 and therefore cannot view any youtube videos.  I downloaded the file flash64.tar.gz and tried to install it using the command  "sudo ./flash.sh".  My terminal's response was 
 sudo: ./flash.sh: command not found

What am I doing wrong?

---

### Post by Lycus on 2009-08-27
> **bobterri73 said:**
> I am running Hardy (8.04) on a 64 bit machine.  I have been unable to download Flash Player 10 and therefore cannot view any youtube videos.  I downloaded the file flash64.tar.gz and tried to install it using the command  "sudo ./flash.sh".  My terminal's response was 
 sudo: ./flash.sh: command not found

What am I doing wrong?

Shot in the dark: try making it executable, chmod +x flash.sh, then try executing it.

---

### Post by Nburnes on 2009-08-28
> **bobterri73 said:**
> I am running Hardy (8.04) on a 64 bit machine.  I have been unable to download Flash Player 10 and therefore cannot view any youtube videos.  I downloaded the file flash64.tar.gz and tried to install it using the command  "sudo ./flash.sh".  My terminal's response was 
 sudo: ./flash.sh: command not found

What am I doing wrong?
The reason it didn't work is because you didn't direct it to where the .sh is.
Type 

```
sudo sh .(drag the .sh file here)
```

Don't type the whole parenthesis part obviously.

---

### Post by itaylor on 2009-08-30
The script ran fine, and some sites requiring Flash 10 worked, but many others caused the Firefox to crash. In the future I would recommend that suggestions for installation scripts like this one be accompanied by removal instructions (i.e. something more than "I don't guarantee this will work for everyone and I am not responsible if this causes any damage.")

I deleted /usr/lib/mozilla/plugins/libflashplayer.so and now the crashing is gone, but I'm stabbing in the dark on how to revert back to flash 9.

---

### Post by bobterri73 on 2009-09-10
Sorry to be a bother, but I need a little more explanation, what do you mean by ".(drag the .sh file here)".   Thanks for any help you can give.  I am not real technically savvy with computers.

---

### Post by admelfo on 2009-10-16
I was optimistic -- script ran fine, thanks -- but Flash still doesn't work. 

~shrugs~

---

### Post by VertexPusher on 2009-10-16
Why is a script even required for something trivial like this? Here's what I did:

1. Download the 64bit plugin from Adobe's site.
2. Unpack the archive (right-click, "Extract here").
3. Move the file "libflashplayer.so" from the extracted folder to "~/.mozilla/plugins/".
4. Restart Firefox.

No command line, no sudo password. Just copy/move a file from A to B in your home folder.

---

### Post by admelfo on 2009-10-31
Follow-up:  I just installed the latest Firefox update that showed up in Update Manager today, and now Flash works.

---

### Post by Freeman88 on 2009-10-31
> Why is a script even required for something trivial like this? Here's what I did:

1. Download the 64bit plugin from Adobe's site.
2. Unpack the archive (right-click, "Extract here").
3. Move the file "libflashplayer.so" from the extracted folder to "~/.mozilla/plugins/".
4. Restart Firefox.

No command line, no sudo password. Just copy/move a file from A to B in your home folder.


This actually works (on FF 3.5.4)!!! :D 
I had to create folder plugins... It wasn't there by default. 


THANKS!

---

