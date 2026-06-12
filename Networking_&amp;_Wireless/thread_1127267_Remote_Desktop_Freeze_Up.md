---
title: "Remote Desktop Freeze Up"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Scott30101 on 2009-04-16
When I try to access my desktop through my lap using the Remote Desktop Viewer, my laptop freezes up, showing a grey screen and I have to restart using the power button.  This is especially strange because it had worked several times before.  Anyone having the same problem or know what to do?  Thanks

---

### Post by carniola on 2009-04-18
I have the same problem, except without the gray screen. But launching remote desktop viewer leads to instant freeze. And it worked flawlessly before.

Any ideas would be appreciated.

---

### Post by EnlistedSquire on 2009-05-01
I'm having this problem too although only in the last couple of weeks. It happens from both my laptop and desktop, both running Ubuntu 8.10.

---

### Post by swarup on 2009-05-08
I have a similar problem: the image being sent to the remote desktop freezes up. But in my case, I think the problem lies with the server computer, not the remote computer. The remote computer itself is fine i.e. I can close the connection any time with no problem and the remote computer works fine. 

I have just loaded Jaunty onto my Dell Precision M6400, and want to use it as a server for a remote desktop. I have tried using Vinagre as well as tightvncserver, but the same problem arises regardless of which I use: the remote desktop can initiate a connection to my laptop, request permission, and achieve a connection. And the image on my laptop's screen immediately appears on the remote desktop's monitor-- as it should. But that initial image which gets transmitted, gets immediately fixed on the remote moniter and does not continue to update as the image on my laptop changes. Whatever the first image was, that is all that gets transmitted.

One odd thing is that if I move the cursor on my laptop screen, the remove desktop moniter will see the cursor moving around. But if I open and close any applications, or anything I do on my laptop screen, nothing of that is visible to the remote desktop except that the cursor itself is moving.

My laptop can work just fine as the remote desktop and recieve images from the desktop of any other computer. But any other computer which tries to connect as the remote desktop to my laptop, will get only one fixed image.

I have Jaunty on another computer, and the remote desktop server is working fine on that one. But on my laptop it is not working. How can I trouble-shoot this?

---

### Post by Scott30101 on 2009-05-11
It's all good now after the new ubuntu upgrades.

---

### Post by Scott30101 on 2009-06-30
Then it started happening again.  My friend fixed it this weekend by changing the settings on the desktop computer.

---

### Post by lores on 2009-07-21
@swarup, I'm experiencing exactly the same issue. I'm using  quite a few Ubuntu 9.04 PCs at the moment, but just one of them has this problem, although all the settings are the same (and it's running U9.04, too). It has been the issue with that machine for ca two months now, since I bought it and installed Ubuntu onto it...

Any clues?


EDIT: Just found out - [http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html](http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html) (3rd bug). I have had nVidia proprietary drivers and compiz enabled on that single machine, thus it didn't work.
So we have got to stick with x11vnc - I have just tested it and it works all fine.

---

