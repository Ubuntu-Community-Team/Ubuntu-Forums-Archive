---
title: "Where is the VLC Log file?"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Spectre5 on 2009-11-19
When trying to stream a video with VLC (MMS), I am getting the following error message:

VLC is unable to open the MRL 'mms://URL_HERE'. Check the log for details.

I've scoured my computer and I have not found any VLC log anywhere.  I've searched google and the forums as well, but I'm not having any luck locating a VLC log file...does anyone know where it is??

Thanks,
Scott

PS:  I've streamed MMS streams with VLC before...in fact I just tried another and it worked, so my problem with this particular stream doesn't have to do with MMS...

EDIT:  And I should mention that I have tried going to VLC -> Tools -> Preferences -> Select "ALL" -> Advanced -> Logging and then entering a log file there since nothing was in the line.  But when I do this, the log file does not get created.  I tried touching a file so that it was already created, but still nothing get put into the file...

---

### Post by mc4man on 2009-11-19
The setting in preferences is to add a file for the log to be outputted to, ie. first create the file and then add thru preferences.

By default vlc won't output to a log, whether there is a way to globally enable don't know other than adding --file-logging to the  default launch command. ( or create a custom vlc launcher for such purposes

otherwise you'd need to specify from the command line vlc --file-logging <whatever>

Really no different in that case from what shows up in the terminal anyway
( the terminal output can be sent to a one time log by just adding after command,
  > vlc_output 2>&1 or whatever you wish the name ( goes to home folder, more useful when running vlc in debug mode

---

### Post by Spectre5 on 2009-11-19
> **mc4man said:**
> The setting in preferences is to add a file for the log to be outputted to, ie. first create the file and then add thru preferences.

By default vlc won't output to a log, whether there is a way to globally enable don't know other than adding --file-logging to the  default launch command. ( or create a custom vlc launcher for such purposes

otherwise you'd need to specify from the command line vlc --file-logging <whatever>

Really no different in that case from what shows up in the terminal anyway
( the terminal output can be sent to a one time log by just adding after command,
  > vlc_output 2>&1 or whatever you wish the name ( goes to home folder, more useful when running vlc in debug mode

Ah, thanks for the info.  Don't know why - but I didn't even think of running vlc from the terminal to see the output from it...

Now I have another interesting problem...I get this error message:
[0x7f88bc02f7f8] access_mms access error: failed to open a connection (tcp)
[0x7f88bc02f7f8] access_mms access error: failed to open a connection (tcp)
[0x7f88bc02f7f8] access_mms access error: cannot connect to server
[0x7f88bc02f7f8] access_mms access error: error: HTTP/1.0 404 Not Found

But....I know that the address is right...I've checked it 10 times and I know the file exists because I can watch it fine in the browser window...

---

### Post by mc4man on 2009-11-19
Well the error message is pretty straightfoward, vlc can't connect off of the add. you're using.

I pretty much just T & E streaming stuff, using a couple of players to compare and or find a 'better' address. ( usually vlc, mplayer,  and for audio sometimes also amarok.

If you wish to see if there is a solution I'd post a new thread and include a link. 
There are several people here who take great interest in such things, but "Where is the Vlc ....' isn't going to attract attention..

---

### Post by Spectre5 on 2009-11-19
> **mc4man said:**
> Well the error message is pretty straightfoward, vlc can't connect off of the add. you're using.

I pretty much just T & E streaming stuff, using a couple of players to compare and or find a 'better' address. ( usually vlc, mplayer,  and for audio sometimes also amarok.

If you wish to see if there is a solution I'd post a new thread and include a link. 
There are several people here who take great interest in such things, but "Where is the Vlc ....' isn't going to attract attention..

Good points - fortunately, I've "solved" this now.  I went back to the website and copied the MRL again.  For some reason, one letter changed in it from the time that I first copied it to the time that I actually played it in the browser!  It must have just been posted at the same time I was first accessing it or something.

---

