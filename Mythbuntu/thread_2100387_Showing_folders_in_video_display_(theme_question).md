---
title: "Showing folders in video display (theme question)"
date: 2013-01-01
forum: Mythbuntu
---

### Post by knowtown on 2013-01-01
I have been running Mythbuntu for years and I love it. About 6 months ago I updated to 0.25 and had to update all of my themes for compatibility reasons. In my older versions I was running a theme called metallurgy and I really liked it's simple interface. That theme is not compatible with 0.25 so I have been going through every theme I can find and the one feature I would really like is to display folders in the video section. This worked great in the older metallurgy theme but I cannot find any theme that does this in version 0.25. Basically, I have some videos that I want to put in separate folders (Music, Sports, Documentaries, etc) and I want that folder to show when I am browsing videos instead of all the items in the folders.

So at /var/lib/mythtv/videos/ I have subfolders /music /sports /TEDtalks /documentaries

In the metallurgy theme I could go to the video section and it would show all my folders at the top, then all the videos in /var/lib/mythtv/videos in sorted order. In all the 0.25 themes, when I go to the video section I see every file in /var/lib/mythtv/videos and all the subfolder files individually. So all the music videos and TEDtalks files show in the video section. This makes the whole list harder to sort through. Is there any theme in 0.25 that will display the folders and then, only if you choose the folder display the files therein? Or am I out of luck?

Thanks!

---

### Post by AlecJ on 2013-01-03
metallurgy was a favourite in our house too, the closest replacement is mythcenterwide, nearly the same just blue. But check out the Theme Chooser in settings, you may have to use Myth Control Centre to install all the themes. Thats option's not in .26 looks like it downloads on demand?
The menu layout is "classic" 
I'm on .26 with fixes now, but i think also in .25 there is a new menu item in the backend setup called Storage Directories, I have used it in the past, to move the recordings to a larger disk and away from the OS disk, but also in there you can (as I just found out) specify the Videos directories as well as lots of other paths.
I have a few folders on various drives, you just list them, but this will not show the path's,
I think if you don't use this and then in Videos settings/ General settings list the folder paths separated with colons
 /meda/disk1/folder1:/media/disk2/folder2:  etc
or just the folder containing the sub folders
This should display the paths but only in the Video List menu option 
Worth a play

---

### Post by nickrout on 2013-01-03
1. You should be using storage groups.

2. I beleive this is not a theme issue but a setup issue. In the video screen press M (menu) and play with the settings.

---

### Post by knowtown on 2013-02-26
Thank you everyone for your helpful comments. It was indeed a setting in the theme. While in the gallery view, I hit the m for menu and played with various settings as suggested and found that m > filter by... > folder
created the layout that I was looking for. This basically lists all my TV shows at the top in separate folders for each and then after all the folders it list the movies individually, which is what I was looking for. The added benefit, is this option also picked up my custom folder images when no other option did.

So thanks everyone for pointing me in the correct direction. I appreciate it.

---

