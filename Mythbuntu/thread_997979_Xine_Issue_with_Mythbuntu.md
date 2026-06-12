---
title: "Xine Issue with Mythbuntu"
date: 2008-11-30
forum: Mythbuntu
---

### Post by cbauch on 2008-11-30
I tried dvd playback using the internal mythdvd player on Mythbuntu 8.10, but it was jerky and there were a lot of artifacts in the video.

I switched to xine using the command: xine -pfhq --no-splash dvd:/

It plays dvds fine now.  The problem is when I try to quit.  It looks like most of the Xine threads end and it attempts to return the Mythtv, but then it sits there and all I see is the Mythtv background.  I can alt tab to other apps if there are any running and regain control of the computer, but I have to kill the mythtv front end process and xine to get it to stop waiting.

I have tried running xine from the terminal using the same command (or even just xine dvd:/).  It quits without a problem when I use the keyboard and press 'q'.  When I use the remote though (newer Windows MCE remote), it will almost quit but not return the command prompt.  The process is still running with a status indicating that it is waiting for one of its threads to return.  I checked the lirc config for xine and hitting the stop button on the remote sends the Quit event to xine, just like hitting the 'q' key does.

Has anyone run into something like this before or can figure out what the problem is?

---

### Post by jadam on 2008-11-30
I've had a very similar issue.  Since I upgraded to 8.10 xine has started not quitting properly after watching a film or video.  The only way that I seem to be able to get control back is to manually kill the xine processes.

I use Xine running XcMC, with the control code
xine -pfhq --no-splash 

I've also noticed that the smoothness of playback seems to be decreased on some source files since I upgraded.

If I figure out a fix I'll post it here

Joe

---

### Post by futelihut on 2008-12-04
I found a solution here, for the problem where xine do not return to mythtv
[http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)

For mee it worked :)
Regards Morten

---

### Post by vjunk on 2008-12-07
I have the same problem.  When I exit xine, the focus returns to MythTV but xine is still running in the background, preventing MythTV from displaying anything besides the background.  This is using Mythbuntu 8.10.  I tried setting my xine command line to the one used in the previous message's link (xterm -geometry 1x1-0-0 -e xine -pfhq -D --no-splash -s DVD), but it still does not work.  For now, I programmed a button on my remote to use irexec to execute a "killall xine", but this is definitely not the preferred method!

---

### Post by johnnysako on 2008-12-29
I also had some issues with DVD playback with the internal player.  Switching to Xine resolved all those issues, but I am not able to get Xine to work with Lirc.  Lirc works fine with MythTV and I have built a lircrc file for Xine which seems to be suitable.  Do I need to rebuild Xine to add support for Lirc?

Thanks,
John.

---

### Post by aynema on 2009-01-13
Has any one worked out a cause of this problem yet. I was looking at xine with the verbosity set high and from what I can gather. Xine exits cleanly if you hit 'q' on your keyboard every time but segfaults if you send the Quit command via lirc and every so often you don't get a seg fault xine just hangs which I'm assuming is what is causing mythvideo to keep waiting for xine to quit.

I'm currently using xine v0.99.6cvs.

---

