---
title: "VMC software from Betavine{ vodafone mobile connect re:Betavine Connection Manager}"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by alexfish on 2010-08-08
[FONT=Verdana][SIZE=2]**VMC software from Betavine{ vodafone mobile connect re:Betavine Connection Manager}** : whilst for some systems and devices in may in part work , however be prepared for[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]**Network Manager** to no longer recognising the device . if you encounter problems after installing this software , if not to late {un-install and repair your system,**if you can find all the bits:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]** part of it look in synaptic bcm,  then you will UNDERSTAND what it does to the SYSTEM **[/SIZE][/FONT][FONT=Verdana][SIZE=2]} Best advice I can give "**DON'T INSTALL VMC** ", or do so at your own risk

**this software is irresponsible**:THIS thread will remain in place until as such time **Betavine and its developers rectify**, the software , and also get the software to use a linux system in a responsible manner: 
[/SIZE][/FONT]

---

### Post by alexfish on 2010-08-08
If you have linked to this thread from the " how to mobile broadband connections. 
this post is been sent via a system with conked Dbus , and usb_mode switch ,caused by by the above software

As regards to betavine there could be thousands of users wondering what has gone wrong with there system, It is fortunate that I can get around these issues , for the average desktop user this will not be the case.

In recent weeks I have noted numerous post relating to this{ Just as well they have an alternate means of communicating} perhaps Betavine could also look them up

[http://ubuntuforums.org/showthread.php?t=1543407](http://ubuntuforums.org/showthread.php?t=1543407)

   	 	 	 	 	 	  

 [http://ubuntuforums.org/showthread.php?t=1510312&highlight=installed+vmc](http://ubuntuforums.org/showthread.php?t=1510312&highlight=installed+vmc)
 

 [http://ubuntuforums.org/showthread.php?t=1405091&highlight=installed+vmc](http://ubuntuforums.org/showthread.php?t=1405091&highlight=installed+vmc)
 

 [http://ubuntuforums.org/showthread.php?t=1371393&highlight=installed+vmc](http://ubuntuforums.org/showthread.php?t=1371393&highlight=installed+vmc)
 

 [http://ubuntuforums.org/showthread.php?t=814561&highlight=installed+vmc](http://ubuntuforums.org/showthread.php?t=814561&highlight=installed+vmc)
 
alexfish

---

### Post by bamabaso@gmail.com on 2010-08-09
I support this post, the BCM/VMC soft. is not stable. Please view my reply in this forum 
[http://ubuntuforums.org/showthread.php?t=1543407&page=2](http://ubuntuforums.org/showthread.php?t=1543407&page=2)

---

### Post by alexfish on 2010-08-09
if you decide to uninstall  

remove bcm  
remove wader-core


OR 

[SIZE=3]**sudo apt-get --purge remove bcm**[/SIZE]

reinstall modemmanager
reinstall usb-modeswitch if required / from safe source
reinstall usb-modeswitch data if required / from safe source

or if not required
remove usb-modeswitch betavine
remove usb-modeswitch-data betavine

also search file " .bcm " set your file browser to show hidden files 

**then use Ubuntu Teak or similar to get rid of the rest**
test your system

if not working try

remove python-messaging : if installed by betavine

if still experiencing problems feel free to post 

IE if your only connection was mobile broadband how can this be resolved

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

### Post by pmarti on 2010-08-12
> **alexfish said:**
> 
**this software is irresponsible**:THIS thread will remain in place until as such time **Betavine and its developers rectify**, the software , and also get the software to use a linux system in a responsible manner:

alexfish, talking about being responsible, wouldn't have been more appropriate to contact the BCM developers and let them know of your problems instead of spreading FUD?

I am one of the BCM developers and we never heard from you or your problems. This is not the way to go in open source alex.

VMC has been completely revamped (BCM) and it is possible that there are some open bugs here and there, but:
 a) We haven't released a final version yet, thus we are not claiming is bug free. If you install an alpha/beta software and it does not work, you should report the bugs instead of whining and discouraging other users of trying our work.
 b) If bugs don't get reported to us, the final release will contain them.

Some of the "bugs" that you mention in your posts have nothing to do with VMC/BCM. For example, Firefox and the infamous "work offline". That's a side effect of having NetworkManager as the one to ask whether we are connected or not. As VMC starts its connections outside NM, NM thinks we are not connected (despite the fact that we are) and thus Firefox/pidgin won't work. THAT'S NOT VMC/BCM's FAULT.

Things to note:
 1) No version of VMC 2.x is supported on jaunty or later
 2) BCM integrates with NetworkManager (using its DBus interfaces), so our users won't suffer from the above problem. No third party connection managers that don't implement NM interfaces can operate without the infamous firefox/pidgin offine bug being seen.

Software like ntrack will (hopefully) sort out this situation, read my rant about the topic here:

[http://minimoesfuerzo.org/2010/03/12/testing-ntrack/](http://minimoesfuerzo.org/2010/03/12/testing-ntrack/)

alex: Change your attitude... pronto!

---

### Post by alexfish on 2010-08-12
> **pmarti said:**
> alexfish, talking about being responsible, wouldn't have been more appropriate to contact the BCM developers and let them know of your problems instead of spreading FUD?

I am one of the BCM developers and we never heard from you or your problems. This is not the way to go in open source alex.

VMC has been completely revamped (BCM) and it is possible that there are some open bugs here and there, but:
 a) We haven't released a final version yet, thus we are not claiming is bug free. If you install an alpha/beta software and it does not work, you should report the bugs instead of whining and discouraging other users of trying our work.
 b) If bugs don't get reported to us, the final release will contain them.

Some of the "bugs" that you mention in your posts have nothing to do with VMC/BCM. For example, Firefox and the infamous "work offline". That's a side effect of having NetworkManager as the one to ask whether we are connected or not. As VMC starts its connections outside NM, NM thinks we are not connected (despite the fact that we are) and thus Firefox/pidgin won't work. THAT'S NOT VMC/BCM's FAULT.

Things to note:
 1) No version of VMC 2.x is supported on jaunty or later
 2) BCM integrates with NetworkManager (using its DBus interfaces), so our users won't suffer from the above problem. No third party connection managers that don't implement NM interfaces can operate without the infamous firefox/pidgin offine bug being seen.

