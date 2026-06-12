---
title: "create slideshow movie out of JPGs on a CD that plays in dvd player for TV"
date: 2011-08-07
forum: Multimedia Software
---

### Post by Antarctica32 on 2011-08-07
Ok So I have about 700 JPGs that I need to go into a slideshow with music. If possible I would also like to burn this slideshow onto CDs that can be played in a dvd player for a tv. I think I have an idea of how to make the slideshow. But I have no clue how to burn it or what kind of file it should be and stuff like that. I know how to make a slideshow with music in pitivi and save it as an avi, but is there an easier way than just drag and drop jpgs? All help of any kind is greatly appreciated.

---

### Post by haqking on 2011-08-07
> **Antarctica32 said:**
> Ok So I have about 700 JPGs that I need to go into a slideshow with music. If possible I would also like to burn this slideshow onto CDs that can be played in a dvd player for a tv. I think I have an idea of how to make the slideshow. But I have no clue how to burn it or what kind of file it should be and stuff like that. I know how to make a slideshow with music in pitivi and save it as an avi, but is there an easier way than just drag and drop jpgs? All help of any kind is greatly appreciated.

mandvd

dvd slideshow [http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

imagination (sudo apt-get install imagination)

all are good and will do what you want.

---

### Post by Antarctica32 on 2011-08-07
The apps you gave me work great with creating the slideshow, except I still can't burn it to a CD. MANdvd only burns to dvd. Would it be possible to play a CD with a video on it in a DVD player?

---

### Post by haqking on 2011-08-07
> **Antarctica32 said:**
> The apps you gave me work great with creating the slideshow, except I still can't burn it to a CD. MANdvd only burns to dvd. Would it be possible to play a CD with a video on it in a DVD player?


use brasero or K3b it burn the file.

I cant remember if any of them support CD to be honest, been a while and i dont thave them installed anymore.  Any reason you cant use a DVD ? if you want to use a CD then you need to create a video CD from the files you create, K3b can do this.

---

### Post by Antarctica32 on 2011-08-07
The reason I have to use CDs is because thats all I have. And K3B only accepts mpeg-1 and mpeg-2 files. I have searched for a while now and have found no way to convert my avi slideshow made in pitivi to mpeg1/2. Any help?

---

### Post by haqking on 2011-08-07
> **Antarctica32 said:**
> The reason I have to use CDs is because thats all I have. And K3B only accepts mpeg-1 and mpeg-2 files. I have searched for a while now and have found no way to convert my avi slideshow made in pitivi to mpeg1/2. Any help?

i am confused, now you are asking about converting an avi made in pitivi ?

so you already have a slideshow and it is a .avi ? which needs to be burned to a CD ?

use digikam, as that will create a mpeg slideshow you cna burn to cd or dvd

---

### Post by Antarctica32 on 2011-08-07
Well yeah, sorry. I have an avi I made in pitivi, but I could make the slideshow in something else. All I need to do is somehow make it play in a dvd player on a cd

---

### Post by haqking on 2011-08-07
> **Antarctica32 said:**
> Well yeah, sorry. I have an avi I made in pitivi, but I could make the slideshow in something else. All I need to do is somehow make it play in a dvd player on a cd


digikam like i said before.

or if you have the .avi already then avidemux and k3b.

see here

[http://www.ubuntugeek.com/make-a-vcd-from-an-avi-using-avidemux-and-k3b.html](http://www.ubuntugeek.com/make-a-vcd-from-an-avi-using-avidemux-and-k3b.html)

---

### Post by Antarctica32 on 2011-08-07
whenever I go to add the avi file in avidemux it gives me this:

---

### Post by haqking on 2011-08-07
> **Antarctica32 said:**
> whenever I go to add the avi file in avidemux it gives me this:

does the .avi play in say vlc or whatever media player you have.

what i mean is, is the file corrupt ?

i take it you are following the instruction in the link i provided ?

there are lots of ways to do this so let me know as i can provide lots more app options which do the same thing

---

### Post by Antarctica32 on 2011-08-07
Yeah the file plays in vlc and movie player. Sorry for making this difficult, im not that good with computers

---

### Post by SeijiSensei on 2011-08-09
You *might* be able to use DeVeDe to create an ISO image from the AVI file, then burn the ISO to the CD with k3b.  That assumes the ISO is less than the 700 MB maximum size of a CD.

---

### Post by haqking on 2011-08-09
> **SeijiSensei said:**
> You *might* be able to use DeVeDe to create an ISO image from the AVI file, then burn the ISO to the CD with k3b.  That assumes the ISO is less than the 700 MB maximum size of a CD.

+1

Good point, yeah he has a .avi file so he can use the Video CD option in DeVeDe as long as you say it is below 700Mb.
If it is higher then you will have to choose a DVD.

---

### Post by Antarctica32 on 2011-08-09
yeah about that .avi file.....
I just wanted to see if it would play on a windows because I'm going to make like 50 of these and give them to guys I know that will use windows. So I put it on a flash drive and tried to open it with windows media whatever and it gave me an error :confused::(:confused:, it said something about it not being a supported file type which is BS so it must be like corrupted (which its not cuz i ran it on my desktop)!!!
I feel so stupid

---

### Post by cotcot on 2011-08-09
I understand that you do not have the possibility to burn DVD's and that you want to play a video CD in a dvd player.

[[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html") can burn video CD's.  Devede is in the repositories.

In your first post you say that you want to add music which means that you have to go for a video format. So your .avi is OK. You can use your .avi in devede to make an iso file to burn with k3b or brasero to the CD or you can burn it directly with devede.

---

### Post by haqking on 2011-08-09
> **Antarctica32 said:**
> yeah about that .avi file.....
I just wanted to see if it would play on a windows because I'm going to make like 50 of these and give them to guys I know that will use windows. So I put it on a flash drive and tried to open it with windows media whatever and it gave me an error :confused::(:confused:, it said something about it not being a supported file type which is BS so it must be like corrupted (which its not cuz i ran it on my desktop)!!!
I feel so stupid

yeah but as stated if you convert the .avi to a video cd you remove the .avi compatability issues on the windows machines.  They will be playing a VideoCD not a .avi.

as said DeVeDe can do this

---

### Post by Antarctica32 on 2011-08-09
OK I will try that. But the thing is I thought avi was completely compatible with windows? guess it doesn't matter

---

### Post by haqking on 2011-08-09
> **Antarctica32 said:**
> OK I will try that. But the thing is I thought avi was completely compatible with windows? guess it doesn't matter


well you want to use a VideoCD so it is irrelevant as they wont be viewing an  .avi they will be viewing a .vcd

---

### Post by Antarctica32 on 2011-08-09
OMG it worked! I love ubuntu! thank you guys sooo much! Ok,now I just have to do that 50 times

---

### Post by haqking on 2011-08-10
> **Antarctica32 said:**
> OMG it worked! I love ubuntu! thank you guys sooo much! Ok,now I just have to do that 50 times

you are welcome.  Congrats.

as for 50 times, not much to do about that apart from make your own .torrent file from it and upload it for them to download possibly

---

### Post by Antarctica32 on 2011-08-10
yes, thank you all soo much, please accept 12 Internets.

---

### Post by SeijiSensei on 2011-08-10
> **Antarctica32 said:**
> OK I will try that. But the thing is I thought avi was completely compatible with windows? guess it doesn't matter

AVI is a "container" format.  What matters is how the material inside the container is formatted.  AVI does well with Windows Media formats (WM*) and with things like DivX/XviD.  Whether it would play the file you created depends on the codec used to encode the video.

---

