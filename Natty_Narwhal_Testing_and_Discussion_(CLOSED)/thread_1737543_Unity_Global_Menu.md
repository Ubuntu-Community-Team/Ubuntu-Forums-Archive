---
title: "Unity Global Menu"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucasart on 2011-04-23
how do I remove it ?

or (even better), how do i make it only appear when the window is maximised ? (OMHO this would have been the right way to do a global menu)

---

### Post by nickleboyblue on 2011-04-23
Unity is a brand new interface, and it's going to be different from what you're used to as a result.  The newness of it is also going to limit how much you can customize behavior, but I am sure that as time goes on, customization features will begin to appear.

To my knowledge, the global menu really is global for all windows under Unity.  Since it is a logical interface suggestion to only use global menus for maximized windows or for windows when they are the only open window on the workspace.

Without that kind of global menu behavior, we have to click an extra time to select the window we want to work with, then navigate to the global menu.  Though one click more doesn't sound like much of a hassle, when you're switching regularly between windows, it gets really annoying.  I suggest that with multiple windows open, only the focused window that is maximized should use the global menu, while all other smaller windows should use the default menu bars that existed before Unity.

---

### Post by beew on 2011-04-23
> **nickleboyblue said:**
> Unity is a brand new interface, and it's going to be different from what you're used to as a result.  The newness of it is also going to limit how much you can customize behavior, but I am sure that as time goes on, customization features will begin to appear.

To my knowledge, the global menu really is global for all windows under Unity.  Since it is a logical interface suggestion to only use global menus for maximized windows or for windows when they are the only open window on the workspace.

Without that kind of global menu behavior, we have to click an extra time to select the window we want to work with, then navigate to the global menu.  Though one click more doesn't sound like much of a hassle, when you're switching regularly between windows, it gets really annoying.  I suggest that with multiple windows open, only the focused window that is maximized should use the global menu, while all other smaller windows should use the default menu bars that existed before Unity.

The thing I hate about this is instead of making the OS works for the user you are trying to tell the user that you know better what works for him and insist that the user should train himself to use Unity rather than to implement the features and options that would work for the user.

I see the same high handed approach from Mark Shuttleworth on those bugs pages. We know what you "should" want, if you don't like it there is something wrong with you.

That turns me off more than the global menu itself.

---

### Post by beew on 2011-04-23
> **lucasart said:**
> how do I remove it ?

or (even better), how do i make it only appear when the window is maximised ? (OMHO this would have been the right way to do a global menu)

I don't know how to selectively enable the global menu, but you can get rid of it by uninstalling indicator-appmenu, that would restore the menu to the application windows but there may be some odd behaviour for maximized windows sometimes.

---

### Post by mc4man on 2011-04-23
Happened to get an email today about this 'opinion' bug that I'd had a similar but not quite then same bug duped too.
You could ck. out though don't think it will produce much.
*do find the current last comment by Chen Li to be very presumptuous and a fairly common mis-read on what window size many people use on 'smaller' screens