Software like ntrack will (hopefully) sort out this situation, read my rant about the topic here:

[http://minimoesfuerzo.org/2010/03/12/testing-ntrack/](http://minimoesfuerzo.org/2010/03/12/testing-ntrack/)

alex: Change your attitude... pronto!

                                 Hi pmarti
 

 [**Welcome to the Forums - Introduce yourself here**]("http://ubuntuforums.org/showthread.php?t=1451097")
 

 can I  suggest this
 

 if the software is beta could it have a button on the gui labled {uninstall} or does it already have one , also some where a help menu stating what to do if it goes wrong {bearing in mind the user may not have a network connection}
 

 if it does not have these features , could you do it pronto
 

 regards
 

 alexfish

OH forgot did you Know Not All Dongles Require usb_mode switch

---

### Post by pmarti on 2010-08-13
> **alexfish said:**
> Hi pmarti

 can I  suggest this

 if the software is beta could it have a button on the gui labled {uninstall} or does it already have one , also some where a help menu stating what to do if it goes wrong {bearing in mind the user may not have a network connection}
 
 if it does not have these features , could you do it pronto

 regards

 alexfish

OH forgot did you Know Not All Dongles Require usb_mode switch

Thing to note:

a) No sane OSS software provides an uninstall button, you have apt-get remove and dpkg --purge just for that.
b) You are not doing any good to OSS being arrogant, instead of apologizing for spreading FUD against a beta software, now you ask for a useless feature... Do you really think that open source works like this?
c) BCM supports more than 60 dongles, many of them require usb-modeswitch, thus is a dependency... What's your point? Rhythmbox has libpod as a dependency and I don't own an iPod.

It deeply worries me that someone with this ideas is giving advice to n00b Ubuntu users. Alex, reconsider your attitude and take a pill pronto.

---

### Post by alexfish on 2010-08-13
I am not getting into a flame war this is not the place

However

I could show you how to implement the above features

I could show you how to check for dependencies when of similar are on the system

I could show you how to implement these dependencies if the software requires them

and I certainly don't need to any pills as of yet

---

### Post by pmarti on 2010-08-13
> **alexfish said:**
> I am not getting into a flame war this is not the place

If you start a thread like you started this one, be ready for some heat

> **alexfish said:**
> 
However

I could show you how to implement the above features

I could show you how to check for dependencies when of similar are on the system

I could show you how to implement these dependencies if the software requires them

and I certainly don't need to any pills as of yet

Alex, we don't need that kind of help. What we need are users that report bugs and try to improve the general OSS ecosystem.

---

### Post by alexfish on 2010-08-13
hi

can I ask a question , I will be polite

as for Ubuntu it may be possible to open a launchpad account and register for a PPA

the debian package (software) could be registered there so any feed could also comeback from that direction

I apologies if you have already done so.

[FONT=Verdana]
[/FONT]regards
alexfish

Betavine    	 	 	 	 	[  Bug 	Tracker]("https://forge.betavine.net/tracker/?atid=121&group_id=12&func=browse")
[LIST]  	
[/LIST]
 

a vodafone user since the days of first vodafone mobile phone

---

