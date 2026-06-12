---
title: "No sound on firefox"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Wolfpack81 on 2008-04-28
When I play something on my desktop I get sound but If I go to youtube or another site with a video on it I get no sound.

---

### Post by amohanty on 2008-04-28
Start firefox from the command line in a terminal by typing firefox (and watch it spew a whole bunch of junk).
Try playing the youtube video and see if you see error messages.
Post the error messages or any messages dumped in the terminal.

AM

---

### Post by Wolfpack81 on 2008-04-29
Ok I typed firefox in it didnt display any other messages, Firefox just started I went to youtube and there was just no sound, no errors popped up in terminal.

---

### Post by amohanty on 2008-04-29
hmm. typically flash problems usually dump the flashplugin output into console for me. are you using the non-free flash plugin or the GPL SWF mozilla plugin??

AM

---

### Post by Wolfpack81 on 2008-04-29
Sorry dont really know much about this, How do you dump it.

Also I downloaded the flash player from the Adobe website and installed it through the terminal.

---

### Post by shawalli on 2008-04-29
I'm having the same problem.  It happens when you try to play sound or video on any website, but music players work fine

---

### Post by Wolfpack81 on 2008-04-29
Amo?

---

### Post by amohanty on 2008-04-29
Ok you can try the following, if you installed the flash plugin from the adobe site and installed it, the downloaded source should contain and uninstall script or should have it specifed in the README. 

If not it is most likely installed in /usr/local
You will have to manually remove the relevant files. fire up nautilus in sudo mode using
gksudo nautilus
and then find the files and remove them
Then remove any file that has flash in its name in the folder /usr/lib/firefox/plugins.

Then in a terminal:
sudo apt-get install flashplugin-nonfree

restart firefox and check again.

AM

---

### Post by lbarnes on 2008-04-29
i had the exact problem but it worked after a restart
of the computer, not just firefox.  you guys probably
tried that already though.

---

