---
title: "Problem burning .iso file"
date: 2010-09-25
forum: Multimedia Software
---

### Post by squidink14 on 2010-09-25
I have an iso file that I have been trying to burn to a blank 4.7gig DVD disk.
I have tried 3 programs and they all do the same thing. It will burn up to 100% and say success but there is actually nothing on the disk. When I insert the disk it comes up with a window saying I have inserted a black DVD+R disk.

But when I look at the disk, you can see where it has been burnt on to it, I have tried on 3 disks now and it is really annoying me!

---

### Post by skyjacker on 2010-09-25
Have you tried the "startup disk creator" in the Systems group?  I use it for any .iso file I have needed, and it hasn't failed me yet.

---

### Post by squidink14 on 2010-09-25
> **skyjacker said:**
> Have you tried the "startup disk creator" in the Systems group?  I use it for any .iso file I have needed, and it hasn't failed me yet.

Okay, thanks will try now

---

### Post by squidink14 on 2010-09-25
I can't get it to work. I select the iso and it doesn't show up on the program, neither does the blank DVD, but it is showing in the 'Places' list.

---

### Post by BrockStrongo on 2010-09-25
This is just what I do, and it works for me. I right click on the .iso file I want to burn, and select write to disk. I select "burnproof" and "simulate before before burning" in the properties menu. I also select a slow write speed, 4-6x. In the past I have found that burning at max speed or anything over 12x results in bad burns. IMO the slower the write speed the less chance of errors.
 again this is just in my experience.
Cheers

---

### Post by squidink14 on 2010-09-25
> **BrockStrongo said:**
> This is just what I do, and it works for me. I right click on the .iso file I want to burn, and select write to disk. I select "burnproof" and "simulate before before burning" in the properties menu. I also select a slow write speed, 4-6x. In the past I have found that burning at max speed or anything over 12x results in bad burns. IMO the slower the write speed the less chance of errors.
 again this is just in my experience.
Cheers

Okay, burning at 6x, I was doing it a 20x. Hope it works!

---

### Post by squidink14 on 2010-09-25
> **squidink14 said:**
> Okay, burning at 6x, I was doing it a 20x. Hope it works!

No! Still a blank disk. Ill have to see if it works on Windows another time. I thought Ubuntu would be better than this!

---

### Post by tony van on 2010-09-25
must burn at lowest rate possible.
 
there are a few cd burners high lighted by others. I had to do it 4 times before it worked also get a sumchecker.

---

### Post by BrockStrongo on 2010-09-25
> **squidink14 said:**
> No! Still a blank disk. Ill have to see if it works on Windows another time. I thought Ubuntu would be better than this!

Bummer, can you still use the "blank" dvd to try burning again, or is the dvd garbage now? the dvds I use are DVD-R I don't know if these are different from DVD+R. Yeah check the burner with windows, at least you will be able to rule out h/w issues.

---

### Post by skyjacker on 2010-09-25
> **BrockStrongo said:**
> Bummer, can you still use the "blank" dvd to try burning again, or is the dvd garbage now? the dvds I use are DVD-R I don't know if these are different from DVD+R. Yeah check the burner with windows, at least you will be able to rule out h/w issues.I only use DVD -r also.  Don't know if +R will work or not.  Is the file small enough that you could burn it to a CD. Try that and see if you have any luck... Let us know.

---

### Post by squidink14 on 2010-09-26
> **skyjacker said:**
> I only use DVD -r also.  Don't know if +R will work or not.  Is the file small enough that you could burn it to a CD. Try that and see if you have any luck... Let us know.
The .iso file is 3GB and the Disk is 4.7GB.
It is really strange though as I can see where it has been burnt on the disk. Maybe it is something to do with permissions?

---

### Post by squidink14 on 2010-09-26
Here are some pics - I used K3b for this

Blank DVD+R Disk
[IMG]http://www.flickr.com/photos/48950348@N02/5025877864/[/IMG] - [http://www.flickr.com/photos/48950348@N02/5025877864/](http://www.flickr.com/photos/48950348@N02/5025877864/)

Burning at 4x speed
[IMG]http://www.flickr.com/photos/48950348@N02/5025878088/[/IMG] - [http://www.flickr.com/photos/48950348@N02/5025878088/](http://www.flickr.com/photos/48950348@N02/5025878088/)

Completed
[IMG]http://www.flickr.com/photos/48950348@N02/5025878290/[/IMG] - [http://www.flickr.com/photos/48950348@N02/5025878290/](http://www.flickr.com/photos/48950348@N02/5025878290/)

Still blank disk
[IMG]http://www.flickr.com/photos/48950348@N02/5025878414/[/IMG] - [http://www.flickr.com/photos/48950348@N02/5025878414/](http://www.flickr.com/photos/48950348@N02/5025878414/)

Cant be my DVD/CD Drive though as it still reads my Ubuntu 10.04 disk
[IMG]http://www.flickr.com/photos/48950348@N02/5025262941/[/IMG] - [http://www.flickr.com/photos/48950348@N02/5025262941/](http://www.flickr.com/photos/48950348@N02/5025262941/)

---

### Post by BrockStrongo on 2010-09-28
Sorry I can't offer much more advice. I am not familiar with K3b or Kubuntu at all really.
Here is a thread that might be of interest [http://ubuntuforums.org/archive/index.php/t-578646.html](http://ubuntuforums.org/archive/index.php/t-578646.html) , it's old but has some trouble shooting tips you might want to try. Particularly the part about burning from command line. I noticed in your pictures that the disk buffer and software buffer were both at 100%. I don't know if that is normal. Maybe give Brasero or some other program a try.   
I realize this is really frustrating, hope you find a solution

---

### Post by Zuul47 on 2010-09-29
Brasero didnt work???

install WINE through software center, then download and install ImgBurn(windows program)...this program checks the disk afterwards

:guitar:

---

