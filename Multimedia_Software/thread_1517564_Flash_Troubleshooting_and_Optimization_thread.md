---
title: "Flash Troubleshooting and Optimization thread"
date: 2010-06-25
forum: Multimedia Software
---

### Post by lovinglinux on 2010-06-25
Due to the enormous quantity of flash plugin related problems, I decided to expand my tutorials and create this thread to provide support for flash issues (*is getting really hard to follow all the flash related threads and provide a decent support*)

[COLOR="Sienna"]**Current available tutorials:**[/COLOR]

[LIST]
[*][Flash Optimization](http://webgapps.org/groups/firefox/docs/flash-optimization/)
[*][Flash Issues & Solutions](http://webgapps.org/groups/firefox/docs/flash-issues-solutions/)
[/LIST]

**[COLOR="Sienna"]Firefox extensions:[/COLOR]**

[LIST]
[*]**[Flash-Aid:](https://addons.mozilla.org/en-US/firefox/addon/161939/)** remove conflicting plugins and install the proper flash version according to browser architecture. [[Mozilla](https://addons.mozilla.org/en-US/firefox/addon/161939/)] [[Blog]("http://webgapps.org/add-ons/flash-aid/")] [[Support](http://ubuntuforums.org/showthread.php?t=1491268)]
[*]**[FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869"):** replace flash videos with mplayer compatible videos to improve performance. [[Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/161869")] [[Blog](http://www.webgapps.org/addons/flashvideoreplacer)] [[Support](http://ubuntuforums.org/showthread.php?t=1487327)]
[/LIST]

When asking for support, please describe your problem in detail and provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```
echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
```

For more Firefox tweaks and tips see [http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/](http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/)
For additional Firefox support see [Firefox Optimization and Troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by johnrobert on 2010-06-25
Thank you lovinglinux for this guide. I'm digging into it right now. BTW, I'm watching Brazil play Portugal right now. Go Brazil!

---

### Post by lovinglinux on 2010-06-25
> **johnrobert said:**
> Thank you lovinglinux for this guide. I'm digging into it right now. BTW, I'm watching Brazil play Portugal right now. Go Brazil!

I'm still writing the guide, since I need to go through hundreds of threads to determine the most successful solutions for each problem. But I hope to have a decent guide after the World Cup. Now is hard to do anything else with so many games :)

---

### Post by vajras on 2010-07-26
Gidday

Just followed your guide starting at the top of: [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Installed Flashaid - no joy - various sites keeps asking to install plugins but Plugin Service says each is already installed; so then ran your commands one-by-one as listed - still no joy.

Then did, 
* type about : config in Firefox address bar
* type plugin.expose_full_path in the filter
* double-click plugin.expose_full_path in the results to make it true
* type about : plugins in the address bar, find Shockwave Flash and copy the corresponding Path and Version information.

Result: 

No plugins are installed
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

Mozilla/5.0 (X11; U; Linux i686 (x86_64) ; en-GB; rv:1.9.2.8 ) Gecko/20100722 Firefox/3.6.8 

Your assistance would be appreciated.

---

### Post by vajras on 2010-07-26
Update - thought i'd try the other browsers to see if specific to FF - i am now unable to see Flash and YouTube in all of Firefox, Sea Monkey and Epiphany!

---

### Post by wojox on 2010-07-26
Try installing the 64 bit version. [Install 64-bit Adobe Flash Player]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

---

### Post by lovinglinux on 2010-07-26
> **vajras said:**
> Gidday

Just followed your guide starting at the top of: [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Installed Flashaid - no joy - various sites keeps asking to install plugins but Plugin Service says each is already installed; so then ran your commands one-by-one as listed - still no joy.

Then did, 
* type about : config in Firefox address bar
* type plugin.expose_full_path in the filter
* double-click plugin.expose_full_path in the results to make it true
* type about : plugins in the address bar, find Shockwave Flash and copy the corresponding Path and Version information.

Result: 

No plugins are installed
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

Mozilla/5.0 (X11; U; Linux i686 (x86_64) ; en-GB; rv:1.9.2.8 ) Gecko/20100722 Firefox/3.6.8 

Your assistance would be appreciated.

Please post the output of these commands:

```
file /usr/lib/firefox-addons/plugins/libflashplayer.so
```

```
file /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

```
file /etc/alternatives/mozilla-flashplugin
```

```
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```

---

### Post by wojox on 2010-07-26
Hey lovinglinux does your Flashaid have the ability to install 64 bit from Adobe? Or just the one with the wrapper.

---

### Post by lovinglinux on 2010-07-26
> **wojox said:**
> Hey lovinglinux does your Flashaid have the ability to install 64 bit from Adobe? Or just the one with the wrapper.

I have decided to remove the support for the 64bit version until adobe supports it again and fixes the critical vulnerability of the available version. So it will install the 32bit with the wrapper. Any particular reason why you don't want that?

---

### Post by vajras on 2010-07-26
> **lovinglinux said:**
> Please post the output of these commands
```
file /usr/lib/firefox-addons/plugins/libflashplayer.so
```
/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'

```
file /usr/lib/mozilla/plugins/flashplugin-alternative.so
```
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'

```
file /etc/alternatives/mozilla-flashplugin
```
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/gnash/libgnashplugin.so'

```
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> ```
file /etc/alternatives/mozilla-flashplugin
```
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/gnash/libgnashplugin.so'

```
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

Make sure you have the latest version of [FLASH-AID](http://flash-aid-extension.blogspot.com), which is 1.0.10. You probably have 1.0.5, which might not be working for you. Restart Firefox and then click the extension icon in the status bar and select install.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164619&stc=1&d=1280205551[/IMG]

Follow the instructions on the screen, then restart the browser.

This will fix your problem.

---

### Post by vajras on 2010-07-27
Hee hee! Now why did i think you may suggest this?!

Had done this prior to your last reply - v1.0.10 IS installed tho' it appears in the top next to 'Search' & not bottom status bar as you suggest.

And no, doing your last instruction has not fixed the problem also.

---

### Post by wojox on 2010-07-27
> **lovinglinux said:**
> I have decided to remove the support for the 64bit version until adobe supports it again and fixes the critical vulnerability of the available version. So it will install the 32bit with the wrapper. Any particular reason why you don't want that?

Just curious, that's all. :D

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> Hee hee! Now why did i think you may suggest this?!

Had done this prior to your last reply - v1.0.10 IS installed tho' it appears in the top next to 'Search' & not bottom status bar as you suggest.

And no, doing your last instruction has not fixed the problem also.

OK. When you click install, there are some commands displayed before it runs on the terminal. Please copy them and paste here.

Also post the output of:

```
uname -a
```

```
file /etc/alternatives/mozilla-flashplugin
```

Don't copy the above from your previous results. Run the command again.

---

### Post by vajras on 2010-07-27
#!/bin/bash

echo "Please wait...DON'T CLOSE THIS TERMINAL!"
sudo apt-get --yes purge swfdec-mozilla
sudo apt-get --yes purge mozilla-plugin-gnash
sudo apt-get --yes purge adobe-flashplugin
sudo apt-get --yes purge flashplugin-nonfree
sudo apt-get --yes purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo apt-get --yes install flashplugin-nonfree && sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
echo -n "Finished! You can close this terminal. You must restart Firefox now." && read

```
uname -a
```

Linux harry-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

---

### Post by vajras on 2010-07-27
```
file /etc/alternatives/mozilla-flashplugin
```

/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> #!/bin/bash

echo "Please wait...DON'T CLOSE THIS TERMINAL!"
sudo apt-get --yes purge swfdec-mozilla
sudo apt-get --yes purge mozilla-plugin-gnash
sudo apt-get --yes purge adobe-flashplugin
sudo apt-get --yes purge flashplugin-nonfree
sudo apt-get --yes purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo apt-get --yes install flashplugin-nonfree && sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
echo -n "Finished! You can close this terminal. You must restart Firefox now." && read

```
uname -a
```

Linux harry-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

> **vajras said:**
> ```
file /etc/alternatives/mozilla-flashplugin
```

/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'

This time FLASH-AID worked as expected and removed the conflicting plugin. It seems the problem is that you are using a 32bit browser on an 64bit system and it is not recognizing the plugin, which is wrapped to work with the 64bit system. I need to confirm that, but I am almost sure this is the problem. Please give me a couple of minutes.

How did you install Firefox 3.6.8?

---

### Post by vajras on 2010-07-27
```
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install firefox-3.7
```

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> ```
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install firefox-3.7
```

Close Firefox and do this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.7
sudo rm -f /var/cache/apt/archives/firefox*
sudo apt-get clean
sudo apt-get update
sudo apt-get install firefox
```

Then paste the output of:

```
which firefox
```

```
file /usr/lib/firefox-3.6.8/firefox-bin
```

---

### Post by vajras on 2010-07-27
```
which firefox
```
Result: 
/usr/bin/firefox

```
file /usr/lib/firefox-3.6.8/firefox-bin
```
Result:
/usr/lib/firefox-3.6.8/firefox-bin: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> ```
which firefox
```
Result: 
/usr/bin/firefox

```
file /usr/lib/firefox-3.6.8/firefox-bin
```
Result:
/usr/lib/firefox-3.6.8/firefox-bin: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

Start Firefox. It should work.

[LIST]
[*]type about:config in Firefox address bar
[*]type plugin.expose_full_path in the filter
[*]double-click plugin.expose_full_path in the results to make it true
[*]type about[noparse]:[/noparse]plugins in the address bar, find Shockwave Flash and copy the corresponding Path and Version information.
[/LIST]

Go to Firefox  "Help >> About Mozilla Firefox" in the menu. and copy the version info and paste here.

---

### Post by vajras on 2010-07-27
> double-click plugin.expose_full_path in the results to make it true
It is 'true' already 

> type about : plugins in the address bar, find Shockwave Flash and copy the corresponding Path and Version information.

about : plugins
No plugins are installed
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

> Go to Firefox "Help >> About Mozilla Firefox" in the menu. and copy the version info and paste here. 
Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9.2.8 ) Gecko/20100722 Firefox/3.6.8

---

### Post by lovinglinux on 2010-07-27
Give me a few seconds.

---

### Post by vajras on 2010-07-27
You're most kind kind - ditto - no rush - i will return after our evening meal in about 1 hour

---

### Post by lovinglinux on 2010-07-27
Post the output of:

```
file /usr/bin/firefox
```

```
file /usr/local/bin/firefox
```

```
file /usr/bin/firefox.ubuntu
```

```
ls /opt/firefox
```

---

### Post by vajras on 2010-07-27
```
file /usr/bin/firefox
```/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'

```
file /usr/local/bin/firefox
```/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)

```
file /usr/bin/firefox.ubuntu
```/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-3.6.8/firefox.sh'

```
ls /opt/firefox
```

application.ini           crashreporter.ini           firefox-bin     
blocklist.xml             crashreporter-override.ini  greprefs
browserconfig.properties  defaults                    icons   
chrome                    dependentlibs.list          libfreebl3.chk
components                extensions                  libfreebl3.so
crashreporter             firefox                     libmozjs.so

libnspr4.so               libplc4.so                  libssl3.so
libnss3.so                libplds4.so                 libxpcom.so
libnssckbi.so             libsmime3.so                libxul.so
libnssdbm3.chk            libsoftokn3.chk             LICENSE
libnssdbm3.so             libsoftokn3.so              modules
libnssutil3.so            libsqlite3.so         mozilla-xremote-client


platform.ini              res                   updater.ini
plugin-container          run-mozilla.sh
plugins                   searchplugins
plugins.backup            Throbber-small.gif
README.txt                update.locale
removed-files             updater

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> ```
file /usr/bin/firefox
```/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'

```
file /usr/local/bin/firefox
```/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)

```
file /usr/bin/firefox.ubuntu
```/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-3.6.8/firefox.sh'

```
ls /opt/firefox
```

application.ini           crashreporter.ini           firefox-bin     
blocklist.xml             crashreporter-override.ini  greprefs
browserconfig.properties  defaults                    icons   
chrome                    dependentlibs.list          libfreebl3.chk
components                extensions                  libfreebl3.so
crashreporter             firefox                     libmozjs.so

libnspr4.so               libplc4.so                  libssl3.so
libnss3.so                libplds4.so                 libxpcom.so
libnssckbi.so             libsmime3.so                libxul.so
libnssdbm3.chk            libsoftokn3.chk             LICENSE
libnssdbm3.so             libsoftokn3.so              modules
libnssutil3.so            libsqlite3.so         mozilla-xremote-client


platform.ini              res                   updater.ini
plugin-container          run-mozilla.sh
plugins                   searchplugins
plugins.backup            Throbber-small.gif
README.txt                update.locale
removed-files             updater

Close Firefox and do this:

```
sudo apt-get remove firefox-mozilla-build
```

If the terminal says that **firefox-mozilla-build** is not installed, then run the following commands. DON'T run the next commands if the previous command returns that **firefox-mozilla-build** was removed successfully.

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

Start Firefox. It should be fixed.

---

### Post by vajras on 2010-07-27
Both commands done.

Success! Flash and Videos are now showing properly.

You should be awarded the Nobel Perseverance Prize for patience and understanding.

Many thanks.

What do you think is the cause of all this (without being too technical for those others following - as each persons box is not unique)?

---

### Post by lovinglinux on 2010-07-27
See next post

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> You should be awarded the Nobel Perseverance Prize for patience and understanding.

Many thanks.

You are welcome. I have already changed my first post in order to gather all the necessary information before trying to figure out the problem. :)

> **vajras said:**
> What do you think is the cause of all this (without being too technical for those others following - as each persons box is not unique)?

There were two main problems. First, the plugin being used was gnash, which was replaced by flashplugin-nonfree, by the second time you ran FLASH-AID.

The second problem was that you had a 32b it version of Firefox installed in the /opt/firefox folder and the location of the firefox executable was diverted to this version. So although you have installed firefox from the repositories, every time you launched it, it was in fact launching the version from /opt/firefox. Since this version was 32bit, then Firefox wasn't able to detect the plugins, which are 64bit.

---

### Post by vajras on 2010-07-27
Thanks - mud clearer now!

And Re-reading from the beginning i can confirm about : plugins is now visible.

Would you like a "firefox-report.txt" ?

---

### Post by lovinglinux on 2010-07-27
> **vajras said:**
> Would you like a "firefox-report.txt" ?

No need.

---

### Post by NorgeNerd on 2010-08-15
I'm so close I can taste it.  Flash version 10.1 r82 is installed; Flash-Aid is installed.  But Firefox refuses to acknowledge 10.1 r82--except in new user accounts.  An "about:plugins" shows that both 10.1 r82 and 9.0 r115 are present.  Maybe if I uninstalled the earlier version?  Can't figure out how to do that (I'm a Linux novice).  My Ubuntu version is 10.4 LTS

---

### Post by lovinglinux on 2010-08-16
> **NorgeNerd said:**
> I'm so close I can taste it.  Flash version 10.1 r82 is installed; Flash-Aid is installed.  But Firefox refuses to acknowledge 10.1 r82--except in new user accounts.  An "about:plugins" shows that both 10.1 r82 and 9.0 r115 are present.  Maybe if I uninstalled the earlier version?  Can't figure out how to do that (I'm a Linux novice).  My Ubuntu version is 10.4 LTS

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by NorgeNerd on 2010-08-17
Results (Just before doing this, I ran upgrades & Firefox upgraded to Namroka . . .):

Shockwave Flash

    File: /home/seth/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

About:

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

System Info:

Ubuntu Architecture

Linux Wedeberg 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.6					install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

lucid-partner.list
lucid-partner.list.save
ubuntu-mozilla-daily-ppa-lucid.list

Flash packages

adobe-flashplugin				install
flashplugin-installer				deinstall

Plugin locations

/home/seth/.local/share/Trash/files/FlashPlayer/install_flash_player_9_linux/libflashplayer.so
/home/seth/.mozilla/plugins/libflashplayer.so
/home/wingram/Desktop/FlashPlayer/install_flash_player_9_linux/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/firefox-addons/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-17
> **NorgeNerd said:**
> Results (Just before doing this, I ran upgrades & Firefox upgraded to Namroka . . .):


Have you actually ran FLASH-AID after installing it? I'm asking this because your problem should be fixed by it. Anyway, you can also just delete the flash 9 version that you have installed manually:

```
rm -f /home/seth/.mozilla/plugins/libflashplayer.so
```

---

### Post by NorgeNerd on 2010-08-17
> **lovinglinux said:**
> Have you actually ran FLASH-AID after installing it? I'm asking this because your problem should be fixed by it. Anyway, you can also just delete the flash 9 version that you have installed manually:

```
rm -f /home/seth/.mozilla/plugins/libflashplayer.so
```

Well, that brings up another question.  I did run flash-aid.  But I see that it did not propagate to all user accounts.  Is there a way (remember my novice status, please) to install software so that it propagates to all user accounts?  I can't believe that installations have to happen under each user account.

Thank you so much for your assistance.

---

### Post by lovinglinux on 2010-08-18
> **NorgeNerd said:**
> Well, that brings up another question.  I did run flash-aid.  But I see that it did not propagate to all user accounts.  Is there a way (remember my novice status, please) to install software so that it propagates to all user accounts?  I can't believe that installations have to happen under each user account.

Thank you so much for your assistance.

Most FLASH-AID operations are done on the system level and should fix the problems for all users. The only thing it does not do for all users is the removal of manually installed plugins under the ~/.mozilla folder and under Wine. But I can implement this in the next version. Thanks for bringing this to my attention.

EDIT: version 1.0.11 is already available for download. It adds multi-user support and also lightspark plugin removal.

---

### Post by NorgeNerd on 2010-08-18
> **lovinglinux said:**
> Most FLASH-AID operations are done on the system level and should fix the problems for all users. The only thing it does not do for all users is the removal of manually installed plugins under the ~/.mozilla folder and under Wine. But I can implement this in the next version. Thanks for bringing this to my attention.

EDIT: version 1.0.11 is already available for download. It adds multi-user support and also lightspark plugin removal.

Wonderful.  Thanks for the great advice and the great utility.  One more question (sorry to be a pest):  I'm wondering what you mean when you asked(a few posts back)whether I "ran" Flash-Aid after installing it.  The information on your LovingLinux web site suggests that it runs automatically.  All the user needs to do (apparently) is to install Flash-Aid, and then restart Firefox.  Am I missing something?

Oh--I neglected to mention that I'm completely up and running now.  That's no surprise, of course, but I do want to publicly acknowledge your valuable assistance.

---

### Post by lovinglinux on 2010-08-18
> **NorgeNerd said:**
> Wonderful.  Thanks for the great advice and the great utility...Oh--I neglected to mention that I'm completely up and running now.  That's no surprise, of course, but I do want to publicly acknowledge your valuable assistance.

No problem. Thanks for the heads up. I'm glad to help. 

> **NorgeNerd said:**
> One more question (sorry to be a pest):  I'm wondering what you mean when you asked(a few posts back)whether I "ran" Flash-Aid after installing it.  The information on your LovingLinux web site suggests that it runs automatically.  All the user needs to do (apparently) is to install Flash-Aid, and then restart Firefox.  Am I missing something?

I have included an automatic launcher that starts when the user install FLASH-AID for the first time or when it gets some of the extension updates. It only starts automatically if is absolutely necessary to run the installer again. I made this way because some users were re-installing flash every time they got a FLASH-AID update, which isn't really necessary. Nevertheless, I also included a manual launcher that is available in the statusbar and the navigation toolbar, so users can remove and install flash manually if needed, without the need to re-install or update the extension.

When I asked if you "ran" (I'm not sure if this is proper English :)) FLASH-AID, I just wanted to make sure you have installed it and it prompted for the flash installation, because it should have removed the last remaining file. Now I know it wasn't removed because was from another user account.

---

### Post by robiinlee on 2010-08-27
I uninstalled firefox using the Synaptic Manager and deleted my firefox profile manually. I used your addon to install flash. It worked, however, the flash plugin does not show itself in firefox. Hence, flash does not load on sites like youtube and it asks me to install the plugin. Even if i do it prompts again when I restart firefox. (timezone GMT+8 )
[B]
Log:[/B]
Ubuntu Architecture

Linux riiddle 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'

---

### Post by lovinglinux on 2010-08-27
> **robiinlee said:**
> I uninstalled firefox using the Synaptic Manager and deleted my firefox profile manually. I used your addon to install flash. It worked, however, the flash plugin does not show itself in firefox. Hence, flash does not load on sites like youtube and it asks me to install the plugin. Even if i do it prompts again when I restart firefox. (timezone GMT+8 )
[B]
Log:[/B]
Ubuntu Architecture

Linux riiddle 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'

I can't see anything wrong in your report. Is there a Shockwave entry in **about[NOPARSE]:[/NOPARSE]plugins**?

---

### Post by orthopod on 2010-08-27
Well, - I just installed the alpha 10.10 release (not rec for daily use, but it seems stable), and EVERYTHING works perfectly out of the box.
Youtube, Flash, Hulu (yeah watched family guy yesterday).  Didn't have to install any plugins - it just works.

Just had to install libxine-ffmpeg to get Amarok to play MP3s, otherwise it seems flawless.

---

### Post by robiinlee on 2010-08-27
> **lovinglinux said:**
> I can't see anything wrong in your report. Is there a Shockwave entry in **about[NOPARSE]:[/NOPARSE]plugins**?

No there is no Shockwave entry in about: plugins.

---

### Post by pivotraze on 2010-08-27
Hi! Flash is not working in Chromium Browser, but is in Firefox. (No audio, but that is not with flash only, but with Ubuntu...) and am confused...

---

### Post by lovinglinux on 2010-08-27
> **robiinlee said:**
> No there is no Shockwave entry in about: plugins.

Close Firefox, go to your Firefox profile folder ~/.mozilla/firefox/<profilename> and delete the file **pluginreg.dat**. Start Firefox and check again the about[noparse]:[/noparse]plugins page.

> **pivotraze said:**
> Hi! Flash is not working in Chromium Browser, but is in Firefox. (No audio, but that is not with flash only, but with Ubuntu...) and am confused...

[http://ubuntuforums.org/showthread.php?t=1556090](http://ubuntuforums.org/showthread.php?t=1556090)

For the audio, see [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by robiinlee on 2010-08-27
> Close Firefox, go to your Firefox profile folder ~/.mozilla/firefox/<profilename> and delete the file pluginreg.dat. Start Firefox and check again the about:plugins page.


It worked! Thank you :D

---

### Post by lovinglinux on 2010-08-27
> **robiinlee said:**
> It worked! Thank you :D

You are welcome.

---

### Post by - Lady - on 2010-09-11
Hi LovingLinux,

I have a problem with Adobe flash Player too;) 

Mostly videos just don`t play. Example here: [http://dramaair.com/air-drama-movie-play.php?mid=1804](http://dramaair.com/air-drama-movie-play.php?mid=1804)

The window is cut in half and Adobe won`t even start to load. 
(These videos are playing on Vista and XP though)

I must say I am new to Linux (Ubuntu) .
I `ve read through your troubleshooting page in your "blog", nothing helped. I also installed your FlashAId, but the problem still exists.

Some days ago I forbid flashplayer to save any contents by this command:
rm -rf ~/.macromedia/Flash_Player/* ; chmod -R a-rw ~/.macromedia/Flash_Player/

I read that some sites need to storage contents so that the video can play. Ok I tried to check this in the settings (at "how much info..is allowed to be storaged?"), but it won`t apply. Everytime I click back to settings the "regulator" is at O kb, but i set it to 100 KB.

Do you think it has something to do with the command I wrote before?

Sorry for my bad English, I am from Germany.

Thank you.

Lady

---

### Post by lovinglinux on 2010-09-12
> **- Lady - said:**
> Hi LovingLinux,

I have a problem with Adobe flash Player too;) 

Mostly videos just don`t play. Example here: [http://dramaair.com/air-drama-movie-play.php?mid=1804](http://dramaair.com/air-drama-movie-play.php?mid=1804)

That video won't work here either, although it plays on Chrome.

Can you view YouTube videos?

---

### Post by - Lady - on 2010-09-12
Hi, thanks for replying ;)   Yes, youtube videos work. Sometimes I watch tv online. And on those pages it won´t play either..:(

---

### Post by lovinglinux on 2010-09-12
> **- Lady - said:**
> Hi, thanks for replying ;)   Yes, youtube videos work. Sometimes I watch tv online. And on those pages it won´t play either..:(

So I guess that site player is not playing well with Firefox.

---

### Post by - Lady - on 2010-09-12
Hi!

But exactly those sites where Adobe won`t play on Ubuntu are working fine on Vista and XP with same Firefox.
Hmmm

:confused::? *confused*
 I forgot to mention, that one week ago those videos (I gave the link in my first post) worked fine, I could watch them. Than there was an update :     


gsfonts-x11 (0.21) java-common (0.34) odbcinst (2.2.11-21) odbcinst1debian1 (2.2.11-21) sun-java6-bin (6.20dlj-1ubuntu3) sun-java6-jre (6.20dlj-1ubuntu3) sun-java6-plugin (6.20dlj-1ubuntu3) unixodbc (2.2.11-21)     

And the moment where I forbid Adobe to storage any contents by this command I wrote in my first post...  
And since that time the videos haven`t worked anymore.   I tried to deinstall Adobe and deleted all the left data, installed it again , but nothing helped. 

So I think it either because of this update or the fact that I forbid the storage in the settings. I can`t change the settings back with the right mouse click on the video, cause they won`be taken, I mean they cannot be saved.
 I hope you can understand what I wrote above ^^ 

Greetz ;),  Lady

---

### Post by lovinglinux on 2010-09-12
Just delete the macromedia folder from Nautilus.

---

### Post by - Lady - on 2010-09-13
Hi, 

I want to search for this  folder, but nothing found? 

Sorry for the language...8-)

Pic 1:In gray it reads there: File not found

Pic 2: I 've tried again by changing the searching settings. 

Failure: Access denied.


What I am doing wrong?


Thank you for your patience ^^


Lady

( I am new to Linux)

---

### Post by lovinglinux on 2010-09-13
> **- Lady - said:**
> Hi, 

I want to search for this  folder, but nothing found? 

Sorry for the language...8-)

Pic 1:In gray it reads there: File not found

Pic 2: I 've tried again by changing the searching settings. 

Failure: Access denied.


What I am doing wrong?


Thank you for your patience ^^


Lady

( I am new to Linux)


Just run this on a terminal (make sure you type it right, otherwise you might delete important stuff with such command):

```
rm -rf ~/.macromedia
```

---

### Post by - Lady - on 2010-09-13
Whoa!

You are a genius!
The videos are working now. 

The one in my first post as well as the other on the streaming online Tv site. Everything works fine. And I can even change the settings, and they stay saved.

Thank you very much!!!!:KS=D>\\:D/:guitar:

---

### Post by Kir_B on 2010-09-13
Hey lovinglinux.

I just used [flashaid]("http://ubuntuforums.org/flashaid") yesterday and I love your contribution. Very much appreciated!

After it ran, I got the foolowing line at the end:
"[COLOR=Red]**ln: creating symbolic link `/usr/lib/firefox-addons/plugins/libflashplayer.so': No such file or directory**[/COLOR]"

I'm not sure that this is normal, so I've copied the terminal readout and saved it as a text file, which I'll attach to this post.

I hope I'm being helpful, instead of being a pain, but still, I thought it might be useful to you.

Keep up the _**awesome work**_!!!

Thanks, yet again! Kirby

---

### Post by lovinglinux on 2010-09-13
> **Kir_B said:**
> Hey lovinglinux.

I just used [flashaid]("http://ubuntuforums.org/flashaid") yesterday and I love your contribution. Very much appreciated!

After it ran, I got the foolowing line at the end:
"[COLOR=Red]**ln: creating symbolic link `/usr/lib/firefox-addons/plugins/libflashplayer.so': No such file or directory**[/COLOR]"

I'm not sure that this is normal, so I've copied the terminal readout and saved it as a text file, which I'll attach to this post.

I hope I'm being helpful, instead of being a pain, but still, I thought it might be useful to you.

Keep up the _**awesome work**_!!!

Thanks, yet again! Kirby

Thanks for all your comments and for the feedback.

The error is because you don't have firefox package installed, so it can't find the file to create the symlink. 

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Kir_B on 2010-09-13
Thanks for the quick response and I'll try to respond in as detailed a fashion as possible.
> 
Type **about:config** in Firefox address bar, then type **plugin.expose_full_path**  in the filter, then double-click the same item in the results to make  it **true**. Then type **about:plugins** in the address  bar, find Shockwave Flash, copy the corresponding Path and Version and  paste here. it should look lie the image below:
**1 - Flash Version**:
The result of** plugin.expose_full_path** was already true.

the corresponding path for "shockwave flash": [B]File:  /usr/lib/flashplugin-installer/libflashplayer.so

[/B]Version: Shockwave Flash 10.1 r82

**2 - Firefox version and architecture:**
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100405 Firefox/3.6.3 (Swiftfox)

[B]3 - System Info:
[/B]It's attached to this post**.**

I hope I haven't missed anything.

Thanks again. Kirby

---

### Post by lovinglinux on 2010-09-13
> **Kir_B said:**
> Thanks for the quick response and I'll try to respond in as detailed a fashion as possible.

**1 - Flash Version**:
The result of** plugin.expose_full_path** was already true.

the corresponding path for "shockwave flash": [B]File:  /usr/lib/flashplugin-installer/libflashplayer.so

[/B]Version: Shockwave Flash 10.1 r82

**2 - Firefox version and architecture:**
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100405 Firefox/3.6.3 (Swiftfox)

[B]3 - System Info:
[/B]It's attached to this post**.**

I hope I haven't missed anything.

Thanks again. Kirby

I think you can safely ignore that error, since you have Swiftfox and it is detecting the plugin in /usr/lib/flashplugin-installer/libflashplayer.so. Does flash work properly now or do you still have issues?

---

### Post by Kir_B on 2010-09-13
> **lovinglinux said:**
> I think you can safely ignore that error, since you have Swiftfox and it is detecting the plugin in /usr/lib/flashplugin-installer/libflashplayer.so. Does flash work properly now or do you still have issues?

Thanks for the info.

I was only bringing it up so that you knew that it was happening.

All flash does work, but at times is using my processor like it owns it. I know that I still have to follow the instructions for [Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html"), which is the next project that I'll tackle.

Thanks a tonne. Kirby

P.S. Awesome work, I love it!!!

---

### Post by lovinglinux on 2010-09-14
> **Kir_B said:**
> Thanks for the info.

I was only bringing it up so that you knew that it was happening.

All flash does work, but at times is using my processor like it owns it. I know that I still have to follow the instructions for [Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html"), which is the next project that I'll tackle.

Thanks a tonne. Kirby

P.S. Awesome work, I love it!!!

Thanks a lot for the feedback.

---

### Post by wiz2010 on 2010-09-17
I was trying to get gnash working atleast with youtube. Installed gnash version 8.8 and also mozilla-plugin-gnash. But it was in vain as i could not get it working with firefox after trying a lot. I lost interest in it so went back to old things. After some days I found that gnash worked well in google-chrome (from google repository) and also in chromium (from ubuntu repository). I had to remove google-chrome's flashplugin that comes with it. I got gnash working only with youtube may be because other things needed atleast flash 10.

As it is working in chrome, how can I get it working in firefox?

When I tried firefox run in terminal i got these messages

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgnashplugin.so [/usr/lib/mozilla/plugins/libgnashplugin.so: file too short]



Thanks in advance

---

### Post by lovinglinux on 2010-09-17
I also couldn't make it work with Firefox.

---

### Post by - Lady - on 2010-09-28
Hi lovinglinux!

it`s me again ^^

I just have one question. There are updates for the flash player available, but I don`t know which one to install that everything work fine as now is. 
Both of them?

Thank you!!

Lady

---

### Post by lovinglinux on 2010-09-28
> **- Lady - said:**
> Hi lovinglinux!

it`s me again ^^

I just have one question. There are updates for the flash player available, but I don`t know which one to install that everything work fine as now is. 
Both of them?

Thank you!!

Lady

Hi Lady,

It is recommended that whenever the Update Manager asks you to upgrade flash, then update both. The flashplugin-nofree is just a dummy package and not necessary, but it should be updated as well if you have it installed.

---

### Post by - Lady - on 2010-09-28
Thank you for your quick answer. This time after the update everything works fine as was before.

---

### Post by Anjin-san on 2010-10-31
Hi lovinglinux,

I had a variety of problems playing videos from websites like youtube in the past until I found Flash-Aid. After using Flash-Aid everything worked fine for months, so many thanks for that brilliant add-on.

Now I have a new problem:
I was watching a video on youtube when Firefox crashed. Since that crash videos are played about 4 times faster than normal and there is no sound.

Reinstalling Flash, Firefox and Flash-Aid didn't solve the problem. 
Surprisingly - at least to my mind - the problem appears only on that user-account. On my admin-account everything works fine like before. Therefore I'm suspecting some king of corrupted user-config but I'm not sure about that.

Shockwave Flash

    Datei: /usr/lib/flashplugin-square/libflashplayer.so
    Version: 
    Shockwave Flash 10.2 d161

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.10 (maverick) Firefox/3.6.12


[LEFT]Any help would be appreciated.[COLOR=Black][U]
[/U][/COLOR][/LEFT]

---

### Post by lovinglinux on 2010-10-31
> **Anjin-san said:**
> Hi lovinglinux,

I had a variety of problems playing videos from websites like youtube in the past until I found Flash-Aid. After using Flash-Aid everything worked fine for months, so many thanks for that brilliant add-on.

Now I have a new problem:
I was watching a video on youtube when Firefox crashed. Since that crash videos are played about 4 times faster than normal and there is no sound.

Reinstalling Flash, Firefox and Flash-Aid didn't solve the problem. 
Surprisingly - at least to my mind - the problem appears only on that user-account. On my admin-account everything works fine like before. Therefore I'm suspecting some king of corrupted user-config but I'm not sure about that.

Shockwave Flash

    Datei: /usr/lib/flashplugin-square/libflashplayer.so
    Version: 
    Shockwave Flash 10.2 d161

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.10 (maverick) Firefox/3.6.12


[LEFT]Any help would be appreciated.[COLOR=Black][U]
[/U][/COLOR][/LEFT]

Try to delete the folders ~/.adobe and ~/.macromedia (backup if you play flash games and want to keep scores).

You are currently using the flash version installed by *sevenmachines-flash* ppa, not the one provided by FLASH_AID. Is the same version, but FLASH-AID has no control over it. So, try to re-install *flashplugin64-installer* or purge it and then use FLASH-AID to reinstall flash 64bit version.

---

### Post by Anjin-san on 2010-10-31
> **lovinglinux said:**
> Try to delete the folders ~/.adobe and ~/.macromedia (backup if you play flash games and want to keep scores).

You are currently using the flash version installed by *sevenmachines-flash* ppa, not the one provided by FLASH_AID. Is the same version, but FLASH-AID has no control over it. So, try to re-install *flashplugin64-installer* or purge it and then use FLASH-AID to reinstall flash 64bit version.

Thanks for the quick reply.

The sevenmachines-flash was one of the remnants of my earlier attempts to solve the problem. I deleted the folders, re-installed flashplugin64-installer and started Flash-Aid again.

Unfortunately the problem persists.

---

### Post by lovinglinux on 2010-10-31
> **Anjin-san said:**
> Thanks for the quick reply.

The sevenmachines-flash was one of the remnants of my earlier attempts to solve the problem. I deleted the folders, re-installed flashplugin64-installer and started Flash-Aid again.

Unfortunately the problem persists.

Purge **flashplugin64-installer**...

```
sudo apt-get purge flashplugin64-installer
```

...then use FLASH-AID to install the 64bit version or the 32bit versions. Experience varies, so I would recommend trying both versions.

---

### Post by Anjin-san on 2010-10-31
> **lovinglinux said:**
> Purge **flashplugin64-installer**...

```
sudo apt-get purge flashplugin64-installer
```...then use FLASH-AID to install the 64bit version or the 32bit versions. Experience varies, so I would recommend trying both versions.


Ok, I did as suggested and tried both versions but nothing changed.

In order to check if this is a browser-specific problem I tried Opera but the results are the same as with Firefox.

---

### Post by lovinglinux on 2010-10-31
> **Anjin-san said:**
> Ok, I did as suggested and tried both versions but nothing changed.

In order to check if this is a browser-specific problem I tried Opera but the results are the same as with Firefox.

What happens if you create a new Ubuntu user just for testing?

---

### Post by Anjin-san on 2010-11-01
> **lovinglinux said:**
> What happens if you create a new Ubuntu user just for testing?

The videos are playing normal.
At least using a new user account would be a backup plan if there is no other solution.

---

### Post by lovinglinux on 2010-11-01
> **Anjin-san said:**
> The videos are playing normal.
At least using a new user account would be a backup plan if there is no other solution.

So I guess the problem lies on the user pulseaudio config files. 

Try this:

```
rm -fr ~/.pulse ~/.asound*
```

---

### Post by Automat2 on 2010-11-01
I've got a problem.

I can play videos in Youtube, embedded videos, and so on, but there are websites that ask me for "Adobe Flash player 10.0.32", saying that I've got "Adobe ... 10.0"

I am running Ubuntu 10.10 64-bits and I've already installed and upgraded your Flash-Aid.

Any solution?

---

### Post by lovinglinux on 2010-11-01
> **Automat2 said:**
> I've got a problem.

I can play videos in Youtube, embedded videos, and so on, but there are websites that ask me for "Adobe Flash player 10.0.32", saying that I've got "Adobe ... 10.0"

I am running Ubuntu 10.10 64-bits and I've already installed and upgraded your Flash-Aid.

Any solution?

Please provide a link for testing. 

Those kind of messages usually happens when you have Gnash installed, but this is not the case since you are using FLASH-AID. So I suppose is an incompatibility with the new preview version of flash 64bit and the web site player. You could try the 32bit with the nspluginwrapper. Just run FLASH-AID again, but choose the 32bit when prompted. You can install the 64bit again later if this doesn't solve your problem.

---

### Post by Automat2 on 2010-11-01
I've tried with 32-bits and asks me to install Flash, Shockwave and Gnash. At 64-bits, it asks me to upgrade to Flash 10.0.32

The most problems I've found, are on this link: [http://www.lovefilm.com](http://www.lovefilm.com) (you should be a member).

They've got a feature where it's possible to watch films online. I used to be able to see trailers and movies, now, I think since the upgrade to Maverick, I can't. I think that I found another website with similar problems, but I don't remember.

---

### Post by Automat2 on 2010-11-02
I've found another website I have some problems with. I can see the image on the minimized video screen, but not when I select the fullscreen mode. The sound is untouched.

[http://www.e-noticies.cat/](http://www.e-noticies.cat/)

---

### Post by lovinglinux on 2010-11-02
> **Automat2 said:**
> I've tried with 32-bits and asks me to install Flash, Shockwave and Gnash. At 64-bits, it asks me to upgrade to Flash 10.0.32

The most problems I've found, are on this link: [http://www.lovefilm.com](http://www.lovefilm.com) (you should be a member).

They've got a feature where it's possible to watch films online. I used to be able to see trailers and movies, now, I think since the upgrade to Maverick, I can't. I think that I found another website with similar problems, but I don't remember.

Please post a new report.

---

### Post by Anjin-san on 2010-11-02
> **lovinglinux said:**
> So I guess the problem lies on the user pulseaudio config files. 

Try this:

```
rm -fr ~/.pulse ~/.asound*
```

Yes! Problem solved. :)
Many thanks for your help.

---

### Post by lovinglinux on 2010-11-02
> **Anjin-san said:**
> Yes! Problem solved. :)
Many thanks for your help.

:guitar:

You are welcome.

---

### Post by Automat2 on 2010-11-03
> **lovinglinux said:**
> Please post a new report.

This is:

```
buntu Architecture

Linux jordi-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

bryceharrington-purple-lucid.list
bryceharrington-purple-lucid.list.save
ferramroberto-extra-lucid.list
ferramroberto-extra-lucid.list.distUpgrade
ferramroberto-extra-lucid.list.save
lucid-partner.list
lucid-partner.list.distUpgrade
lucid-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
sevenmachines-flash-maverick.list

Flash packages


Plugin locations

/home/jordi/.cache/.fr-pCbJVo/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapp*er.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapp*er.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

---

### Post by lovinglinux on 2010-11-03
> **Automat2 said:**
> This is:

```
buntu Architecture

Linux jordi-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

bryceharrington-purple-lucid.list
bryceharrington-purple-lucid.list.save
ferramroberto-extra-lucid.list
ferramroberto-extra-lucid.list.distUpgrade
ferramroberto-extra-lucid.list.save
lucid-partner.list
lucid-partner.list.distUpgrade
lucid-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
sevenmachines-flash-maverick.list

Flash packages


Plugin locations

/home/jordi/.cache/.fr-pCbJVo/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapp*er.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapp*er.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

It appears to me that you have now removed all flash versions. Please use FLASH-AID to install it again. Then generate a new report. Then test if it works.

---

### Post by Automat2 on 2010-11-04
> **lovinglinux said:**
> It appears to me that you have now removed all flash versions. Please use FLASH-AID to install it again. Then generate a new report. Then test if it works.
I had to install the Flash drivers (Shockwave, Gnash and Flash) and then, Flash-Aid at 32-bits for me to see those websites. And to obtain this code:
```
Ubuntu Architecture

Linux jordi-desktop 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:13:06 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/home/jordi/.cache/.fr-pCbJVo/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapp*er.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
```

---

### Post by lovinglinux on 2010-11-04
> **Automat2 said:**
> I had to install the Flash drivers (Shockwave, Gnash and Flash) and then, Flash-Aid at 32-bits for me to see those websites.

Actually, only FLASH-AID would suffice, because it removes all those versions you installed before it.

> **Automat2 said:**
> [CODE]Ubuntu Architecture

Linux jordi-desktop 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:13:06 UTC 2010 x86_64 GNU/Linux


Your report is OK. Does it work know? Any additional problem you need to fix?

---

### Post by Automat2 on 2010-11-04
> **lovinglinux said:**
> Actually, only FLASH-AID would suffice, because it removes all those versions you installed before it.

Your report is OK. Does it work know? Any additional problem you need to fix?

There were some websites that asked me to install Flash too, despite having  installed Flash-Aid, on its own. So I kept trying different set-ups and the actual sequence was: Uninstall 64-bits, reinstall Flash -from the repos-, reinstall Flash-Aid 32-bits.

After that, I got the report. And it's working fine. I don't know if I could now remove Flash and it would still be working.

64-bits worked ok except for the sites I mentioned above, which was rather annoying.

---

### Post by lovinglinux on 2010-11-04
> **Automat2 said:**
> I don't know if I could now remove Flash and it would still be working.

No, don't do that. FLASH-AID is just an installer/remover, so if you remove flash from your system using the Software Center, Synaptic or apt via command-line it will completely remove flash.

---

### Post by Automat2 on 2010-11-05
Do you know why Flash (or Flash-Aid) works on certain websites at 64-bits and not on others? I don't mind having Flash-Aid at 32-bits, because ultimately, I would like to be able to see videos everywhere.

Does it depend on the particular website or is it a Flash (or the wrapper) incompatibility?

---

### Post by lovinglinux on 2010-11-05
> **Automat2 said:**
> Do you know why Flash (or Flash-Aid) works on certain websites at 64-bits and not on others? I don't mind having Flash-Aid at 32-bits, because ultimately, I would like to be able to see videos everywhere.

Does it depend on the particular website or is it a Flash (or the wrapper) incompatibility?

Depends on the player used in the web site. Some players have version incompatibilities, don't play well with the wrapper or have some special feature that screw things up.

---

### Post by Automat2 on 2010-11-05
Thanks lovinglinux. I guess I am sorted now, until we can use the 64-bits version everywhere.

Keep the hard work.

---

### Post by xescuy on 2010-11-10
Hello lovinglinux
Just a quick fault description and some basic reports:

I'm experiencing the good old high processor usage on all flash videos. 
All is running well for the first 3-4 min of the video (runs in full screen @ 1080p, all interactive menus are functional, etc etc). During this the processor usage is not higher than 40%-60%.
Afterwards the CPU spikes to 97%-98% the movie turns into a slide show and the whole PC slows down for maybe 30 sec - 1 min. Finally, the CPU goes down to normal speeds and so is the video and the PC. And the whole process repeats itself after another minute or so. 

**Shockwave Flash**

 File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.2 d161
**Your User Agent:** Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.04 (lucid) Firefox/3.6.12

hardware report 
Computer
********


Summary
-------

-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Memory        : 2057MB (705MB used)
Operating System        : Ubuntu 10.04.1 LTS
Date/Time        : Thu 11 Nov 2010 01:20:07 NZDT
-Display-
Resolution        : 1680x1050 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
Audio Adapter        : USB-Audio - C-Media USB Headphone Set  
-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 Microsoft Comfort Curve Keyboard 2000
 Microsoft Comfort Curve Keyboard 2000
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
 C-Media USB Headphone Set
 HDA Digital PCBeep
-Printers-
No printers found
-SCSI Disks-
ASUS DRW-1814BLT
ATA ST3250310AS
WD 3200BMV External
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader

I have updated the Nvidia 8600 GT drivers to the latest one available and the Flash to the version above from the sevenmachines ppa.
Any ideas would be greatly appreciated as I've been struggling with this since I updated to Lucid 64bit 

Please let me know if you need more info and I'll make sure to get it for you.

Thanks

---

### Post by Mariane on 2010-12-11
I have a set of slides which I downloaded through mozilla flashget plugin. 
When I try to open the file I see the first slide but not the others. 
I tried to print them with the command:

lpr -P PDF Coppelie\ Cocq\ Liminality\ 2.swf > Copp.pdf

Because simple

lpr -P PDF Coppelie\ Cocq\ Liminality\ 2.swf

returned no error but apparently did nothing. 

Copp.pdf exists now but cannot be opened. 

The slides are the one called "Flash files (powerpoints)" there:
[http://kemst.hi.is/gods_and_goddesses/](http://kemst.hi.is/gods_and_goddesses/)
I can apparently download them but I can neither view them online nor offline nor
print them to pdf. And watching the conference videos without being able to see the slides makes no sense!

Please help. 

Mariane

---

### Post by ron999 on 2010-12-11
> **Mariane said:**
> 
When I try to open the file I see the first slide but not the others. 

Hi
Open the downloaded swf file with Firefox.
See the first slide then click on it with mouse to cycle through other slides.

---

### Post by Mariane on 2010-12-11
You again! Next time I need help I'll send you an mp! (only joking).
Thanks very much Ron999, one again you saved my life :D 

And it was that simple and I was trying the most complicated things I could think of... 

Mariane

---

### Post by lovinglinux on 2010-12-11
> **xescuy said:**
> Hello lovinglinux
Just a quick fault description and some basic reports:

I'm experiencing the good old high processor usage on all flash videos. 
All is running well for the first 3-4 min of the video (runs in full screen @ 1080p, all interactive menus are functional, etc etc). During this the processor usage is not higher than 40%-60%.
Afterwards the CPU spikes to 97%-98% the movie turns into a slide show and the whole PC slows down for maybe 30 sec - 1 min. Finally, the CPU goes down to normal speeds and so is the video and the PC. And the whole process repeats itself after another minute or so. 


First of all, I'm sorry for the lack of response for so long. I don't know how I missed your post.

It looks to me you have a CPU heating problem. Flash starts to heat the CPU, then it stutters, then CPU cools down and it goes back to normal.

---

### Post by xescuy on 2010-12-18
Hi Lovinglinux. 
Thanks for all your help. I've cleaned the CPU fan/heatsink and what a mess that was.
The whole flash situation has improved but now that the fan and the heatsink are not all nice and plushy the noise is baad :)
So I guess I'm at the point where I need to buy a new MOBO with enough power connectors for all the fans in the box. I'm running without a chassis fan so that's a bit of an issue.
Thanks a lot for all your help again and I hope that you'll continue helping ppl.

Cheers
R

---

### Post by lovinglinux on 2010-12-18
> **xescuy said:**
> Hi Lovinglinux. 
Thanks for all your help. I've cleaned the CPU fan/heatsink and what a mess that was.
The whole flash situation has improved but now that the fan and the heatsink are not all nice and plushy the noise is baad :)
So I guess I'm at the point where I need to buy a new MOBO with enough power connectors for all the fans in the box. I'm running without a chassis fan so that's a bit of an issue.
Thanks a lot for all your help again and I hope that you'll continue helping ppl.

Cheers
R

You are welcome.

---

### Post by sswords on 2010-12-18
Hi,

Flash works for me on most websites (e.g. Youtube) but on thedailyshow.com, in particular, all the videos give me a dialog box with the following message and an "OK" button, and then go black when I press "OK":

```
Error loading stylesheet. 
RSL http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz 
failed to load. Error #2046

```

I've tried a number of solutions found while Googling around and they haven't made any difference.  I'm on Ubuntu 10.10 64-bit and I've tried both 64- and 32-bit plugins, additionally.

Here's my info:

about: plugins:
Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

(note: I've also tried the 64-bit plugin)

Firefox version:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13

(note: recently updated, but had the same problem before)

firefox-report.txt -- attached.

Any ideas?

Thanks :-)

---

### Post by lovinglinux on 2010-12-19
> **sswords said:**
> Hi,

Flash works for me on most websites (e.g. Youtube) but on thedailyshow.com, in particular, all the videos give me a dialog box with the following message and an "OK" button, and then go black when I press "OK":

```
Error loading stylesheet. 
RSL http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz 
failed to load. Error #2046

```

I think your problem on that site is not flash related. I think the problem is that the flash module has a stylesheet that is hosted on a different domain and your browser is unable to resolve the domain IP. So is probably a DNS issue.

Try to disable ipv6.

[LIST]
[*]Type a**bout[noparse]:[/noparse]config** in Firefox address bar to open the advanced preferences 
[*]Type **network.dns.disableIPv6** in the filter field and hit enter
[*]Double click **network.dns.disableIPv6** in the results in order to set it as true
[/LIST]

Also clear th browser cache.

---

### Post by sswords on 2010-12-19
Hi Lovinglinux,

Thanks for the suggestion.  I tried it (and additionally deleted my ~/.adobe and ~/.macromedia directories) but unfortunately I still get the same error.  If it makes any difference, I can point Firefox at the URL mentioned in the error message, and it loads some glob of binary; maybe that suggests that it's not a DNS problem.  (Also, I dual-boot Windows, where the site works, and my resolv.conf lists the same two addresses that Windows lists as its dns servers.)

It's pretty mystifying since it's cross-browser (Chromium sees the same error), it's specific to whatever Flash video scheme Comedy Central uses, and apparently many Linux users running near-identical setups are not having this problem or have solved it using a variety of different methods.

Thanks again; let me know if you have any other ideas.

Edit: Also, the same problem occurs with a brand new Firefox profile.

---

### Post by sswords on 2010-12-19
> **sswords said:**
> 
...

It's pretty mystifying since it's cross-browser (Chromium sees the same error), it's specific to whatever Flash video scheme Comedy Central uses, and apparently many Linux users running near-identical setups are not having this problem or have solved it using a variety of different methods.

Thanks again; let me know if you have any other ideas.

Edit: Also, the same problem occurs with a brand new Firefox profile.

Okay, I just made a new user, logged in as that user, and was able to watch video on that site.  Now I just need to figure out what is wrong with my original user that doesn't have to do with any Firefox settings or the .adobe or .macromedia directories.

---

### Post by sswords on 2010-12-19
> **sswords said:**
> Okay, I just made a new user, logged in as that user, and was able to watch video on that site.  Now I just need to figure out what is wrong with my original user that doesn't have to do with any Firefox settings or the .adobe or .macromedia directories.

I guess I've solved my problem, but it's a weird one.  First I renamed my .mozilla/firefox/profiles.ini.  I ran Firefox to generate a new one, and noticed that the problem was gone -- in both Firefox and Chromium (!).  Of course, all my bookmarks and settings were also gone, so I wasn't satisfied with this solution.  So I opened the new profiles.ini and pasted in the info about my real profile from the original one as a second profile there, labeled [Profile1] (the first being [Profile0]).  Observed that thedailyshow.com still worked in Chromium, and also now in Firefox even with my original profile.  Switching the two versions of profiles.ini reliably causes the problem to go away and come back in both browsers.

So WTF.  It seems that the Flash plugin makes some use of a user's profiles.ini, and probably, in particular, the first profile listed there, even when you're running that profile, and even when you're not running Firefox at all.  Oddly enough, this behavior is now something I'm counting on, because it seems there's still something broken about my actual Firefox profile that this arrangement works around.

---

### Post by lovinglinux on 2010-12-19
> **sswords said:**
> I guess I've solved my problem, but it's a weird one.  First I renamed my .mozilla/firefox/profiles.ini.  I ran Firefox to generate a new one, and noticed that the problem was gone -- in both Firefox and Chromium (!).  Of course, all my bookmarks and settings were also gone, so I wasn't satisfied with this solution.  So I opened the new profiles.ini and pasted in the info about my real profile from the original one as a second profile there, labeled [Profile1] (the first being [Profile0]).  Observed that thedailyshow.com still worked in Chromium, and also now in Firefox even with my original profile.  Switching the two versions of profiles.ini reliably causes the problem to go away and come back in both browsers.

So WTF.  It seems that the Flash plugin makes some use of a user's profiles.ini, and probably, in particular, the first profile listed there, even when you're running that profile, and even when you're not running Firefox at all.  Oddly enough, this behavior is now something I'm counting on, because it seems there's still something broken about my actual Firefox profile that this arrangement works around.

That is really weird. I have no idea why and how your Firefox profile could affect Chrome and how deleting the profiles.ini would solve the problem, even adding your profile back.

---

### Post by isuru_opt on 2010-12-30
This is a repost from [here]("http://ubuntuforums.org/showthread.php?t=1491268&page=1") as suggested by lovinglinux.

I cannot view clips in youtube or metacafe, they all go in fast forward  mode. Then I saw several people have recomended Flash-Aid and I  installed it. I tried installing both 32 and 64 bit versions of flash.  but unfortunately it didnot solve my problem. 

Below are my settings. 

uname -a
Linux isihome 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Firefox info
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13

I went through all the pages in forum post. I couldnot find one to resolve my issue and hope you could help me.

I have latest version of Flash-Aid ( 1.0.18 )

---

### Post by lovinglinux on 2010-12-30
> **isuru_opt said:**
> This is a repost from [here]("http://ubuntuforums.org/showthread.php?t=1491268&page=1") as suggested by lovinglinux.

I cannot view clips in youtube or metacafe, they all go in fast forward  mode. Then I saw several people have recomended Flash-Aid and I  installed it. I tried installing both 32 and 64 bit versions of flash.  but unfortunately it didnot solve my problem. 

Below are my settings. 

uname -a
Linux isihome 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Firefox info
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13

I went through all the pages in forum post. I couldnot find one to resolve my issue and hope you could help me.

I have latest version of Flash-Aid ( 1.0.18 )

Try to delete the ~/.macromedia folder, clear the browser cache and restart it. If that doesn't help, then see the fourth item on [this list]("http://www.webgapps.org/flash/issues-and-solutions").

---

### Post by isuru_opt on 2010-12-31
Thanks for the reply. Well, deleting .macromedia/ didnot help either.

Then I check the link you suggested. But I dont have a .asound file in my home directory. Could this have anything to do with the problem I am facing.

Thanks again for your help.

---

### Post by farmeralice on 2010-12-31
I tried using your Flash-Aid Plugin and got this error message: There was an error creating the child process for this terminal

Then I did all of the bits in there manually Re: [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)

Still no flash, would love some help since you seem to be the guru.

Flash Version is: 
File:  /usr/lib/flashplugin-nonfree/libflashplayer.soVersion:    Shockwave Flash 9.0 r289Firefox Version and architecture: Mozilla/5.0  (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/8.04  (hardy) Firefox/3.6.13Firefox Report: 
Ubuntu Architecture

Linux alice-laptop 2.6.24-28-generic #1 SMP Wed Nov 24 09:30:14 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

Firefox Packages

firefox                        install
firefox-branding                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash packages

flashplugin-nonfree                install

Plugin locations

/home/alice/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-nonfree/libflashplayer.so'

Thanks!

---

### Post by lovinglinux on 2010-12-31
> **farmeralice said:**
> I tried using your Flash-Aid Plugin and got this error message: There was an error creating the child process for this terminal

Then I did all of the bits in there manually Re: [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)

Still no flash, would love some help since you seem to be the guru.

Flash Version is: 
File:  /usr/lib/flashplugin-nonfree/libflashplayer.soVersion:    Shockwave Flash 9.0 r289Firefox Version and architecture: Mozilla/5.0  (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/8.04  (hardy) Firefox/3.6.13Firefox Report: 
Ubuntu Architecture

Hardy still uses Flash 9. Try to install the latest deb of flash 10 from Adobe: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Next version of Flash-Aid, that should be released in a couple of days will allow to easily install the beta version.

---

### Post by joehill on 2011-01-01
Holy cow, this is the strangest bug I've ever seen. I installed Ubuntu on my new netbook and was relieved to see that Comedy Central clips worked on it as opposed to my laptop (where I get the error mentioned above--

```

Error loading stylesheet. 
RSL http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz 
failed to load. Error #2046

```
Then I copied over my Firefox directory from my old laptop to my netbook and suddenly it didn't work, even when I created a new, empty profile. Tried in other browsers and it didn't work either.

Then I followed sswords's counterintuitive solution above, moving profiles.ini to have Firefox create a new one, then I moved all the contents of the old profile into the new one, and it WORKED! So the problem is not in the profile itself or anywhere else in the home directory--it's the firefox/profiles.ini, which as mentioned above, is read even when you're not using Firefox or the relevant profile. I wouldn't have believed this if I hadn't tried it.

---

### Post by lovinglinux on 2011-01-01
> **farmeralice said:**
> I tried using your Flash-Aid Plugin and got this error message: There was an error creating the child process for this terminal

This problem, which only affected Hardy users, has been fixed on version 2.0.0, which was released today. 

> **farmeralice said:**
> 
Then I did all of the bits in there manually Re: [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)

Still no flash, would love some help since you seem to be the guru.


Try version 2.0.0. You can get it from the [extension web site]("http://www.webgapps.org/addons/flash-aid"). 

> **lovinglinux said:**
> Hardy still uses Flash 9. Try to install the latest deb of flash 10 from Adobe: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Next version of Flash-Aid, that should be released in a couple of days will allow to easily install the beta version.

If you are using 64bit, then the new Flash-Aid will install the version from the repositories, which is actually the 32bit version 9 with the nspluginwrapper. If you are on 32bit, then you will get the beta version from Adobe. This limitation is because the beta 64bit is crashing on Hardy when trying to go fullscreen. Nevertheless, you can install whatever you want using the "Expert Mode" of Flash-Aid 2.0.

---

### Post by bumder on 2011-01-02
Just used latest Flash Aid 2 on my system to try and remedy my random flash crashing on both Chrome and Firefox (they use different flash version aswell.

Will test to see if crashes still occur.

Thanks

---

### Post by lovinglinux on 2011-01-02
> **bumder said:**
> Just used latest Flash Aid 2 on my system to try and remedy my random flash crashing on both Chrome and Firefox (they use different flash version aswell.

Will test to see if crashes still occur.

Thanks

Your report looks fine. Let me know how it goes.

---

### Post by bumder on 2011-01-02
Out of interest, if I wanted to return my Firefox flash version to the current stable release (10.1.102.65), instead of the beta version installed by Flash Aid (10.2.151.49), how would I go about doing it?

Thanks

---

### Post by lovinglinux on 2011-01-02
> **bumder said:**
> Out of interest, if I wanted to return my Firefox flash version to the current stable release (10.1.102.65), instead of the beta version installed by Flash Aid (10.2.151.49), how would I go about doing it?

Thanks

Click the "Expert Mode" checkbox, then the "Installation Options" tab, then select the option "Adobe from repositories", then click "Execute".

---

### Post by bumder on 2011-01-03
Not really a solution to the flash issues on linux, but I've started using VLC as a workaround, just cut and pasting the YouTube URL into 'open stream'. Seems to work well.

Also, if a flash video crashes, it may still be buffering behind the scenes. If you go into the files system, in the 'tmp' folder, you should hopefully see some randomly named .flv files that you can manually open/save with vlc.

Not ideal, but a good workaround until/if Adobe pull their finger out!

---

### Post by lovinglinux on 2011-01-03
> **bumder said:**
> Not really a solution to the flash issues on linux, but I've started using VLC as a workaround, just cut and pasting the YouTube URL into 'open stream'. Seems to work well.

Also, if a flash video crashes, it may still be buffering behind the scenes. If you go into the files system, in the 'tmp' folder, you should hopefully see some randomly named .flv files that you can manually open/save with vlc.

Not ideal, but a good workaround until/if Adobe pull their finger out!

In this case, you are going to love my extension [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer"). It can launch YouTube videos with an external player automatically or replace the video on site, using a different plugin like gecko-mediaplayer. You can also open the video on a new tab or new window.

It works on YouTube, Vimeo and Metacafe.

---

### Post by lovinglinux on 2011-01-04
If flash has sound but video is white, even when not in fullscreen, see [http://ubuntuforums.org/showpost.php?p=10317206&postcount=9](http://ubuntuforums.org/showpost.php?p=10317206&postcount=9)

---

### Post by lovinglinux on 2011-07-06
For those experiencing problems with Flash on YouTube see [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by fulm3n on 2012-06-23
hejho, i'm not quite sure if this is the right thread. anyway, i was struggling a lot with error #2046 the last weeks. neither the flash settings, the cache, nor spaces within the path of firefox' profiles.ini where responsible in my case (lubuntu 12.04, adobe flash plugin 11.2). what finally did the trick was changing the path from absolute to relative (IsRelative=1).

---

