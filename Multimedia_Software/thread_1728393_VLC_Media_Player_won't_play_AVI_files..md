---
title: "VLC Media Player won't play AVI files."
date: 2011-04-13
forum: Multimedia Software
---

### Post by markymark64 on 2011-04-13
VLC Media player has been giving me a few problems and I'm hoping someone here has a fix for this issue.

Yesterday I was playing an avi file and my browser, that was also running, froze up in the background. At the same time my video became choppy and started to freeze. I shut down firefox and vlc but when I opened it back up all of my avi files where greyed out. I've posted a request for help on the vlc forums but no one has responded. Has anyone else experienced this problem? It's frustrating because my vlc player will still play dvd's but it won't play any avi files. Oh and I tried the drag and drop option per a suggestion but all I get is sound with no video. 

Lastly, I should mention that I'm a multi tasker and was also trouble shooting a problem I was having with amarok, which I've since uninstalled. Could amarok have some how screwed up my files? I've even uninstalled an reinstalled vlc but nothing works. 

Please help me Obi Wan Kenobi, you're my only hope.

---

### Post by wolfen69 on 2011-04-13
Open your home folder and do Ctrl-H. That will show your hidden files. Go to the .config folder and open it. You will see a VLC folder inside. Delete it and then restart VLC. If that doesn't work I'm at a loss.

---

### Post by markymark64 on 2011-04-13
Wolfen, thanks for the suggestion but it didn't work. Cheers.

---

### Post by wolfen69 on 2011-04-13
Completely remove vlc, and try a newer version of vlc. Do:
```
sudo add-apt-repository ppa:n-muench/vlc
```
then 
```
sudo apt-get update
```
then go to synaptic and look for version 1.1.8

This is for ubuntu 10.10

---

### Post by markymark64 on 2011-04-13
Wolfen, I now have the latest version installed and even upgraded the ibavcodec-extra-52 files but still no cigar. All of my avi files remain greyed out.

---

### Post by markymark64 on 2011-04-13
Wolfen, I think my problem is resolve sort of but I'm going to leave this thread open for another day or so because the problem isn't with vlc media player but with the way ubuntu handles non unix partitions. I think ubuntu has treated all of my videos on this one partition as well as another as hidden files because they're not ext3 or ext4 partitions. This is why all of my avi files are greyed out. I don't have many but when I copied one avi file to the videos folder on my home partition and clicked on it, it played perfectly! Well, it had a moment of lag at the beginning but I can handle that because I suspect that is the actual hard drive my ubuntu is installed on. No errors mind you but just a crappy hard drive by a top name manufacturer. So, I'm going to dig around to see how I can unhide windows files and see if there's a fix. If you have any thoughts please post them here. I really appreciate all the help you've offered to me.

---

### Post by markymark64 on 2011-04-13
Ok, I think I'm a bit premature but this issue does have something to do with ubuntu and permissions. When I copied a file over to the video folder from the explorer window and right clicked I chose use vlc to play this file and it did. I figured it was fixed but my video files are still greyed out. I guess I just found a workaround.

---

### Post by wolfen69 on 2011-04-13
Are you trying to play avi's from an NTFS partition? I do that all the time without any issues. Ubuntu is very good at reading other file systems.

---

### Post by markymark64 on 2011-04-14
Yes, it's an ntfs partition. For some reason vlc simply doesn't want to read any avi files even those that I've added to my home partition. Oh, and as mentioned before, Totem can see these files. It's just VLC that views them as hidden.

---

### Post by markymark64 on 2011-04-16
Hey Wolfen, or anyone else reading this thread. I think I figured out the problem. Seems like maybe my ntfs partitions are being mounted correctly. I can see them and browse them but I can't play music in vlc at all or videos unless I open up a explorer window and right-click on the file and choose to open it in vlc. It's weird though, I can play music through another application but not through vlc. I installed the NTFS configuration tool and believe they are mounted correctly. So, I'm scratching my head now. I mean, I could originally see all of them. Now I can see them but they're greyed out as if they're hidden from me. Audacious can see and play any of the music files and so can my totem movie player so it can't really be a mounting issue, can it? There's got to be some setting in vlc that I'm missing, right?

---

