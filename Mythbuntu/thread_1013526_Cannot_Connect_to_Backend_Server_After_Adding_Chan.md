---
title: "Cannot Connect to Backend Server After Adding Channels to Input Sources"
date: 2008-12-16
forum: Mythbuntu
---

### Post by CGW on 2008-12-16
After about a week of troubleshooting to find the problem...I at least found the cause.  So now I need help finding the solution.

I've re-installed Mythbuntu twice trying to find the problem.  Finally I figured out what's causing it.  I enter MythTV setup--->go to 4. Input Connections.  Each input is setup for my video source via the inputs on my card.  Everything works fine.  However, once I try and "fetch channels from listing source" I can't connect to the backend server for livetv, etc.

If you go to Input Connections the first time you'll notice the first there's a "Fetch channels from listing source" button (I'm getting my listings from Schedules Direct).  When I hit the button and scan for channels then I'm supposed to set my starting channel.  Let's pretend that's channel 4.  Problem is, once I "fetch" the channel listings and then exit I cannot connect to the backend server.  This happens whether I set the "starting channel" or not.

If I delete the video source and reset the input connections without "fetching" the listings then everything is fine.  

What am I doing wrong?

Thanks in advance.

---

### Post by uMuppet on 2008-12-17
When you say "Icannot connect to the backend server" I assume you mean that in the frontend when you try and watch TV or quit it it kicks the error "Cannot connect...".  
Have you checked your IP address settings are still correct for both frontend and backend?
Is your backend running?  
Can you go into Backend setup?

I hit a problem a while ago that my frontend was looking for "localhost" and my backend was at address 127.0.0.1 and they couldn't find each other, so make sure that they are staying exactly the same.  I have never used Schedules Direct but it sounds like it is altering your address when you do a channel fetch somehow.

---

### Post by CGW on 2008-12-17
> **uMuppet said:**
> When you say "Icannot connect to the backend server" I assume you mean that in the frontend when you try and watch TV or quit it it kicks the error "Cannot connect...".  

That's exactly what happens.


> **uMuppet said:**
> Have you checked your IP address settings are still correct for both frontend and backend?

Yes.  The IP addys are correct.  I checked them repeatedly before I figured out the whole channels thing was causing the problem.

> **uMuppet said:**
> Is your backend running?  
Can you go into Backend setup?

I assume it is.  I can enter the MythTV setup.  How can I determine if the backend is running properly?


> **uMuppet said:**
> I hit a problem a while ago that my frontend was looking for "localhost" and my backend was at address 127.0.0.1 and they couldn't find each other, so make sure that they are staying exactly the same.  I have never used Schedules Direct but it sounds like it is altering your address when you do a channel fetch somehow.

Again, I don't think it is.  I checked the FE/BE addresses many times before figuring out the fetching channels issue.  The IP addys stay the same regardless of whether I've added channels to my lineup or not.  

What I don't get is it worked fine for months and all of a sudden it starts doing this.

---

### Post by My Name on 2008-12-17
you may need to give the backend thing a pin number.
I think it defaults to a blank pin, but it requires one. you can use "0000" which means that it has no PIN if that makes sense...
Have a look under general in the backend settings. I'm at work so I don't know exactly where it is.

---

### Post by klc5555 on 2008-12-17
> **CGW said:**
> After about a week of troubleshooting to find the problem...I at least found the cause.  So now I need help finding the solution.

I've re-installed Mythbuntu twice trying to find the problem.  Finally I figured out what's causing it.  I enter MythTV setup--->go to 4. Input Connections.  Each input is setup for my video source via the inputs on my card.  Everything works fine.  However, once I try and "fetch channels from listing source" I can't connect to the backend server for livetv, etc.

If you go to Input Connections the first time you'll notice the first there's a "Fetch channels from listing source" button (I'm getting my listings from Schedules Direct).  When I hit the button and scan for channels then I'm supposed to set my starting channel.  Let's pretend that's channel 4.  Problem is, once I "fetch" the channel listings and then exit I cannot connect to the backend server.  This happens whether I set the "starting channel" or not.

If I delete the video source and reset the input connections without "fetching" the listings then everything is fine.  

What am I doing wrong?

Thanks in advance.

Why fetch the channels? Try scanning channels from the input connection, do the editing you need to do from the channel editor for each input, and exit the backend setup allowing mythfilldatabase to run. If you really need to set the starting channels after a scan (unlikely), then make a second special trip back into the backend setup to do this alone. And have mythfilldatabase run again. Sometimes the backend is a bit cranky restarting after being stopped for mythtv-setup activity --usually restarting the whole machine after running mythfilldatabase takes care of this. 

When you reinstalled twice, did you save and restore your earlier database, or are these completely clean installs including completely new mythconverg's? If you backed up and restored an earlier database that dates to a point when you had already started having your initial problem, then the restored database itself is likely to be the source of the continued problem --the hardware sections of mythconverg seem prone to corruptions of various sorts, particularly when connecting new slave backends, and I've found on a couple of occasions that some persistent tuning card problems that survived complete mythbuntu reinstallations suddenly disappeared when I restored mythconverg from a backup that dated _before_ the problems started. If your mythconverg is new with each installation, then obviously this is not the issue.

If you have real IP addresses (i.e. not 127.0.0.1 and localhost) set in your backend, and depending on what sort of name resolution you have going on on your local network, sometimes you need to edit up your /etc/hosts file properly to explicitly tell the machine which IP address translates to which machine, as Ubuntu doesn't always seem to do this right. I once had an installation that couldn't find localhost --I had to edit that one in also. In these cases the backend server can't be connected to until the hosts issue is resolved.

At any rate, some things to look at that don't involve a reinstallation. Good luck!

---

### Post by CGW on 2008-12-17
All re-installs were from scratch.  All IPs are on the local machine.

Also, I can't really scan for channels (I'm using a DirecTV box) but I'll give your other suggestions a try when I get home tonight.

Thanks

---

### Post by Damanther on 2008-12-17
A secondary hint first. In my experience, If you have successfully retrieved the lineup from schedules direct, that you probably should do either the "Scan for Channels" or "Download from Listings Source" but not both.

On to your real problem. I think you are having a problem connecting to the database in the backend, not the backend itself. I had some similiar problems with a hardy install and it kind of sounds like what you are experiencing.

You might check out this:
[MythTv Community Docs]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#Mythbackend%20setup%20not%20saving%20settings")

---

