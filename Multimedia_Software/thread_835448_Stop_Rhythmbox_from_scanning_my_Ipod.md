---
title: "Stop Rhythmbox from scanning my Ipod?"
date: 2008-06-20
forum: Multimedia Software
---

### Post by tabithaboof on 2008-06-20
I use rockbox with my Ipod turns the ipod into a generic filesystem based MP3 player. I want to tell Rhythmbox to scan the folders on the IPOD but not to treat it as an ipod, only as a generic storage device. I have tried disabling the Ipod plugin but it still automatically scans the entire ipod whenever I start Rhythmbox. Is there any way to avoid this?

Its a shame, I love RB but this is kind of a deal breaker for me.

---

### Post by markbuntu on 2008-06-20
You can change the default opener for your ipod in the file manager. Just open nautilus and choose edit/preferences/media. You can change it to "ask me what to do"

I don't know how you could change the ipod recognition to generic mp3 though. I don't use my ipod much.

---

### Post by hollowhead on 2008-06-20
I've got a similar problem, the above will do, but in gutsy you used to be able to tell the system to start another application when an ipod was connected.  We use gtkpod for file transfer is there any way to tell hardy to start gtkpod when an ipod is mounted by default?  NH

---

### Post by Wobblybob on 2008-06-20
> **hollowhead said:**
> I've got a similar problem, the above will do, but in gutsy you used to be able to tell the system to start another application when an ipod was connected.  We use gtkpod for file transfer is there any way to tell hardy to start gtkpod when an ipod is mounted by default?  NH

I have the same problem and got it solved on this thread:

[http://ubuntuforums.org/showthread.php?t=270211]("http://ubuntuforums.org/showthread.php?t=270211")

This what I did to get Amarok as the default music player.
Copy and paste the following into a Terminal;

martin@linux:~$ sudo gedit /etc/gnome/defaults.list

then edit the file changing the line 'x-content/audio-player=rhythmbox.desktop' to 'x-content/audio-player=amarok.desktop' then save the file and close gedit.

This creates several launcher files - amarok.desktop - but doesn't create one in '/usr/share/applications'. To solve this copy and paste the following into the Terminal;

martin@linux:~$ sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

Now log out and back in, open Nautilus, go to [Edit], [Preferences], [Media] and in the [Music Player] option select Amarok from the drop down list. When you next plug in your iPod, Amarok will launch.
.

---

### Post by hollowhead on 2008-06-21
Thanks I guessed there would be a way of doing it.  The design change is irritating though....

---

