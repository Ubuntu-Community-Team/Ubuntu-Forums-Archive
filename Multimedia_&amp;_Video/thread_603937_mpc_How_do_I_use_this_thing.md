---
title: "mpc: How do I use this thing?"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by desklamp on 2007-11-05
I am looking for a small music player that runs in terminal.  And I was suggest this by many.  But I am having a hard time trying to get this thing to work.

```
mpc add song.foo
```
does not add the song to the list.

```
mpc ls
```
does not list the songs in the current directory.

---

### Post by trak87 on 2007-11-05
There are two separate parts to this program and you must have both installed, the server and the client. There's one server and many client programs. MPD is the server and you must install that and set it up. What you've installed, MPC, is a text based ***client*** program.

So just install mpd, the server part of it. Then edit /etc/mpd.conf and give the *music_directory* parameter the correct path to your music files. Save and exit. Then restart mpd (sudo /etc/init.d/mpd restart). Then you want to index your music collection with *sudo mpd --create-db* .

At this point you should be ready to listen to music with mpc, or any other mpd client. Sonata is good for gui use.

---

### Post by mali2297 on 2007-11-05
You can also see these tutorials:
[http://ubuntuforums.org/showthread.php?t=31763](http://ubuntuforums.org/showthread.php?t=31763)
[http://ubuntuforums.org/showthread.php?t=320469](http://ubuntuforums.org/showthread.php?t=320469)

---

### Post by trak87 on 2007-11-05
That first link is two years old, and the second link talks about compiling the program which is unnecessary today. These links are not at all helpful. 

It's simple. Just install mpd and configure it by telling it where your music is. Then install an mpd client (mpc, sonata, pympd, etc). And away you go.

Just to be clear, mpd will start automatically when you start your computer. Then just run the client program whenever you want to listen to music.

---

### Post by desklamp on 2007-11-05
I need some help.  For some reason I can not get the mpd to work.

```
$ sudo /etc/init.d/mpd restart
Stopping Music Player Daemon: mpd.
Starting Music Player Daemon: Avahi: Failed to create client: Daemon not running
mpd.
```

---

### Post by trak87 on 2007-11-05
I don't know what causes that. You might try rebooting and then see if mpd is running with 

```
ps aux | grep mpd
```

You should see something like this:

```
mpd       7480  0.0  0.1  10844  1944 ?        S    18:35   0:00 /usr/bin/mpd /etc/mpd.conf
```

---

### Post by trak87 on 2007-11-05
Try this:

```
sudo /etc/init.d/avahi-daemon restart
```

and then try to restart mpd.

---

### Post by desklamp on 2007-11-05
mpd looks like it is running.

As for the other:

```
sudo: /etc/init.d/avahi-daemon: command not found
```
Is this avahi thing a dependent of mpd?  If so, it should have been installed along with it when I installed mpd via apt-get.

---

### Post by aidanr on 2007-11-05
It's recommended by mpd, if you right click mpd in synaptic and go to mark recommended for installation.

---

### Post by desklamp on 2007-11-05
I read that mpd can be used via a network.  This avahi-daemon thing must be it.

However, I do not plan to use use it via a network.  I am only planning on using it on this computer.  Therefore, it does not matter if I have it, right?

So the mpd daemon seems to be running.  I have ~/myaudio in the ~/.mpdconf.  But when I "mpc ls" nothing gets listed.

Even after rebooting.

What am I missing here?

---

### Post by aidanr on 2007-11-05
Try:
mpd --create-db
mpc update
mpc ls

---

### Post by desklamp on 2007-11-05
```
$ mpd --create-db
cannot init supplementary groups of user "desklamp" at line 35: Operation not permitted
```

I left it as the default "mpd", but that did notwork.  I changed it to my username, and that did not work either.  What is suppose to be in there?

---

### Post by daengbo on 2007-11-05
Can I be blunt? If you are not going to use MPC over a network, it's kind of a waste.

I use it because I have a central server in the house with all the music. MPD runs on it and shares music to Rhythmbox on each of the client PCs. If I had an iPod or iTunes, the daemon would also share to that, but I'm not that sophisticated. My MythTV box will eventually support DAAP (the protocol iTunes uses). This is what MPD/MPC is for.

If you are only using one box, there's no need for a server/client architecture. You'll be better off using another client. There are a million of them, but I suggest Rhythmbox for Ubuntu and Amarok for Kubuntu because they're the officially supported applications, and you'll get better-tested software. Answers on the forum will probably be easier to find, as well.

That said, I think the Avahi link can be turned off in etc/mpd/mpd.conf. Use "sudo gedit" to edit it. Or just comment the zeroconf_name setting in ~/.mpdconf.

Best of luck.

---

### Post by aidanr on 2007-11-05
Huh, maybe it's because you're running mpd as root, try

sudo killall mpd
mpd
mpd --create-db

If that works and you want mpd to start up with the computer add it to your session startup programs and remove /etc/init.d/mpd

daengbo there's several reasons you may want to run mpd and not use the network features, for example being able to restart x and keep the music playing, being able to restart the computer and have your music automatically start up from where it left off and the fact that there's a tonne of great lightweight clients for it.

---

### Post by daengbo on 2007-11-05
About the DB failure -- check your mpd.conf file to see where the database is to be stored. If it's not in your home directory, you won't have permission to create it. You'll need to change the location to somehwere writable by you.

Again, MPD is a little complicated just to use with one computer ...

---

### Post by aidanr on 2007-11-05
> **daengbo said:**
> If it's not in your home directory, you won't have permission to create it. You'll need to change the location to somehwere writable by you.
Indeed the default is /var/lib/ you'll want to make ~/.mpdconf look something like this:

```
port			"6600"
music_directory		"~/myaudio/"
playlist_directory	"~/myaudio/Playlists/"
log_file		"~/.mpd/log"
error_file		"~/.mpd/error"
db_file			"~/.mpd/db
state_file		"~/.mpd/state"
pid_file		"~/.mpd/pid"
bind_to_address		"127.0.0.1"
```
I like to create a .mpd folder to keep things a bit tidier, it'll complain if it's not there so create it beforehand.

---

### Post by desklamp on 2007-11-05
> If that works and you want mpd to start up with the computer add it to your session startup programs and remove /etc/init.d/mpd
No, that did not work.  Same problem still occuring.

Dead end?

> Can I be blunt? If you are not going to use MPC over a network, it's kind of a waste.
Waste as in "not using its full potentials", then yes.  So long as it fits my criteria, I do not really care what else it can do or meant to do.

> If you are only using one box, there's no need for a server/client architecture. You'll be better off using another client. There are a million of them, but I suggest Rhythmbox for Ubuntu and Amarok for Kubuntu because they're the officially supported applications, and you'll get better-tested software. Answers on the forum will probably be easier to find, as well.

As I stated in the original message:

"I am looking for a small music player that runs in terminal."

The 2 suggestions you made are neither small nor runs in terminal.  Also, they are dependent on desktop environments.  I am using neither.  In fact, I am not even using one.

If you or anyone else have something better or that does the job, then I am all ears.

The closest thing I found is moc.  But I am looking for something smaller than that.

---

### Post by daengbo on 2007-11-06
Sorry I misses the part about the terminal.

You should take a look at [CMus]("http://cmus.sourceforge.net/") and [Squash]("http://savannah.nongnu.org/projects/squash/").

Best of luck, again.

---

### Post by desklamp on 2007-11-06
Thanks.  I will look into them.

---

### Post by trak87 on 2007-11-07
> **desklamp said:**
> I read that mpd can be used via a network.  This avahi-daemon thing must be it.

However, I do not plan to use use it via a network.  I am only planning on using it on this computer.  Therefore, it does not matter if I have it, right?

So the mpd daemon seems to be running.  I have ~/myaudio in the ~/.mpdconf.  But when I "mpc ls" nothing gets listed.

Even after rebooting.

What am I missing here?

I never had to jump through any hoops to get mpd and a client working. My original messages explain exactly what I did to get it working. mpd does sort of work on a network, but it works in a "jukebox mode", i.e., you cannot have different computers playing their own song like a typical server application. You can only control the one song that is playing from multiple locations. However you can add streaming capabilities to mpd with shoutcast. I've never tried this. 

For true client/server networking of music you could use nfs or samba. That way you access a remote mount/share just like it was a local drive.

---

