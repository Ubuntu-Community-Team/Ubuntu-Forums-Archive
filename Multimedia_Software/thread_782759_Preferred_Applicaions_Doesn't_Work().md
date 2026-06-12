---
title: "Preferred Applicaions Doesn't Work(?)"
date: 2008-05-05
forum: Multimedia Software
---

### Post by movedx on 2008-05-05
Hello,

I'm trying to configure Ubuntu Hardy to use VLC has my default DVD player. Here is the process I'm following in an attempt to get this working:

1. Going to the relevant tool for the job:

[IMG]http://mcrilly.co.uk/dump/posts/ubuntu-forums/defaut-media-player/menu-selected-cropped.jpg[/IMG]

2. Editing the relevant option(s):

[IMG]http://mcrilly.co.uk/dump/posts/ubuntu-forums/defaut-media-player/preferred-apps.jpg[/IMG]

Now am I getting this wrong here? I don't know. When I insert a DVD it simply opens with Totem as if I'd never changed this option. I've tried this option with and without the '%m', with no change in performance. I've also tried checking the 'Run in Terminal' option.

Suggestions?

---

### Post by movedx on 2008-05-05
It appears it has something to do with nautilus, not Ubuntu/GNOME. *investigates*

---

### Post by movedx on 2008-05-05
I couldn't find a resolution to my problem. Instead, I changed the way in which nautilus deals with an inserted DVD by starting nautilus and going to Edit -> Preferences -> [Media Tab]:

[IMG]http://mcrilly.co.uk/dump/posts/ubuntu-forums/defaut-media-player/fm-preferences.jpg[/IMG]

And changing 'DVD Video' to 'Do Nothing'. When I insert a DVD I merely start VLC my self and do as I please at that stage. I don't always insert a DVD to watch it ;)

I hope this helps someone else out there in some manner.

---

### Post by erginemr on 2008-05-06
Here is a similar thread:
[http://ubuntuforums.org/showthread.php?t=748742](http://ubuntuforums.org/showthread.php?t=748742)
and a promising solution candidate from there:
[http://ubuntuforums.org/showpost.php?p=4674199&postcount=10](http://ubuntuforums.org/showpost.php?p=4674199&postcount=10)

If it doesn't work for you, you may go messy with some other techniques presented in:
[http://ubuntuforums.org/showthread.php?t=733559](http://ubuntuforums.org/showthread.php?t=733559)

---

### Post by Awalton on 2008-05-06
Don't ask me why this is; I didn't write it, I don't agree with it, etc. You'll need to pester David Zeuthen as to why he made this decision ([http://www.mail-archive.com/nautilus-list@gnome.org/msg04224.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg04224.html)).

Anyways, the magic is in setting an association for the X-Content mime-type of the media:
in my $XDG_DATA_HOME/applications/mimeapps.list:
[Added Associations]
x-content/video-dvd=vlc.desktop

Tada, VLC is now associated, and will appear in the menu (so you can select it in the dialog above). The upstream solution would be for applications, such as VLC and Totem-Xine, to add "x-content/video-dvd" to their "MimeType=" key in their .desktop files. The same will work for cds, bluray disks, etc.

---

### Post by mgmiller on 2008-06-08
Awalton says:
> Anyways, the magic is in setting an association for the X-Content mime-type of the media:
in my $XDG_DATA_HOME/applications/mimeapps.list:
[Added Associations]
x-content/video-dvd=vlc.desktop

Where in my system is "$XDG_DATA_HOME/applications/mimeapps.list" located?  

I can't find it anywhere.

---

### Post by p_quarles on 2008-06-09
Moved to Multimedia & Video.

---

### Post by mc4man on 2008-06-09
> Where in my system is "$XDG_DATA_HOME/applications/mimeapps.list" located? 
home/username/.local/share/applications

edit: that method can be a little tricky especially with anything other than vlc
For just vlc and dvds see here
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)
After that you can go there (mimeapps.list) if you want, append the line vlc is on to add additional players - you need to find right launch command for them  (any add. players) to work properly in autoplay (if there is one)

---

### Post by mgmiller on 2008-06-09
Got it, Thank you.

---

