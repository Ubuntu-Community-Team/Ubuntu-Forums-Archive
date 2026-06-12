---
title: "USB webcam visible for one user ... but not the other?"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by tbraun on 2008-01-27
Hello!

I have a weird problem: Running under 7.10 (Gutsy) on a somewhat older desktop, I can use Cheese or Skype (with video) to see a picture from my USB web-cam when I am logged into one user account. However, when I then log into a different user account (on the same machine!), it tells me that there is no video device.

Both users have the same set of privileges according to the user manager. The hardware manager shows even in the second account that there is a video device. But applications for some reason cannot find it...

Any idea what's going on? Where do I even begin to look to solve that problem?

Thank you very much...

---

### Post by luiverco on 2008-02-15
Hi
I can comment that I have exactly the same problem.

I only see the web cam on the administrator account.

in the non-administrator account I can use the microphone on the web cam but not the actual camera

Any help is much appreciated
Miguel

---

### Post by luiverco on 2008-02-16
Hi
I found the problem in my case
I hope this can help you as well tbraun

I checked the properties of  the /dev/video0 file 
owner was root with RW privileges
group was video also with RW privileges

Once I added the second account to the video group It found the video device

BTW the group video  did not exist and I had to create it

That was it!

---

### Post by tbraun on 2008-03-06
> **luiverco said:**
> I checked the properties of  the /dev/video0 file 
owner was root with RW privileges
group was video also with RW privileges

Once I added the second account to the video group It found the video device

BTW the group video  did not exist and I had to create it



That worked perfectly! Thank you so much! I'm so relieved that it is working now...

BTW, the 'video' group did exist for me already. One of the users was in that group, and was able to see the camera device. It was only the other user who was not. But now it's all nice... :)

---

