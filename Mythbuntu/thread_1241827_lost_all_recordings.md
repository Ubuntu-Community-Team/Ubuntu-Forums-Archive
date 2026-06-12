---
title: "lost all recordings"
date: 2009-08-16
forum: Mythbuntu
---

### Post by jccubs on 2009-08-16
I'm a super newbie, so please keep this in mind with your replies.  I had a friend help me set up MythTV.  I have Jaunty Jackelope.  Things were working ok until a couple days ago.  Was watching a recorded show.  Left the room as the show ended.  When i returned the system said that there were no recordings to show.  I rebooted and it appears that when I try to run backend setup i get the following message: Failed to run /etc/init.d/mythtv-backend 'stop' as user root.  Unable to copy the user's Xauthorization file.  The only option is to close that window.  I do that. Then, i get the following: WARNING: MythTV has detected that the backend is running.  Changing existing card inputs, deleting anything, or scanning for channels may not work.  I can continue or exit.  If I continue I can then exit, and start the front end.  I do not have the program guide, but I am able to watch TV.  I cannot set things to record or watch previously recorded shows (it says there are none).  I will try to work through this, but if you are giving me directions please list EVERY step as I am very very inexperienced.  Any and all help is greatly appreciated!

---

### Post by klc5555 on 2009-08-17
> **jccubs said:**
> I'm a super newbie, so please keep this in mind with your replies.  I had a friend help me set up MythTV.  I have Jaunty Jackelope.  Things were working ok until a couple days ago.  Was watching a recorded show.  Left the room as the show ended.  When i returned the system said that there were no recordings to show.  I rebooted and it appears that when I try to run backend setup i get the following message: Failed to run /etc/init.d/mythtv-backend 'stop' as user root.  Unable to copy the user's Xauthorization file.  The only option is to close that window.  I do that. Then, i get the following: WARNING: MythTV has detected that the backend is running.  Changing existing card inputs, deleting anything, or scanning for channels may not work.  I can continue or exit.  If I continue I can then exit, and start the front end.  I do not have the program guide, but I am able to watch TV.  I cannot set things to record or watch previously recorded shows (it says there are none).  I will try to work through this, but if you are giving me directions please list EVERY step as I am very very inexperienced.  Any and all help is greatly appreciated!

First step is to determine accurately what you have left in your installation. Your recordings are probably all perfectly safe; it is more likely that the database's ability to access them has been temporarily interrupted, or that the database itself has been corrupted. As frequently happens after a dirty restart after a power glitch, or having hit the reset button.

The first step is to do not just a restart, but rather do a complete clean shutdown, let the machine sit for a minute or so, and then do a cold start. After a booting from a cold start, the machine may be able to find its recordings again, or your symptoms may be unchanged.

If unchanged, a second attempt would be to go into the mythbuntu control center (Setup>Mythbuntu>Advanced Management) and at this Advanced Management screen, click to have mythbuntu run the MySQL repair/optimize utility. When the utility has completed, exit the mythbuntu control center and see, when the backend has restarted, whether the database seems to be alive again.

If not, we can proceed from there.

---

### Post by jccubs on 2009-08-18
OK, did what I believe to be a clean shutdown. Power off to the computer for 5 minutes. Rebooted. The problem persists. Went into the Advanced management and clicked the repair / optomize, but that check box was for daily repair. I also clicked the button above the checkbox menu Optomize Tables. This took onlyabout 1/2 second. Applied changes, quit, tried to run the frontend, but could not watch tv. This happens frequently. Before exiting I checked and the recordings are there. THANK YOU SO MUCH! What I do when it does not allow watch tv is to exit, right click on the screen, click applications, click system, click backend setup. In backend setup i just escape, then it asks me if I want to run mythfilldatabase. I click OK and let it run. When that is complete then I right click the screen again, click applications, click multimedia, then click frontend. From that point I can watch tv or watch my recordings. Often when running mythfilldatabase it does freeze and i have to restart the computer though. Thanks again for your help.

---

### Post by jccubs on 2009-08-18
Thought I was Home free, but mythfill database keeps freezing and I am back where I started.  I can repeat the steps from before, but then cnnot watch tv, only recordings.

---

### Post by jccubs on 2009-08-18
bump

---

### Post by tgm4883 on 2009-08-18
How much free space do you have on your drive?

Lets see some logs too
/var/log/mythtv/

---

### Post by jccubs on 2009-08-19
yes - I believe that is it.  I restarted the computer and the update manager screen came up and I was not able to update because the drive was full.  I have a terabyte drive adn the last time I checked I had 58% free.  Like I said earlier - I'm a supernewbie - in Ubuntu I don't even know how to clear drive space.  Please help!

---

### Post by laffinet on 2009-08-19
The information you're giving is slightly convoluted, can you try to give a some more structured description of your problems, please.

A few questions to start:

1. What's the state of your system, what works, what doesn't work ?
2. Is this a dedicated media PC or do you do other things with it ?
3. You mentioned that mythfilldatabase freezes. How do yo know ? What happens when it freezes ?
4. Is your system set up to get channel/TV program information ? If so, how, what are your settings ?
5. How much space do you have on your drive at the moment ? Please run 
```
df -Th | sort 
```
in a terminal and post the output here.

---

### Post by jccubs on 2009-08-20
right now i cannot watch tv or watch previously recorded shows.
this is a dedicated front and backend machine - I do not use it for anything else, however I have saved some pictures and home videos on it as well.
When I run mythfill database it runs for 10 - 20 seconds and then freezes. I have left it running for 30 minutes, but it remains in the same spot.
Yes, my system is set to automatically grab the listings through schedules direct.
 
I ran df -th and the results are:
 
Filesystem Type Size Used Avail Use% Mounted on
/dev/sdal ext3 12G 12G 0 100% /
tmpfs tmpfs 501M 0 501M 0% /lib/init/rw
varrun tmpfs 501M 352K 501M 1% /var/run
varlock tmpfs 501M 0 501M 0% /var/lock
udev tmpfs 501M 144K 501M 1% /dev
tmpfs tmpfs 501M 0 501M 0% /dev/shm
lrm tmpfs 501M 2.2M 499M 1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda6 xfs 920G 425G 495G 47% /var/lib
overflow tmpfs 1.0M 1.0M 0 100% /tmp

---

### Post by laffinet on 2009-08-20
> **jccubs said:**
> 
When I run mythfill database it runs for 10 - 20 seconds and then freezes. I have left it running for 30 minutes, but it remains in the same spot.


