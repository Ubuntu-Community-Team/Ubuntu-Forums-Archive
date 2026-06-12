---
title: "Can't get MPD to start...port 6600 trouble"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by rggavubt on 2007-02-22
I installed Music Player Daemon..MPD and when I try to run it I get the following message :

unable to bind port 6600: Address already in use
maybe MPD is still running?

I went to the MPD website forums and could not figure out how to fix this problem...any help would be appreciated.

---

### Post by rggavubt on 2007-02-22
> **rggavubt said:**
> I installed Music Player Daemon..MPD and when I try to run it I get the following message :

unable to bind port 6600: Address already in use
maybe MPD is still running?

I went to the MPD website forums and could not figure out how to fix this problem...any help would be appreciated.

I was reading the forum at the MPD web site and it said the following :

you have a "bind_to_address" specified.  Does the computer running mpd actually have that ip configure on one of the eth*?

They then said I would have to edit the mpd.conf file and take out the IP address for port 6600.  How do I do that?  What terminal commands will I have to enter to edit the mpd.conf?  I don't know what directory it is in?

---

### Post by rggavubt on 2007-02-22
I was reading and found that I could use "locate filename | less" as a terminal command to find the file.  The mpd.conf file is in /etc directory.  I checked out the file and under security settings the "bind_to_address' is entered as "local host".  I think this is the problem and need to delete this entry.......help

---

### Post by rggavubt on 2007-02-22
> **rggavubt said:**
> I was reading and found that I could use "locate filename | less" as a terminal command to find the file.  The mpd.conf file is in /etc directory.  I checked out the file and under security settings the "bind_to_address' is entered as "local host".  I think this is the problem and need to delete this entry.......help

Now I have figured out how to edit this file but I don't know what to enter as my "bind to address"  I tried "any" and that didn't work??  Stumped!  I also tried the IP address of my router and that didn't work either.

Pretty Soon I will figure this thing out by myself if no one answers my post.

---

### Post by rggavubt on 2007-02-25
I found out that mpd was already running and this is not a problem.  I used "sudo killall mpd" to stop it running and was able to do some of the commands listed in the how to that is posted on the forum.  I also was told by someone to use "man mpd" to see all of the commands for mpd.  The how to listing by JMO707 shows a "sudo mpd -create -db" command which should read db "sudo mpd --create -db"  That missing dash created lots of headhaches!

---

### Post by gonzo_cotto on 2007-07-18
Well, like almost every deamon you can always do:

```
sudo /etc/init.d/mpd stop [or start] [or restart]
```

If you receive the message saying a server/deamon is already running, well it is already running!!! I don't understand if you want to access mpd from another client or not... if you want to hear your music "locally", that means, hear the music in the same computer where the deamon is, leave 

```
bind_to_adress     "localhost"
```

If you want to access and hear the music from other clients (i.e. other computers), then you will have to change it accordingly (I believe it depends a lot on where the client lays: LAN or WAN, but I don't really remember), the MAN pages will tell you which options you have...

i wish you lots of fun hearing your music

:guitar:

---

