---
title: "Wait for Sound System to respond step to solution?"
date: 2010-06-06
forum: Multimedia Software
---

### Post by deckoff on 2010-06-06
After I got this Wait for Sound System message, I started to play with my laptop ,read a few solutions( which did not help) and reinstalled a few times, I found this:
If I move my home folder after a clean install, only Xmarks added to firefox, nothing more, to  a new drive I got the message. When I reverted to default everything worked fine - no error message.
To move the home folder I copy pasted the hidden files the installation created. docs, audio and other visible folders were there from the previous installation. 
Then I added [FONT=monospace]to [/FONT] “/etc/fstab” 
/dev/sda2     /home ntfs nodev,nosuid 0 2....
I use IBM THINKPAD X40. 
I will install updates and see if affects the sound system message

---

