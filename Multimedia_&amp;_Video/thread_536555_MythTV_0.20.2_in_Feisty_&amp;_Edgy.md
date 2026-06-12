---
title: "MythTV 0.20.2 in Feisty &amp; Edgy"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by superm1 on 2007-08-27
Hi everyone.  As most North American users now know, guide data from Zap2it labs has gone away.  Schedules direct ([www.schedulesdirect.org]("http://ubuntuforums.org/www.schedulesdirect.org")) is out there to replace it, but requires the 0.20.2 release of MythTV.

This release is already in Gutsy, but also has been released to **feisty-updates** and **edgy-updates.**

If your a MythTV user, you can easily (and hopefully painlessly ;)) upgrade to the new packages.  Here's how:

**GUI Method:**
Open up System->Administration->Software Sources. 
Choose the 'Updates' tab.
Make a full checkmark in "Recommended Updates"
Here is what it should look like (although from a gutsy box, should be very similar on feisty or edgy)
[IMG]http://home.eng.iastate.edu/%7Esuperm1/softwaresources.png[/IMG]
Hit close, and let it update your package lists.

Open up update manager or synaptic, and you should see all of your mythtv related items listed as possible updates.

[B]Command Line Method
[/B]
1) Edit /etc/apt/sources.list
Make sure that the feisty-updates or edgy-updates line is **not** commented out.  Also make sure **universe multiverse main restricted **are all listed.
2) Update package lists
```
sudo apt-get update
```
3) Update packages
```
sudo apt-get upgrade
```
4) Open up mythtv-setup
Provide your new source information
5) Run mythfilldatabase

Note: These packages just have updated MythTV / Mythplugins versions. The packaging is not updated to the same packaging in Gutsy.  If you are interested in the same packaging as gutsy, you may want to look at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by lefthand on 2007-08-28
Worked perfectly. I didn't even have to use synaptic, after enabling the Pre-released Updates repository the magic orange icon told me I had updates. I just ran that and mythtv was updated. 

MythWeather is also working now, another pleasant surprise.

---

### Post by m_yates on 2007-08-28
Worked perfectly for me.  I subscribed to schedules direct and was able to get my TV listings downloaded from them.

---

### Post by newlinux on 2007-08-28
Worked for me. It broke my mythweb slightly, however. I had to go modify the .htaccess file with the database password. But it worked fine across all my backends, both feisty and edgy. Seemless transition for my scheduled recordings however. Mythweather (at least through the web) still doesn't work for me. I didn't think to try it on the frontend. Perhaps it needs configuring again. I'll look at it when I get home.

---

### Post by dannyboy79 on 2007-08-28
can some1 please inform me what the url's are for those that would like to try this thru ssh or non-GUI. thank you. is it just enabling the backports repo's? Will that bring anything else that I don't want to bring from the backports or am I barking up the wrong tree and that's not even the repo to enable thru ssh?? Any help would be appreciated.

Also, Newlinux, can you maybe be a little more specific as to how mythweb broke? I use it a lot and would like to be prepared on how to fix it. I currently am not even sure how I enabled security but it's on. When I look in /usr/share/mythtv/mythweb/.htaccess I see a bunch of stuff but the important stuff from what I remember is commented out, see below:
#AuthType Digest
#AuthName "MythTV"
#AuthUserFile /etc/apache2/httpd-passwords
#Require valid-user
#BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
#Allow from 192.168.1.
#Satisfy any


So i must be using another method. I remember I had a lot of problems enabling security for mythweb but ended up getting it working just don't remember how. I think I am using  the method toward the bottom of this guide but obviously the paths that they use (/etc/httpd/conf/httpd-passwords) would be different for ubuntu. DAMN IT, I just lost my ssh connection so I can't check. I hate this when this happens. My internet will go down due to torrenting (i think) and then the only way to get it working again is to unplug the modem and router, and then plug in modem first, wait a second, then plug in router. You guys have a possible solution for this?

---

### Post by newlinux on 2007-08-28
> **dannyboy79 said:**
> can some1 please inform me what the url's are for those that would like to try this thru ssh or non-GUI. thank you. is it just enabling the backports repo's? Will that bring anything else that I don't want to bring from the backports or am I barking up the wrong tree and that's not even the repo to enable thru ssh?? Any help would be appreciated.


It's the proposed (pre-release) repo, not the backports repo. I think there are a couple of other things in there that if you do a standard update will come through. I don't remember any of them looking like major things, but I did not install them. I'm not at home (and have ssh blocked through my firewall - someone kept trying to break in) so I can't explicitely check the URL...

---

### Post by newlinux on 2007-08-28
I think it is just the standard repo url ([http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) I think) with feisty-proposed, or edgy-proposed as the repo (and it would be in the multiverse).

---

### Post by dannyboy79 on 2007-08-28
well whenever you can confirm I would appreciate it. Also, you didn't comment on the mythweb access issue. can you make any comments?

---

### Post by superm1 on 2007-08-28
Yes standard repo line just with feisty-proposed or edgy-proposed rather than.  So something like this:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main multiverse universe restricted

As for mythweb htaccess, this has been changed entirely in Gutsy.  I didn't backport the code to prevent risk of further regression.  So the situation with setting a htaccess password should have been the same as before this SRU.

---

### Post by newlinux on 2007-08-28
> **dannyboy79 said:**
> well whenever you can confirm I would appreciate it. Also, you didn't comment on the mythweb access issue. can you make any comments?

Sorry. Somehow I completely missed your post about mythweb. For some reason my .htaccess file (located at /usr/share/mythtv/mythweb/ I think) was softlinked to a file that no longer existed after the update (this is on edgy). I don't remember softlinking it at all, but it has been a while. So I basically did not have a .htaccess file. In that direct was the generic .htaccess.dist file, which I copied over as .htaccess and changed the database access password from "mythtv" to what I have my database password set as. That was it. It didn't affect my apache password protection, which is set somewhere else. It only affected mythweb's access to the mythconverg database. If you are at all worried about this, just backup your .htaccess file somewhere safe.


I do have to wonder why you want to do this over a flaky ssh connection. sounds kind of problematic to me. Also, if you aren't forwarding X, you won't be able to go into mythtv-setup and modify the video sources to use schedules direct.

---

### Post by dannyboy79 on 2007-08-28
I merely want to add the sources, update, then upgrade mythtv. then I'll start a x11vnc --usepw if I really want to do all that from work. so that I can mythtv-setup but like I said I'll most likely wait to do that at home. I do many little tasks over ssh which don't require a  gui. x11vnc will get me into my current logged in session and I have plenty of times messed with mythtv-setup thru x11nvc and it's tolerable but today I am swamped at work so I need to actually work. he he he. anyway, I can't get into my box anymore as I stated that my internet goes down for whatever reason (maybe due to to many people connecting to me for torrenting?) and then the only to fix is to unplug router, then modem, and plug it in the opposite way. ANy thoughts on why my connection stops working? I have thought about time warner cable possible having come kind of filter that shuts the connection off if so many other's (people in the swarm both seeders and leechers) are connected to me but that's highly unlikely and maybe it's just do my crappy NetGear Router? The weird thing is that it hardly used to happen until my roommate moved in and he torrents as well as me. Our clients allow us to limit the upload and download max settings as well as the amont of open connections but I don't think anything is closing the connections that were opened but then people disconnected and maybe that's why it goes down???? Can you comment. Sorry off topic just curious?

---

### Post by newlinux on 2007-08-28
I've had that problem before, actually (and it was caused by torrents). After a while of downloading torrents I would have reboot the router.There was some setting in my router that stopped that (I use a linksys wrt54G with dd-wrt firmware). I'll look around at it when I get a chance at home. I do remember I found the answer searching the Internet. hopefully the netgear will have a similar setting. It seems as if your clients are managing the connections all should be well, however...

I tried forwarding X to work a while back, but it was just too slow. I need more upstream bandwidth. I used to do little things as well over terminal, but as I mentioned, someone kept trying to login and I thought I'd close the port... :-(

---

### Post by newlinux on 2007-08-28
which torrent client do you use? Maybe try changing clients as well. I use ktorrent. Used to use Azureus, but that caused problems, one of which might have been the router problem.

---

### Post by dannyboy79 on 2007-08-28
bittornado all the way. I use it on windows as well. If you use denyhosts program and use public/private key pair for your authentification to your ssh server no one will get in. it's the only port I have open on my router besides the bittorrent ports of course. Then I forward my mythweb thru a putty tunnel, my x11vnc thru a putty tunnel, I even use a dynamic putty tunnel for IM. then you just set PIDGIN to SOCKS5 proxy 127.0.0.1 and instead of not being able to use IM thru work because of firewalls, I can use it!! HA HA HA 

So, needless to say, I love SSH and use it for everything!!!

---

### Post by newlinux on 2007-08-28
> **dannyboy79 said:**
> bittornado all the way. I use it on windows as well. If you use denyhosts program and use public/private key pair for your authentification to your ssh server no one will get in. it's the only port I have open on my router besides the bittorrent ports of course. Then I forward my mythweb thru a putty tunnel, my x11vnc thru a putty tunnel, I even use a dynamic putty tunnel for IM. then you just set PIDGIN to SOCKS5 proxy 127.0.0.1 and instead of not being able to use IM thru work because of firewalls, I can use it!! HA HA HA 

So, needless to say, I love SSH and use it for everything!!!


I know we are way off topic here... but I have no idea about setting up denyhosts programs and using a public/private key pair. But at least I know what they are. I look into it. Any pointers are great.

I'm curious about your upstream bandwidth at your home internet connection. how fast is it? When I did forward X through ssh to windows (using putty and Xming) X apps were really slow (I tried this because I wanted to do exactly what you are... do some things at work that are blocked - just during lunch breaks :) ). However doing the same thing on my LAN is fine, so I chalked it up to speed problems.

---

### Post by dannyboy79 on 2007-08-28
> **newlinux said:**
> I know we are way off topic here... but I have no idea about setting up denyhosts programs and using a public/private key pair. But at least I know what they are. I look into it. Any pointers are great.

I'm curious about your upstream bandwidth at your home internet connection. how fast is it? When I did forward X through ssh to windows (using putty and Xming) X apps were really slow (I tried this because I wanted to do exactly what you are... do some things at work that are blocked - just during lunch breaks :) ). However doing the same thing on my LAN is fine, so I chalked it up to speed problems.

