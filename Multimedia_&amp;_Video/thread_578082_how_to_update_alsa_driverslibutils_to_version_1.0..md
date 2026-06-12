---
title: "how to update alsa drivers/lib/utils to version 1.0.15"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by karma_2burn on 2007-10-16
i have been having static issues with all media (audio and video players) and decided to attempt to update my alsa drivers to the latest version 1.0.15

i am still pretty green when it comes to these types of operations so "dummy proof" instructions/tips would be helpful

i located a procedure here in the forums: [http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268)

and after proceeding with the first command:  sudo /etc/init.d/alsa-utils stop      i was not able to get the following commands to work

i have downloaded the 3 relevant tarballs to my desktop

any help would be great - as i now have no audio because i don't even know how to undo my command: sudo /etc/init.d/alsa-utils stop

i am running fiesty and am unsure how to find out what my sound card is...

i would appreciate any help

---

### Post by skotadi on 2007-10-16
to get your sound working again, either restart or do this command:
```
sudo /etc/init.d/alsa-utils start
```

(I just sorta guessed on that command, but it should work)

to find out more about your sound card, go to system -> preferences -> hardware information.

It's quite verbose, but your soundcard should show up in the tree on that left pane.  Or perhaps someone else knows the terminal command to find information on your audio device?

hope that helps ;)

---

### Post by karma_2burn on 2007-10-16
many thanks skotadi, that got my audio working again

*but*, as always i am getting static in my left speaker

my sound card is: 82801G (ICH7 Family) High Definition Audio Controller

is updating to the latest version of alsa a potential fix for this? and if so how do i proceed?

i know the speaker is fine-it works quite nicely on my windows partiton

any suggestions?

---

