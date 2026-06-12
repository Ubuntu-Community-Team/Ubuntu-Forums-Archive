---
title: "Total impasse setting-up Mythbuntu"
date: 2011-01-09
forum: Mythbuntu
---

### Post by torpare on 2011-01-09
Hi

I've been making repeated attempts, all so far unsuccessful, to set up Mythbuntu 10.10.

I've installed it on a 4GB usb thumb drive and have this connected to my main (workstation) PC.  Installed on that machine's hard drive is (apart from WinXP) Mepis Linux - so there's a swap partition already there.  I intended this to be the backend.  

I'm using the CD as a live frontend running on my HTPC in my TV room.  So this is a "live session", which the Wiki doesn't directly refer to.  Instead, clicking on the Mythbuntu icon on the frontend's desktop brings up a box called "Mythbuntu live session configuration" which demands a "4-digit security key set" - which I'm supposed to get from the backend MythTV setup.

Major problem :(

Although clicking on Applications -> System -> MythTV Backend Setup on the backend's menu is supposed to bring up the backend setup screen, it doesn't.  Instead it brings up what I take to be the frontend setup screen ("select language", 2 pages of "database configuration" in which the only reference is to frontend...).  

In MCC > System Roles I have Backend Role/Primary backend, and Frontend Role/Desktop frontend, checked.  If that doesn't conform to my physical setup as described, what does? 

Can anyone please suggest what I might do?  Right now, I might just as well not have bothered, and saved myself a lot of grief.

---

### Post by newlinux on 2011-01-09
If you want to run the backend setup at a terminal on the backend type
```

mythtv-setup

```


Unless you've changed the default backend security PIN, it is 0000.

Have you completed the backend setup on this machine previously?

---

### Post by tgm4883 on 2011-01-09
The live disk is for running the frontend, the backend doesn't run on it. You may be able to get it to work, but AFAIK it's completely untested.

---

### Post by newlinux on 2011-01-09
> **tgm4883 said:**
> The live disk is for running the frontend, the backend doesn't run on it. You may be able to get it to work, but AFAIK it's completely untested.

I assumed from the below quote he had the backend booting of a 4GB USB drive on another machine. If that isn't true then, yeah,I wouldn't suggest getting the front and backend to work off the liveCD


> **torpare said:**
> Hi
...

I've installed it on a 4GB usb thumb drive and have this connected to my main (workstation) PC.  Installed on that machine's hard drive is (apart from WinXP) Mepis Linux - so there's a swap partition already there.  I intended this to be the backend...  


---

### Post by BicyclerBoy on 2011-01-09
You need to run mythtv-setup (terminal) on the each backend before doing anything else.
This has always been the case.
You should do this after every update.

The backend should be happy & running (with database-mythfilldatabase, tuners, network) before anything else..

The first time you run myth frontend it will set the language prefs.
Each frontend has its own language prefs (I believe)

Run stuff (with debugging) from terminal so you can see the stdout messages.

---

### Post by torpare on 2011-01-10
> **tgm4883 said:**
> The live disk is for running the frontend, the backend doesn't run on it. You may be able to get it to work, but AFAIK it's completely untested.@tgm4883
I must have explained myself badly.

It is in fact for running the frontend that I'm using the live disc, just as you say.  That's what I was attempting to describe.

Just so we're clear...:)

---

### Post by torpare on 2011-01-10
> **BicyclerBoy said:**
> You need to run mythtv-setup (terminal) on the each backend before doing anything else.
This has always been the case.
You should do this after every update.

The backend should be happy & running (with database-mythfilldatabase, tuners, network) before anything else..

The first time you run myth frontend it will set the language prefs.
Each frontend has its own language prefs (I believe)

Run stuff (with debugging) from terminal so you can see the stdout messages.Hi BicyclerBoy
As a (more-or-less complete) ignoramus, I must of course defer to your superior knowledge - and will gladly do so, so far as I'm able.

However, I remain curious as to why I'm being forced to use a terminal when (as appears from this, among other things I've read, [http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#configure](http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#configure) ) the designers' intention was that the user be provided with a GUI for performing the entire backend setup process.

The Wiki also confirms this (though its failure so far to provide any screenshots - still "TBD") severely vitiates the Wiki's usefulness to any noob such as myself, which is regrettable.

Experienced Linux users such as yourself are of course entirely comfortable using a CLI.  I'm not, unfortunately, and would much prefer to use the GUI which - despite the literature promising it - the ver. 10.10 CD doesn't, for some unknown reason, appear to be delivering.  Hence my frustration and bewilderment.

---

### Post by torpare on 2011-01-10
> **newlinux said:**
> If you want to run the backend setup at a terminal on the backend type
```

mythtv-setup

```


Unless you've changed the default backend security PIN, it is 0000.

Have you completed the backend setup on this machine previously?@newlinux

Hi
No, I haven't - because the GUI for doing so has never appeared on my backend (as explained in the immediately preceding post).  So no, I haven't changed the default backend security PIN.

When I go back into Mythbuntu - I'm posting this using (shudder!) Windows - I'll try to follow BicyclerBoy's instructions using a terminal instead.  If this is successful then I ought to be in a position to make some useful progress at last.

As already said above, I remain baffled as to why  Mythbuntu 10.10 isn't putting-up the backend GUI on my backend machine as it's supposed to.  Even more baffled as to why it puts-up a GUI but it's the wrong one.  Something clearly isn't right, and I don't know what.

---

### Post by torpare on 2011-01-10
> **BicyclerBoy said:**
> You need to run mythtv-setup (terminal) on the each backend before doing anything else.Understood but, unfortunately, proving impossible...> The backend should be happy & running (with database-mythfilldatabase, tuners, network) before anything else..

Run stuff (with debugging) from terminal so you can see the stdout messages....for this very reason:- that I haven't the glimmering of an idea how I'm to run MythTV setup **without** a GUI to do it with.

We keep returning to this core problem, unfortunately.  I had understood that the whole point of Mythbuntu was to enable the non-linux user (me, for instance) to make use of MythTV through the agency of a "barebones" Ubuntu installation.  If said installation refuses to work as it's supposed-to, it leaves the non-linux user completely high and dry.  That's the situation I find myself in.

Logically, it seems to me, it's the non-functioning of Mythbuntu in the way intended by its developers that needs addressing first, because it's that functionality that the non-linux/non-Ubuntu user is relying upon as a bedrock for everything else.  Why am I seeing the behaviour I described in the OP in this thread, which in no way accords with what is supposed to be happening, and how can I get the system to function in the way it's supposedly designed-to - without first having to try ro turn myself into a Ububtu/Linux expert (which the whole point of Mythbuntu was allegedly to avoid any necessity for)?

Just as a (completely off-the-wall) suggestion:- might the fact that I'm running Mythbuntu from a usb stick have anything to do with the problems I'm experiencing?  I ask because I've had no previous experience of running an OS this way and don't know what, if any, pitfalls it may have.  (I've noticed that it's **very** slow, for example - is this normal?).

---

### Post by larsolav on 2011-01-10
Is your backend set up and working properly? Is the backend properly recording stuff? You should be able to set it up using the GUI setup menus and no terminal needed. You should have everything you need to set up both the backend and the frontend in the respective computers' Myth Control Centre (just like the creators of Mythbuntu intend. In MCC there is a link to the backend setup screen.

---

### Post by newlinux on 2011-01-10
You said you weren't able to configure the backend. What happens when you open up a terminal from mythbuntu on the backend and type:

mythtv-setup

---

### Post by BicyclerBoy on 2011-01-11
Exactly..

We want mythtv-setup run from a terminal so we get to see all the stdout messages.
This will reveal all sorts of issues.
mythtv-setup etc allow setting the verbosity of the debug messages.

Running applications from the terminal is an excellent start to debugging in linux & windows. 

If your desktop menu launcher is screwed up then the terminal method is ideal.

Make sure the database stuff is installed on the backend machine.
You can connect/login to the mysql server quite easily to check it works.
You can run terminal scripts that create the database tables.
see the mythTV website about the scripts that backup & restore/create the database.

---

### Post by nickrout on 2011-01-11
Heres hoping that the OP isn't running mythtv-setup from a console (ie alt-ctrl-f1).

You need to start it from an x-terminal, ie from withing the desktop click applications|accessroeis|terminal.

type mythtv-setup then <enter> and the setup gui will appear.

Alternatively the mythbuntu way is to click applications|system|mythbuntu control centre. click the mysql button and there is a button to start mythtv-setup.

---

### Post by torpare on 2011-01-11
Sorry guys, this is getting us nowhere!

Can I plead that you take on board the fact that Mythbuntu is a very different animal from Ubuntu, and that it's supposed to be able to be used as it stands?

Now, in spite of the fact that that is fundamental as far as I'm concerned I wouldn't wish people to think I'm being pedantic or difficult.  Believe me, I am truly appreciative of the fact that people are willing to try to to help me, out of the goodness of their hearts.  So, can I please assure everyone (in case there's any doubt) that - even though I shouldn't have to - I would be only too glad to use a terminal to try to solve this problem if I could - because it's driving me nuts.  

And I have - of course - tried to; please believe me.  I've got nowhere because (and this is the only way I can put it, in my language not yours) Mythbuntu running on my backend machine, for some reason I can't fathom persists in thinking that it's running on a frontend (and behaving accordingly), even though I have from the start told it that it's a backend.  Not only is this shown by the fact that it has refused to bring up the backend GUI but also by the fact that in a terminal as well its behaviour and output is frontend-oriented.  When I run the terminal (which I've now done several times) no matter how I answer the questions (and I've tried every way) it ends up every time bringing me back to the frontend.  It will not allow me to configure the backend and (although I'm sure any of you guys would know how to) I don't know how to force it to do so - because I'm not a Linux user and was not aiming to become one.  In other words, I'm trapped in an endless loop.

In sheer desperation, I now plan to uninstall and reinstall Mythbuntu to see if that makes any difference.  Tedious and aggravating, but I see no other choice.

I'll report-back the results.  Meanwhile, a sincere 'thank you' to everyone for the help that's been proffered.

---

### Post by torpare on 2011-01-11
@newlinux> What happens when you open up a terminal from mythbuntu on the backend and type:

mythtv-setup The first thing that happens is that a dialog-box comes up saying that Mythbackend is running and must be closed before Setup can be opened, and asking if that's OK.  I find that baffling and inconsequential in itself (but maybe that's just me...).  If I click on 'no' nothing else happens, so I'm forced to click on 'yes', whereupon I promptly find myself in frontend mode.

@nickrout> type mythtv-setup then <enter> and the setup gui will appear.That's just it:- it doesn't.

---

### Post by thatguruguy on 2011-01-11
> **torpare said:**
> @newlinux The first thing that happens is that a dialog-box comes up saying that Mythbackend is running and must be closed before Setup can be opened, and asking if that's OK.  I find that baffling and inconsequential in itself (but maybe that's just me...).  If I click on 'no' nothing else happens, so I'm forced to click on 'yes', whereupon I promptly find myself in frontend mode.

