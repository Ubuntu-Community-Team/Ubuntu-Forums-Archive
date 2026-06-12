---
title: "Controlling rhythmbox through an iphone (ssh without X)!"
date: 2008-10-25
forum: Multimedia Software
---

### Post by emshains on 2008-10-25
So, the story is, I would love to skip/play/pause/stop songs on the rhythmbox through ssh, but as far as I know, the rhythmbox-client tries to do stuff with X, but since iphone runs on BSD, which (as far as I know) uses a different kind of X, modified to work on the phone. So is there a client for the iphone, or a specific command/way to get this worked out ? 

Sorry for the lack of info, it's kinda' late (early?) in the night (morning?).

---

### Post by emshains on 2008-10-26
I so hate to double-post, but *bump*!

---

### Post by Richard Mathie on 2009-02-02
it looks to me like rhythmbox-client needs X forwarding to work over ssh.

```
you@remote:~$  ssh -X you@your_music_server
```

this gets rid of the Dbus problem

then in the ssh session 

```
you@your_music_server:~$ rhythmbox-client --do-some-music 
```

where do-some-music is what ever command you require.

my only problem is that rhythmbox then try's to open the client on the computer being used as a remote (you@remote) and dose not control you@your_music_server, even with the --no-stat option, this means it trys to stream the music to the remote and subsequently crashes :( or hangs.

how do i tell rhythmbox-client which instance to control

i had a bit of a fool around as well and tunneled with ssh from where the music should be playing back to the remote to execute the above commands

ssh you@your_music_server >> you@remote >> you@your_music_server

this worked like normal, but isn't very useful. :(

---

### Post by Richard Mathie on 2009-02-02
found this its perfect

[http://web.vee.net/projects/rhythmweb/](http://web.vee.net/projects/rhythmweb/)
install on you music playing machine

then in your browser [http://your.ip:8000/](http://your.ip:8000/)

enjoy

---

### Post by emshains on 2009-02-08
> **Richard Mathie said:**
> found this its perfect

[http://web.vee.net/projects/rhythmweb/](http://web.vee.net/projects/rhythmweb/)
install on you music playing machine

then in your browser [http://your.ip:8000/](http://your.ip:8000/)

enjoy

Why did they shut down the thanking system ? Cause you'd get a "Thanks a lot" right now!

---

### Post by griffjon on 2010-07-05
[http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote) is an iphone optimized update to the web remote, and works much better. Still a bit light on features, but a big step forward.  

I'd love to see full WAWI-level playlist/media library access. Without, that is, diving into the insanity that is rhythmote (works great, unless you have a huge music library) [http://www.winamp.com/plugin/winamp-web-interface/92511](http://www.winamp.com/plugin/winamp-web-interface/92511) is the WAWI (for Winamp) plugin homepage.

---

### Post by keithspg on 2011-01-23
As a newbie to this, It was very confusing as there are a number of different rhythmweb projects: [http://web.vee.net/projects/rhythmweb/](http://web.vee.net/projects/rhythmweb/) [http://www.joaomak.net/projetos/rhythmote/](http://www.joaomak.net/projetos/rhythmote/)
The first one is from 2007 and appears to have spawned the second one. It does not show any development since then. The second one appears recent and current, but does not work completely. Any event such as next or volume up, causes a server error and I have to open a new page to see where it is. Pretty annoying. Besides, it does not have all the features I'd like, but it looks nice.

There is a 3rd and 4th version:
[https://bitbucket.org/jimcerberus/rhythmweb/overview](https://bitbucket.org/jimcerberus/rhythmweb/overview)
 
The first of this set is more complete and functions as advertised. It probably has more of the capability asked for. I'd like to see a volume control, though. The 'fork' I was not able to make work. 

Is there an 'official' rhythmweb plugin? Why so many different with the same name?

---

### Post by peibol on 2011-01-24
> **Richard Mathie said:**
> it looks to me like rhythmbox-client needs X forwarding to work over ssh.



There is no need, you can always set the DISPLAY variable:

```

# ssh your_user@your_server
# DISPLAY=:0.0 rhythmbox-client --do-some-stuff

```

The bad part is that rhythmbox-client will try to start a new instance as the main GTK loop is attached to another tty, so you should kill it first and then start a new one.


Anyway, I think this one looks great for what you want to do  [https://bitbucket.org/jimcerberus/rhythmweb](https://bitbucket.org/jimcerberus/rhythmweb)

And it's in active development right now.

---

### Post by nstenz on 2011-02-12
(Instead of messing with an SSH terminal connection, something like Rhythmote would really be a better solution...)

But I did the following for my laptop yesterday as a quick solution.

You don't need to kill anything. It's very easy to tell rhythmbox-client which X display to use, and not to try launching another copy.

This is the proper way to skip to the next track:
```
env DISPLAY=:0.0 rhythmbox-client --no-start --next
```

Here is the whole next.sh script I wrote yesterday after finding this info. It prints the new song's title as well:
```
#!/bin/bash
env DISPLAY=:0.0 rhythmbox-client --no-start --next
currentSong=`env DISPLAY=:0.0 rhythmbox-client --no-start --print-playing`
echo Now playing: $currentSong
```

You probably to control the volume, too...

Down:
```
amixer -c 0 set Master 5%- | grep "Mono: Playback"
```

Up:
```
amixer -c 0 set Master 5%+ | grep "Mono: Playback"
```



EDIT: Unfortunately, I haven't been able to get Rhythmote to work. There's a bug where it tries to append the port to the end of the URL again after you perform any action, and after I fixed that in the code, all it ever says is "playlist is empty". The Play/Pause button doesn't appear to do anything. I guess I'll try RhythmWeb.

---

### Post by peibol on 2011-02-16
[Rhythmote]("http://www.joaomak.net/projetos/rhythmote") has been included into [RhythmWeb]("https://bitbucket.org/jimcerberus/rhythmweb"), as a mobile skin, right now you will download the same project from both sites.

---