[https://bugs.launchpad.net/unity/+bug/682788](https://bugs.launchpad.net/unity/+bug/682788)

I have both a 24" Desktop and 13" laptop and many times don't use maxed windows on the laptop.
In fact there are many apps where the GM makes no sense at all.

To individually cause an app to retain it's menu while keeping GM enabled there are a couple of ways - the easiest is to just edit the apps .desktop, most commonly in /usr/share/applications
This works for all uses of an app except from  cli which requires a different approach

Simply add this directly after Exec= and before the binary name
```
env UBUNTU_MENUPROXY=0
```

Example for gedit to show how, note the space after =0 
(i often have multiple unmaxed separate gedit windows, the GM is a hindrance

```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=env UBUNTU_MENUPROXY=0 gedit %U
Terminal=false
Type=Application
ect.
ect.
```

qt4 apps usually need a slightly different edit - 
```
env QT_X11_NO_NATIVE_MENUBAR=1
```
Ex, vlc

```
Desktop Entry]
Version=1.0
Name=VLC media player
Comment=Read, capture, broadcast your multimedia streams
clipped..
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U
Icon=vlc
ect.
ect.

```

---

### Post by ds_shellback on 2011-04-24
I'd like to change the global menu for gedit but I can't seem to find the .desktop file your referring too - sorry.

In /user/share/applications there is a file called gedit which is 520 bytes long and claims to be a desktop configuration file. If I open as administrator all I see is a blank screen !!!

Where am I going wrong?

---

### Post by mc4man on 2011-04-24
To open a .desktop in an editor you either need to create a nautilus action for r.click option or do from command line, either completely or command <space> drag and drop the .desktop into terminal, click in terminal to return focus > enter on keyboard
(or open a gksudo gedit window, then D&D the .desktop on to

```
gksudo gedit /usr/share/applications/gedit.desktop
```

Edit: after editing a .desktop best to logout then back in

---

### Post by ds_shellback on 2011-04-24
Ah, thanks for that I was trying to edit the file from the graphical interface (nautilus-gksu installed).

Begs the question - why is this only editable from the command line???

---

### Post by teachop on 2011-04-24
You can drag and drop selected ones on a sudo'ed gedit too.

---

### Post by rtalcott on 2011-04-24
**beew**  Thank You for the tip...my global menu is now gone and life is good.....time for a beer!
Thank You!
rt

---

### Post by mc4man on 2011-04-24
> Begs the question - why is this only editable from the command line???
The reasoning not actually sure - there is no open with in .desktop file properties so one can't change the default which is to open (run the Exec=) on l.click.
As far as no default r. click option (though you can create one or more) I guess because .desktops are not considered text/plain or any other mimetype associated by text editors

(and as noted you can drop them into an open text editor window

---

### Post by lucasart on 2011-04-27
> **beew said:**
> The thing I hate about this is instead of making the OS works for the user you are trying to tell the user that you know better what works for him and insist that the user should train himself to use Unity rather than to implement the features and options that would work for the user.

I see the same high handed approach from Mark Shuttleworth on those bugs pages. We know what you "should" want, if you don't like it there is something wrong with you.

That turns me off more than the global menu itself.

After playing with Unity, and trying to understand its logic, I can safely say that I *hate everything* about it. Or should I say each and every of its alleged "improvements" over GNOME. I don't even want to start listing them, as someone has already done it for me[http://www.omgubuntu.co.uk/2011/03/unity/](http://www.omgubuntu.co.uk/2011/03/unity/)

But what bothers me most is that canonical is taking all these decisions without listening to the users. And if the community vastly rejects Unity, they will just not listen and carry on their effort in developping Unity. Perhaps they imagine that users will "have" to follow, but as it happens they don't and that's the whole point of free software in the first place, FREEDOM, simply

As for me, will now move to Fedora, with GNOME 3. I really can't wait for Fedora 15 to come out.

---

### Post by seeker5528 on 2011-04-27
> **lucasart said:**
> After playing with Unity, and trying to understand its logic, I can safely say that I *hate everything* about it. Or should I say each and every of its alleged "improvements" over GNOME. I don't even want to start listing them, as someone has already done it for me[http://www.omgubuntu.co.uk/2011/03/unity/](http://www.omgubuntu.co.uk/2011/03/unity/)

But what bothers me most is that canonical is taking all these decisions without listening to the users. And if the community vastly rejects Unity, they will just not listen and carry on their effort in developping Unity. Perhaps they imagine that users will "have" to follow, but as it happens they don't and that's the whole point of free software in the first place, FREEDOM, simply

As for me, will now move to Fedora, with GNOME 3. I really can't wait for Fedora 15 to come out.

That stuff indicated in [http://www.omgubuntu.co.uk/2011/03/unity/](http://www.omgubuntu.co.uk/2011/03/unity/) bothers you about Unity, but not Gnome-shell?

Some people might be tempted to think the stuff said there applies even more to gnome-shell since there has not seemed to be any equivalent to....

[http://design.canonical.com/2010/11/usability-testing-of-unity/](http://design.canonical.com/2010/11/usability-testing-of-unity/)

[http://lwn.net/Articles/438678/](http://lwn.net/Articles/438678/)

[http://design.canonical.com/2011/04/unity-benchmark-usability-april-2011/](http://design.canonical.com/2011/04/unity-benchmark-usability-april-2011/)

... while gnome-shell was under development. 

Later, Seeker

---

### Post by ranch hand on 2011-04-27
> **lucasart said:**
> After playing with Unity, and trying to understand its logic, I can safely say that I *hate everything* about it. Or should I say each and every of its alleged "improvements" over GNOME. I don't even want to start listing them, as someone has already done it for me[http://www.omgubuntu.co.uk/2011/03/unity/](http://www.omgubuntu.co.uk/2011/03/unity/)

But what bothers me most is that canonical is taking all these decisions without listening to the users. And if the community vastly rejects Unity, they will just not listen and carry on their effort in developping Unity. Perhaps they imagine that users will "have" to follow, but as it happens they don't and that's the whole point of free software in the first place, FREEDOM, simply

As for me, will now move to Fedora, with GNOME 3. I really can't wait for Fedora 15 to come out.
As has been pointed out here a number of times, the Ubuntu users here on the forums make up a small fraction of Ubuntu users and they need to consider the other folks too.

I find that statement a little disturbing.  I am not sure how they can possibly get the opinion of those other users in a meaningful way.

This is the "official" Ubuntu forums, set up by Ubuntu and run on their servers.  We are told that the devs and, I assume, the design folks too, pay little attention to the forums.  If this is the case with the official forums, how much attention is given to these other  folks opinion, however obtained?

---

