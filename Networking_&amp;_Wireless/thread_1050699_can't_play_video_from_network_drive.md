---
title: "can't play video from network drive"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by madmaxnj on 2009-01-25
My network consists of a wireless router, a wired XP machine, a wired IOMega Home Network Hard Drive, and Intrepid on an older machine running wireless.  The only way I've been able to connect to the nas from the Intrepid machine is to make it an FPT connection.  I setup a bookmark, so I can just select from the Places pull down and I get a folder icon on my desktop that I can browse.  I can open pictures, do slideshows, and I can even play music (mp3) by double-clicking and the movie player opens them and plays them.  I was running the System Monitor and see that after I select a song it downloads a good bit of it first before it starts playing, and then after it starts playing about every 10 seconds it will request and get more of the file.

This doesn't work with video files.  After it downloads a good bit of the file and its about to play I get an error message "An error occurred.  Could not read from resource."  I can play the files if I copy them to the local drive.  I've installed Gstreamer and it doesn't help, if I right-click on the file and select open with Movie Player(Gstreamer), same error message.  After doing some research I installed VLC media player.  It doesn't work either.  If I right click the file and select open with VLC media play, VLC will open, I'll see in System Monitor that the file starts to download, but VLC will start to play a couple of frames of the video and then the application will close with no error message.  Again, VLC will play a file fine if I copy down to the local drive first.  To see if it might be something with the way the network drive is configured I tried to play the same media files from the XP machine with WMP and they work fine, even super huge DVD files.  I'm only trying to do little digital camera generated mpgs on the Intrepid machine.

Anybody know what could be the problem?  I've tried mounting the network drive so I can see it as a local folder but that doesn't seem to work with this drive.  I've checked around and alot of other people have a problem accessing this drive with Ubuntu.  I don't think thats my problem here with video since the applications start to pull down the files.

---

### Post by nixscripter on 2009-01-26
I would suggest this:

If FTP works, and what you want is a mounted device, there is a way to have an FTP connection "pretend" to be a mounted device. It's called FTPfs. I don't know whether the perforamce will be good, but there shouldn't be any more filesystme problems.

[http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

If this doesn't work, then I do have a more complex suggestion or two.

---

### Post by madmaxnj on 2009-02-02
jeff@jeff-desktop:~$ curlftpfs [ftp://192.168.0.101/public](ftp://192.168.0.101/public) /media
Error connecting to ftp: Server denied you to change to the given directory

This is what I got right away after booting up.  Then I connected to the bookmark for the share, opened File Browser and navigated to some files, and tried this command line again with the same error message.

So then I try this

jeff@jeff-desktop:~$ curlftpfs [ftp://192.168.0.101/public](ftp://192.168.0.101/public) /media/share -o user="user:pass"
fusermount: failed to open /etc/fuse.conf: Permission denied
fusermount: user has no write access to mountpoint /media/share
jeff@jeff-desktop:~$ sudo curlftpfs [ftp://192.168.0.101/public](ftp://192.168.0.101/public) /media/share -o user="user:pass"
[sudo] password for jeff: 
jeff@jeff-desktop:~$ 

This may have worked, but when I navigate to the folder in File Browser I get this error message:
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "share".

I'm trying to figure out how to change the permissions to /media so I can try and look in there.  It seems that I can't do any admin changes through the guis and always need to figure it out through Terminal.

---

### Post by nixscripter on 2009-02-02
Silly question: you logged in as Jeff before with FTP, and you could see and fetch all the files, right?

If you still can, then try another version with some more options:

```
sudo curlftpfs -f -r -o uid=**[local Jeff's UID]** --user=jeff:**[remote password]** 192.168.0.101 /media/share
```

This will have the system give the local user Jeff access to the files, which might have been your problem before.

If you can get this working, I suggest putting your FTP server into a jail root to avoid giving access to your entire disk.

---

### Post by cybermatthieu on 2009-08-13
I also had the error :
```
Error connecting to ftp: Server denied you to change to the given directory

```

for that same knid of mount as yours:
> curlftpfs [ftp://192.168.0.101/public](ftp://192.168.0.101/public) /media

I fixed it by adding a second backslash after the servername or ip.

Like this :

```
curlftpfs ftp://192.168.0.101//public /media
```

Hope this helps

---

