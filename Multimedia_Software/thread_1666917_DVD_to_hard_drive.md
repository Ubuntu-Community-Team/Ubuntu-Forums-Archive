---
title: "DVD to hard drive"
date: 2011-01-14
forum: Multimedia Software
---

### Post by Jimmmac1 on 2011-01-14
Good morning

I frequently play dvd's on my pc.  Question : Is there a way to copy a dvd to my hard drive, then play it?  I am a 24 fan and have all the dvd's.  But someday, they will deteriorate and disintegrate.  I don't want to recut dvd's, but I thought it might be a good thing to bring them down, where they could be backed up and then played on my PC.  Running the latest Ubuntu.  Thanks.

Jim

---

### Post by Grenage on 2011-01-14
Indeed!

You can rip the disc to an ISO (dd or Brasero etc), then mount the ISO:

You'll need a mount point:

```
sudo mkdir /mnt/iso
```

Then:

```
mount -o loop YOURISO.iso /mnt/iso
```

---

### Post by JDorfler on 2011-01-14
You don't even have to mount the ISO.  You can use VLC to just read your DVD ISO file and it will read just like a DVD.  However, from the ISO you can use Handbrake to transcode the movie to .mp4 and play it from almost any device you want.

---

### Post by JDorfler on 2011-01-14
You don't even have to mount the ISO.  You can use VLC to just read your DVD ISO file and it will read just like a DVD.  However, from the ISO you can use Handbrake to transcode the movie to .mp4 and play it from almost any device you want.  There's even some stand alone network media players, if your files are shared out, that can play the movie like a DVD right from the ISO.

---

### Post by Jimmmac1 on 2011-01-14
Hi Grenage

Thanks for your response.  I tried using both AcetoneIso, Brasero and dd and couldn't get it done with any of them.  I got errors from Brasero and AcetoneIso, and dd just created a little file which was useless. More details would be very much appreciated.  I tried a few google posts, which is where I got the info on Brasero and AcetoneIso.  Didn't quite work.  Thanks again.

---

### Post by Jimmmac1 on 2011-01-14
Hi Grenage

Thanks for your response.  I tried using both AcetoneIso, Brasero and dd and couldn't get it done with any of them.  I got errors from Brasero and AcetoneIso, and dd just created a little file which was useless. More details would be very much appreciated.  I tried a few google posts, which is where I got the info on Brasero and AcetoneIso.  Didn't quite work.  Thanks again.

---

### Post by Grenage on 2011-01-14
Hi there,

When attempting to create an image from a disc (let's assume Brasero), what error do you get?

---

### Post by Jimmmac1 on 2011-01-15
Hi all

Thanks for your reponsed.  Well I managed to create an iso from a dvd using Brasero.  It was about 8 gb in size  I created a Data iso, but am not sure if that was right. Then I tried to open it in VLC, which I installed and all I got was a orange and white cone as a picture.  It also maxed out my CPU.  I  might try another DVD to see if that makes a difference.  Still working on it.  Thanks for the help.  Any further information would be much appreciated.  

Jim

---

### Post by Grenage on 2011-01-16
Did you try mounting it, then opening it as a DVD?

---

### Post by Jimmmac1 on 2011-01-18
Hi Grenage


Wow, that is interesting.  I didn't know that you could do that.  Well I managed to mount a clonezilla iso (just for a test).  Could you outline the steps for copying a dvd to iso and then opening the iso as a dvd?  Thanks.

Jim

---

### Post by BicyclerBoy on 2011-01-18
...

---

### Post by Hakunka-Matata on 2011-01-18
I simply copied a DVD to a folder I created named "Son-Rise", see attached .png.

Then I opened the Son-Rise folder with VLC, and it plays just fine.  I do have the libdvd........... etc modules installed.

---

### Post by Grenage on 2011-01-20
> **Jimmmac1 said:**
> Hi Grenage


Wow, that is interesting.  I didn't know that you could do that.  Well I managed to mount a clonezilla iso (just for a test).  Could you outline the steps for copying a dvd to iso and then opening the iso as a dvd?  Thanks.

Jim

Hey there,

My first post has the commands you need; you basically mount the iso in a similar fashion to a normal drive.

---

