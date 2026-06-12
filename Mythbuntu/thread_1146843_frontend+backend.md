---
title: "frontend+backend?"
date: 2009-05-03
forum: Mythbuntu
---

### Post by clopnaz on 2009-05-03
I have a mythbuntu machine I made, and I want to be able to record a dvd to it and play it on my ubuntu machine across the room. Is this a classic frontend/backend setup? Is there a way to install a frontend on ubuntu? Or can you only watch tv from a frontend?

---

### Post by andrewc6l on 2009-05-03
You can do pretty much anything on a frontend that you can do on a standalone installation (which, if you think about it, is really just a regular frontend talking to a regular backend which just happens to be running on localhost). If your network has sufficient throughput, another frontend sounds like the solution.

In the past, you could boot the Mythbuntu install CD and run it as a frontend without installing anything - which would be a good test. I haven't tried it on 9.04, though - don't know if it still works.

---

### Post by clopnaz on 2009-05-03
okay. I thought this was the case. The problem is, I installed mythbuntu and then tried to install mythtv on another computer and I couldn't seem to see or play any of my dvds. Could it be a port forwarding issue?

I'm reinstalling to jaunty to make sure all of my settings are correct and trying again today.

---

### Post by andrewc6l on 2009-05-04
Are the DVDs in a DVD reader on the backend, or one on the frontend? I confess I haven't tried doing that remotely - but it's certainly possible the frontend is looking for the DVD to be in a player on the backend and the DVD is in the frontend, or vice versa.

What sort of error messages do you see if you run mythfrontend from the console and then try to play a DVD?

---

### Post by clopnaz on 2009-05-04
I'm about to go to bed, but last I tried to play a dvd it just goes to a blank screen and then goes back to the menu. I just ripped a cd on the backend and can see the music from the frontend, but not the cd. If I try to play the music, I get the error "mythmusic has encountered the following error: DecoderOgg: failed to open input. Error 5."

---

### Post by SiHa on 2009-05-06
Not sure what you're ripping to, but if you just rip the DVD to an .iso, and put the file in /var/lib/mythtv/videos (or whatever you've specified, if you've changed the defaults) on your backend, the frontend should be able to play this.

Just read your last post more thoroughly. It looks like you haven't shared the mythvideo & mythmusic directories on the backend.

The frontend will expect to see the video / music files on it's own local filesystem. It's confusing because they show up on the menu, but that's just loaded from the MySQL database. So your 'error 5' is most likely because the fontend is looking in /var/lib/mythtv/music on the frontend, when the files are actually in this location on the backend.

Look here [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=967635&highlight=nfs+videos) for guide to setting up nfs shares for these two folders

---

