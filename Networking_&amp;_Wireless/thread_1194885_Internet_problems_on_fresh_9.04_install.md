---
title: "Internet problems on fresh 9.04 install"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by penguinchrissy on 2009-06-23
My tower crashed so I decided I would do a fresh install on it. I was previously running 8.10. My wireless card was working fine then. When I installed 9.04 I installed bcm43xxx-fwcutter (not 100% on the name) to get my wireless running. It was REALLY slow like 15kb/s max. So I tried to remove them so I could reinstall them. After rebooting after the uninstall I was getting speeds of 700kb/s +. So I shut down my computer and moved it back into the room where I keep it. Started it up and it was slow again. I tried reinstalling the drivers and doing the fetch firmware. Still nothing.

To compare I went to speedtest.net and used my laptop vs my tower
Laptop 12.17 Mb/s down 2.79 Mb/s up
Tower(with bcm43) 1.68 Mb/s down .79Mb/s up (these aren't the exact numbers but close)
Tower(w/o bcm43).28Mb/s down .1Mb/s up (These are exact :(  )


Is this a known problem cause I can't find any info on it that concerns 9.04. If you need me to post any info just let me know.

Thx.

---

### Post by tmht on 2009-06-23
You have to activate the drivers too.  It sounds like you did that, but can you confirm that you infact did do that?

---

### Post by umaxtu on 2009-06-24
The same problem began happening to me after I upgraded my kernel a week or so ago. I also use the bc43xx-fwcutter thing for my linksys wireless g pci card when my internet started running slow I opened a terminal and ran the following.
```
sudo /etc/init.d/networking restart
```
And it said somtething like > Ignoring unknown interface WLAN0

When I ran the command again it didn't say that again and my internet ran smoothly for a while. So when my internet started running slow again I ran the command again. The first time it complained about unknown interface WLAN0 and the second time it didn't and my internet started running smootly again.

This seems to be a temporary fix for me. Please let me know how it works for you.

---

### Post by penguinchrissy on 2009-06-25
I did get the same message as you did when doing the network restart wither the drivers were installed or not. Having the drivers did make a small difference from like .56 to 1.28 (making up rough numbers). Installed a different card I had laying around get up to 9 but avg about 6. Better but still not great. My old card was a microsoft broadband networking card MN-730, My new one is a Dynex. Thanks for the suggestions.

---

### Post by penguinchrissy on 2009-06-25
> **tmht said:**
> You have to activate the drivers too.  It sounds like you did that, but can you confirm that you infact did do that?

Is there something special I have to do to do this. Like a command or is just going to synaptic and installing them there and restarting good enough?

---

