---
title: "MPD --create-db / install"
date: 2012-08-16
forum: Multimedia Software
---

### Post by BugFixBug on 2012-08-16
Hello,

I was looking for using my local servers to play music ( from the actual server itself not streaming it to other pc's) . After some googling i found MPD . i followed all instructions on installing. I now have mpd and mpc installed. But in the instructions (in every howto i found) it says i need to execute the following command: 
sudo mpd --create-db

the problem is i am getting the an error:
** (mpd:1708): CRITICAL **: option parsing failed: Unknown option --create-db

I have no clue on what is wrong and how to get it to work... so any help would ba appreciated

---

### Post by albandy on 2012-08-16
> **BugFixBug said:**
> Hello,

I was looking for using my local servers to play music ( from the actual server itself not streaming it to other pc's) . After some googling i found MPD . i followed all instructions on installing. I now have mpd and mpc installed. But in the instructions (in every howto i found) it says i need to execute the following command: 
sudo mpd --create-db

the problem is i am getting the an error:
** (mpd:1708): CRITICAL **: option parsing failed: Unknown option --create-db

I have no clue on what is wrong and how to get it to work... so any help would ba appreciated

Did you installed mpd from repositories?

---

### Post by BugFixBug on 2012-08-16
> **albandy said:**
> Did you installed mpd from repositories?

yes. i used apt-get install mpd mpc

---

### Post by albandy on 2012-08-16
> **BugFixBug said:**
> yes. i used apt-get install mpd mpc

Have you configured /etc/mpd.conf ?

---

### Post by BugFixBug on 2012-08-16
I only changed the music directory

[http://pastebin.com/PdEK4cPp]("http://pastebin.com/PdEK4cPp")

---

### Post by albandy on 2012-08-16
> **BugFixBug said:**
> I only changed the music directory

[http://pastebin.com/PdEK4cPp]("http://pastebin.com/PdEK4cPp")

change the port, I've readed here [http://ubuntuforums.org/showthread.php?t=1428619](http://ubuntuforums.org/showthread.php?t=1428619) that some times it can be a problem.

---

### Post by BugFixBug on 2012-08-16
Tried but doesn't help

---

### Post by albandy on 2012-08-16
in /etc/mpd.conf disable the line bind_to_address localhost. To disable it add a "#" at the beggining of the line.

#bind_to_address localhost

---

### Post by BugFixBug on 2012-08-16
Also tried that from the ohter post. But this gives a error:

 * Stopping Music Player Daemon mpd                                                                                                                                                                [ OK ] 
 * Starting Music Player Daemon mpd                                                                                                                                                                       listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)


also tried:

bind_to_address		"/var/run/mpd/socket"

but still get the unable to parse option error

---

### Post by albandy on 2012-08-16
I'm doing the test in 10.04 what version are you using?

---

### Post by BugFixBug on 2012-08-16
12.4

---

### Post by BugFixBug on 2012-08-16
found this.

[http://mpd.wikia.com/wiki/Music_Player_Daemon_Database_Updating](http://mpd.wikia.com/wiki/Music_Player_Daemon_Database_Updating)

got it working now.... thanx for your help

---

