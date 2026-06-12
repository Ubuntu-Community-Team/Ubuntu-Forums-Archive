---
title: "Fubar'd my VLC media player"
date: 2009-02-04
forum: Multimedia Software
---

### Post by jaqrah on 2009-02-04
I finally have gotten around to customizing my Ubuntu world.  I downloaded a number of VLC skins for the VLC Media Player.  I got them into their appropriate folders.  I was testing out the feel of the various skins, seeing what I liked and didn't like.  I loaded a skin and when the VLC window popped up I received the following message:

VLC could not open the file "/tmp/vlt8sfcA/img\playlistWindow.png"

I have Clear or Close button from which to choose (not that it matters because neither help in this situation).  After I hit either button, there is a smear of garbled output which should be the media player.  And because it is just a smear I can't go back in change my preferences.

I tried uninstalling...twice, to no avail.  

How do I go about getting VLC Media Player back?  Any and all suggestions would be greatly appreciated.  Thanks

---

### Post by lakersforce on 2009-02-04
Try and delete the .vlc folder in you home directory (if it exists).

(it's a hidden directory, so you have to have hidden files enabled).

---

### Post by redroad55 on 2009-02-04
When you uninstall one of the requirements may be to log out and log back in for change to take effect..Just a thought .. Post back..Best to you

---

### Post by jaqrah on 2009-02-04
Thanks for both of the suggestions.

After I uninstalled, I did a restart. Then I re-installed.  But I noticed it just re-installed the package without actually downloading it from the repository.  It is still lurking somewhere in my system. And the re-install is still a mess.

I will try removing the .vlc folder when I get home this evening.  Yes, it does exist.  It is how I got the vlc player skins installed in the first place.  They have to be physically placed into: /usr/share/vlc/skins2.

If anyone else has some suggestions, I would greatly appreciate it.  Thanks

---

### Post by redroad55 on 2009-02-04
This is the command line to use to debug

> vlc -vv

Post your results here so we can see what is happening ..Best to you

---

### Post by BazookaAce on 2009-02-04
Okay, i'm no expert here, but after you have uinstalled, and you're ready to re-install VLC, try to delete the downloaded package with the command: 

```
sudo apt-get autoremove
```

And you can try with: 

```
sudo apt-get autoclean
```

Again, i don't know if this will work, but it doesn't hurt to try :)

---

### Post by mc4man on 2009-02-04
In a terminal go this and it will be set back to orig. default settings.
```

vlc --reset-config
```

---

### Post by redroad55 on 2009-02-04
That's it Mc4man sometimes I'm taking the long way home ..Thanks

---

### Post by jaqrah on 2009-02-04
mc4man...excellent!

redroad55...thanks for all the help.

Ubuntu community is the best!

jack

---

### Post by itsjustarumour on 2009-02-19
> **mc4man said:**
> In a terminal go this and it will be set back to orig. default settings.
```

vlc --reset-config
```

Worked for me - thanks!

:-)

---

