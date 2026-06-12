---
title: "Can't play flv video in mythvideo, can't change file types"
date: 2009-12-13
forum: Mythbuntu
---

### Post by stib on 2009-12-13
Hi

I'm trying to get flash video to play in mythvideo. With the internal player nothing happens when I choose a flv file, it just blinks and comes back to the browser. I tried changing the command for flv files in set up>media settings>videos settings>file types to various things. First I tried this, which worked on a command line
```
cvlc -f --play-and-exit %s
```
then just plain
```
vlc %s
```
but none of them did anything, except freeze.

when I tried
```
vlc file://%s
```
I got an error message 
```
vlc could not open the MRL myth://videos@127.0.0.1:6543/path/to/thevideo.flv
```
looks like mythtv is passing a myth:// style url. Is there any way to just get t to pass the file path, or a local file:// type url?

I can't seem to find any documentation for the commands here, if anyone can point me in the right direction I' much appreciate it.

---

### Post by stib on 2009-12-13
Oh, my bad, the reason I couldn't get the videos to play with the internal player was that the permissions were wrong. I'd copied them off another machine and it hadn't given group access to mythtv.

However, I still want to switch to VLC for ogg files, as I'm getting lots of blocky artefacts with the internal player. Once again I've tried vlc -f file://%s, but all I get is the vlc controls, and no video.

thanks.

---

### Post by Rocko262c on 2011-09-24
Dear Stib,

I think I am having a similar problem setting permissions.  I have set the permissions for my directory videoz as follows:

sudo chmod 7555 videoz
sudo chown mythtv:mythtv videoz
sudo chown mymachine:mymachine videoz

Unfortunately, this didn't work. Can you kindly suggest how you would set permissions.

Thanks for your assistance.

Cheers,
Rocko262c

---

### Post by nickrout on 2011-09-25
You cannot combine storage groups (which use the myth:// protocol) and external players.

Some people use a script to turn the myth:// url passed by myth to a proper path, if the file is accessible by a normal path (eg is on a local system or is on a network mounted drive elsewhere on your lan).

---

### Post by Rocko262c on 2011-09-25
Dear Nickrout,

Thanks for your reply.  

Nickrout>You cannot combine storage groups (which use the myth:// protocol) and external players.

I am actually using the Internal Player and that didn't work so I tried using external players to assess the problem.

I have partitioned my hard drive so that I have a partition called "videoz" so I can put files there and watch them.  If i copy the to the files to the default folder (/var/lib/mythtv/videos) and change the directory back to this in the "Storage Groups" in the Backend Setup and reboot, everything works well. But if i change everything to match the "videoz" folder, nothing works.

I did make another partition for the LiveTV recordings and MythBuntu has no trouble writing the files to that partition.

I will do some Googling as you suggested and try to create a script to overcome the nomenclature that Mythtv uses when using an external player.

Thanks for your help,
Rocko262c

---

