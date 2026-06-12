---
title: "Blue video screen when using totem-xine"
date: 2008-08-22
forum: Multimedia Software
---

### Post by Si-Ddevil on 2008-08-22
Right, I've been using ubuntu since around feb this year and its been bliss, after a lot of tinkering I had everything I wanted working the way I wanted... until now :(

I was using totem-xine as with totem-gstreamer i was getting super laggy video and general desktop feel. i.e. when gstreamer is installed my whole system runs slower in general

Yesterday I installed a few new packages:

The first one was EnvyNG - the sole reason for this was so that I could use ATI-CCC because I wanted AA & AF to make the desktop look smoother and It was successful 

The second thing I done was enable the hardy-backports and hardy-proposed repos

Now to the porblem, I went to watch a movie last night (.avi) when I went to bed and realised that when I opened the movie up in totem (which worked the night before) there was sound but no video, just a blue screen... I tried all the "fixes" that i could find on ubuntu forums and other forums (like start gstreamer-properties and switch to xwindow system no-xv) but none of them worked! So, I switched back to totem-gstreamer and hey presto it now plays video! Thing is I don't like the performance loss that comes with this switch at all, If it didnt have such an effect on the system I wouldn't mind but it does and I likes the way xine performed - amazing quality video at no performance cost!

could anyone shed some light on what may have caused xine to stop working?
like I said before it only happened yesterday and I'm not sure if its to do with the backport/proposed updates that came through after I enabled the repos or something to do with the new ati driver and/or CCC!?

Any responses would be greatly appreciated.

Thanks in advance (",)
Si

---

### Post by Si-Ddevil on 2008-08-22
Does no one else have this issue? or a solution, even a suggestion?

---

### Post by Si-Ddevil on 2008-08-25
BUMPED! Does ANYONE have any idea what is wrong with xine?

---

### Post by Si-Ddevil on 2008-08-26
4 days and uber bumpage! can anyone shed light on this please?

---

### Post by Si-Ddevil on 2008-08-28
Why is no one replying? Isn't there an admin or someone who can at least confirm theres no solution to this? or even tell me everythings gonna be ok? lol

HEEEEEELP MEEEEEEEEE!

---

### Post by Si-Ddevil on 2008-09-04
Not even an attempt at helping me...

What happened to "Ubuntu"...

Its cool though, I've fixed it with a re-install, I simply wont be using backports or proposed updates again!

---

### Post by ronnielsen1 on 2008-09-04
Sounds like you don't like gstreamer and assuming everything is playing nice together besides the xine issue, I would uninstall gstreamer and reinstall xine and codecs. I'm sure there's settings in xine that you could adjust but I'm not sure which ones to tell you.
From googling I found this - which may or may not be your issue.
> I did the same once on a fresh install of Ubuntu (self-installation, no Dell pre-install). The reason it stopped working is probably that you installed libdvdcss2 from two different locations. The install-css.sh script actually installs libdvdcss2 and so you should just have launched that instead of adding the medibuntu repositories. That, or not have launched the script.
I don’t remember exactly, but I think I followed some instructions for replacing gstreamer with xine as backend for totem. That worked good for me so I didn’t feel the need to change the default totem for playing dvds. The advantage of xine over gstreamer is that xine will show the dvd menus, while gstreamer will immediately play the movie itself, at least according to my experience.
A little side note, when you select the xine-plugin for totem in synaptic or add/remove programs, it will automatically propose to uninstall gstreamer-plugin (and gstreamer completely iirc). I have no experience with gxine. 
[http://linux.about.com/b/2007/06/17/installing-software-for-viewing-dvd-movies-on-dells-inspiron-e1505n.htm](http://linux.about.com/b/2007/06/17/installing-software-for-viewing-dvd-movies-on-dells-inspiron-e1505n.htm)

---

### Post by ronnielsen1 on 2008-09-04
If a program doesn't start, I usually find the command and run it in a terminal to see what the errors are.
You also might consider VLC

---

### Post by Si-Ddevil on 2008-09-04
Thanks man, Like I said I re-installed hardy without backports/proposed updates and all is well
also only installed libdvdcss2 as opposed to the whole medibuntu repo this time and things are schaweet! Thanks for the two replys though man, at least someone cares! haha

Peace, or "UBUNTU" ;-)

---

