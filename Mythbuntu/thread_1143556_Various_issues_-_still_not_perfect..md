---
title: "Various issues - still not perfect."
date: 2009-04-30
forum: Mythbuntu
---

### Post by carrucha on 2009-04-30
OK, this mythbuntu thing is pretty cool.  I do have a few problems that I still haven't figured out.  I'm on 8.10.

1. My wireless network works, but I get this little popup asking to connect every once in a while.  I forget the message.  How do I make it go away?

2. I've got the PVR-150 with the Hauppage remote.  I can't figure out how to delete recordings.  Is there a special place to do that or is it a button on the remote?  Do all the remotes have the same functions, or is it possible to be missing something?  Should I dump the remote (I don't like it much) and get something else?  What are your recommendations? 

3. I've got schedules direct set up and it got it's data the first time it tried, but now it doesn't appear to be updating.  I've only got like 5 days' worth of data.  Do I need to tell it to update somewhere?  My internet should be connected all the time (but goes out sometimes with the dumb wireless connection).

4. How can I have the system name the files something readable so I can view them over the network easily (like on a Windows machine - I've got Samba working)?

5. How do I get it to transcode the videos?  I'd like to save them as xvid or something.  I see the option while recording, but it doesn't appear to be doing anything.  Is this while recording or processed when the system is idle?

6. How can I have the commercials excluded from my recording?

7. When there are long lists of things, how can I scroll faster than 1 by 1?  On my other DVR, one of the buttons went down a page at a time.

Thanks.

---

### Post by elgordo123 on 2009-04-30
Dude you should really read the manual/documentation, some of these are easily answered there. 

1, I am not sure on this one. 

2. I have the older hauppauge "grey" remote. Under Media Library, Watch Recordings you'll have a list of your recordings.  Highlight the one you want and press the menu button.  It should open a menu, and one of them is to "Delete Recording".    You can also go to Delete recordings in the menu. 

3.  It looks like your wireless connection keeps going down (from issue #1), so most likely when it is trying to update, it can't.   You should open a terminal and type mythfilldatabase and let it run and get caught up.  It will then reschedule itself to run, but again if your wireless is down when it runs it might get "stuck" and not reschedule itself until you run it manually.  You might want to setup a cron job to run it when you know the wireless will be working. 

4.I haven't tried this, but look at this thread: [http://ubuntuforums.org/showthread.php?t=1142127&highlight=mythpretty](http://ubuntuforums.org/showthread.php?t=1142127&highlight=mythpretty)

5. RTFM (Read the Mythtv Manual for this)

6. RTFM (Read the Mythtv Manual for this)

7. RTFM (Read the Mythtv Manual for this) - you can reprogram a remote's button for Page Down (or Page Up)

---

### Post by carrucha on 2009-05-01
Thanks for the reply.  

I've spent way more time to just get this to work than it should take. Maybe I'm just lucky, but this thing can be quite buggy.  I don't want to scour all over to find the remaining answers if people already know them.

1. This is a big issue.  If wireless goes in and out that's no problem.  But it keeps asking for the password that it has saved and works when I press enter.  What, do I gotta write a cron to press the enter button for me?

2. When I press the menu button on your same remote there is no such option.  Logically, that is where it should go, so that's where I've been looking.  The delete recordings area works though.  I didn't know that was there.

3. Ran mythfilldatabase and it didn't update the data.  Does this not run automatically already?  

4. I'll have to check this out.  Kinda a dumb hack.  Myth guys - build in good file naming. 

5. Like I mentioned, I tried this.  I would have assumed this would work right out of the box when selecting it.  I'll look in the manual and see what I'm missing.

6. Ditto.

7. Cool.  That should be a default too, it's necessary.  

8. NEW**  My remote has issues sometimes.  I've had to restart the service the other day and I have problems with it responding sometimes.  It's like the system's not responding, not that the remote isn't working.  Is this just life with Myth sometimes?  Do some of the other remotes work better?

Thanks

---

### Post by elgordo123 on 2009-05-01
1- I dont use wireless, so I can't be much help to you on that. 

2- In your /home/(user) directory type:
nano .lircrc  
Somewhere you should see this: 
begin
    prog = mythtv
    button = Menu
    config = M
end
 (M is the key to bring up the menu).   Does the menu come up when you are watching live tv and hit that same key?   Also try just hitting the M key on the keyboard and see if that works. 

Check this link to someone else's lircrc file (that uses the 150's silver remote).  [http://wiki.nerdylorrin.net/wiki/Wiki.jsp?page=MythTVLircrc](http://wiki.nerdylorrin.net/wiki/Wiki.jsp?page=MythTVLircrc)
I'd put it in both /home/(user)/.lircrc and also in /home/(user)/.mythtv/lircrc  (not quite sure which one it reads).  Restart the frontend after you do this so it will pick it up. 

3. Have you setup an account with schedules direct?  If so, is this information in the mythtv-setup?   If you run mythfilldatabase from a terminal look for any errors.   You will need to make sure your wireless is on and working at the time.  Run it as regular user (not sudo).   Also I'd do a ping [www.yahoo.com](www.yahoo.com) before you run it to make sure your wireless is getting out to the internet. 

5. In the setup there is a screen that asks if you want to run a job after every recording.  You can also tell it what to transcode to. I dont use it, so I am not sure.  I always press the menu button and select the Transcode option. The mythtv manual will tell you how.   Check the mythtv site (not mythbuntu) for a more comprehensive manual. 

6. This too is in the setup screens, to auto-flag commercials, this does take a few minutes though.  The mythtv manual will tell you how. 

8. I am not experiencing this with mine, so not for me.   Alot of people really love the Microsoft MCE remote: [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

---

### Post by jb5 on 2009-05-03
> **carrucha said:**
> 
1. This is a big issue.  If wireless goes in and out that's no problem.  But it keeps asking for the password that it has saved and works when I press enter.  What, do I gotta write a cron to press the enter button for me?

I switched to jaunty (at the beginning of April), so this _may not_ be the case in intrepid, I can't remember.

If you click on the wireless connection icon and select edit-connections.

Select your wireless connection and at the bottom of the panel there is a check box - make connection available to all users - check this box.
At the top of the panel there is a check-box to enable auto-connection - select this.

If there are any other connections listed in the wireless tab, that you don't use / need (I had lots of my neighbours wireless networks show up initially) delete these from your list.

At the end, you should have one wireless connection, that auto-connects and does not bug you for a password.

I saw this tip elsewhere but can't remember the reference, so credit to the person who pointed out this tip.

---

