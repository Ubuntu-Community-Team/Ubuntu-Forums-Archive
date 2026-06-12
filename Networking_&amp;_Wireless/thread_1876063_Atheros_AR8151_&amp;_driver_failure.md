---
title: "Atheros AR8151 &amp; driver failure"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by 3dbDown on 2011-11-05
Setup is MSI H61M-P23/B3 Sandy bridge mainboard with built-in 1969-1083 Atheros chip, distro is Slackware 13.37 (linux 2.6.37.6). Device shows in lspci output, but apparently the atl1e driver is incompat with linux 2.6.37.6, so no eth0 displayed by ifconfig. Note that LQ.org redirects to the ubuntu formus for the solution... which is why I'm bothering folks "out of band"
 
Don't know why FrazAli (also a Slackware user) had success using **_m0gwai's solution_** ( [http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122) ) and I don't, but when attempting to patch (step 1) I get failure:
 
Note: At first I was trying to patch the source atl1e_main.c in the "build" directory, which failed, so I changed to the /usr/src/.../atl1e/ dir, but the same problem persists.
 
@ can't find file to patch at input line 4
@ perhaps you used the wrong -p or --strip option?
@ The text leading up to this was:
@ --------------------------------------
@ |diff -urN src-old/atl1c_main.c src/atl1c_main.c
@ |--- src-old/atl1c_main.c 2011-01-28 13:32:59.277576319 +0100
@ |+++ src/atl1c_main.c 2011-01-28 11:48:39.677573301 +0100
@ --------------------------------------------------
@ File to Patch:
 
Note: In **m0gwai**'s discussion and code block, it *appears* that the code will patch either the atl1c **or **the atl1e driver/module file, but when I input the atl1e_main.c where asked which file to patch, I just get many more failure blocks (way too many to reproduce manually here, the machine is an island without a connection)
 
I am truely a "Patch Virgin" ! This IS my first rodeo.
 
Are failure reports nominal in patching?
 
I get a null response when I: 
diff atl1e_main.c atl1e_main.c.orig
... so it appears that nothing has happened.
 
any thoughts?

---

### Post by 3dbDown on 2011-11-06
Late update:
Not sure why the patch didn't work against the distribution copy of the atl1e_main.c, but as you can see above, it didn't
(used that since it was already in the "proper location" for these files.... perhaps dumb thinking!)
I remembered reading somewhere that there was at least some report of some files in this topic haveing become corrupted, so I beat the patch file against the copy available from the link on m0gwai's solution.... and that played like a stratavarius violin:
the patch went perfectly
the make went perfiectly
(at which point I thought I needed to go clean up the garbage I had created in the first attempt)
so I set the old driver (atl1e.ko) aside and moved the new one into it's place.
made sure the old driver wasn't still lurking in the kernel with a modprobe -r and then loaded the new one.... ifconfig showed me the eth0 was up, and I was able to ping my local router. Yee-haw!
Never did do the "install" (oops.. that'll probably bite me in the rear some time... but for now: success! )
 
all the new files are in a separate directory under root, so I sould be able to fixit again, should a future sw upgrade need assistance too.

---

