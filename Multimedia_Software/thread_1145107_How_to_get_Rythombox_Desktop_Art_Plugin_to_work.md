---
title: "How to get Rythombox Desktop Art Plugin to work"
date: 2009-05-01
forum: Multimedia Software
---

### Post by ubuwatson on 2009-05-01
I tried following the steps on the site: [http://nedrebo.org/code/rhythmbox/desktop_art](http://nedrebo.org/code/rhythmbox/desktop_art) without any luck.  The svn command of course didn't work so i downloaded all the files manually and put them into the plugin folder with executable permissions.  I can see the plugin in Rythombox, but when I attempt to activate it it states: Plugin Error: Unable to active plugin Desktop Art.

I am running 9.04.

Thanks for any suggestions you might have.

---

### Post by Parp on 2009-05-01
install subversion first, then svn will work... sudo apt-get install subversion

---

### Post by ubuwatson on 2009-05-01
> **Parp said:**
> install subversion first, then svn will work... sudo apt-get install subversion

Thank you very much, it worked like a charm !

---

### Post by phlancelot on 2009-12-23
Hey, apologies in advance if I'm hijacking this thread. I'm having some issues with this plug-in as well and wondering if anyone can lend some advice.

I am able to install the thing just great and it sits perfectly where I want it and displays my song info in all its gorgeous compiz glory.. the only thing missing is the album covers! 

I had this installed and working great on my old computer about a year ago but since trying it again on my new laptop it simply refuses to show me any covers!

I have covers sitting in each album folder as a .jpg in a very organized /home/Music. The covers show up just fine within Rhythmbox itself... just not on the desktop art plug-in. 

I'm using ubuntu 64-bit 9.10 with Rhythmbox v0.12.5 and whichever version of the desktop-art plugin is downloaded via the commands shown on the author's webpage [http://www.nedrebo.org/code/rhythmbox/desktop_art](http://www.nedrebo.org/code/rhythmbox/desktop_art).

I can think of a few things which might be the cause of the problem... but I'm really grasping at straws so if anyone has experienced this problem also and fixed it I would love to hear you solution!

What I can think is that my .jpgs might be labelled incorrectly and the plug-in is having trouble finding them

Or perhaps because I am using a folder containing two symbolic links to two other folders within my /Music/ directory... In other words, Rhythmbox does not directly watch a folder containing actual .mp3s but instead one that contains links to other locations within /Music/ ... can't see how this would interfere though.

Thats really all I can come up with so if anyone has suggestions that would be wonderful.

Thanks a million.

PS - I've attached a screenshot of what things look like while playing a song.[IMG]http://dl.dropbox.com/u/2702257/Forum%20Stuff/rhythmbox_desktopart_problem.jpg[/IMG]

---

### Post by dtr1001 on 2010-03-24
Folks ive got the same problem. Was there a solution?

---

### Post by phlancelot on 2010-04-01
Well, I've still got the problem but I managed to find a workaround that I've settled with for now. If I go into each of my album folders within music and rename the album cover jpg to "cover.jpg" then the plug-in is able to recognize it and it will show up. 

I can't remember where but I read on a certain site that it only picks up a certain set of filenames... I think you can use "cover" "album" "front" and theres some others... if I find the site again I'll post it. A little bit annoying to go in and change all my album covers to the same name, though it does work so I'm happy enough.

---

### Post by zeroseven0183 on 2010-05-01
I had the same problem but was able to resolve it.

The result of 
```
rhythmbox --debug &>rhythmbox-log.txt
``` shows that there's a problem with rsvg as 

```
Traceback (most recent call last):
  File "/home/tutdek/.gnome2/rhythmbox/plugins/desktop-art/__init__.py", line 25, in <module>
    from DesktopControl import DesktopControl
  File "/home/tutdek/.gnome2/rhythmbox/plugins/desktop-art/DesktopControl.py", line 27, in <module>
    import rsvg
ImportError: No module named rsvg

(rhythmbox:2304): Rhythmbox-WARNING **: Could not load plugin desktop-art

(14:49:10) [0x8cda028] [rb_python_module_finalize] rb-python-module.c:427: Finalizing python module (null)

(rhythmbox:2304): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Desktop Art'
```

So here's what I did to somehow bypass that:
1. edited **/home/username/.gnome2/rhythmbox/plugins/desktop-art/DesktopControl.py**
2. put a **#** before the line that says **import rsvg** to "comment" it
3. saved the file
4. start Rhythmbox

---

### Post by persio on 2010-05-01
> **zeroseven0183 said:**
> 
So here's what I did to somehow bypass that:
1. edited **/home/username/.gnome2/rhythmbox/plugins/desktop-art/DesktopControl.py**
2. put a **#** before the line that says **import rsvg** to "comment" it
3. saved the file
4. start Rhythmbox
Praise you [-o<

It was working fine on 9.10 but it broke when I upgraded to 10.04. Thanks to your solution it's now back :)

---

### Post by kerbernic on 2010-05-02
Hi there

Simpler is to let the plugin work as it should do and not edit its source code without committing it or understanding it, it's a matter of maintenability.

Just do :

```
sudo aptitude update
sudo aptitude install python-gnome2-desktop
```And python-rsvg will be installed as depedency.

Your Rhythmbox Desktop art plugin will work like a charm with that.

Hope this help

Pierre

---

### Post by tiznom on 2010-06-18
This still isn't working for me. I suspect I'm not the only one. I have tried the above suggestions, as well as a couple from the launchpad site. Rhythmbox displays all the art, no problem. Why won't the plugin? Re-downloading all the album covers and manually putting them in folders is simply not an option, I have way too many. If this is a lost cause and the plugin is an abandoned project, are there other options? Rhythmbox is working great for me and the plugin is exactly what I want, except it won't see the art.

---

### Post by Jimmeh! on 2010-06-21
> The plugin can not yet fetch covers from the net, so it is       recommended to also have the default Album Art plugin enabled and let  it do the fetching. 

The       plugin also requires a composite manager (e.g. Metacity, Compiz or  xcompmgr) to work properly.

Python, Cairo, librsvg, Glade, Pango,  and GTK+.    This plugin requires python 2.5 or higher and gnome-python-desktopNot sure if this was luck or judgement, but I've just managed to get mine working with album covers from last.fm after trying everything above without success.

I read the quoted list and noticed it said python 2.5. So I installed python-old-doctools and Cairo. After messing with Cairo for a while (ooh pretty!) and shutting it down, the album covers are working :)

As I said more luck than judgement but hopefully it helps someone :)

EDIT: Hrmm it only worked for a couple of tracks, I guess it has those cached somewhere, now it's back to not working. It did look awesome for a brief while though :*(

Messing some more with Cairo, it seems it is capable of downloading it's own artwork, so the script is probably picking it up from cairo's cache. What we really need is to edit the desktop art plugin to use the artwork directly from the "Cover Art" plugin, but unfortunately I don't speak python.

Is anyone willing to hack something together?

---

### Post by Yneth on 2010-06-29
> **kerbernic said:**
> Hi there

Simpler is to let the plugin work as it should do and not edit its source code without committing it or understanding it, it's a matter of maintenability.

Just do :

```
sudo aptitude update
sudo aptitude install python-gnome2-desktop
```And python-rsvg will be installed as depedency.

Your Rhythmbox Desktop art plugin will work like a charm with that.

Hope this help

Pierre




Thanks a lot for this! It could get Desktop-Art to work. Cheers.

---

### Post by frogotronic on 2010-07-02
Hi,

  I'm running KK and get this error on start-up (even with compiz enabled):

```
**you are not running under a composited desktop-environment. the desktop art plugin cannot work without one.**
```

How can I prioritize the start of Rhythmbox?  You used to be able to give it a number, but that seems to have been eliminated from the Startup Programs GUI.

- CH

---

### Post by Chodid on 2010-10-01
> **kerbernic said:**
> Hi there

Simpler is to let the plugin work as it should do and not edit its source code without committing it or understanding it, it's a matter of maintenability.

Just do :

```
sudo aptitude update
sudo aptitude install python-gnome2-desktop
```And python-rsvg will be installed as depedency.

Your Rhythmbox Desktop art plugin will work like a charm with that.

Hope this help

Pierre

I already have that package installed and it still doesn't show the cover art on the desktop. I tried the suggestion with commenting the "import rsvg" out as well which didn't help either. Does anybody have another idea how to get it to work?

Thanks a lot in advance

---

### Post by mathewas on 2011-04-11
You should install Sceenlets.

---

