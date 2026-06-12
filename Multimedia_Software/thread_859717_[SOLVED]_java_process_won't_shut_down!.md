---
title: "[SOLVED] java process won't shut down!"
date: 2008-07-14
forum: Multimedia Software
---

### Post by dodle on 2008-07-14
I found a media player that I like called aTunes.  It's written in java and, I think, is a frontend for mplayer.  I've installed it and everything works fine, until I "x" out of it.  Once it closes, I can't re-open.  After going into taskmanager I see that "java" is still running.  I kill the process and am able to open aTunes again.  If I go to File > Exit to close out, the java process ends and I am able to re-open.  Why does one work, but not the other?  Is there something I can do to fix this, or should I give up on this software?

---

### Post by scragar on 2008-07-14
have you tried editing the launcher to read:
```
atunes && killall java
```
that way when atunes is closed it sends the kill signal to java

---

### Post by dodle on 2008-07-14
> **scragar said:**
> have you tried editing the launcher to read:
```
atunes && killall java
```
that way when atunes is closed it sends the kill signal to java

Thanks for thw quick response.  aTunes isn't a built-in command, so my launcher looks like this:```
sh "/opt/aTunes/aTunes.sh
```I tried adding what you said:```
sh "/opt/aTunes/aTunes.sh" && killall java
```but that didn't work.

---

### Post by HotCupOfJava on 2008-07-14
Ha! It sounds like whoever wrote the code forgot to add a WindowClosing event handler for System.exit(0); - They just did it for EXIT on the menu item. A common mistake when doing Java code, I'm afraid. I don't suppose you have access to the source code?

---

### Post by dodle on 2008-07-14
I download the .jar file from [http://sourceforge.net/project/showfiles.php?group_id=161929]("http://sourceforge.net/project/showfiles.php?group_id=161929"), there are a couple other packages but I don't know if they are source.

---

### Post by HotCupOfJava on 2008-07-14
OK - I'll see if I can peek at the source code.....it should all be there in the JAR....I can't guarantee that I'd be able to rebuild the application IF that's the problem, but at least we could then tell the developers "hey! You guys might want to add one more line of code..."

---

### Post by dodle on 2008-07-14
Thanks.  I appreciate it.

---

### Post by HotCupOfJava on 2008-07-15
OK - from what I can make of their code, the method "Kernel.finish()" isn't being called when you click to close the window. I'm trying to find the code for the window itself to be sure, but that IS the method that closes the application and exits the Java virtual machine....

---

### Post by HotCupOfJava on 2008-07-15
OK - I'm looking at their code for the VisualHandler class, which is where they seem to have set up their GUI components......they do use the WindowAdapter class and several of the methods........but I don't see any code for "public void windowClosing......." which is what you need. They need to reference "Kernel.finish" in a "windowClosing" method of the "WindowAdapter" class. Now, there is a HECK of alot of code there, and I may be missing something, but that SEEMS to be the source of your woes. In other words, its not something you're doing wrong, it is a few extra lines of code they need in their app. It may be worth your time to notify them of the problem - and hey, you may have just helped them in the development of their app.

---

### Post by dodle on 2008-07-15
Thanks a lot for checking into that for me.  I think I will try to contact them.

---

### Post by dodle on 2008-07-22
Figured out the problem from the sourceforge forum.  aTunes isn't compatible with the xfce4 panel, only Gnome and Kde... and Windows.

---

