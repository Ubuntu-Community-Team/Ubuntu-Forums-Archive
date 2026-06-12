---
title: "diskless server/client control center operation"
date: 2009-11-29
forum: Mythbuntu
---

### Post by jimp180 on 2009-11-29
when I make changes in mythbuntu control center on a frontend it causes the same changes to be applied to the backend diskless server. for instance, if I change the system role to include frontend it shows on the "backend only" diskless server that it now is a backend + frontend in the control center on that machine.

the same thing happens with plugins, I dont need the plugins on the server but if I install them on the frontend machine they show to be installed on the server also.

is this normal operation? 

maybe I have something wrong in my setup, I am using a separate machine for a dhcp server and have my filename set as "/ltsp/i386/pxelinux.0" and root path set as "/opt/ltsp/i386" (these settings I gleaned from the example file)

if this is normal operation using the control center on the frontend, is there a beter way to make changes to an individual frontend that wont affect the settings on the backend or other frontends?

I would like to get this working right now its not a workable frontend because when I try to add support for my mce remote via the frontend control center it really is added to the server machine and I dont want to run a 300 ft usb cable to the room the server is in so I can change channels on my frontend box!

---

### Post by blackoper on 2009-11-29
no that is not normal operation of diskless clients. My clients do not do that.

I made/followed this thread to manually build mine after the release of 9.10 since it doesn't have the diskless tab anymore: [http://ubuntuforums.org/showthread.php?t=1305845]("http://ubuntuforums.org/showthread.php?t=1305845") I know it works because I just built the diskless image this weekend for my parent's home following the instructions and it worked like a charm (other than needing to use avenard's repo to install nvidia 190.42 drivers)

Since I did not have any issues like that I would assume you somehow built it wrong. It sounds like you are shareing the /root file systems of both boxes somehow

---

### Post by jimp180 on 2009-11-30
actually that is the thread I used to build my image, I used your post #5 in that thread. I was a little concerned about the username/password line but I entered it just like you had it, then when my client first booted it asked for a password and I used my usual user/password combination. I wonder if this caused the problem?

I dont know what to do at this point but to start over, I assume I can just delete the ltsp folders in /var/lib/tftpboot and /opt then try again.

---

### Post by blackoper on 2009-12-01
I created a new user of frontend1 and a password and didn't reuse any user from the master backend. It should have failed out if you used a current username (that's what mine did) but that could explain it as it may somehow be sharing the root file structure. 

I checked again and I can't even get the mythbuntu control center to complete correctly on the frontends when I make changes. I just manually setup everything on the diskless image as far as a I could and then edit each frontend as needed. I don't have access to the working frontends I made this weekend as they are about 2 hours away and I didn't setup ssh access

---

