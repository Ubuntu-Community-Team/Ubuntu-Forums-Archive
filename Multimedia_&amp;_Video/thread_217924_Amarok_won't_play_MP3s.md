---
title: "Amarok won't play MP3s"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by MiniZiper on 2006-07-17
I know, install libxine-extracodec, but when I do I get this:
[COLOR="DarkOrange"]sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate
[/COLOR]

I have enabled all my repositories... And I upgraded to amarok 1.4.1... but still no mp3 would work. It just starts and ends without palying anything....

Help!!

---

### Post by jrjr on 2006-07-17
I know its not a solution but I switched to XMMS. Its a sweet player... similar to Win Amp

---

### Post by Rackerz on 2006-07-17
Hmmmm, did you reboot recently and try again? Try searching for that package in Synaptic.

---

### Post by MiniZiper on 2006-07-17
I reinstalled amarok, amarok-xine and all of that. I rebooted... but no fix :(
what repository am I supposed to have to get libxine-extracodec ??
any more ideas??

---

### Post by T700 on 2006-07-17
See my sig for the link to Automatix.  Run it and it will take care of all this for you.  Safe and effective.

Paul

---

### Post by MiniZiper on 2006-07-17
Automatix or w/e is nice. I have google earth, gaim, and java (which is a pain in the rear end with kubuntu) installed. But, it didnt fix amarok... sigh... it just reinatalled it. Now it Amarok syas "No Mp3 support". at least now it tells me what its going on... and no sudo apt-get install libmad0 libxine-extracodecs does not work for some odd reason...:mad: 

thanks for your help... but any more ideas?? like, what repository i need for  libxine-extracodecs?? or something?

---

### Post by MiniZiper on 2006-07-17
No wait!! I slected audio & video codecs in automatix, now it works!!!! thank you so much!!

---

### Post by T700 on 2006-07-18
> **MiniZiper said:**
> No wait!! I slected audio & video codecs in automatix, now it works!!!! thank you so much!!

Glad it's going now.  Have fun!

Paul

---

### Post by butchd on 2006-07-19
I was having the same issue (i.e. alsamixer checked out and my sound card was detected) and Automatix fixed me right up. This is the best free OS I've ever seen. That said, it's still not ready for the average user. It takes a warped mind to wrap around it.

---

### Post by T700 on 2006-07-19
> **butchd said:**
> I was having the same issue (i.e. alsamixer checked out and my sound card was detected) and Automatix fixed me right up. This is the best free OS I've ever seen. That said, it's still not ready for the average user. It takes a warped mind to wrap around it.

That's a fallacy to equate your limited experience as being the general experience.  Just because it isn't what you're looking for, doesn't mean that "it's still not ready for the average user."

Paul

---

### Post by Nightsapper on 2006-07-24
Actually that depends on your definition of average user.  Your fallacy is assuming the "average user" should be a geek, not a mom or pop.  That's elitism, and bad - bad for Ubuntu in that it needs to be spread widely, and bad for you because you are making erroneous assumptions about the user base. 

The "Average Windows Users" would not expect to chase hither and yon for libraries to decode MP3s for his media player - he would expect that when it installs, it would have that, the most common format for music files, "built in".   ](*,) 

And you must admit - scrabbling about for "libxine-extracodecs" is not the first thing that comes to mind.  As you can see from googling for it, many others give up and go to XMMS.  The problem is two fold: one that when the Xine setup is loaded for amaroK it doesn't suggest the user get the MP3 codec for the Xine driver, and two (worse) the codec lib is not readily available in a "normal" repository. ](*,) 

You must admit that these are NOT in the usual places/repositories, or else they would have been found in synaptic with a search for "mp3" or "xine" or "codec".  The fact that you recoomend that they run yet another app indicates that amaroK and its codec dependencies/xine-situation are flawed in the implementation for the *average* user.

So "inexperienced user" is no excuse for what an "average" user would consider to be "crappy" functionality of a beautiful program that doesn't work (because it doesn't play his MP3 "out of the box") nor does it even tell him why his play list just "bumps along not playing anything at all".  To the average computer user, it *appears* defective.  Yes I realize that a lot of this is probably the fault of interfering intellectual property laws, etc.  :-k 

Geeks live with it, and like the internet, we see damage and route around it.  "Average users" in general do not.  That's why Ubuntu (and Linux, and amaroK and similar things), as nice as they are compared to what we had back in the 90's (or even last year), well they simply aren't ready for prime time until common items like a media player work at the effortless level that just about every Mac app does "out of the box" (even freeware), or even the realative ease of MS Media Player.

Don;t get me wrong: its ready for my desktop though (and I appreciate the power and flexibility), and that's good enough for me. 8) 

By the way, here are repositories that have the libxine-extracodecs.  

```

deb http://se.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper multiverse

```

I got that info from [Original Thread on the Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?p=1266646") via Google.

Somehow this needs to be put into a FAQ for amarok users on deb based systems.

I gave up when Synaptic couldn't find it in Universe and elsewhre in the "normal" set of repositories for a Ubuntu user (the ones that "come with" synaptic on a 6.06 install).  

I discarded amaroK because it wasn't worth spending my recreational time hunting a solution for something that shouldn't be a problem to begin with.  But I may revisit it, now that I've had time to think about it and the proper repository is available.  A quick check of "xine" with the above resources added to my repos shows the drivers to be right there - Im queuing them for install.

Regards

---

