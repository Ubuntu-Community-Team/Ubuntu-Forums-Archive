---
title: "Changing Channels the old school way."
date: 2008-01-18
forum: Mythbuntu
---

### Post by psybert on 2008-01-18
So I'm wondering, can I somehow configure my system to change channels the old school way using the up/down button? Right now my channel up and down button brings up the guide info at the bottom of the screen and cycles through the channels that way. I just don't see any options within MythTV "edit keys" for a standard channel change. I thought "channelup" would do it, but it just changes the guide info. 

To make things clearer: I want the channel up or down button to goto the next channel, up or down, instead of bringing it up in the small guide window on the bottom and having to push OK to switch channels. Like the old school: channel flipping. 

For what it's worth the up/down arrow buttons around the OK buttons do the same thing as the channel up and channel down buttons, and i'd like for them to maintain the same functionality. The problem I see is that I don't see an option in MythTV for a standard channel change to bind anything to. 

Also, i'm a complete nub when it comes to mythbuntu, ubuntu, mythtv and linux in general. I figured out how to get my PVR500 windows vista remote to work with a custom lirc.conf and lircrc file. 

Thanks for the help!

---

### Post by newlinux on 2008-01-18
Sounds like you have browse mode enabled on your frontend. I think you can just turn this off and you'll get the functionality you want. I'm not at my machine now, but I think the setting is in: Setup->TV Settings->Playback->On Screen Display. However, your up and down buttons won't maintain the same functionality they have now (they'll do the same thing as the ChUp and ChDn buttons. I don't know anyway of having both functionalities running at the same time because there aren't separate key mappings for channel browsing and channel changing. Just a flag to say whether you browse or change channels in general

---

### Post by psybert on 2008-01-18
Yes, I did have browse mode enabled. Turning it off brings me the "old school channel changing" but then I can't do the preview mode. 
The problem is, I want both types of functionality. I have an up/down arrow, and a channel up/down. Almost all remotes have that feature, it should be supported :\

---

### Post by volkswagner on 2008-01-18
I agree it should not only be possible but the norm.  If Mythtv was designed to run with a remote why would they map the navigation keys to channel changing?

Possibly it would be more correct is to say the two functions use the same command.

[http://www.mythtv.org/wiki/index.php/Keybindings]("http://www.mythtv.org/wiki/index.php/Keybindings")

I learn something new everyday.

---

