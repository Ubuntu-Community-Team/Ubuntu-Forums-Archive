---
title: "Anyone have any experience with Ace Stream HD and the AceStreamingEngine on Ubuntu?"
date: 2017-09-01
forum: Multimedia Software
---

### Post by bcxxbc on 2017-09-01
I installed it from the Ubuntu App store or whatever it's called, and it works very well. However I need to configure it, and it seems it was installed via a snap something I am quite unfamiliar with. I need to set the paramaters in a conf file, but everything in the snap is unwriteable. How can I access the snap for writing? Alternatively, if anyone has experience with it how else can I pass the configs to it? You can also pass the changes to it via command line, but I am unsure how I can change the command it runs from in the .desktop file. Can I just edit the exec line to include the config flags?

Because I see this: Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/acestreamplayer_acestreamplayer.desktop /snap/bin/acestreamplayer %U
Could I just do: Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/acestreamplayer_acestreamplayer.desktop /snap/bin/acestreamplayer -max-connections100 -max-upload-slots100 %U

I am super confused because this is new stuff to me when it comes to snaps.

---

### Post by mc4man on 2017-09-01
Never used (and at 1st/2nd glance don't know how to..
What I do see - 
Wouldn't do any good to add to the acestreamplayer.desktop as that just opens the player which is basically vlc. So only vlc options would be possible/acceptable.

The 2 options you mentioned seem to be AceStreamingEngine options. Not sure if adding to it's .desktop will do any good, you could try but I didn't notice any change in the engine's reported start up options
(- here those options seemed to need -- not -

The engine has some options available thru the indicator icon drop down though didn't see yours listed. When changing any of the listed options it seems to write to this file, maybe you could add in thru it??
> ~/snap/acestreamplayer/common/.ACEStream/playerconf.pickle

---

