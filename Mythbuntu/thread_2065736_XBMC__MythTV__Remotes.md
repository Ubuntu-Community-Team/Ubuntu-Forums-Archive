---
title: "XBMC / MythTV / Remotes"
date: 2012-10-02
forum: Mythbuntu
---

### Post by alanrbryant on 2012-10-02
I am going to describe my current architecture and then explain what my potential problem is at the end.

I have a dedicated MythTV backend running Mythbuntu 12.04 with MythTV 0.25-fixes. I currently only have one HD-PVR connected to a Dish VIP211k HD receiver. I have 3 frontends all running Mythbuntu 12.04 & MythTV 0.25-fixes. I will be upgrading all to 0.26 tonight since I have just installed all of this and figured now is the time to upgrade before I get it all set up the way I want.

I will also be running XBMC 11.0 (Eden) on the 3 frontends.

I know MythTV's Video section continually gets better, but I still prefer XBMC's handling of Movies & TV Shows. Plus all of my movies & TV Shows are organized & named for better metadata handling with XBMC.

Anyway, my problem that I think I will have is ease of use with a remote. Our main living room tv which has a high WAF is currently controlled with a Logitech Harmony 700 remote. I know I can get it to work great with XBMC or with MythTV, but I'm concerned with it working great with both of them together.

I know several others on this forum use both programs in a similar fashion to how I plan to.

What have you done to use a remote to control both. I have a menu item in Mythfrontend to start XBMC which works great, but I would prefer to have a seamless transition in control of the two programs.

Once I get this working, my next project is to get an automated system going to transcode & export recorded TV Shows to where XBMC will pick them up on the next scan. Does anyone else do this currently or does everyone do it manually?

Thanks in advance for any help, suggestions, pointers, etc.

---

### Post by uteck on 2012-10-02
I did not have to do anything special to get my remotes to work with MythFrontend and XBMC, but the behavior is different between the two applications, is that what you are talking about?  In Myth I have to press the stop or back button to leave a screen in Myth, but XBMC I have to press start or the windows button to go back to the previous menu.  My wife never exits XBMC so it is not much of an issue.

Getting a MythTV app that works for .26 may not be possible or hard to find, but the myth protocol should work, [http://wiki.xbmc.org/?title=MythTV#Setup_in_XBMC](http://wiki.xbmc.org/?title=MythTV#Setup_in_XBMC) Then you don't need to bother with transcoding.

---

### Post by nickrout on 2012-10-03
I find this $13 delivered anywhere in th world remote works fine with both: 

[http://rtr.ca/sapphire_remote/](http://rtr.ca/sapphire_remote/)

However as uteck says there will always be differences because of the different way myth and xbmc do things. with the sapphire remote you can change keymaps on the fly. The keymap that comes with the driver works fine with myth. So what i plan to do is to work out a keymap that works really well with XBMC and then have my XBMC startup scrip look something like this:
```
#!/bin/sh
/usr/local/bin/sapphire_keymap.sh /etc/sapphire.xbmc.keymap # load the xbmc keymap
/usr/bin/xbmc # run xbmc
/usr/local/bin/sapphire_keymap.sh /etc/sapphire.keymap #when xbmc exits revert to the default (myth) keymap
```

---

