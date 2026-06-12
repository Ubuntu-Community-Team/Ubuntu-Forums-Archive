---
title: "devede not working in 11.04"
date: 2011-05-04
forum: Multimedia Software
---

### Post by denolion on 2011-05-04
For some reason I keep getting the error message that says "Failed to create the DVD tree, maybe you ran out of disk space. Is this a bug related to the upgrade, and if so will it be resolved soon.

---

### Post by wolfen69 on 2011-05-04
Go to synaptic and Completely Remove it, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
then reinstall devede.

---

### Post by denolion on 2011-05-04
I tried your solution, but I'm still getting the same error message.

---

### Post by Darknezz41 on 2011-05-07
I am getting the same message and there is no help at all about it nowhere so I installed Convertx under Wine and this has been my only solution.

---

### Post by uRock on 2011-06-22
Bump for having the same problem. 
[ATTACH]195763[/ATTACH]

---

### Post by howefield on 2011-06-22
I tried to replicate the issue, but all went fine.

Try this thread..

[http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1](http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1)

---

### Post by ron999 on 2011-06-22
> **howefield said:**
> 

Try this thread..

[http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1](http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1)
Hi

In that thread it hints that the DeVeDe problem is caused because the latest version of **dvdauthor** is being used now.
dvdauthor -h
DVDAuthor::dvdauthor, version **0.7.0**.

This is a workaround for dvdauthor, maybe it will cure the DeVeDe problem too:- 

Use a text editor to create a file named **video_format**.
In the file, just type one word...
Either:-
**PAL**
Or:-
**NTSC**

Save this video_format file in (hidden) folder **/home/username/.config**.

---

### Post by uRock on 2011-06-22
I gave up on it after getting past the errors, it started creating the ISO with only one of the video clips instead of all of them. I am using Brasero, which looks like it is going to take at least 3 hours to convert to mpeg2. 8(

Leave it to Brasero to run for almost two hours then quit without an error message.

---

### Post by handy on 2011-06-22
What version of DeVeDe are you using?

I'm just doing my daily system upgrade on Arch & I noticed that there is a new version: 

devede-3.16.9-3

Perhaps it will solve your problem?

---

### Post by uRock on 2011-06-22
3.16.9-0

I have uninstalled it for the moment. I had installed 4 or 5 dvd burning programs, so I figured removing them all, then installing devede by itself will get the job done. I am currently waiting on ffmpeg to convert the files to mpeg2 in case I have to use brasero, though I prefer to have the ability to add a menu and breaks in the vids which devede has the ability to do.

---

### Post by handy on 2011-06-23
Yes, DeVeDe is certainly straight forward, especially when compared to the likes of the editors like Cinelerra...

---

### Post by uRock on 2011-06-23
Devede seems to not like m4v as it creates the menu, but when I click on a title, it just restarts the menu. Using mpg files, though, seems to be working fine. I'll post back after I see for sure.

---

### Post by denolion on 2011-06-23
my apologies, but i forgot to mention that I get the "failed to create dvd tree" message when trying to convert an mkv file to iso through devede.

---

### Post by uRock on 2011-06-23
So far the only way I can get Devede to work is by using .mpg files. I just completed my first ISO with it and it turned out fine.

---

### Post by denolion on 2011-06-23
.avi files also work, but if you want to add .srt subtitle files you'll have to use the VIDEO_FORMAT=NTSC trick to get that to work.I'm still waiting to see if someone can find a way to get the .mkv files to work again like they use to before the 11.04 upgrade.

---

### Post by 4Foot on 2011-07-03
> **denolion said:**
> .avi files also work, but if you want to add .srt subtitle files you'll have to use the VIDEO_FORMAT=NTSC trick to get that to work.I'm still waiting to see if someone can find a way to get the .mkv files to work again like they use to before the 11.04 upgrade.

Denolion:

As I mentioned in the other thread that you opened, I cannot get .avi files to convert to ISO either. I get the " cannot create...disk space" message.

4Foot

---

### Post by nkbatsi on 2011-07-17
This topic was very helpful and I found solution to my problem.

I kept getting a SPUMUX error at DeVeDe each time I was trying to make a movie with subs.

The problem started since I upgraded   to 11.04.

I did what wolfen69 proposed: 

Go to synaptic and Completely Remove it, then do:
     Code:
     sudo apt-get clean && sudo apt-get autoremove 
then reinstall devede.

And also before running DeVeDe for the first time after the fresh installation i did what ron999 proposed:

[SIZE=1] [SIZE=2]                    Originally Posted by **howefield**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10969909#post10969909")[/SIZE][/SIZE][SIZE=2]                 
                 [I]
Try this thread..

[http://groups.google.com/group/deved...81fc4948?pli=1]("http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1")  [/I]
                                 
[/SIZE] [SIZE=2]Hi

In that thread it hints that the DeVeDe problem is caused because the latest version of [/SIZE] [SIZE=2]**dvdauthor** is being used now.
dvdauthor -h
DVDAuthor::dvdauthor, version **0.7.0**.

This is a workaround for dvdauthor, maybe it will cure the DeVeDe problem too:- [/SIZE] [SIZE=2]

Use a text editor to create a file named [/SIZE] [SIZE=2]**video_format**.
In the file, just type one word...
Either:-
**PAL** [/SIZE][SIZE=2]
Or:-
**NTSC** [/SIZE][SIZE=2]

Save this video_format file in (hidden) folder [/SIZE] [SIZE=2]**/home/username/.config**.
                                                                                                                                    [/SIZE][SIZE=2]*                                              Last edited by ron999; 3 Weeks Ago at 08:22 PM..                                                           *             
                                         [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                                                                [/SIZE]                                                     [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10969968")
It seems that DeVeDe works again for me. Thank you all gyus

---

### Post by handy on 2011-07-18
**@nkbatsi:** Did you upgrade your system to 11.04 or do a fresh install of 11.04 ?

---

### Post by nkbatsi on 2011-07-24
upgraded from 10.10 to 11.04

---

### Post by Casper34 on 2011-07-29
Here is how I fixed mine..... 

[]("http://www.rastersoft.com/programas/devede.html#download_section")[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

All I did was download the DEB file and install over the exsiting install. the latest build is Version 3.17.0 (2011-07-03) and fixes...


[LIST]
[*]Fixed a bug in MKISOFS, when it shows decimals with a comman instead of a dot
[*]Defines the VIDEO_FORMAT environment variable, needed in current SPUMUX versions
[*]Added bugfix AC3_FIX for current MENCODER versions
[*]Other little bugfixes
[*]
[/LIST]

I converted a movie last night and just burnt it with no issues. Good Luck!

---

### Post by volito on 2011-10-03
wondering if fix was uninstall reinstall?comments?

or just happens with certain files?

thnx having same issues

---

