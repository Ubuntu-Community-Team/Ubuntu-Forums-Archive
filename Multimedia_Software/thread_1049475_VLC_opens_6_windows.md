---
title: "VLC opens 6 windows"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Wobblybob on 2009-01-24
Hi All, I'm using VLC 0.9.4 installed on a Gnome desktop in Intrepid Ubuntu. When I open any video file it gets opened 6 times each window playing at the same time. One window is the normal VLC window headed VLC media player the rest are headed VLC XVideo output. I installed using synaptic and have checked all the settings including "open only one instance" and have even resorted to re installing this no luck, can anyone help?

Martin

---

### Post by mc4man on 2009-01-24
While i can think of a way 2 or 3 may pop up, 6 seems unlikely. Anyway why don't you delete vlc's config files totally and try again. They'll be found in home folder (view -> show hidden files) -> .config
Delete the complete vlc folder inside.

Maybe try opening vlc from the terminal
vlc -vv


If still an issue copy and paste this, if no file is found, no problem, it doesn't exist by default

```
cat ~/.local/share/applications/mimeapps.list

```

---

### Post by Wobblybob on 2009-01-24
Hi mc4man

Thanks for your reply, the out put is;

```
martin@laptop:~$ cat ~/.local/share/applications/mimeapps.list

[Added Associations]
application/x-shellscript=gedit.desktop;ooo-writer.desktop;geany.desktop;
application/octet-stream=gedit.desktop;
```

I deleted the VLC Dir in .config as you suggested but this made not difference, i still have 6 windows palying my wmv files but plays mp4's correctly!

---

### Post by Wobblybob on 2009-01-24
Hi mc4man

Thanks for your reply, the out put is;

```
martin@laptop:~$ cat ~/.local/share/applications/mimeapps.list

[Added Associations]
application/x-shellscript=gedit.desktop;ooo-writer.desktop;geany.desktop;
application/octet-stream=gedit.desktop;
```

I deleted the VLC Dir in .config as you suggested but this made not difference, i still have 6 windows playing my wmv files but plays mp4's correctly!

attached resulting output from using vlc -vv option

---

### Post by mc4man on 2009-01-24
It looks like vlc is finding 6 active video streams in your wmv and so it opens them all in separate windows.
Would have to search out and see what that's about. Is there any apparent way to just pick one?
I would think (s)mplayer may be a better alternative

[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php) (ck. under 'new' listing

Edit:
This is from a windows user, same idea

[http://forum.videolan.org/viewtopic.php?f=14&t=54517](http://forum.videolan.org/viewtopic.php?f=14&t=54517)

---

### Post by Wobblybob on 2009-01-24
> **mc4man said:**
> It looks like vlc is finding 6 active video streams in your wmv and so it opens them all in separate windows.
Would have to search out and see what that's about. Is there any apparent way to just pick one?
I would think (s)mplayer may be a better alternative

[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php) (ck. under 'new' listing

Edit:
This is from a windows user, same idea

[http://forum.videolan.org/viewtopic.php?f=14&t=54517](http://forum.videolan.org/viewtopic.php?f=14&t=54517)

no way to just pick 1, the wmv's play ok in mplayer and gxine, but I prefer vlc, will have to try them out on my PC and see if it's just something on this laptop that's causing the problem.

---

