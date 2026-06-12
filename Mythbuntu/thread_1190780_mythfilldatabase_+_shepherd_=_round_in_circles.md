---
title: "mythfilldatabase + shepherd = round in circles"
date: 2009-06-18
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-18
I cannot get working EPG data into MythTV.

After installing Shepherd I create a new video source in the backend. MythTV looks for installed XMLTV grabbers and a new config window comes up, the rest of the process runs in the MythTV Setup Terminal.

After answering a few questions, A pop-up window appears back in MythTV that says the first time I run mythfilldatabase I must run it like so:
> 
mythfilldatabase --manual

So I quit out of the MythTV back end setup, answer no to the question asking me if I want to run mythfilldatabase, open a terminal and run **mythfilldatabase --manual** instead.

When it finishes up everything seems OK. But after I go into MythTV and look at the listings there is nothing there. It says mythfilldatabase was run, but then it says no guide data is available and asks if I have run mythfilldatabase. Annoyingly it also says WARNING: Is mythfilldatabase still running?

I'm basically getting the same problem this guy was having here:

[http://ubuntuforums.org/showthread.php?t=800696&highlight=shepherd](http://ubuntuforums.org/showthread.php?t=800696&highlight=shepherd)

But with a different command being used to populate MythTV. I was going to try the command he used but I can't find the xml file. I have one under /.shepherd that is a .xmltv file and pretty big in size. Is that it?

Can anyone tell me what I am doing wrong per chance?

Help would be greatly appreciated as I truly am just blindly doing this - I seem to have answered the exact same questions about 4 times now. 

Cheers.

---

### Post by jbman on 2009-06-18
Set up your dvb cards on the bankend setup, choose au as the source for xmltv data, alt tab and ignore close down the tv_grab_au trying to load. Scan for the channels, hide/delete what you don't want/need. close down the bakend setup. run Shepherd configure and map your channels, tell Sheperd to link it to mythtv, set it to run the cron job and let it run.

if you have more issues make a post on the mailing list for quick answers

---

### Post by Mattaus on 2009-06-18
> Set up your dvb cards on the bankend setup, choose au as the source for xmltv data, alt tab and ignore close down the tv_grab_au trying to load. Scan for the channels, hide/delete what you don't want/need. close down the bakend setup. run Shepherd configure and map your channels, tell Sheperd to link it to mythtv, set it to run the cron job and let it run.

I could be wrong but I swear that's what I did...Shepherd asked me what channels I did and did not want,  it asked me if I wanted to auto configure MythTV, it did some cron job stuff, and I left it to run until MythTV told me it was done.

Still nothing. Just empty. So I tried the following:

1) I inspected the file output.xmltv that was sitting in my /.shepherd directory and it contained EPG data. LOTS of EPG data.

2) I checked what number my video source was with this:

> $ mysql -u root mythconverg
mysql> select * from cardinput\G


Which told me my source was "1"

3) I then ran this:

> mythfilldatabase --file 1 /.shepherd/output.xmltv

It thought for a bit and then said done. I went into MythTV and low and behold it said it was successful and that everything was up to date, no errors.

BUT I then went to recordings to check out the EPG and while it listed all my channels, the data for every time slot was **unknown(unknown)**

So it STILL hasn't fetched the data from that xmltv file.

When you say run shepherd configure do you mean **shepherd --configure**? Will this not ask me the same questions I was asked when I added the video source in MythTV (as it ran the configuration in the terminal then as well?

Sorry to be a nub, but when you say "post on the mailing list" what exactly are you talking about?

Thanks for the reply!

- Matt

---

### Post by jbman on 2009-06-18
run shepherd -- check

what do u get?

---

### Post by laffinet on 2009-06-18
I remember I had problems getting things to work with myth and shepherd too. In the end I pretty much started from scratch and followed the shepherd instruction to the dot and everything has been working fine since. From memory I think it took a few hours for the schedule data to appear in myth, so I would suggest you set everything up and leave it untouched until the next day to see if it works.
So, I'd suggest you do the following:

1. Uninstall shepherd by deleting the .shepherd folder in your home folder
2. In mythbackend setup, delete all you channels, rescan and hide/delete the channels you don't want
3. In mythbackend setup video sources, set the grabber to "none"
3. [Install ]("http://svn.whuffy.com/index.cgi/wiki/Installation")shepherd 
```
wget http://www.whuffy.com/shepherd/shepherd

```
```
perl shepherd

```
4. As part of the installation process, configure shepherd when prompted and let it:
- assign channels
- integrate with myth
- set up cron jobs
5. Finish and leave things alone !

Don't go straight into myth and check for schedule data. It might not be there yet and fiddling with things might break stuff.

---

### Post by Mattaus on 2009-06-18
OK, I cannot run **shepherd --check** atm as I am at work, but I will give it a shot tonight.

laffinet: The problem is that what you suggest there is pretty much what I did! I am installing a new GFX card tonight but after I get that working I will leave my machine on overnight and see if the EFG data appears in MythTV.

If nothing appears by say late Sat, I'll start the process from scratch as you suggest.

Fingers crossed something works :(

---

### Post by Mattaus on 2009-06-19
I seem to be having **another** problem:

> Region 75. 0 MythTV channels. 0 Shepherd channels.

   #  MythTV Channel                 Shepherd Guide Data
 --------------------------------------------------------

Create configuration file and update MythTV? [yes,no (default=yes)] yes
Successfully updated MythTV channels.

I did exactly what you said to do in your last post laffinet. To me what is going on above says that MythTV has no channels - but I have scanned them. All of them. In fact I could not figure out how to delete ones I didn't want!!!

What could I have missed?

UPDATE: I started from scratch **again** and did the channel scan from the video source menu instead of the channel editor menu and it seems to have worked. I can't go into MythTV yet to check however so hopefully I will know tomorrow morning.

---

### Post by Mattaus on 2009-06-19
omg it worked lol.

I left it running all night and this morning the EPG data was full. I need to get rid of some channels that have shown up but other than that it seems to be working perfectly!

Thanks for the help - much appreciated.

---

### Post by laffinet on 2009-06-19
Glad it worked !

---

