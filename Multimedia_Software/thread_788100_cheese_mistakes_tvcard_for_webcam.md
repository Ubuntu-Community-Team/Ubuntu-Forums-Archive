---
title: "cheese mistakes tvcard for webcam"
date: 2008-05-09
forum: Multimedia Software
---

### Post by tony11235 on 2008-05-09
I currently have a leadtek tv card (video0), and a logitech webcam (video1). Cheese chooses to go with video0, and within cheese there is no configuration option for which device you are using. And I haven't been able to find any configuration file to change the video device that Cheese uses. Does anybody happen to know where to change this?

---

### Post by victorgreen on 2008-05-09
Try changing the video device in System==>Preferences==> Multimedia System Selector. If that option doesn't appear in the menu, right click the application menu, hit edit menus, navigate to the menus under system preferences and check the box to display the multimedia system selector. 

The in the selector go to the video tab and see if it'll let you select a device.

---

### Post by tony11235 on 2008-05-09
I tried that, but cheese still prefers video0. There's got to be a config file for cheese, just not finding it.

---

### Post by steevc on 2008-06-26
I have a DVB TV card and recently added a webcam. When I first tried Cheese it worked fine with the camera. Since then I just get a blank screen, so suspect that it is using the TV card. Perhaps it picked up on the camera as it was a new device initially.

Cheese is mainly a novelty, but that would not stop my kids from playing with it.

To just view the webcam stream I find VLC useful. I suspect that opens up possibilities for all sorts of fun and games such as streaming it to somewhere else.

---

### Post by jmtdstoc on 2008-08-28
I have exactly the same problem. I also have a TV card (analog) with a Logitech STX webcam... Cheese always chooses to use the TV card.
I have also selected the webcam on System==>Preferences==> Multimedia Systems Selector but Cheese always goes for the TV card.

Can someone please help us two desperate users who want to try Cheese :) (without having to uninstall the TV card, of course :) ).

Thanks.

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

