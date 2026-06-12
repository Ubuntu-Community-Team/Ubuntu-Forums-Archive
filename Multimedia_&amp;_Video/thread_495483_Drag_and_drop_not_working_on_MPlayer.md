---
title: "Drag and drop not working on MPlayer"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by ataiger on 2007-07-08
I installed mplayer using synaptic. (Ubuntu Feisty)

mplayer itself is working fine, but whenever I drag and drop a file on the program a error message is displayed and mplayer exits.

```
Title: Fatal error!
Mplayer interrupted by signal 6 in module: unknown
```

when I click OK in the dialog, it shows another dialog saying "MPlayer crashed~~ blah blah"

any help?

---

### Post by david_2001 on 2007-07-08
This is not something that I'd ever tried before.  Anyway, I added the mplayer launcher to the desktop and then dragged an mpeg file on to it from nautilus and mplayer just started and played it.  Do you get that error when dragging any file onto mplayer or just from one specific file?  If from a specific file, does it play when opened in mplayer by any other method?

---

### Post by ataiger on 2007-07-08
I uninstalled mplayer now.. but I guess drag and drop to the mplayer icon would work. The error occurs when I drag and drop a video file(not a specific one but all) to the program window of mplayer already opened. Files that I tried play ok when I right click them and then click open with mplayer in context menu.

I googled enough but I couldn't find any help. I think that's weird because I haven't done much to my ubuntu after I installed it. There must be people who suffer the same problem. I even tried compiling mplayer from source but still that wont work.

And I found another problem that I cannot navigate thru a video file when I play a realmedia file with mplayer(gui). So I just decided to give up and use RealPlayer and other players instead.

**EDIT** david_2001, if you never tried, please try dragging a file from nautilus to the mplayer window and tell me whether you see the same error or not.

---

### Post by david_2001 on 2007-07-08
> **ataiger said:**
> **EDIT** david_2001, if you never tried, please try dragging a file from nautilus to the mplayer window and tell me whether you see the same error or not.
Nothing happens at all if I try doing that, i.e. the file icon just goes back into the nautilus window.

---

### Post by ChaoticMind on 2007-07-17
I have exactly the same problem as ataiger. 

On a perhaps related note, I also had the problem described in the third post in this thread: [http://ubuntuforums.org/showthread.php?p=2849549](http://ubuntuforums.org/showthread.php?p=2849549). However the suggested solution by jarlath worked like a charm for me. Not sure if this is related at all. 
I'm on a relatively fresh Ubuntu installation. A bit over a week old now.

---

### Post by mike102282 on 2007-07-17
> **ataiger said:**
> I installed mplayer using synaptic. (Ubuntu Feisty)

mplayer itself is working fine, but whenever I drag and drop a file on the program a error message is displayed and mplayer exits.

```
Title: Fatal error!
Mplayer interrupted by signal 6 in module: unknown
```

when I click OK in the dialog, it shows another dialog saying "MPlayer crashed~~ blah blah"

any help?

I didn't know you could drag and drop to Mplayer?

---

### Post by david_2001 on 2007-07-17
> **mike102282 said:**
> I didn't know you could drag and drop to Mplayer?
Apparently recent versions of mplayer have this facility but certainly not the version installed by feisty.

---