sorry off topic, this is taking it away to another thread, please respond here:
[http://ubuntuforums.org/private.php?do=showpm&pmid=300335](http://ubuntuforums.org/private.php?do=showpm&pmid=300335)

---

### Post by newlinux on 2007-08-28
> **dannyboy79 said:**
> sorry off topic, this is taking it away to another thread, please respond here:
[http://ubuntuforums.org/private.php?do=showpm&pmid=300335](http://ubuntuforums.org/private.php?do=showpm&pmid=300335)

That forum link appears to be broken... or for some reason isn't working for me but I think I found your post anyway...

---

### Post by Crashmaxx on 2007-08-28
Working great for me. But it removed my XM radio hack. I guess that's to be expected though.

The Schedules Direct interface is great. And I think it might even do mythfilldatabase faster now. Assuming all still looks good in a couple days, I pay for the first 3 months ASAP.

---

### Post by wfaris on 2007-08-28
feisty proposed worked like a charm for me.  So far so good.   Whats this I hear about schedule direct lowering their price if enough people sign up?

---

### Post by newlinux on 2007-08-28
I believe their goal is $20 a year. During the first 3 months they are trying to gauge demand.

---

### Post by dannyboy79 on 2007-08-28
all good here running feisty. am curious about these other updates that I am guessing are from the proposed repo as well? is it safe to allow these? i don't like having to fix things as I am sure others don't either.
the only problem with mythweb was that the username within this file /usr/share/mythtv/mythweb/.htaccess somehow was changed to nothing, so I just made this:
        setenv db_server        "127.0.0.1"
        setenv db_name          "mythconverg"
        setenv db_login         ""
        setenv db_password      "HAHATHISISNOTMYPASSWORD"

look like this:
        setenv db_server        "127.0.0.1"
        setenv db_name          "mythconverg"
        setenv db_login         "mythtv"
        setenv db_password      "HAHATHISISNOTMYPASSWORD"


[[IMG]http://img337.imageshack.us/img337/2130/upgradesfromproposedie6.th.png[/IMG]](http://img337.imageshack.us/my.php?image=upgradesfromproposedie6.png)

---

### Post by dannyboy79 on 2007-08-28
i am sorry I have to ask this is here but I am curious about what to do for a problem I am experiencing. My hard drive was dieing and luckily smartmontools informed me before it was too late and I lost all my DVR recordings. anyway, I transferred everything to a new 400gb using grsync. all the permissions were left alone and owners stayed the same and all is good. HOWEVER, there were a few recordings that failed i/o during the grsync, I even tried to use cp but to no avail, just couldn't read them off the bad disk. myquestion is, How do I update the database so that those recordings no longer show up in mythtv or mythweb? is there some kind of mythconverg update I can run based on file location and whetther they are there or not? Also, I noticed that some .png thumbnails have been left behind. Now I can't say whether they are from recordings that I deleted thru xbmcmythtv or thru mythweb but I am guessing it's from one of those frontends. how can I right a script to look thru my recordings directory and if it finds any .png that don't have a matching .mpg named the same, the script should delete it. Anyone good at python or bash or perl? Maybe I should learn this myself. Can anyone point me to a good tutorial for learning programming in any of these langauages?

thanks.

(PS GREAT WORK ON GETTING 20.02 TO US FAST MARIO!! YOU ARE THE MAN!)

---

### Post by barney_1 on 2007-08-28
Thanks for this, I was able to get the packages installed (proposed) and set up my new source with Schedules Direct.

What I can't do is get it to "Fetch Channels From Listing Source".  I am able to scan channels and then get it to run mythfilldatabase.  I have the program guide but instead of having stations titles like ABC, NBC, FOX, etc.  it just says "Adding Channel" where that should be.

Am I doing something wrong?

Thanks!

---

### Post by barney_1 on 2007-08-28
Ok, I was able to fetch my Channel Lineup with the following steps:

1. Setup the schedules direct information as a source
2. Associate your input connection with Schdules direct - at this point the "fetch channels from listing source" was ineffective for me.  DO NOT scan for channels.
3. Exit out of the setup program and when asked to run "mythfilldatabase" please do so.
4. After running mythfilldatabase start the backend setup program again and go to "input connections".  Clicking the "Fetch Channels from Listing Source" should now work.

Is this a bug?  If so, please tell me what to do as I have not filed a bug report before.  Thanks!

---

### Post by PilotJLR on 2007-08-28
Thank you! Works well - I posted comments to launchpad.

---

### Post by NT4usB on 2007-08-28
no joy updating the slave be/fe.
posting to the buglist.
ed:
#135433
I fixed it. libmyth-0.20 didn't install/upgrade when I updated. Added it and now it works.

---

### Post by racmar on 2007-08-29
I just wanted to chime in to also offer my thanks. 

I just did my upgrade to 20.2 and it was almost perfect.  I have a Feisty myth setup, and used this procedure as a guide.  

My actual procedure was:
```

sudo sh -c 'echo "deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install -t feisty-proposed mythtv mythweather mythweb
sudo mythtv-setup
sudo mythfilldatabase --replace-all

``` 

For "mythtv-setup":
I deleted all my "video sources" and then added my info for schedules direct.  Last, I updated all my "input connections" to point to the schedulesdirect video source.

I used ssh X forwarding from my laptop ( ssh -X username@mythtvbox ), and I had to temporarily disable Beryl for "mythtv-setup" to work properly.

Anyway, thanks for the quick response to an otherwise stressful situation.  My finance would have probably called off the wedding if she had to go back to *regular* TV.  ( haha ).

THANKS

---

### Post by dannyboy79 on 2007-08-29
> **racmar said:**
> I just wanted to chime in to also offer my thanks. 

I just did my upgrade to 20.2 and it was almost perfect.  I have a Feisty myth setup, and used this procedure as a guide.  

My actual procedure was:
```

sudo sh -c 'echo "deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install -t feisty-proposed mythtv mythweather mythweb
sudo mythtv-setup
sudo mythfilldatabase --replace-all

``` 

For "mythtv-setup":
I deleted all my "video sources" and then added my info for schedules direct.  Last, I updated all my "input connections" to point to the schedulesdirect video source.

I used ssh X forwarding from my laptop ( ssh -X username@mythtvbox ), and I had to temporarily disable Beryl for "mythtv-setup" to work properly.

Anyway, thanks for the quick response to an otherwise stressful situation.  My finance would have probably called off the wedding if she had to go back to *regular* TV.  ( haha ).

THANKS

fyi for other users, don't remove your source. you merely rename the zap2it one to something else and change your username and password. this way you don't have to redo the input part of mythtv-setup.

---

### Post by dmfrey on 2007-08-29
My MythTV Backend appeard to update correctly, however, I too experienced issues with MythWeb.  I could see my Listings, Recording Schedules, and Recorded Programs.  I could not access my settings or any Upcoming Recordings.  I tried to schedule recordings through MythWeb.  They appeared to schedule the recording, but the program never recorded.  I was tailing the myth logs and it never attempted to record the programs.  I haven't had a chance to look into the problem as of yet, but will try to get to it tonight.

Any suggestions would be greatly appreciated.

---

### Post by djseto on 2007-08-29
I'm getting an error in the mythbackend.log that says this version of MythTV was not compiled for DVB support and that I have to recompile. Is there are another version somewhere that has this?

---

### Post by superm1 on 2007-08-29
> **djseto said:**
> I'm getting an error in the mythbackend.log that says this version of MythTV was not compiled for DVB support and that I have to recompile. Is there are another version somewhere that has this?
They are built with DVB support.  Is this edgy or feisty?

---

### Post by hackmeister on 2007-08-29
I did the upgrade and everything seems to be o.k.. I had to pass the --refresh-all flag for mythfilldatabase to populate the listings for the first time. Mythweather is working now in the frontend but does not work via Mythweb.

---

### Post by dannyboy79 on 2007-08-29
can anyone answer my posts #21 and #22. the questions regard the upgrades that I am guessing are from proposed repo. then the issue with my mythweb previous recordings that I had to delete from a dieing hard drive but the pointers must be in the mythdatabase.

---

### Post by djseto on 2007-08-29
> **superm1 said:**
> They are built with DVB support.  Is this edgy or feisty?


This is on Edgy. I used Synaptics to reinstall whatever the lastest version was before 0.20.2 (0.20.1?) and everything went back to working fine. I have two PC-HDTV 5000 cards...do I need to recompile the drivers again if i do an install over 0.20.1? I tried that and it didnt work. I kept seeing that error in the mythbackend log and I kept getting Tuner not available in the System status from with in MythFrontend

---

### Post by dmfrey on 2007-08-29
As it turns out, my issue with not being able to record anything after the upgrade is not isolated to me.  There appears to be a bug in the MythTV code that is preventing channel lineups from being downloaded when connected to an input source over firewire.  More can be read about it [[COLOR="Red"]here[/COLOR]]("http://www.gossamer-threads.com/lists/mythtv/users/285693").  There is a workaround listed as well, but I have yet to get it to work.

---

### Post by newlinux on 2007-08-29
I didn't read the details of the bug, but I have a firewire attached to an video source and everything is okay. But then, I didn't delete my video sources, or change any channels. I just changed the grabber to schedules direct.

---

### Post by flyingcircus on 2007-08-30
The upgrade to 0.20.2 worked fine on Edgy for me. However, I had a problem with the .htaccess file  for mythweb. I was getting a 403 forbidden error when I tried to access mythweb. I finally, found the problem to be a broken symlink.
     For some reason the symlink /var/www/mythweb/.htaccess  was pointing to /etc/mythtv/mythweb-htaccess . However /etc/mythtv/mythweb-htaccess doesn't exist, it needs to point to /etc/mythtv/mythweb-htaccess.conf   As soon as I changed that, the 403 error went away and all is back to normal.

---

### Post by newlinux on 2007-08-30
> **flyingcircus said:**
> The upgrade to 0.20.2 worked fine on Edgy for me. However, I had a problem with the .htaccess file  for mythweb. I was getting a 403 forbidden error when I tried to access mythweb. I finally, found the problem to be a broken symlink.
     For some reason the symlink /var/www/mythweb/.htaccess  was pointing to /etc/mythtv/mythweb-htaccess . However /etc/mythtv/mythweb-htaccess doesn't exist, it needs to point to /etc/mythtv/mythweb-htaccess.conf   As soon as I changed that, the 403 error went away and all is back to normal.

That is exactly what happened to me, although I fixed it by just creating a new .htaccess (on edgy as well).

---

### Post by jjohns63 on 2007-08-30
Seems to be working now, but I had some initial trouble when I decided to just use a command line apt-get upgrade instead of synaptic. But after getting everything set up again and then using synaptic I got it all working. Used mythfilldatabase --refresh-all to completely refresh the guide data.

Thanks a lot for the guide


Edit:
I am using feisty btw

---

### Post by Dertiger on 2007-08-30
I tried updating to .20.2, but had some problems.  Edgy-backports reports a SVN version that is newer than .20.2.  When I upgraded to it and run mythfrontend --version (or backend) it reports I have version 0.20.20060828-3.  I removed the edgy-backport repository and removed then installed version .20.2.  After installation, Synaptic reports I have 20.2 but when I check --version, it still reports 0.20.20060828-3.  What do I need to do to get the "real" .20.2?  I currently can't setupScheduledDirect with my installed version of mythtv.

Thanks

---

### Post by dannyboy79 on 2007-08-30
> **Dertiger said:**
> I tried updating to .20.2, but had some problems.  Edgy-backports reports a SVN version that is newer than .20.2.  When I upgraded to it and run mythfrontend --version (or backend) it reports I have version 0.20.20060828-3.  I removed the edgy-backport repository and removed then installed version .20.2.  After installation, Synaptic reports I have 20.2 but when I check --version, it still reports 0.20.20060828-3.  What do I need to do to get the "real" .20.2?  I currently can't setupScheduledDirect with my installed version of mythtv.

Thanks
well it appears that you may have used the backports repo instead of what the guide states, Mario has put the new 20.02 version's in the "proposed" repo. Don't delete your source for zap2it, just edit the name, enter your new username (sd email) and password and when you exit mythtv-backend, mythfilldatabase will update and you'll be done. I have a question I am awaiting anyone's response however related to other packages that I beleeive are from the proposed repo and whehter it's safe to let them update/upgrade. Other than that, it should be seemless unless you use mythweb, a few users have reported how to fix above. Good luck

---

### Post by djseto on 2007-08-30
I just used Synaptics to upgrade to 0.20.2 from the proposed internet updates after reinstalling 0.20.1 and I am seeing three problems:

1. I used Synaptics to upgrade my plugins as well and none of them show up in the MythTV Frontend Menu

2. When I go to watch TV, it says my tuners are unavailable. When I look into the mythbackend.log, I see the following:
2007-08-30 07:41:41.623 MainServer::HandleAnnounce Monitor
2007-08-30 07:41:41.632 adding: MythTV as a client (events: 0)
2007-08-30 07:41:41.633 MainServer::HandleAnnounce Monitor
2007-08-30 07:41:41.634 adding: MythTV as a client (events: 1)
2007-08-30 07:41:41.635 Reschedule requested for id -1.
2007-08-30 07:41:41.777 Scheduled 15 items in 0.1 = 0.12 match + 0.02 place
2007-08-30 15:40:46.224 MainServer::HandleAnnounce Monitor
2007-08-30 15:40:46.226 adding: MythTV as a client (events: 0)
2007-08-30 15:40:46.227 MainServer::HandleAnnounce Monitor
2007-08-30 15:40:46.228 adding: MythTV as a client (events: 1)
2007-08-30 15:42:38.807 MainServer::HandleAnnounce Monitor
2007-08-30 15:42:38.815 adding: MythTV as a client (events: 0)
2007-08-30 15:42:38.816 MainServer::HandleAnnounce Monitor
2007-08-30 15:42:38.816 adding: MythTV as a client (events: 1)
2007-08-30 15:47:27.105 Using runtime prefix = /usr/local
2007-08-30 15:47:27.208 New DB connection, total: 1
2007-08-30 15:47:27.238 Connected to database 'mythconverg' at host: localhost
2007-08-30 15:47:27.256 Current Schema Version: 1160
Starting up as the master server.
2007-08-30 15:47:27.357 New DB connection, total: 2
2007-08-30 15:47:27.366 Connected to database 'mythconverg' at host: localhost
2007-08-30 15:47:27.377 EITHelper: localtime offset -4:00:00
2007-08-30 15:47:27.398 TVRec(1) Error: DVB card configured on video device 0,
but MythTV was not compiled with DVB support.

Recompile MythTV with DVB support or remove the card
from the configuration and restart MythTV.
2007-08-30 15:47:27.410 EITHelper: localtime offset -4:00:00
2007-08-30 15:47:27.413 TVRec(3) Error: DVB card configured on video device 1,
but MythTV was not compiled with DVB support. 

3. My ALSA audio stops working. 

Can someone please please help me fix this. I need this upgrade to work with Schedules Direct! I can't figure out why I am having a problem with  what should be a seemless upgrade. I already tried recompiling and installing the drivers for my 2 PCHDTV 5500 cards.

---

### Post by djseto on 2007-08-30
For the record, I'm a huge moron. I fixed my problem. I had the use Backport option selected in my Software sources so it was upgrading the wrong version of 0.20.2. My only problem now is that the analog audio on my PCHDTV-5500 card is nothing but static crap. Everything else seems to work now!

---

### Post by djseto on 2007-08-30
I did a "mythbackend --version" and I got the following version number: "0.20.20060828-3". When I go into MythTV-setup, it does not list Schedules Direct as a grabber option. I did a complete removal and reinstall of Mythtv-frontend, backend,database, and all the associated packages. What am I missing here? I am so close I can taste it...

---

### Post by Crashmaxx on 2007-08-30
> **djseto said:**
> I did a "mythbackend --version" and I got the following version number: "0.20.20060828-3". When I go into MythTV-setup, it does not list Schedules Direct as a grabber option. I did a complete removal and reinstall of Mythtv-frontend, backend,database, and all the associated packages. What am I missing here? I am so close I can taste it...

0.20.20060828-3 is NOT 20.2, its 20.0 released on 8-28-2006. You want 20.20070821-1 which is 20.2 and was built on 8-21-2007. For some reason the build date is part of the version info.

Anyway, no need to reinstall in the first place, and it is 20.2 is NOT in the Backports repos. Please see the first post of the thread here. You are looking for the Pre-release repos. Then just do an upgrade with update manager and select the myth packages and libmyth, or just do an update and upgrade with apt (which will also upgrade any other packages you have that are in Pre-release, may not be the best idea).

Hope that helps.

---

### Post by djseto on 2007-08-30
OK. I FINALLY got version 0.20.20070821-1 installed and I guarantee that DVB was NOT compiled with this version. It is not an option in mythtv-setup AND it says its needed to be compiled with DVB support in the mythbackend.log. This renders my mythv worthless as DVB is a must to get PCHDTV-5500 cards working right. Now what? Ahhhhhhhhh (frustration)

---

### Post by newlinux on 2007-08-30
> **djseto said:**
> OK. I FINALLY got version 0.20.20070821-1 installed and I guarantee that DVB was NOT compiled with this version. It is not an option in mythtv-setup AND it says its needed to be compiled with DVB support in the mythbackend.log. This renders my mythv worthless as DVB is a must to get PCHDTV-5500 cards working right. Now what? Ahhhhhhhhh (frustration)

I have 5 cards that require DVB support that are working fine with this version. Are you sure this isn't related to your other post where you tried to compile it on your own? Maybe you didn't completely get rid of the version you compiled.

---

### Post by djseto on 2007-08-30
How would I get rid of previously compiled and installed versions that werent installed via Synaptics? Right now, Synaptics shows none of the MythTV products installed since I just uninstalled MythTV again. So you are saying that when you go into Mythtv-setup you see an option for DVB when you add a new capture card?

---

### Post by newlinux on 2007-08-30
> **djseto said:**
> How would I get rid of previously compiled and installed versions that werent installed via Synaptics? Right now, Synaptics shows none of the MythTV products installed since I just uninstalled MythTV again. So you are saying that when you go into Mythtv-setup you see an option for DVB when you add a new capture card?


You'd have to undo whatever you did to install it. The only way I'd know for sure is to look and see where the make file places files. According to your post, you only deleted the untarred directory structure. Without looking at the compile instructions, I doubt that gets rid of everything. When you install it it probably places files in other places. Did you compile the plugins too? Do you now see the  plugins when you run mythfrontend? 

I'm saying I have five cards set up as DVB cards and I have tested all of them so I know DVB configuration is working. But let me check... yes, I can run mythtv-setup and see a DVB card option when added a new capture card?

---

### Post by djseto on 2007-08-30
Well this sucks. Is there some type of uninstall command that runs against the make file to remove everything? I cant imagine there isnt some command line type uninstall?

---

### Post by newlinux on 2007-08-30
there might be a make uninstall. That isn't uncommon.

---

### Post by newlinux on 2007-08-30
If there is a make uninstall, you might want to do that -- then reinstall the ubuntu packages. If I have any time I'll take a look at the instructions for compiling it to see how to undo. Not likely with my 3 month old right now... :)

---

### Post by djseto on 2007-08-31
SUCCESS! I had to download the MythTV code from mythtv.com, recompile it, make install, make uninstall, and then I installed 0.20.2 from Synaptics and restored my database. It all works now. This took way longer than it should, but I definitely worked the rust off whatever linux skills i learned 3 months ago when I first set this up. Thanks for everyones help and patience.

---

### Post by newlinux on 2007-08-31
I am glad you got it working! From now on, have some patience with the ubuntu packages :). Superm1 does a great job at getting us what we need.

Look at it this way, now you are an expert at installing and configuring it. I had to redo it a few times when I first set it up, and it certainly made me know more (and afraid to ever really mess it up).

happy Mything!

---

### Post by dannyboy79 on 2007-08-31
n anyone answer my posts #21 and #22. the questions regard the upgrades that I am guessing are from proposed repo. then the issue with my mythweb previous recordings that I had to delete from a dieing hard drive but the pointers must be in the mythdatabase.

---

### Post by newlinux on 2007-08-31
> **dannyboy79 said:**
> n anyone answer my posts #21 and #22. the questions regard the upgrades that I am guessing are from proposed repo. then the issue with my mythweb previous recordings that I had to delete from a dieing hard drive but the pointers must be in the mythdatabase.

I didn't install the proposed updates other than Myth, so I don't know what shape they are in. I actually disabled the proposed repo after installing myth. I see no need to install proposed updates unless there is something in them I need or want now. When they are approved they'll be available in the other repos.

With regards to the recordings, are you getting an error when you try and delete them from mythfrontend or mythweb? I'm not sure if I understand your problem properly.

In what may be a similar situation, I had a corruption problem and the frontend still showed the recording and wouldn't let me delete it because the file didn't exist, even though the recording wasn't there anymore. I just ended up creating and empty file for it to delete  (using touch) and that worked... I found out the file name by looking up the error myth was having deleting the file in the logs...

---

### Post by afljafa on 2007-09-01
Well - I have a frontend only edgy install. I get 

"mythfrontend: error while loading shared libraries: libmythtv-0.20.2.so.0"

errors when starting the frontend. libmythtv-0.20.so.0 exists under /usr/lib however libmythtv-0.20.2.so.0 doesn`t.

---

### Post by newlinux on 2007-09-01
install libmythtv-0.20 from the proposed repo. It is version 0.20.2

---

### Post by NT4usB on 2007-09-01
I see you have "Unsupported" checked also. Is this necessary in order to install Myth?
ed: maybe that's why some of us had issues with that library not installing?

---

### Post by NT4usB on 2007-09-01
... Day 2 of trying to get Myth proposed working.
I flatlined my Dapper master backend/frontend and did a fresh install of 7.04. Dapper was pretty kluged in order to make 0.20 run on it so I figured upgrading would be a mess.
The first day issues are vague as I went about fixing one non-functioning thing to another. permissions issues with mysql, existing recordings, etc. *Note to the developers: phpmyadmin should really be included in the package. It makes working with mysql much easier*

At one point, my keyboard stopped working... after I broke it in half over my knee. Got a spare out of the closet (big ol' Logitech multimedia one, not gonna break so easy) and continued sorting...
I intended to keep usernames, IP addresses, etc., the same as they were in Dapper to lessen the complications with my slaves. I already updated to the proposed on the slave and it worked well.

After installing Myth, I restored my entire mysql DB backup, fixed the paths to recordings, etc.
All recordings show up and will play. Upgrading did not fix my HD playback problem however.
Live TV works for all cards and I can record live TV. All my existing scheduled recordings are failing so I have to figure out what's up with that. I **don't** want to have to go back and reschedule everything.
Still sorting out lirc and getting the remote working. Install didn't work and nothing in the HowTo's solved it so I went back to Hyams page. irw works now so all we have to do is get it to see the lircd.conf.

ed: how fupped duck is that? I read the fine print on the wikki and see that my remote is supported by the kernel and I didn't have to install anything. Now that I've jacked with lirc I have to figure how to undo all that and get back to kernel support. Isn't Linux fun..? not!
That'll teach me to upgrade.
Repeat after me...
** If it works, don't break it!**
** If it works, don't break it!**
** If it works, don't break it!**

---

### Post by afljafa on 2007-09-01
> **newlinux said:**
> install libmythtv-0.20 from the proposed repo. It is version 0.20.2

Ok - That worked.

For others - the correct name is libmyth-0.20

---

### Post by florin on 2007-09-02
Testing the update on Feisty with a HDHomeRun tuner.

Step #7 "Return to Connect source to input page" fails - I can't choose the Starting Channel field. It looks like there's a problem with the previous step "Scan for channels page"

[https://help.ubuntu.com/community/HDHomeRun]("https://help.ubuntu.com/community/HDHomeRun")

Here's the output:

```
florin@rivendell:~$ mythtv-setup
Stopping MythTV server: mythbackend .
2007-09-02 16:33:48.340 Using runtime prefix = /usr
2007-09-02 16:33:48.355 Gnome-Screensaver support enabled
2007-09-02 16:33:48.357 DPMS is active.
2007-09-02 16:33:48.378 New DB connection, total: 1
2007-09-02 16:33:48.386 Connected to database 'mythconverg' at host: localhost
2007-09-02 16:33:48.387 Total desktop dim: 1152x864, with 1 screen[s].
2007-09-02 16:33:48.391 Using screen 0, 1152x864 at 0,0
2007-09-02 16:33:48.407 Current Schema Version: 1160
2007-09-02 16:33:48.427 Total desktop dim: 1152x864, with 1 screen[s].
2007-09-02 16:33:48.429 Using screen 0, 1152x864 at 0,0
2007-09-02 16:33:48.430 Switching to square mode (MythCenter)
2007-09-02 16:33:48.457 Using the OpenGL painter
2007-09-02 16:33:48.881 Joystick disabled.
2007-09-02 16:33:49.003 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-09-02 16:33:49.306 Using NV NPOT texture extension
2007-09-02 16:36:02.742 DiSEqCDevTree, Warning: No device tree for cardid 0
2007-09-02 16:38:01.761 New DB connection, total: 2
2007-09-02 16:38:01.762 Connected to database 'mythconverg' at host: localhost
2007-09-02 16:38:26.992 DiSEqCDevTree, Warning: No device tree for cardid 0
2007-09-02 16:39:19.511 Failed to run tv_find_grabbers
2007-09-02 16:40:09.000 New DB connection, total: 3
2007-09-02 16:40:09.001 Connected to database 'mythconverg' at host: localhost
2007-09-02 16:40:09.004 New DB connection, total: 4
2007-09-02 16:40:09.005 Connected to database 'mythconverg' at host: localhost
2007-09-02 16:40:09.012 New DB connection, total: 5
2007-09-02 16:40:09.012 Connected to database 'mythconverg' at host: localhost
2007-09-02 16:41:32.935 HDHRChan(1010734f/0): device found at address 192.168.100.197
2007-09-02 16:48:22.502 Failed to run tv_find_grabbers
2007-09-02 16:48:59.539 Skipping channel fetch, you need to scan for channels first.
2007-09-02 16:50:10.087 HDHRChan(1010734f/0): device found at address 192.168.100.197
2007-09-02 16:56:13.466 Failed to run tv_find_grabbers
2007-09-02 16:57:59.898 Skipping channel fetch, you need to scan for channels first.
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.

```

I know for a fact that I do get HD content on this cable, I am able to view HD channels with VLC and the hdhomerun_config utility.

If you want me to test something, please let me know.

---

### Post by Slim Backwater on 2007-09-02
I had a slight problem with the upgrade on my headless backend.  I had originally used the 7.04 Server CD and I kept getting "updates held back:" when doing an apt-get upgrade.

```

root@gateway:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythtv-backend mythtv-backend-master mythtv-common mythtv-database
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Eventually I figured out apt-get install mythtv-backend and got somewhere:
```

root@gateway:~# apt-get install mythtv-backend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbus-1-utils launchpad-integration liblaunchpad-integration0 libvte-common libvte9 mythtv-backend-master mythtv-common mythtv-database python-dbus
  python-gconf python-pyorbit python-vte synaptic update-manager update-notifier
Suggested packages:
  mythtv-frontend mythweb python-dbus-dbg python-gconf-dbg python-pyorbit-dbg python-vte-dbg dwww
Recommended packages:
  xmltv-util mythtv-doc deborphan libgnome2-perl apport-gtk
The following NEW packages will be installed:
  dbus-1-utils launchpad-integration liblaunchpad-integration0 libvte-common libvte9 python-dbus python-gconf python-pyorbit python-vte synaptic
  update-manager update-notifier
The following packages will be upgraded:
  mythtv-backend mythtv-backend-master mythtv-common mythtv-database
4 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.0MB of archives.
After unpacking 13.3MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Everything seems to be ok, but I think that the proposed packages have significantly different dependencies than the originals. and thought maybe you'd like to know about this.

._.

---

### Post by Eibwen on 2007-09-03
I have seen a number of posts complaining about the no sound issue.  Has anyone have a good explaination why it is failing to play sound after the upgrade to 0.20.2?

I have a Haup. 250, 350 cards.

Thanks,

Eibwen

---

### Post by dannyboy79 on 2007-09-04
it's not related to your haup cards because I have a pvr-350 and all is fine. it's possible that something else was updated from the proposed repo and has overwritten a config file that you have changed to get sound working??? Is that possible? Did you have to mess around to get sound working? What sound card do you have? This is really not a question to be answered for this thread as it's off topic but just trying to help you recall possibly why your sound isn't working.

---

### Post by newlinux on 2007-09-04
I have a pvr-150 and it's not having any problems after the update (on edgy).

---

### Post by jmcgee on 2007-09-04
Ok I have managed to hose my MythTV.  I am running Dapper, enabled the 
[http://ppa.dogfood.launchpad.net/mythbuntu/ubuntu](http://ppa.dogfood.launchpad.net/mythbuntu/ubuntu) 
repository which was probably a mistake.  Reloaded synaptic, marked what the 20.2 myth stuff and it appears to be gone.

#1) are there 20.2 packages for Dapper?  If so where?
#2) if not, does that mean I have to upgrade to Feisty?

---

### Post by NT4usB on 2007-09-04
> **jmcgee said:**
> Ok I have managed to hose my MythTV.  I am running Dapper, enabled the 
[http://ppa.dogfood.launchpad.net/mythbuntu/ubuntu](http://ppa.dogfood.launchpad.net/mythbuntu/ubuntu) 
repository which was probably a mistake.  Reloaded synaptic, marked what the 20.2 myth stuff and it appears to be gone.

#1) are there 20.2 packages for Dapper?  If so where?
#2) if not, does that mean I have to upgrade to Feisty?

You could probably roll your own and get it going on Dapper. I had 0.20 running on Dapper. Dapper didn't like it but MythTV ran fine.

Others will undoubtedly say different but I just spent the weekend getting 20.2 going on Feisty and if I had to do it over again, I'd go with Edgy.
I ran Dapper for a year with an Edgy slave and they were very reliable.
Feisty has already shown me some things that aren't promising.
The nic stopped working. ifdown and ifup I could see it turn off and back on but no connection. A restart got it back.
(Probably a setting I haven't discovered yet, butt...) When Mythplayback is paused, the screen goes black after a while. If the Mythmenu is up, it never goes black. If the frontend is closed, it goes black after a while and doesn't wake up via ssh or if I launch the frontend via vnc. Have to plug in a mouse to get it back. I've already turned off powersave and screensaver...

---

### Post by bla2000 on 2007-09-04
Following the instructions in the 1st post my upgrade worked perfectly.  Thanks.

btw, I'm using Feisty.

---

### Post by mchang on 2007-09-05
Is this moving out of proposed soon? Just wondering.

---

### Post by twkisner on 2007-09-05
Installed from proposed last night on Fiesty.  All is well.:)

---

### Post by Pizzaman777 on 2007-09-05
Can anyone help with this error?

```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-09-05 18:09:43.871 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-09-05 18:09:58.724 Unable to connect to database!
2007-09-05 18:09:58.724 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.2.9' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-09-05 18:09:58.780 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-09-05 18:09:58.835 Failed to init MythContext, exiting.
```

I can't get into my backend...

---

### Post by clievers on 2007-09-05
Well, I just tried it, neverously, and it seems to work -- knock on wood. I am going on holidays soon so I had to do it as I will be away from my computer for the next week and a half.
---
Update sources to include the proposed packages.
Uncheck all updates (cause they could be pre-release as well).
Check "mythtv" (version 0.20.2-0ubuntu0.7.04~proposed, and it will automatically select it's dependencies needed in the updates.
Click "Install Updates".
You should get a message that says there is information about the update that just happened. Close it.
Run "mythtv-setup" from the command line.
Go into the Video Sources and choose your source, change the information to your schedule direct account, save the information.
When prompted for the mythfilldatabase, click OK.
Restart your mysql/mythbackend (I just rebooted).
Set the sources back to "not" include the proposed packages.

---

### Post by heckheck on 2007-09-06
Has this patch made it out of proposed and into the normal feisty distribution yet?  The bug is marked fixed, and there was an update yesterday to the bug saying "The uploads to proposed have been accepted now" (see [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/134726](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/134726)).

I'd like to get it without having to use the proposed repository and then updating twice (but I'm quickly running out of guide data :-)

Thanks

-Jim

---

### Post by kspider on 2007-09-07
0.20.2 from proposed works well for me.  A couple questions:

1) Does a 0.20.0 frontend need to be updated to 0.20.2 to connect with a 0.20.2 backend?

2) Once 0.20.2 switches over to normal multiverse, will the mythtv packages installed from proposed have to be updated?  Also, will I safely be able to remove proposed from my sources.list?

I've never installed anything from proposed before...

Thanks - spider

---

### Post by newlinux on 2007-09-07
> **kspider said:**
> 0.20.2 from proposed works well for me.  A couple questions:

1) Does a 0.20.0 frontend need to be updated to 0.20.2 to connect with a 0.20.2 backend?

2) Once 0.20.2 switches over to normal multiverse, will the mythtv packages installed from proposed have to be updated?  Also, will I safely be able to remove proposed from my sources.list?

I've never installed anything from proposed before...

Thanks - spider

1. I don't think so -  I don't think there has been a protocol change.

2. I've already removed the proposed repo from my sources.lst Unless there is a major bug fix that goes in the proposed, I'll wait until myth updates are in the multiverse.

---

### Post by NT4usB on 2007-09-07
I just looked and there is a ~proposed1 in there now.
Waffling if I should break a working install in order to continue test driving these new proposed...
Guess that's why were here so, lets go for it.

---

### Post by newlinux on 2007-09-07
wonder what's been changed...

---

### Post by NT4usB on 2007-09-07
I dunno but it works fine.
Overwrote all my custom osd*.pngs though.

---

### Post by mackandall on 2007-09-07
Does anyone know how to get this update fro Dapper yet? I cant upgrade to Feisty because my usb tuners dont work well with the newer kernel when both are installed at the same time.

---

### Post by mfarley on 2007-09-08
> **heckheck said:**
> Has this patch made it out of proposed and into the normal feisty distribution yet?  The bug is marked fixed, and there was an update yesterday to the bug saying "The uploads to proposed have been accepted now" (see [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/134726](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/134726)).

I'd like to get it without having to use the proposed repository and then updating twice (but I'm quickly running out of guide data :-)

Thanks

-Jim

I'm with Jim -- still waiting to update, don't want to use the proposed repos.

When will this make it into multiverse?

---

### Post by vanilla slimfast on 2007-09-09
Help!  I've managed to get myself stuck in dependency hell, and I'm not sure how to get myself out, short of completely uninstalling everything related to myth.

Here's where I'm at now

```
root@theking:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20.2-0ubuntu0.7.04.1) but 0.20.1+fixes14084-0.0ubuntu0mythbuntu1 is installed
          Depends: mythtv-backend (= 0.20.2-0ubuntu0.7.04.1) but 0.20.1+fixes14084-0.0ubuntu0mythbuntu1 is installed
  mythtv-frontend: Depends: mythtv-common (= 0.20.2-0ubuntu0.7.04.1) but 0.20.1+fixes14084-0.0ubuntu0mythbuntu1 is installed
E: Unmet dependencies. Try using -f.

```

Ok, so it seems that the fixes weeklies I had been running don't want to cleanly upgrade back to the ubuntu packages.  I try doing -f install and get this

```
root@theking:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  php5-mysql
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mythtv-backend mythtv-common mythtv-database
Suggested packages:
  mythweb
Recommended packages:
  mythtv-doc
The following packages will be REMOVED:
  mythtv-transcode-utils
The following packages will be upgraded:
  mythtv-backend mythtv-common mythtv-database
3 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/6167kB of archives.
After unpacking 111kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 123530 files and directories currently installed.)
Preparing to replace mythtv-backend 0.20.1+fixes14084-0.0ubuntu0mythbuntu1 (using .../mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb) ...
Unpacking replacement mythtv-backend ...
dpkg: error processing /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mythtranscode', which is also in package mythtv-transcode-utils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Nothing I seem to do gets me past it blowing up when installing the backend...something related to the transcode utils?  I can't seem to do anything else and now I'm in a halfway upgraded state with no working myth :(

