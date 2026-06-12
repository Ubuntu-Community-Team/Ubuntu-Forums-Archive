---
title: "Fuppes absolutely refuses to launch on boot (Mythbuntu 9.04)"
date: 2009-05-19
forum: Mythbuntu
---

### Post by nexpe on 2009-05-19
Hello, first post here and its going to be a long one =/ I'd greatly appreciate any help you would be able to give on this issue.

I successfully compiled fuppes from source following guides posted here:
[http://ubuntuforums.org/showthread.php?t=1156752](http://ubuntuforums.org/showthread.php?t=1156752)
(google cache) [http://74.125.113.132/search?q=cache:S7GVefQJzy0J:fuppes.ulrich-voelkel.de/forum/viewtopic.php%3Ff%3D2%26t%3D513+fuppes+jaunty&cd=9&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.113.132/search?q=cache:S7GVefQJzy0J:fuppes.ulrich-voelkel.de/forum/viewtopic.php%3Ff%3D2%26t%3D513+fuppes+jaunty&cd=9&hl=en&ct=clnk&gl=us&client=firefox-a)

I've got it setup and its working like a dream, I am now just having quite a bit of trouble getting it to start automatically.

I've tried the following methods to get fuppes to boot:

-After i got fuppes installed I followed this guide to the letter:
[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

I made sure that all the scripts created were executable (the guide already does this but as one of suggestions found helpful to a similar problem, I double checked to make sure I didnt make some stupid mistake.)

[http://ubuntuforums.org/showthread.php?p=7294649](http://ubuntuforums.org/showthread.php?p=7294649)

-According to a suggestion in the above post I created a crontab to execute (for the main user on the system) on reboot (not ideal as noted in the post, but it would not execute anyway.) I first did this manually using cron, adding a @reboot fuppes line to the tab for the main user on the system, to make sure i was doing this right i installed the gnome-schedule package and re-added the crontab (first as main user then as root, dont know if this would make any difference since fuppes doesnt require this when running from the terminal). the cronjob worked great when executed manually in gnome-scheduler.


-I added the command to /etc/rc.local (no other commands were in the file, except for the exit 0 line)

-I added a launcher to ~/.config/autostart to start fuppes in the terminal (and realized that the primary purpose of this method is for gui programs, but I was getting a little frustrated at this point and just wanted the dang thing to start, hehe. I tested that the launcher would start fuppes manually, and it did it just fine, here are the contents of the launcher file:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=fp.desktop
Categories=Application;
Exec=fuppes
Hidden=true
Terminal=true
StartupNotify=false

I have added other programs to start successfully using the ~/.config/autostart/ method, so why fuppes work this way I don't know...

I think it also might be helpful to know how to disable the Mythbuntu splash screen or the location of the last startup log so i can see if it has any errors running the commands.

Thanks in advance for any help you might be able to provide, This has been quite frustrating for me (especially for something so basic).
~Tim

---

### Post by nickrout on 2009-05-19
can you post your crontab line please?

---

### Post by nexpe on 2009-05-20
Absolutely (its got 2 lines cause i tried to run the script created in the first tutorial first)

```
@reboot fuppes # JOB_ID_2
@reboot fuppesd >/dev/null 2>&1 # JOB_ID_1
```

---

### Post by nickrout on 2009-05-20
OK try giving the full path to the programs you want to execute.

Like /usr/local/bin/fuppesd

or whatever.

an init script is really the proper way to do it. I see the script is (according to the tutorial at [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d#Debian_.2F_Ubuntu](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d#Debian_.2F_Ubuntu) ) to start with priority 60. The startup scripts go in numerical order, so level 50 starts before 60 which starts before 70 etc.

SO fuppes may be starting before another script that it depends on, try setting it to 99 and see if it works.

---

### Post by nexpe on 2009-05-20
Setting the priority of the script to 99 did the trick! thanks for your help. =)

---

### Post by nickrout on 2009-05-20
> **nexpe said:**
> Setting the priority of the script to 99 did the trick! thanks for your help. =)

If you look in /etc/rc2.d (I think thats the dir) you may get a clue as to what meeds to start before fuppes for it to work. Something that starts between 60 and 99 I guess :)

Then go to the wiki that had the howto and put a note in about your experiences. Thats what wikis are for!

---

