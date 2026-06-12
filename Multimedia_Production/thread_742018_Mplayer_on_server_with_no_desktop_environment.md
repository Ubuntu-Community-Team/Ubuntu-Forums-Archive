---
title: "Mplayer on server with no desktop environment"
date: 2008-04-01
forum: Multimedia Production
---

### Post by Rizla on 2008-04-01
I was wondering if anyone has tried this sort of setup.  I'm setting up a NAS server that will primarily host my dvd's and xvids.  I plan on watching most of the movies on either my other pc or xbox, but wanted to know if its possible to install mplayer on the server and still be able to watch dvd's.  I dont have a GUI desktop like gnome or kde installed, are those necessary for mplayer?

Along the same lines, does anyone have a recommendation for a lightweight desktop.  Something basic, I dont want the bloat of gnome or kde on it.  I read a little about xubuntu, would that be what im looking for?

---

### Post by stefangr1 on 2008-04-01
No, you don't need a desktop manager to run mplayer. All you need to install is xorg (for reasons all to obviously).

What a good lightweight desktop environment is depends on your system specs, Xubuntu is very mucht like gnome but needs less recources, maybe it's something for you.

---

### Post by aeiah on 2008-04-01
im a little confused. by 'want mplayer on the server' do you mean on the NAS? does this NAS have a screen attatched or are you wanting to stream video?

and mplayer can run without a desktop environment, but it still needs X i do believe. its probably easier to install a lightweight desktop or windowing environment though, like fluxbox, openbox, icewm etc. or xubuntu of course, although that is a little heavier (and easier to use in my opinion)

---

### Post by Rizla on 2008-04-01
> **aeiah said:**
> im a little confused. by 'want mplayer on the server' do you mean on the NAS? does this NAS have a screen attatched or are you wanting to stream video?

and mplayer can run without a desktop environment, but it still needs X i do believe. its probably easier to install a lightweight desktop or windowing environment though, like fluxbox, openbox, icewm etc. or xubuntu of course, although that is a little heavier (and easier to use in my opinion)

Resource wise, this server is diesel.  2GB RAM, NVIDIA GeForce 7150 (onboard), 1.5TB raid5, Quad Core 2.4Ghz, 1Gb NIC (integrated)

Currently i have it set up to a kvm  so it has a monitor.

given that it can handle most things, i still want to keep it with a light foot print.  So i want a light GUI for the desktop.

How do i setup x by itself?  whats the package that i shoudl download via apt-get or (aptitutde *whats the diff anyway?*)

Last question, can you forward x via ssh?  Hypothetically I want to be able to test my dvd's and xvids remotely if need be (i know it will be bandwith intensive).

I think thats all, thanks for taking the time out to respond.

---

### Post by aeiah on 2008-04-01
maybe im just having an idiot day but i dont really understand why you want to play movies on a server. why dont you look at a streaming solution? vlc can stream from a host to a client, for instance

---

### Post by stefangr1 on 2008-04-01
Since this is the Ubuntu forum I'm assuming that you have Ubuntu server edition. You can just install X by typing:

sudo apt-get install xorg

then after running startx you will get a console that looks a little different. From there you can execute mplayer movie.avi etc.

Maybe however, it is more user friendly to install a desktop interface that is not started by default. Then if you want to do some non server tasks ocasionally, you just start the interface and close it after you're finished.

It's not possible to use x-forwarding to watch a dvd, since that will almost certainly demand more upload speed then you have.

---

### Post by Rizla on 2008-04-01
> **aeiah said:**
> maybe im just having an idiot day but i dont really understand why you want to play movies on a server. why dont you look at a streaming solution? vlc can stream from a host to a client, for instance

I'm not so sure why I want to do it either, but just so that when i rip some dvd's i can test them locally on the server.  Dumb i know, but why not.

---

### Post by Rizla on 2008-04-01
> **stefangr1 said:**
> Since this is the Ubuntu forum I'm assuming that you have Ubuntu server edition. You can just install X by typing:

sudo apt-get install xorg

then after running startx you will get a console that looks a little different. From there you can execute mplayer movie.avi etc.

