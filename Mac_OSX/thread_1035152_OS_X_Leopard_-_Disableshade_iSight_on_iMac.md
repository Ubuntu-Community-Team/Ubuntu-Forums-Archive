---
title: "OS X Leopard - Disable/shade iSight on iMac?"
date: 2009-01-09
forum: Mac OSX
---

### Post by nightfire117 on 2009-01-09
New iMac, how to disable the iSight? I saw the iSight disabler AppleScript here: [http://techslaves.org/index.php?page=52](http://techslaves.org/index.php?page=52) but you have to restart a process, and it's a script... I'm looking for a binary program that can do the same without admin privileges or anything *special*. Possibly, a program that hogs the webcam (and hogs it up) so it says it's "in use" so *no* other application can get access it? Or one that shades the webcam with an image? So one of these solutions would be great.

I don't write AppleScript or am not really a Mac guy myself, even a Mac fan aside from their awesome appearance, so any help here would be great.

This probably isn't the right place to ask, seeing as it's the Ubuntu forum, but when I need a reliable community for computer-related issues this is definitely the place to go, haha.

~Night

---

### Post by damis648 on 2009-01-09
This should be moved to the Mac OS X forum. I am quite not getting your point... why is this script insufficient?

---

### Post by Joeb454 on 2009-01-09
> **damis648 said:**
> This should be moved to the Mac OS X forum

And so it shall be ;)

---

### Post by nightfire117 on 2009-01-09
> **damis648 said:**
> This should be moved to the Mac OS X forum. I am quite not getting your point... why is this script insufficient?

> **Joeb454 said:**
> And so it shall be ;)

Sorry, guys, I didn't see the Mac forum - I looked for it since I knew of it, but >.<

Trying to run the iSight cam disabler ([http://techslaves.org/index.php?page=52](http://techslaves.org/index.php?page=52)) - since I don't have access to the Mac right now (this is for a friend), would this need admin privileges? Which would be unavailable, of course, which is why I'm asking, and apparently it's bad practice to put the root password in AppleScript anyway (duh - well, not like I know what I'm talking about haha). It says something in the script about restarting the apps, is it automatic:

```
-- Intel Mac iSight Disabler
-- Tested on OS X 10.5
-- Tested on 1st generation MacBook
-- Version 3
--
-- All this does is change permission on the iSight driver files. From normal 'a+r' and 'u+rx' when enabled to 'a-rwx' when disabled.
--
-- cense@techslaves.org

display dialog "Intel Mac iSight Disabler
brought to you by techslaves.org.

Version 3
Support for Leopard

You need to restart applications which use the iSight driver(s) after applying these settings." buttons {"Enable iSight", "Disable iSight"} with icon stop

set userChoice to button returned of result

set iSightDrivers to "/System/Library/QuickTime/QuickTimeUSBVDCDigitizer.component/Contents/MacOS/QuickTimeUSBVDCDigitizer /System/Library/PrivateFrameworks/CoreMediaIOServicesPrivate.framework/Versions/A/Resources/VDC.plugin/Contents/MacOS/VDC"

if userChoice = "Enable iSight" then
    do shell script "/bin/chmod a+r " & iSightDrivers & "; /bin/chmod u+rx " & iSightDrivers with administrator privileges
else if userChoice = "Disable iSight" then
    do shell script "/bin/chmod a-rwx " & iSightDrivers with administrator privileges
end if
```

Thanks... sorry about the wrong forum area ; P

~Night

---

