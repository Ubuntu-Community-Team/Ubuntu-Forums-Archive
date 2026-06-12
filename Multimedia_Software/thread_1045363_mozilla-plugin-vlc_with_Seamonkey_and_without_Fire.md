---
title: "mozilla-plugin-vlc with Seamonkey and without Firefox...is it possible?"
date: 2009-01-20
forum: Multimedia Software
---

### Post by darthchaosofrspw on 2009-01-20
I want to remove Firefox and start using Seamonkey, but I want to keep mozilla-plugin-vlc so I can play streaming multimedia content in Seamonkey. However, when Is this possible? If so, how?


EDIT: Never mind. I meant to ask if there was a way that I could keep the sun-java6-plugin by installing Seamonkey and removing Firefox. When I go to remove Firefox in Xubuntu 8.04.1, it tells me that sub-java6-plugin will be removed as well.

---

### Post by kansasnoob on 2009-01-20
Why remove Firefox?

I'll try to explain a bit. I did some fairly extensive testing for Nanotube at Ubuntuzilla beginning with post #66 here:

[http://ubuntuforums.org/showthread.php?t=467724&page=7](http://ubuntuforums.org/showthread.php?t=467724&page=7)

Now, from the Ubuntuzilla install page:

> do not remove the repositories version of Firefox, as doing so will break a lot of Gnome packages that depend on the Gecko rendering engine.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Now, I'll grant you that Xubuntu is a different animal, but I'd think the same applies.

BTW the Ubuntuzilla script works for installing Seamonkey also!

Just download Ubuntuzilla 4.6.1 to your desktop then double click the Ubuntuzilla icon and Ubuntuzilla will install to the repos.

Then be sure Firefox is closed (so you might want to copy these commands to Open Office or Abiword) and run:

```
ubuntuzilla.py -a install -p seamonkey
```

You'll be asked a few questions and that's it.

I must admit that I did all of my testing in Ubuntu - none in Xubuntu!

---

### Post by kansasnoob on 2009-01-20
Just out of curiousity I booted into Ubuntu 8.10 which is running the Mozilla build of Firefox thanks to Ubuntuzilla and chose to install Seamonkey:

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Seamonkey on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 1.1.14. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Old Seamonkey preferences not found. Nothing to back up. Proceeding with installation.


Downloading Seamonkey archive from the Mozilla site

--2009-01-20 12:14:58--  [ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/seamonkey-1.1.14.en-US.linux-i686.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/seamonkey-1.1.14.en-US.linux-i686.tar.gz)
           => `seamonkey-1.1.14.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 128.61.111.9, 64.50.238.52, 64.50.236.214, ...
Connecting to releases.mozilla.org|128.61.111.9|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.14 ... done.
==> SIZE seamonkey-1.1.14.en-US.linux-i686.tar.gz ... 14819360
==> PASV ... done.    ==> RETR seamonkey-1.1.14.en-US.linux-i686.tar.gz ... done.
Length: 14819360 (14M)

100%[======================================>] 14,819,360   168K/s   in 83s     

2009-01-20 12:16:21 (175 KB/s) - `seamonkey-1.1.14.en-US.linux-i686.tar.gz' saved [14819360]


Downloading Seamonkey MD5 sums from the Mozilla site


Verifying Seamonkey MD5 sum

./seamonkey-1.1.14.en-US.linux-i686.tar.gz: OK
[sudo] password for lance: 
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 1.1.14 has been installed successfully.

If you are looking to use Seamonkey in other languages, head over to [http://www.mozilla.org/projects/seamonkey/releases/#l10n](http://www.mozilla.org/projects/seamonkey/releases/#l10n) and download the installable language pack of your choice.

Would you like to set up automatic update checking for the official Mozilla build of Seamonkey (recommended)? This feature will regularly check for updates to Seamonkey, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 

I looked under Internet and there it was so I dragged it to my panel:

[ATTACH]100517[/ATTACH]

So it looks like that works;)

---

### Post by darthchaosofrspw on 2009-01-20
> **kansasnoob said:**
> Why remove Firefox?

Well to me, Seamonkey seems to run faster than Firefox 3. Of course YMMV.

---

