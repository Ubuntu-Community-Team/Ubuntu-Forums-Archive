---
title: "Good DVD Player"
date: 2009-08-08
forum: Multimedia Software
---

### Post by snakeman21 on 2009-08-08
Hi all.  My wife recently started watching Stargate DVDs on her laptop.  We both run Jaunty, and use VLC for DVD movies.  But my wife doesn't like having to bring up the separate control window just to pause the movie.  What she wants is a good DVD application that she can watch in full screen, but she wants to be able to move the mouse to the bottom to bring up a simple control.  I'm making this sound more complicated than it is... Basically, she wants something with a full screen mode that works like Totem's full screen mode.  Totem does not handle DVDs well (if at all) or she'd use that.  Any ideas?  I just don't want to download every Ubuntu DVD player under the sun to find the right one.  Any suggestions would be greatly appreciated!

---

### Post by Katalog on 2009-08-08
Totem is perfectly capable of handling DVDs if you have a certain library installed, a library  which is questionably illegal in the U.S. If you live in a different country (or just have a blatant disregard for the DMCA) though, it might be different in your case. For more information on these restricted formats read this page in the Ubuntu Wiki:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Arup on 2009-08-08
Install mplayer and smplayer, the smplayer front end is an excellent interface for watching DVD in full screen.

---

### Post by snakeman21 on 2009-08-08
I just tried the SMPlayer front end.  That's the right idea, but there's one major flaw:  No menu button!  My wife usually watches one or two episodes at a time, then puts it away for later.  She wants to be able to use the DVD menu to choose the episode she left off at.

---

### Post by rvm4000 on 2009-08-08
First be sure the option "Enable DVD menus" (in preferences -> drives) is enabled.

There's an option to go to the DVD menu in the "Browse" menu. (This option is assigned by default to the key shortcut Shift+Return)

---

### Post by andriusbu on 2009-08-08
> **snakeman21 said:**
> Hi all.  My wife recently started watching Stargate DVDs on her laptop.  We both run Jaunty, and use VLC for DVD movies.  But my wife doesn't like having to bring up the separate control window just to pause the movie.  What she wants is a good DVD application that she can watch in full screen, but she wants to be able to move the mouse to the bottom to bring up a simple control.  I'm making this sound more complicated than it is... Basically, she wants something with a full screen mode that works like Totem's full screen mode.  Totem does not handle DVDs well (if at all) or she'd use that.  Any ideas?  I just don't want to download every Ubuntu DVD player under the sun to find the right one.  Any suggestions would be greatly appreciated!

Could be only one option for your wife - Moovidia (former Elisa). Apple style GUI, perfect play DVDs. (Tested yesterday on Ubuntu 8.10) Probably most visualised Media Center ever are.

---

### Post by Arup on 2009-08-08
Best part is smplayer will start the movie from where you left off so you don't have to hunt for the chapter.

---

### Post by snakeman21 on 2009-08-08
> **Arup said:**
> Best part is smplayer will start the movie from where you left off so you don't have to hunt for the chapter.

Not when you watch an episode, remove the disk, watch a movie, then try to watch another episode.

---

### Post by qamelian on 2009-08-08
> **snakeman21 said:**
> Hi all.  My wife recently started watching Stargate DVDs on her laptop.  We both run Jaunty, and use VLC for DVD movies.  But my wife doesn't like having to bring up the separate control window just to pause the movie.  What she wants is a good DVD application that she can watch in full screen, but she wants to be able to move the mouse to the bottom to bring up a simple control.  I'm making this sound more complicated than it is... Basically, she wants something with a full screen mode that works like Totem's full screen mode.  Totem does not handle DVDs well (if at all) or she'd use that.  Any ideas?  I just don't want to download every Ubuntu DVD player under the sun to find the right one.  Any suggestions would be greatly appreciated!
You don't need to bring up a separate control window to pause. Hitting the space bar toggles pause on and of in VLC.

---

### Post by snakeman21 on 2009-08-08
> **rvm4000 said:**
> First be sure the option "Enable DVD menus" (in preferences -> drives) is enabled.

There's an option to go to the DVD menu in the "Browse" menu. (This option is assigned by default to the key shortcut Shift+Return)

I think you're talking about a different program.  There is no menu option the the browse menu, and there is no "enable DVD menus" option in preferences > drives

---

### Post by snakeman21 on 2009-08-08
> **qamelian said:**
> You don't need to bring up a separate control window to pause. Hitting the space bar toggles pause on and of in VLC.

Sorry for the double post, but thanks, that works!

---

### Post by rvm4000 on 2009-08-08
> **snakeman21 said:**
> I think you're talking about a different program.  There is no menu option the the browse menu, and there is no "enable DVD menus" option in preferences > drives

It seems you have an old version (those options were added in version 0.6.7). Update it:

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

It also recommended that you update mplayer too if still using the old 1.0rc2:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by ratcheer on 2009-08-08
My strongest recommendation is for **vlc**.

Tim

---

### Post by snakeman21 on 2009-08-08
> **rvm4000 said:**
> It seems you have an old version (those options were added in version 0.6.7). Update it:

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

It also recommended that you update mplayer too if still using the old 1.0rc2:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

nope, I checked in Synaptic...It's all up to date... It doesn't matter, though, I'm going to remove it and just leave her with vlc... now that we know the spacebar pauses it

---

