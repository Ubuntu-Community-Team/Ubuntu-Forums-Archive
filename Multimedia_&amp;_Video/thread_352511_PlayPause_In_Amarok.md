---
title: "Play/Pause In Amarok"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by chocomoojuice on 2007-02-03
So I've been using Ubuntu for a while, and have decided to try its Kubuntu counterpart.  However, I seem to be having some issues when using my favorite music player, Amarok.  

I have a Microsoft Multimedia Keyboard, so there are special keys on it (volume up/down, next/previous track, etc).  Now I am pleased to say that most of the configurations that came with Amarok have left these keys functional.  All but one is configured to my liking...the play button.  In Amarok you can chose to have a play or play/pause button, and one of the keys is currently configured to be a play button, but I'd like it to be responsible for the play/pause function.  When I try to configure the key myself, I'll press it but there will be no recognition to set the new key.  However, the key is recognized by Amarok under it's current play function, so I am getting frustrated and confused!  I've tried searching for the Amarok global keyboard shortcuts configuration file to edit it manually, but I can't seem to locate it.

Any help with this issue would be greatly appreciated!
- James

---

### Post by chocomoojuice on 2007-02-06
Bump!

Does anyone know the location of the global keyboard shortcut configuration file for Amarok, or a solution to this problem?

---

### Post by dillzz on 2007-02-06
Hey

Have the same problem with similar keyboard but fixed it.  Go to settings -->Global shortcuts.  Look for Play/Pause.

---

### Post by chocomoojuice on 2007-02-06
I've tried going there and setting the key under the play/pause function, but for some reason amarok won't recognize the key when I try to set it :(.  And yet, it responds to the key under its current play function.

---

### Post by dillzz on 2007-02-07
Hmmm.....Interesting it worked for me but I am using a different keyboard than yours.  Is KMilo turned on in KDE services?  Mine is checked as primary shortcut w/out multi.

---

### Post by chocomoojuice on 2007-02-09
> Is KMilo turned on in KDE services? Mine is checked as primary shortcut w/out multi.
When I check the system service list, I see no service listed as KMilo.  I am using a Microsoft Multimedia Keyboard 1.0A (not USB).  The weird thing is that recongifuring these shortcuts worked fine in Ubuntu.  However, I do distinctly remember having to select a keyboard model similar to mine in a menu of some type to get the keys responding.  Is there any way to do something similar to that in Kubuntu?

---

### Post by DaveQB on 2007-02-10
Bump on this.

I am using an A4tech RFKB-25 and had it working in Dapper, but lost the ability to use the Play/Pause button in Edgy.  Everything else works and this very same button does impact Amarok; is starts/restarts playing from the start of the current track, but wont pause.

Setting in Global Shortcuts wont recognise the key.

Also in an effort to fix this, I have lost the nice GUI that Kubuntu 6.10 added that shows the volume status when you change it using the keyboard keys :(

PS I had to create a file in ~/.kde/Autostart that set up the keyboard mapping when KDE started.  Now this is not needed in Edgy.  Nice work Kubuntu team.

---

### Post by dillzz on 2007-02-12
*> When I check the system service list, I see no service listed as KMilo. I am using a Microsoft Multimedia Keyboard 1.0A (not USB). The weird thing is that recongifuring these shortcuts worked fine in Ubuntu. However, I do distinctly remember having to select a keyboard model similar to mine in a menu of some type to get the keys responding. Is there any way to do something similar to that in Kubuntu?*

Are you sure you are looking under kde services and not runtime services.  It is located in Kcontrol and another subcategory, I can't remember off the top of my head.  Also are you running edgy?

Also check this post if it leads you in any direction

[http://www.ubuntuforums.org/showthread.php?t=124467&highlight=kmilo]("http://www.ubuntuforums.org/showthread.php?t=124467&highlight=kmilo")

[http://www.mepis.org/node/6195]("http://www.mepis.org/node/6195")

---

### Post by dillzz on 2007-02-12
Ok I got a chance to jump on my linux box.  What you should also check is under Kcontrol.

kde components-->service manager-->on bottom of pane kmilo should be there

kde components-->regional & accessibility-->keyboard layout-->look for keyboard selection eg:micrososft (irony)

---