Maybe however, it is more user friendly to install a desktop interface that is not started by default. Then if you want to do some non server tasks ocasionally, you just start the interface and close it after you're finished.

It's not possible to use x-forwarding to watch a dvd, since that will almost certainly demand more upload speed then you have.

Alright, just installed xorg.  I'm currently ssh'ed remotely so i cant test it out until later.

WHats a good desktop interface that isnt bloated like gnome or kde?

One other note, seeing that this will be my encoding server as well for ripping/transcoding dvd's, what is an easy to use CLI ripper?  dvdbackup?  I'm used to k9copy, which is a nice easy to use gui, but since its a bare bones server, no k9copy.

---

### Post by aeiah on 2008-04-01
ahhh i get what you mean now. i thought by watching the rip you meant actually sitting down and watching it, but you just mean viewing a few seconds to see if its done it more or less. well yes, you can install xorg and run it with the command as mentioned, or install something like fluxbox. most dvd rippers for linux will run on CLI backends, so yes, you can use them with the command line. i dont rip dvds very often so i cant think of one off the top of my head, but i believe if you use acid rip, you can see what commands it is going to use and you can reuse those commands later

edit:

although k9copy is like a dvd shrinking app and not like acidrip, which converts to avi, so you'd have to find out what k9copy does behind the scenes i guess, or find a tutorial for that kinda thing

---

### Post by Rizla on 2008-04-01
> **aeiah said:**
> ahhh i get what you mean now. i thought by watching the rip you meant actually sitting down and watching it, but you just mean viewing a few seconds to see if its done it more or less. well yes, you can install xorg and run it with the command as mentioned, or install something like fluxbox. most dvd rippers for linux will run on CLI backends, so yes, you can use them with the command line. i dont rip dvds very often so i cant think of one off the top of my head, but i believe if you use acid rip, you can see what commands it is going to use and you can reuse those commands later

edit:

although k9copy is like a dvd shrinking app and not like acidrip, which converts to avi, so you'd have to find out what k9copy does behind the scenes i guess, or find a tutorial for that kinda thing

I was actually using k9copy to rip to ISO, no compression.  At least I assumed it was no comprression because some of my rips were over 4GB's.  I edited the DVD settings and set the max file size to 8GB (highest it would allow).

Anyhow as far as this thread goes, i think i'm set.  Now that i've got xorg installed i can use mplayer to preview my rips, or watch them if I wanted to.

Thanks for your help guys.

---

### Post by eriqjaffe on 2008-04-01
As far as a lightweight gui goes, I'd recommend Openbox or Fluxbox.

---

### Post by stefangr1 on 2008-04-01
You could use mencoder to do this. Especially if you make some scripts for the often occuring tasks, it's not very difficult to use from the commandline.

---

### Post by Rizla on 2008-04-01
> **stefangr1 said:**
> You could use mencoder to do this. Especially if you make some scripts for the often occuring tasks, it's not very difficult to use from the commandline.


so mencoder can do the ripping by itself?  I just wnat something to do an ISO rip to the drive.

---

### Post by stefangr1 on 2008-04-01
Well, it can't really rip the dvd. It's just for if you want xvid or h264 avi files. But shouldn't the ripping be done while you're present anyway, I mean you'd have to put the drive in etc... 

Normaly I just mount the dvd player, then copy the movie from the disk to my hdd with a command like:

cat file1.VOB file2.VOB file3.VOB > movie.mpeg

and then let mencoder work on it for some hours to get a nice .mkv file with very little quality loss that needs only 25% of the disk space.

---

### Post by Rizla on 2008-04-01
You're right about the whole doing it remotely, i still need to be present to do so.  I'm looking for a app that rips and decrypts the dvd (if ncessary) that can be done from the command line.

The way you do it by just copying the files over seems ok, but i want a program that will cut all the crap and just give me the main movie and the sound stream with the most channels.  Ideally convert it to .iso as well, but no biggie i can use mkisof afterwards if need be..

i've been using K9Copy for the majority of my rips and its been working great, but i want something on the server to do so (its 64 bit also)

---

