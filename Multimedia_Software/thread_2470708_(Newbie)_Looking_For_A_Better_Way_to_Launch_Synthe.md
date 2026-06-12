---
title: "(Newbie) Looking For A Better Way to Launch SynthesizerV Studio"
date: 2022-01-08
forum: Multimedia Software
---

### Post by djunna on 2022-01-08
Howdy, I'm running Ubuntu Mate but I'm still pretty new to it. I've been using this software called [synthesizerV]("https://dreamtonics.com/en/"). It has a native linux version and that's been running without issue, but the only way I've been able to get it to run is by manually typing into the terminal 

/home/usr/synthv
 
and then entering: 
[URL="https://forum.synthesizerv.com/t/installing-synthv-on-linux/687"]
 LD_PRELOAD=/usr/lib/libcurl.so.3 ./synthv-studio[/URL]

 It launches without problem but I can't help but feel there's a better way to do this.

Apologies if the answer is super obvious. Thanks for reading.

---

### Post by TheFu on 2022-01-08
/usr/lib/ will be in the LD_LIBRARY_PATH, so I'm confused by the preload stuff. That's new to me and I can't imagine it is actually needed unless the program was poorly made or is using the wrong version of a library already on the system.

If you don't actually install the program, then it won't show up in the menus.  You can manually create a .desktop file which can run a script.  I hope/suspect the paths in the first post are all incorrect, since they don't make sense.  /home/usr/synthv makes no sense.

If you aren't good with getting details correct, then you'll struggle to create a tiny script that can be used in a .desktop file to launch the program.

You can look up the format and best location for a .desktop file that will be found when the menus are rebuilt.  I don't know those off the top of my head and haven't created a .desktop file in a decade or so.  A .desktop file is sorta like the old .pif files from Windows 3.0 days.  It is just text and says what icon to use, the name to display in a menu and which, exact, program to run. The program can be a script.

A script is just a text file that lists commands in order.  You've already done that above, so put those into a file (if you know they are correct), make the file permissions "executable", then you can just run that single command.  I like to put personal scripts in ~/bin/ - that is the same as $HOME/bin/.  I have ~/bin/ in my PATH so it can be found and any programs/scripts inside it can be run from any directory location (or from a menu).

---

### Post by djunna on 2022-01-09
Thank you for your reply! 

Oops. I think I was trying to use "usr" to censor my user profile's name on my desktop, completely forgetting that that's a separate functional folder. [Here]("https://imgur.com/rbWfDNI") is the process I was trying to describe. Thank you for telling me about the .desktop, that sounds like exactly what I need and I'm looking into a guide to create one & looking into adding my ~/bin/ to path (I was doing something earlier that would also find that beneficial). Thanks for your help. :)

---

### Post by TheFu on 2022-01-09
> **djunna said:**
> Thank you for your reply! 

Oops. I think I was trying to use "usr" to censor my user profile's name on my desktop, completely forgetting that that's a separate functional folder. [Here]("https://imgur.com/rbWfDNI") is the process I was trying to describe. Thank you for telling me about the .desktop, that sounds like exactly what I need and I'm looking into a guide to create one & looking into adding my ~/bin/ to path (I was doing something earlier that would also find that beneficial). Thanks for your help. :)

I can't see anything on imgur.com. Sorry.

There are probably 100+ example ".desktop" files on your system now.  Find a short one as an example and do what it does.  It is just a text file.

To look for files on your system you can use the **locate** command or **find**.  Find is hard to use - don't expect to magically use it without some study first.  Locate needs a DB built, which comes in the same package and is pretty bonehead to use.

```
$ locate -i part-of-filename
so
$ locate .desktop 
```
will find all .desktop files that your userid can see.
The DB gets updated, automatically, daily. I don't think it is created just because the package is installed.

The best way to learn 'find' is to look for a top 10 or top 50 'find' examples webpage.  'find' shows what exists on the system now.  locate shows what was on the system when the DB was last updated.  99% of the time, locate is fine, since we most often forget about files that have been around over a day ... perhaps months or years.  Plus the syntax of locate is easier than find by far.  But if you know some specific information beyond part of the name, find can be crazy powerful.  Like If you only want filenames (not any directories) that haven't been modified in the last 90 days that begin with a vowel ... and you want to send the file list into some other program in chunks of 20 files at a time.  That's where 'find' would be better.  Find lets us search by owner, group, permissions, atime, ctime, mtime, name, symlinks, files, directories, inodes, and probably 10 other things.  Very powerful.

---

