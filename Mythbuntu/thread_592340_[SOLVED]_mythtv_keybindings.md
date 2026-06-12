---
title: "[SOLVED] mythtv keybindings"
date: 2007-10-26
forum: Mythbuntu
---

### Post by dysphasi on 2007-10-26
Hey all, just set up mythbuntu on my ubuntu 7.10 installation. I want to make use of my MCE Remote.... whilst it's installed and working, the default keybindings were a bit off, so I downloaded a new lircrc file from a site (can't remember which now :s)

This lircrc works great....with a few exceptions. Some of the keys don't do a lot and I think I know why, at the top of the file it says:
```

# You will also need to make a few changes to the MythTV key bindings and jump
# points as follows.
#
# Jump Points:
#
#   TV Recording Playback:                      Alt+R
#   Program Guide:                              Alt+G
#   Live TV:                                    Alt+P
#   MythVideo -> The MythVideo default view:    Alt+V
#   Main Menu:                                  Alt+Home
#
# Key Bindings:
#
#   TV Playback -> CHANNELDOWN:  Down,PgDown
#   TV Playback -> CHANNELUP:    Up,PgUp
#   TV Playback -> JUMPRWND:     Shift+PgUp
#   TV Playback -> JUMPFFWD:     Shift+PgDown

```

So the question is, how do I go about making these keybinding/jump point changes. I've looked high and low but can't find a simple how-to anywhere.

Ta in advance people!

---

### Post by tgm4883 on 2007-10-26
install myth controls, then you can do it from the frontend.  BTW, those lines you posted are commented out.

---

### Post by napsilan on 2007-10-26
the settings area in mythweb also has a clean table for editing keybindings.

---

### Post by dysphasi on 2007-10-27
> **tgm4883 said:**
> ...BTW, those lines you posted are commented out.

Lol, I'm a bit of a newbie to all this but I did know that ;)

...never know though, thanks for pointing it out anyway :D

I'll give the controls dooda a go right away. Fingers crossed :)

---

### Post by dysphasi on 2007-10-27
> **napsilan said:**
> the settings area in mythweb also has a clean table for editing keybindings.

If I could get mythweb working! Is it meant to work 'out of the box' as it were with the mythbuntu install? 

I've been editing files here there and everywhere (yes...I did keep track and do things one step at a time) but I've seen just about all the error messages possible and received no joy at actually firing it up.

Is there a good idiots' guide to setting up mythweb you could recommend?

---

### Post by napsilan on 2007-10-27
All I had to do to set up mythweb was "sudo apt-get install mythweb"  And then access the mythtv computer either from another computer's web browser, or by using localhost.  I did do some manual file editing to secure a couple pages, but the base installation was just that one apt line.  Do you need to do port forwarding?

---

### Post by dysphasi on 2007-10-27
Well, I uninstalled apache and mythweb, then reinstalled them, this seemed to let me actually get beyond [http://localhost/](http://localhost/) to [http://localhost/mythweb](http://localhost/mythweb)

BUT all I see is a list of folders now: data, includes, js, modules, skins and the files mythweb.php and mythweb.pl

No user interface at all. Is there something I could be missing that will let me see a graphical interface rather than this index?

---

### Post by napsilan on 2007-10-27
I really don't know where to go from there.  You can try using --purge with dpkg to uninstall and then reinstall again, but I really don't know.

---

### Post by dysphasi on 2007-10-27
Why does nothing just work :p lol 

Thanks for the reply, I didn't know about the purge option. Probs my best bet, I'll let you know how it goes.

---

### Post by dysphasi on 2007-10-27
> **napsilan said:**
> I really don't know where to go from there.  You can try using --purge with dpkg to uninstall and then reinstall again, but I really don't know.

You absolute genius....would it be inappropriate for me to hug you?!!! ;)

Woooooooooooooooooooooooot :popcorn::lolflag: :D


ps.. If there's anyone else out there as useless as myself, all I did was:

```
sudo dpkg --purge mythweb
```
Then did the same for apache and it's associated packages (I found the package manager a bit easier to use for this).
Then:
```

sudo apt-get install libapache2-mod-php5
sudo apt-get install mythweb

```
And it worked :D

---

### Post by dysphasi on 2007-10-27
> **napsilan said:**
> ... I did do some manual file editing to secure a couple pages...

I don't suppose you'd either be able to tell me, or link me to where you got the info for those manual changes?

I actually got it passworded using mythbuntu control cenetre...is that any less secure?

---

### Post by dysphasi on 2007-10-28
Would still appreciate some tips at those manual changes you were talking about napsilan, but otherwise problems solved. Thanks! :popcorn:

---

### Post by napsilan on 2007-10-28
I did that in feisty before mythbuntu-control-center was released.  If you added a password using the control center, then it's secure.  Editing apache.conf will let you specify different security settings for different users and pages, and allow tricks like not requiring a password for anyone on the local network.  It's not necessary now, however, since mythbuntu can do the basic security.  

further reading-- [http://mythtv.org/wiki/index.php/Mythweb](http://mythtv.org/wiki/index.php/Mythweb)

---

### Post by dougsnell on 2009-05-13
Awesome.  Thanks for posting ... even if this is an old thread.  I ran into issues with mythweb on jaunty, and these simple instructions (while probably obvious to anyone who's been doing this for years) were exactly what I needed.

---

> **dysphasi said:**
> You absolute genius....would it be inappropriate for me to hug you?!!! ;)

Woooooooooooooooooooooooot :popcorn::lolflag: :D


ps.. If there's anyone else out there as useless as myself, all I did was:

```
sudo dpkg --purge mythweb
```
Then did the same for apache and it's associated packages (I found the package manager a bit easier to use for this).
Then:
```

sudo apt-get install libapache2-mod-php5
sudo apt-get install mythweb

```
And it worked :D

---

