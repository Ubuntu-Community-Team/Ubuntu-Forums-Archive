---
title: "media streaming software"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by quickshot89 on 2007-11-10
so ive built my server, installed apache for when i get my wepages built, but i want to be able to stream music, ive tried installing the apache mod, but it wont install, but it says i cant install apache common

so i tried to install ample, but i have no idea how to connect or start it

anyone know how to do this, 

so, to sum it up

i have ubuntu
it has my music on there
i want to be able to create a radio / msic streamer on it
im stuck

help!

---

### Post by dfreer on 2007-11-10
I use gnump3d for streaming music with media players that support .m3u files across the internet, and I use firefly mt-daap server for streaming music to iTunes and Rythmnbox clients on my LAN.

---

### Post by quickshot89 on 2007-11-10
ok, my music files are mp3 and some wma

does gnump3d allow for them?

edit: installed gnump

now what do i do?

---

### Post by dfreer on 2007-11-10
Ok, after install gnump3d, you'll need to specify which directory contains your music files. Edit your /etc/gnump3d/gnump3d.conf and change the default directory option.
It'll scan it recursively, so it doesn't matter if you have them in folders or not.

To start gnump3d for the first time, I think you need to run this command:
```
sudo gnump3d --background
```
It should then proceed to scan your directory for music files, and after it's done running, the dameon should be running each time your server restarts. You can browse the files by pointing your browser to:
[http://**your_domain_name_or_IP_address](http://**your_domain_name_or_IP_address)**:8888

Since the playback of the files is soley dependent on the client, MP3's will be detected and should work on any computer with the codec's to play them. WMA's should too, but if they aren't detected by gnump3d at first, you'll probably just need to add the wma extension to your /etc/gnump3d/gnump3d.conf file.

I'm not really an expert at gnump3d, as I've had my own struggles with the software.

---

### Post by quickshot89 on 2007-11-10
cheers for the info

i tried to edit the file, but when i click save it wont let me

my servers path to the music is smb://file-server-1/File_Server/Music

so i guess the root is /file-server-1/File_Server/Music right????

so any ideas how to get it to save

im guessing it could be because im running the server remotly, as i cant spare any output devices on it (dont have any tbh, lol)

---

### Post by xyphur on 2007-11-10
I have no experience with gnump3d, but I'm assuming because it's a conf file, you need root credentials to write to it.

sudo nano /etc/gnump3d/gnump3d.conf

or

gksudo gedit /etc/gnump3d/gnump3d.conf

---

### Post by quickshot89 on 2007-11-10
cheers, i think i have it done now, just got to get it to rescan for files, it wouldnt matter if everything is in folders?

edit: got the folder changed, it was located in home/public..... not file server lol

now its saying the listening port is being used, so ive closed everything down, and still no luck :(

just this to go :(

---

### Post by quickshot89 on 2007-11-10
bump

---

### Post by dfreer on 2007-11-10
Check your /etc/gnump3d/gnump3d.conf to see what port it is using, and then check which ports are in use with this command (this should list them all):
```
netstat --numeric-ports | grep tcp
```

EDIT: You may need to stop gnump3d the first time, now that I think about it:
```
sudo /etc/init.d/gnump3d stop
```

Then run your update command (after this, it should update automatically):
```
sudo gnump3d --background
```

---

### Post by quickshot89 on 2007-11-11
cheers for the info, everything works now :)

edit: one thing, how do you disable the download links on the pages, i want stream only, and i cant find anything in the conf file

---

### Post by dfreer on 2007-11-11
With gnump3d, I dunno if you can. Check the official site:
[http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

Sorry, can't help you with this one. There are several other streaming media servers, unfortunately other than Firefly I don't have any experience with them.

---

