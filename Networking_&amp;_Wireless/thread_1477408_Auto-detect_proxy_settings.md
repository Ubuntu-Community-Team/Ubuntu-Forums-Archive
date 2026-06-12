---
title: "Auto-detect proxy settings"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by The End of The World on 2010-05-08
Hey, completely stuck here
[i checked around the forums before i posted this to check no one else had this problem, also checked google and such]

ok so my school has this REALLY annoying way of us connection to the internet, they use a thing which you have to log into a webpage [which is an ip adress type job, web browsers are conveniently automatically redirected there if your computer isn't logged in] and you type in your name and password. the software its called is Smoothwall SSL [i believe, if i remember thats what it says lol] and you have to log into that before you can do ANY desktop things that require the internet, or just browse the internet at all - only problem, is that this Smoothwall SSL thing can only work if you set firefox [well any web browser] to ''auto-detect proxy settings''. now, i did this, and yes, the internet works, yay me, but you cant run anything in ubuntu that requires the internet - for example, pigdin etc. you cant do this in system - preferences - network proxy so i'm quite stumped really :( 

my schools network is a windows one. [either that or its some RM version of windows]

any help will be SO UNIMAGINABLY thanked lol

=edit=
it says Smoothwall SSL but i think the actual program is Smoothwall School Guardian

---

### Post by The End of The World on 2010-05-11
[[Bump]]

---

### Post by landymann on 2010-05-25
I have a similar problem with my eee connecting it to the network, although we don't use that software firefox can auto detect proxy settings but I don't know what they are so only firefox works :(. I take it your school runs community connect 3 or 4.

---

### Post by The End of The World on 2010-08-10
I dont know, havent sorted it yet :S maybe ill ask the it dept...but then again, they might all be like "whats ubuntu?" jee, an it dept should have techs of all(-ish, if u count linux as 1 os with a tree of distros coming from it) types of OS's.

[[bump]], as well, while im here lol

---

### Post by Jack Brown on 2011-01-05
have you tried steps in this thread?

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1390260](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1390260)

also looking for the place where you can set proxy settings in ubuntu.  It's not in the network applet on the panel.

edit add: was trying to file a bug but can't since i have to go through the proxy.

---

### Post by PatchesTheCaveman on 2011-01-05
Jack Brown:  System > Preferences > Network Proxy.  There's an *Apply System-Wide* button that should apply those settings to *apport* (the bug filing assistant program) as well as APT and other system utilities.  It also sets the *HTTP_PROXY* environment variable so most console applications pick up your proxy settings too.

---

### Post by Jack Brown on 2011-01-06
yeah Patches, just found it and came in here to say never mind.. but you were prompter :)

Just wasnt able to find it when i was looking for it in Ubuntu netbook edition Lucid...  Is it in 'system'?  I'll just look again.

thanks

Edit: yeah it's in there (UNE system prefs), just scrolled over too fast

also the proxy automatic configuration URL textbox on firefox is inaccessible on an eee701 UNE Lucid, even while holding the ALT key and moving the window around. it's cut off. That's on the latest firefox (not beta).
So workaround was to go into about:config,  search for autoconfig_url and type in the autoconfiguration url as the string value.

of course the system wide button on your post above would probably enable proxy as well.

---

### Post by PatchesTheCaveman on 2011-01-06
> of course the system wide button on your post above would probably enable proxy as well.

You don't even have to do that.  As long as the *Use system proxy settings* radio button is checked in Firefox's proxy settings, it will pick up your per-user Network Proxy settings.

---