I'm not sure that you're seeing what you think you're seeing.

---

### Post by thatguruguy on 2011-01-11
> **torpare said:**
> @newlinux The first thing that happens is that a dialog-box comes up saying that Mythbackend is running and must be closed before Setup can be opened, and asking if that's OK.  I find that baffling and inconsequential in itself (but maybe that's just me...).  If I click on 'no' nothing else happens, so I'm forced to click on 'yes', whereupon I promptly find myself in frontend mode.

When you say that you "find yourself in frontend mode," does it look something like the following?

---

### Post by torpare on 2011-01-11
@thatguruguy

No.  That's what I'd call a GUI.  No GUI, of any description, has yet displayed on my Mythbuntu backend desktop.

---

### Post by torpare on 2011-01-11
@thatguruguy

No.  That's what I'd call a GUI.  No GUI, of any description, has yet displayed on my Mythbuntu backend desktop.

---

### Post by newlinux on 2011-01-11
> **torpare said:**
> @thatguruguy

No.  That's what I'd call a GUI.  No GUI, of any description, has yet displayed on my Mythbuntu backend desktop.

You've confused me now. I thought you said the frontend setup was coming up when you use mythtv-setup on your backend. But now you're saying you get no GUI at all? Maybe you should post a screenshot so we can know exactly what is going on. You said you get a dialog box asking to shut down mythbackend, which is what you should get if it is running because you may change parameters that will require a restart of the backend, so you should say yes to that if your backend isn't currently doing anything that stopping it would cause problems (Like getting ready to start a recording) which is why it asks instead of just doing it.

