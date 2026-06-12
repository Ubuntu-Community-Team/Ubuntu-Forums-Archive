---
title: "zmodo security system client?"
date: 2012-01-25
forum: Multimedia Software
---

### Post by rebeltaz on 2012-01-25
I don't know if this is the right category or not, but I just got a Zmodo security system with DVR. The DVR is accessible through either an Android device or a Windows client application. I have an Android device (Entourage Pocket eDGe) and I can run the Windows app through a VirtualBox session, but I would like to be able to access this through Linux natively. 

I tried running the client through Wine. The version in the Ubuntu repository (1.2.2 I think?) got part way through the installation and then froze. I upgraded Wine to 1.2.3 and the installation completed, but when I try to run the program, my hard drive sits there showing constant activity, but the program never starts. I have to reboot the computer to get the hard drive to stop. No clue what it's doing.

Does anyone know how to either get the program to work in Wine, or of a native Linux application that will access the DVR?

---

### Post by huanix on 2012-02-04
I purchased the same system (DVR-H9124V) from woot last week and discovered two good ways to get it working in ubuntu:

The easy way is to run the DVRCMS.msi installer in wine. I got DVRCMS 1.1.0.6 from the zmodo website, but it may also be on the mini-cd that came in the box (I didn't look). Here's the current address for that zip file 

direct link to zip: [http://www.zmodo.com/downloader/index/download/file_id/1014/](http://www.zmodo.com/downloader/index/download/file_id/1014/)

The second and potentially better (more difficult) method is to use the zmodo DVR to feed a zoneminder system which is 100% linux compatible. A guy called Phoenix84 has figured out how to get that working over at the ZoneMinder forums:

[http://www.zoneminder.com/forums/viewtopic.php?f=9&t=18137](http://www.zoneminder.com/forums/viewtopic.php?f=9&t=18137)

Just a note, using ZoneMinder would require you to set up an additional video server that uses the zmodo DVR as a video feed. It would probably be a 4 or 5 hour project.

---

### Post by rebeltaz on 2012-02-05
I have Wine installed on my system and I had already tried both versions of the client software that came with my DVR. Both install just fine, but neither version will actually run, for some reason. 

Just for kicks, I went ahead and downloaded the version that you are using. It installed fine and to my surprise, it actually ran! Unfortunately, the login protocol must be different. There is no where on the login screen to input a username, only the password. I went ahead and tried all of the ports that are open on my DVR anyway, but :( sadly, no go...

BUT, it is encouraging that the software actually ran. Maybe I'll download all the client packages and see if I can find one that will run AND log in...

Thanks for that...

---

### Post by rebeltaz on 2012-02-11
Uhg. Not a single app on their web site will talk to the H8118 except for the application that comes with it, not even from within Windows :(

---

