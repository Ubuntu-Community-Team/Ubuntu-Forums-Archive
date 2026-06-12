---
title: "Problem installing DivX"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by onedeep713 on 2007-05-03
I am new to Linux. I am using Ubuntu ultimate gamers edition. I downloaded the DivX 6.11 codec but can not install it. I need it to watch streaming videos. It gives me this message when I run the installation file:

 inflating: /tmp/.divx/lib/libdivx.so  
cp: cannot create regular file `/usr/local/lib/libdivx.so': Permission denied
mkdir: cannot create directory `/usr/local/include/divx': Permission denied
cp: target `/usr/local/include/divx/' is not a directory: No such file or directory
chown: cannot access `/usr/local/lib/libdivx.so': No such file or directory
chmod: cannot access `/usr/local/lib/libdivx.so': No such file or directory
ln: creating symbolic link `/usr/local/lib/libdivx.so.0' to `/usr/local/lib/libdivx.so': Permission denied
chown: cannot access `/usr/local/lib/libdivx.so.0': No such file or directory
chmod: cannot access `/usr/local/lib/libdivx.so.0': No such file or directory
/sbin/ldconfig: Can't create temporary cache file /etc/ld.so.cache~: Permission denied


Can somebody help me?

---

### Post by LuisGMarine on 2007-05-03
Have you tried installing VLC, which has these plugins built into them?  

All you have to do is do these commands, ( of course this is hoping you have your extra repos enabled )

```
sudo apt-get update
```

Then this is the command to install everything you need,
```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

After that everything should work properly.  I've heard of some people running into problems with the DiVX streaming off firefox, if that is the case pleaser refer to this thread below,

[Click Here!]("http://http://ubuntuforums.org/showthread.php?t=422445")

If you read that thread, there are a couple of extra minor fixes and setups to get you to stream just about every video out there with VLC.  For me VLC has done everything its suppose to do, things do run a bit different from windows, but nothing dramatical.  There are a few affects that I don't like, for example when you stream videos you don't get a user control ( play, stop, rewind ) etc buttons.  You have to reload the page entirely to start the clip all over again.

Good Luck

-LuisGMarine :guitar:

---

### Post by onedeep713 on 2007-05-03
Thanks for your help, but it still doesn't work. I'm trying to watch movies at [www.ssupload.com](www.ssupload.com) I have to have DivX web player to watch movies there. You have to check out the web site to know what I'm talking about. The way they have their videos is kind of like YouTube. They do not open in a player.

---

### Post by onedeep713 on 2007-05-03
Anyone?

---

### Post by tippit78 on 2007-05-15
Install the mozilla-mplayer plugin, and then move a couple of files, as explained here:

[http://ubuntuforums.org/showpost.php?p=2551819&postcount=6](http://ubuntuforums.org/showpost.php?p=2551819&postcount=6)

Alternatively, you could also copy the address of the content you're trying to watch and watch it in either mplayer or vlc.

---

