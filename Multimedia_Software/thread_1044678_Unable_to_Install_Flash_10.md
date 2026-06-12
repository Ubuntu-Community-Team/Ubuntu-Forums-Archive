---
title: "Unable to Install Flash 10"
date: 2009-01-19
forum: Multimedia Software
---

### Post by eckeroo on 2009-01-19
Hello all,

At some point, my flash plug-ins were no longer working on Firefox. I uninstalled flash followed by a re-installation.

The tar.gz file was downloaded, but the following error message occurred at the end of the failed installation:

> 
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is not installed/

The flashplugin-nonfree was registered installed in the Synaptic Package manager, but no Flash was available on firefox. I then uninstalled flashplugin-nonfree again and tried something else:

After searching the Ubuntu forums for help on flash installation, I came across this thread that mentions the 'md5sum' error:

[http://ubuntuforums.org/showthread.php?t=932056](http://ubuntuforums.org/showthread.php?t=932056)

I then followed the instructions on the thread for a manual flash installation, downloaded the install_flash_player_10_linux.tar.gz file from adobe and extracted it. But I got as far as running the installer and could not get past the following prompt:

> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

At this stage I always entered: /usr/lib/firefox -but this always returns with:

> WARNING: Please enter a valid installation path.

And at this point I am stuck.

My system is Hardy 8.04 and I have all the repositories enabled as per the 'Comprehensive Multimedia & Video Howto' thread.

Any help will be much appreciated

---

### Post by eckeroo on 2009-01-20
*bump*

---

### Post by wolfen69 on 2009-01-20
> **eckeroo said:**
> 


At this stage I always entered: /usr/lib/firefox -but this always returns with:


the path should be /usr/lib/mozilla

if that does not work i have another suggetion. try that first.

---

### Post by eckeroo on 2009-01-21
> the path should be /usr/lib/mozilla

I tried this and unfortunately the same message appears: 
> WARNING: Please enter a valid installation path.

---

### Post by gandaran on 2009-01-21
eckeroo
to install the flashplugin-nonfree from the repository you have to reload/update (sudo apt-get update) synaptic before installing anything to get the new packages or you'll get that md5sum mismatch error
the flashplugin-nonfree in ubuntu 8.04 installs flash 9, you can get the flash 10 .deb package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) just double click the package to install
about the .tar.gz package, to install in /usr/lib/mozilla you have to run the install command with sudo, running without sudo you choose the path to install in /home/'user'/.mozilla  
you can also just simply install it yourself too by extracting the package and drag the libflashplayer.so file to either home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins

---

### Post by eckeroo on 2009-01-21
Thank you gandaran

Unfortunately, the same message appeared even when I ran the installation script with the sudo. However, the user installation worked without running sudo. Following your instructions, I then sudo copied the libflashplayer.so file to the /usr/lib/mozzila/plugins directory. I now have flash player 10 back on firefox and it should also work on all users (I've yet to test this).

I should have a look through the extracted installation script to find out
what was leading to the message: "WARNING: Please enter a valid installation path."

One last question - this instruction appeared at the end of the installation:

> 
NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

Is this important?

Thank you :)

---

### Post by michael37 on 2009-01-21
The program may be referring to file 

To check, run command
```

locate flashplayer.xpt

```

Perhaps you may want to remove it.

FYI, the best command to download the file from Adobe that worked for me perfectly was
```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz

```

---

