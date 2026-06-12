---
title: "Nvidia resolution settings - no can save"
date: 2009-07-29
forum: Multimedia Software
---

### Post by billzinn on 2009-07-29
No doubt, this may have already been addressed (in some part) within this forum, but I guess I'm having problems locating a 'fix' for this easily...
Yes, we are relative 'noobs' as re: Ubuntu Linux (Jaunty Jackelope), although we're 'fairly capable' as regards hardware (normally) under Windows... 
But we also appreciate the *need* to 'go elsewhere' with an O.S. since Windows is becoming more of a problem than it's seemingly worth....
Since we ARE 'noobs', I guess we need 'guidance' in how to save our resolution settings with an Nvidia GeForce MX4000 video card (and since Linux has the reputation for working well with 'older hardware', our thought was to use this old workstation as a 'test bed').
This system is an MSI KM400 mobo with 1 GB RAM, a 'dedicated' 80 GB IDE hard disk solely for Ubuntu (dual booting XP Pro from another 80GB disk), Sony DVD-R/W, and the aformentioned Nvidia MX4000 (64 MB single VGA w/ s-video output).
Originally, the Ubuntu system was installed using the onboard S3 video, but we had problems getting even 800 x 600 with that so we grabbed this MX 4000 'off the shelf'..
 
We have only a single monitor (CRT) connected to the VGA and want to run 1024 x 768 resolution, but the drivers we are using (ENVY) constantly 'default' to 800 x 600 and we can't seem to 'save' the changes using the 'manufacturers controls' (Ubuntu message when we alter video settings).  
When we choose to 'save settings', we get the 'usual' message re: unable to parse xconf... which obviously must mean we do not have rights to 'overwrite' a "system protected" file (xorg.conf ) - correct?.
So what's the 'secret' in how to save the new resolution settings?  We've tried the "sudo nvidia-config" inside of terminal - just as we've tried "sudo nvidia-settings"...
Also moved and renamed xconfig - but STILL get the same error.
So what are we doing wrong, here? 
 :confused:   (and I thought I KNEW hardware... hmph..)
 
Specific instructions help us noobs, y'know..?

---

### Post by doas777 on 2009-07-29
are you prompted for a password when you open nvidia settings?
if not, hit Alt+F2 and enter
```
gksu nvidia-settings
```then you shoudl be able to save and use the "Save to X configuration" button.

you can edit your launcher for nvidia-settings to use the command above if you need to use it often.

the "Unable to parse" may mean that the file has bad contents. if absolutely needed, you can reset it to default by running this command in a terminal:
```
sudo dpkg-reconfigure -p High xserver-xorg
```
after than though, you will have to reinstall the restricted drivers and reboot before continuing. 

good luck

---

### Post by billzinn on 2009-07-29
Well... we _are_ asked for a password when we 'sudo' - is that what you're referring to?
I'll try what you suggest and re-post with results... (as soon as I get done with this 'hosed' Windows XP box...  again... 'massaging' Windows is all I do, it seems)

---

### Post by billzinn on 2009-07-29
OH - and BTW:  Your suggestion that xconf has errors...
At one point we DID get an error saying "line 31 contains an error - 'disable' is invalid entry" - but 'looking' at xconf seems to have nothing in line 31 - and I mean NOTHING.  The line is 'empty"...(?) so....
Hmmm.... ANOTHER line 31...? somewhere...?

---

### Post by doas777 on 2009-07-29
i think the line numbers may not include comments and whitespace. depends on the parser I guess. if you copy the document, to another gedit window, and delete the commends and whitespace lines, is there a 'disable' on line 31 now?

---

### Post by doas777 on 2009-07-29
> **billzinn said:**
> Well... we _are_ asked for a password when we 'sudo' - is that what you're referring to?
I'll try what you suggest and re-post with results... (as soon as I get done with this 'hosed' Windows XP box...  again... 'massaging' Windows is all I do, it seems)


sudo and gksu are basically the same thing, but sudo usually isn;t safe for GUI apps, so they created gksu for elevating gui apps.

---

