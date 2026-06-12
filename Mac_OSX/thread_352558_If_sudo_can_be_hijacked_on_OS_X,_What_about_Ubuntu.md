---
title: "If sudo can be hijacked on OS X, What about Ubuntu?"
date: 2007-02-03
forum: Mac OSX
---

### Post by AlphaMack on 2007-02-03
A sample exercise in getting your sudo hijacked via ~/.bash_profile and /Users/Shared is documented here (although the code has been cleaned up):

[http://rixstep.com/2/20070201,00.shtml](http://rixstep.com/2/20070201,00.shtml)

I tried this on a fully patched 10.4.8 system (build 8L127) and was able to get a fake sudo embedded in /Users/Shared and my ~/.bash_profile altered to include the malevolent $PATH.

My method of poisoning my system involved saving the script as an .app, setting the executable bits (chmod a+x), executing it from the Terminal (since the Finder tried to launch Classic), and opened a new terminal window with the now poisoned path to sudo.

To demonstrate that sudo was indeed poisoned, I tried to run something like "sudo ls."  I was prompted for my password, which was rejected (maybe a typo? hmmm) and was asked to enter it again.  Game over.  The script harvested the password and saved it to /Users/Shared/.keylog while at the same time destroying the fake sudo, leaving only the altered ~/.bash_profile behind along with the .keylog.

This is very dangerous, especially if this script can be wrapped inside Cocoa apps.

Knowing that /Users/Shared is wide-open, the question is:  Can this be done in Ubuntu, or any Linux distro, or any UNIX system?  If so, how can one best protect their box from such interlopers (besides the advice given in the article re: full paths)?

Note:

The sample script provided by Rixstep assumes the following:

- The default setup has not been changed
- You're running as an admin (by default in OS X)
- Your default shell for Terminal.app is /bin/bash
- /Users/Shared is world-writeable

---

### Post by PriceChild on 2007-02-03
Doesn't =>Edgy use dash not bash?

"/Users/Shared" ?

You've got to remember that almost every linux system is unique with its own little quirks... something that can't be said for proprietory systems... what works on one machine has no guarantees that it'll work for another.

---

### Post by AlphaMack on 2007-02-03
Just made it work in Dapper 6.06-1 by using /var/lock as a hideout.  I had to modify the script to accommodate the new path and logout/in.

My sudo was poisoned easily by exploiting ~/.bash_profile.

Not good. :?

Edit:  I know of one other person who has also made this work in Dapper using the same target directory.

/tmp and /var/tmp are more directories to watch for interlopers.

---

### Post by aysiu on 2007-02-04
Can you give a real-world scenario by which this exploit can be exploited (for either Ubuntu or OS X)?

---

### Post by AlphaMack on 2007-02-04
For starters...

- Downloading a cocoa app with this wrapped in an Applescript inside

- Classic social engineering - tricking users into thinking that this code is a JPEG, an app, or whatever the black hat wants it to be (think Oompa-Loompa from last year about this time)

Of course, there are more scenarios but these should still set off alarm bells.

Granted, Ubuntu does have its accessible directories but OS X has many more hiding places.  Since this is the OS X forum, I want to keep this focused on OS X.  The take home message for right now while this is still being looked into (good luck getting Apple to act and "take security seriously") is to ensure the following:

- DON'T run as an admin for day-to-day tasks.  While this isn't a cure-all, it will surely prevent interlopers from sneaking themselves into areas that admins have write access to (e.g. /Library).

- DON'T blindly furnish your credentials when prompted.  Know why something is asking for your admin password.

- CHECK your ~/.bash_profile.

- Use the full path to sudo whenever you want to perform admin tasks from the command line.

- LOCK DOWN directories such as /Library/InputManagers and /Library/StartupItems.  Check your /tmp.  Don't allow third party garbage to place things in there (e.g. APE).

---

### Post by 3rdalbum on 2007-02-04
The exact same issue was raised on the Ubuntu forums a little while ago, and posted to the Bash website's forum. The Bash developers have no desire to fix it, so it's unsurprising that Apple hasn't fixed it either (or rather, Apple probably hasn't realised it).

---

### Post by AlphaMack on 2007-02-04
[http://www.ubuntuforums.org/showthread.php?t=277940](http://www.ubuntuforums.org/showthread.php?t=277940)

---

