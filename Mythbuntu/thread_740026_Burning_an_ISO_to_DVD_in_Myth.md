---
title: "Burning an ISO to DVD in Myth"
date: 2008-03-30
forum: Mythbuntu
---

### Post by Levander on 2008-03-30
I used mythdvd to rip a DVD to an ISO.  Can I now burn that ISO to a black DVD-R?  I tried mytharchive.  But, I keep getting errors that make me think it wants an AVI file and doesn't understand ISO's.

So, can I use myth to burn an ISO to a blank DVD-R?

If not, what program is most myth users using to burn them?  I've never done this under Linux before.

---

### Post by volkswagner on 2008-03-30
I have not used myth to burn any DVD's yet.  I like K3B for all my burning.

---

### Post by tgm4883 on 2008-03-30
> **Levander said:**
> I used mythdvd to rip a DVD to an ISO.  Can I now burn that ISO to a black DVD-R?  I tried mytharchive.  But, I keep getting errors that make me think it wants an AVI file and doesn't understand ISO's.

So, can I use myth to burn an ISO to a blank DVD-R?

If not, what program is most myth users using to burn them?  I've never done this under Linux before.

Can you post some of these errors?

> **volkswagner said:**
> I have not used myth to burn any DVD's yet.  I like K3B for all my burning.

Not trying to be mean, but how is this productive to this conversation and not just a waste of bandwidth?

---

### Post by Levander on 2008-03-30
Not that there isn't entirely too much cruft on Ubuntu Forums.  But, volkswagner was just recommending a DVD burning app he likes.  Now, if a bunch of snarky newbs hijack my thread saying "me too", then yeah, it becomes a waste of bandwidth.

I can post some errors, but I'm really under the impression that mytharchive just doesn't support burning ISO's to DVD.  The errors were like "failed to pull video stream out of <file name>.iso".  Plus, when I go to find a file to burn, and not just a video (file and video being used in the same sense mytharchive uses them) the select box only lists avi files and ignores all the iso files in the same directory.

If you're saying it does support burning ISO's then I definitely need to check those errors out more thoroughly, but if it doesn't support it, why bother?  Are you saying that it does support it?

---

### Post by volkswagner on 2008-03-30
> **tgm4883 said:**
> Can you post some of these errors?



Not trying to be mean, but how is this productive to this conversation and not just a waste of bandwidth?

> 
If not, what program is most myth users using to burn them? I've never done this under Linux before.


I just thought I was answering the OP's question.

Now I am wasting bandwidth.  :lolflag:

---

### Post by teet on 2008-03-30
In gnome, I always just pop open nautilus, right-click on the file, and then click "burn iso to disc" (or something like that).  I'm not sure if thunar has that ability.

-teet

Edit:  make sure your "temporary" folder for mytharchive has the proper permissions.  My temporary folder is /video/temp...so I had to do a "sudo chmod 777 /video/temp" to get mytharchive to work.

---

