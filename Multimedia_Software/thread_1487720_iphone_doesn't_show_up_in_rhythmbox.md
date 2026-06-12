---
title: "iphone doesn't show up in rhythmbox"
date: 2010-05-19
forum: Multimedia Software
---

### Post by tschuliaen on 2010-05-19
hello folks

I have an iPhone 3GS with Firmware 3.1.3 and I'd like to sync the music over rhythmbox in lucid (64bit).

The phone does mount in nautilus and I can also mount it with ifuse to use it witz gtkpod.
However it does not show up (it only blinks and disappears) in the list at the left in rhythmbox though I have MTP and iPod Plugins enabled.

I thought I'd ask after having waited several weeks and none of the gvfsd updates changed anything :(

thanks anyway!

---

### Post by mhedges48 on 2010-05-19
Sorry, I don't have an answer, I have the exact same problem... 

What error do you get when you run rhythmbox in terminal?  I get the below


(rhythmbox:18192): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
avoid probing device using kernel interface "uvcvideo"
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team

---

### Post by tschuliaen on 2010-05-20
> What error do you get when you run rhythmbox in terminal?

I remember getting a similar error saying unknown device and libMTP but at the moment rhythmbox doesn't write anything to the console dunno why.

---

### Post by ajayrockrock on 2010-06-09
I was able to get mine working by disabling the "Portable Players - MTP" plugin in rhythmbox.  MTP is not compatible with iPhones so I tried disabling it and it's working fine for me now.

[http://sourceforge.net/tracker/index.php?func=detail&aid=3001111&group_id=158745&atid=809061](http://sourceforge.net/tracker/index.php?func=detail&aid=3001111&group_id=158745&atid=809061)

---

