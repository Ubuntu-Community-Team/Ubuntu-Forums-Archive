---
title: "[SOLVED] Updated!  Broken Resolution"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by bordman on 2008-02-12
For some reason in my incredibly tired state, i thought it'd be wise to install the updates (which i know better to update cause i figured something like this would happen) and now my resolution is stuck at 640x480. Well, not stuck, i have the choice of lower resolutions or auto. All the video settings seem to be working,windows programs using dx work as does Compiz etc. My native resolution is normally 1680x1050 and i used envy to get it working in the first place. I don't know what i need to do to get it back to my native resolution and i can't work in this tiny workspace!

Any help is greatly appreciated!

---

### Post by DaveFP on 2008-02-12
Are you running any of the restricted drivers? I have the same problem, it seems that while I have the nvidia restricted drivers turned on the best I can get is 640x480, when previously it worked fine. I've now turned them off and I can use my full resolution again, but not any of the fancy stuff that the restricted drivers provide.

---

### Post by bordman on 2008-02-12
No i do not have my restricted driver in use. I messed around with my xorg file thanks to a walkthrough i found with the internet on my phone while trying to resolve the resolution issure. Now, I have another problem:

Now i am trying to reinstall my nvidia driver again (through envy) and it worked somewhat, but when i open nVidia Settings I get the following prompt:

"You do not appear to be using the latest nVidia X driver. Please edit your X configure file (just run 'nvidia-xconfig' as root), and restart the x server.

... and that's where I am lost at now. Any help?

---

### Post by bordman on 2008-02-12
So after using this guide: [http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver]("http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver")

using envy again and getting the error from the above post

all I had to do to get it fixed was 
go to system
preferences 
appearance 
click the visual interface tab
select normal
restart

worked! redid the above steps but set to custom and my compiz interface is back in action.

---

