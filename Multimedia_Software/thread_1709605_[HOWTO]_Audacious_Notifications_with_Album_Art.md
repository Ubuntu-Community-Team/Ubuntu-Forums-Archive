---
title: "[HOWTO] Audacious Notifications with Album Art"
date: 2011-03-18
forum: Multimedia Software
---

### Post by AndyBoy_LV on 2011-03-18
Hi!

I am not sure if this is going to be useful to anyone, but anyway, i will write a tutorial for it.

I know that Audacious has its own Notification Plugin, but i don`t really like it, especially when comparing to Ubuntu`s Notify-OSD bubble. Most of all, i like that you can also send notifications with Album Art using Notify-OSD. 


I coded a small Python script for it (See attachements). It does not download Album Art from the internet (although i might implement this later if i get some positive responses), but it searches for it locally. This script looks for cover art in .thumbnails folder, in music folder where the currently playing song is saved and finally checks ID3 tags. If it fails to find anything, it sends notification with a default Audacious Icon, provided by your Icon Theme.


I have not tested this in KDE.


Installation Instructions:

1. For this script to work, you must have audacious-plugins, python-mutagen and libnotify-bin installed
1.1 You may also enable audio file thumbnail generation in gconf-editor
2. Download AudaciousNotifier.py. Remember that it has to be saved in a directory, where user has reading and writing permissions.
3. In Audacious, go to File-->Preferences-->Plugins-->General and enable Song Change plugin.
4. Click on this plugin`s preferences and in the "Command to run when Audacious starts a new song" field write this command:
```
python /path/to/your/directory/AudaciousNotifier.py "%f" "%n"
```
4.1. You may put this command in the "Command to run when title changes for a song (i.e. network streams titles)":
```
notify-send -i audacious "Audacious" "%n"
```
Click OK.


Because of a Notify-OSD bug it does not allow to clear previous notifications or set a custom timeout, so i had to put an 11-seconds timeout between notifications, otherwise they would stack up under each other if user changes songs too fast :)

Any feedback is appreciated.

---

### Post by gusio on 2012-04-11
using it right now and it was just what i needed. thanks !!!

---

