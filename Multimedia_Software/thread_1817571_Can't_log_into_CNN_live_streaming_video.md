---
title: "Can't log into CNN live streaming video"
date: 2011-08-03
forum: Multimedia Software
---

### Post by gfe on 2011-08-03
I'm not sure this is, strictly speaking, an Ubuntu problem (although it may be), but people around here seem to be more knowledgeable than they are anywhere else, so it's worth a try.

CNN recently started offering its news station on live streaming video for those who get CNN from a participating cable provider. For better or worse, I get CNN on Comcast, so no problem there.

Except for lagging video because lack of processing speed, it all works fine on my netbook, on which I have Ubuntu 10.04 installed.

But on my desktop, where I'm using Ubuntu 11.04, no such luck. The problem is the same regardless of whether I'm using Opera, Firefox or Chrome.

I can go to [http://cnn.com/video]("http://cnn.com/video") and get the standard video streams (not CNN live) just fine. When I click on the "Live" button and then the "Unlock Live TV" button, I get, as expected, the "Sign in to watch live TV" dialogue box. So I click on Comcast, log in correctly, and am returned to the main screen. The page appears to be loading correctly, and then I get the "Sign in to watch live TV" dialogue box again. No matter how many times I try, that's what I keep on getting.

If this didn't work on my netbook, I'd just assume that for some reason the setup is Linux-unfriendly, but now I'm determined to get this working.

I've checked my plugin settings on my browsers and nothing seems amiss. I've tried deleting all cookies, persistent storage, Flash cookies and all such things, but to no avail. Even though I had the most recent version, I even uninstalled and reinstalled Flash, but that didn't change anything.

Any suggestions?

---

### Post by gordintoronto on 2011-08-03
Did you install the "restricted extras"?

---

### Post by sbeitzell on 2011-08-04
I'm having the same issue with Firefox and Chrome (didn't try Opera...).

I do have the restricted extras installed and re-verified I have the latest adobe flash player.
No joy.

Help?

---

### Post by gfe on 2011-08-04
I also have the restricted extras installed and the latest Flash version. I even tried installing a development version (v. 11) but ended removing it because of an annoying display bug.

---

### Post by gfe on 2011-08-11
I tried it again today after a regular system update that included Flash, and it worked fine. I have no idea if it's because of Flash or something else.

---

### Post by gfe on 2011-08-13
And today it doesn't work. This is frustrating.

---

### Post by gtippitt on 2012-03-09
Has anyone yet found a fix for this problem.  I'm using 11.10 and have all the adobe and extra stuff.  I tried it both with and without Adobe Air.

Thanks,

---

### Post by LuridCinema on 2012-03-09
Perhaps GOD is wanting you to watch FOX news !!! HMMMM ?? HMMM ???

ok, just kidding

Have you tried another browser ? my Firefox has been crazy letely w/ Youtube Vids, I keep uninstalling the Mozilla plugin for flash and reinstalling and it still messes up and I have to repeat....Good luck

---

### Post by gfe on 2012-06-04
Yes, I've tried several browsers. The CNN videos, including live feeds that aren't of what is being broadcast, all work fine.

I was hoping that when I upgraded to Precise that that would solve the problem. But alas, it doesn't. I assume that the problem has something to do with the way Flash checks to see if I'm logged onto my cable provider, but as far as I can tell that's something I don't have control over.

---

### Post by gfe on 2012-07-31
Problem solved! The method used is the same as needed to get live NBC coverage of the Olympics. Basically, Flash requires installation of the Hardware Abstraction Layer so it can use DRM, and the HAL isn't installed in Ubuntu by default.

These directions come from Adobe at [http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html").

Here's what to do: From the terminal:

[FONT="Courier New"]sudo apt-get install hal[/FONT]

Then close your browser if it's open (I've got this to work with Opera and Firefox, haven't tried other browsers), and once the layer is installed, run the following commands so that Flash can create a new list of protected content it can play (or something like that):

[FONT="Courier New"]cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2[/FONT]

---