---

### Post by nickrout on 2011-01-11
OK well there will be a whole lot of messages in the terminal where you ran mythtv-setup. Post them.

---

### Post by thatguruguy on 2011-01-11
I must join the chorus of people who are pleading with you to post any messages which appear in your terminal when you run mythtv-setup.

Moreover, I'd like to re-examine some of your other posts in this thread.  For instance, please compare:
> **torpare said:**
> @thatguruguy

No.  That's what I'd call a GUI.  No GUI, of any description, has yet displayed on my Mythbuntu backend desktop.
... to:
> **torpare said:**
> @newlinux The first thing that happens is that a  dialog-box comes up saying that Mythbackend is running and must be  closed before Setup can be opened, and asking if that's OK.  I find that  baffling and inconsequential in itself (but maybe that's just me...).   If I click on 'no' nothing else happens, so I'm forced to click on  'yes', **whereupon I promptly find myself in frontend mode**. [Emphasis added.]
...and:

> **torpare said:**
> Although clicking on Applications -> System -> MythTV Backend  Setup on the backend's menu is supposed to bring up the backend setup  screen, it doesn't.  **Instead it brings up what I take to be the frontend  setup screen** ("select language", 2 pages of "database configuration" in  which the only reference is to frontend...).  
 [Emphasis added.]

