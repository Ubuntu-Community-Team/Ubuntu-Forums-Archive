---
title: "Can't See All of Login Screen"
date: 2011-01-19
forum: Mythbuntu
---

### Post by sudleyplace on 2011-01-19
Recently, I've been trying to upgrade my old MythBuntu system based on 7.1 -- I did say it was old -- when I ran into the following problem.  After running the package manager installing whatever updates it said were available, when the system rebooted I was confronted with what looks like a login screen I can't see all of:

[http://www.sudleyplace.com/LowerRightCorner.jpg](http://www.sudleyplace.com/LowerRightCorner.jpg)

As the name implies, this image appears at startup in the lower right corner of the screen.  The above image is displayed with F10 pressed.  My name Bob Smith is behind the popup menu.  Unless I press F10, no keys appear to help further the action.  Enter, Tab, Esc, etc. all to nought.

I want upgrade to the latest MythBuntu, but first I want to backup my databases.  However, I can't login so that's not possible as yet.

I'm not too familiar with the details of ubuntu, so I don't know how to proceed, so I'm seeking professional help (you, not the shrink).

Any help is appreciated.

---

### Post by realwildman on 2011-01-20
My brother had the same trouble with his.  All he had to do was type his user name <return> and his password<return> and it would login into his desktop.  He could not see what he was typing when he was loging in but his desktop looked like normal once it loaded

---

### Post by Hatsune Miku on 2011-01-20
> **realwildman said:**
> My brother had the same trouble with his.  All he had to do was type his user name <return> and his password<return> and it would login into his desktop.  He could not see what he was typing when he was loging in but his desktop looked like normal once it loaded

Try doing this first and see what happens if it does not work try this

1. Reboot computer
2. After BIOS flash keep tapping esc key
3. GRUB should now be infront of you Select "Recovery"
4. Let the system boot into a command line
5. It should log you in a ROOT, if not log in (Type your name of your home directory "john, marry, etc) along with you password
6. Type in "startx" this will start the xserver along with GNOME.
7. Adjust the login screen settings.

---

### Post by sudleyplace on 2011-01-21
> **Hatsune Miku said:**
> Try doing this first and see what happens if it does not work try this

1. Reboot computer
2. After BIOS flash keep tapping esc key
3. GRUB should now be infront of you Select "Recovery"
4. Let the system boot into a command line
5. It should log you in a ROOT, if not log in (Type your name of your home directory "john, marry, etc) along with you password
6. Type in "startx" this will start the xserver along with GNOME.
7. Adjust the login screen settings.

Thanks very much to both of you for your help.

I tried blindly entering my user name and password without success.

Then I tried the second solution ending with startx and that got me to a desktop, however I could not find the correct place to set the screen resolution for the login screen.  I could change the display resolution via Right-click | Settings | Settings manager | Display, but no change there seemed to affect the login screen.

Where should I have gone to make that change?

Eventually, I realized that the login screen already knew my user name and was asking only for my password.  That got me logged in and back to a familiar desktop.

Then I found the place where I could tell it to log me in automatically and the login screen no longer appeared when rebooting.  The screen resolution at startup is still wrong, but at least it doesn't prevent me from logging in.

Again, thanks for all your help.  If anyone knows the answer to the question of where to set the screen resolution at login, I'd appreciate it.

---

