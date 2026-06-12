---
title: "MythTV - Can't open it?"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by socngill on 2008-01-15
Hi all, hoping you can help me.

I have installed MythTV (or at least i think i have ;) ) but when I go to run it (via Sound and Video - MythTV front end) it opens a screen that wants to check my settings (something to do with database settings, but I have not set one up yet?) - I have no idea what any of this means but it is all prefilled by the machine - which i OK all the way through.  But when I get to the end and click finish.  Nothing happens.  It just takes me back to my Ubuntu desktop.  The same thing happens if I try to run the back end version.  Am I doing something wrong, and if so any ideas what?  Or is this supposed to happen????

I can't seem to find anyway of actually using the software?

Thanks in advance!

If it's any help this is the only machine I have it installed on and am just trying to test it before using it on my media PC and trying to use it as a networked media hub...

---

### Post by rhpot1991 on 2008-01-15
Follow the directions here:
[https://help.ubuntu.com/community/MythTV_Gutsy](https://help.ubuntu.com/community/MythTV_Gutsy)

You need to actually set up everything before you can run it.

---

### Post by socngill on 2008-01-15
Have just found the following:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Which I am trying to get through, but it's just mind boggling.  If only you downloaded the files via Synaptic, installed them and it works lol

First problem I have hit is accessing MySql through @localhost as nothing comes up.  Discovered that all the correct stuff php stuff and Mysql is all installed so skipped that part and moved on.  Next snag was this:

apt-get install linux-source-<kver> linux-headers-`uname -r`

Tried about 15 possible variations of which bit to put where and which < and ' to take out before it finally did something.  Whih it is currently running through  but it said:

bash: 2.6.22-14-generic: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done

and continued to download 45mb of stuff - so I assume it is working despite the "not found" bit?

If this doesn't work i shall try the link you have provided - I just hope it works :lolflag: spent about 2 hours now trying to install this bloody thing!!

---

### Post by rhpot1991 on 2008-01-15
That link you are following is for an older version of Ubuntu, and you are doing a lot of stuff that you no longer need to do.  Just follow the link that I gave you.

---

### Post by socngill on 2008-01-15
> **rhpot1991 said:**
> That link you are following is for an older version of Ubuntu, and you are doing a lot of stuff that you no longer need to do.  Just follow the link that I gave you.

Cheers.  I think I shall give up for tonight and try again tomorrow with your link.  Thanks.

---

### Post by vlaporte on 2008-01-15
Dear Scogngill,
I have tried multiple MythTv install methods (MythDora, MythKnoppix, Ubuntu and add MythTV and finally MythBuntu). I recommend MythBuntu-7.10 as it installs by default all the right software. trying to install all the programs into a regular linux desktop if difficult and the subsequent setup is cryptic. So, just load MythBuntu-7.10 and follow the excellent install guide here - [http://www.mythbuntu.org/documentation/mythbuntu_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_installation.pdf)
You will choose most of the default options.
Navigating through the setup selections is an adventure with old dos - controls: tab, arrow keys, space bar and enter but in no consistent form.
My selections were as follows:
 1. “General” selections
page 75:
TV format: NTSC
VBI format: None
Channel frequency table: us-cable
page 76: defaults
page 77: defaults
page 78: defaults
page 79: defaults
page 80: defaults – and that finishes “General”

2.“Capture cards” - selections
page 82: new capture cards
page 83: Card type: MPEG-2   (I have a Hauppauge PRV150 analogue capture card)
		Device ID: /dev/video0

3.“Video sources” - selections
page 85: Video source name: charter cable (or whatever you want to name it)
		Listings grabber: North America(SchedulesDirect.org)
		User ID: my schedulesdirect username  Password: my password
		Channel frequency table : us-cable

4.“Input connections” - selections
		page 86: [MPEG : /dev/video0] (Tuner 1) > charter cable
		page 87: Video source: charter cable 
				“Scan for channels”
5. “Channel editor” - this can usually be left alone
Luck,
Vince

---

### Post by socngill on 2008-01-16
vlaporte  - Thanks very much. 

I was toying with the idea of installing Mythbuntu but didn't want to lose my current set-up.  The intention, if I can get everything working successfully on this test machine was to install Mythubuntu onto my MediaCentre PC downstairs.  It is currently running XP but I would prefer to use Linux as I don't need all the crap that comes with Windows.  What I might do is run the liveCD version of Mythubuntu on the system to try it out - asuming there is one?  That should tell me if my graphics card (it's ATI - gulp) and Soundcard will work with it before getting rid of my XP set-up.

What I really want to test is the compatibility of MythTV with Nero Home.  They both use upnp software so I am hoping it will be straightforward to use Nero Home on the other PC's to access the TVchannels from the Mythbuntu system, along with all the video photos and music. Don't suppose anybody has tried this?

---

### Post by wolfen69 on 2008-01-16
+1 for Mythbuntu

---

