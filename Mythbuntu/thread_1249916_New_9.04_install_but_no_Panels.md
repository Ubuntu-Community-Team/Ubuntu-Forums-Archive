---
title: "New 9.04 install but no Panels"
date: 2009-08-25
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-08-25
So I am trying to upgrade by installing 9.04 into a new partition.  The live CD looks good.  3 runs though the install, once I get the install complete there are no panels.  I can right click on the desktop to get to programs, but all my panels are gone.  If I go into Xfce 4 Settings Manager and try to select Panel, it does nothing.  

I can try working around, but this is just odd.  I guess I can leave it on 8.04.1 since I didn't lose that partition.  Any thoughts.  (Hopefully I didn't miss something obvious, but googling for mythbuntu panels wasn't getting anything.)  

I have tried using the nVidia and open source video drivers.  There just isn't that much I can see in the install that should be making much difference.  (Video is on board 6150 SE that has worked reasonably well with 8.04.)

--
So, I thought I could set grub to boot to my old version but I don't have /boot.  I expect it somehow is seeing my other partition's /boot.  Could this be at all related?  I haven't yet changed my fstab.  (on the install, I am having it install to a new ext3 partition on the same disk and telling it to mount as /.)

---

### Post by Boppy3125 on 2009-08-25
I don't know what I am smoking but I do have /boot.

I can't easily go back to 8.04 because I have a busted upgrade there.  I started the upgrade and then accidentally canceled out of it mid way now its busted (at least video is.)

I don't know what to do next.  This sucks.  I might try finding my 8.10 CD I used for my other frontend.

---

### Post by nickrout on 2009-08-26
> **Boppy3125 said:**
> I don't know what I am smoking but I do have /boot.

I can't easily go back to 8.04 because I have a busted upgrade there.  I started the upgrade and then accidentally canceled out of it mid way now its busted (at least video is.)

I don't know what to do next.  This sucks.  I might try finding my 8.10 CD I used for my other frontend.

Are they off the edge of the screen, and you are suffering from overscan?

try ctrl-esc to see if a menu drops down?

---

### Post by Boppy3125 on 2009-08-26
> **nickrout said:**
> Are they off the edge of the screen, and you are suffering from overscan?

try ctrl-esc to see if a menu drops down?

Thanks, no.

---

### Post by Boppy3125 on 2009-08-26
8.10 installed fine.  Doing the dist upgrade to 9.04 seems to work.  I guess I have a work around.

---

