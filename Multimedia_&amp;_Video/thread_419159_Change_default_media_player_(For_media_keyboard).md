---
title: "Change default media player? (For media keyboard)"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by martinw89 on 2007-04-22
Hello all,
First off I apologize if this has been mentioned but a search only found changes in Nautilus for specific file types.  I have a laptop with multimedia keys (HP DV6000t), two of which launch multimedia software.  System>>Preference>>Keyboard Shortcuts shows this action as "Launch music player".  At the moment, this launches Rhythmbox.  I would prefer to use Amarok.  Does anyone know how to do this?

Thanks,
Martin

---

### Post by robrmd9 on 2007-04-23
I am curious about this too!

---

### Post by tdozier on 2007-04-26
As am I.

---

### Post by martinw89 on 2007-04-26
Well at least I'm not the only person baffled by this.  I know that keyboard shortcuts are inflexible at the moment, maybe we just have to wait for an upstream update from Gnome to get a more flexible shortcut manager.  I assumed that the action called some command, if we knew what this command was we could change the player it calls.

---

### Post by tdozier on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=187698&highlight=change+default+media+player](http://ubuntuforums.org/showthread.php?t=187698&highlight=change+default+media+player)

I ran the command sited in this post via ssh and I will try it when I get home.

---

### Post by robrmd9 on 2007-04-27
That thread essentially tells the user to make the symlink to Rhythmbox refer to another player.  That is a temporary fix at best, but will work for people who don't mind breaking Rhythmbox's functionality.

We still haven't found the place where we could specify a specific player, though.

---

### Post by tdozier on 2007-04-27
You are correct. It would be better to actually change the setting instead of using a work around. However, because it works I will post the command here for those who do not mind using a workaround for the time being.

$ ln -s /usr/bin/amarok /usr/local/bin/rhythmbox

Has anyone found a post that will help make the Play(pause), Stop, Previous, and Next Buttons work. Changing the keyboard shortcuts has not fixed mine.

---

### Post by robrmd9 on 2007-04-27
If you are talking about the shortcuts in amarok not working, I have heard some people say that removing the keybindings from System->Preferences->Keyboard Shortcuts for the media functions (stop, play, etc) allows amarok to properly respond to the keys.

So I would try removing the keybindings from Gnome, and then configuring within amarok to respond to media keys.  I think I tried this a couple days ago and it did not work for me, but it is worth a try.

---

### Post by martinw89 on 2007-04-28
Thank you for the suggestion to remove the play/pause shortcuts in the shortcut manager, that worked very well.  For some reason stop/prev/next still does not work globally, it does work when the player is up though.  I know the symlink will work but I'm not very interested at the moment.

---

### Post by Inxsible on 2007-05-01
just what I was looking for to try out tonite on my HP dv9000t laptop !!!
 
gotta bookmark this page ! 
:popcorn:

---

### Post by irishbandit on 2007-09-25
In Gutsy Gibbon you need to run configuration editor under system tools then find desktop>gnome>applications>media> Change the value to the application you want launched. You can make it firefox if you want.

---

### Post by mgdm on 2008-01-09
There's a far easier way to do it: click System, then Preferences, then Preferred Applications, and finally the Multimedia tab. This lets you choose whatever you like without needing to use the gconf editor.

---

### Post by dgen on 2008-02-10
> **mgdm said:**
> There's a far easier way to do it: click System, then Preferences, then Preferred Applications, and finally the Multimedia tab. This lets you choose whatever you like without needing to use the gconf editor.
you're the man!!

---

### Post by supermonkey77 on 2008-02-17
Worked a treat for me. Just set field to custom and typed exaile in the box. Media key now launches exaile of the bat

---