In the first statement noted above, you assert that " No GUI, of any description, has yet displayed," yet you make specific references in the other posts I've cited to the display of a GUI (although I acknowledge your assertion that it is the "wrong" setup GUI).  Your statements are inconsistent at best.  At worst, you are being purposefully obtuse.  I am starting to believe that the latter is true, particularly given your apparent refusal to follow suggestions given to you thus far.  Again, the reason people are asking you to runt mythtv-setup in a terminal is to see what error messages, if any, are generated.  It's part of the trouble-shooting process.

I am also interested in the following statement made in your original post:
> **torpare said:**
> 
I've installed it on a 4GB usb thumb drive and have this connected to my main (workstation) PC.  Installed on that machine's hard drive is (apart from WinXP) Mepis Linux - so there's a swap partition already there.  I intended this to be the backend.  


What do you mean, exactly, when you state that you "installed it [by which you apparently mean mythbuntu] on a 4GB usb thumb drive?"  What steps did you follow, exactly, to accomplish this installation?

---

### Post by torpare on 2011-01-12
@that guruguy> Your statements are inconsistent at best. At worst, you are being purposefully obtuse. I am starting to believe that the latter is true, particularly given your apparent refusal to follow suggestions given to you thus far."Inconsistent" I grant you.  Sorry.

But the type of GUI to which I was referring was of exactly that type which you showed an example of in your post: an opening screen with a menu enabling options to be selected.  But yes, you're correct, the others are GUIs too - useless to me but GUIs nonetheless.  I stand corrected.

But I'm mystified why you appear to think yourself justified in making a personal attack on me, still more why you can suspect that I (or anyone else come to that) could "purposefully" (ie with intent) be being obtuse.  For what reason, for God's sake?  Seems a bit paranoid to me.  

Can I suggest that you for your own part are failing to make even a reasonable allowance for the gulf between your knowledge of and familiarity with Ubuntu/Linux and mine?  And for the extent of the difficulties I've been encountering?  Or for the many hours of pretty unrewarding labour I've been dedicating to this?  It's a bit rich after all that to find myself being accused, without the slightest justification, of "purposeful" obtuseness.  

May I point out - since you don't seem able to have deduced it - that because of the intermittent recurring problem I've been having (which I have documented in this thread) in getting a Mythbuntu desktop to function I've been forced to fall back on posting to this forum from within Windows.  Obviously, much as I might have wanted to, from there I couldn't take screenshots.  Contrary to your assertion, I have not refused to follow suggestions given to me: I have done my level best to follow them and I have punctiliously reported-back.> I am also interested in the following statement made in your original post:
Quote:
Originally Posted by torpare View Post
I've installed it on a 4GB usb thumb drive and have this connected to my main (workstation) PC. Installed on that machine's hard drive is (apart from WinXP) Mepis Linux - so there's a swap partition already there. I intended this to be the backend.
What do you mean, exactly, when you state that you "installed it [by which you apparently mean mythbuntu] on a 4GB usb thumb drive?"Why "apparently"?  (Sarcasm?)  What else would I have meant?
> What steps did you follow, exactly, to accomplish this installation?I plugged the thumb drive into my PC and the LiveCD into the PC's CD/DVD drive and booted-up.  In the Mythbuntu menu I selected "Install...", chose to do my own partitioning and in the partitioning screen selected the thumb drive (designated Hard Drive 2 - I have two hard disks), with / as mount point and Grub to be installed on the boot sector (sda0).  That's as much as I remember; I hope it helps but if there's anything else I can tell you please say so.

