---
title: "Unable to save playlist with VLC-1.0.2"
date: 2010-01-07
forum: Multimedia Software
---

### Post by fancypiper on 2010-01-07
I am running VLC release 1.0.2 and I am unable to save a playlist.  Does anyone else have this problem and/or know of a fix?

---

### Post by mc4man on 2010-01-07
```
sudo apt-get install qt4-qtconfig
```

Then go to System -> Preferences -> Qt 4 Settings and for the gui pick something other than default or GTK+. (Cleanlooks works well - save on way out

---

### Post by fancypiper on 2010-01-07
No joy :(.

I am upgrading to VLC-1.0.3 and will try that and see if it's fixed.  According to launch pad, this bug is supposed to be fixed.

---

### Post by mc4man on 2010-01-07
I use 1.1 and 1.0.4 (have 1.0.3

As I remember (and can see now in 1.1), if you're saving a playlist to file you still can't use the default (gtk+) gui.

---

### Post by fancypiper on 2010-01-07
How did you install vlc-1.1? Perhaps you meant 1.0.1?

---

### Post by mc4man on 2010-01-07
> How did you install vlc-1.1

You have to build it. It has some interesting new features, can be up and down as far as reliability, ect. which can change from day to day

(I keep a 1.0.4 install which for the most part works great

---

### Post by ron999 on 2010-01-11
Hi
I have this problem too. I can't save playlists with VLC v1.0.3.
I found a thread that says it's something to do with the GUI.

Here:-[http://omgili.com/jmp/.0rSU5LtMgxP5I3BMqJ0_YCBLJ8uBa5hpgALvYmKJv.nN3P_zX2qFFGOdISjYJeqgAHvxXmmih0ml7dHUHWNhj2beOZPvBujImGsvezfSYgzXsh3i9Sji81vZwGIZc3.f25_SNsWZPtciUBJnCHUI.yx2Do_4MqRVgBpq26Z_fJ.q1Wj7rQvVXYsdKm27WnfHbnmRLOyflT3mA59.hy_AikC5hguU3H8]("http://omgili.com/jmp/.0rSU5LtMgxP5I3BMqJ0_YCBLJ8uBa5hpgALvYmKJv.nN3P_zX2qFFGOdISjYJeqgAHvxXmmih0ml7dHUHWNhj2beOZPvBujImGsvezfSYgzXsh3i9Sji81vZwGIZc3.f25_SNsWZPtciUBJnCHUI.yx2Do_4MqRVgBpq26Z_fJ.q1Wj7rQvVXYsdKm27WnfHbnmRLOyflT3mA59.hy_AikC5hguU3H8")

Until there's an easy solution I'll make playlists using a text editor.

This thread's marked as SOLVED. What's the solution, upgrade to v1.1?
:confused:

---

### Post by fancypiper on 2010-01-11
My solution, step by step.

> **ron999 said:**
> 
This thread's marked as SOLVED. What's the solution, upgrade to v1.1?
:confused:First, I added the getdeb apps sources

# getdeb apps for VLC
Go to System-Administration-Software Sources, Third-Party Software tab, Add:
```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

Add the repository GPG key, open a terminal window and type:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

Next, Using Synaptic, I installed VLC-1.0.4.

Then I installed qt4-qtconfig.  I think I used the command:

```
sudo apt-get install qt4-qtconfig
```

You can do this with synaptic as well.

Finally, I went to System -> Preferences -> Qt 4 Settings and for the gui, I picked Cleanlooks, saved and exited.

I launched vlc and all my gripes were fixed. :D

---

### Post by ron999 on 2010-01-11
YES! :grin:

I am still running v1.0.3. Not upgraded to v1.0.4.


But your other instructions solved it. Playlist saved OK.

When I saw the instruction in post #2 above, I thought it was some setting needed in VLC. :confused:

Thanks a lot.=D>

[B][SIZE="5"][SOLVED][/SIZE]
[/B]

---

### Post by ron999 on 2010-01-11
Thanks again fancypiper.
I may upgrade to v1.0.4 later using your instructions.

---

### Post by ron999 on 2010-01-11
[SIZE="5"][COLOR="Red"]Everything's Hunky Dory.[/COLOR][/SIZE]

[IMG]http://img696.imageshack.us/img696/4969/vlc104.jpg[/IMG]

---

### Post by rifter on 2010-02-27
Running Ubuntu 9.10 (Karmic) 32 bit

A few things I would like to add in case anyone else finds this and has problems.

I would like to start this by saying that vlc is a great player, but saving and editing playlists has been a problem for a long time, with varying results, across platforms over the years.

When I changed the gui using the _[color=blue][post=8628299]above instructions[/post][/color]_, still running 1.0.2, I was able to save playlists, but vlc would not properly open them.  (It added them to the playlist as files, and when you hit play it did not do anything.  Normally when you add a playlist to vlc and hit play it loads the playlist and populates the playlist with files).

Then I tried to add the getdeb repository _[color=blue][post=8647021]as suggested above[/post][/color]_.  Unfortunately the repository was down, and although the wiki and blog for the project were up, and the wiki mentioned there were mirrors, I could not find a list of mirrors from them.

Google found a mirror at mirrors.dotsrc.org, which I added to my sources with the following lines:

```

deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) karmic-getdeb apps
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) karmic-getdeb games

```

However, when I tried to add the key I got this:

```

$ wget -q -O- [http://mirrors.dotsrc.org/getdeb/ubuntu/dists/karmic-getdeb/Release.gpg](http://mirrors.dotsrc.org/getdeb/ubuntu/dists/karmic-getdeb/Release.gpg) | sudo apt-key add -
gpg: no valid OpenPGP data found.

```

I kept hitting my head against the wall on this one. The file looks like a perfectly good keyfile to me, but gpg gave the same kind of errors:

```

$ file Release.gpg
Release.gpg: PGP signature
$ sudo apt-key add ./Release.gpg
gpg: no valid OpenPGP data found.

```

Thankfully I found _[color=blue][post=7667086]this post[/post][/color]_, which helped me out.  I had tried to add the key through the "add sources" gui to see if I would get a different error, and I did. It included the NO_PUBKEY error described (which is how I found that post).  So I did the commands described with the following output:

```

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8A515F046D7E7CF
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys A8A515F046D7E7CF
gpg: requesting key 46D7E7CF from hkp server keyserver.ubuntu.com
gpg: key 46D7E7CF: public key "GetDeb Archive Automatic Signing Key <archive@getdeb.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
$

```

Then the repos worked and I was able to get vlc 1.0.5

This fixed the problem of not being able to save playlists, and unlike before when you add a playlist file it not only knows what to do, but it correctly loads up the playlist (you don't have to hit play first like before).

It also fixed the problem I was having with 1.0.2 where I was unable to change the order of files in a playlist by dragging them up or down on the playlist (this was a new one).
Even better, it fixed an ancient bug that had been present in vlc for ages, which is that even after you reorder files in a playlist and save the playlist, when you load it next time the files are still in the wrong order (this no longer happens -- hooray!).
I will say that there remains one more annoying bug with the vlc playlist feature.  Vlc relies on extensions to know what to do with a playlist file, and does not put an extension on the file by default when you save it. What I mean is, if you save a playlist file, type a name for the file to be saved and select a type (which shows an extension), vlc will not add an extension to the name of the file you save, and when you try to load that playlist it will not work (it just adds that file to the playlist, and does nothing.  You have to type an extension when vlc asks you what to name the file, and you have to make sure you type the same extension it says for the type of playlist you are saving (for instance xspf).

Anyway Thank you to the people earlier in the thread who puzzled out this problem, and good luck to those of you who might stumble on this and need to follow their and my instructions.

UPDATE 03-05-2010: The bugs came back ... all of them. Maybe an update knocked the fixes out, but it wasn't a vlc update. In any case what I had to do to fix this was go to the qt4 settings, pick a different GUI style from the one I had (cleanlooks) (I picked windows for this test), save, and the bugs went away. Then I was able to switch back to cleanlooks, save, and the bugs were still gone. I don't know if this had to be redone because of a recent unclean reboot that I had to do or what, but that is how I got things back to normal.

New update: It seems that this fix did not completely work after all.  The reordering didn't work right (in that any file I tried to move to a different place in the playlist moved to the top of the playlist instead), and I can't save playlists that I reordered.  It's weird because when I did the above fix (changing the gui style back and forth) I tested and the playlist edited and saved fine.  But when I quit vlc again and started it up again it was broken again.  I think I may have to do the gui style change before I launch vlc every time in order for the fixes to stick, which would be bad. But like I said before, all of these playlist bugs in vlc are cross-platform (well at least windows and linux) and have been there for a long time (or at least repeatedly pop up).  
     I don't think making the playlist work is a high priority for vlc devs because if it was the playlist would cease being such a red-headed stepchild.  One other bug I hate that has never been fixed: when you select multiple files to add in the add file dialog they appear in semirandom order in the playlist.  This is especially a pain in conjunction with the other bugs.  Essentially the only way to guarantee you will be able to watch videos in the right order in vlc is to have them all in the same directory with names that enforce their order.  That is a kind of dumb hack/requirement.

---

