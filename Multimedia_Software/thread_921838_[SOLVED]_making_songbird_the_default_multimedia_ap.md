---
title: "[SOLVED] making songbird the default multimedia application"
date: 2008-09-16
forum: Multimedia Software
---

### Post by ericmc783 on 2008-09-16
EDIT: I think I may have accidentally posted this in the wrong categor. Apologies.

My Issue:
I haven't had much luck so far with Linux's choices for Ipod managers. GTKPod lets me edit tags, but gives me an error whenever I try to use the built-in player. Rhythmbox is a wonderful player but it doesn't let you edit tags. Banshee does not recognize my ipod when I connect it. Amarok has never worked right for me (possibly because I'm using Gnome instead of KDE).

So I went ahead and installed one of my favorite Windows apps, songbird ([http://getsongbird.com/download/](http://getsongbird.com/download/)). It does have a linux version, but it was not available for download in Synaptic. I downloaded the Tar archive, and was able to extract it ok, so I now have it installed.

What I would like to do is make songbird my default multimedia application (and thus causing it to load whenever I connect the Ipod). When I go to system | preferences | preferred applications, songbird is not listed as an option. I was wondering if there was a custom command I could put in the command box to make it load.

Thanks for any help you can offer.

---

### Post by mc4man on 2008-09-17
> What I would like to do is make songbird my default multimedia application (and thus causing it to load whenever I connect the Ipod)
That won't be any problem, the only issue is whether you want it to auto connect to the ipod also. That would depend on if the default launch command of songbird is suitable or if there are any available launch parameters that would work.

I don't have songbird installed, if you get a chance describe how you connect to the ipod after opening songbird and if there are any launch parameters listed in songbird --help or man songbird.

The autorun for ipods is controlled in file management -> media -> music player.

We can either add songbird to that list (and have it use a custom launch command, or

Use an existing choice for autorun to run songbird (substitute launch commands or use to point to a script to start songbird properly

---

### Post by mc4man on 2008-09-17
Installed songbird 0.7 from getdeb, very easy to do, the default command works fine. (songbird autoconnects to ipod by default
See here *first* for more complete instr. on the method (copy .desktop

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

Assuming you've glanced at above post and you have a _folder named applications with a  mimeapps.list inside and this line_
> x-content/audio-player=banshee.desktop;rhythmbox.desktop;

You should have that line, if not add as in other post or go to file management -> media and switch default *music player* to banshee, the line should then be created. (the first listed is the current default

Then it's simple (songbird is the easiest I've done
```
cp /usr/share/applications/songbird.desktop ~/.local/share/applications/songbird.desktop

```

Then run 
```
gedit ~/.local/share/applications/mimeapps.list

```

Add this **to end of** x-content/audio-player= line (no spaces ```
songbird; 
```

That's it, go to file management and choose songbird as default music player.

Here' my line for comparison *after* setting songbird as default (**don't copy**
> x-content/audio-player=songbird.desktop;banshee.desktop;banshee-1.desktop;rhythmbox.desktop;


edit: 
As far as system | preferences | preferred applications just add songbird in custom box, don't know what it will change, as noted above ipod's are controlled in system -> preferences -> file management -> media -> music player.  If not available in preferences menu add with edit menus or go home folder -> edit -> preferences

---

### Post by ericmc783 on 2008-09-17
Mc4Man, Your instructions worked perfect! Issue solved!

Im a newbie to linux, so not only did you resolve my issue, you showed me some useful stuff that I didn't know about before. I was unfamiliar with getdeb. When I first installed songbird, I got it from the mozilla website, in the form of a .tar archive. There was no songbird.desktop in my applications folder (maybe because of the way i extracted the tar archive?).

So I remove my installation from the tar file, and downloaded and installed songbird from getdeb, which was very simple. Once I did that, I was able to follow your instructions with ease. I'll be sure to use getdeb more often if I can't get something in Synaptic.

In addition, I did not know about System | Preferences | File Management. I had to add it in the main menu settings. Very useful.

I can see why the Ubuntu community thrives.... because of great  members like you. Thanks again!

---

