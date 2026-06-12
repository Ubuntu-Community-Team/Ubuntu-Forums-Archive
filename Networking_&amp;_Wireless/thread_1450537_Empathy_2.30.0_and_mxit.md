---
title: "Empathy 2.30.0 and mxit"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by thenailedone on 2010-04-09
Hiya,

I cannot seem to set up my mxit account on Empathy 2.30.0... just keeps on saying connecting and nothing...  Is there a special why I should put my mobile number?

Regards
Neil

---

### Post by thenailedone on 2010-04-24
Empathy 2.30.0.1 and still no MXIT... oh and no replies either :/

On Pidgen you get the option to add a "anti-bot" code the first time you set up the client that I am not getting with Empathy, can this be the problem?

---

### Post by thenailedone on 2010-04-26
Well, it isn't working yet :/ (also no replies after just about two days)... switched to Pidgin, only problem is it doesn't integrate with the notification area in the same manner as Empathy :(

---

### Post by thenailedone on 2010-04-30
Now on the official release of Lucid Lynx and still no joy getting Empathy to connect to mxit... :(

---

### Post by unavenged on 2010-05-01
I seem to be having the same problem... Could it be something to do with the wap site it tries to connect to? When i use [http://www.mxit.com/wap](http://www.mxit.com/wap) then it says "Disconnected - network error"... But when i use [http://www.mxit.com](http://www.mxit.com) it just keeps saying "Connecting"?

---

### Post by unavenged on 2010-05-01
As far as i can see the mxit evo pc client for windows seems to be connecting to 41.191.124.10:9119 and that points to pc.stream.mxit.co.za.html, pcstream.mxit.co.za, and stream.mxit.co.za... I tried all 3 of the addresses with no luck even selected "Use http"

---

### Post by rudihawk on 2010-05-02
Can confirm that I am having the same problems. Using Empathy 2.30.0.1 

Cannot connect to my account. 

I would really like this feature as it is the only thing that's stopping me from using empathy.

---

### Post by thenailedone on 2010-05-02
Hi all,

Thanks for all the replies and for trying... the Pidgin client for Linux works well, and it also points to [www.mxit.com](www.mxit.com)... the difference thus far seems to be that as soon as the client in Pidgin is configured you get another options dialogue where you have to add an anti-bot code (enter the numbers in the image deal) and you must also select your country etc.  This does not happen when using Empathy and I think this is the main problem...

---

### Post by rudihawk on 2010-05-02
I wonder if the Mxit dev's will be planning on supporting empathy at some stage soon.

---

### Post by thenailedone on 2010-05-02
> **rudihawk said:**
> I wonder if the Mxit dev's will be planning on supporting empathy at some stage soon.

Well Mxit is one of the protocols so you would imagine that Empathy is supporting mxit?!

---

### Post by rudihawk on 2010-05-02
Perhaps we should file a bug report?

---

### Post by thenailedone on 2010-05-02
> **rudihawk said:**
> Perhaps we should file a bug report?

"You can do it!"

Lol, and if you don't I guess I can... Wonder if I did?  Can't remember doing it :p

---

### Post by thenailedone on 2010-05-02
> **thenailedone said:**
> "You can do it!"

Lol, and if you don't I guess I can... Wonder if I did?  Can't remember doing it :p

Bug reported :D... now we wait... [IMG]http://www.overclock.net/images/smilies/ninja.gif[/IMG]

---

### Post by Supa_Fly on 2010-05-03
I'm also having this problem. Hopefully your bug report gets addressed soon :-)

---

### Post by Supa_Fly on 2010-05-03
I see thenailedone [submitted a bug report]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/573857"). Will help if other people respond to the "does this bug affect you" option at the top of the page (just above 'Bug Description').

---

### Post by m4tic on 2010-05-03
also not working on a fresh 10.04 install, facebook on empathy also does not work. anyone else has that problem?

---

### Post by MJWitter on 2010-05-04
Facebook works fine, could it be your username settings?  I know of a few people who had trouble with that.  The username in the Empathy settings is that which you choose on the Facebook My Account page.

---

### Post by thenailedone on 2010-05-04
> **MJWitter said:**
> Facebook works fine, could it be your username settings?  I know of a few people who had trouble with that.  The username in the Empathy settings is that which you choose on the Facebook My Account page.

:) Was just going to answer the same thing... can see mxit is a from South Africa... it's only us that worry about using it :P

---

### Post by kleinric on 2010-05-05
hey guys, 

its a pity its not up and working yet :( in the meantime i got pidgin installed as well and have my mxit account on that which works fine. if u install pidgin-libnotify then it integrates with the new chat menu thing too... 

sudo apt-get install pidgin pidgin-libnotify

ric

---

### Post by rudihawk on 2010-05-06
Yea, pidgin is a good way to connect to mxit, would be better if I didn't have to install another IM program if empathy supposedly supports it by default. 

I have also marked the bug as affecting me. Doesn't seem to be much happening on launchpad though regarding the bug.

---

### Post by thenailedone on 2010-05-07
> **rudihawk said:**
> Yea, pidgin is a good way to connect to mxit, would be better if I didn't have to install another IM program if empathy supposedly supports it by default. 

I have also marked the bug as affecting me. Doesn't seem to be much happening on launchpad though regarding the bug.

Assuming it isn't very high on the priority list...

---

### Post by rudihawk on 2010-05-07
> **thenailedone said:**
> Assuming it isn't very high on the priority list...

It should be, it is a protocol that is included by default and just doesn't work.

---

### Post by thenailedone on 2010-05-07
> **rudihawk said:**
> It should be, it is a protocol that is included by default and just doesn't work.

Thing is it can be a problem with Empathy and not necessarily Ubuntu...

---

### Post by rudihawk on 2010-05-07
> **thenailedone said:**
> Thing is it can be a problem with Empathy and not necessarily Ubuntu...

Well it might be Ubuntu's fault. They have included an app with support for a protocol when that doesn't work it reflects badly on Ubuntu as is an alternative which DOES support mxit as well and functions correctly. 

I guess it is a fault with empathy and it wouldn't be a problem if they had tested it properly.

---

### Post by thenailedone on 2010-05-13
Well... just an update to let you know the bug is not even assigned yet... guess it isn't important enough...

---

### Post by rudihawk on 2010-05-13
Is there anyway we can get some official feedback on this issue?

---

### Post by unavenged on 2010-05-17
Here is a link to someone that you can ask if it is an empathy problem? [http://live.gnome.org/GuillaumeDesmottes](http://live.gnome.org/GuillaumeDesmottes)

---

### Post by thenailedone on 2010-05-17
> **unavenged said:**
> Here is a link to someone that you can ask if it is an empathy problem? [http://live.gnome.org/GuillaumeDesmottes](http://live.gnome.org/GuillaumeDesmottes)

Cool,

Sent an e-mail, now we wait...


Neil

---

### Post by cassidy on 2010-05-18
The best thing you can do to help addressing this issue is to open a telepathy-haze bug report on bugs.freedesktop.org and attach haze log when trying to connect.
You can get logs from the Help - Debug menu.

---

### Post by thenailedone on 2010-05-18
> **cassidy said:**
> The best thing you can do to help addressing this issue is to open a telepathy-haze bug report on bugs.freedesktop.org and attach haze log when trying to connect.
You can get logs from the Help - Debug menu.

Hey you other South Africans... your turn :p ... I am on Fedora now ;)

---

### Post by Beanmonster on 2010-05-20
I have the same problem... posted in the [mxit forums]("http://forum.mxit.com/viewtopic.php?f=3523&t=24235&start=0"). Hopefully we can spark some interest in the issue :)

**_---Edit---_**
This is requested from the user using purple_request_fields(), telepathy-haze doesn't implement that API.
 ([http://git.collabora.co.uk/?p=telepathy-haze.git;a=blob;f=src/request.c](http://git.collabora.co.uk/?p=telepathy-haze.git;a=blob;f=src/request.c))

---

### Post by rudihawk on 2010-05-20
I've also added a post to that thread! 

Lets see if we can get some action on this.:P

---

### Post by rudihawk on 2010-05-20
Update:

[quote=Launchpad]Empathy 2.30.0.1 on Lucid Lynx.

 ProblemType: Bug
 DistroRelease: Ubuntu 10.04
 Package: empathy 2.30.0.1-0ubuntu3
 ProcVersionSignature: Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2
 Uname: Linux 2.6.32-21-generic i686
 Architecture: i386
 Date: Sun May  2 21:51:29 2010
 InstallationMedia: Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
 ProcEnviron:
-  LANG=en_US.utf8
-  SHELL=/bin/bash
+  LANG=en_US.utf8
+  SHELL=/bin/bash
 SourcePackage: empathy

** Also affects: empathy
  Importance: Undecided
      Status: New

** Changed in: empathy
      Status: New => Confirmed

** Changed in: empathy (Ubuntu)
      Status: New => Confirmed

** Also affects: telepathy-haze
  Importance: Undecided
      Status: New

** Changed in: telepathy-haze
      Status: New => Confirmed

[/quote]

Seems like there has been some activity. Bug is still unassigned though. Although it has been confirmed which is a good sign.

---

### Post by thenailedone on 2010-05-21
Well Pidgin does all I need and as I am on Fedora now its all I need :)

---

### Post by rudihawk on 2010-05-21
> **thenailedone said:**
> Well Pidgin does all I need and as I am on Fedora now its all I need :)

Agreed. I'm still using Pidgin too. 

:guitar:

---

### Post by ufu1 on 2010-07-15
Apparently Fedora is moving to empathy to ;)

I don't understand this stuff but been assigned

Affects       Status       Importance       Assigned to       Milestone                                                [                                ]("https://bugs.launchpad.net/empathy/+bug/573857/+editstatus")                                      &#8201;                                 [Empathy]("https://bugs.launchpad.net/empathy")                                        Edit                              

                                 [Confirmed]("https://bugs.launchpad.net/empathy/+bug/573857/+editstatus")         [           [IMG]https://bugs.launchpad.net/@@/edit[/IMG]         ]("https://bugs.launchpad.net/empathy/+bug/573857/+editstatus")       
                                Unknown       
                                                                                                 [gnome-bugs  #619275]("https://bugzilla.gnome.org/show_bug.cgi?id=619275")         
                                      
                                                                           Affecting:       [Empathy]("https://bugs.launchpad.net/empathy")                 Filed here by:       [Michael Heyns]("https://launchpad.net/%7Emike-bean-heyns")                 When:                2010-05-20                                                                                           Project                                                     Chat app, and Telepathy user interface                                                                             Status                             Importance                                         Confirmed                               Unknown                                                              Assigned  to                                *unknown*                                            Remote  Watch                                                   None, the status of the bug is updated manually.                               None, the status of the bug is updated manually.                               GNOME Bug Tracker [#619275]("https://bugzilla.gnome.org/show_bug.cgi?id=619275")                               URL: 
                                            The information about this bug in Launchpad is         automatically pulled daily from the remote bug.                                   This information was last pulled               **2 hours ago**.                                                       
               Comment  on this change (optional)            
                              E-mail me about changes to this bug report            
   
           
                                                     [                                ]("https://bugs.launchpad.net/telepathy-haze/+bug/573857/+editstatus")                                      &#8201;                                 [Telepathy Haze]("https://bugs.launchpad.net/telepathy-haze")                                        Edit                              

                                 [Confirmed]("https://bugs.launchpad.net/telepathy-haze/+bug/573857/+editstatus")         [           [IMG]https://bugs.launchpad.net/@@/edit[/IMG]         ]("https://bugs.launchpad.net/telepathy-haze/+bug/573857/+editstatus")       

                                Undecided       
                                   &#8201;                                                    Unassigned                                                Edit                                           

                  
                                                  Affecting:       [Telepathy  Haze]("https://bugs.launchpad.net/telepathy-haze")                 Filed here by:       [Michael Heyns]("https://launchpad.net/%7Emike-bean-heyns")                 When:                2010-05-20                        Confirmed:                2010-05-20                                                                                      Project                                                     Telepathy Haze                                                                             Status                             Importance                                            New Incomplete Opinion Invalid Confirmed In Progress Fix Committed Fix Released  
  
                               Undecided                                                              Assigned to                                                                                           Nobody                                                                            Me                                                                                 Remote Watch                                                   None, the status of the bug is updated manually.                               None, the status of the bug is updated manually.                               GNOME Bug Tracker [#619275]("https://bugzilla.gnome.org/show_bug.cgi?id=619275")                               URL: 
                                            The information about this bug in Launchpad is         automatically pulled daily from the remote bug.                                 
               Comment on this change (optional)            
                              E-mail me about changes to this bug report            
   
           
                                                     [                                ]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/573857/+editstatus")                                                                       [empathy  (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/empathy")                                        Edit                              
                                 [Confirmed]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/573857/+editstatus")         [           [IMG]https://bugs.launchpad.net/@@/edit[/IMG]         ]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/573857/+editstatus")       

                                Undecided       
                                   &#8201;                                                    Unassigned                                                Edit

---

### Post by rudihawk on 2010-07-15
Please can someone fix the problem! :D

---

### Post by cobolt01 on 2011-04-06
Haha still not working in 2.32.1

time for somebody who really wants mxit on empathy to actually do it. The protocol should at least be removed from the gui list imo. It's sloppy.

---

### Post by rudihawk on 2011-04-08
> **cobolt01 said:**
> Haha still not working in 2.32.1

time for somebody who really wants mxit on empathy to actually do it. The protocol should at least be removed from the gui list imo. It's sloppy.

Agreed.

Make it work, or remove it! :D

---

### Post by rudihawk on 2011-05-31
So does anyone have any feedback regarding this issue?

---

### Post by Steve Kroon on 2012-02-14
Still broken in 3.2.0.1.

But FYI, it seems the design of a solution is now getting attention - see the discussion at [https://bugs.freedesktop.org/show_bug.cgi?id=32125](https://bugs.freedesktop.org/show_bug.cgi?id=32125) .

---

### Post by rudihawk on 2012-02-14
> **Steve Kroon said:**
> Still broken in 3.2.0.1.

But FYI, it seems the design of a solution is now getting attention - see the discussion at [https://bugs.freedesktop.org/show_bug.cgi?id=32125](https://bugs.freedesktop.org/show_bug.cgi?id=32125) .

Thanks for bringing this up! 

Glad to see they are finally taking notice.

---