### Post by PaulReaver on 2010-09-05
> **alexfish said:**
> [FONT=Verdana][SIZE=2]**VMC software from Betavine{ vodafone mobile connect re:Betavine Connection Manager}** : whilst for some systems and devices in may in part work , however be prepared for[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]**Network Manager** to no longer recognising the device . if you encounter problems after installing this software , if not to late {un-install and repair your system,**if you can find all the bits:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]** part of it look in synaptic bcm,  then you will UNDERSTAND what it does to the SYSTEM **[/SIZE][/FONT][FONT=Verdana][SIZE=2]} Best advice I can give "**DON'T INSTALL VMC** ", or do so at your own risk

**this software is irresponsible**:THIS thread will remain in place until as such time **Betavine and its developers rectify**, the software , and also get the software to use a linux system in a responsible manner: 
[/SIZE][/FONT]
funny??? I installed the latest version of betavine connection manager on ubuntu lucid and all of my huawei, zte and option modems are NOW recognized by network-manager,   actually some modems that didn't work started working with nm-applet because vodafone provided a pre-done usb modeswitch config file.
  
how else are people supposed to send sms text's and top-up vodafone mobile broadband without betavine connection manager? no other software on linux provides these features.  It even works with non vodafone dongles.

I responded to a help query asking how to connect a vodafone k3765 to the internet, the obvious advice is to point in the direction of vodafone's open source software that would remedy the situation.
don't be sending me spam messages linking to your own "opinions" again.  
just plain rude.


[B]
big THANK YOU 2 VODAFONE for the software :)[/B]

---

### Post by lilraphael on 2010-10-18
Thanks a million for helping out after installing bmc which messed up my modem manager.

Cheers

---

### Post by Manjuvajra on 2010-10-22
I too had similar problems with network manager after installing Betavine software.  (I eventually discovered that after tweaking the config file I could use wvdial from a terminal - but this was a bit fiddly) 

I appreciate the efforts at Betavine to produce this useful program but it took quite a while to find this thread and sort things out as Alexfish suggested.

So thanks to all.

---

### Post by garybrlow on 2012-05-07
Is there still anybody reading this thread? BCM can be made to work with 11.10 but crashes with 12.04. Is anyone on Ubuntu Precise having this error?

--------------------------
Traceback (most recent call last):
  File "/usr/bin/bcm", line 105, in <module>
    main()
  File "/usr/bin/bcm", line 71, in main
    from wader.bcm.controllers.main import MainController
  File "/usr/lib/python2.7/dist-packages/wader/bcm/controllers/main.py", line 68, in <module>
    from wader.bcm.messages import get_messages_obj, is_sim_message
  File "/usr/lib/python2.7/dist-packages/wader/bcm/messages.py", line 25, in <module>
    from wader.common.oal import get_os_object
ImportError: No module named oal
--------------------------
Xubuntu 12.04

A suggestion or solution would be most helpfull since I use bcm for SMS and SIM Data Management (SIM Addressbook & SMS).

---

### Post by alexfish on 2012-05-07
> **garybrlow said:**
> Is there still anybody reading this thread? BCM can be made to work with 11.10 but crashes with 12.04. Is anyone on Ubuntu Precise having this error?

--------------------------
Traceback (most recent call last):
  File "/usr/bin/bcm", line 105, in <module>
    main()
  File "/usr/bin/bcm", line 71, in main
    from wader.bcm.controllers.main import MainController
  File "/usr/lib/python2.7/dist-packages/wader/bcm/controllers/main.py", line 68, in <module>
    from wader.bcm.messages import get_messages_obj, is_sim_message
  File "/usr/lib/python2.7/dist-packages/wader/bcm/messages.py", line 25, in <module>
    from wader.common.oal import get_os_object
ImportError: No module named oal
--------------------------
Xubuntu 12.04

A suggestion or solution would be most helpfull since I use bcm for SMS and SIM Data Management (SIM Addressbook & SMS).

Best thing thing to do is report bugs to source . IE: Betavine,,
 part of the package  made it into the repos , "wader core" , don't know if it will help

For Huawei devices can Look here
[Huawei Mobile Broadband Devices (Ubuntu 12.04)]("http://ubuntuforums.org/showthread.php?t=1974458")

If want help about the Device connection problems RE: Ubuntu ,  Start new Thread in Network and Wireless.

---

### Post by drsrinivas294 on 2012-05-27
Unfortuantely I have installed VMC software from betavine and facing the problem of modem not being detected.
Tried to uninstall VMC as suggested by ALEXFISH but could not succeed.I am pasting the terminal output below.Please help me out

srinivasarao@srinivasarao-Laptop:~$ sudo apt-get --purge remove bcm
[sudo] password for srinivasarao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'bcm' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
srinivasarao@srinivasarao-Laptop:~$

---

### Post by oldos2er on 2012-05-27
Please start a new thread for your question.

---

