---
title: "Banshee not recognizing .flac metadata"
date: 2011-09-08
forum: Multimedia Software
---

### Post by lfreeze on 2011-09-08
I've been using Ubuntu (currently 11.04) on my primary, work computer now for about a year.  Though there's been a bit of a learning curve I think I can say that I've enjoyed it for the most part and am enjoying my (relative) independence from Windows.

I recently decided to set up a file server in my home using Ubuntu Server (10.10).  I've begun the project of converting all of my music on CD to .flac files on the server.  The plan is to eventually have various other computers in the house be able to play music off of it and put all of my CDs into storage.  I've come to like Banshee and would like to be able to use Banshee on the various computers for the task.  I'm running into one problem, however.  Banshee isn't recognizing/reading the metadata I've encoded into the .flac files.

I've been converting my CDs with Asunder, manipulating the metadata with Ex Falso---much of my music is classical music and I like to have composer, conductor, etc. information available when the files play and Asunder isn't quite sophisticated enough for this---and then attaching album art with Metaflac from the command line.  Banshee has no trouble reading the metadata in the .flac files when the files are on the same system as the one running Banshee.  However, when I move the same files to my server (I use Rsync for this) and play them, Banshee doesn't seem to read/recognize any of the metadata.  I know that the metadata accompanies the .flac files on to the server, because many other media players read/recognize the metadata just fine---I've played the files off the server with Totem, VLC, and even Winamp on a Windows-running system and they all display the correct metadata and album art.

Any help with this would be much appreciated.  Unless I can find a way to fix this problem, I won't be able to use Banshee for the task, which would be a shame.  Because of this problem, Banshee imports the entire music collection on the server into one "Unknown Artist" folder.  I know that I can set up a DAAP server, but the little reading I've done suggests that I wouldn't have album art available on the client side.  I'm not sure if this is correct.  At any rate, it seems rather odd that Banshee doesn't recognize the metadata when so many other media players do.

---

### Post by dniMretsaM on 2011-09-08
What version of Banshee are you using? For the latest daily builds, run these commands:
```
sudo add-apt-repository ppa:banshee-team/banshee-daily
sudo apt-get update
sudo apt-get upgrade
```

You also might try a different tag editor. Kid3-qt works well for me. EasyTag is another option for GNOME/Unity. I never really liked it though. Note that the Kid3-qt is designed for KDE (Kubuntu) and EasyTag for GNOME/Unity (Ubuntu). Although either can be installed on any system.

---

### Post by lfreeze on 2011-09-08
Thanks for your suggestions.  I was running Banshee 2.0, but am now, following your suggestion, running 2.1.3.  I was doubtful that changing tag editors would make a difference, since even the previous version of Banshee had no trouble reading the metadata when the files were on the same system running Banshee.  I tried EasyTag and that didn't seem to make any difference.  Again, Banshee (2.3.1) had no trouble reading metadata off of local files, but when those files were copied to the server, Banshee failed to read the metadata.

---

### Post by dniMretsaM on 2011-09-09
Ok well then it probably a problem on the server side of things. You  cold try installing Banshee on the server and see if it reads the  metadata from there. That way you'll know that it's getting transfered  to the server and not lost somehow. Anyway, I have no experience with servers, so someone  with more knowledge will have to help you. Good luck!

---

