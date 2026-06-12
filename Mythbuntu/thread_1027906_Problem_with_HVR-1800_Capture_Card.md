---
title: "Problem with HVR-1800 Capture Card"
date: 2009-01-01
forum: Mythbuntu
---

### Post by Ovulator on 2009-01-01
I am extremely new to Linux so I'm sorry for any stupid question. I have installed Mythbuntu and for the life of me can't get anything to go with the HVR-1800. 

When clicking on "watch tv" nothing happens, screen flicks black very briefly.

After googling this seems to be the most helpful thread:
[http://ubuntuforums.org/showpost.php?p=6129026&postcount=132](http://ubuntuforums.org/showpost.php?p=6129026&postcount=132)

I tried to follow the instructions here, but after doing what seemed to start well after typing in 'make && make install' it ended with a long list of:

"strip:zr364xx.ko: could not create temporary file to hold stripped copy: No error"

ending with:

"make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/usr/local/src/v4l-dvb/v4l'
make: *** [install] Error 2"

I tried editing the xorg.conf file like stated in that thread but I don't seem to have the permission to save the changes, what can I do to get that? I'm trying to edit in the GUI not the terminal.

I'm running Ibex 8.10 AMD64, Myth TV .21. In the MythTV backend setup I have it set to V4L Analog card, which seems to detect the HVR-1800.

Any advice of what I need to do or what I'm doing wrong? If any more information is needed I am willing to provide it if I have the know how to obtain that information.

Thanks a ton to anyone who is willing to help out.

---

### Post by ahood on 2009-01-02
> **Ovulator said:**
> I am extremely new to Linux so I'm sorry for any stupid question. I have installed Mythbuntu and for the life of me can't get anything to go with the HVR-1800. 

I tried to follow the instructions here, but after doing what seemed to start well after typing in 'make && make install' it ended with a long list of:

I tried editing the xorg.conf file like stated in that thread but I don't seem to have the permission to save the changes, what can I do to get that? I'm trying to edit in the GUI not the terminal.

First, WELCOME! to the world of Linux. 

I have been watching the threads on the HVR-1800 and any successes made with this piece of hardware.

Installing programs and editing system files, like xorg.conf, requires admin/root privileges. On Ubuntu systems, the first user does not have admin/root privileges by default. However, the first user can execute commands with admin/root privileges by preceding the command with 'sudo', and then after pressing the Enter key, type in the user account password.

For instance, to edit xorg.conf, I will type...

> sudo nano /etc/xorg.conf

Press the Enter key and then type in my user password.

Be careful with using sudo. I recommend backing up files before editing them with the command.

> sudo cp /etc/xorg.conf /etc/xorg.conf.backup

I hope this helps. Good luck. Report any success with the HVR-1800.

---

