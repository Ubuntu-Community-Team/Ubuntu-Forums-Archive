---
title: "mythbuntu default storage groups"
date: 2011-04-25
forum: Mythbuntu
---

### Post by romerje on 2011-04-25
I had to reload my mythbuntu b/c I couldn't get myself out of the reset from Xserver.  ...so now I need to reset everything.  Before the reload I had found a txt dir for the four default storage groups on MythTV.  I was able to edit the "video" one so that that my videos were redirected to an alternative HDD.  It worked perfectly.  I don't plan on using the main drive for media storage,  So I want to change the path of the default storage directories.  This is the only way that I can get my media to show up on my WD Live device.  Anyone can give me the path where to find it?

Thanks

P.S.   /var/lib/myth is not what I am looking for....I am looking for the directory that show the path for each default location  "video, music, pictures, recording"  ---this was done on the previous load and was working exactly the way I needed it to

Thanks for your help

Jennifer

---

### Post by tgm4883 on 2011-04-25
> **romerje said:**
> I had to reload my mythbuntu b/c I couldn't get myself out of the reset from Xserver.  ...so now I need to reset everything.  Before the reload I had found a txt dir for the four default storage groups on MythTV.  I was able to edit the "video" one so that that my videos were redirected to an alternative HDD.  It worked perfectly.  I don't plan on using the main drive for media storage,  So I want to change the path of the default storage directories.  This is the only way that I can get my media to show up on my WD Live device.  Anyone can give me the path where to find it?

Thanks

P.S.   /var/lib/myth is not what I am looking for....**I am looking for the directory that show the path for each default location  "video, music, pictures, recording" ** ---this was done on the previous load and was working exactly the way I needed it to

Thanks for your help

Jennifer

I think what you are looking for is in mythtv-setup. You can define storage groups there. If not, then you need to delete /var/lib/mythtv/videos and create a symbolic link.

---

### Post by romerje on 2011-04-25
by running mythtv-setup, it just throws me into the GUI.  what i am looking for is a txt file that I am able to edit with a txt editor.

---

### Post by tgm4883 on 2011-04-25
> **romerje said:**
> by running mythtv-setup, it just throws me into the GUI.  what i am looking for is a txt file that I am able to edit with a txt editor.

That file doesn't exist. All of the storage group information is kept in the database

---

### Post by romerje on 2011-04-25
> **romerje said:**
> I had to reload my mythbuntu b/c I couldn't get myself out of the reset from Xserver.  ...so now I need to reset everything.  Before the reload I had found a txt dir for the four default storage groups on MythTV.  I was able to edit the "video" one so that that my videos were redirected to an alternative HDD.  It worked perfectly.  I don't plan on using the main drive for media storage,  So I want to change the path of the default storage directories.  This is the only way that I can get my media to show up on my WD Live device.  Anyone can give me the path where to find it?

Thanks

P.S.   /var/lib/myth is not what I am looking for....I am looking for the directory that show the path for each default location  "video, music, pictures, recording"  ---this was done on the previous load and was working exactly the way I needed it to

Thanks for your help

Jennifer

Solved:  (wasn't sure how to put "solved" in the header"   anyway....had to set up samb.conf  the setting I am looking for are there.  you sign in as root user and then I can edit the way i need to.

---

### Post by tgm4883 on 2011-04-25
> **romerje said:**
> Solved:  (wasn't sure how to put "solved" in the header"   anyway....had to set up samb.conf  the setting I am looking for are there.  you sign in as root user and then I can edit the way i need to.

I believe it's under thread tools at the top.

And yea, samba configuration is way different than what I thought you were talking about

---

### Post by romerje on 2011-04-28
> **tgm4883 said:**
> I believe it's under thread tools at the top.
 
And yea, samba configuration is way different than what I thought you were talking about
 
 
Thanks for your quick repsonses....still way new to all this Linux stuff.....still figuring out all the lingo and correct terminology....thanks Jen

---

