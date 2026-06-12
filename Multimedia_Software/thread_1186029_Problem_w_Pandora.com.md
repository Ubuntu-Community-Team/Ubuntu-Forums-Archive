---
title: "Problem w/ Pandora.com"
date: 2009-06-12
forum: Multimedia Software
---

### Post by missing in action on 2009-06-12
Hey all.. I don't know what happened, but when I try to use Pandora now it does not load like it used to. It just freezes up and nothing happens. Anyone have the same issue? :-?

---

### Post by lexbarron2007 on 2009-07-06
im having the same problem.
when i load pandora.com in firefox it only loads part way and stops. i installed all the drivers firefox suggested for me, now im wondering what drivers are likely to help here.
i dont actually know what drivers pandora should need to be able to run.

---

### Post by crawlerzero on 2009-07-08
I have the same issue with Pandora.

I recently upgraded my machine to 9.04 and now Pandora will not work properly.  It loads partially, and around 20% loaded it hangs.

---

### Post by dansar99 on 2009-07-10
Pandora does not load for me either. I wish someone could post a fix,if there is one. Dan

---

### Post by dE_logics on 2009-07-10
Appears to be more of a Firefox problem.

You all installed that flash and java plugin for firefox?

Can't try it, I'm outside the US.

---

### Post by bcfieldi on 2010-07-06
Same here, pandora will not load for me. I have java 6u20 and latest flash 10.1 update. Most flash and java works for me fine but pandora will not load the player itself. Opening the javascript console gives me this error. 

[PHP]Failed to load resource
Unsafe JavaScript attempt to access frame with URL http://www.pandora.com/ from frame with URL http://www.facebook.com/extern/login_status.php?api_key=ca44798cf7067942a82579c2c720f7dd&extern=2&channel=http%3A%2F%2Fwww.pandora.com%2Ffacebook%2Fxd_receiver.htm&locale=en_US. Domains, protocols and ports must match.[/PHP]

I've tried re-installs of both java and flash, chrome, firefox, and probably a dozen different fixes to no avail. I'm stumped.

---

### Post by ronnielsen1 on 2010-07-06
No problem here with Ubuntu 10.04 and firefox

---

### Post by ronnielsen1 on 2010-07-06
You might make sure these aren't installed
> In Firefox, make sure to disable add-ons (extensions) like Adblock,  Flashblock, or NoScript.  These add-ons are **not** supported for use  with Pandora.  Also, select Tools -> Options (on a Mac: select  Firefox -> Preferences):
[LIST]
[*]Under "Content," make sure "Load images automatically" and  "Enable JavaScript" are checked.
[*]Under "Privacy," make sure "Accept cookies from sites" and  "Accept third-party cookies" are checked.
[/LIST]

[http://blog.pandora.com/faq/contents/144.html](http://blog.pandora.com/faq/contents/144.html)

---

### Post by bcfieldi on 2010-07-06
Already checked that. I don't use Ad or flashblockers and all java and cookie settings are appropriate. Not the issue. Pandora loads, but the flash player itself is just a blank white square. Same thing happens if I go to adjust the website or global adobe flash settings. Blank square where the flash should be. Probably unsolvable until adobe gets their act together and fixes this with the next update, which may be never... I guess I'll log the issue with them today.

Is this just happening to me or is this what is happening to others not seeing pandora as well?

---

### Post by ronnielsen1 on 2010-07-07
> 
Is this just happening to me or is this what is happening to others not  seeing pandora as well?
It's working fine on my box with Ubuntu 10.04 and firefox 3.6.6
I assume you have ubuntu-restricted-extras and all codecs etc installed

---

### Post by ronnielsen1 on 2010-07-07
I just installed firefox 4 and had no issues either. You might make sure you have all the codecs and everything installed.

[http://linuxpoison.blogspot.com/2009/04/multimedia-support-in-ubuntu-904-jaunty.html](http://linuxpoison.blogspot.com/2009/04/multimedia-support-in-ubuntu-904-jaunty.html)

---

### Post by bcfieldi on 2010-07-12
Well, my problem has been fixed but I'm not sure what exactly I did to fix it. I think that it might have been conflicting lib files. There is a libgcflashplayer.so file located in /opt and a libflashplayer.so file in /usr and I think that they conflict with each other. If you are using Chrome, click the wrench in the upper right corner then click Options > Under the Hood > Content Settings > Plug-ins > Disable individual plug-ins, then disable the shockwave flash plug-in under the /opt location.

Disabling the same in Firefox should have the same affect. Let me know if this is successful for everyone that was experiencing the problem. If not I'll try and see if there was something else I did that fixed the problem for me.

---

### Post by fireoftroy on 2010-10-17
What's weird for me is that my 10.10 desktop will run Pandora, but my 10.10 laptop will not.  Firefox reports the flash plug-in is up to date, so I'm not really sure what is different between the two.  If I figure it out, I'll let you know.

---