Any ideas?  Thanks in advance for the help!

---

### Post by kc0dhb on 2007-09-09
You can try uninstalling (not purging) all (or simply part of the) myth related packages, and then installing them again. Alternatively, you can use synaptic to select the correct versions. What appears to be happening is that it won't let you upgrade one piece at a time.

summary
```

sudo apt-get remove mythtv mythtv-backend mythtv-database

```
might have to do it twice
then
```

apt-get install  mythtv mythtv-backend mythtv-database

```

---

### Post by vanilla slimfast on 2007-09-09
> **kc0dhb said:**
> You can try uninstalling (not purging) all (or simply part of the) myth related packages, and then installing them again. Alternatively, you can use synaptic to select the correct versions. What appears to be happening is that it won't let you upgrade one piece at a time.

summary
```

sudo apt-get remove mythtv mythtv-backend mythtv-database

```
might have to do it twice
then
```

apt-get install  mythtv mythtv-backend mythtv-database

```

So I went ahead and tried this and it worked.  I had to uninstall EVERY myth package.  I also made sure to exclude transcode-utils from my subsequent install statement

```
apt-get remove mythtv mythtv-backend mythtv-database mythtv-common mytharchive mythdvd mythflix mythgallery mythmusic mythtv-frontend mythtv-transcode-utils mythvideo mythtv-themes
apt-get install mythtv mythtv-backend mythtv-database mythtv-common mytharchive mythdvd mythflix mythgallery mythmusic mythtv-frontend mythvideo mythtv-themes

```

