---
title: "Home Networking/PC Syncing?"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Algus on 2009-10-13
Hey guys, 

I know what I want to do but I'm not even sure what to type in to try and search for explanations so here goes.

I've got a desktop PC running Windows Vista Home Premium 32-bit and a laptop running Ubuntu 9.04 64-bit.  

I'd like to be able to sync a few folders between these two machines (mainly the music folder, though documents as well even though I keep most of that stuff online with Google Docs). 

Now when I was running Vista on both machines I know that I could access either remotely through "Network" on Vista if they were both connected to my router.  (Both are operating over wireless-G connections as my router had to be centralized to hit all the machines in my house)  

Is there a good way to sync these two machines over my network? (If there's some sort of "sync manager" prog so I don't have to do it by hand, that'd be awesome) or am I looking at having to set up an external hard drive to swap data between my machines? 

I've got roughly 15 GB of data that I'd like to sync so I'm assuming any solution isn't going to be super fast.  

Thanks for any help.

---

### Post by cb951303 on 2009-10-13
there is rsync but beware its a CLI application

---

### Post by Boondoklife on 2009-10-13
Honestly the best way to do it is some sort of a storage area being the central repository. I really would not mess with client syncing unless you are absolutely sure only one pc with have made changes at a time as you could end up with a clash.

You could just setup a samba share on the ubuntu box and be able to access it just like a windows box but that would not do the syncing.

Again I cant say it enough be careful with syncing as you can loose data if you are not careful.

If you do go with a central file server then the best way to do it is to setup one user with RW privs and have everyone else have R that way you know only one person can update the files.

---

### Post by Algus on 2009-10-13
Boondoklife,

Thanks! Looked into it, messed around a bit with Samba and figured out how to tinker with my share and network settings in order to connect to my PC through my laptop.  (Although, unfortunately, I can't quite figure out how to do it in reverse - a byproduct of Windows not understanding ext3 perhaps?) 

Copied a few files manually (Guess I'll have to wait until tonight to try and get most of the data) just to see if it worked.  

I read about something called Unity when I was trying to hunt for some other clues on what the best route to go would be.  Do you know anything about that? 

Side note - when copying data between my computers when both were running Vista I usually ended up borking my router and needing to reboot it to get internet back up.  When transferring the data via Ubuntu it worked without a hitch and I was able to get right back to the intrawebs.  Oh Linux, how I love you.  

Marked the thread as 'solved' but I'm happy to take any other suggestions or read experiences from other folks who need to transfer data (esp larger volumes) between machines!

---

### Post by Boondoklife on 2009-10-13
No idea on unit, if i get some time ill take a look and see what it is. If you are just trying to get windows shares to work both ways, then look in the howto's there is a great doc there that will get you going.

---

### Post by Algus on 2009-10-13
Was hoping for something a bit more advanced (some sort of manager I guess; spoiled by the manager programs for my media devices I think) but two-way sharing will get the job done.  

Will check out the how-to guides, thanks for pointing me in that direction.  ):P

---

