---
title: "Changing default path for 'pictures' and 'music'."
date: 2008-10-22
forum: Multimedia Software
---

### Post by dlenoxx on 2008-10-22
Evening,

   I've been fooling with ubuntu for awhile now and I gotta say I love it- so I put it on my laptop (triple booting with XP, Vista, and now Ubuntu). But I was wondering if there was a way to change the default path that ubuntu uses for pictures and music to the WinXP drive's pictures and music instead of it's own.

Thanks for the help,

D

---

### Post by steviefordi on 2008-10-22
There is probably a more elegant way of doing this, but as a noob myself I can only advise on what I know.

Your default folder for pictures and music are probably /home/*username*/pictures and /home/*username*/music. By default, bookmarks are given to these locations in the "places" menu on the gnome desktop. These bookmarks then appear as shortcuts on the left of a FILE >> OPEN dialogue (ie. the screen that appears in any most applications when you choose 'file' then 'open' from the main menu.)

From the 'Places' menu on the desktop you can add a bookmark and point it at the windows "My Music" and/or "My Pictures" folders. You can give the bookmark a name other than "My Music" if you wish.

If you don't need shortcuts to the ubuntu folders, you can delete those bookmarks to keep things tidy.

Another, possibly more elegant way would be to take advantage of a really cool Linux feature. Instead of /home/*username*/pictures being a directory, you could change it to be a symbolic link to your windows pictures directory. I'm not sure how to do that though.

Hope this helps.

---

### Post by dlenoxx on 2008-10-22
Thanks for the tip, but I had thought of that already- It created shortcuts, which is functional, but I'm aiming for that perfect 10/10 score here.

When you add the short cuts into the places folder it doubles up (My Pictures (XP)/Pictures (Ubuntu)) on links within the places folder. I'm just looking for a way to edit the link that pictures and music point to.

I thought it would be an easy task, took me three seconds in Vista, but not so much in Ubuntu-

---

### Post by steviefordi on 2008-10-22
Like I said, you can delete the shortcuts that are there by default, saving you the mess of 'doubling up'. You can also rename your shortcuts to be called 'Pictures' instead of 'My Pictures' without actually renaming the folders.

I really think (correct me if I'm wrong) that a more experienced Linux user will tell you to remove the directory /home/username/pictures and replace it with a **symbolic link**
to "/media/hda1/Documents & settings/My Documents/My Pictures" or whatever the path is. In effect making the location '/home/username/pictures' in your Linux file system BE your windows "My pictures" folder.

Doing it that way, any time you save or open data in the ubuntu 'pictures' directory, you will see the changes in your windows 'my pictures' folder. Although in the file system the data will appear in two locations, it's actually only on disc once.

have a look here [http://kb.iupui.edu/data/abbe.html](http://kb.iupui.edu/data/abbe.html) some info on how to create a symbolic link.

Cheers
S

---

### Post by dlenoxx on 2008-10-23
Thanks for the help- That will work. I had to set the drives to automount on load, but now my shortcuts will always work from the get-go.

---

### Post by tiga2001 on 2009-07-06
Although this is an old post, I thought some people might still stumble upon it on Google.
The text file that stores the default path for 'pictures', 'music', and other such directories are at ~/.config/user-dirs.dirs
Since by default, files that start with "." are hidden, the easiest way to access it is to open a Terminal, then type
```
nano ~/.config/user-dirs.dirs
```

---

