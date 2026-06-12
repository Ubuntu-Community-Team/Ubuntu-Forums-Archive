---
title: "New Install Xbuntu 6.10 No VIDEO"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by Rich_li_ny on 2007-04-01
I just installed Xbuntu 6.10 using the alternate CD ISO.  

I am running it on a PII-300 mhz 
192 mb RAM
Itel AL440LX motherboard.
Unsure of video memory but its probably shared.  

System hung twice during installation but eventually completed.  When prompted by the installation I removed CD from tray and pressed ENTER to restart so system could configure (finalize) everything.   

Heres the problem:

System Boots.  
I get error message: "[17179569.184000] ACPI: Unable to locate RDSP"  and system contiunes with boot prorocess.

When it comes time for the Xbuntu logo and gui to display the monitor goes dead and LED on monitor goes from green to flashing amber (no video). 

When I press:  "Control + Alt + Backspace"  the LED on the monitor turns green for a sec and it attempts to do some thing but then just goes back into a dead state.


To try to solve the problem I exited to a command prompt to try to manually set my video mode.  This is what I did: 

Pressed  "Control + ALT + F1 to get to a command prompt.  On exit to a command prompt this is what is get:

Starting up ...
[17179569.184000] ACPI: Unable to Locate RSDP

usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600

Ubuntu 6.10 ubuntu tty1

Ubuntu login: _ 


Ok So it seems the 1024x768 isnt working with this and the 800x600 is fine (for a command prompt anyway)  So I log in and try to make a change but I am a total noob and having some problems.  This is what I tried to do next and it didnt work :( 

From the command prompt I typed: sudu dpkg-reconfigure xserver-xorg   
It didnt like this command.  

Anyway now I am stuck.  This is an older machine and I did have a puppy distro working on it with 1024x768 and 800x600.   

Can someone please tell me what I am doing wrong?    There has to be a command I can use to get a selection of video modes/resolutions, test them out and save them..  

Any help is greatly appreciated 

Rich

---

### Post by clarkej on 2007-04-07
> **Rich_li_ny said:**
> I just installed Xbuntu 6.10 using the alternate CD ISO.  

I am running it on a PII-300 mhz 
192 mb RAM
Itel AL440LX motherboard.
Unsure of video memory but its probably shared.  

System hung twice during installation but eventually completed.  When prompted by the installation I removed CD from tray and pressed ENTER to restart so system could configure (finalize) everything.   

Heres the problem:

System Boots.  
I get error message: "[17179569.184000] ACPI: Unable to locate RDSP"  and system contiunes with boot prorocess.

When it comes time for the Xbuntu logo and gui to display the monitor goes dead and LED on monitor goes from green to flashing amber (no video). 

When I press:  "Control + Alt + Backspace"  the LED on the monitor turns green for a sec and it attempts to do some thing but then just goes back into a dead state.


To try to solve the problem I exited to a command prompt to try to manually set my video mode.  This is what I did: 

Pressed  "Control + ALT + F1 to get to a command prompt.  On exit to a command prompt this is what is get:

Starting up ...
[17179569.184000] ACPI: Unable to Locate RSDP

usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600

Ubuntu 6.10 ubuntu tty1

Ubuntu login: _ 


Ok So it seems the 1024x768 isnt working with this and the 800x600 is fine (for a command prompt anyway)  So I log in and try to make a change but I am a total noob and having some problems.  This is what I tried to do next and it didnt work :( 

From the command prompt I typed: sudu dpkg-reconfigure xserver-xorg   
It didnt like this command.  

Anyway now I am stuck.  This is an older machine and I did have a puppy distro working on it with 1024x768 and 800x600.   

Can someone please tell me what I am doing wrong?    There has to be a command I can use to get a selection of video modes/resolutions, test them out and save them..  

Any help is greatly appreciated 

Rich

Rich,

This post 'Ubuntu 6.10 fresh install - video' may help you to boot with basic video:

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/998007193831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/998007193831)

good luck.

 JC

---

### Post by Rich_li_ny on 2007-04-10
JC,

Thank you for the link.  I'm working on it now :)

Rich

---

