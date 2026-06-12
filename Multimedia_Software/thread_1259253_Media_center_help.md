---
title: "Media center help"
date: 2009-09-06
forum: Multimedia Software
---

### Post by shadghost on 2009-09-06
I am making a media center that can be controaled via a web browser from a diffrent computer, the set up is the ubuntu computer is hooked up to my 5.1 sound and tv, so it will be playing the media, and i need a way to controal it

right now i have jinzora set up to play music from the web browser, just looking for something that will start movies from the web browser

---

### Post by lovinglinux on 2009-09-06
I recommend using ssh.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
[http://ubuntuforums.org/showthread.php?p=6926168#post6926168](http://ubuntuforums.org/showthread.php?p=6926168#post6926168)

You could also try my media center extension for Firefox, called [FoxMediaCenter]("http://fmc.isgreat.org"). It is designed for a standalone computer, so it's not exactly what you want, but you might like it.

---

### Post by shadghost on 2009-09-06
ya, right now i do use ssh and vlc for movies, just want it so outhers can figure it out, like my roomate

---

### Post by issih on 2009-09-06
Enable the remote control interface in vlc:

(go into the preferences and then hit advanced or all (I forget which it is now), navigate to interface->Main Interfaces and select the http interface in extra interfaces.

Now just set vlc to autostart with the computer and you should be all set..

Just point a web browser at (hostip:8080) and you should get a web page for controlling the vlc instance running on your box.

Hope that helps

---

### Post by shadghost on 2009-09-07
i am not sure it would work good with biger libaries, but that is what i wanted, thanks 

this is a long shot, but any ieda of something that does the same thing for tv tuner cards, like a way to get mythtv controled via browser

---

### Post by issih on 2009-09-07
Not via browser no, but you can have a little standalone remote app:

[http://www.telemedia.ch/publ/myth-telnet.html](http://www.telemedia.ch/publ/myth-telnet.html)

There are also iphone/ipod touch apps to do it if you jave such things (the one I've played with is called mymote or something liek that)

Hope that helps

---