After it ran successfully, I was able to fire up the setup program and update my guide info...all my settings were preserved.

Thanks again!

---

### Post by Rogerwa on 2007-09-10
OK maybe I'm just stupid, it is 3 am and I am messing with this, but I enable the checkbox for the propsed and reload and I don't see any new versions of Myth to install.

I am running Edgy(2.6.17-10-generic (SMP))

What simple thing am I missing.

---

### Post by newlinux on 2007-09-10
> **Rogerwa said:**
> OK maybe I'm just stupid, it is 3 am and I am messing with this, but I enable the checkbox for the propsed and reload and I don't see any new versions of Myth to install.

I am running Edgy(2.6.17-10-generic (SMP))

What simple thing am I missing.

That should be all you have to do. Did you search for myth in synaptic and look carefully at version numbers?

---

### Post by Rogerwa on 2007-09-10
Yes, the versions were the same.  I even reinstalled just to be sure and I'm still at the old version/.

---

### Post by MrFSL on 2007-09-10
I upgraded last night.

Fixed a bunch of things including mythweather. I have the Schedule Direct option now but the problem is that it doesn't seem to be retrieving my lineup.

I run mythfilldatabase and it seems to work correctly but no lineup info is showing. Any clues?

---

### Post by NT4usB on 2007-09-10
Did you go to SD and setup a lineup?