I have from the start wondered whether the source of the problem might be the fact that I have the OS on a thumb drive not a hard disk.  But since I've no knowledge or experience of using one in this way (and precious little of Linux) I've no idea whether my suspicion is justified: it's just that I can't see what else could be causing it.
  I had - before reading your last post - been on the point of giving up with the thumb drive and instead installing Mythbuntu on my hard drive; this may be the only way to establish definitively whether it's the culprit or not.  I've been loath to contemplate this step up till now because of all the time and patience I've already invested in the way I had planned to set it up, and because nothing I've read had led me to anticipate that an installation on a thumb drive was a risky undertaking.

Is it, in your view, and if so why, please?

For the first time I'm now able to post from within Mythbuntu, and I have just installed Screenshot in the hope that I shall be able to use it for - at last - posting screenshots of what I've been seeing.  If I succeed I will of course lose no time in posting them, not least because (in spite of what you appear to believe) I am trying my damnedest to get help here.

---

### Post by torpare on 2011-01-12
> **newlinux said:**
> You've confused me now. I thought you said the frontend setup was coming up when you use mythtv-setup on your backend. But now you're saying you get no GUI at all? Maybe you should post a screenshot so we can know exactly what is going on. You said you get a dialog box asking to shut down mythbackend, which is what you should get if it is running because you may change parameters that will require a restart of the backend, so you should say yes to that if your backend isn't currently doing anything that stopping it would cause problems (Like getting ready to start a recording) which is why it asks instead of just doing it.@newlinux

I'm sorry about the confusion.  Mea culpa! :(

From the immediately preceding post to thatguruguy (who also pointed out the contradiction) I hope the confusion is now dispelled.

As also stated there, I shall now be trying to employ Screenshot.  Wish me luck!

---

### Post by torpare on 2011-01-12
Screenshots attached

---

### Post by torpare on 2011-01-12
Screenshots attached

---

