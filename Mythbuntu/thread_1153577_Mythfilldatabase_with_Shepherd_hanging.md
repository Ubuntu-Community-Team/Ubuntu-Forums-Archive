---
title: "Mythfilldatabase with Shepherd hanging"
date: 2009-05-08
forum: Mythbuntu
---

### Post by lmclaren on 2009-05-08
Hi,

I am using Shepherd as my grabber, when I run mythfilldatabase it tries to read a Shepherd.xmltv config file that does not exist and hangs at that point.

I have tried to run --configure to recreate the file but no joy, does anyone have a Shepherd.xmltv file? if you do can you paste it please so I can try to work out which file Shepherd is looking for.

thanks

Lee

---

### Post by Bernmeister on 2009-05-12
I am getting this too...any luck?  I find that if I CTRL-C the script sort of continues...but I don't like the look of it.  

(I'm running Mythbuntu 9.04)

---

### Post by shooter80 on 2009-05-19
Hi - Did you mange to sort this issue out? I have just installed Mythbuntu with Shepherd and I am having exactly the same problem.

---

### Post by laffinet on 2009-05-19
What exactly is happening ? How do you guys know that shepherd isn't running properly ? What's the error ?

When I first installed shepherd I thought it didn't work because the first run failde (returned some error code). I left the whole thing alone, it started another run and everything was fine.

You could also try to reinstall and reconfigure shepherd. Just make sure you delete it first: just delete the shepherd directory in your home directory (might be hidden).

---

### Post by shooter80 on 2009-05-20
I am confident that shepherd is running correctly is fetching the data as I have checked the shepherd logs. 

Going by what mythfilldatabase is outputting below, it appears it doesn't know where to find the xmltv file that I sheperd creates??

 Connected to database 'mythconverg' at host: localhost
2009-05-20 18:50:33.590 XMLTVConfig entry in settings table missing, falling back to old behavior
2009-05-20 18:50:33.590 XMLTV config file is: /home/ronan/.mythtv/freeview.xmltv

Basically it hangs at this point until I hit control-c. It then continues on and exits.

^C2009-05-20 18:56:29.228 Error in 1:1: unexpected end of file
2009-05-20 18:56:29.229 Updating icons for sourceid: 1
2009-05-20 18:56:29.230 New DB connection, total: 4
2009-05-20 18:56:29.234 Connected to database 'mythconverg' at host: localhost
2009-05-20 18:56:29.235 No programs found in data.
2009-05-20 18:56:29.235 Failed to fetch some program info


I have tried reinstalling a number of times and it doesn't appear to work. Any clues?????

---

### Post by shooter80 on 2009-05-20
I have been having a play and I discovered some other information which may be usefull. I get the following error when I exit the Video sources configuration page on the myth backend -

"Your grabber does not provide channel numbers, so you have to set them manually"

How do I do this?

Cheers
Ronan

---

### Post by laffinet on 2009-05-20
You shouldn't have to do anything in the video sources configuration. What grabber is set up in there ?

Try reconfiguring the whole thing:

- in video sources, set the grabber to "none"
- go to channel set up, delete all channels
- do a full channel scan
- exit the mythbackend setup
- run "~/.shepherd/shepherd --configure" to re-configure shepherd

That should do it. Let's see how you go.

---

### Post by parsim on 2009-07-02
> **shooter80 said:**
> Connected to database 'mythconverg' at host: localhost
2009-05-20 18:50:33.590 XMLTVConfig entry in settings table missing, falling back to old behavior
2009-05-20 18:50:33.590 XMLTV config file is: /home/ronan/.mythtv/freeview.xmltv

Basically it hangs at this point until I hit control-c. It then continues on and exits.

Sorry to gravedig, but I'm pretty sure that is not a hang. Mythfilldatabase suppresses Shepherd's output, so you can't see it running, and Shepherd can take several hours (especially the first time). By hitting Control-C, you are aborting Shepherd. The warning about a missing "Shepherd.xmltv" config file is harmless and unrelated.

---

