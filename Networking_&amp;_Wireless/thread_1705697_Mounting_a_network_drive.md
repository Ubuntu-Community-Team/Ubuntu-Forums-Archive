---
title: "Mounting a network drive"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by jstnhickey2 on 2011-03-12
I have tried to follow other tutorials, but my linux knowledge is pretty limited.  I have never mounted a drive in anyway and know nothing about networking in linux.

I have a Western Digital Live TV Box on my wireless network, connected to that is a harddrive.  If I use the gui to browse folders I can go to Network - Windows Network - Workgroup - WD - Elements.  From there I can browse in elements and see and open files.  
My problem though, I think, is mounting this elements folder.  I use this drive for media and would like to be able to add it to rhythmbox or some other media player as a library.  If I try to add it now it will find a few files, then it will stop and say that other files are not accessible. 

How do I make it so this drive is always accessible and so that a media program can use it as a library?  

I'm not sure if I am phrasing this question correctly, but I can try to explain more if needed.

---

### Post by thunderbirdje on 2011-03-12
I'm not sure if I can help you further but in my network disk's case I can setup some shares who maps to my media folders. 

For example I can make a share called 'bt' mapped to my broadcasted library 'videos'. Or a share called 'digital-pictures' mapped to a library called 'pictures'. 

In my case I have not a expensive media player so I can't connect to them via any program. But maybe in you case it's the solution?

---

### Post by Morbius1 on 2011-03-12
You actually have two questions:
 > If I use the gui to browse folders I can go to Network - Windows  Network - Workgroup - WD - Elements.  From there I can browse in  elements and see and open files.  My problem though, I think, is mounting this elements folder.It actually is mounted. The mount point is in your home directory:
```
/home/user-name/.gvfs/share-name on server-name
```Note the .gvfs - it's a hidden directory.
>  How do I make it so this drive is always accessible and so that a media program can use it as a library?  If you're talking about automounting it and you're OK with the hidden directory then I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

[COLOR=Blue]EDIT: Forgot something.[/COLOR]
Some applications don't take kindly to things in hidden directories. One way around this is to create a symbolic link from the hidden to a non-hidden directory. For example, if I have a remote share named "music" on server "Elements" then I would create a symlink:

Create a non-hidden directory for the Elements' music share:
```
 mkdir /home/morbius/EMusic
```Then create the link:
```
ln -s /home/morbius/.gvfs/"music on elements" /home/morbius/EMusic
```

---

### Post by jstnhickey2 on 2011-03-14
thanks I created a link to it in my home folder, so far so good, rhythmbox seems to be reading and finding everything.

---

### Post by jstnhickey2 on 2011-03-29
Just noticed that the .gvfs folder does not always have the network drive listed.  I have to go to "network" then click on the drive for it show up again.  Any ideas?

---

### Post by collisionystm on 2011-03-29
I know you have looked at a few tutorials. but this one here is very simple.

[here]("http://cri.ch/linux/docs/sk0001.html")

---

### Post by Morbius1 on 2011-03-30
> **jstnhickey2 said:**
> Just noticed that the .gvfs folder does not always have the network drive listed.  I have to go to "network" then click on the drive for it show up again.  Any ideas?
> **Morbius1 said:**
> If you're talking about automounting it and  you're OK with the hidden directory then I would suggest **[COLOR=Blue]Gigolo[/COLOR]**: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Give Gigolo a shot if you want to mount the network drive on boot. It will even wait for the drive to be turned on before it attempts to mount.

---

### Post by jstnhickey2 on 2011-04-03
thanks.  It looks like my media box that my hard drive is connected to may have updated firmware because the issue was that it's name in the .gvfs file was slightly different instead of "elements on wd" it was something like "elements on wdlive".
Things seem to be working and I'm using gigolo and the other method posted.

---

