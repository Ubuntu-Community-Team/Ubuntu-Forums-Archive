---
title: "Odd Exaile problem"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by jbysmith on 2008-02-01
Just did a (reasonably) fresh install of Gutsy, and installed Exaile, which I've used in the past with good results.

Now I'm having problems launching audio files through Nautilus.  

When I double-click an mp3, Exaile loads, then it shows the file name, then it just sits there.  It won't actually play it.  It's also displaying the file name "incorrectly", with %20's instead of spaces, etc.

If I do a "File -> Open Media", or use the media library, it'll play and display just fine.

I ran it via a terminal, but not getting any errors.  Here's a sample from double-clicking through Nautilis:

```

Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x89be638>}
Using multimedia keys from: gnome
Starting scan timer at 25.0
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Last playlist loaded
testing dbus service
file:///home/jen/Music/AC-DC/ACDC%20-%20Thunderstruck.mp3
ReplayGain support initialized.

```

I've tried the version from the default Ubuntu repository, as well as their development repo, but getting the same result.  I've used Exaile with no problems in Feisty, and other multimedia players are working correctly.  I'm rather fond of Exaile though so hoping to get this worked out.

Any suggestions?  Thanks

---

### Post by marco.pizziol on 2008-03-08
Try installing "Ubuntu restricted extras" from "add/remove" or using
```
sudo apt-get install ubuntu-restricted-extras
```

Hope it helps :)

---

### Post by phil_elson on 2008-05-31
Same problem.
Solution offered doesn't work. 

Note the command (to give an example)
$ exaile "/media/My Book/Music/ACDC - Greatest Hits/02. Problem Child.mp3"
works

is there anyway to get nautilus to put the filename in quotes? 
Maybe this is an exaile problem and should convert the file name to remove %20 for spaces.

---

### Post by eryksun on 2008-06-06
I figured out a workaround that solves this %20 problem. I overrode the default launch command, changing %u (URL) to %f (file). Here's the sequence of commands/edits:

```
sudo mkdir /usr/local/share/applications
sudo cp /usr/share/applications/exaile.desktop /usr/local/share/applications
sudo nano /usr/local/share/applications/exaile.desktop

```
Scroll down and change the line "Exec=exaile %u" to
```
Exec=exaile %f
```

Save and exit. Finally, refresh the desktop database:

```
sudo update-desktop-database -v
```

---

### Post by natibo on 2008-07-20
Thanks much.  I had the same problem and that fix worked great.

---

