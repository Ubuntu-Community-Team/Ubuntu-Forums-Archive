---
title: "Where is an ideal place for keeping software icon ?"
date: 2022-01-07
forum: Multimedia Software
---

### Post by satimis on 2022-01-07
Hi all,

I have Shotcut installed and added to the favourites on Menu bar.  Also I have its icon download on Internet.  

Please advise where is an ideal place for keeping the icon?

Thanks in advance

Regards

---

### Post by schragge on 2022-01-07
**~/.local/share/pixmaps**

Using **~/.local/share/icons** is much more involved.

---

### Post by satimis on 2022-01-07
> **schragge said:**
> **~/.local/share/pixmaps**

Using **~/.local/share/icons** is much more involved.
Thanks for your advice.

icons folder is not existing.  Shall I create it?

Besides where is an ideal place storing the software?  I'm now keeping Shortcut on Video folder

Regards

---

### Post by schragge on 2022-01-07
> icons folder is not existing.  Shall I create it?
NO. As I said, use **~/.local/share/pixmaps**.
> Besides where is an ideal place storing the software?
I usually unpack binary tarballs under **/opt**. AppImages go to **~/Applications**

BTW, Ubuntu Backports Testing Team currently has a **shotcut-21.01.29** package in [ppa:ubuntu-backports-testers/ppa](https://launchpad.net/~ubuntu-backports-testers/+archive/ubuntu/ppa). If I were you, I'd give it a try.

---

### Post by &amp;KyT$0P# on 2022-01-07
> **schragge said:**
> Using **~/.local/share/icons** is much more involved.

How so?

---

### Post by satimis on 2022-01-07
> **schragge said:**
> NO. As I said, use **~/.local/share/pixmaps**.
Whether you suggested installing pixmaps and use the icons on pixmaps store?  Not download on Internet?

> 
I usually unpack binary tarballs under **/opt**. AppImages go to **~/Applications**
I see, on;
/home/satimis/.local/share/applications/

now 
shotcut.desktop
avidemux.desktop
are there.

avidemux_2.8.0.appImage
shotcut-linux-x86_64-211224.AppImage
on /Videos

> 
BTW, Ubuntu Backports Testing Team currently has a **shotcut-21.01.29** package in [ppa:ubuntu-backports-testers/ppa](https://launchpad.net/~ubuntu-backports-testers/+archive/ubuntu/ppa). If I were you, I'd give it a try.
I have a Shotcut installed running flatpak on a Linuxmint 11.2 VM of VirtualBox.  Maybe I'll try there.

Regards

---

### Post by &amp;KyT$0P# on 2022-01-07
> **satimis said:**
> Whether you suggested installing pixmaps and use the icons on pixmaps store?  Not download on Internet?

If the icon theme you're using does not have an icon for this app, which I assume is the reason you want to do this, you can download the icon from the Internet and place it in [FONT=Courier New]~/.local/share/icons[/FONT] and you should be able to reference it from the .desktop file.  Look at [FONT=Courier New]Icon=[/FONT] line in the .desktop file - for example if the .desktop file says
```
Icon=shotcut
```
then you must place your downloaded icon as [FONT=Courier New]~/.local/share/icons/shotcut.png[/FONT] (assuming you downloaded a png).  And yes you can just create the icons directory if it doesn't exist.

This works for me across every desktop environment I've tried.  But, again, only for icons that don't already exist in the active icon theme.  If I assumed wrong and your active icon theme does have an icon for this app, this method won't work, and the process to override the existing icon *does* get more involved.

If your desktop environment is GNOME you may need to log out & back in to see the change to the icon.

---

### Post by schragge on 2022-01-07
> **halogen2 said:**
> How so?

> **halogen2 said:**
> then you must place your downloaded icon as [FONT=Courier New]~/.local/share/icons/shotcut.png[/FONT] (assuming you downloaded a png).
Yes, that's the fallback path for when the lookup algorithm didn't find a suitable icon on previous steps, but see [Icon Lookup]("https://specifications.freedesktop.org/icon-theme-spec/latest/ar01s05.html") in the *Icon Theme Specification* to understand what I mean. To override an icon from an icon theme, it'll have to be located at the correct place, i.e. something like
```
~/.local/share/icons/<theme_name>/<size>/apps/shotcut.png
```

---

### Post by &amp;KyT$0P# on 2022-01-07
Thanks schragge for the clarification.  But [FONT=Courier New]~/.local/share/pixmaps[/FONT] doesn't seem to work for me (in Xfce), either to override an icon or place a new one?

Looking at the icon theme spec you linked, I don't see that path listed: from [https://specifications.freedesktop.org/icon-theme-spec/latest/ar01s03.html]("https://specifications.freedesktop.org/icon-theme-spec/latest/ar01s03.html") -
> By default, apps should look in $HOME/.icons (for backwards compatibility), in $XDG_DATA_DIRS/icons and in /usr/share/pixmaps (in that order). Applications may further add their own icon directories to this list, and users may extend or change the list (in application/desktop specific ways).

Is [FONT=Courier New]~/.local/share/pixmaps[/FONT] desktop environment specific?  or is there special configuration needed to make it work?

---

### Post by satimis on 2022-01-08
Hi all,

I run shotcut-linux-x86_64-211224.AppImage to start Shotcut without installing it on Ubuntu20.04 OS

I download an icon for it on Internet and store the icon on /home/satimis/Picture/

Then I edit shotcut.desktop as follow;

$ cat /home/satimis/.local/share/applications/shotcut.desktop```
 
[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Videos/shotcut-linux-x86_64-211224.AppImage
Icon=/home/satimis/Pictures/shotcut.png

```

It works for me seamlessly.  I hesitate to know whether /Picture is an ideal place for keeping shotcut.png file therefore I started this posting.

Regards

---

### Post by ajgreeny on 2022-01-08
As long as you know where the icon image is sitting and can find it, and it works for what you want it, I do not see why it matters too much where the image sits.

For many years I have used ~/Pictures as the destination for all my photographs but also created a ~/Pics folder in which I have several subfolders including one named Icons, another called Screenshots and another called Wallpapers.

It is simply my way of organising image files which I find easier than any other.

---

### Post by satimis on 2022-01-08
> **ajgreeny said:**
> As long as you know where the icon image is sitting and can find it, and it works for what you want it, I do not see why it matters too much where the image sits.
- snip - 
I got your point.  Thanks

There is no fixed rule keeping icon of software

Regards

---

