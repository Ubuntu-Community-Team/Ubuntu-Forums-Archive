---
title: "Playing MP3's over a network"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by Underpants on 2007-01-02
Using 6.10 

I need to mount a windows share to my ubuntu desktop. There are two ways of achieving this. 

1.“places” and then “connect to server”
This works well. I can read and write where I need to, the mount comes back after a reboot. Looks really good. However, I can't stream mp3's from this location. The files must first be moved to the local hard disk for playback. Searching around shows that this is an issue with 6.10

2.Oldschool “smbmount” Here's the command I'm using
```

 sudo mount -t smbfs -o username=aaron,password=foobar //bluebox/bluebox-data /home/aaron/Desktop/bluebox-data

```

The mount works and I can play mp3's and videos directly from this mount, except I don't think that R/W is working properly. All of the folders have the padlock icon on them. Typing 'mount' in the terminal shows that the share is mounted in Read/Write mode

```

//bluebox/bluebox-data on /home/aaron/Desktop/bluebox-data type smbfs (rw)

```

So, what the hell is going on? Number one I can't stream files over the network. Number two won't let me make any changes. WHO DOES NUMBER TWO WORK FOR!? /end joke.

Seriously. 

Thanks!

---

### Post by Underpants on 2007-01-02
OK. The problem with #2 has something to do with not have super user rights on my ubuntu desktop.  If I open &#8220;sudo gedit&#8221; from the terminal and create a text file, I can save it anywhere on my mounted media. 

WTF.

---

### Post by jzlharvey on 2007-02-05
I can't stream my music from a share that I have rights to either.  I can bring the file over locally and get it to play in totem or xmms... but when it comes to streaming it over the lan it will not play.  Any idea?

---

### Post by Underpants on 2007-02-05
> **jzlharvey said:**
> I can't stream my music from a share that I have rights to either.  I can bring the file over locally and get it to play in totem or xmms... but when it comes to streaming it over the lan it will not play.  Any idea?


[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by jzlharvey on 2007-02-05
Underpants; thanks for the reply.  I have this share mounted already .. I used the places>connect to server GUI.  The share is shown on my Desktop

Do I need to do it another way?

---

### Post by docshawnc on 2007-02-07
Hi -
    There is an issue with streaming files over a samba network with xmms.  Try using sshfs and you will find that you can play mp3s on other network machines with xmms.

This drove me nuts too until I stumbled across the answer

---

### Post by jae1227 on 2007-02-10
I have tried all the stuff above and still no luck. I have all my MP3s on my windows box being shared. All my other windows boxes can stream from it but my Linux box using XMMS, or anyother player, can not steam. It just displays the title of the song and won't play.  I can however drag it from the shared location to my hard drive and it plays fine. I really want a way to do this in the GUI. I tried the smbmount but I don't have that commend. I tried ```
sudo apt-get install smbmount
``` and no luck still.

---

### Post by Underpants on 2007-02-10
> **jae1227 said:**
> I have tried all the stuff above and still no luck. I have all my MP3s on my windows box being shared. All my other windows boxes can stream from it but my Linux box using XMMS, or anyother player, can not steam. It just displays the title of the song and won't play.  I can however drag it from the shared location to my hard drive and it plays fine. I really want a way to do this in the GUI. I tried the smbmount but I don't have that commend. I tried ```
sudo apt-get install smbmount
``` and no luck still.

Dude, you have to read this post. 
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

It needs to be mounted up as root, and in the command line it give your user account access to R/W the files.

---

### Post by Underpants on 2007-02-10
Here's what I use.

```

sudo smbmount //blueboxen/bluebox-data /home/aaron/Desktop/bluebox-data -o credentials=/home/aaron/.smbpasswd,uid=aaron 0 0

```

.smbpasswd is my password file.

---

### Post by blazemiskulin on 2007-02-21
I'm having a similar problem with my NAS.

It's permanently-mounted.   I can access it, view it, transfer files--all with no problems.

However, if I try to save a torrent directly to it, the mount "breaks" [1]  If I try to play mp3s from it (in either Songbird or Amarok), the mount "breaks".   I got about half of a song to play in Amarok before it locked up.   I run several boxen in the house, so having a central file server for music and videos is rather important to me.

I use networked drives (primarily NAS) extensively, and this is one of the largest issues standing in the way of me migrating to Ubuntu on my primary box (these problems are occurring on my "learning" box).  Any help and/or pointing in the right direction for research would be greatly appreciated.

I've been working with computers for over 25 years and have a fair amount of experience and knowledge (I still look back at DOS with a wistful gleam in my eye), but I'm an absolute noob in regards to linux.   I'm trying!  I really am!  I just keep running into the "old dog/new tricks" hurdle.  ;)


For reference:
Ubuntu 6.10
Dual-core AMD Athalon 1.8GHz
Simpletech NAS (It also happens with my Buffalo Linkstation)
Hard connection (no wireless)
Actiontec router and Linksys switch


[1]"breaks" = the connection to the NAS is lost, and the file browser locks up (presumably because it's trying to read the mapped drive).

---

