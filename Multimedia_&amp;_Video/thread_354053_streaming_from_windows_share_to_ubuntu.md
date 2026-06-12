---
title: "streaming from windows share to ubuntu"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by farscape on 2007-02-05
I have 2 computers. One dedicated Windows XP PC. And a Dual boot(removable hard drives) WinowsXP and Ubuntu(6.06) PC. I have a usb extrnal hard drive attached to the windows box that is full of movies(avi) and music(mp3/ogg).

Is there a linux media player that will make and stream playlists from that external hardrive attached to the windows box?
The only application that I can get to play even one song at a time is movie player. And movie player won't stream movies from it. All other players(xmms, amarok, kaffeine etc...)won't even browse the network.

Is it possible to do this without any additional server type software?

Thanks

---

### Post by farscape on 2007-02-07
I can't seem to find one. Is the limitation because of the NTFS file system? Would Linux play better with a fat32 share? or is it that Linux dosen't do well on a home network without support programs?

---

### Post by Bram77 on 2007-02-08
I have exactly the same problem. I can browse the files, even write to the shares, but I can't play any media (movies or music) directly from the shares. I have to copy them to a local drive to be able to do that.

---

### Post by farscape on 2007-03-29
GOT IT!
Permanently mount the share with smbfs.

Read this.
[HowToMountsmbfsSharesPermanently]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently")

Don't forget to install smbfs. I did...
Mount the share.
Then install the proper codecs....
import the playlist and BAM!

I have an external HD attached to my windows machine that holds all my music. I can now stream them to Ubuntu. I'm using Rhythmbox right now.

---

### Post by pognonec on 2007-05-09
Does it also work for your .avi files? In my case, I can stream .mp3, but not .avi !?!?!?
However, when I copy the .avi through the network from the windows box to the Ubuntu box, and play it on Ubuntu, its works fine...
Any idea?

---

### Post by FatherVic on 2007-05-13
I am having the same problem.
I have mounted my share from a Vista PC.
I can browse the directory and even copy avi's to and from, however, I am not able to stream the AVI's to mplayer.
The vids do eventually come up after 5-10 minutes of waiting.  The vids are play a second or two and stall for long periods of time.  I am not sure who to nail this on, Ubuntu or MS But I am very, very frustrated.

---

### Post by eli_d on 2007-07-22
i have had this problem before. XMMS/Mplayer/etc will stream your mp3s/videos through a windows network share, but you need to mount it first. see this thread: [http://doc.gwos.org/index.php/HowToM...resPermanently](http://doc.gwos.org/index.php/HowToM...resPermanently) for specific instructions.

it's a bit overwhelming at first (considering how much you have to do, just to play mp3s, but it's worth it in the end).

basically:

1) use synaptic to make sure you have the smbfs / smbmount command package. search for samba, you'll probably already have samba installed, but you will need the smbfs command.
2) create a directory on your desktop that will be the share mounting point
3) create a file in your root directory for your password / username information (gedit .smbpasswd... see instructions in link above for more detail)
4) mount the drive by entering something along the lines of:
Code:

sudo smbmount //elidesk/backup /home/eli/Desktop/elidesk -o credentials=/home/eli/.smbpasswd 0 0

5) open the directory on your desktop and your files should now be accessible and playable in xmms


this will not be saved when you restart your computer. so an additional step is to add your mount command line from #4 to /etc/fstab (the file that mounts all your drives when you start the computer) is necessary. see the link above for more specific instructions.

---

### Post by jimrz on 2007-07-22
> **farscape said:**
> I can't seem to find one. Is the limitation because of the NTFS file system? Would Linux play better with a fat32 share? or is it that Linux dosen't do well on a home network without support programs?

nope fat32 is gives the same results

---

### Post by jimrz on 2007-07-22
I just used [[COLOR="Sienna"]**_this thread_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") to try and fix the same problem and it worked like a charm :)

---

### Post by celliott on 2007-08-14
I have posted the solution in the following thread. Please post there if you have questions. 


[http://ubuntuforums.org/showthread.php?p=3188215#post3188215]("http://ubuntuforums.org/showthread.php?p=3188215#post3188215")


Cheers

---

