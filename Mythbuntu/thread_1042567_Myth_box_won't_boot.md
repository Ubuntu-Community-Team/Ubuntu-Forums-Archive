---
title: "Myth box won't boot"
date: 2009-01-17
forum: Mythbuntu
---

### Post by tlehotsky on 2009-01-17
I'm a noob (I'm running Mythbuntu 8.10)

So far I've built the box, got all the software loaded, added a hard drive, mounted, shared, even got so far as to be able to remote into with a windows box - all by searching and researching,and not posting dumb questions...until now

I've run into this problem three times, the last time I've booted after each change to check that everything was ok.

Right now when the machine boots I see the mythbuntu bar progress all the way accross, then the mouse pointer changes to an arrow, then to the outline of an x.  At that point it indefinatley hangs.  Problem is, I'm not sure how to even acurately search on this, my first couple attempts futile.

Can someone explain to me where I'm at in the boot process?

Evertime it happened soon after I installed nx client/server.

thanks for any direction...

Tim

---

### Post by tlehotsky on 2009-01-18
just to be clear, each time the box was stable and running and rebooting only to start hanging at this point later.  

I've also tried recovery mode and rebuilt broken packages to no avail....

---

### Post by tlehotsky on 2009-01-18
rebuilding again, I will keep track of my steps, maybe some can point out where they think its going awry..

install mythbuntu 8.10 using advance install option
install nautilus (find it easier to make samba shares this way)
install debinstaller
setup samba shares

restart (successfully) 

install nx client, node, and server (in that order)
enable remote (settings/login window - remote tab- set same as local)

restart (successfully) 
add ubuntu desktop as a system role (system/myth control center/roles)


restart (successfully) 

setup VNC server following the instructions here: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

restart (successfully)

enable vnc services via system/myth control center
run update manager, install all updates

restart - bamm it hangs now


note:each rebuild I've tried somewhat different order, this time I did the updates at the end instead of beginning hoping that made a difference...

---

