---
title: "ManDVD busted!"
date: 2010-12-12
forum: Multimedia Software
---

### Post by dxrey on 2010-12-12
This program has always worked well for me, but after the last big upgrade to current kernel I ran it to the part where you take a snapshot of a scene to use as a menu background. At that exact point it crashed, disappeared.

Restarting the program I get this script:  "Program seams [sic] to be running! Else please remove lockfile .run in .mandvd/ directory" and it it will not allow the program to run.

Needless to say, I have hunted for anything of that description in the filesystem without success. I have restarted the computer many times. I have uninstalled and reinstalled the program twice, yet I get the same message and failure to start. 

Perhaps someone could guide me through terminal to get at the offending file?:(

---

### Post by ender4 on 2010-12-12
it looks like the program crashed, and didn't remove a lock file.  So you simply (hopefully) need to remove the lock file.  From the error message it looks like the file is located at /home/<username>/.mandvd/.run, so typing "rm ~/.mandvd/.run" should remove it, and get your program working again.  Alternatively you could just navigate to .mandvd and remove .run from a file manager. But you will have to enable displaying hidden files in order to see the .mandvd folder and the .run file.

---

### Post by dxrey on 2010-12-12
Thanks - dang hidden files - I had forgotten to check that. 

I clicked "show hidden files" this time, went to the "home/<username>/.mandvd" file and opened it - still no .run file apparent, but I sent the .mandvd folder there to the trash, emptied, and now the program opens and runs as before.

Thanks again!

---

