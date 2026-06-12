---
title: "Creating Video DVD"
date: 2009-03-01
forum: Multimedia Software
---

### Post by zeroemissions on 2009-03-01
ello,

I have in the past used convertXtodvd in windows, which was a great program for turning avi files into DVD's for the DVD player.

Struggling to get any results using Ubuntu. It looks like Brasero is quiet simple to use but it won't let me burn. It says: 

"Please replace the disc with a supported CD or DVD, It is not possible to write with the current set of plugins" 

My burner has no problem burning these same discs in windows so I figure it must be a setting or a plugin that I am missing, any ideas?

or, any other apps that are simple, fast and work??

Thanks

---

### Post by binbash on 2009-03-01
You can use Devede which does same thing as convertXtodvd.Did you install libdvdcss2 which is at medibuntu repo?

Also please go and download try it with nero linux trial so we can see if it is a brasero problem or not.

---

### Post by zeroemissions on 2009-03-01
Thanks for the hasty reply.

I had a quick look in synaptic for libdvdcss2, seems its a part of the restricted extras which I didn't have, but will do soon.

If that doesn't help then I'll try devede and if all else fails, nero.

Thanks again

---

### Post by zeroemissions on 2009-03-01
Brasero just crashes now. I might need to restart though.

Devede should work because it only creates an image file. And I have had no problem burning images to disc. Is there a way to get it to write to the dvd? 

The disadvantage of this is you have to do twice the work to get the disc. Much better when you can just select the video file, wack in a blank disc and come back in 40 mins when its done.

---

### Post by binbash on 2009-03-01
download latest brasero from getdeb.net also if you made iso with devede you can write it via command line.

---

### Post by mnellie on 2009-03-03
I've been searching a way to create a video DVD to play in any DVD player device plugged in a big screen TV, but this still can't be done by using any Linux distribution.

As far as I know, brasero is the only open source software that has an option to create a playable video DVD, but it sadly does not work: after you organize your project, with the video files you want to be burned to your DVD, you press the "burn" button just to realize this is grayed out and nothing can be done.

I experienced this myself and also I read others' similar experiences in many forums and communities regarding brasero: everyone is having the same issue.

And we are talking about the last version of brasero here. I'm using the last Ubunt version as well. Ubuntu is great. Brasero is going for it (I hope)

I'm sure the issue regards the brasero software and soon or later someone may fix it.

By now, I'd better try the old and good nero trial for linux.

---

### Post by Paddy Landau on 2009-03-05
Try ManDVD.

[http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD)

I found that it works for most AVI files, but sadly not for all. It creates the directory structure, and you can use K3B to burn a video DVD with that.

---

### Post by neppakyo on 2009-03-05
> **mnellie said:**
> I've been searching a way to create a video DVD to play in any DVD player device plugged in a big screen TV, but this still can't be done by using any Linux distribution.

As far as I know, brasero is the only open source software that has an option to create a playable video DVD, but it sadly does not work: after you organize your project, with the video files you want to be burned to your DVD, you press the "burn" button just to realize this is grayed out and nothing can be done.

I experienced this myself and also I read others' similar experiences in many forums and communities regarding brasero: everyone is having the same issue.

And we are talking about the last version of brasero here. I'm using the last Ubunt version as well. Ubuntu is great. Brasero is going for it (I hope)

I'm sure the issue regards the brasero software and soon or later someone may fix it.

By now, I'd better try the old and good nero trial for linux.

Every DVD i have made with Devede has worked in all the dvd players.

Mind you the list is small, just 7 different ones, but no problems at all.

---

### Post by Paddy Landau on 2009-03-05
> **neppakyo said:**
> Every DVD i have made with Devede has worked in all the dvd players.
That just shows how variable computers can be.

I can't get DeVeDe to work at all for me.
ManDVD works for me most of the time.
When it doesn't, I resort to ffmpeg or tovid, and dvdauthor.

---

### Post by neppakyo on 2009-03-05
> **Paddy Landau said:**
> That just shows how variable computers can be.

I can't get DeVeDe to work at all for me.
ManDVD works for me most of the time.
When it doesn't, I resort to ffmpeg or tovid, and dvdauthor.

Well if I remember, devede is just a front end to those commands.

Can't remember or check as I'm on my blackberry at work Lol

---

