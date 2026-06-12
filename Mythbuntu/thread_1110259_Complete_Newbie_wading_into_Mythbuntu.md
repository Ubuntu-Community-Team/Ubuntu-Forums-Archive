---
title: "Complete Newbie wading into Mythbuntu"
date: 2009-03-29
forum: Mythbuntu
---

### Post by MountainKing on 2009-03-29
This is my first foray into Linux of any sort and I thought it would be fun to tinker around with a Mythbuntu installation so I could record TV etc etc.

I am an utter newbie, I have been using Windows for years at a very high level, I have QA'ed Windows software and administered small networks and built countless PCs over the years.  But when it comes to Linux, as thrilling as it is, I am utterly lost.  Fun times. :)

Anyway, I have downloaded Mythbuntu 8.10, I have a PC all ready to go (Intel P4 with a gig of Ram and a 300gb HDD).  I bought a brand new Hauppauge Win TV PVR 150 card (with remote).  I think I have everything ready to roll.

So I installed the OS and started configuring it, but I am getting lost in the weeds, when I get into configuring the storage directories (I think I need 3 of them) I can't seem to get the command to "commit" (if that's the right word).  So when I leave that config screen I get a warning "Directory 'TVstorage' is not created... do you know what you're doing?"

I am trying to do all this thru the GUI as I understood that wast he way Mythbuntu works, but everywhere I search for help I come across command line commands that don't really help as I don't know how to use the command line interface.

So long story short here are my questions:
-Can I configure mythbuntu and mythtv entirely thru the gui?
-Is my hardware going to work?  There seems to be some debate over the PVR 150 card.

I am really hoping some kind soul won't mind patiently answering my questions (the questions that will probably get stupider as I progress :P).

---

### Post by theophile on 2009-03-29
Hi and welcome!

Theoretically, you should be able to get everything up and running through the GUI. In reality, you aren't likely to go very long without having to use the command line to some degree. If you're like most people, eventually something will get messed up and there's no GUI-based recovery application. Unlike most Windows software which is self-contained, MythTV relies on other component software which is developed independently. 

For example, if you have a problem with recordings not showing up, it could be a problem with the MySQL database. If something goes awry with the web interface, something could be wrong with your Apache or PHP installations. There are a lot of different projects working together and inevitably, something breaks. Using a packaged distribution like Mythbuntu decreases the chances of this happening, but I would still say that sooner or later, you'll have to open up a terminal.

That being said, it's not too bad. Most Linux rookies can be coached through it. We'll tell you what to paste and you just past back the output. If you're patient and have a general aptitude for computers, you'll learn really quickly.

As to your specific problem, it's been a while since I went through the initial Mythbuntu setup so I don't recall what the steps were. Someone else may be of more help in that regard. I'm assuming you went through the hard drive formatting/partitioning steps already. Is that what you meant by needing three storage directories?

For MythTV, you only need one storage directory for recordings. Having others for other media (i.e. downloaded, ripped, etc.) is always a good thing too. But these are not the MythTV storage directories you have to create during MythTV setup. For MythTV, all you need to set up is the location for the recordings made by the TV tuner.

---

### Post by MountainKing on 2009-03-29
Thank you so much for answering my question.

Some questions that came up from your comments.  Do I need to install anything else to use Mythbuntu or is it all self contained?  IE: you mentioned MySql and Apache for instance... I assumed everything I needed was in the .iso I downloaded.

> **theophile said:**
> As to your specific problem, it's been a while since I went through the initial Mythbuntu setup so I don't recall what the steps were. Someone else may be of more help in that regard. I'm assuming you went through the hard drive formatting/partitioning steps already. Is that what you meant by needing three storage directories?

When configuring Mythbuntu during the set up stage there is a menu with 6 steps:
1 General
2 Capture Cards
3 Video Sources
4 Input Connections
5 Channel Editor
6 Storage Directories

Option six indicates there are 3 Storage Groups (default, LiveTV and DB Backups), I assumed I had to create a directory under each of these headings, but when I exit the configuration screen it tell met the directories I thought I had created do not exist.  

IE 
"PATH nameIused/ doesn't exist"

Here's the stupid part, in the directory setup screen the instruction is: Enter directory name or press Select.  Uh, where is the select button?  Is that Linux speak for something else?

---

### Post by MountainKing on 2009-03-29
well I am finally watching TV, that's a start.

