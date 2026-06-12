---
title: "Creative Live&quot; Notebook Webcam almost working, help!!!"
date: 2009-06-28
forum: Multimedia Software
---

### Post by LinuxBob on 2009-06-28
OK I have a Dell 1505n Inspiron with Feisty from the factory.

I have a usb webcam from Creative, a notebook cam brand new and I installed following the instructions here:

[http://www.andreagrandi.it/2008/06/05/creative-live-cam-notebook-su-ubuntu-linux/](http://www.andreagrandi.it/2008/06/05/creative-live-cam-notebook-su-ubuntu-linux/)

and here:

[http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218)

The jpg driver on the Italian website almost works, the spca one on the site above did not.  Having done the English instructions with the wrong driver first, it was easy to then follow the Italian instructions with what looks like the right driver.  Why do I say that?

Because although I initially could not get Camorama to find /dev/video0, I googled and found out there is a permissions issue.  Apparently /dev/video0 is owned by root and the "video" group.  SOmeone suggested adding MY USER to the "video" group and so I did.  And then Camorama kinda worked.  I got 3 images of my mug in black and white on screen.  

After that I tried other programs that use the webcam and nothing.  I issued this command;

cat /dev/video0 and I got back, I am paraphrasing, "resource in use or busy."

So apparently camorama held onto the cam after I shut it down.  I logged out and re logged and the cat /dev/video0 returned more verbose info, in English and I had to kill the cat process as it was hung, ctrl-c would not work, nor ctrl-z.

ANyone have any idea what I can try next?  The blue light is on the webcam which happened after completing the Italian instructions.  The three of four hours before I stumbled on that instruciton I did not get any light, or any thing recognized as /dev/video0, so I am making progres.  It almost works . . . 


Almost.  Who can help get me over the line?

---

