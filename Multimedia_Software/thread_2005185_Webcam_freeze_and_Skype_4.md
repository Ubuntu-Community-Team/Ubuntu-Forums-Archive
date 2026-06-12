---
title: "Webcam freeze and Skype 4"
date: 2012-06-17
forum: Multimedia Software
---

### Post by grenier on 2012-06-17
Hi all.
To make things short :
- My webcam works perfectly with cheese or google+
- If I use the command ```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```, the webcam also works with skype when I test it, but within 2 seconds of a real call, it freezes (there's no problem with sound, though).
- All of this is with the beta, I have yet to update to skype4.
Unfortunately, there are a couple of persons I need skype for.

So the question is, has anybody with the same problem seen improvement when switching to skype 4?
I'm tempted to give it a try, but on the off-chance it breaks everything down, I'd like to have at least one person tell me it was worth it.

---

### Post by Paddy Landau on 2012-06-19
Some people have found Skype 4 works better (I have), while others have found the opposite.

Nothing stops you from trying. To install Skype 4, download it from the Skype website. **Before installing Skype 4**, you need to purge the old Skype.
```
sudo apt-get purge skype skype-bin skype-common skype-bin:i386
```Install Skype 4, and reboot. (Yeah, I know, rebooting is usually only for Windows, but Skype is a bit different.)

If it is worse than the old Skype, it's easy enough to revert. Uninstall Skype 4 as follows and reinstall Skype 2 from the standard repositories.
```
sudo apt-get purge skype
```

---

