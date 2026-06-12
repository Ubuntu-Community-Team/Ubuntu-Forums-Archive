---
title: "Cannot Play AVI Files Over a Samaba Share"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by deejross on 2006-11-25
Just installed Edgy last night and finished going through the fiasco of getting X and Usplash to run properly, so I can mark one thing off my ever-growing list of problems. Today's problem is I can't play AVI files (XviD/DivX) over a samba share. I tried mounting the share with Places->Connect To Server.. (which I shouldn't have to do anyways. It should play straight from the share). Then I made sure I had all the codecs installed, then finally got fed up with the whole thing, downloaded EasyUbuntu, and had it install all the bad and ugly codecs. Still nothing. Then I removed totem-gstreamer and replaced with totem-xine. Nothing. Then I installed Kaffeine. Nothing. Then I installed gxine. Nothing.

After much time spent Googling the problem, it's obvious that no one has an answer to the problem, other than "install VLC".

I can't keep my thoughts about VLC to myself anymore, so I will post them here. This is your fair warning if you like VLC or don't want to hear my rant, please skip over the following rant section.

[begin rant]

1 - I shouldn't have to install VLC to begin with if I don't wanna. It's not a solution to the problem, merely a band aid for a broken bone.
2 - VLC sucks. The user interface is buggy, not user friendly, and annoying.
3 - VLC is dead (at least, soon to be dead if they don't get their priorities straight). By this I mean they haven't updated/fixed anything in over 2 years. Sure, they released a new version in June 2006, but it didn't address ANY of the major problems people were complaining about. Instead, they update unicode support. Who gives a flying crap about unicode support when the UI doesn't even remember my preferences after it closes (assuming I don't have to kill it with System Monitor)?

Again, sorry if you are in love with VLC, but this is MY opinion, so please don't flame me for it.

[end rant]

After reading my own post, I realize it sounds as if I'm really upset, and to be honest, I'm more disappointed and frustrated more than anything. I have high hopes for Ubuntu as being the replacement for Windows one day, but in my opinion, after going through all of this, it still has a long way to go.

In closing, I hope someone has a solution, and as far as communities go, I think Ubuntu has one of the best. I've always been able to get a good answer from everyone here, and I really hope I have not upset anyone with my venting frustration.

Thanks in advance for any help you can give me.

EDIT: It appears as though MP3 files will not play over samba shares either, so it's definatly something samba/xine related.
this is the output I get from Kaffeine when trying to play video or audio:

xine: cannot find input plugin for MRL [smb://WORKGROUP;linux@ross/E-SATA2/Downloads/Bullet For My Valentine - The Poison/Bullet For My Valentine - Tears Dont Fall.mp3]
xine: input plugin cannot open MRL [smb://WORKGROUP;linux@ross/E-SATA2/Downloads/Bullet For My Valentine - The Poison/Bullet For My Valentine - Tears Dont Fall.mp3]
xine: found input plugin  : CIFS/SMB input plugin based on libsmbclient

---

### Post by Mike'sHardLinux on 2006-11-25
Hi.

This is a known problem. There is another thread in the general forum already. I doubt there's a fix yet. I ended up getting NFS working again on my server and quit using Samba.

I actually like VLC for some things, and don't have any problems with it. Since it doesn't remember your settings, you could make a script that runs VLC with all the right command-line switches. This is what I do. I know it's a PITA, but you'll learn from doing it, and you'll only have to write the script once, unless you want to use VLC with different settings.

I understand your being upset. The problem with Samba and media files is kind of a big deal for a home computer, I think. 


Sorry I don't have a real solution, but I feel your pain. This one really bugged me, too. :(

---

### Post by deejross on 2006-11-25
Well, if anything, I feel a little better knowing that it's not just me having the problem. My biggest problem is that all my media files are stored on my XP machine, so doubt I could use NFS for that :) 

I guess now my question is, are they ever going to fix it? I know it used to work about a year ago without problems and I haven't tried it since then, so I don't know if it's an Edgy thing or if someone screwed up Samba. But either way, it would be impossible for someone like me to make the move to Ubuntu from Windows knowing about a set back like this.

But thanks for the information. As I said, I do feel a bit better knowing that it's not just a stupid mistake on my part.

---

### Post by buddie on 2006-11-26
you can try to mount the share folder into your filesystem so that xine, or any player recognize it as local file. i personally like amarok for playing mp3s and xine for movies.

and xine can stream on samba share, but u need to do it the hard way.
- browse the share folder (alt+f2, then type smb://ipaddress, then go to the desired folder)
- open xine (Application - sound n video - xine, or alt+f2, type xine)
- drag and drop the file file.
- note that if you want to change the video, you need to Stop the current playing video.

---

### Post by deejross on 2006-11-26
Are you saying to copy the file to a local folder or to drag & drop the file from the samba share to xine?

Copying to a local folder is unacceptable...period. If I want to watch a DVD from a samba share, I'd have to wait 15 minutes to watch it. Having to copy it is unacceptable anyways.

Else, I was dragging and dropping from the samba share to xine, and that is what started the whole post.

I just checked the Samba site and it seems as if they either don't know about the problem, or they gave up trying to fix it. So, again, I'm very disappointed that Linux will ultimately fail as a multimedia PC if it can't stream audio/video when stored on a Windows machine. :(

---

### Post by Mike'sHardLinux on 2006-12-01
This problem has been brought up a few times at Ubuntu Forums. Just do a search with keywords totem samba. Funny how many people still aren't aware of it. I guess not everyone plays videos or music on their computers.

Here is the bug report: [https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147")

One of the workarounds was to not use totem, but I haven't actually tried that since using NFS is better for me than using Samba.

---

### Post by process91 on 2007-04-12
**FIXED IT!**

I was having this problem as well over a number of shares before I figured out what was causing it.

The problem is the permissions on the share, nothing really to do with kaffeine or xine or anything (although it would be nice if your permissions could transfer). 

If it's a windows share:
From the Windows Host
1 - Right-click the share folder and go to properties
2 - Select the share name and click Permissions
3 - If "everyone" isn't already there, then click Add...
         - Type in Everyone and press Add
4 - Give "everyone" at least read access
5 - Click "OK" and click "OK"

Try it out and let me know if this works, I'm dying to know if it works.

Also, if it's a Linux share like mine was:
From the Linux Host
1 - Right-click the share folder and go to properties
2 - Click the Share tab and click the "Configure file sharing" button (enter root password)
3 - Click on the share you'd like to stream your videos from
4 - Click change...
5 - Tick the public option
6 - Click "more samba options"
7 - Click the Users tab
8 - Change "All Unspecified Users" to "Allow"
9 - Click OK - OK - OK - OK

Try it out. I realize this opens up the network for reading (the shares don't have to be writable by everyone, just readable). It's possible that there is an "xine" user that you can configure specific access for, but I'm really just a n00b on this subject.

-- Michael Boratko
Shameless Plug for [Computer Repair and Web Design]("http://www.starstreak.com")

---

### Post by deejross on 2007-04-12
Well, I won't be able to try it out for a couple days, but I'll tell you what I've experienced since I posted this. I have all my media on my Windows machine, and at the time, I had created a 'linux' user on the box and gave it the correct permissions. If what you're saying is true, then even though you have a user setup to properly, you STILL need to give Everyone read access. If that's true, then it could be a Windows related sharing problem, but I doubt it and I'll tell you why.

A few updates have come out that fix the error, but there is still a problem...it still doesn't "stream". Instead, you have to wait for whatever program to download the ENTIRE file before it starts playing. Unless whatever you're watching is less than 50 MB (seriously doubt it), then it takes some time. Most of my stuff is around the 700 MB range, which could take 5 or 6 minutes to download (it's really slow for some reason). That is WAY too long. And what's worse is you don't see it download anything, all you see is the application freeze while it's downloading...so you just have to have faith that it's doing what it's supposed to be doing.

As stated in my original post, a couple years ago, I opened the SAME file and it streamed (not copied in full) the media file I was watching in seconds. 

So what happened? Is this ever going to get fixed? According to Mike'sHardLinux, this is a pretty well known problem. If it's not fixable, you'd think someone, somewhere would have said something.

---

### Post by process91 on 2007-05-18
Wow, you're in Vernon, CT and I'm in New Britain, CT - small world.

Anyway, I was having this problem as well and I had created the "linux" user. I think the problem is that xine or mplayer or any streaming media player has it's own user for the process and any file it plays has to be accessible to that user. So even though you can browse, edit, rename, delete, etc. a file when logged in as the "Linux" user, the media player's process is not able to touch anything on that share because it doesn't have the privileges. I could be way off base, I just started getting really into Linux like a month ago but I have worked with Windows and permissions extensively.

Anyway, conclusion is that I'd be interested to know if you enable full access for everyone if the problem goes away or not. It did for me, but I might be lucky. Also, if you use a Linux share there's an option for process user access (I think I saw that in Advanced SWAT config) which should solve the problem without opening huge network security holes. If you figure out the user name that your media player uses you should be able to give that user full access which should close the hole on a Windows box too, but that type of handshake between Microsoft and Linux would be too much to hope for.

---

### Post by celliott on 2007-08-14
Hi,

There is a way to get the files to STREAM over your SMB network. All you need to do is mount the volume. (NOT COPY THE FILES)

Its quite simple really. Follow instructions below.

[LIST=1]
[*]Open Up Terminal
[*]Type the following:
[/LIST]

```
cd /mnt
```

NOTE: (You can use any name of a directory you want. For example purposes i am using smbfiles as my directory name.
```
sudo mkdir smbfiles
``` 

Set Permissions
```
sudo chmod -R 775 smbfiles
```

Mount the volume.  NOTE: if your server address = server IP or name. Also, share name = the share you have setup or the folder name. 
```
sudo mount -t smbfs -o username=your username,password=your password //server address/Share Name /mnt/smbfiles/
```

Presto, you can now double click the files and rum them in totem-xine.

If you have any questions, please let me know.

Cheers
Spikey :D

---

### Post by deejross on 2007-08-14
Thanks for your reply, though this topic is somewhat outdated now with the release of Feisty. But the original point of this post was saying that you shouldn't have to mount anything to stream files over SMB. Before Edgy, you didn't have to, which means something happened with the release of Edgy that disabled that ability. Feisty seemed to fix this problem, but at the cost of performance. I am now helping test out Gusty which seems to improve upon the speed of SMB streaming without mounting.

---

### Post by DugieHowsa on 2007-08-15
--------------------------------------------------------------------------------

I have found that smbfs is very buggy. You may have better luck with cifs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

### Post by celliott on 2007-08-22
I am not able to stream from an SMB on Fiesty. What could be broken then?

---

### Post by deejross on 2007-08-22
You should probably first, copy a music file to your local drive and make sure it works that way. If not, you need to install the restricted packages. If you can play locally, but not over SMB, then something weird is going on as this got fixed with Feisty.

Worst case, if there actually is a problem with streaming over SMB, try mounting the share first using mount.cifs. I don't know the exact command for it, but there are plenty of examples, just Google "mount cifs"

Hope that helps somewhat.

---

### Post by fjpos on 2007-11-16
Hi

The problem I am having is specific to VLC on Linux. I can play avi files with totem on a linux box (Gutsy 7.10) stored on  another linux machine ( gutsy 7.10) or stored on an XP box. but not using VLC. From my XP box I can use VLC to play avi files stored on my linux box (gutsy 7.10) and from memory this was also the case with feisty 7.04. So for me it is related to VLC on a linux box. Apart from that I can't add anything:confused:

---

