---
title: "How to play music/video from server to Stereo?"
date: 2008-05-27
forum: Multimedia Software
---

### Post by antechinus on 2008-05-27
Need to work out the best way to play sound and video from Ubuntu server. Let me say at the outset, I am a complete newbie to this.

I have a networked server running Hardy Heron with no GUI. This machine is intended to act as a file server, music and video player as well as a few other applications. It is a quiet, low power box with a VIA C7™ processor that will sit with the stereo gear. It has video/sound output that I will plug into the TV.

The server will only be accessed via Windows machines using Putty or applications that use web-browser interface.

Now, I would like to play music & video from the server into the stereo system, but control the song selection/playlist via a web browser on a networked Windows machine.

How does one go about doing this?

So far I have set up networking and the server runs Samba. It has the LAMP apps installed.

---

### Post by antechinus on 2008-05-29
Should I have put this question in a more general forum?

---

### Post by jethro10 on 2008-05-29
I think most people would not link the PC to the TV but use a media streamer front end hardware box (neuros would work) then pull data off your server by using Upnp for instance.
The PC would then run something like Meidatomb or Twonkyvision media server s/w.

I Think to use it direct to a TV, you need a GUI, which you say you havn't got/Dont want?.

Installing lets say, gnome and Myth TV would be a way to do it with the box being directly connected to the TV assuming your TV has a PC-In socket or your graphics card has TV out perhaps.

Does this make sense or have I missed the point?
Jeff

---

### Post by antechinus on 2008-05-29
I want the server to be part of the stereo system - a headless box that stores the music and plays it straight to the stereo. It can then be remote controlled by another machine in the house (wireless Windows laptop) via browser.

There is no need for streaming.

I have just stumbled across MPD [http://www.musicpd.org/](http://www.musicpd.org/) ,which looks promising. And it can be administered via browser.

Anyone have any experience with MPD?

---

### Post by OpenFish on 2008-05-29
i am using a networked box to play music as my new pc's sound card is being cussid !!

i use ssh and 
```
vlc -I Dummy relitive/path/to/File.mp3
```

this is not very setisfing but vlc has a web interface so u can replace dummy with a dirent argument then point ur browser at the box with a spesicic port and Vala u have a crud Gui

just google 'vlc command line interface ' or some thing to that effect

if it was me i would add mysql to my sever and us pygtk to add songs to a data base and use an init on the box to get python to play the music on the data base but i have to much time on my hands and an unhelthy love of python !:) !

atualy thats a good idea i may have to do some playing !!!

---

### Post by OpenFish on 2008-05-29
sorry realy shold read post properly befor i post 

u have all of a lamp so instad of pygtk u could use a php scipt to brows and add to the data base and then use python to play the stuff
(id use python as it is easy to install and modif ur script with out any compilers i do us compilers but we dont get along)
again a little ahead of my self (i love open stuff)

that would mean u wouldn't need to install anything and when ur freand come round there wireless laptops could just point at ur page and VALA the power of ice weasel and python !!

again vlc would be more sence and with a web gui probably what u want 

by the way u could use init to set it off so on reboots u dont have to tuch it

---

### Post by paulsdavies on 2008-05-29
I do exactly what you describe...

Check out the Sqeezebox - [www.slimdevices.com](www.slimdevices.com) - I think this is what you are looking for - a headless, wireless or wired device (audiophile quality) which connects to your stereo.

The Squeezebox receives a stream from a piece of software called SqueezeCenter, which runs on your Unbuntu box. You can control it (if you wish) through a web interface from a Windows machine.

---

### Post by antechinus on 2008-05-29
> **paulsdavies said:**
> I do exactly what you describe...

Check out the Sqeezebox - [www.slimdevices.com](www.slimdevices.com) - I think this is what you are looking for - a headless, wireless or wired device (audiophile quality) which connects to your stereo.

The Squeezebox receives a stream from a piece of software called SqueezeCenter, which runs on your Unbuntu box. You can control it (if you wish) through a web interface from a Windows machine.

Squeezebox looks good, but is an expensive option. Anyway I already have the headless box sitting with my stereo. All I have to do is get the software.

What do you mean by "I do exactly what you describe"? Do you use MPD?

I want to know if MPD is the way to go, and what is the best client to run it from a windows machine - using browser.

---

### Post by paulsdavies on 2008-05-30
I didn't mean that I use MPD - Just that I store my music on a Linux box, stream it my my stereo and control it from a Windows box.

The software that the Sqeezebox would use on the Linux server is open source, and supports other players and various standards - I don't know details as I have not used it this way. But it may well work with your device.

---

### Post by yousillygoose on 2008-05-30
I wouldn't mind setting up the same thing :).  I have an extra server in my house that I would like to plug into a tv and stereo system so that I can control it through a laptop.  I believe this is what the thread creator is trying to do.  I as well would want to do it in an inexpensive way.  Thanks

---

### Post by yousillygoose on 2008-06-01
bumpity bump bump

---

### Post by antechinus on 2008-06-01
Well, I have decided to go down the MPD path. My small headless linux server is connected to stereo system and networked. I have downloaded and unpacked latest MPD, libao, libid3tag, zlib, audiofile, madplay and ampache onto the server.

Now the hard part. Trying to install it all.

---

### Post by mcduck on 2008-06-01
> **antechinus said:**
> Well, I have decided to go down the MPD path. My small headless linux server is connected to stereo system and networked. I have downloaded and unpacked latest MPD, libao, libid3tag, zlib, audiofile, madplay and ampache onto the server.

Now the hard part. Trying to install it all.

Why not install it from the repositories? Downloading stuff and installing by hand really isn't the way to do things in Linux..

And yes, MPD is most likely exactly what you are looking for, although I can't tell anything about those browser-based clients as I haven't tried any.

---

### Post by yousillygoose on 2008-06-01
my main problem with this issue stems from hardy having trouble working with svideo cables.  I have done a lot of hard work to get my svideo cable to work and i fail every time.  Would there be another way to connect a computer to a tv other than via svideo to accomplish the media center.

---

### Post by antechinus on 2008-06-20
An update for other who may wish to do the same. 

Using MPD with Pitchfork was successful and the set-up is working very well. I can play mp3s through my stereo and control playlist remotely via any machine on the network. Just what I wanted.

I installed MPD and Pitchfork from repositories. Had a problem working out how to configure pitchfork - [solution here]("http://www.musicpd.org/forum/index.php?topic=1624.0"). Updated soundcard driver, restarted Ubuntu and all worked.

---

### Post by cariboo on 2008-06-21
For music if your going to connect to yor stereo any command line music player will work. It just depends on how complicated you want to get, mpg321 is a great command line music player, but it is pretty basic. My self I use gnump3d but it streams music to other computers, and I stream video using a web interface.

Have you considered setting up a MythTv server. have a look at it at here:

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

Jim

---

### Post by OpenFish on 2008-06-23
if u are using a CRT tv then svideo is ur best bet i think! but if its a plasma/lcd then ur DVI/vga cable will do the trick as well (if ur tv has apropriate imputs most flat HD-tvs do) but is also intresting to set up:) not don it my self but lots of example of poeple on the forum having ishus with tv resolutions remember vga only suports somany pixels so u will have poor pic quolit at hi def with vga cable no mater the quolity of graphics card or tv thats why they invented DVI-D (well that or they wonted to make things even more complicated!!)

---