### Post by larsolav on 2011-01-12
When you click on "Yes" in your first screen shot, does it go directly to the second screenshot ("Would you like to run mythfilldatabse?". It should not, you actually should be getting the backend setup GUI in between these two screenshots.

---

### Post by tgm4883 on 2011-01-12
FWIW, I was confused by all of your posts as well. 


Back on topic, now that we are getting some actual screenshots it seems your backend can't connect to the database. Is mysql running?

```
service mysql status
```

---

### Post by torpare on 2011-01-12
> **larsolav said:**
> When you click on "Yes" in your first screen shot, does it go directly to the second screenshot ("Would you like to run mythfilldatabse?"Hi larsolav

Yes it does.> It should not, you actually should be getting the backend setup GUI in between these two screenshots.You're confirming what I've been assuming all along.  Thank you!

---

### Post by torpare on 2011-01-12
> **tgm4883 said:**
> FWIW, I was confused by all of your posts as well.@tgm4883

I'm sorry.  Words are no real substitute for screenshots, I do realise that.  I was crippled by being prevented from posting from within Mythbuntu.
> Back on topic, now that we are getting some actual screenshots it seems your backend can't connect to the database. Is mysql running?

```
service mysql status
```I typed that code into a terminal, then tried >Applications>System>MythTV Backend Setup again.  Same response as before.

---

### Post by tgm4883 on 2011-01-12
> **torpare said:**
> @tgm4883

I'm sorry.  Words are no real substitute for screenshots, I do realise that.  I was crippled by being prevented from posting from within Mythbuntu.
I typed that code into a terminal, then tried >Applications>System>MythTV Backend Setup again.  Same response as before.

When you typed it in, what did it say?

---

### Post by tgm4883 on 2011-01-12
From the mythbuntu support channel bot
> 
If you are having problems connecting to your mysql database, you can perform the following to reconfigure it: 

1. sudo dpkg-reconfigure mysql-server-5.0 (pay attention to the root password you set, you will need it for the next step) 

2. sudo dpkg-reconfigure mythtv-database 

3. sudo dpkg-reconfigure mythtv-common


---

### Post by thatguruguy on 2011-01-12
You STILL haven't posted any messages generated in the terminal when you type "mythtv-setup."  It will be impossible to help you until you do.

Your posting style implies that you consider yourself eloquent and intelligent.  However, you still seem unwilling or unable to comply with this most basic request.  In fact, it seems that you are going out of your way to avoid providing the information which has been requested, while you seem perfectly willing to bloviate at length about  your observations and how they impact not only you, but any other potential user of mythbuntu.  It is this tendency on your part that led me to suspect that you are being purposefully obtuse.

Your screen shots are interesting.  Now, please provide the messages received in the terminal when you type "mythtv-setup."

---

### Post by nickrout on 2011-01-12
> **thatguruguy said:**
>  bloviate 

Wow I learned a new word today!

---

### Post by torpare on 2011-01-13
> **tgm4883 said:**
> When you typed it in, what did it say?"mysql start/running, process 1028"

---

### Post by torpare on 2011-01-13
> **tgm4883 said:**
> If you are having problems connecting to your mysql database, you can perform the following to reconfigure it:

1. sudo dpkg-reconfigure mysql-server-5.0 (pay attention to the root password you set, you will need it for the next step) @tgm4883
Attached is a screenshot showing the response I got to this command.

I took this to mean that the other two steps weren't available, and so I halted there.  Was this correct or should I have gone on anyway?

---

### Post by torpare on 2011-01-13
> **thatguruguy said:**
> You STILL haven't posted any messages generated in the terminal when you type "mythtv-setup."  It will be impossible to help you until you do.

Your posting style implies that you consider yourself eloquent and intelligent.  However, you still seem unwilling or unable to comply with this most basic request.  In fact, it seems that you are going out of your way to avoid providing the information which has been requested, while you seem perfectly willing to bloviate at length about  your observations and how they impact not only you, but any other potential user of mythbuntu.  It is this tendency on your part that led me to suspect that you are being purposefully obtuse.

Your screen shots are interesting.  Now, please provide the messages received in the terminal when you type "mythtv-setup."Do you get some kind of kick out of being gratuitously offensive?  

If you're interested in helping, you'll see the messages you're asking about in the screenshot attached to the preceding post, to tgm4883.> it seems that you are going out of your way to avoid providing the information which has been requested
It never crosses your mind that I could simply have missed seeing it? 

It might interest you to know (or even better you might have figured it out for yourself) that the two dialog boxes that come up are superimposed on top of the messages in the terminal, causing me not even to have registered the fact that there were messages there which I'd omitted to capture (you see, I'm not used to using a CLI - but I already explained that didn't I).  
>  your observations and how they impact not only you, but any other potential user of mythbuntu.Isn't that supposed to be the purpose of a forum?

Just what is it, exactly, that you think gives you grounds for attacking me?  I'd be very interested to know.

---

### Post by tgm4883 on 2011-01-13
I'm going to say this one time. Everybody chill out.



Back on topic. You don't have a SQL server, so that would explain why you are unable to get anywhere. That might have been a nice piece of information for you to tell us earlier, as it would have saved a lot of time. If anything, start out with what options you selected during install. 

Since you don't have an SQL server in your environment, you need to add one. This can be done via the mythbuntu control centre.

---

### Post by nickrout on 2011-01-13
stop pull up, he possibly does have a mysql server, he just couldn't copy the command that was suggested. (look at the lack of hyphen between mysql and server in the command he typed.


And please don't post screenshots if you can simply copy & paste from the terminal.

---

### Post by tgm4883 on 2011-01-13
> **nickrout said:**
> stop pull up, he possibly does have a mysql server, he just couldn't copy the command that was suggested. (look at the lack of hyphen between mysql and server in the command he typed.


And please don't post screenshots if you can simply copy & paste from the terminal.

Good catch. OP, please try the commands again by copying and pasting the commands into your cmd line

---

### Post by thatguruguy on 2011-01-13
FWIW, on my system (also running 10.10), I'm running mysql-server-5.1 instead of 5.0. He may want to try dpkg-reconfigure mysql-server-5.0.

Also, the minimum recommended backend setup is a machine with 20 gig disk drive. According to the OP, he is trying to run the backend completely off a 4 gig thumbdrive.  Could this be an issue?

---

### Post by torpare on 2011-01-13
> **tgm4883 said:**
> Good catch. OP, please try the commands again by copying and pasting the commands into your cmd line@tgm4883

Here's the result:-

robert@mythbuntu:~$ sudo dpkg-reconfigure mysql-server-5.0
[sudo] password for robert: 
Package `mysql-server-5.0' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.0 is not installed
robert@mythbuntu:~$

> You don't have a SQL server, so that would explain why you are unable to get anywhere. That might have been a nice piece of information for you to tell us earlier, as it would have saved a lot of time. If anything, start out with what options you selected during install.The information that I don't have a

---

### Post by thatguruguy on 2011-01-13
try it with mysql-server-5.1, instead.

---

### Post by torpare on 2011-01-13
#42 contd.
...SQL server has come in response to a command-line.  I didn't have the means to use a terminal until a short time ago...

> If anything, start out with what options you selected during install.I'm sorry to say that I don't recall precisely.  But I don't remember that installing MySQL was offered as one of the (four) optional extras - isn't it supposed to be built-in?

---

### Post by torpare on 2011-01-13
> **thatguruguy said:**
> try it with mysql-server-5.1, instead.Thanks.

I did that:-

robert@mythbuntu:~$ sudo dpkg-reconfigure mysql-server-5.0
[sudo] password for robert: 
Package `mysql-server-5.0' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.0 is not installed
robert@mythbuntu:~$ sudo dpkg-reconfigure mysql-server-5.1
[sudo] password for robert: 
mysql stop/waiting
mysql start/running, process 8169
robert@mythbuntu:~$ sudo dpkg-reconfigure mythtv-database
robert@mythbuntu:~$ sudo dpkg-reconfigure mythtv-common
robert@mythbuntu:~$

The outcome is that I now, at last, have access to the backend GUI.

I'm very sorry about the bad feeling which has been engendered along the way., and for any part I may have (unwittingly) played in giving rise to them.

---

### Post by thatguruguy on 2011-01-13
Good luck with the rest of the set up.

Although I'm still concerned that a 4 gig thumbdrive may not be large enough to run the backend.

---

### Post by torpare on 2011-01-14
@thatguruguy

Thank you for your good wishes.

And yes, I've noted with alarm the second para in your post #41.

It hadn't been my intention to run the backend on a 4GB usb drive in the longer term.  The idea I had had was to test my ability to set up Mythbuntu by - in the first place - using the usb drive as backend and the LiveCD as frontend.  After my previous attempt to set-up MythTV ended in failure (due to my own ineptitude), I wanted to give myself one more chance to get it right, and I hoped - and still do - that Mythbuntu might make it easier for me to do that.

The plan was that if I could crack that, then I could feel confident investing in some new hardware (assuming I can find the cash!).  Conversely, if I couldn't, that'd be throwing money down the drain.

But if the source you quoted is right my experiment was/is doomed to fail anyway.

So as you say it would be interesting to hear others' opinions about that.

---

### Post by torpare on 2011-01-14
PS
"Properties" for my usb drive is currently showing 1.2 GB of free space.

---

### Post by nickrout on 2011-01-14
1.2 G will quickly get used up when TV is about 2.0 G per hour at Std Definition.

---

### Post by torpare on 2011-01-16
> **nickrout said:**
> 1.2 G will quickly get used up when TV is about 2.0 G per hour at Std Definition.@nickrout
Yes, I appreciate that 1.2 GB would be hopelessly inadequate for any serious running of MythTV.  But I was only aiming to set up a temporary "mock-up" of a functioning installation, to prove to myself that I could do it.  For that purpose I probably wouldn't need to record more than a few minutes of actual video - or so I reasoned anyway.

Do you think this sounds reasonable, may I ask?

---

### Post by sami8519 on 2011-01-16
For that you must not use Livetv, because it records whatever you watch automatically. Or if you have a space on one of your hard disks then you can mount that hard disk on your backend partition and direct recordings and livetv into that mount point's path.

Best luck
Sami

---

### Post by nickrout on 2011-01-16
> **torpare said:**
> @nickrout
Yes, I appreciate that 1.2 GB would be hopelessly inadequate for any serious running of MythTV.  But I was only aiming to set up a temporary "mock-up" of a functioning installation, to prove to myself that I could do it.  For that purpose I probably wouldn't need to record more than a few minutes of actual video - or so I reasoned anyway.

Do you think this sounds reasonable, may I ask?

there is no reason it won't work, providing you don't fill the partition it is installed on.

---

### Post by nickrout on 2011-01-16
sorry for the triple post, operator error.

---

### Post by nickrout on 2011-01-16
as above

---

