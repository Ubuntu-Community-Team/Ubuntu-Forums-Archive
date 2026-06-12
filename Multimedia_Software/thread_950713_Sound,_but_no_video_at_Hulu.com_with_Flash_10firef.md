---
title: "Sound, but no video at Hulu.com with Flash 10/firefox 3-- AMD64"
date: 2008-10-17
forum: Multimedia Software
---

### Post by Mothinator on 2008-10-17
I am using ubuntu hardy amd64. I installed Adobe flash 10.0.12.36 using nspluginwrapper into firefox 3.0.3.

Everything works fine with sites like pandora and you tube. However, when I go to watch a video on Hulu, I get a white box where the video should be with sound, but no video.

Does anyone else have this problem or know a solution?


I do have noscript installed, but I have it set to allow all scripts on hulu.

BTW, I also had this problem with the last couple of releases of Flash 9. The last version that I know works is 9R48.

I have a Dell M1330 laptop with Nvidia 8400M GS using the nvidia driver 173.14.12


Thanks for your help.

[EDIT] Ok, I think I know what is happening. It appears that the first flash element on Hulu is the only one that will run. Usually, this is their gallery on their home page. However, if you launch a video, kill firefox, and open firefox with the restore pages option, the video will load.

[EDIT #2] It actually appears to be a "first flash per tab" thing. If you go to Hulu and then open a video in a new tab, it'll play just fine. Well, looks like this is the workaround.

---

### Post by Mothinator on 2008-12-04
The little workaround I came up with above doesn't appear to work with Intrepid.

But, Adobe is publicly testing a native 64-bit version of flash player:
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

This seems to work great!

---

### Post by markbuntu on 2008-12-04
I just installed amd64 Intrepid about a week ago, got the ubuntu-restricted-extras which included flash10.0.b218. Hulu works without problems for me. On my amd64 Hardy I am still using the original flash10b which also works without problems on hulu.

---

### Post by Mothinator on 2008-12-05
Thanks for the post, Markbuntu. Due to the activity (or lack thereof) on this post, I guess it is not a common problem.

Maybe it is related to my video card. I have a Dell m1330 with an nvidia 8400M GS.

---

