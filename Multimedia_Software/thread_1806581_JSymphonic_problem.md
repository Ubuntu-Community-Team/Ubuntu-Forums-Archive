---
title: "JSymphonic problem"
date: 2011-07-17
forum: Multimedia Software
---

### Post by dtower on 2011-07-17
Hello,

I'm trying to run JSymphonic. The first time I ran it today, it opened up a GUI screen for me, but then I couldn't figure out what to do with it, and after I pressed OK, the GUI screen disappeared and the following appeared in the terminal:

Jul 18, 2011 10:46:47 AM org.danizmax.jsymphonic.gui.JSymphonic <init>
SEVERE: Preparing to run..
Exception in thread "AWT-EventQueue-0" java.lang.ArrayIndexOutOfBoundsException: Array index out of range: 0
	at java.util.Vector.get(Vector.java:721)
	at org.danizmax.jsymphonic.gui.JSymphonicFrame.loadNewConfig(Unknown Source)
	at org.danizmax.jsymphonic.gui.JSymphonicFrame.<init>(Unknown Source)
	at org.danizmax.jsymphonic.gui.JSymphonic.<init>(Unknown Source)
	at org.danizmax.jsymphonic.gui.JSymphonic$2.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
	at java.awt.EventQueue.access$000(EventQueue.java:96)
	at java.awt.EventQueue$1.run(EventQueue.java:608)
	at java.awt.EventQueue$1.run(EventQueue.java:606)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

After trying to start it again, I kept getting the same message. I tried sudo apt-get remove jsymphonic
and sudo apt-get autoremove jsymphonic

and appeared to be successful at removing it, but then when I tried to re-install it (after a system reboot), it still goes back to the same error message in the terminal when I try to run it, only this time, the GUI doesn't open at all. 

If anyone can help, I'd greatly appreciate it!

---

### Post by tgalati4 on 2011-07-17
I don't know what version you are running but I run it as follows:


java -jar JSymphonic_v0.3.0_Ode_To_Freedom.jar 


The first dialog box to pop up asks you to select the directory /media/mycrappysonywalkmanmp3playerthatusescrappysonicstage

Then there is a selection list below to pick the type of player.

---

### Post by oeckes on 2011-09-03
Hey,

I have exactly the same problem as described in the first post.

JSymphonic simply does not start at all and the same message as in the first post pops up. I also tried to run it from the shell with the suggested java -jar option and also with any kind of version depiction i could find on my system like

JSymphonic.jar
JSymphonic-0.3.0.Ode.To.Freedom+svn387.jar
JSymphonic-v0.3.0.Ode.To.Freedom+svn387.jar
JSymphonic-v0.3.0_Ode_To_Freedom+svn387.jar

it always says: unable to acces jarfile

I'm really frustrated because jsymphonic already worked previously. I don't understand, why it does not start any more. I would be grateful for help

---

### Post by oeckes on 2011-09-04
Ok, hi again.

Finally I found a solution that I'm confident with. I simply downloaded the older 0.3.0 beta version and safed the file JSymphonic_v0.3.0b.jar directlly on my MP3-Player next to the OMGAUDIO folder.
Afterwards I could start it from the shell in the correct directory ( media/MP3-PLAYER in my case) with:
java -jar JSymphonic_v0.3.0b.jar

Though it is the older version at least I can now change the music on my player again.
That is all I need.

Bye

---