---

### Post by tgm4883 on 2009-03-29
Everything you need is included in the ISO, but not everything is maintained by us (we don't mainstain MySQL for instance).  

The part about the directory not existing is because the directories need to exist already on the file system.  This you must do in on the command line (or alternatively you can use the desktop).

---

### Post by MountainKing on 2009-03-29
Thanks it's coming along, like I said earlier, now I can watch TV, but only channels 2-13.  That's the next thing I want to figure out, after that I need to sort out how to get this remote control... after that... recording.

Help so far has been appreciated, any more would be great :)

---

### Post by MountainKing on 2009-03-29
OK I'm just gonna keep updating this thread as I go along.

I now have all my channels working, I just had the wrong setting (basic as opposed to cable).

Three things left to go:
-get my directory working
-get remote working (I suspect this will be hardest part)
-figure out how to record stuff

---

### Post by Nobodyspeshul on 2009-03-29
Welcome to Linux!

I'm a fairly new user as well, best thing I can suggest is posting your specs somewhere and have a link to it in your Sig, something which I have not done myself.

Also, have you been to [Schedules Direct]("http://www.schedulesdirect.org/") and set up an account there to get your listings?

---

### Post by laffinet on 2009-03-29
1. Directories
You actually shouldn't have to create the directories manually. During installation Mythbuntu creates the default directories. Unless you don't want to use those, you shouldn't have to touch things. 
Sooo, what is currently listed under "Storage directories" ? Do those exist on the system ?

From memory, my system had the following directories created as default:

