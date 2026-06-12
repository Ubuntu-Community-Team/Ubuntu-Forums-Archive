---
title: "Collection scan error - amarok"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by cryptonic on 2006-10-29
Recently i reinstalled ubuntu from beta edgy to rci edgy adn im ahaving some problems with amarok now, i was just wondering if im the only one. the bug is with the collection scanner, here it is ;

Sorry, the Collection Scan was aborted, since too many problems were encountered.
Advice: A common source for this problem is a broken 'TagLib' package on your computer. Replacing this package may help fixing the issue.
The following files caused problems:
/media/External Hardrive/Music/Bill Hicks/bill+chigg_sm.rm
/media/External Hardrive/Music/Bill Hicks/h_loses_sm.rm
/media/External Hardrive/Music/System Of A Down/System Of A Down/album review.txt
/media/External Hardrive/Music/Rammstein/Rammstein_-_Vater_Remix-2003-TLT/11_rammstein_-_vaters_minimix-tlt.mp3
/media/External Hardrive/Music/Ramstein/Sehnsucht/06 - RAMMSTEIN - BÃƒÂ¼ck dich.m
/media/External Hardrive/Music/Bill Hicks/bill+chigg_sm.rm
/media/External Hardrive/Music/Bill Hicks/h_loses_sm.rm
/media/External Hardrive/Music/System Of A Down/System Of A Down/album review.txt
/media/External Hardrive/Music/Rammstein/Rammstein_-_Vater_Remix-2003-TLT/11_rammstein_-_vaters_minimix-tlt.mp3
/media/External Hardrive/Music/Ramstein/Sehnsucht/06 - RAMMSTEIN - BÃƒÂ¼ck dich.m
/media/External Hardrive/Music/Bill Hicks/bill+chigg_sm.rm
/media/External Hardrive/Music/Bill Hicks/h_loses_sm.rm
/media/External Hardrive/Music/System Of A Down/System Of A Down/album review.txt
/media/External Hardrive/Music/Rammstein/Rammstein_-_Vater_Remix-2003-TLT/11_rammstein_-_vaters_minimix-tlt.mp3
/media/External Hardrive/Music/Ramstein/Sehnsucht/06 - RAMMSTEIN - BÃƒÂ¼ck dich.m
/media/External Hardrive/Music/Bill Hicks/bill+chigg_sm.rm
/media/External Hardrive/Music/Bill Hicks/h_loses_sm.rm
/media/External Hardrive/Music/System Of A Down/System Of A Down/album review.txt
/media/External Hardrive/Music/Rammstein/Rammstein_-_Vater_Remix-2003-TLT/11_rammstein_-_vaters_minimix-tlt.mp3
/media/External Hardrive/Music/Ramstein/Sehnsucht/06 - RAMMSTEIN - BÃƒÂ¼ck dich.m

---

### Post by linuxgrrl on 2006-10-30
Last week I upgraded from Hoary to Dapper and I had the same exact problem. I am using amarok svn. 

The solution for me was to uninstall the taglib 1.4 package using synaptic, then compile and install taglib 1.4 from source code using the file here: [http://developer.kde.org/~wheeler/files/src/taglib-1.4.tar.gz](http://developer.kde.org/~wheeler/files/src/taglib-1.4.tar.gz)

Thankfully it was not too difficult.
hope this helps,
Mary

---

### Post by koshari on 2006-11-01
hi mary, 

can i ask how you do this while still satisfying all amaroks dependencies?

---

### Post by koshari on 2006-11-02
btw this looks like the same issue being discussed in this closed thread, which suggests its not a libtag issue.

[http://www.ubuntuforums.org/archive/index.php/t-249442.html](http://www.ubuntuforums.org/archive/index.php/t-249442.html)

i have tried cifs remote share and it doesnt seem to matter, the scan just wont register the music in the share.

---

### Post by linuxgrrl on 2006-11-02
> **koshari said:**
> hi mary, 

can i ask how you do this while still satisfying all amaroks dependencies?

I am using the SVN version of amarok (so there is no Synaptic amarok package to complain at me :D )

I followed the excellent instructions here to set up Amarok SVN: [http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn](http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn))

it takes a little time but the instructions are nice and clear.

EDIT: and I guess there is probably a way to uninstall amarok and all its dependencies, compile/install taglib, and then reinstall the amarok package but I'm not sure exactly how that would work.  Might be worth a try.

---

### Post by catfishy on 2006-11-16
I've been noticing the REAL MEDIA files in the posted problem logs all over the place!

How i fixed this possible taglib/collection-building issue on my machine:
I read somewhere that .rm files were a problem with one user and i also found a few realmedia files in my collection; they are random and not-needed so i deleted them.... And THEN.... Amarok made it through the entire music collection (except one 10gb folder it keeps ignoring).  But the point is: No more possible taglib errors, and i've got my music again!
Perhaps try converting any .rm files or omit them from the collection and give it a try....
good luck!
[IMG]http://ubuntuforums.org/images/smilies/eusa_think.gif[/IMG]

---

### Post by juxmw on 2006-11-20
Hey

I have the same problem here in edgy. Tried to build amarok and libtag from source, but the same error still occurs (no *.rm problem :-) )

I changed smb.conf to utf8 and also the client side to cifs using correct charset -> the problem still exists.

The songs that are causing the problem have sometimes german umlauts, and the collection scanner error message cant display them correctly, but when i browse through the share with konqueror everthing's fine and amarok can also play them simply clicking the file AND it displays the file correctly ...

I'm driving crazy with this "bug" (if it is one), i've already read alle comments in all threads, the amarok mailing lists and so on ... still no solution?

juxmw

---

### Post by juxmw on 2006-11-20
I use NFS now, which isnt't a practicable solution for longer time ... but i 've alread played around hours and hours. Hopefully this will be fixed soon

---

### Post by koshari on 2006-11-22
well it seems the offending charactors here were uhmlets and the humble ' .

i removed/changed those charactors and it scanned fine, must be a cifs thing iam guessing. so as a workaround i guess you will have to do as i did, i changed them using easytag. and yet it took ages,

this seems to have removed the errors as in the initial post of this thread, however it will then scan through the entire collection but doesnt update the database, i also find that that amarok doesnt seem to be able to read the tags on the files i get it to play via cifs share. vlc and rhythmbox dont have this trouble.

---

### Post by koshari on 2006-11-29
for the record.

after changing the permissions on the box with the music to read/write amarok was happy,

---

### Post by bastille on 2007-02-10
I had the <<too many prblems encountered>> problem with the collection scanner too. But when I added the kubuntu-source for amarok and updated amarok from version 1.4.3 to 1.4.5 this problem was gone. Dunno if it works with dapper as well but i guess it's worth a try....
[http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)

---

### Post by koshari on 2007-02-13
> updated amarok from version 1.4.3 to 1.4.5

the error handling on 1.4.5 is vastly improved, 

it wont barf on an arror, and continues to scan, then will give you a dialog at the end of the scan that tells you of the offending files, 

a lot more user friendly IMHO.

---

### Post by spectralwt on 2007-09-01
Hi, I'm new here. 

It seems that Amarok scan is rather inefficient on my system.  I was hoping that when I use mySQL, Amarok will know to scan the collection only in the newly added directory, or it can pick out the new songs faster.   But it always scans the whole collection and takes very long every time I add something new.   I have about 5000 songs, too many ? it can't be. 
Is there a way around this?

---

