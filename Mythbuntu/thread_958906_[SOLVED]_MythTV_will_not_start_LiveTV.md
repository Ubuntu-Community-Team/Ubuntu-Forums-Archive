---
title: "[SOLVED] MythTV will not start LiveTV"
date: 2008-10-25
forum: Mythbuntu
---

### Post by Buschbarber on 2008-10-25
I am running Ultimate 1.9 and I have MythTV installed and it has been working in the past couple of weeks. I launched the Frontend, today, and when I clicked on Watch TV, it just blinks and the Icon for Watch TV reappears.

I can get Movie Listings, the Program Guide, Weather, everything seems to be OK except Watch TV. I have not changed any hardware.

I do not know how to diagnose the problem.

---

### Post by Shadowfire on 2008-11-02
I have this same issue.  What I find temporarily fixes it, is to go in the back-end again and scan the channels again.  After this it runs the mythdatabase again and then I can go in to the frontend and use the WATCH TV again.

Only thing is once I turn mythtv off, I have to go back in to the back-end and scan the channels again and exit to the mythdatabase and all is once again fine.

I am not sure why the mythdatabase does not retain my information for the channels and why I have to rescan every time I restart Mythbuntu, but it happens.

If someone has a clue as to why this is, I would be exstatic to fix this with their input and help.

Thanks in advance..

---

### Post by Shadowfire on 2008-11-02
Okay.. I got a step futher... after looking at my Backend logs, I found 

-mythtv  	Problem with capture cards  	Card 1failed init

Then I found this post and it got me to thinking... 

[http://ubuntuforums.org/showthread.php?t=925242]("http://ubuntuforums.org/showthread.php?t=925242")

even though it is not my network card... it still is not initializing, which means it has something to do with loading order, or at least that was what I was seeing. So I changed the backend load order like they did in the post above and now...

It is recognicing the capture card and it doesn't fail... as well as I don't have to go back in to the backend to bring the capture card back up.

Now... I have the issue of the Watch Now coming up.. BUT! it stays on a black screen and it will not show the video.  I have to hard reset from there.

Any ideas?

---

### Post by Buschbarber on 2008-11-02
When I first set up MythTV, I had to download and install the firmware CX18 for my WinTV card. There is a website that has the instructions on how to do this. 

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

I just followed all the steps for downloading and installing and now everything works again.

It specifically states, for now, that everytime the kernel changes, I have to do this again. My problem is I don't know when the kernel has changed.

---

