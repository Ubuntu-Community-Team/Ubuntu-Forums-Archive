---
title: "Only minor inconveninces today (server)..."
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MAFoElffen on 2011-04-18
After updates today-  Fairly stable, with a few crashes that all got reported- less one when apport crashed. (That's happened a few time this week, but well?)

RE: Natty Server 11.04beta2, with LAMP, SSH, Samba, CUPS... ubuntu-desktop, kubuntu-desktop & xubuntu-desktop.  Setup as a media server and a few other things on a somewhat low-end box.

Thought I could stress it today streaming both video and audio to 7 other boxes.  An eigth box was logged in ssh and remote desktop, hitting graphics webpages and doing queries on some MySQL files... and looking at system monitor. It really didn't even yawn or blink.  I was real happy with the results.

And things that didn't work a few days ago, such as being able to toggle between a graphics session and the tty console, now work.

The only real "odd" things I noticed that really stood out is something with "Remote Desktop!" and with configurations/updates across the network..   

Remote Desktop has always had a lag.  It seems to be "more" of a lag with 11.04.  I can have 1 (10,10) box connect VNC to both a 11.04 box and a 10.10 box... and the screen redraw of the controlled 11.04 slave on the Control Box is slower- although I see no difference in timings on either of the controlled boxes responses.  Does that explanation make sense?  Real biggey was cursor on, thumb-wheel scroll > above cursor redrew  in 7 seconds. > Below the cursor, redrew 125 seconds later. (But this  was also during that stress test...)

(From within 11.04)  
Another thing I keep noticing, is if you go to a graphical applet in ubuntu-desktop, it doesn't always "show" what I know is current in a status or configuration as it relates to a network info.... so I close that applet and start it again- and it "is" then there/right. Just really odd!  One of those I had to bounce the router to get resolved, all others were just reloading the app I was using.

Another instance is looking for network mapped drives and folders from within app's.  Sometime they don't see it when you are trying to set them up as a preference... even though you can see that they are mounted in a file manager or from terminal. Then I close and reopen that app and there it is.  These are not creating any crash or error- just intermittently not showing up in desktop app's...

I think 11.04 is close now.  I'm happy.

---

