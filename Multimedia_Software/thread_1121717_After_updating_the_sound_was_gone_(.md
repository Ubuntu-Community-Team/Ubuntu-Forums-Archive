---
title: "After updating the sound was gone :("
date: 2009-04-10
forum: Multimedia Software
---

### Post by ASM888 on 2009-04-10
After updating the sound was gone
Recently, after next &#1086;&#1073;&#1085;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103; ubuntu 8.10 the sound was gone.
In adjustments gnome there is no arrangement
Writes:
The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting ' Remove From Panel ' from the menu.
What to do?

---

### Post by markbuntu on 2009-04-10
Check in System/Administration/Users and Groups that your users and root are members of the following groups

pulse
pulse-rt
pulse-access

For some reason updates on Intrepid cause this problem for some people.

---

### Post by ASM888 on 2009-04-11
> **markbuntu said:**
> Check in System/Administration/Users and Groups that your users and root are members of the following groups

pulse
pulse-rt
pulse-access

For some reason updates on Intrepid cause this problem for some people.
I was included this groups, bud i don't have sound :(
it's my groups:
asmaster@user886:~$ groups
asmaster adm dialout cdrom plugdev lpadmin pulse pulse-access pulse-rt admin sambashare

thank you for advice.
P.S. sorry, if my english is bad..

---

### Post by markbuntu on 2009-04-11
In a terminal type

aplay -l

what does it say?

---

### Post by ASM888 on 2009-04-11
it's say:
asmaster@user886:~$ aplay -l
aplay: device_list:207: no soundcards found...

---

### Post by markbuntu on 2009-04-12
Hmmmm, go here for troubleshooting help. If basic trouleshooting does not help then try reinstalling alsa before doing anything drastic. There are directions for doing so in the post.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ASM888 on 2009-04-13
I was reinstaled alsa last weak, with the alsascript0.19...
but, gnome don't sea my sound card..

---

### Post by ASM888 on 2009-04-15
:p I was reinstaled alsa 1.0.19, it's help me. I have sound now!!!
Thanks!

---

