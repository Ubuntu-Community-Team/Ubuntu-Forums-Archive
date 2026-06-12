---
title: "Audacious - won't start up"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by skydiverQ on 2008-04-04
Disclaimer:  total newbie.

That said....

I have been trying to get Audacious to work.  I know I had it working at some point, lord only knows when...I have fooled around with a variety of distros until settling on Xubuntu, which in general is working quite well.

Here's where I am at:  When I originally tried to install it, it would not let me, because I had to add a couple extra libs, one I recall being mowgli.  resolved all the dependencies (I think that's what I did...?) and was finally able to install it, and the plugins.  But when I click on the icon to start it, nothing comes up.  I tried purging it and reinstalling via apt-get (first time was using synaptic package manager) but I still get the same result.  When I try to sudo it in terminal, I get the following:

john@desktop:~$ sudo audacious
I/O warning : failed to load external entity "/root/.config/audacious/playlist.xspf"
Illegal instruction (core dumped)
john@desktop:~$ 

There's a pause of about ten seconds between those two outputs, then back to the command prompt.

Thoughts?

---

### Post by Seti on 2008-04-04
Have you tried checking to see if its running after you launch it (check in System Monitor; System>Administration>System Monitor) see if its there under the 'Processes' tab.
If it is running then its probably just hidden and you didn't enable the Status Icon plugin, I dunno.

It's normal for you to get that error message if you run ```
sudo audacious
```

I'd say rm -r /usr/lib/audacious and anywhere else there's audacious config files and reinstall it. Quick and dirty.

---

### Post by skydiverQ on 2008-04-04
I deleted it as you instructed, then also marked it for complete removal in synaptic.

I then reinstalled, it appears to have installed fine....meaning no erros or messages.

Same behaviour again when I try to run it now...when I check the system monitor, it shows up for a few seconds after I run it, then disappears....

---

### Post by ftmichael on 2008-04-26
I just had the same issue (and audacious-crossfade was not installed), and managed to fix it by doing this:

Delete and purge audacious like you did before.

Delete the directory ~/.config/audacious - you can go to Places-->Home Folder, press Ctrl H to show hidden files and directories, and then go into .config, and delete audacious.  Delete it from your trash as well.

*Then* reinstall audacious.

Michael

---

### Post by legalizemeth on 2008-04-27
The audacious-crossfade package seems to be causing the problem.  I removed it and got Audacious back.  See here: [http://ubuntuforums.org/showthread.php?t=706497](http://ubuntuforums.org/showthread.php?t=706497)

---

