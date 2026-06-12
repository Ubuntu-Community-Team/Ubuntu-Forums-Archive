---
title: "Launcher shortcut to open XnView Favorites"
date: 2020-01-27
forum: MINT
---

### Post by contrast9390 on 2020-01-27
Hello, Ubuntu Community. I am running Linux Mint which is for all means Ubuntu 18.04 LTS base 

XnView was installed as a 64 bit .deb directly from the developers website as it is not in Bionic's repos
[https://www.xnview.com/en/xnviewmp/#downloads](https://www.xnview.com/en/xnviewmp/#downloads)

I am not complaining about a feature that is not in XnView but rather trying to do something unorthodox such as making a command line path "xnview --(WHATEVER IS NEEDED)"
to make a shortcut to my bookmarked folders that I can place as desktop icons for easy access. Finding a way to get specific favorited folders to be opened from desktop icons is the goal.

[https://media.discordapp.net/attachments/646833154992111616/671518004596441117/xnview_favorites.png](https://media.discordapp.net/attachments/646833154992111616/671518004596441117/xnview_favorites.png)


Thanks anyone in advance who takes time to troubleshoot my problem.

---

### Post by wildmanne39 on 2020-01-27
Hello and welcome to the forum.

*Thread moved to **MINT a more appropriate sub-forum**.*

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by contrast9390 on 2020-01-27
It's about software. It could be on Arch, Fedora, Gentoo, or whatever distro (the same hypothetical answer would apply to all of them) I asked in the multimedia software section for help for that reason.

---

### Post by wildmanne39 on 2020-01-27
I understand that but since it is running on Mint it belongs in the Mint forum, most of the users that help here use the activity page to view threads so your thread is just as likely to get answered here as in the Multimedia forum.

This is a link to the activity page so you can see for yourself.

[https://ubuntuforums.org/activity.php](https://ubuntuforums.org/activity.php)

---

### Post by contrast9390 on 2020-01-28
Problem solved by myself!

Open terminal/bash

_For directories without spaces_
xnview /home/**USERNAME**/Pictures/[B]FOLDER
[/B]
_For directories with spaces_xnview /home/**USERNAME**/Pictures/[B]FOLDER\ OF\ INTEREST

[/B]-note the "\" key represents spaces in bash
This applies to all distros running xnview not just Mint or Ubuntu**, **you can make desktop icons, add it too your start menu or add keyboard shortcuts for easy access to picture galleries. 
Make habit of not using spaces in folder names to make this easier.


Happy Linuxing.

---