I don't have experience with schedules direcet, but my listings grabber (which gets called up during mythfilldatabase) can take some time to run (1hour+), especially on the first run or if it hasn't run successfully in some time. You won't see any progress in the mythfilldatabase window during that. I suspect you cancelled mythfilldatabase prematurely. I'd suggest next time you run mythfilldatabase you let it run for longer to make sure it finishes properly.
Also, in the frontend, check under "Information" (or something like that), "Machine status", "Listings". Should have an entry about mythfilldatabase and when it last run and what the result was.

> **jccubs said:**
> 
Filesystem Type Size Used Avail Use% Mounted on
/dev/sdal ext3 12G 12G 0 100% /


There's your problem, your root partition is 100% full. You need to clean up and creat some space.
Any idea what's using all that space ? Where are your videos and pictures stored ? Do you have existing recordings ? Where are they stored ?
In mythbackend setup, go into "storage directories", there should be a "default" entry (any others ?), check that, what's the content ?

Also, check your trash. Start by right clicking on the desktop icon and select empty trash. Run
```
df -Th | sort
```
and see if you've got some space back.

What's the content of /var/lib ?

---

### Post by klc5555 on 2009-08-20
That does seem to be a bit of a flaw with the Mythbuntu 8.04 and later default partitioning scheme: if the unaware user does any of the usual things that one automatically expects to do under /home/<username> on a PC (like saving large files apart from recordings, or working with DVD archiving tools, etc.) that itty-bitty root partition gets maxed out pretty quickly.

I wonder how or whether this default partitioning scheme could be modified in future versions of Mythbuntu without losing the "ease of installation" feature of the installation. Maybe a separate (somewhat bigger) partition for /home ? Even if such a /home partition inadvertently got maxed out, it wouldn't interfere with the OS or PVR functions of the machine.

---

### Post by tgm4883 on 2009-08-20
> **klc5555 said:**
> That does seem to be a bit of a flaw with the Mythbuntu 8.04 and later default partitioning scheme: if the unaware user does any of the usual things that one automatically expects to do under /home/<username> on a PC (like saving large files apart from recordings, or working with DVD archiving tools, etc.) that itty-bitty root partition gets maxed out pretty quickly.

I wonder how or whether this default partitioning scheme could be modified in future versions of Mythbuntu without losing the "ease of installation" feature of the installation. Maybe a separate (somewhat bigger) partition for /home ? Even if such a /home partition inadvertently got maxed out, it wouldn't interfere with the OS or PVR functions of the machine.

Modifying the partitioning scheme is pretty easy, it's just a [partman recipe]("http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/devel/partman-auto-recipe.txt"). The one caveat is that we can only have a single recipe (limitation of ubiquity). This means only a single partitioning scheme, so we can't do cool things like multiple drive configuration, only the first drive. If someone wants to post the recipe that they think we should use I will look at it. I don't promise to implement it, but I'll at least look.


To the OP, what is the output of 
```
ls -l /var/log/mythtv/
```


:EDIT:

So we don't hijack the thread, To discuss the Partitioning Recipe, please discuss in [this thread]("http://ubuntuforums.org/showthread.php?t=1245527")

---

### Post by jccubs on 2009-08-20
how do I empty trash. I do not have icons on my desktop. I only have the mythbuntu logo at the bottom. I don't have a menu bar across the top either. I can right click and get a menu, but didn't see anywhere to empty trash. Also in backend setup for storage locations there is only the Default, I have 3 options to create groups, but have not made any. How do I fix this, and then how do I avoid it in the future? Again, thank you for any and all help.

---

### Post by jccubs on 2009-08-20
Looked at the partman recipe also, and wasn't exactly confident enough to start messing with things, so I left them as they are.

---

### Post by laffinet on 2009-08-20
Okay, first let's try and get that panel back.

Open a terminal and run 

```
xfce4-panel
```

You should now have a panel. Log out but make sure you got "save current session" checked in the confirmation window.
Log back in, hopefully you still have a panel.

You can access trash via the file manager: just open the menu, accessories, thunar file manage. Find trash, right click, select empty trash (or something similar).

To get a trash icon on your desktop, in the menu, select settings, Desktop, icons, check "trash".

How much space have you got now ?

What's the content of /var/lib/mythtv ?

---

### Post by jccubs on 2009-08-20
OK, I followed the steps to get a panel, but the panel disappeared when I closed the terminal.  So I left the terminal open and tried to log out, but the exit screen disappeared and I was back to the screen with the terminal still open.  When I closed the terminal, the panel disappeared also.  I was able to find the trash, but it was empty, my situation is basically unchanged.  When I used to haave the panel, the Panel was labeled Applications.  Now when the machine boots up (before the front end starts) the panel is labeled xfce, not sure if that tells you anything.

---

### Post by laffinet on 2009-08-20
Ooops, forgot about that. Try hitting ALT+F2, then enter xfce4-panel plus the other steps. 
Panel name seems ok, mine is called xfce-menu.

---

