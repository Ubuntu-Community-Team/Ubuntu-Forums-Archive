---
title: "Mythstream - Help on installing"
date: 2010-03-16
forum: Mythbuntu
---

### Post by Symbiot78 on 2010-03-16
Hi.

1st.. I am a windows user just ported to linux/ubuntu.. so PLEASE.. speak in laymen's terms :) sloooooooow nicely understandable words :)

Ok, that out of the way...

I have installed mythbuntu as a vmWare install, and am setting it up as an independent mediacenter.

I want to be able to stream radio and TV.

I found Mythstream, and it seems to contain all I need, like plugins for youtube etc.

But honestly I have no idea how to install it.

I've been looking through the mythstream website, but haven't found anything I could use or understand.

I tried downloading the youtube plugin, and followed the readme.. which told me to put the pl files in /home/username/.mythtv/mythstream/parsers
now .mythtv did exist, but not as a hidden folder..
/mythstream didn't exist
/parsers didn't exist..

I created both, and put the files in the parsers folder, but it didn't really do anything.
I assume I need some 'main plugin' installed?

I am hoping someone will guide me.. 

I will probably have many many many many more questions :-)

---

### Post by Symbiot78 on 2010-03-17
Any takers on this wonderful noob question? :)

---

### Post by SiHa on 2010-03-17
Not sure Mythstream is being supported anymore.
Anyway, for a more polished experience for streaming stuff, you might want to look at Boxee.
It is fairly simple to add a menu option to MythTV to fire up Boxee when you want to watch Youtube (for example). When you exit Boxee, you're back at the MythTV menu. There's a few posts on here about it.

BTW .mythtv **is** a hidden folder, the '.' means it is hidden.
```
ls
```will not show it```
ls -a
```will.

---

### Post by azmyth on 2010-03-17
You have to compile mythstream. I know the shoutcast parsers work but I'm not sure about the youtube ones. You need to install the mythtv-dev package. You need to download the latest mythstream and untar the package and you need to navigate to mythstream then mystream again then

qmake-qt4 mythstream.pro
make
sudo make install

You'll need a compiler installed and some qt4 packages. Probably a bit tricky for someone new to linux.

---

### Post by Symbiot78 on 2010-03-17
hi

thanks, I can't run boxee since I am currently running linux via vmWare. 

Is there an alternative to mythstream to stream netradio etc?

---

### Post by SiHa on 2010-03-17
> **Symbiot78 said:**
> hi

thanks, I can't run boxee since I am currently running linux via vmWare. 

Is there an alternative to mythstream to stream netradio etc?

Sorry thought you meant you'd had a play with it under vmWare and were now going for a proper install.

---

### Post by timconradinc on 2010-03-17
If this is all you're using it for, perhaps try an older release of mythbuntu? I'm pretty sure it worked in 8.10. Just go to the mythbuntu site, go to the downloads, and expand the 'historical downloads' section.

---

### Post by Symbiot78 on 2010-03-17
> **SiHa said:**
> Sorry thought you meant you'd had a play with it under vmWare and were now going for a proper install.

No Worries.. I am not yet ready to do a full step into Linux.
I have decided to learn learn learn first..

---

### Post by Symbiot78 on 2010-03-17
> **timconradinc said:**
> If this is all you're using it for, perhaps try an older release of mythbuntu? I'm pretty sure it worked in 8.10. Just go to the mythbuntu site, go to the downloads, and expand the 'historical downloads' section.

Thanks, I am downloading it as I type.

Do you mean to say that it(mythstream) is already functionel under 8.10?
or that it still needs to be installed ?

---

### Post by timconradinc on 2010-03-17
I think it comes already installed, or it's available as a package, any ways.

I'm pretty sure that's what I recently upgraded from and it was there. If not, try the next older one - sorry for my foggy memory.

---

### Post by techstop on 2010-03-17
> **Symbiot78 said:**
> Thanks, I am downloading it as I type.

Do you mean to say that it(mythstream) is already functionel under 8.10?
or that it still needs to be installed ?

I wouldn't go back to 8.10. 9.04 was the last version with mythstream in the ubuntu repo;

[http://packages.ubuntu.com/jaunty/mythstream](http://packages.ubuntu.com/jaunty/mythstream)

You could always try these instructions here for compiling mythstream on 9.10;

[http://dougaus.blogspot.com/2009/12/installing-mystream-on-mythbuntu-910.html](http://dougaus.blogspot.com/2009/12/installing-mystream-on-mythbuntu-910.html)

There's some related instructions on these forums too to fix a minor install niggle;

[http://ubuntuforums.org/showthread.php?t=1369412](http://ubuntuforums.org/showthread.php?t=1369412)

---

### Post by lank23 on 2010-03-17
You should look at MythNetvision  [http://www.mythtv.org/wiki/MythNetvision]("http://www.mythtv.org/wiki/MythNetvision").

It is due to be released with Mythtv version 0.23 even though it is beta works pretty well.

Get the *.debs here. [https://launchpad.net/~mythbuntu/+archive/0.23/+packages]("https://launchpad.net/~mythbuntu/+archive/0.23/+packages")

---

