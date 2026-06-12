---
title: "Burning WMV to DVD"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by Patriot1776 on 2007-11-16
Can mencoder be used to take a WMV file into a DVD burnable format? I've got a couple large WMV files (350-400 MB) that I want to put on a DVD disc. Also what programs would work best for burning a DVD from this format?

---

### Post by ron999 on 2007-11-16
Hi
I don't know whether mencoder can be used or not - I'm not that clever.

If I was doing this job I would use 
DeVeDe to create an ISO file of the DVD
then VLC to test view the ISO file
then K3b to burn it.

These three applications are in the repos.
:cool:

---

### Post by Patriot1776 on 2007-11-16
In the repos, the Ubuntu repositories?  Of those three, I've got VLC.  Lemme check the program installer.

Thanks much for replying.  I was starting to lose confidence in this place from not getting any responses to my questions or anybody even telling me if I was asking them in the right places or not.

---

### Post by ron999 on 2007-11-16
> **Patriot1776 said:**
> In the repos, the Ubuntu repositories?  
Yes, in the Ubuntu repositories.
Use Synaptic Package Manager to install them.

System > Administration > Synaptic Package Manager

Good luck
8)

---

### Post by Patriot1776 on 2007-11-16
Burn worked, but the DVD wasn't playable.  Any ideas on what I need to do in DeVeDe?

---

### Post by ron999 on 2007-11-17
Hi
Try to break the problem down.
If the ISO file played OK in VLC then probably something's gone wrong when burning it.
If the ISO file doesn't play OK in VLC then probably you need to experiment with different settings in DeVeDe.

---

### Post by Patriot1776 on 2007-11-17
Found out what happened, I didn't set the frames and perspective to NTSC before starting the conversion in DeVeDe.  Now I've got a DVD that works good with one of them.

Then proceeded to try and make a disc with both of them on it, with a title leading to each, but I don't think DeVeDe has provisions for inserting a title screen and titles.  In case, I have to include a new title for each separate file I want on the disc right, to be able to freely switch between them.

When I tried making that one, with both of them on it, I set the other file as the first one, and it doesn't have sound, and that's I know because I need to update my win32codecs.  Those found in the software installer or in Synaptic?

---

### Post by ron999 on 2007-11-17
Hi
Well, you're getting there.:)

You're right, DeVeDe won't let you create a menu.
So if you make a DVD with both clips they will just play one after the other.
You will have to skip through to the right place if you only want to view the second one.

I don't know about the codec thing. But make sure that the original file plays with sound OK before you change it into a DVD.

If you want to make a DVD with a menu then the app to use is 'tovid'. It's more difficult to use.

This is the link for tovid:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

This was a simple menu that I made with tovid:-[[img=http://img523.imageshack.us/img523/8160/screenshot0fp3.th.png]]("[url=http://img523.imageshack.us/my.php?image=screenshot0fp3.png)"][[img=http://img523.imageshack.us/img523/8160/screenshot0fp3.th.png]](http://img523.imageshack.us/my.php?image=screenshot0fp3.png)[/URL]

Don't give up
8)

---

### Post by Patriot1776 on 2007-11-17
I'll try asking on another part of the site about the codecs thing.  I think the problem is that the wmv file that the sound is not working on in VLC, running from a terminal it comes up saying that 'wmap' is not supported, which I checked another way and is the audio codec used.  Probably start another thread in here on it.

I'll see if tovid can let you add more stuff so it's more complete as a DVD.  Learn how to title chapters so I can stamp up parts of the vids.  I hope it can do that, as both of these vids are over two hours long, but aren't real movies, just footage.

---

