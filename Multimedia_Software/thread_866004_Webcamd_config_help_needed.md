---
title: "Webcamd config help needed"
date: 2008-07-21
forum: Multimedia Software
---

### Post by kcox5342 on 2008-07-21
I've been trying to setup a webcam on my home server.  I got the webcam working with Ekiga and I've been trying to use webcamd to automate the capture process.  Here's the error that's got me stuck:

Configuration file found
webcamd run, pictures are taken every 30 secondes
mv: cannot stat `/home/kcox/.webcamd/pre-webcam.jpg': No such file or directory
mv: cannot stat `/home/kcox/.webcamd/webcam.jpg': No such file or directory
kcox@mythbox:~$ ioctl: VIDIOC_G_STD(std=0x0 []): Invalid argument
no way to get: 352x288 24 bit TrueColor (BE: rgb)

I've got a TV tuner card in the server which I believe is video0 and the webcam should then be video1.  (Ekiga does not make this clear.)  I've made JPGs and put them in ~/.webcamd/pre-webcam.jpg and webcam.jpg and made sure they've got read/write permissions, and ~/.webcamd does as well.  What does "cannot stat" mean?  And those last two lines have me totally stumped.  Is webcamd even the best tool for the job?  I briefly tried using "webcam" but "webcamd" is easier to Google for help, and it seems to do what I need, if I can just get it working...

Thanks for reading this far!

BTW, the server's running Ubuntu 7.10 AMD64, and the webcam is using v4l2.

---

### Post by cybertechx on 2008-10-03
probably your webcam don't support that resolution, you need to change it in configuration file.
you don't need create any jpg file it's automatically created.

---

