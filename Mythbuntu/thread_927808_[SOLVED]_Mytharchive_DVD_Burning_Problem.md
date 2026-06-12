---
title: "[SOLVED] Mytharchive DVD Burning Problem"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Ronno6 on 2008-09-23
I'm running Mythbuntu 8.04.1 on a Dell Optiplex 370. I'm trying to burn a recorded TV show to DVD using Mytharchive. Everything seems to go fine till the actual burning process with  growisofs .
Burning stops during the first commercial segment , and the Log Viewer gives me the line: Failed while running growisofs.
                   Result 1, command was: growisofs -dvd-compat -Z/dev/dvd -dvd-video -V "Modern Marvels"/var/lib/mytharchive/temp/work/dvd

Please check the troubleshooting section of the README for ways to  fix this error.

README offers no solution, only to make sure that the user has permissions for the dvd device, which I have enabled. I have a hard time believing that writing would start, then quit 25% of the way in if permission was not granted in the first place. 

Anyone have any ideas?

---

### Post by klc5555 on 2008-09-23
There have been threads in the forum about problems with the version of growisofs in Hardy. Check the thread from a day or so ago titled "[Solved] Mytharchive Hell". Perhaps changing the version of growisofs might also solve your particular symptoms.

Good luck! :)

---

### Post by Ronno6 on 2008-09-23
A-OK !! Thanks to you for that one (as well as the help given to the original poster by Nikas) Apparently that did the trick, and the burning process was a success. 

One down, one to go ( transcoding problem on my other post.)

Thank you again.

---

