---
title: "cpu hog when playing any video"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by jaredmi on 2007-08-01
hi there.I'm fairlynew to ubuntu and linux for that matter but having a great time.the only real problem im having right now is with video playpack.im using a nvidia 7600gs vid card,athelon xp2500 1.5gig ram.when playing video with mplayer or any other player my cpu usage hops up from around 3-4% idle up to around 65%. With fullscreen I'm up to 98% and the vid plays pretty sluggishly.i do have beryl running and if i switch back to metacity my performance is better at full screen but still hogs about 65% or more.If anyone has any ideas that would be great.Im not sure what to post that might help but ill try my darndest.thx-jared

---

### Post by eeried on 2007-08-01
next time, launch a terminal and type: top

Then post the result here or at least the line where you can see "90% CPU usage" or more. in a word, spot the hog. I have a simiilar poblem: my hog is hald-addon-stor and I'm wondering how to mend things other than killing that hog -- that's no solution because I can't even play an audio-CD with or without the hog.

---

### Post by jaredmi on 2007-08-02
thx for the response.i ran "top"in term as you suggested.im not sure how to save those results from term to post but mplayer(and whatever other players i tried) and xorg both were hogging up about 40% each give or take.this along with beryl and and a few other goodies topped me out around 90%.the drivers im using for my vid card is just whatever the restricted drivers manage in ububtu installs.im not sure if thats the correct one to be using or not.any suggestions?

---

### Post by eeried on 2007-08-03
hello jaredmi,
If your're using beryl you may need to install the drivers specific to your video card, So you need the nvidia drivers. You'll find the drivers on the Nvidia website and plenty of doc on help.ubuntu.com (User documentation):

[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

After installing drivers, you can reboot or at least log out then in again.

To copy some terminal output, simply select the text with the mouse, and click the wheel to copy the content on your message form.

Of course if your screen freezes and your mouse can't move you'll have to resort to pen and paper. It seems to me only the first four lines are about the hogs. In my case only one hog was responsible for the freeze.

if you're new to Linux, read the documentation carefully. it's a great help, I've found.
cheers

---