---

### Post by heckheck on 2007-09-10
> **mfarley said:**
> I'm with Jim -- still waiting to update, don't want to use the proposed repos.

When will this make it into multiverse?

Well only 3 days of guide info left, and still this package hasn't shown up in the "regular" multiverse repository.  Can anyone comment?  I'm going to update the original bug and ask this question, but it looks like I might be using proposed in order to avoid interruption.

-Jim

---

### Post by uopjohnson on 2007-09-10
Guide data is running thin.  Any update on when this will make it out of proposed and into multiverse?  I don't need an exact date I just need to know if the release is imminent or if I need to go ahead an switch to proposed because it is going to be a few weeks.   
I don't think I'm the only one waiting on this info...

---

### Post by aaltieri on 2007-09-10
I just installed Myth per the guide at [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

I tried to update and that gave me several errors.  So I tried removing the myth packages I had installed, and re-installing the new packages.  Now the auto-login for gdm no longer works.  And that package does not, nor do I want, have synaptic installed.  And the gdm.conf file is back to spec.  Yes, I know...I should have made a copy.

Can anyone post the relevant bits of files for the gdm config to make this work again?  Or tell me how to pull the file out of the old myth package without hosing my system even more?


Thanks!

Peace.

---

### Post by MrFSL on 2007-09-11
Alrighty I finally got this working.

I added the repo then:
```
sudo apt-get update
```
Next:
```
su8do apt-get upgrade
```
When asked if I wanted to install the packages I answered NO

I noted which updates were for myth and installed them individually:
```
sudo apt-get install mythtv-backend-master mythtv-frontend ...etc 
```

I remove the repo.

I inputed my user account information - Did a channel scan - then ran mythfilldatabase.

Thanks all.

---

### Post by superm1 on 2007-09-11
Guys regarding this leaving proposed.  It needs at least 7 days of gestation after every upload.  The last upload was accepted 6 days ago, so there will be a request tomorrow to copy it over to -updates.  Please post in the bug that things were working for you if you haven't already.

---

### Post by pnotequalsnp on 2007-09-11
Thank you for your install instructions.

I have found that I get a process called mysqld_safe using 100% of 1/4 CPU's after the mythtv 0.20.2 install.  I am running the 64-bit version of Ubuntu.  Any ideas?

---

### Post by Rogerwa on 2007-09-11
Regarding my problem with see the proposed update, I get the following message when I press reload.  Could this be a problem and how would I fix it. Please bear with me as I am new to Linux and Ubuntu..

[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/edgy/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy/Release:) Unable to find expected entry  multiuniverse/source/Sources in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)

