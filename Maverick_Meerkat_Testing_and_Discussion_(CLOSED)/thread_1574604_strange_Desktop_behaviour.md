---
title: "strange Desktop behaviour"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-09-14
I have a problem: The files and folders which appear on my desktop are the contents of my home folder (e.g. /home/ubername) rather than the contents of Desktop (e.g. /home/ubername/Desktop)

This is a small step forward from my previous situation where the files / folders were the contents of /home/ubername/downloads/Desktop. I have no idea how I ended up with that. I guessed I might have dragged-and-dropped my original Desktop folder there by mistake and ubuntu cleverly realised that. However I still had a /home/ubername/Desktop folder.

When I noticed it, I moved the contents of the /home/ubername/downloads/Desktop folder to /home/ubername/Desktop. This resulted in nothing on the desktop (bar drive icons). When I logged out and back in I got the situation described at the top. I have looked in gconf-editor for any clues, but cannot find what tells ubuntu which folder's contents to display on the desktop. 

Any clues - I guess this may welll not be a Maverick specific issue, but would welcome any help?

---

### Post by 23meg on 2010-09-14
Launch gconf-editor and check if you've accidentally enabled /apps/nautilus/preferences/desktop_is_home_dir.

---

### Post by ubername on 2010-09-14
> **23meg said:**
> Launch gconf-editor and check if you've accidentally enabled /apps/nautilus/preferences/desktop_is_home_dir.

Nope.

I've tried setting it to true, then unsetting it etc. to no avail.

Anyone know what

/apps/nautilus/desktop-metadata/directory/nautilus-window-scroll-position

does?

That had a reference to ~/downloads/Desktop in it.

---

### Post by ubername on 2010-09-14
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/638463](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/638463)

Further experimentation has crashed Nautilus - I think I will re-install.

---

### Post by QwUo173Hy on 2010-09-14
> **ubername said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/638463](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/638463)

Further experimentation has crashed Nautilus - I think I will re-install.
I don't have permission to access that web-page - odd, as I'm logged in to launchpad. If you re-install, you might not be able to help them troubleshoot the problem. Entirely up to you of course.

---

### Post by ranch hand on 2010-09-15
The bug was not marked public.  This needs corrected by the bug filer.

---

### Post by teh603 on 2010-09-15
I don't know if this is the intended behavior for Gnome, but in Kubuntu Maverick the default folder for the desktop view widget is set for the Home Folder. So it could be "working as intended"?

---

### Post by ubername on 2010-09-15
Bug now public (FWIW)

I am sure this is not intended behaviour - the forums would be awash with comments!

Good call re helping to debug - I've decided not to reinstall.

---

### Post by ubername on 2010-09-19
Bit more info:

If I use Thunar to browse to my home directory, when I double click on Desktop in the left hand panel it says 'The specified directory is not valid' and the title bar of Thunar (which normally shows the name of the directory) changes to 'artup'!
However if I double click on the directory 'Desktop' in the right hand panel, showing the contents of the home directory,it works.

edit - I have searched in my home folder for anything with '/artup' in it (via places>Search for files...)and searched in gconf editor for any key with a name or value including 'artup'. Results were 12 keys with 'startup' in the name, but nothing with '/artup'

---

### Post by liorwohl on 2010-09-20
why not try to remove the settings? (back to defaults)
just open Nautilus -> view -> show hidden files 
then delete any hidden folder you want, there is no risk- if for example you remove .mozilla, your firefox settings will be back to defaults.
so you can remove all .gconf or you can go to .gconf/apps/ and delete just the nautilus folder, but i'm not sure if your problem is with nautilus.

---

### Post by QwUo173Hy on 2010-09-20
ubername, I've just had a look at your bug report. I think the steps are easy to reproduce - just enable desktop-as-home and watch the madness unfold. So maybe there's no need for you to keep your bewildered setup :)

Personally, I would try a fresh install if you don't find any similar reports (assuming you tried Gnomes Bugzilla?)

---

### Post by ubername on 2010-10-05
All fixed after the drastic steps or renaming ~/.config and ~/.nautilus, then logout / login.

Bizarely Nautilus remembered many of my preferences which I thought would have gone. I had to reset options / copy files from renamed .config for other apps, as I expected.

---

