---
title: "default app for audio CD"
date: 2008-07-25
forum: Multimedia Software
---

### Post by marfea on 2008-07-25
I have a machine that I'm using as a server, with Ubuntu 8.04 installed on it. I have a custom CD-ripping script that I would like to be executed automatically upon insertion of an audio CD.

Ideally, as I am treating this machine as a server, I would like a solution that works in headless mode, so that it does not require a user to be logged on at the console.

I couldn't find a headless solution when I first attacked this problem, when I had Ubuntu 7 installed. So I plumped for configuring the default application for an audio CD to point to my script. This was semi-workable, as it would work without user intervention, so long as I'd logged on to the console each time the machine is rebooted.

However, in Ubuntu 8, the default applications are limited to a list box, so I cannot persuade it to call my script.

Any bright ideas? Ideally I'd like a headless solution, but failing that, I'd like to know how to add my script to the list of options on the default application configuration screen.

Thanks in advance!

Kevin.

---

### Post by logos34 on 2008-07-25
I'd look into ABCDE ripper (cli app).   Or maybe grip

---

### Post by mc4man on 2008-07-25
> I'd like to know how to add my script to the list of options on the default application configuration screen.
There are several ways to do that ranging from complicated and possibly risky to quite simple.
For an entry to be added to the drop down requires editing the proper line in defaults.list or adding or adding to a line in mimeapps.list. (has to be done very carefully).  As far as the .lists that would require a corresponding .desktop in /usr/share/applications. So I quess you could create an 'app' (your script), create a .desktop for it, make the exec= your script or a link in /usr/bin targeting your script, edit defaults.list, ect.,ect.

What would be far easier is to 'hijack' an existing choice. By default rhymthbox is there, installing banshee and or banshee-1 will add them to the list. Pick _one you don't want to use_ and use it to run your script. 

The simplest way would be to edit the launch command to run your script.

Ex. with banshee
  i put my script (test) in home dir. then from edit menus, sound & video, I r. click banshee -> properties and change the command to ./test. Then i change the default to banshee, pop in a cd and the script runs.

You could also achieve the same by renaming/deleting banshee in /usr/bin and then creating a link in /usr/bin named banshee targeting your script

edit;  as far as 'headless' I'm basically clueless, but maybe this is something you can work with

edit ;
I tried above 'simple' method with an app, Amarok, works fine, a simple script will now start amarok and play when a cd is inserted. (one set drive only, can't figure how to script to work with two.) To try a Cli I used a dvd insertion, 'hijacking' gxine's launch command to try a script to run vobcopy. Works fine either silently in background or with a slight change in script runs vobcopy in a visible  terminal to view progress.

Thanks for posting, at least now I finally can set amarok as default cd player in a manner that actually works properly

Edit ; Ot to op but just noticed holding shift down when inserting media pulls up a box of all your choices for that media, ie. run the script, run a real player, run another script if in place ect.

---

### Post by marfea on 2008-07-28
Thanks for the tip on the .list and .desktop files- I've edited these by hand and it works well. Now I just need to find a headless solution...

---