Thanks

---

### Post by Rogerwa on 2007-09-11
Nevermind..  Fixed problems in my sources file.  I can now see the proposed updates..

Its mostly working fine now. I am getting program listings.  I did have to do a couple tweaks.  See following:

1) I had to reset the MythTV DB account password for mythtv@localhost - Backend wasn't loading and I was getting errors that could not log into DB
2) Had to reset symbolic link for .ht access in the /var/www/mythweb directory to /etc/mythtv/mythtv-ht access.conf.  It broke during the upgrade

MythWeather works fine on the tv screen but doesn't work on Mythweb..  Anyone?

---

### Post by BruceLerner on 2007-09-13
Just checking in with a data point and thank you. Followed the instructions from the 1st post on Kubuntu Feisty on an AMD-64 in 386 mode. Smooth. Thank you.

---

### Post by superm1 on 2007-09-14
As of this evening these were copied over to -updates.  All users setting up myth from this point forward should end up with a copy of them.

Thanks for all the great feedback in this thread :)

---

### Post by tagra123 on 2007-09-14
Please add the following helps to your main post.

MythTV LIRC Serial Blaster
[http://ubuntuforums.org/showthread.php?t=550068](http://ubuntuforums.org/showthread.php?t=550068)

MythTV Fixing Duplicate Recording Problem  Converting ZapToIt to Schedule Direct SOLVED
[http://ubuntuforums.org/showthread.php?t=550011](http://ubuntuforums.org/showthread.php?t=550011)

---

### Post by napsilan on 2007-09-14
> **superm1 said:**
> As of this evening these were copied over to -updates.  All users setting up myth from this point forward should end up with a copy of them.

Thanks for all the great feedback in this thread :)

Do we have to install from scratch again, because apt update/upgrade isn't finding any upgrades to mythtv.  (feisty 32bit, installed via myth-backend and myth-frontend metapackages)

---

### Post by superm1 on 2007-09-14
> **napsilan said:**
> Do we have to install from scratch again, because apt update/upgrade isn't finding any upgrades to mythtv.  (feisty 32bit, installed via myth-backend and myth-frontend metapackages)
When I say copied, I literally mean copied from *proposed* to *updates.  *If you were running the -proposed version, you've already got the version that is in updates now too.

---

### Post by Explodinglemur on 2007-09-14
How long should it take for the new Myth packages to show up in the -udpates package lists?  The Packages.gz/bz2 files at [http://mirrors.kernel.org/ubuntu/dists/feisty-updates/multiverse/binary-i386/](http://mirrors.kernel.org/ubuntu/dists/feisty-updates/multiverse/binary-i386/) were last updated on August 31st, and do not yet include the new mythtv packages (though the .deb files are in the repositories, [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/) )

---

### Post by Explodinglemur on 2007-09-14
Aha, I see an updated packages listing on archive.ubuntu.com...so it should distribute to the other mirrors soon, and I'll just use archive.ubuntu.com for now.  Nevermind, I was just a bit impatient :)

---

### Post by ravalox on 2007-09-16
I marked the repository to use pre-release items so I can get the latest Mythtv to use SchedulesDirect.  Everything installs, but when I run mythtv-setup it doesn't show anything I add; I ad capture cards and they aren't listed; they do appear in the database.  When I attempt to run mythfilldatabase I'm told "Table 'mythconverg.videosource' doesn't exist".  Has anyone struggled with this already?

---

### Post by Chuckels550 on 2007-09-17
I updated to MythTV and plugins 0.20.2 with no trouble.  

It fixed Mythweather on the MythTV frontend, but for some reason MythWeb doesn't display the fixed Mythweather, but instead displays the way it displayed before with errors.  

I am having trouble with the audio for MythDVD, but that existed before - issue with configuring ALSA, the PVR 350 and the soundcard.  

Schedule Direct channels and shows were mixed up, but I was able to fix that by running mythfilldatabase with the renew all option.

---

### Post by tridens on 2007-09-19
I had a fresh install of MythTV on Feisty.  To fix the "Table 'mythconverg.videosource' doesn't exist" problem delete the tables in the mythtv database.  In my case there were only two tables to delete.

Running mythtv-setup through a terminal window showed all sorts of DB problems, but wasn't going  to try to rebuild because it found a mythtv database.  Deleting all the tables deletes the DB (at least the way I did it through phpmyadmin) and will cause mythtv-setup to rebuild the whole database.  In my case it did this correctly....

---

### Post by michwill on 2007-09-22
> **NT4usB said:**
> no joy updating the slave be/fe.
posting to the buglist.
ed:
#135433
I fixed it. libmyth-0.20 didn't install/upgrade when I updated. Added it and now it works.


How exactly did you get this to work?  I keep getting an error stating the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kommander
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libmyth-0.20
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0B/7271kB of archives.
After unpacking 193kB of additional disk space will be used.
(Reading database ... 137050 files and directories currently installed.)
Preparing to replace libmyth-0.20 0.20-svn20070223-0.0 (using .../libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb) ...
Unpacking replacement libmyth-0.20 ...
dpkg: error processing /var/cache/apt/archives/libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmyth-0.20.2.so.0.20.2', which is also in package libmyth-0.20.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by techstop on 2007-09-23
> **flyingcircus said:**
> The upgrade to 0.20.2 worked fine on Edgy for me. However, I had a problem with the .htaccess file  for mythweb. I was getting a 403 forbidden error when I tried to access mythweb. I finally, found the problem to be a broken symlink.
     For some reason the symlink /var/www/mythweb/.htaccess  was pointing to /etc/mythtv/mythweb-htaccess . However /etc/mythtv/mythweb-htaccess doesn't exist, it needs to point to /etc/mythtv/mythweb-htaccess.conf   As soon as I changed that, the 403 error went away and all is back to normal.

I'm also on Edgy, just upgraded in the last few days to 0.20.2. It broke MythWeb in the same way as it did for you. I created the symlink again and it's working once more. Thanks for posting the fix!

---

### Post by superm1 on 2007-09-23
> **michwill said:**
> How exactly did you get this to work?  I keep getting an error stating the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kommander
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libmyth-0.20
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0B/7271kB of archives.
After unpacking 193kB of additional disk space will be used.
(Reading database ... 137050 files and directories currently installed.)
Preparing to replace libmyth-0.20 0.20-svn20070223-0.0 (using .../libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb) ...
Unpacking replacement libmyth-0.20 ...
dpkg: error processing /var/cache/apt/archives/libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmyth-0.20.2.so.0.20.2', which is also in package libmyth-0.20.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmyth-0.20_0.20.2-0ubuntu0.7.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Check your source for that libmyth package.  Sounds like you've got a conflict of repositories.

---

### Post by pnotequalsnp on 2007-09-23
The install worked perfectly on a fresh install of 64-bit Ubuntu.  I quick set up of the backend and schedules direct worked with no problem. 

The only problem I have is that I must change channels before the sound works.  If I schedule a recording, there is no sound.  Thanks for a SD mythtv version and any help you could give.

---

### Post by michwill on 2007-09-24
> **superm1 said:**
> Check your source for that libmyth package.  Sounds like you've got a conflict of repositories.


Ok, I've looked at my sources file.  But what is the fix?  I'm not sure which repositories would be conflicting.  Should I remove/comment the "proposed" repository after all, or is there another that needs to be stopped?

---

### Post by dannyboy79 on 2007-09-24
since the 20.2 packages have been copied to the normal repositories, you should be able to remove proposed and reinstall or just do an update, upgrade. if you had mythtv working, backup your mysql database using mysqldump, [http://www.devarticles.com/c/a/MySQL/Backing-Up-Your-MySQL-Databases-With-MySQLDump/](http://www.devarticles.com/c/a/MySQL/Backing-Up-Your-MySQL-Databases-With-MySQLDump/)
then completely remove mythtv, then reinstall it.

---

### Post by superm1 on 2007-09-24
you can use apt-cache to determine where a package is coming from.

```
apt-cache policy PACKAGENAME
```

is the syntax for it

---

### Post by NT4usB on 2007-09-24
Will there be any official 'hacks' to disable the helpful prompt which notifies us that the backend is running and forces us to shut down the backend before running mythtv-setup?
On 0.19 and stuff, if we made changes, we'd restart the backend and they would take effect. That way we'd only miss a second or two of anything recording.
And sometimes we just want to look around.
I found the skript in an earlier version and managed to butcher it up and stop it from prompting. It was ugly and complained and kicked and screamed, but I could look around setup without stopping the backend. Of course, I didn't take notes when I did it so I would have to chase it down all over again...

Thanks for all the good work you're doing on Myth!

---

### Post by superm1 on 2007-09-24
> **NT4usB said:**
> Will there be any official 'hacks' to disable the helpful prompt which notifies us that the backend is running and forces us to shut down the backend before running mythtv-setup?
On 0.19 and stuff, if we made changes, we'd restart the backend and they would take effect. That way we'd only miss a second or two of anything recording.
And sometimes we just want to look around.
I found the skript in an earlier version and managed to butcher it up and stop it from prompting. It was ugly and complained and kicked and screamed, but I could look around setup without stopping the backend. Of course, I didn't take notes when I did it so I would have to chase it down all over again...

Thanks for all the good work you're doing on Myth!
Just run /usr/bin/mythtv-setup.real instead.

---

### Post by NT4usB on 2007-09-26
Interesting... I have mythtv-setup.real on my master but not on my slave.
I'm pretty sure I updated after 20.2 was moved to updates. The slave says it's 0.20.2...

---

### Post by superm1 on 2007-09-26
> **NT4usB said:**
> Interesting... I have mythtv-setup.real on my master but not on my slave.
I'm pretty sure I updated after 20.2 was moved to updates. The slave says it's 0.20.2...
Well mythtv-setup is a wrapper for mythtv-setup.real.  There is no way mythtv-setup will work unless mythtv-setup.real exists.  The only explanation for this is if you installed from source or something to that effect.

---

### Post by NT4usB on 2007-09-26
The install and all updates have been from the repos, nothing handrolled on Edgy.

I ran ```
/usr/bin/mythtv-setup.real
```and just plain old```
mythtv-setup.real
```and got a not found.

I searched for .real```
ct@wimp:~$ locate *.real
```and found other reals but not mythtv-setup.real.

I know I hacked on mythtv-setup (or whatever it points to)  to get rid of the prompt... have to open it up, retrace my steps, and see what I did to it.

---

### Post by superm1 on 2007-09-26
> **NT4usB said:**
> The install and all updates have been from the repos, nothing handrolled on Edgy.

I ran ```
/usr/bin/mythtv-setup.real
```and just plain old```
mythtv-setup.real
```and got a not found.

I searched for .real```
ct@wimp:~$ locate *.real
```and found other reals but not mythtv-setup.real.

I know I hacked on mythtv-setup (or whatever it points to)  to get rid of the prompt... have to open it up, retrace my steps, and see what I did to it.

Ohh.  Your on edgy.  I believe the mythtv-setup.real was introduced to the packaging later on.  I forgot to mention that part :)

---

### Post by michwill on 2007-09-26
But how do you actually set up the "schedulesdirect.org" info?  I keep missing this. I'm looking for explicit instructions.  There is no option available by default in the GUI or in any files as far as I see.

---

### Post by superm1 on 2007-09-26
> **michwill said:**
> But how do you actually set up the "schedulesdirect.org" info?  I keep missing this. I'm looking for explicit instructions.  There is no option available by default in the GUI or in any files as far as I see.

Once you've got 0.20.2 installed, there is an option within mythtv-setup for your video source type.  If you're not seeing this option, your not on 0.20.2.  Remove any installs from source (if you have done any), and make sure that you have the right versions installed in apt.

---

### Post by michwill on 2007-09-26
Alright, I finally removed the "feisty proposed" nonsense and got everything to upgrade.  I changed the source to SD, but now mythfilldatabase gives me a million errors and says it's still looking at "Zap2It".

I've seen several different forums that talk about a manual setup involving XMLTV and such, but I fail to believe that it is really this complex.  I'm sure there is something amazingly simple that I'm mssing. :confused:

---

### Post by NT4usB on 2007-09-27
> **superm1 said:**
> Ohh.  Your on edgy.  I believe the mythtv-setup.real was introduced to the packaging later on.  I forgot to mention that part :)

Yup. Edgy slave. Probably going to blow out Feisty and put Edgy on the master too. So far, Feisty has been less than reliable...
Edgy had a mythtv-setup.sh, which I think I hacked to get rid of the close prompt. Looks like it doesn't use it anymore though since only my backups remain on the system.

---

### Post by superm1 on 2007-09-27
> **michwill said:**
> Alright, I finally removed the "feisty proposed" nonsense and got everything to upgrade.  I changed the source to SD, but now mythfilldatabase gives me a million errors and says it's still looking at "Zap2It".

I've seen several different forums that talk about a manual setup involving XMLTV and such, but I fail to believe that it is really this complex.  I'm sure there is something amazingly simple that I'm mssing. :confused:
perhaps just blow away your guide source and make a new one.  Should go away.  I've had no issues or needs for xmltv on mine :)

---

### Post by michwill on 2007-09-27
Ok, word to the wise.  Don't always assume that you're going to run into the same troubles as everyone else.  I often make this mistake, and have found that following your own course is at times advisable.

For instance.  In this case, I started reading the boards and collecting data before touching my system -- a responsible approach in and of itself.  But in this case it proved to be the wrong choice.

I began by implementing updates assuming my system was going to run into the "update" problems as others.  After encountering numerous other issues during this process, I decided to simply "roll back" and get rid of all the changes I'd made and simply do the following:


1) since the new myth is now in the default repositories *DON'T  USE THE PROPOSED REPOSITORIES*
2) sudo apt-get update
3) sudo apt-get upgrade
4) edit your source in mythtv-setup
5) run mythfilldatabase