### Post by jccubs on 2009-08-20
I did that and I got :
bash: syntax error near unexpected token `;'

---

### Post by laffinet on 2009-08-20
> **jccubs said:**
>  Now when the machine boots up (before the front end starts) the panel is labeled xfce, not sure if that tells you anything.

Hang on, does that mean you now have a panel after you reboot ?

After booting, if you close the frontend (esc until you get to the bit where it asks if you want to close, choose yes), do you have a panel then ?

---

### Post by jccubs on 2009-08-20
no, I do not have a panel then, only as I watch it boot to the front end.

---

### Post by laffinet on 2009-08-20
> **jccubs said:**
> no, I do not have a panel then, only as I watch it boot to the front end.

What do you see when you close the frontened ?

---

### Post by jccubs on 2009-08-20
only the mythbuntu logo (very large) at the bottom of the screen (the one with the TV).

---

### Post by laffinet on 2009-08-20
Okay,while displaying the desktop, hit ALT+f2, what do you get?

---

### Post by jccubs on 2009-08-20
nothing happens.

---

### Post by laffinet on 2009-08-20
open a terminal, type ```
xfrun4
```, this will open the "run command" dialog.

Now type xfce4-panel, this should open the panel.

Close the terminal (panel should stay open), log out etc. as described in my earlier post. Log back in, close frontend, do you have a panel ?

---

### Post by jccubs on 2009-08-20
ok - panel stayed this time.  When I tried to log out I got the following message:
 
Failed to receive a reply from the session manager
Session manager must be in idle stae when requesting a shutdown

---

### Post by laffinet on 2009-08-20
Don't know about that one. Can you try logging out again ?

---

### Post by jccubs on 2009-08-20
same thing.  Should I shut off the computer?

---

### Post by laffinet on 2009-08-20
to reboot, open a terminal, type 
```
sudo reboot 
```

enter your password. This should reboot your computer.

Then try again.

---

### Post by jccubs on 2009-08-20
ok - rebooting - that worked.

---

### Post by jccubs on 2009-08-20
still no panel though.

---

### Post by laffinet on 2009-08-20
Now repeat the steps from above, hopefully you'll be able to log out now.

---

### Post by jccubs on 2009-08-20
ok - logged out!

---

### Post by laffinet on 2009-08-20
logged back in ? Panel back ?

---

### Post by jccubs on 2009-08-20
OK - sorry I'm being such a pain, just so unfarmiliar with this.  Learning though.  How exactly do I log in after logging out?

---

### Post by laffinet on 2009-08-20
You should have a window that prompts you for your username. Type it in, hit enter, type your password, hit enter, you should be logged in. Close the frontend and hopefully you have a panel.

---

### Post by jccubs on 2009-08-20
I did not get a window that asked me for username only exited to Xfce Menu screen.

---

### Post by laffinet on 2009-08-20
I'm lost. What do you see on your screen right now ?

---

### Post by jccubs on 2009-08-20
I have the Xfce Menu at the top of the screen.  and the mythbuntu logo (same one) at the bottom center of the screen.

---

### Post by laffinet on 2009-08-20
BTW Seems like your posting this from a different computer. Do you have an irc account ?

---

### Post by jccubs on 2009-08-20
Ummmm, I have no idea.  i'm posting this from my laptop.  I can open a browser window on the computer with mythtv if that would help.

---

### Post by laffinet on 2009-08-20
> **jccubs said:**
> I have the Xfce Menu at the top of the screen.  and the mythbuntu logo (same one) at the bottom center of the screen.

You haven't logged out yet. But it seems you have a panel.

Open the menu, select "log out", check the "save session for future logins" box, click "log out". Log back in.

---

### Post by jccubs on 2009-08-21
Clicked log out, got the log out screen.  Made sure the save settings ox was checked.  clicked log out.  screen went black for a split second, now back to Xfce Menu.  Tried to log out again and got the same message as before:
Session manager must be in idle state when requesting a shutdown.  I'm going to do the reboot procedure you described earlier.  This has left me with no panel on my prior attempts though.  I do not know, but does my partition problem factor into this?

---

### Post by laffinet on 2009-08-21
This is weird. I'm wondering if you're running two sessions somehow, not sure if and how that's possible.

I'm also starting to think that your system seems fairly screwed up. A clean re-install might be the best (easiest) option. 

Do you have the possibility to back up everything you'd like to keep (videos, pictures, anything else you copied to the myth computer)?

---

### Post by jccubs on 2009-08-21
OK - rebooted.  Followed the steps you described earlier to get the panel.  The panel appeared, but in the terminal it said the following:
Unable to write to history file.

---

### Post by jccubs on 2009-08-21
i have copies of the pictures and home videos that are on here, but the recorded shows would be removed and I'd prefer not to lose those. Not even sure how to transfer those to another location. The computer is networked to my main computer (that's how i copied the pictures and home videos there).  The computer in new, never used it for anything before mythtv.  Using HD homerun and a good video card, if any of that makes any difference.

---

### Post by laffinet on 2009-08-21
The recordings can be saved as well, bit more work but possible.

There just seem to be a lot of problems with your machine which makes me think the installation is somehow not ok and a reinstall might be easiest.

Before you do that, though, with the panel now open, can you log out etc.?

---

### Post by jccubs on 2009-08-21
no - it does the same thing.  I'm left with the Xfce Menu at the top of the screen.  I can run the frontend and watch TV, but the guide does not work, and previously recorded shows are not available.  I wanted to save one set of shows for my wife, but if it is a bunch of work, we'll forget it.

---

### Post by laffinet on 2009-08-21
It's not that hard.

Steps involved are:

1. copy the recorded files to a backup location
2. back up the database
3. reinstall mythbuntu
4. restore the recording files 
5. restore the database

If you want to go ahead we can go through the details

---

### Post by jccubs on 2009-08-21
if you're up for it, I am too.

---

### Post by jccubs on 2009-08-21
You know what, I can't thank you enough for your help, but it's almost midnight and I have to be at work in about 6 hours.  I'll be back on here tomorrow.  Thank you again!

---

### Post by laffinet on 2009-08-21
We can give it a shot. Just beware that there is a risk that your recordings will get lost. But I'll try my best to keep them ;-)

To start with, open mythbackend setup, go to storage directories, default, what's listed there ? This is where your recorded shows are.

---

### Post by laffinet on 2009-08-22
> **jccubs said:**
> You know what, I can't thank you enough for your help, but it's almost midnight and I have to be at work in about 6 hours.  I'll be back on here tomorrow.  Thank you again!

It all depends on how confident you feel installing mythbuntu. I suggest you read up on that before starting and see if you think you're up to it. Shouldn't be too hard, but depending on what hardware you use things can get a bit tricky.

Start by reading this [manual]("http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf"). 

There's an excellent guide on how to backup and restore your database [here]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")

---

### Post by jccubs on 2009-08-22
going to try this tonight - thanks again!!

---

### Post by jccubs on 2009-08-24
Totally wiping out my hard drive tonight.  Starting from scratch.  Was wondering why the only download I could find was 9.04 and the only instruction manual was for 8.10.  Is there a download for 8.10 or instructions for 9.04?  I just do not want to make any of the same mistakes I made in my previous installation.  Any suggestions for partitioning my drivewhen I am asked?

---

### Post by laffinet on 2009-08-24
Are you planning to back up your database to keep your recordings?

There's no manual for 9.04, but the differences are neglible so the 8.10 will do fine.

I'd go with the partitioning scheme suggested by the installer.
This should create one root partition (ext3, relatively small 10-20gig) and one xfs partition (as big as possible), mounted as /var/lib/mythtv.

The important thing is that your recordings and videos directories are setup properly, so you don't fill up your root partition. This should be done automatically by the installer but it might pay to check.

Recordings: go to mythbackend setup, storage directories, defaults. The recordings directory should be /var/lib/mythtv/recordings.

Videos: this is done in mythfrontend. I think it's under setup, media settings, but not sure. Once there, the directory should be /var/lib/mythtv/videos.

Whenever copying large quantities of data onto your machine (music, pictures, videos) you have to make sure they go into a folder under /var/lib/, otherwise you'll end up filling up your root partition again and running into problems

What kind of hardware are you using ? TV card, graphics card, remote ?

---

### Post by jccubs on 2009-08-24
the remote is a Windows XP media center remote, that i copied to a logitech harmony remote.  I'm using a HD homerun and the graphics card is  GeFORCE 8500 GT.  The recordings and everything is getting wiped now - not keeping anything.  Going to use the installation manual to install and go over it line by line.  I'm not going to copy any pictures or videos for a while to be sure that everything is working fine.  I did have one issue also.  I have iTunes and tried to copy my music to the music area in mythtv, but it did not recognize any of it.  Do the files need to be mp3?  Thanks again for helping me.  I really appreciate it.

---

### Post by laffinet on 2009-08-24
> **jccubs said:**
> I have iTunes and tried to copy my music to the music area in mythtv, but it did not recognize any of it.  

Did you scan for new music ? 

First of all you music needs to be stored in the directory specified here: Utilities/Setup->Setup->Media Settings->Music Settings->General Settings

Then go to Utilties/Setup->Music Tools and select "scan for new music". This will scan the directory specified above for music and add it to the database. You should be able to play it after that.

---

### Post by jccubs on 2009-08-25
no - i did not scan!!  another thing i did not know.  thanks again!!!!!!!

---

### Post by jccubs on 2009-08-26
ok - I'm back and running.  I have the panel and most things seem fine.  Couple issues.  the guide does not show any shows.  It only says Unknown.  I did run mythfilldatabase with no problems.  I waited 8 hours and rechecked, but it still has no listings for the shows.  I have a schedulesdirect account that is current, so that is not the problem.  perhaps i missed a checkbox on the setup, but I did really take my time setting it up.  Also last night i left the tv on a channel when i turned it off.  when i woke up this morning i noticed that it recorded everything through the night (they were all labeled Unknown though).  I deleted those, but want to be sure that this isn't happening because i don't want to go away for the weekend and have to delete 100 shows!  How do I stop this from contnuing?  This time when I shut down, i went to the main menu before turning the tv off.  I'm at work for the next 7 hours so I can't check anything for at least that long.

---

### Post by laffinet on 2009-08-26
Good work.

TV schedules: 
Have you set up your schedule grabber in mythtv backend ? I don't have experience with schedules direct, so probably can't help an awful lot with this one. There's a (rather brief) guide [here]("http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Video_sources")

In mythfrontend, go to Information Centre, System status, Listings status. What does the bit about mythfilldatabase say ?

TV you recorded: 
First of all, it's a good idea to exit liveTV when leaving the machine running without watching TV. Long term you might want to look into shutting the machine down automatically when idle (saves power, too) but let's get things running first.
By design mythtv records every time you watch TV. These "recordings" expire quickly, so don't worry about filling up your hard drive that way. 
Go to Utilities/Setup, TV settings, Playback, screen5/9, untick "Show LiveTV recordings when using all programs filter". That way the liveTV recordings don't get listed when browsing your recordings.

---

### Post by jccubs on 2009-08-29
ok - been a while since I tried to tackle this.  Here's what i noticed.  On the screen you mention above (screen 5/9) i had that unticked, but it appears to record everything if I accidentially leave the tv on a station when turning the tv off.  I have a terabyte drive and it is already 12% full with none of the shows that I want recorded.  I still can't get anything to show up in my guide.  I've gone over the installation steps again and checked and double checked what I did on installation, but everything seems fine there.  Mythfill runs great and watcing tv is fine, except that everything is coming up Unknown!  In the listing status it does say Myth version: 0.21.20080304-1 19961
Last mythfilldatabase guide update:
started:  2009-08-29 18:38
finished: 2009-08-29 18:39
Result:
Suggested Next:2009-08-30 21:30:48
 
There's no guide data available!
Have you run mythfilldatabase?
WARNING: is mythfilldatabase running?
DataDirect Status:
your subscription expires on 07/30/2010.....

---

### Post by jccubs on 2009-08-29
Also since we cannot set things to recore, we tried to manually record my wife's soap, but it didn't record anything. We set it to record every day in the correct time slot on the correct channel.  Then we figured since it was recording the station we left it on, we just turned it to that station a few minutes before her show.  It taped the minutes before her show, then actually skipped her show, and taped everything afterwards.  It was like it didn't tape when we had it programmed!!!

---

### Post by laffinet on 2009-08-29
Okay, let's try to fix your guide data first. Remember I'm not familiar with schedules direct but I'll try...

In mythbackend setup, go to channel editor, pick any channel, hit enter. This will show you a whole heap of information for that channel.
What does it show for xmltv channelid ?
Check a few other channels and see what it says.

One thing I just noticed is that mythfilldatabase only ran for a minute or so, which seems awfully short. I'm sure the listings grabber didn't actually run, question is why ?

Did you check your settings in "video sources" and "input connections". Post them here.

Sorry, got to run, back in a few hours.

---

### Post by tgm4883 on 2009-08-29
> **jccubs said:**
> Also since we cannot set things to recore, we tried to manually record my wife's soap, but it didn't record anything. We set it to record every day in the correct time slot on the correct channel.  Then we figured since it was recording the station we left it on, we just turned it to that station a few minutes before her show.  It taped the minutes before her show, then actually skipped her show, and taped everything afterwards.  It was like it didn't tape when we had it programmed!!!

Lets see some backend logs
```
/var/log/mythtv/mythbackend.log
```

---

### Post by jccubs on 2009-08-30
XMLTV channel ID id empty on all channels!

---

### Post by jccubs on 2009-08-30
Video Sources
(New video source)
(Delete all video sources)
Schedules Direct

---

### Post by jccubs on 2009-08-30
Input connections
[HDHomeRun : ID FFFFFFFF Port 0](MPEG2TS->Schedules Direct
[HDHomeRun : ID FFFFFFFF Port 1](MPEG2TS->Schedules Direct

---

### Post by jccubs on 2009-08-30
Tried to do the log, and I must have done it incorrectly.  I opened a terminal and the prompt was:
[EMAIL="jc@jc-myth:~/Desktop$"]jc@jc-myth:~/Desktop$[/EMAIL]
 
When I typed in the /var/log/mythtv/mythbackend.log - - I received the following message:
Permission denied

---

### Post by tgm4883 on 2009-08-30
Well the problem with the Unknown channels is that you don't have any XMLIDs for your channels. You can input these manually, you can get the XMLID by hovering over the channel on the Schedules Direct website.


And for the backend logs, you will need to use sudo

---

### Post by jccubs on 2009-08-30
I entered the id's and that seems to have my guide problem fixed.  I opeed a terminal and typed in sudo/var/log/mythtv/mythbackend.log and the reply was No such file or directory.

---

### Post by tgm4883 on 2009-08-30
> **jccubs said:**
> I entered the id's and that seems to have my guide problem fixed.  I opeed a terminal and typed in sudo/var/log/mythtv/mythbackend.log and the reply was No such file or directory.

run mythbuntu-log-grabber

You can run that from a terminal, or from the app menu. I think you can even run it from the frontend, but you still need a mouse available

---

### Post by jccubs on 2009-08-30
==> /var/log/mythtv/mtd.log <==
mtd started at Wed Aug 26 22:10:58 2009
mtd is running on a host called jc-myth
22:10:58: Waiting for connections/jobs
22:10:58: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-08-30 12:57:52.587 AFD: codec AC3 has 6 channels
2009-08-30 12:57:52.589 AFD: Opened codec 0x9bd2860, id(AC3) type(Audio)
2009-08-30 12:57:52.592 AFD: codec AC3 has 2 channels
2009-08-30 12:57:52.597 AFD: Opened codec 0x9bd2e50, id(AC3) type(Audio)
2009-08-30 12:57:52.642 Using runtime prefix = /usr
2009-08-30 12:57:52.653 Empty LocalHostName.
2009-08-30 12:57:52.655 Using localhost value of jc-myth
2009-08-30 12:57:52.689 New DB connection, total: 1
2009-08-30 12:57:52.721 Connected to database 'mythconverg' at host: localhost
2009-08-30 12:57:52.728 Closing DB connection named 'DBManager0'
2009-08-30 12:57:52.731 Connected to database 'mythconverg' at host: localhost
2009-08-30 12:57:52.735 New DB connection, total: 2
2009-08-30 12:57:52.737 Connected to database 'mythconverg' at host: localhost
2009-08-30 12:57:52.743 Current Schema Version: 1214
2009-08-30 12:57:52.769 Preview Error: Previewer file '/var/lib/mythtv/recordings/1051_20090830125748.mpg' is not valid.
2009-08-30 12:57:52.772 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1051_20090830125748.mpg'
2009-08-30 12:57:52.860 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1051_20090830125748.mpg.png) exists: 0 readable: 0 size: 0
2009-08-30 12:57:55.649 Preview: Grabbed preview '/var/lib/mythtv/recordings/1091_20090830125708.mpg' 1920x1088@64s
2009-08-30 12:58:32.526 Expiring 0 MBytes for 1071 @ Sun Aug 30 12:56:02 2009 => Unknown
2009-08-30 12:58:32.531 Expiring 0 MBytes for 1053 @ Sun Aug 30 12:56:28 2009 => Unknown
2009-08-30 12:58:32.538 Expiring 10 MBytes for 1053 @ Sun Aug 30 12:56:30 2009 => Unknown
2009-08-30 12:58:32.541 Expiring 0 MBytes for 1071 @ Sun Aug 30 12:56:55 2009 => Unknown
2009-08-30 12:58:32.543 Expiring 0 MBytes for 1091 @ Sun Aug 30 12:57:06 2009 => Unknown
2009-08-30 13:00:01.424 Finished recording Unknown: channel 1051
2009-08-30 13:00:01.552 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-08-30 13:00:01.677 TVRec(1): RingBufferChanged()
2009-08-30 13:00:01.684 Finished recording Unknown: channel 1051
2009-08-30 13:00:02.463 Using runtime prefix = /usr
2009-08-30 13:00:02.469 Empty LocalHostName.
2009-08-30 13:00:02.471 Using localhost value of jc-myth
2009-08-30 13:00:02.488 New DB connection, total: 1
2009-08-30 13:00:02.514 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:00:02.517 Closing DB connection named 'DBManager0'
2009-08-30 13:00:02.519 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:00:02.527 New DB connection, total: 2
2009-08-30 13:00:02.531 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:00:02.580 Current Schema Version: 1214
2009-08-30 13:00:05.096 AFD: Opened codec 0x838e260, id(MPEG2VIDEO) type(Video)
2009-08-30 13:00:05.099 AFD: codec AC3 has 6 channels
2009-08-30 13:00:05.101 AFD: Opened codec 0x838e850, id(AC3) type(Audio)
2009-08-30 13:00:09.929 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090830125751.mpg' 1920x1088@64s
2009-08-30 13:00:32.556 Expiring 65 MBytes for 1091 @ Sun Aug 30 12:57:08 2009 => Unknown
2009-08-30 13:00:32.559 Expiring 0 MBytes for 1051 @ Sun Aug 30 12:57:48 2009 => Unknown
2009-08-30 13:10:23.453 TVRec(1): HW Tuner: 1->1
2009-08-30 13:10:24.522 Finished recording Unknown: channel 1051
2009-08-30 13:10:24.668 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-08-30 13:10:25.908 Using runtime prefix = /usr
2009-08-30 13:10:25.912 Empty LocalHostName.
2009-08-30 13:10:25.913 Using localhost value of jc-myth
2009-08-30 13:10:25.990 New DB connection, total: 1
2009-08-30 13:10:26.004 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:26.006 Closing DB connection named 'DBManager0'
2009-08-30 13:10:26.010 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:26.013 New DB connection, total: 2
2009-08-30 13:10:26.016 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:26.059 Current Schema Version: 1214
2009-08-30 13:10:28.879 AFD: Opened codec 0x83ce3c0, id(MPEG2VIDEO) type(Video)
2009-08-30 13:10:28.880 AFD: codec AC3 has 6 channels
2009-08-30 13:10:28.883 AFD: Opened codec 0x83ce8b0, id(AC3) type(Audio)
2009-08-30 13:10:30.952 Preview: Grabbed preview '/var/lib/mythtv/recordings/1051_20090830130000.mpg' 1920x1088@64s
2009-08-30 13:10:32.592 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-08-30 13:10:36.847 TVRec(1): HW Tuner: 1->1
2009-08-30 13:10:38.732 Finished recording Unknown: channel 1071
2009-08-30 13:10:38.777 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-08-30 13:10:39.278 Using runtime prefix = /usr
2009-08-30 13:10:39.288 Empty LocalHostName.
2009-08-30 13:10:39.289 Using localhost value of jc-myth
2009-08-30 13:10:39.304 New DB connection, total: 1
2009-08-30 13:10:39.332 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:39.336 Closing DB connection named 'DBManager0'
2009-08-30 13:10:39.340 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:39.345 New DB connection, total: 2
2009-08-30 13:10:39.348 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:39.353 Current Schema Version: 1214
2009-08-30 13:10:39.389 Preview Error: Previewer file '/var/lib/mythtv/recordings/1071_20090830131023.mpg' is not valid.
2009-08-30 13:10:39.392 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1071_20090830131023.mpg'
2009-08-30 13:10:39.408 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1071_20090830131023.mpg.png) exists: 0 readable: 0 size: 0
2009-08-30 13:10:39.945 Finished recording Unknown: channel 1091
2009-08-30 13:10:41.019 Finished recording Unknown: channel 1091
2009-08-30 13:10:41.105 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-08-30 13:10:41.462 Using runtime prefix = /usr
2009-08-30 13:10:41.468 Empty LocalHostName.
2009-08-30 13:10:41.470 Using localhost value of jc-myth
2009-08-30 13:10:41.487 New DB connection, total: 1
2009-08-30 13:10:41.509 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:41.512 Closing DB connection named 'DBManager0'
2009-08-30 13:10:41.514 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:41.518 New DB connection, total: 2
2009-08-30 13:10:41.576 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:41.579 Current Schema Version: 1214
2009-08-30 13:10:41.594 Preview Error: Previewer file '/var/lib/mythtv/recordings/1091_20090830131037.mpg' is not valid.
2009-08-30 13:10:41.597 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1091_20090830131037.mpg'
2009-08-30 13:10:41.670 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/recordings/1091_20090830131037.mpg.png) exists: 0 readable: 0 size: 0
2009-08-30 13:12:32.646 Expiring 0 MBytes for 1071 @ Sun Aug 30 13:10:23 2009 => Unknown
2009-08-30 13:12:32.652 Expiring 0 MBytes for 1091 @ Sun Aug 30 13:10:37 2009 => Unknown
2009-08-30 13:15:33.413 TVRec(1): Changing from WatchingLiveTV to None
2009-08-30 13:15:34.508 Finished recording Unknown: channel 1091

==> /var/log/mythtv/mythfrontend.log <==
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-08-30 12:49:38.295 NVP: Prebuffer wait timed out 10 times.
2009-08-30 12:49:38.619 AFD: Opened codec 0x8b932c0, id(MPEG2VIDEO) type(Video)
2009-08-30 12:49:38.619 AFD: codec AC3 has 6 channels
2009-08-30 12:49:38.621 AFD: Opened codec 0x8a37de0, id(AC3) type(Audio)
2009-08-30 12:49:39.965 NVP: prebuffering pause
2009-08-30 12:50:27.640 [mpeg2video @ 0xb7441744]Warning MVs not available
2009-08-30 12:50:48.880 [mpeg2video @ 0xb7441744]00 motion_type at 38 22
2009-08-30 12:50:48.889 [mpeg2video @ 0xb7441744]Warning MVs not available
2009-08-30 12:51:26.956 NVP: prebuffering pause
2009-08-30 12:51:36.606 NVP: prebuffering pause
2009-08-30 12:51:43.888 NVP: prebuffering pause
2009-08-30 12:51:54.988 NVP: prebuffering pause
2009-08-30 12:52:03.604 NVP: prebuffering pause
2009-08-30 12:52:21.937 NVP: prebuffering pause
2009-08-30 12:52:34.653 NVP: prebuffering pause
2009-08-30 12:52:40.122 NVP: prebuffering pause
2009-08-30 12:52:51.405 NVP: prebuffering pause
2009-08-30 12:52:57.086 NVP: prebuffering pause
2009-08-30 12:55:59.443 NVP: prebuffering pause
2009-08-30 12:56:01.619 NVP: prebuffering pause
2009-08-30 12:56:03.013 NVP: prebuffering pause
2009-08-30 12:56:32.560 NVP: Prebuffer wait timed out 10 times.
2009-08-30 12:56:33.029 AFD: Opened codec 0x8e007f0, id(MPEG2VIDEO) type(Video)
2009-08-30 12:56:33.029 AFD: codec AC3 has 2 channels
2009-08-30 12:56:33.031 AFD: Opened codec 0x8a10930, id(AC3) type(Audio)
2009-08-30 12:56:55.940 NVP: prebuffering pause
2009-08-30 12:57:10.621 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-08-30 12:57:10.921 NVP: Prebuffer wait timed out 10 times.
2009-08-30 12:57:11.369 AFD: Opened codec 0x9d83380, id(MPEG2VIDEO) type(Video)
2009-08-30 12:57:11.369 AFD: codec AC3 has 6 channels
2009-08-30 12:57:11.371 AFD: Opened codec 0x9ac1000, id(AC3) type(Audio)
2009-08-30 12:57:11.371 AFD: codec AC3 has 2 channels
2009-08-30 12:57:11.372 AFD: Opened codec 0x8b6cb30, id(AC3) type(Audio)
2009-08-30 12:57:12.713 NVP: prebuffering pause
2009-08-30 12:57:46.806 NVP: prebuffering pause
2009-08-30 12:57:49.027 NVP: prebuffering pause
2009-08-30 12:57:52.988 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-08-30 12:57:52.989 AFD: Opened codec 0x8cdb4f0, id(MPEG2VIDEO) type(Video)
2009-08-30 12:57:52.990 AFD: codec AC3 has 6 channels
2009-08-30 12:57:52.991 AFD: Opened codec 0x8cdb0d0, id(AC3) type(Audio)
2009-08-30 12:57:53.117 NVP: Prebuffer wait timed out 10 times.
2009-08-30 12:57:54.343 NVP: prebuffering pause
2009-08-30 12:58:18.277 NVP: prebuffering pause
2009-08-30 12:58:58.059 NVP: prebuffering pause
2009-08-30 13:00:02.307 NVP: prebuffering pause
2009-08-30 13:00:03.025 [ac3 @ 0xb7441744]frame CRC mismatch
2009-08-30 13:00:03.340 NVP: prebuffering pause
2009-08-30 13:00:03.830 NVP: prebuffering pause
2009-08-30 13:04:33.790 [mpeg2video @ 0xb7441744]00 motion_type at 100 6
2009-08-30 13:04:33.819 [mpeg2video @ 0xb7441744]Warning MVs not available
2009-08-30 13:04:52.430 NVP: prebuffering pause
2009-08-30 13:06:41.968 [mpeg2video @ 0xb7441744]Warning MVs not available
2009-08-30 13:06:51.377 [mpeg2video @ 0xb7441744]ac-tex damaged at 66 50
2009-08-30 13:07:01.497 NVP: prebuffering pause
2009-08-30 13:07:05.459 NVP: prebuffering pause
2009-08-30 13:07:12.342 NVP: prebuffering pause
2009-08-30 13:07:19.626 NVP: prebuffering pause
2009-08-30 13:07:30.375 NVP: prebuffering pause
2009-08-30 13:07:48.508 NVP: prebuffering pause
2009-08-30 13:07:53.641 NVP: prebuffering pause
2009-08-30 13:08:22.590 NVP: prebuffering pause
2009-08-30 13:08:31.039 NVP: prebuffering pause
2009-08-30 13:08:42.073 NVP: prebuffering pause
2009-08-30 13:08:49.122 NVP: prebuffering pause
2009-08-30 13:08:52.939 NVP: prebuffering pause
2009-08-30 13:08:58.289 NVP: prebuffering pause
2009-08-30 13:09:01.805 NVP: prebuffering pause
2009-08-30 13:09:03.455 NVP: prebuffering pause
2009-08-30 13:09:16.640 NVP: prebuffering pause
2009-08-30 13:09:19.838 NVP: prebuffering pause
2009-08-30 13:09:23.788 NVP: prebuffering pause
2009-08-30 13:09:27.452 [mpeg2video @ 0xb7441744]skipped MB in I frame at 4 0
2009-08-30 13:09:31.821 NVP: prebuffering pause
2009-08-30 13:09:46.855 NVP: prebuffering pause
2009-08-30 13:09:57.454 NVP: prebuffering pause
2009-08-30 13:10:03.670 NVP: prebuffering pause
2009-08-30 13:10:08.586 NVP: prebuffering pause
2009-08-30 13:10:21.307 NVP: prebuffering pause
2009-08-30 13:10:22.288 NVP: prebuffering pause
2009-08-30 13:10:23.736 NVP: prebuffering pause
2009-08-30 13:10:23.787 WriteAudio: buffer underrun
2009-08-30 13:10:38.783 New DB connection, total: 5
2009-08-30 13:10:38.804 Connected to database 'mythconverg' at host: localhost
2009-08-30 13:10:41.961 NVP: Prebuffer wait timed out 10 times.
2009-08-30 13:10:42.317 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-08-30 13:10:42.347 AFD: Opened codec 0x8cdb4f0, id(MPEG2VIDEO) type(Video)
2009-08-30 13:10:42.347 AFD: codec AC3 has 6 channels
2009-08-30 13:10:42.349 AFD: Opened codec 0x8cdb0d0, id(AC3) type(Audio)
2009-08-30 13:10:42.349 AFD: codec AC3 has 2 channels
2009-08-30 13:10:42.351 AFD: Opened codec 0x97fdd70, id(AC3) type(Audio)
2009-08-30 13:10:43.505 NVP: prebuffering pause
2009-08-30 13:10:44.369 NVP: prebuffering pause
2009-08-30 13:15:33.303 TV: Attempting to change from WatchingLiveTV to None
2009-08-30 13:15:34.602 TV: Changing from WatchingLiveTV to None
2009-08-30 13:15:34.716 DPMS Reactivated.
2009-08-30 13:15:39.129 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Aug 30 06:34:42 jc-myth syslogd 1.5.0#5ubuntu3: restart.
Aug 30 06:39:01 jc-myth /USR/SBIN/CRON[18316]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 06:40:01 jc-myth /USR/SBIN/CRON[18455]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 06:47:01 jc-myth /USR/SBIN/CRON[18644]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
Aug 30 06:47:05 jc-myth mythtv-database[18734]: mythconverg checked and backedup.
Aug 30 06:47:06 jc-myth syslogd 1.5.0#5ubuntu3: restart.
Aug 30 06:50:01 jc-myth /USR/SBIN/CRON[18968]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:00:01 jc-myth /USR/SBIN/CRON[19168]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 07:00:01 jc-myth /USR/SBIN/CRON[19183]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:09:01 jc-myth /USR/SBIN/CRON[19406]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 07:10:01 jc-myth /USR/SBIN/CRON[19545]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:17:01 jc-myth /USR/SBIN/CRON[19734]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 07:20:01 jc-myth /USR/SBIN/CRON[19874]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:30:01 jc-myth /USR/SBIN/CRON[20067]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:39:01 jc-myth /USR/SBIN/CRON[20262]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 07:40:01 jc-myth /USR/SBIN/CRON[20401]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 07:45:05 jc-myth dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 192.168.1.1 port 67
Aug 30 07:45:05 jc-myth dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Aug 30 07:45:05 jc-myth dhclient: bound to 192.168.1.100 -- renewal in 33896 seconds.
Aug 30 07:50:02 jc-myth /USR/SBIN/CRON[20595]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:00:01 jc-myth /USR/SBIN/CRON[20800]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 08:00:01 jc-myth /USR/SBIN/CRON[20803]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:09:01 jc-myth /USR/SBIN/CRON[21087]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 08:10:01 jc-myth /USR/SBIN/CRON[21226]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:13:31 jc-myth ntpd[3650]: kernel time sync status change 4001
Aug 30 08:17:01 jc-myth /USR/SBIN/CRON[21415]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 08:20:01 jc-myth /USR/SBIN/CRON[21555]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:30:01 jc-myth /USR/SBIN/CRON[21748]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:39:01 jc-myth /USR/SBIN/CRON[21943]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 08:40:01 jc-myth /USR/SBIN/CRON[22082]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 08:50:01 jc-myth /USR/SBIN/CRON[22275]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:00:01 jc-myth /USR/SBIN/CRON[22480]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 09:00:01 jc-myth /USR/SBIN/CRON[22483]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:06:01 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:09:01 jc-myth /USR/SBIN/CRON[22790]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 09:10:01 jc-myth /USR/SBIN/CRON[22930]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:12:17 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:13:22 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:17:01 jc-myth /USR/SBIN/CRON[23261]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 09:17:21 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:17:41 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:17:56 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:18:02 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:20:01 jc-myth /USR/SBIN/CRON[23505]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:21:47 jc-myth ntpd[3650]: kernel time sync status change 0001
Aug 30 09:23:55 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:30:01 jc-myth /USR/SBIN/CRON[23771]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:33:12 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:37:48 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:38:23 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:38:34 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:39:01 jc-myth /USR/SBIN/CRON[24126]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 09:39:07 jc-myth lircd-0.8.4a[1534]: removed client
Aug 30 09:40:01 jc-myth /USR/SBIN/CRON[24318]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 09:40:33 jc-myth lircd-0.8.4a[1534]: accepted new client on /dev/lircd
Aug 30 09:50:01 jc-myth /USR/SBIN/CRON[24978]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:00:01 jc-myth /USR/SBIN/CRON[25220]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 10:00:01 jc-myth /USR/SBIN/CRON[25223]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:09:01 jc-myth /USR/SBIN/CRON[25507]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 10:10:01 jc-myth /USR/SBIN/CRON[25646]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:17:01 jc-myth /USR/SBIN/CRON[25863]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 10:20:01 jc-myth /USR/SBIN/CRON[26006]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:30:01 jc-myth /USR/SBIN/CRON[26200]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:39:01 jc-myth /USR/SBIN/CRON[26389]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 10:40:01 jc-myth /USR/SBIN/CRON[26533]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 10:50:01 jc-myth /USR/SBIN/CRON[26726]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:00:01 jc-myth /USR/SBIN/CRON[26931]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 11:00:01 jc-myth /USR/SBIN/CRON[26934]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:09:01 jc-myth /USR/SBIN/CRON[27217]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 11:10:01 jc-myth /USR/SBIN/CRON[27356]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:17:01 jc-myth /USR/SBIN/CRON[27545]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 11:20:01 jc-myth /USR/SBIN/CRON[27685]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:21:16 jc-myth ntpd[3650]: kernel time sync status change 4001
Aug 30 11:30:01 jc-myth /USR/SBIN/CRON[27878]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:38:19 jc-myth ntpd[3650]: kernel time sync status change 0001
Aug 30 11:39:01 jc-myth /USR/SBIN/CRON[28067]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 11:40:01 jc-myth /USR/SBIN/CRON[28211]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 11:50:01 jc-myth /USR/SBIN/CRON[28404]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:00:01 jc-myth /USR/SBIN/CRON[28602]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 12:00:01 jc-myth /USR/SBIN/CRON[28616]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:09:01 jc-myth /USR/SBIN/CRON[28841]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 12:10:01 jc-myth /USR/SBIN/CRON[28980]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:12:29 jc-myth ntpd[3650]: kernel time sync status change 4001
Aug 30 12:17:01 jc-myth /USR/SBIN/CRON[29169]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 12:20:01 jc-myth /USR/SBIN/CRON[29307]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:29:32 jc-myth ntpd[3650]: kernel time sync status change 0001
Aug 30 12:30:01 jc-myth /USR/SBIN/CRON[29530]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:39:01 jc-myth /USR/SBIN/CRON[29817]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 12:40:01 jc-myth /USR/SBIN/CRON[29961]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 12:50:02 jc-myth /USR/SBIN/CRON[30226]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 13:00:01 jc-myth /USR/SBIN/CRON[30562]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 13:00:01 jc-myth /USR/SBIN/CRON[30565]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 30 13:09:01 jc-myth /USR/SBIN/CRON[30874]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 30 13:10:01 jc-myth /USR/SBIN/CRON[31015]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 13:15:39 jc-myth lircd-0.8.4a[1534]: removed client

==> /var/log/Xorg.0.log <==
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2 Generic Mouse
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event5"
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Configuring as mouse
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Generic Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Generic Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Generic Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event3"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Dell Dell USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Dell Dell USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Dell Dell USB Keyboard: xkb_layout: "us"

==> /home/jc/.xsession-errors <==
2009-08-29 22:05:30.121 New DB connection, total: 1
2009-08-29 22:05:30.130 Connected to database 'mythconverg' at host: localhost
2009-08-29 22:05:30.132 Closing DB connection named 'DBManager0'
2009-08-29 22:05:30.135 Primary screen 0.
2009-08-29 22:05:30.135 Connected to database 'mythconverg' at host: localhost
2009-08-29 22:05:30.137 Using screen 0, 1920x1080 at 0,0
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-08-29 23:45:02.835 Using runtime prefix = /usr
2009-08-29 23:45:03.370 XScreenSaver support enabled
2009-08-29 23:45:03.371 DPMS is active.
2009-08-29 23:45:03.372 Empty LocalHostName.
2009-08-29 23:45:03.372 Using localhost value of jc-myth
2009-08-29 23:45:03.384 New DB connection, total: 1
2009-08-29 23:45:03.393 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:45:03.395 Closing DB connection named 'DBManager0'
2009-08-29 23:45:03.398 Primary screen 0.
2009-08-29 23:45:03.398 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:45:03.400 Using screen 0, 1920x1080 at 0,0
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
** (update-notifier:3487): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-08-30 09:17:19.731 Using runtime prefix = /usr
2009-08-30 09:17:20.266 XScreenSaver support enabled
2009-08-30 09:17:20.267 DPMS is active.
2009-08-30 09:17:20.268 Empty LocalHostName.
2009-08-30 09:17:20.268 Using localhost value of jc-myth
2009-08-30 09:17:20.280 New DB connection, total: 1
2009-08-30 09:17:20.289 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:17:20.291 Closing DB connection named 'DBManager0'
2009-08-30 09:17:20.294 Primary screen 0.
2009-08-30 09:17:20.295 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:17:20.296 Using screen 0, 1920x1080 at 0,0
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-08-30 09:37:46.867 Using runtime prefix = /usr
2009-08-30 09:37:47.403 XScreenSaver support enabled
2009-08-30 09:37:47.403 DPMS is active.
2009-08-30 09:37:47.404 Empty LocalHostName.
2009-08-30 09:37:47.404 Using localhost value of jc-myth
2009-08-30 09:37:47.416 New DB connection, total: 1
2009-08-30 09:37:47.425 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:37:47.428 Closing DB connection named 'DBManager0'
2009-08-30 09:37:47.430 Primary screen 0.
2009-08-30 09:37:47.431 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:37:47.432 Using screen 0, 1920x1080 at 0,0
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-08-30 09:40:32.417 Using runtime prefix = /usr
2009-08-30 09:40:32.951 XScreenSaver support enabled
2009-08-30 09:40:32.952 DPMS is active.
2009-08-30 09:40:32.953 Empty LocalHostName.
2009-08-30 09:40:32.953 Using localhost value of jc-myth
2009-08-30 09:40:32.965 New DB connection, total: 1
2009-08-30 09:40:32.974 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:40:32.976 Closing DB connection named 'DBManager0'
2009-08-30 09:40:32.978 Primary screen 0.
2009-08-30 09:40:32.979 Connected to database 'mythconverg' at host: localhost
2009-08-30 09:40:32.981 Using screen 0, 1920x1080 at 0,0
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.0G  8.5G  19% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  388K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  144K  501M   1% /dev
tmpfs                 501M     0  501M   0% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda6             920G   21G  899G   3% /var/lib

==> uname -a <==
Linux jc-myth 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model:          GeForce 8500 GT
IRQ:            16
Video BIOS:      60.86.41.00.85
Card Type:      PCI-E
DMA Size:      40 bits
DMA Mask:      0xffffffffff
Bus Location:      02.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1001MiB
     *-cpu
          product: AMD Sempron(tm) Processor LE-1250
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: 15.15.2
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=[REMOVED] latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce 8500 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by tgm4883 on 2009-08-30
Do any of your recorded shows work?

---

### Post by jccubs on 2009-08-30
Yes,  they are working fine.  I seem to have things in control now, but I know last time I installed I did not have to manually enter the ID's for each channel.

---

### Post by arnaudv6 on 2009-10-17
Ok, my post is related to your problem with panels disappearing,
"Failed to receive a reply from the session manager" message,
and non-working key bindings :

I ran into that problem today on my Gentoo,
I think I played too much with the notification area of my panels
... but I've played with so many things : I can not assure this is the responsible one ;-)

Well, then to get the things working again,
I removed from my account every panel related setting file,
logged out, and killed every thing related to dbus :
that last step seams to be the key :-)

I'm late I know, but maybe this will help someone once.
Arnaudv6

---

