---
title: "Samba error while copying, invalid argument"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by tebucky on 2010-01-05
Hello,

I'm running ubuntu 9.04 and trying to pull over some files via the GUI from a XP box over locally. I'm getting this error:

"error while copying file into /volcano/tunes invalid argument" (under show more details)

If I just copy over a mp3 file it works fine but the when I copy the entire directory I get this error. Any thoughts?

---

### Post by VastOne on 2010-01-05
> **tebucky said:**
> Hello,

I'm running ubuntu 9.04 and trying to pull over some files via the GUI from a XP box over locally. I'm getting this error:

"error while copying file into /volcano/tunes invalid argument" (under show more details)

If I just copy over a mp3 file it works fine but the when I copy the entire directory I get this error. Any thoughts?

Is it any directory you try to copy over or just that one?

When you say GUI, you mean Nautilus file manager?

Can you copy the entire contents of that dir over? As opposed to the whole directory?

---

### Post by tebucky on 2010-01-05
>Is it any directory you try to copy over or just that one?

Any directory

>When you say GUI, you mean Nautilus file manager?

Yes, sorry about that.  It is Nautilus

>Can you copy the entire contents of that dir over? As opposed to the whole directory? 

Yes, when I move inside the dir and copy singe files or all of them it works just fine.

---

### Post by VastOne on 2010-01-05
> **tebucky said:**
> >Is it any directory you try to copy over or just that one?

Any directory

>When you say GUI, you mean Nautilus file manager?

Yes, sorry about that.  It is Nautilus

>Can you copy the entire contents of that dir over? As opposed to the whole directory? 

Yes, when I move inside the dir and copy singe files or all of them it works just fine.

What if you select 5 files from that directory to copy over at one time?

Never mind I see the answer now sorry

---

### Post by VastOne on 2010-01-05
> **tebucky said:**
> >Is it any directory you try to copy over or just that one?

Any directory

>When you say GUI, you mean Nautilus file manager?

Yes, sorry about that.  It is Nautilus

>Can you copy the entire contents of that dir over? As opposed to the whole directory? 

Yes, when I move inside the dir and copy singe files or all of them it works just fine.

Within Nautilus will you make a directory on the XP box and copy any contents to it and then try to copy that whole directory to Ubuntu please?

---

### Post by tebucky on 2010-01-05
So its a Network share on the LAN but the same thing happens when moving directories from an XP box directly.

So I can successfully do the revers, move folders from Ubuntu to the NAS or to XP.  The issue seems to be one way (from NAS/XP to Ubuntu)

---

### Post by VastOne on 2010-01-05
> **tebucky said:**
> So its a Network share on the LAN but the same thing happens when moving directories from an XP box directly.

I am not sure what you are saying here.... You are getting the same error on the XP box when on it?

---

### Post by tebucky on 2010-01-05
No, it works if I perform the reverse (copy directory to XP box from Ubuntu).  Does that make sens?

---

### Post by VastOne on 2010-01-05
> **tebucky said:**
> No, it works if I perform the reverse (copy directory to XP box from Ubuntu).  Does that make sens?

Yes that does...

Can you create a new directory on XP from Nautilus, copy files to it and then copy that whole directory back to Ubuntu as a test?

---

### Post by tebucky on 2010-01-05
I can do everything except copy the directory back from the XP box to Ubuntu.  I get an error copying the file

---

### Post by VastOne on 2010-01-05
It looks as if this is a bug that is being worked on

Check this link

[https://bugs.launchpad.net/autofs/+bug/393012](https://bugs.launchpad.net/autofs/+bug/393012)

---

### Post by tebucky on 2010-01-05
This appears to be the reverse though, correct?

While copying a folder from ubuntu to a Windows XP PC, I get an error message, "Error while copying "Tarantula-1.jpg".

I'm trying to do it from XP to ubuntu

---

### Post by adam814 on 2010-01-05
Is it possible you're trying to copy to a folder your user doesn't have write permissions on?  Does it fail if you try to copy it to your home directory or /tmp?

---

### Post by tebucky on 2010-01-05
I only have one user (me) so that shouldn't be an issue ;-)

---

### Post by adam814 on 2010-01-05
Well, you *almost* never really have only one user on a *nix system (It could be done, but that one user would have to be root and that would be dangerous).  For example on mine /usr is owned by root and if I try to copy to something in /usr without using sudo the copy fails with an error that permission is denied.

Nautilus doesn't use sudo for copies so if it would fail without sudo/gksu on the command line it'll fail in Nautilus too.

---

### Post by VastOne on 2010-01-05
> **adam814 said:**
> Well, you *almost* never really have only one user on a *nix system (It could be done, but that one user would have to be root and that would be dangerous).  For example on mine /usr is owned by root and if I try to copy to something in /usr without using sudo the copy fails with an error that permission is denied.

Nautilus doesn't use sudo for copies so if it would fail without sudo/gksu on the command line it'll fail in Nautilus too.

I thought this too but wouldn't it be a totally different error message along the lines of access denied or no rights?

---

### Post by tebucky on 2010-01-05
copying works, its the copying of directories that is failing...

---

### Post by adam814 on 2010-01-05
Yeah, I actually tried it and didn't get the same message tebucky's having.  It was kind of a shot in the dark.

---

### Post by tebucky on 2010-01-05
Totally stumped... any other ideas?

---

### Post by KeLa on 2010-01-05
Are you having same username/password used in both computers?
That's what i use and it works well for me.

---

### Post by Morbius1 on 2010-01-05
First off I don't know the ansewer to the problem but maybe it has something to do with this.

Create an empty directory called test in your home directory and then use a terminal to copy Documents to test. You'll get an error:

**cp /home/morbius/Documents /home/morbius/test**
[COLOR=Blue]cp: omitting directory `/home/morbius/Documents'
[/COLOR]
But if you do it this way:
**cp -R /home/morbius/Documents /home/morbius/test**

It works and the Documents directory and all it's contents are copied.

I can copy /paste in nautilus from Documents to test but maybe there is a restriction when using the network. CIFS limitation ?

I don't know.

---

### Post by tebucky on 2010-01-05
It doesn't seem to be authentication related... Although for some reason I can see the drive on my XP box, enter the user name credentials and I get a permissions error...  I have no problem doing the reverse, authenticating windows shares from ubuntu.

---