/var/lib/mythtv/recordings
/var/lib/mythtv/videos
/var/lib/mythtv/music
(one other, which I can't remember right now).

Have a look what's on your system.

Sorry, might not solve your problem directly, but might point you in the right direction.

2. Remote
Figure out your model and google with Mythbuntu or Mythtv. Should give you some guidelines

3. Recording
To schedule recordings conventiently you need to obtain EPG (electronic program guide) data. Once you have that you just go to "Manage Recordings"->"Schedule recordings"->eg "program guide". Here you pick the program you want to record, hit enter and go through the options. All pretty self explanatory.
If you don't have EPG you should look into setting this up first (again, google is your friend. This can vary a lot, depending which country you live in).
Otherwise the only option is to manually schedule recordings (under "manage recordings").

---

### Post by nickrout on 2009-03-29
> **MountainKing said:**
> OK I'm just gonna keep updating this thread as I go along.

I now have all my channels working, I just had the wrong setting (basic as opposed to cable).

Three things left to go:
-get my directory working

dealt with by others I think, but you don't actually need to touch item 6 of mythtv-setup unless you want to do something fancy with different storage directories. Leave it as per the defaults fornow.> 

-get remote working (I suspect this will be hardest part)



get into mythbuntu-control-center and you should just be able to set up the type of receiver and remote.

You get into the control center through the menu system on the frontend by going into setup then setup then knoppmyth. (I think thats the menu structure without a myth box on front of me).
> 
-figure out how to record stuff

1. press the remote key, or r on the keyboard while watching livetv; or

2. go into the manage recordings menu and into the electronic programming guide. Hit OK on the remote (or enter on the keyboard) and navigate through the options.

But really you should read about such stuff here:

[http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

---

### Post by MountainKing on 2009-03-30
Alright, thanks so much everyone I am now down to one last goal.   **Getting the remote control to work**.  From some of the browsing I have done around this site and elsewhere it appears that the choice of Card+Remote I made may have put me at a disadvantage.

I have the Huappague WinTV PVR-150 MCE Kit

I only (for now) want to use it to control the MythTV interface, can I assume that for that purpose I do not need to use the IR transmitter?

This thread [http://ubuntuforums.org/showthread.php?t=1105313](http://ubuntuforums.org/showthread.php?t=1105313) has some discussion about getting this remote working, in fact it appears that post 6 has a bunch of code and configs that I could use... if I had the foggiest notion on how to carry out the commands displayed there.

Can someone point me the in the right direction as to how to use those commands?  Thanks.  [-o<

EDIT: I should point out that so far when I point the remote at the receiver and push a button the redlight is going on in the receiver, but there does not appear to be any affect to MythTV.

---

### Post by nickrout on 2009-03-30
Could you tell me whether you have set it up in mythbuntu-control-center?

I believe the right one to choose is "Hauppauge TV Card".

---

### Post by MountainKing on 2009-03-30
> **nickrout said:**
> Could you tell me whether you have set it up in mythbuntu-control-center?

I believe the right one to choose is "Hauppauge TV Card".

Yeah I did that, but I am not getting joy from the remote control yet.  The wee light flashes, but nothing happens.

---

### Post by tgm4883 on 2009-03-31
Is the remote you have pictured here?

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

If so, in MCC you should configure it as a "Windows MCEUSB2 Remote" or something to that effect.

---

### Post by MountainKing on 2009-03-31
> **tgm4883 said:**
> Is the remote you have pictured here?

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

If so, in MCC you should configure it as a "Windows MCEUSB2 Remote" or something to that effect.

Yup, I have the black one, 2nd from the right.  I was about to go to bed, but first I'll go test this out...

---

### Post by MountainKing on 2009-03-31
W00t.  That did it.  Thank you so much!  I am very excited right now.  

Thanks to everyone who offered advice and support.  I think I will be around for a while now, but it might be a while before I can actually help anyone else  :)

Oh, one more question.  With the hardware I described earlier, should I be able to watch one channel while recording another.  I assume that I should  be able to and maybe its just a configuration I have to sort out.

Anyway, thanks again.

You all rock  :guitar:

---

### Post by nickrout on 2009-03-31
> **MountainKing said:**
> W00t.  That did it.  Thank you so much!  I am very excited right now.  

Thanks to everyone who offered advice and support.  I think I will be around for a while now, but it might be a while before I can actually help anyone else  :)

Oh, one more question.  With the hardware I described earlier, should I be able to watch one channel while recording another.  I assume that I should  be able to and maybe its just a configuration I have to sort out.

Anyway, thanks again.

You all rock  :guitar:

glad it goes :)

no you can only watch/record one channel with one pvr150 - it only has one tuner.

---

### Post by uncle hammy on 2009-03-31
Before you go too far with recordings, I would make 2 recommendations...

1.  Make sure you are doing daily backups of your MySQL database.  I am like you, I have been using Windows as an Admin or Developer for years now, but my Linux is not fantastic (though getting much better).  As a result, I installed the MySQL admin tools on my windows pc, and just do the backups from there.  You just have to allow network access in MySQL.  [http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html) "Modifying for multiple systems".

2. Personally, I would split my 300gb hdd into 2 partitions.  Maybe 5GB ext3 for the OS and 295GB xfs for storage.  This can be done with GParted or during installation.  Mount the large partition to something like /myth_storage, change owner to "mythtv", set the permissions to match /var/lib/mythtv/recordings, and make 2 directories in there "recordings" & "livetv".  Then use the gui to change your storage directories to these.

If you do the above, you can do a clean installation without disturbing your recordings and restore your database in about 15 minutes.  You'll be back like you never changed anything in no time...the first round of updates will require more time than anything.

---

### Post by nickrout on 2009-03-31
> **uncle hammy said:**
> Before you go too far with recordings, I would make 2 recommendations...

1.  Make sure you are doing daily backups of your MySQL database.  I am like you, I have been using Windows as an Admin or Developer for years now, but my Linux is not fantastic (though getting much better).  As a result, I installed the MySQL admin tools on my windows pc, and just do the backups from there.  You just have to allow network access in MySQL.  [http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html) "Modifying for multiple systems".

2. Personally, I would split my 300gb hdd into 2 partitions.  Maybe 5GB ext3 for the OS and 295GB xfs for storage.  This can be done with GParted or during installation.  Mount the large partition to something like /myth_storage, change owner to "mythtv", set the permissions to match /var/lib/mythtv/recordings, and make 2 directories in there "recordings" & "livetv".  Then use the gui to change your storage directories to these.

If you do the above, you can do a clean installation without disturbing your recordings and restore your database in about 15 minutes.  You'll be back like you never changed anything in no time...the first round of updates will require more time than anything.


mythbuntu does this automatically on install now. On my last install it made an ext3 / partition of 7G and the rest mounted on /var/lib as xfs

/var/lib is in fact the place you should mount the data/storage partition as thats where mythbuntu stores recordings, videos, music, archives etc.

---

### Post by uncle hammy on 2009-03-31
Ahh, well there you go, I wasn't aware of that.  I am still using the same config that I set up back when it did not do that.  So, it's pure habit for me.

---