. . .that worked for me with *no* problems.  Hope the same goes for the majority

Regards


P.S. Thanks again to superm1 and the others for continuously giving assistance

---

### Post by bliffle on 2007-10-03
Zap2it may be going away, but "freeguide" still insists that one register at zap2it and use that handle. But even that doesn't work.

---

### Post by merkur2k on 2007-10-05
So I lost my hard drive and have been forced to rebuild my myth box.
I decided to use feisty for this (since i already had a copy of the cd handy).
Long story short, it installed mythtv 0.20.0, and i have no idea why nor can i figure out how to make it upgrade (apt sources have not been modified, and apt-get update apt-get upgrade etc more than once).
If it helps any, I used the guide here: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)
The upgrade was painless a few weeks ago on my previous edgy setup, so I dont understand what has happened. All I can think of right now is that the debs have been reverted on the repositories for some reason, and that would simply be unacceptable behavior for something supposedly as mature as ubuntu.
```

root@core:~# ls /var/cache/apt/archives/*myth*
/var/cache/apt/archives/libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-backend_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-backend-master_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-common_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-database_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-frontend_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-themes_0.20-0.1_all.deb
/var/cache/apt/archives/ubuntu-mythtv-frontend_0.20-svn20070122-0.0ubuntu6_all.deb

```
interestingly enough, this isnt even the version thats displayed in mythtv itself, rather it thinks it is 0.20.20060828
Any ideas?

---

### Post by superm1 on 2007-10-05
> **merkur2k said:**
> So I lost my hard drive and have been forced to rebuild my myth box.
I decided to use feisty for this (since i already had a copy of the cd handy).
Long story short, it installed mythtv 0.20.0, and i have no idea why nor can i figure out how to make it upgrade (apt sources have not been modified, and apt-get update apt-get upgrade etc more than once).
If it helps any, I used the guide here: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)
The upgrade was painless a few weeks ago on my previous edgy setup, so I dont understand what has happened. All I can think of right now is that the debs have been reverted on the repositories for some reason, and that would simply be unacceptable behavior for something supposedly as mature as ubuntu.
```

root@core:~# ls /var/cache/apt/archives/*myth*
/var/cache/apt/archives/libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-backend_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-backend-master_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-common_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-database_0.20-svn20070122-0.0ubuntu6_all.deb
/var/cache/apt/archives/mythtv-frontend_0.20-svn20070122-0.0ubuntu6_i386.deb
/var/cache/apt/archives/mythtv-themes_0.20-0.1_all.deb
/var/cache/apt/archives/ubuntu-mythtv-frontend_0.20-svn20070122-0.0ubuntu6_all.deb

```interestingly enough, this isnt even the version thats displayed in mythtv itself, rather it thinks it is 0.20.20060828
Any ideas?
You are missing the feisty/edgy-updates for universe and multiverse/

---

### Post by merkur2k on 2007-10-05
so there we go, thats what i get for working on this so late at night...
now to figure out how to properly run mythtv-setup, i used to just run it in a vnc, but now it segfaults.

---

### Post by superm1 on 2007-10-05
> **merkur2k said:**
> so there we go, thats what i get for working on this so late at night...
now to figure out how to properly run mythtv-setup, i used to just run it in a vnc, but now it segfaults.
Should run fine in either vnc or X forwarding.

---

### Post by antoniuk on 2007-10-05
Can someone please help me by telling me how I get back into mythtv-setup? I can't from the command line it gives me some gtk-warning. Is there a way to delete out the setup config and start over? I am way frustrated right now

Just watn to add I am following this guide:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

all I want to do is reset ym setup but I keep getting unable to open display becasue I have no gui only the mythtv frontend. Is there some way to remove the settings so that it prompts upon launching mythtv?

---

### Post by antoniuk on 2007-10-05
nevermind, I started a failsafe xterm session and got it going. Wow talk about frustrating!

---

### Post by lawson23 on 2007-10-06
> **afljafa said:**
> Well - I have a frontend only edgy install. I get 

"mythfrontend: error while loading shared libraries: libmythtv-0.20.2.so.0"

errors when starting the frontend. libmythtv-0.20.so.0 exists under /usr/lib however libmythtv-0.20.2.so.0 doesn`t.

Ok not entirely sure what happened but I ran an
apt-get update
apt-get upgrade
Let it do it's thing and seen some myth stuff in the upgrade.

Now today I can't start mythtv anymore.  Looks similar to the issue quoted above.  As I'm a newb can someone give me low down on what I need to do?

What I get exactly:
***/usr/bin/mythfrontend.real: error while loading shared libraries: libmythtv-0.20.so.0: cannot open shared object file: no such file or directory***

---

### Post by superm1 on 2007-10-07
> **lawson23 said:**
> Ok not entirely sure what happened but I ran an
apt-get update
apt-get upgrade
Let it do it's thing and seen some myth stuff in the upgrade.

Now today I can't start mythtv anymore.  Looks similar to the issue quoted above.  As I'm a newb can someone give me low down on what I need to do?

What I get exactly:
***/usr/bin/mythfrontend.real: error while loading shared libraries: libmythtv-0.20.so.0: cannot open shared object file: no such file or directory***

You either have had (or have) a different repository other than ubuntu activated, or have not upgraded libmyth-0.20.

Try to upgrade libmyth-0.20.  If you had a different repository activated, you need to roll back to the right packages.

---

### Post by lawson23 on 2007-10-07
> You either have had (or have) a different repository other than ubuntu activated, or have not upgraded libmyth-0.20.

Used your guide you had built right when Feisty was released.

> Try to upgrade libmyth-0.20. If you had a different repository activated, you need to roll back to the right packages.
Could you please provide some help on how to do this?
When I looked at:
```
myth1@SERVER:/usr/lib$ ls libmyth*
libmyth-0.20.2.so.0
libmyth-0.20.2.so.0.20 
libmyth-0.20.2.so.0.20.2

```
So from this I'm guessing it is already upgraded but isn't looking for the correct files??

---

### Post by superm1 on 2007-10-07
> **lawson23 said:**
> Used your guide you had built right when Feisty was released.


Could you please provide some help on how to do this?
When I looked at:
```
myth1@SERVER:/usr/lib$ ls libmyth*
libmyth-0.20.2.so.0
libmyth-0.20.2.so.0.20 
libmyth-0.20.2.so.0.20.2

