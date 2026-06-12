---
title: "access openoffice documents across network"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by motoperpetuo on 2009-05-22
i've been having a lot of trouble accessing openoffice.org documents across my home network lately. seems like this used to work, but now it doesn't.

both of the computers i'm working with are running linux (ubuntu 8.10 on my laptop, fedora 10 on my desktop, for what it's worth). here's the process i go through:

1) on my laptop, i open nautilus to my home directory.
2) i choose go|location.
3) in the location field, i type something like sftp://root@10.55.77.2/home/motoperpetuo (i.e. the ip address and destination i want to connect to on my desktop).
4) i have to type in a few passwords here, the root password for the desktop, and some sort of keyring password. the remote directory on my desktop opens up.
5) i double-click on any openoffice.org document in the remote directory.
6) a dialog reading "user name and password required" appears. it specifices that the user name is root (and that i'm logging on to the desktop).
7) i enter the root password for my desktop and click OK.
8 ) the same "user name and password required" dialog appears, this time with no user name specified. i try the root password a few more times and eventually get the error "general internet error has occured."

the same thing happens if try opening the openoffice.org app first and browsing within it to the remote file.

on the other hand, if i double-click on a simple text file in the remote directory, for example, it opens right up. i can also browse directly to music files on the remote computer and get them to play. this problem only seems to happen with openoffice.org files.

anyone have any idea how to get this to work? it's driving me quite mad.

---

### Post by cariboo on 2009-05-22
If you need to use root to remotely access your own home directory on a remote computer, you probably have seriously screwed up ownership and permissions. I have all my documents stored on my file server, I never have to log in as root to access Openoffice.org files. I just double click the file and it opens in OpenOffice. They usually open as read only, but all I have to do is click on the open document to allow read/write.

---

### Post by motoperpetuo on 2009-05-22
> **cariboo907 said:**
> If you need to use root to remotely access your own home directory on a remote computer, you probably have seriously screwed up ownership and permissions. I have all my documents stored on my file server, I never have to log in as root to access Openoffice.org files. I just double click the file and it opens in OpenOffice. They usually open as read only, but all I have to do is click on the open document to allow read/write.

that may well be, although i haven't changed ownership on any files or folders, and i've tried to change permissions to make them as open as possible. i don't have to use root to access my remote desktop, i just figured root would have the best access and maybe help get around this problem, but no dice. i get the same problem no matter what user account i use to access the remote computer, and it's always only with OOo files.

does anyone have any advice on how i might get around this? does anyone else get the "general internet error" when trying to access OOo files on a remote computer?

---

### Post by motoperpetuo on 2009-06-21
i got a new laptop and put ubuntu 9.04 on it. that seems to have fixed this problem. i think 9.04 uses openoffice.org 3.0. i would imagine that a combination of the two resolved this.

---

### Post by motoperpetuo on 2009-06-21
btw, how can i mark this thread resolved? i think it used to be under "thread tools," but the options seem to have changed.

---

### Post by dmizer on 2009-06-21
> **motoperpetuo said:**
> btw, how can i mark this thread resolved? i think it used to be under "thread tools," but the options seem to have changed.

That plugin was causing database corruption issues on the forum, so it's permanently disabled.

You can, however, add a "solved" tag.

---

