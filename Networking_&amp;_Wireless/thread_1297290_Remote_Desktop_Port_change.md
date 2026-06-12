---
title: "Remote Desktop Port change"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by unclejac on 2009-10-21
Hello :) 

Anyone remember how to change the Remote Desktop Port number to something different? 

I am certain I did this before on Intrepid. However there is no Port choice on the Jaunty Remote Desktop Preferences.

I also have myself convinced I edited a file before :S

Anyway Thanks in advance to anyone who has a better memory than me :D

---

### Post by Fodox on 2009-11-04
I have the same problem with Ubuntu 9.10, when I activated Remote Desktop the field to change the port is vanished.
I tryed to launch in the terminal:
sudo gconf-editor

then I changed in desktop -> gnome -> remote access the values of:
alternative_port=5901
use_alternative_port=<checked>

After restart, my pc continue to accept connection on port 5900.
Why?!

---

### Post by swirlypillow on 2009-11-11
Same exact thing here.  Used sudo gconf-editor to enable alternate port and set the port to something else.  I have No-ip running on the system so i can check the ports externally, and even though I've set the port to something else, checked the box and even rebooted the system it doesn't enable the alternate port and I still have to use 5900.  What up with that?

---

### Post by andrewbrown22 on 2009-12-24
I would like to know if anyone has found a solution to this problem yet.  I'm interested in building myself a HTPC based on an Atom chip and Ubuntu 9.10 running XBMC, but I would really like to be able to (with ease) remote desktop into this computer to control a few things.

---

### Post by andrewbrown22 on 2010-01-21
Bump. 

Anyone?

---

### Post by andrewbrown22 on 2010-01-27
Surely a solution/work around for this has come to pass by now. 

Anybody know?

---

### Post by MikeTheGeek! on 2010-03-14
How to get Ubuntu 91.0 Remote Desktop to work with alternate port
 

 Finally I have found the answer. I have seen several responses that were partially correct in the fix for changing the Remote Desktop port from the standard 5900 to another port. But when applied and the system was rebooted it would always revert back to port 5900.  
 

 The Fix:
 
[LIST=1]
[*]Open Gnome Configuration Editor  -     gconf-editor (can use ALT-F2 for quick access)
[*]Open Folder Desktop
[*]Open Folder Gnome
[*]Open Folder remote_access
[*]In right had pane:
[*]Right Click on alternative_port     and click on edit key
[*]Enter desired port number
[*]Click OK
[*]Again Right Click on     alternative_port and click on Set as Default [COLOR=DarkSlateBlue](this is important)[/COLOR]
[*]Enter the Admin password for     Authentication and click on Authenticate
[*]Right click on     authentication_methods and edit key – and set to vnc
[*]Put a check in the check box for     enabled
[*]Put a check in the check box for     use_alternative_port
[*]Click on File and Close Window
[*]Reboot the system
[/LIST]
  This should allow you to use an alternative port for your vnc access and not be reset to the original 5900 during reboots.   
 

 Thanks to Dave's Tech Blog for most of the basics:  
 [http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/](http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/)
 

Let's hope they return the Advanced tab back to the Remote Desktop Preferences settings in the next version. 

 

MikeTheGeek!

---

### Post by andrewbrown22 on 2010-03-14
This worked great, thanks!

---

### Post by heian on 2011-09-11
Hi,

I'm still wondering,

Why is it still not possible in remote desktop to set a port number that users prefer?

Standard port is 5900, but if people have more than one pc connected to the internet ( a working- and test pc :) ) then they run in trouble. Make some same like the program Transmission by example.

heian

---

### Post by davidstoll on 2011-09-29
This procedure does not seem to work for me.  I've tried it on two different computers.

It only seems to want to use 5900.

---

### Post by diablo75 on 2011-09-30
Edit:  Woops, just tried the little step by step that's a few posts back and that fixed the problem.  Ironically, that's my blog he linked to in the post (I'm laughing my *** off in embarrassment now).  It would however seem to take a few more steps than I remember writing about in that post so I might as well update it.

---

### Post by davidstoll on 2011-10-01
> **diablo75 said:**
> Edit:  Woops, just tried the little step by step that's a few posts back and that fixed the problem.  Ironically, that's my blog he linked to in the post (I'm laughing my *** off in embarrassment now).  It would however seem to take a few more steps than I remember writing about in that post so I might as well update it.

Well, what part did you miss?  Maybe I'm missing the same thing.

---

### Post by diablo75 on 2011-10-01
> **davidstoll said:**
> Well, what part did you miss?  Maybe I'm missing the same thing.

The steps I was skipping were anything involving the right-clicking on a key and then clicking "Set as default".  I also was not adding in a check mark for the "enabled" parameter, and the authentication method was originally set to "none".  I added in "vnc" to that so the line now says [vnc,none].

In the past all I was doing was setting the alternate port number and adding a checkmark next to "use_alternative".

Edit:  I've updated my blog he linked to so the what needs to be done is made very clear and in order from top to bottom.  Look just past the screenshot of the gconf window.  [http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/](http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/)

---

### Post by davidstoll on 2011-10-01
> **diablo75 said:**
> The steps I was skipping were anything involving the right-clicking on a key and then clicking "Set as default".  I also was not adding in a check mark for the "enabled" parameter, and the authentication method was originally set to "none".  I added in "vnc" to that so the line now says [vnc,none].

In the past all I was doing was setting the alternate port number and adding a checkmark next to "use_alternative".

Edit:  I've updated my blog he linked to so the what needs to be done is made very clear and in order from top to bottom.  Look just past the screenshot of the gconf window.  [http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/](http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/)

yeah, wow, that just doesn't work for me.  Right clicking and all.  It looks the same except the encryption method which just shows vnc.  Mine shows none,vnc, but I also tried to remove none...still no luck.

---

### Post by davidstoll on 2011-10-02
Is there a command line input that I can use to enable all the settings?

In Winblows, you can make a registry file and export/import it.  I would be forever grateful if someone can make a script/file or show me the command line version.

:)

---

### Post by deerewright on 2012-01-23
Does not work for me! I have tried changing the alternative_port key to 5901, 1, 5555. None of them work. It will only use 5900, not matter what is set in the key.

Anyone have a solution?

---

### Post by diablo75 on 2012-01-23
> **deerewright said:**
> Does not work for me! I have tried changing the alternative_port key to 5901, 1, 5555. None of them work. It will only use 5900, not matter what is set in the key.

Anyone have a solution?

Have to jump in and join the bandwagon because last time I tried (a long time ago) I was still having bad luck.  The PC I used to use 5900 for died so I've just been working off a different computer (my main one) with the 5900 port instead.  Anyway, I've not been able to figure out how to fix this either.

---

