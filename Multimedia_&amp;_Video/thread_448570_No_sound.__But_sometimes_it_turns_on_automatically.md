---
title: "No sound.  But sometimes it turns on automatically?"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by mmilitia9 on 2007-05-19
I just installed Ubuntu the other day and have been enjoying it ever since.  I got everything to work!   My Nvidia Geforce FX 5500 didn't work at first but I got it to work.  Then.. the next issue was my Sound Blaster Audigy 2 ZS.. Which I'm still having an issue with still.

I don't get it because... For the last 2 days I've been listening to music on Ubuntu  feisty perfectly fine through all of my speakers(I have a 5.1 system) and it worked great!

Now.. I don't have any sound at all.. I don't get it because some times it kicks in and sometimes it doesnt. For example.. I shut down the PC last nite and booted back into  feisty and my sound worked.. I rebooted into Windows XP to grab my bookmarks and came back to  feisty with no more sound..  Just like that it was gone again... So I thought maybe  feisty needed to be shutdown in order to keep the sound going.. but that didn't work either..

I don't think it's any more options.. I think something broke.. 

I have everything in the Volume Control where it needs to be and it worked fine for the last 2 days.  I mean.. I have downloaded some software from the add/remove section.. Maybe it broke it?  I don't know..

I really dont know what kinda info to give you since my sound settings worked for 2 days strait prior to the lack of sound incident... but if theres anything I could do to help solve this case just ask!


Thanks again,

Dominick

---

### Post by mmilitia9 on 2007-05-19
Ahh.  I found the answer myself.  

"I had a similar problem and the case was that my soundcard wasn't set as default.

Try
sudo asoundconf list
This will return a list of your soundcards
sudo asoundconf set-default-card <name of your soundcard from the previous list>
reboot"


I did that and everythings perfect again.

---

### Post by tree trunk on 2007-05-19
I agree, something is wrong.](*,)

My sound worked flawlessly in Ubuntu 6.10,  when I upgraded to 7.04 things became unreliable. Sometimes there is sound, sometimes there isn't.

Always looking for something that works, I installed the Gnome option for Mandriva Free 2007.1 (the "Spring" version).  The same sound problem exists with it.

I think Mandriva 2007.1 and Ubuntu 7.04 have little in common, save Gnome 2.18.  So I'm surmising that that is where the problem lies.

I may be wrong.  But I think looking to Gnome for a bug would be productive.

---

### Post by dermann on 2007-05-19
Don't know if this will help, but it worked on my laptop with similar sound issues.
See thread I just posted:
[http://ubuntuforums.org/showthread.php?t=448588](http://ubuntuforums.org/showthread.php?t=448588)

---

