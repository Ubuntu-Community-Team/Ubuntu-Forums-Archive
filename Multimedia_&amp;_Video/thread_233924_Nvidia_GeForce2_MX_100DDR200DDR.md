---
title: "Nvidia GeForce2 MX 100DDR/200DDR"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by thistlebrae on 2006-08-10
According to my Ubuntu conf file I have the above noted graphics card in my box on which I just installed Unbuntu today.  Here is my issue.  The only option displayed for resolution is 640 x 480 (kindergarten mode :mad: )

Does anyone out there know how I rectify this?  I would like it to be at least 1024 x 768 or higher...but that option is not available.  I have searched to see if I could find a similar post but have not come up with one as of yet.

Would appreciate a steer....

Regards,
Todd

---

### Post by Ziox on 2006-08-10
> **thistlebrae said:**
> According to my Ubuntu conf file I have the above noted graphics card in my box on which I just installed Unbuntu today.  Here is my issue.  The only option displayed for resolution is 640 x 480 (kindergarten mode :mad: )

Does anyone out there know how I rectify this?  I would like it to be at least 1024 x 768 or higher...but that option is not available.  I have searched to see if I could find a similar post but have not come up with one as of yet.

Would appreciate a steer....

Regards,
Todd

try sudo dpkg-reconfigure xserver-xorg

and pay special attention to the resolution section

---

### Post by tseliot on 2006-08-11
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by thistlebrae on 2006-08-11
Many thanks to both of you who replied.  Perhaps you were both on the right track.  In the late afternoon yesterday before you replied I lucked onto this document (posting here so that others may "luck" onto easier than I did](*,) )

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It containted all the answers.  In brief, the part about "nv" versus "nvidia" in the xorg.conf file was the magice bullet..while I did all steps "to the letter" it was when I made that final change that I reached nirvana!

Now I am really lovin' UBUNTU!

Thanks again for jumping in....

Todd

---