```So from this I'm guessing it is already upgraded but isn't looking for the correct files??

1) Okay like this:

```
apt-cache policy libmyth-0.20
```

if need be,

```
apt-get install libmyth-0.20
```

2) Check for any files in /usr/local/lib or /usr/local/bin

3) Check for any third party repositories you have activated

```
cat /etc/apt/sources.list
```

---

### Post by lawson23 on 2007-10-08
1.```
apt-cache policy libmyth-0.20
```
Produces:
```
apt-cache policy libmyth-0.20
libmyth-0.20:
  Installed: 0.20.2-0ubuntu0.7.04.1
  Candidate: 0.20.2-0ubuntu0.7.04.1
  Version table:
 *** 0.20.2-0ubuntu0.7.04.1 0
        500 http://archive.ubuntu.com feisty-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.20-svn20070122-0.0ubuntu6 0
        500 http://archive.ubuntu.com feisty/multiverse Packages

```
Didn't run the install suggested yet.
2.files in /usr/local/lib or /usr/local/bin
```
/usr/local/lib$ ls
python2.5

```
```
/usr/local/bin$ ls

```
3.
```
cat /etc/apt/sources.list
```
Produces (minus the # commented entries):
```
#
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#libdvdcss2 videolan.org source
deb ftp://ftp.videolan.org/pub/videolan/ubuntu feisty universe

#Canonical Repository
deb http://archive.canonical.com/ubuntu feisty-commercial main

```
I do believe there is something wrong with my videolan source as I get an error during update.

---

### Post by superm1 on 2007-10-08
> **lawson23 said:**
> 1.```
apt-cache policy libmyth-0.20
```Produces:
```
apt-cache policy libmyth-0.20
libmyth-0.20:
  Installed: 0.20.2-0ubuntu0.7.04.1
  Candidate: 0.20.2-0ubuntu0.7.04.1
  Version table:
 *** 0.20.2-0ubuntu0.7.04.1 0
        500 http://archive.ubuntu.com feisty-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.20-svn20070122-0.0ubuntu6 0
        500 http://archive.ubuntu.com feisty/multiverse Packages

```Didn't run the install suggested yet.
2.files in /usr/local/lib or /usr/local/bin
```
/usr/local/lib$ ls
python2.5

``````
/usr/local/bin$ ls

```3.
```
cat /etc/apt/sources.list
```Produces (minus the # commented entries):
```
#
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#libdvdcss2 videolan.org source
deb ftp://ftp.videolan.org/pub/videolan/ubuntu feisty universe

#Canonical Repository
deb http://archive.canonical.com/ubuntu feisty-commercial main

```I do believe there is something wrong with my videolan source as I get an error during update.

Okay, we're going to have to look a little closer here at other possible problems:

Regarding the VLC error, you may need their apt key.  I hope that they don't have any conflicting dependencies (but that is a possbility).  You can get libdvdcss2 from medibuntu to be safe.

Try this:
ldd /usr/bin/mythtv-setup.real

That will show where all the shared libraries that get loaded for mythtv-setup.real are located at.

Lastly, disable that VLC repository, and apt-get update.  Open up synaptic and check the section entitled "Local or Obsolete".  See what's listed there.  You shouldn't see anything but libdvdcss2 typically.  If there is any other stuff, choose it and hit ctrl-e.  This will let you roll back to the proper version that is in Ubuntu.  Also, please list it here so others can make sense of it.

---

### Post by lawson23 on 2007-10-08
```
 ldd /usr/bin/mythtv-setup.real
        linux-gate.so.1 =>  (0xffffe000)
        libmythtv-0.20.so.0 => not found
        libmythavformat-0.20.so.0 => not found
        libmythavutil-0.20.so.0 => not found
        libmythavcodec-0.20.so.0 => not found
        libmythfreemheg-0.20.so.0 => not found
        libmythupnp-0.20.so.0 => not found
        libmythlivemedia-0.20.so.0 => not found
        libmyth-0.20.so.0 => not found
        libmythui-0.20.so.0 => not found
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7e76000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb7dbd000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7cf8000)
        libartsc.so.0 => /usr/lib/libartsc.so.0 (0xb7cf1000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7cee000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cea000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7ce5000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7cdc000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7c47000)
        libjack-0.100.0.so.0 => /usr/lib/libjack-0.100.0.so.0 (0xb7c2d000)
        libraw1394.so.8 => /usr/lib/libraw1394.so.8 (0xb7c27000)
        libiec61883.so.0 => /usr/lib/libiec61883.so.0 (0xb7c1a000)
        libavc1394.so.0 => /usr/lib/libavc1394.so.0 (0xb7c16000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7c13000)
        libXv.so.1 => /usr/lib/libXv.so.1 (0xb7c0e000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7c08000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7c02000)
        libXvMCW.so.1 => /usr/lib/libXvMCW.so.1 (0xb7bfd000)
        libXvMC.so.1 => /usr/lib/libXvMC.so.1 (0xb7bfa000)
        libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0xb73ea000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb736a000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7309000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb72f3000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb72e5000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb71f4000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb71dd000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb70f3000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb70cb000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb70bf000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6f7e000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb6f6a000)
        /lib/ld-linux.so.2 (0xb7eef000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6f62000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb6f36000)
        libaudio.so.2 => /usr/lib/libaudio.so.2 (0xb6f20000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb6ecf000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb6eb0000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6e8d000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb6e85000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6e7b000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb6e69000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb6e60000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb6e48000)
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb6e3f000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb6e3b000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6e36000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6e16000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6e11000)

```
Now I'm going to do what you mention LASTLY.  By the way thanks for the help.

---

### Post by lawson23 on 2007-10-08
I disabled the vlc repository and did the update but lost on the next item.
> Open up synaptic and check the section entitled "Local or Obsolete"
I may say something stupid here but isn't this through the gui?
I used your guide using the alternative disk setup like a server.

---

### Post by superm1 on 2007-10-08
> **lawson23 said:**
> I disabled the vlc repository and did the update but lost on the next item.

I may say something stupid here but isn't this through the gui?
I used your guide using the alternative disk setup like a server.
Yeah this is through the GUI.  If you are remotely working on this (via ssh), you can X forward and run synaptic.  Synaptic is probably the easiest way to check this though.

---

### Post by lawson23 on 2007-10-08
Ok I have openbox running on the screen with a terminal open.  How do I execute something to start synaptic?  Searching online I can't find a terminal command to do this.

Figured it out.  First I had to install synaptic:
```
sudo apt-get install synaptic
```
Then ran synaptic:
```
sudo synaptic
```

---

### Post by superm1 on 2007-10-08
```
sudo synaptic
```

In case its not installed, ```
sudo apt-get install synaptic 
```first

---

### Post by lawson23 on 2007-10-08
Hey thanks for replying but as you could see I finally figured it out and then realized you posted the answer.

Anyways in Sections I couldn't find Local or Obsolete.
In Status I found:
Installed (local or obsolete)
I figure this is what you want.
Listed is only
lirc-modules-2.6.20-15-generic

Did not hit ctrl e
Yet

Now if I look at installed (upgradable)
I have a ton of Myth options

---

### Post by superm1 on 2007-10-08
> **lawson23 said:**
> Hey thanks for replying but as you could see I finally figured it out and then realized you posted the answer.

Anyways in Sections I couldn't find Local or Obsolete.
In Status I found:
Installed (local or obsolete)
I figure this is what you want.
Listed is only
lirc-modules-2.6.20-15-generic

Did not hit ctrl e
Yet

Now if I look at installed (upgradable)
I have a ton of Myth options

Okay there you go.  Upgrade any of the myth stuff that is upgradable :)

---

### Post by lawson23 on 2007-10-08
Ok they are being upgraded.  Here is what I selected (see attached jpg).


---------------------
Update this fixed my problem myth now loads.  Thank you!

---

### Post by markuswells on 2007-10-10
ok, maybe I am missing something but I am not able to upgrade because my repo only shows the 20.0 version.

I am running a fairly new install of feisty 7.04.
I have tried to apt-get update and apt-get upgrade and tried synaptic but I seem to be unable to get the new package. ANY help would be great at this point!

```
~$ apt-cache policy libmyth-0.20libmyth-0.20:
  Installed: 0.20-svn20070122-0.0ubuntu6
  Candidate: 0.20-svn20070122-0.0ubuntu6
  Version table:
 *** 0.20-svn20070122-0.0ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
        100 /var/lib/dpkg/status
~$
```

---

### Post by Explodinglemur on 2007-10-10
You need to have feisty-updates enabled in your package source list.

GUI (gnome):
System, Administration, Software Sources, Updates tab, make sure "Recommended updates" is checked.

Console:
Edit /etc/apt/sources.list and add:
deb [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) feisty-updates main restricted universe multiverse

Then update your package list and you should see the newer version.

---

### Post by markuswells on 2007-10-10
yup that got me squared away - thanks

---

### Post by Hopworks on 2007-10-21
Sorry for the late bump on this thread, but superm1! You are my hero!

And I almost gave up hope because I did all that you described, and then ran the mythfilldatabase from the CLI, and it still failed, with that old URL.

Just before I gave up, a light bulb exploded over my head and I ran the backend setup again, but now this time, there are different options in the video source setup, and I picked what I needed, grabbed my lineup, and WOW! YEAH!  Now mythfilldatabase is taking a long time to do its thing, and that is just fine with me! That means it is working!

This is a major triumph for me, since I jumped through some major flaming hoops to get to this point. I was following the excellent [setup guide]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O") I found here when I ran into file system recommendations I didn't have in place. I guess most would be content setting it up to save recorded files on a EXT3 partition, but I wanted this right on my very old Athlon XP 2600+ machine, to squeeze out whatever performance I can get. I had a spare 120gig drive and wanted to put the recorded data on it, leaving my main drive alone.

I'm a major noob at this. Windows all my life and all that. I spent over a whole day (3 hour nap mind you) researching, trying, tearing my hair out, trying to create an XFS file system partition and mount it, and make sure it STAYS mounted after a reboot (big issue there). I took notes so I wouldn't forget if it was needed again, and here I am. MythTV using a PVR-150, recording video to my XFS partition on my second drive, but alas! I didn't have lineup channel guide data. I was so upset, and felt I had to go through all that again.

Another 3-4 hours Googling, and I happened upon this thread. Did what was prescribed, and it works! I watched some recordings on my laptop via raw files accessed through a network drive I set up in Windows. I still can't get the MythTV windows client to work because of problems accessing my database on my Linux machine. No problem! I'll just google the crap out of that issue, and I'm sure the great people here have found an answer I have yet to read.

Thanks to all that contributed! It's what makes this Ubuntu community so rich and grand! The more I read, the further from Windows I venture, and that is just fine with me!

Hop

---

