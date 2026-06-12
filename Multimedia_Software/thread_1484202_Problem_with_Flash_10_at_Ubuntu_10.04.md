---
title: "Problem with Flash 10 at Ubuntu 10.04"
date: 2010-05-15
forum: Multimedia Software
---

### Post by gramsyn on 2010-05-15
Problem with Flash 10 at Ubuntu 10.04
Hello everyone,

I was using Ubuntu 09.10 and everything worked fine. When I upgrated to the new version, I had no sound using YouTube.

I installed the version Flash 10 and flashplugin-nonfree-extrasound from package manager and the problem was fixed for a few days. Suddenly, I had no sound again. Other sound applications work properly.

I checked the plugins of Mozilla and discovered that the Shockwave flash version was 9.0 r31! However, the package manager says that the 10 version is installed!

I tried to upgrade the version of the plugin. It sends me to a link of Adobe where I can download a tar.gz file. I follow the instructions:

<Installation instructions for tar.gz
1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
2. Save the .tar.gz file to your desktop and wait for the file to download completely.
3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.>

When I open the tar.gz file, I only see a file named libflashplayer.so, which is extracted as such. No match with the previous instructions and as a result I cannot follow them to install that file.

Please, do you have any ideas of what should I do???

Thanks in advance

---

### Post by WinterRain on 2010-05-15
Open terminal and do:
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
to delete the existing libflashplayer.so file

Then, with the libflashplayer.so you downloaded (make sure it's on your desktop) open terminal again and do:
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```
restart firefox.

---

### Post by kaiwi on 2010-05-16
Thanks, WinterRain, for that simple solution! I had the same problem.




> **WinterRain said:**
> Open terminal and do:
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
to delete the existing libflashplayer.so file

Then, with the libflashplayer.so you downloaded (make sure it's on your desktop) open terminal again and do:
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```
restart firefox.

---

### Post by kaiwi on 2010-05-18
Got Flash working one day, next day it didn't work. Very strange. 

In any case, I would recommend Mozilla's support page 

[http://support.mozilla.com/en-US/kb/Managing%20the%20Flash%20plugin]("http://support.mozilla.com/en-US/kb/Managing%20the%20Flash%20plugin")

which provides links for testing the Flash plugin. The Plugin Check at

[http://www.mozilla.com/en-US/plugincheck/]("http://www.mozilla.com/en-US/plugincheck/") 

told me my Flash Plugin was outdated, so I again copied libflashplayer.so to /usr/lib/mozilla/plugins which again solved the problem.

---

### Post by kaiwi on 2010-05-18
A quick follow-up:

Firefox and Flash plugin do work correctly with the following script:


```
cp /media/C:/Users/Kai/Downloads/libflashplayer.so /usr/lib/mozilla/plugins;
/usr/bin/firefox;
```

In other words, I have "redefined" the firefox command so as to copy libflashplayer.so (Version 10,0,45,2) from my download directory to the plugin directory each time before launching firefox. 

If I don't copy libflashplayer.so to the plugin directory, Firefox uses an outdated (9.x) version of the Flash plugin. 

I verify which version of the Flash plugin is currently being used be Firefox by going to [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/")

All this is EXTREMELY WEIRD. 

It seems that the file libflashplayer.so in the plugin directory is not changed while Firefox is running. **So why does it make a difference whether or not I copy libflashplayer.so to the plugin directory before launching Firefox?**

I have searched for older versions of libflashplayer.so on my PC, but did not find any.

---

### Post by shashi859 on 2010-08-03
Thanks WinterRain, it worked for me

I installed flash plugin from synaptic using flash-plugin installer and then firefox was unable to play any flash videos. And i tried command 

[I]ubuntu-geek@gnubox:~$ sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory[/I]

 Later however i downloaded a tar.gz file and copied it as explained and firefox can now play flash content.

---

### Post by gandaran on 2010-08-03
----------

---

### Post by kaiwi on 2010-08-04
I may recommend the Flash-Aid add-on for Firefox

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

For me it works great.

---

### Post by AstroPhysik on 2010-08-04
Thanx! worked for me fine!

greetz AP.

---

### Post by joshthewhistler on 2010-08-04
Worked for me too! Such a great little tool. Sit back and watch...

---

### Post by alexm0428 on 2010-08-14
> **WinterRain said:**
> Then, with the libflashplayer.so you downloaded (make sure it's on your desktop) open terminal again and do:
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```
restart firefox.

This work for me even when the flash-aid couldn't.

Thank you so much.

---

### Post by TaxAlien on 2010-10-09
This was driving me insane...but solved now when I noticed that this thread was talking about /usr/lib/mozilla/plugins...

which on my system had the wrong priviledges:

/usr/lib$ ls -ld mozilla/
drwx------ 4 root root 40 2010-10-09 19:22 mozilla/

the solution is simple:

sudo chmod 755 /usr/lib/mozilla

Then restart firefox.

Job done.

---

