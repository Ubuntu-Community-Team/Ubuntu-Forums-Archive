---
title: "Auto Rip CD"
date: 2011-01-11
forum: Multimedia Software
---

### Post by markturnip on 2011-01-11
I have a headless Ubuntu Server & would like to auto rip an audio CD to FLAC upon insert. 

I've tried this solution with ivman:
[http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html](http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html)

But ivman doesn't seem to detect when a CD is inserted. I'm using an external USB CD drive.

I've found another solution:
[http://www.monkeynet.ca/viewProject.php?project=daemonrip](http://www.monkeynet.ca/viewProject.php?project=daemonrip)

Which seems to work fine & import my CD upon insert. However it imports it as OGG. I've changed the daemonrip.conf file to change the encoder without any luck. 

I wonder if anyone has used this script & whether they've been able to import using FLAC?

Thanks. 
Mark

---

### Post by mc4man on 2011-01-11
I think you'd need to trial and error your conf line for flac if you want tags. (if it ultimately can at all

There'd be no problem getting it to encode to flac, something like this should work fine (also edit your encoder_extension = line to flac
```
# To rip using flac to create a flac file
encoder = flac --best %w

```
Myself use either abcde and or rubyripper to autorip from cd insertion, both can be set up fairly easy to do silently in background or in a visible terminal
(having a monitor I prefer either to open a temp terminal so as to monitor progress though certainly not required.

---

### Post by markturnip on 2011-01-11
Hello mc4man, Thanks for the response. 

I did try some trial and error, but it's quite difficult without any documentation nor much to go by in the script.

The code you've given works. However I prefer using ABCDE, would you mind explaining how you were able to autorip upon cd insertion?

Thanks.

---

### Post by mc4man on 2011-01-11
It would be beyond simple on a regular install (gui, ect), but I'm sure you can adapt to headless  - no experience here w/ that.

I use a modified abcde that I packaged up (abcde-nero), but the method shouldn't be any different.
what you need to do is make sure that whichever abcde conf you're using is set up as you wish, either the default one that's probably installed to /etc (/etc/abcde.conf) or possibly better one in your home dir. (~/.abcde.conf

The it's simply setting the default autorun option for audio cd's to run this command for silent/in background (what you'd want I'd think

abcde -N

What i use here is (obviously the -nero is just for here
gnome-terminal -e "abcde-nero -N"

Again on a gui to set is simple - in 'File Management > media > cd audio there is a dropdown - 'open with other application' > use a custom command
I think the command can be entered directly there, I've always just used a script in path (arip2), so I just use that name as the command
The script here is  simply 
#!/bin/bash
gnome-terminal -e "abcde-nero -N"

In your case I'm not sure if you can access File Management, if not then shouldn't be a problem.

Let me know if you don't see a way - basically a custom command creates a userapp.desktop and then that userapp.desktop is added to a line in ~/.local/share/applications/mimeapps.list
x-content/audio-cdda=
Ex. here - 3 choices - first listed is the default
> x-content/audio-cdda=userapp-arip2-O7G5OV.desktop;aud-cd.desktop;vlc-cd.desktop;
One can create a .desktop from scratch to accomplish the same, as seen above - the aud-cd.desktop and vlc-cd.desktop I created 
(are/can you work in a home dir.?

---

### Post by sudocode on 2011-02-23
Regarding the method described at sudocode.blogspot.com, I have since updated my set up to use halevt in place of ivman. Ivman does not work in current Ubuntu.

---

