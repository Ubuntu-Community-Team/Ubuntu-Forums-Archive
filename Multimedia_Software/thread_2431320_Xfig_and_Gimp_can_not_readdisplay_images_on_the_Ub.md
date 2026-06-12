---
title: "Xfig and Gimp can not read/display images on the Ubuntu18.04LTS subsystem in Win10"
date: 2019-11-14
forum: Multimedia Software
---

### Post by qixycn on 2019-11-14
I have installed Ubuntu18.04LTS subsystem in Win10. Xfig and gimp are also installed and updated, and the fonts errors in xfig have also been solved. 
However, imges which were copyed from win10 folder to the home folder of Ubuntu subsystem can not be read and displayed in xfig 3.2.6a and gimp.
The error messages are shown below,
1) the xfig error messages:
No such picture file: /home/qixycn/ObservationSystem.png
No such picture file: /home/qixycn/CutbackMethod2.pdf
No such picture file: /home/qixycn/CutbackMethod.jpg
No such picture file: /home/qixycn/CutbackMethod.eps
Although the images can be loaded in xfig, however they are blank when you read the figures and there is no error message shown in the unbuntu terminal.

2) the gimp error messgaes:
(1) when I open gimp with the code: "export DISPALY=:0.0, gimp", an error message will be shown in the Ubuntu terminal, as shown in the below,

Failed to execute child process “dbus-launch” (No such file or directory)
(gimp:1109): GLib-GObject-WARNING **: 10:18:49.757: g_object_set_is_valid_property: object class 'GeglConfig' has no property named 'cache-size'
/usr/bin/dbus-launch terminated abnormally without any error message

(2) when I would like to read a image(gimp can not open .eps, .jpeg, but can open PDF file ) with gimp, a gimp message will appear as the following,
Opening '/home/qixycn/P1structure.eps' failed:
Permission denied

I truely hope someone can help me solve these problems. It has troubles me about a week. I'm so frustrated. Thank you in advance.

---

### Post by Holger_Gehrke on 2019-11-18
WSL is to Linux (or Ubuntu) as WINE to Windows. It's a compatibility layer that allows Windows to run *some* Linux software. Officially graphical applications aren't supported (yet ?), but if you've got an X-Server running on Windows it *can* work. I wouldn't bother with it for programs of which native versions exist (there are windows version of both GiMP and xfig available).

1) xfig is a vector graphics package which only handles it's own format (usually with the extension ".fig"). You can import some bitmaps, but you can't pass them on the command line. If you give a file on the command line, xfig assumes - whatever the file's name and extension may be - that it's a .fig file and tries to read it as if it were one, which will fail if it isn't. There are various programs that can create '.fig' files or convert to '.fig'.

2) I really hope that DISPALY is a typo ... you wouldn't get any kind of display with that (it should obviously be 'export DISPLAY=:0.0; gimp' or just 'DISPLAY=:0.0 gimp' - the first is two commands (that's what the ';' does, it separates multiple commands): define 'DISPLAY' and mark it for export then start gimp, the second form defines DISPLAY just in the environment of gimp). 
I'm **very** sure GiMP can read jpeg and eps, I've done both quite often.
Check the permissions of the file with 'ls -l /home/qixycn/P1structure.eps'. The beginning of the line you get in response should look something like '-rw-r--r-- 1 qixycn qixycn'. Characters 2-4, 5-7 and 8-10 are the permissions for user, group and others (r=read,w=write,x=execute). The number after isn't of interest for now. The next two words are the user and the group this file belongs to. You can use 'chmod' to change the permissions of a file and 'chown' to change ownership of a file, see the manual pages ('man chmod', 'man chown') or any good book on the Unix / Linux command line. You'll probably need to use 'sudo chown' (sudo=**s**witch **u**ser and **do**, I think Windows has something comparable, a 'run as' option in the context menu) if you are not the owner of the file.

Holger

---

### Post by SeijiSensei on 2019-11-18
You'd probably be better off installing the Windows version of [VirtualBox]("https://www.virtualbox.org/") and running Ubuntu in a virtual machine.  If you install the Extension Pack, you can use the "Shared Folders" feature which lets the VM access files stored on the host.  If you have a network, you can transfer the files by putting them in a shared folder.

---

