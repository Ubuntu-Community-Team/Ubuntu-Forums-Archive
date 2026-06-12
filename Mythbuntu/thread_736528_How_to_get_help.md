---
title: "How to get help"
date: 2008-03-26
forum: Mythbuntu
---

### Post by laga on 2008-03-26
If you have a question or a problem with Mythbuntu, the following items will help you to request support in an efficient manner:



[CENTER]**General**[/CENTER]
[LIST]
[*]Make sure your new thread has a **meaningful title**. Just "Help! MythTV is not working" isn't helpful.

[*] **Complaining** that the new version of Mythbuntu/MythTV "sucks" isn't going to help anyone. In fact, it'll make it a lot less likely that you receive support. Remember, nobody is obliged to help you unless you paid them for it. Even if you're frustrated because the problem you're experiencing is very annoying, please be polite. Thank you.

[*] Please remember to search the forums and the Internet before asking here. Often, a question has already been answered.
[list]
[*] [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php) - Make sure to select the Mythbuntu forums.
[*] [http://wiki.mythtv.org](http://wiki.mythtv.org) - The MythTV wiki is a great resource.
[*] [http://www.gossamer-threads.com/lists/mythtv/](http://www.gossamer-threads.com/lists/mythtv/) - An archive of the MythTV mailing lists. Lots of problems are discussed (and resolved) on the mythtv-users mailing lists. The mythtv-dev list has lots of interesting development questions, but you probably want to exclude it when searching for answers.
[/list]
[*] Please state what **version of Ubuntu** (7.10 or 8.04) you are running.

[*] Please state what **version of MythTV** you are using. Open a terminal and type
```

apt-cache policy mythtv-common

```
 to find out. You can also use your favourite package manager. 
Just saying "0.21" isn't helpful because the MythTV packages often receive bug fixes so it's important to know the exact version.

[*] Please **provide log files**. The log files for MythTV can be found in */var/log/mythtv/*. 
If you think your problem is backend specific, you can find the log files for mythbackend in */var/log/mythtv/mythbackend.log*.
The frontend logs to */var/log/mythtv/mythfrontend.log*. If you're using Mythwelcome, */var/log/mythtv/mythwelcome.log* is the right place.

To access these log files, just open them in your favourite editor or bring up a terminal and type ```
less /var/log/mythtv/mythfrontend.log
``` Of course, you need to substitute the correct file name here.

Sometimes, the log files will already contain instructions to fix the problem you're seeing so it's beneficial to look over them before posting. If you're experiencing a more general problem, like no video playback when you go to 'Watch TV', it's a good idea to post information from both the frontend and the backend log.
[/list]

[CENTER]**Extra credit**[/CENTER]
[list]
[*] If you're feeling that your log files don't provide enough information, you might benefit from increasing the verbosity. 

Use ```
mythfrontend -v help
``` to find out about the available verbosity levels. After you've chosen some, for example "important,general,audio", proceed with the instructions below. Please note that you have to prepend "--verbose", so an example line might look like *--verbose "important,general,audio"*.

[list]
[*] mythfrontend: If your mythfrontend starts automatically on boot, you should edit */etc/mythtv/session-settings* and adjust the *MYTHFRONTEND_OPTS* variable in that file. Please note that it'll be necessary to uncomment that line by removing the *#* symbol at the beginning of the line.
If you're starting mythfrontend manually, then just open a terminal and type ```
 mythfrontend --verbose your,verbosity,flags
```

[*] mythbackend: edit */etc/default/mythtv-backend* and adjust the *EXTRA_ARGS* variable. You'll likely have to uncomment this line by removing the *#* character at the beginning of the line.
[/list]
[/list]

[CENTER]**Debugging Crashes**[/CENTER]
Sometimes, the frontend or the backend will just exit without giving any useful error messages. That's often caused by bugs in MythTV. Often, you'll find a ["segmentation fault](http://en.wikipedia.org/wiki/Segmentation_Fault) message in the log files or in dmesg. To debug these crashes, a crash report needs to be send to [Launchpad](http://en.wikipedia.org/wiki/Segmentation_Fault) using a tool called "apport".

[list]
[*] First, enable apport.
[list]
[*] edit /etc/default/apport and set enabled=1. Apport is usually disabled on stable Ubuntu releases and enabled by default only on the development series.
[*] run ```
/etc/init.d/apport start
``` in a terminal to initialize apport
[*] it is also a good idea to install the apport-gtk package to give you some nice pop-ups when something crashes. ```
sudo aptitude install apport-gtk
```
[/list]
[*] Now, try to reproduce your crash.
[*] Once your application has crashed, you should get a window telling you that something went wrong. You can file a bug report then. If you opted not to install apport-gtk, you can run ```
apport-cli
``` in a terminal to send a bug report.
[*] Once the bug has been reported, the Mythbuntu developers will look at it and forward it the MythTV developers unless there was a problem when creating a backtrace from your crash report.
[/list]

---

### Post by Michel1 on 2009-12-05
Very easy!!!!! Just admit that mythtv sucks...

---

