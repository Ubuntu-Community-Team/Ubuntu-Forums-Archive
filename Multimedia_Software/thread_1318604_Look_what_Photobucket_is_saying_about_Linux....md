---
title: "Look what Photobucket is saying about Linux..."
date: 2009-11-07
forum: Multimedia Software
---

### Post by Indy452 on 2009-11-07
Dear ...

The issues are not with the camera or files. The issues you are having are due
to the Linux OS. Please note we do not support this operating system(OS) and
at this time you must update your OS for full functionality. Please read the
following FAQ link in regards to supported OS.

[http://photobucket.com/faq?catID=57&catSelected=f&topicID=739](http://photobucket.com/faq?catID=57&catSelected=f&topicID=739)

Sincerely,

Your Photobucket Support Team

------
Online Help Center: [http://photobucket.com/tips.php](http://photobucket.com/tips.php)
FAQ's: [http://photobucket.com/faq](http://photobucket.com/faq)
Support Forums: [http://forums.photobucket.com](http://forums.photobucket.com)
Support Email: [email]support@photobucket.com[/email]



.com wrote:

> I recently purchased a Sony cybershot DSC-W190 and I have added all the photos
> I've taken from this camera to a folder in my computer, but for some reason
> when I go to upload them from this particular camera, photobucket does not see
> them. Why is that?
> I need to upload the pictures that the Sony has taken but I'm unable to if
> photobucket cannot see them in my folder from my computer.  Its really weird.
>
> What do you suggest?
>
> username: Indy452
> 
>
>  User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4)
> Gecko/20091028 Ubuntu/9.10 (karmic) Firefox/3.5.4
>
>  IP Address: 
> 

[COLOR="Red"]
Is this BS or are they correct?  I've used Linux the past 4 years and uploaded hundreds of photos using Linux on my photobucket account in the past all with linux...[/COLOR]

---

### Post by detroit/zero on 2009-11-07
Just a thought: Double check your file extensions. I have a problem with a Canon PowerShot camera - it uses all-caps extensions (e.g., .JPEG or .JPG) and on some photo-upload sites, when the upload window opens and has selection of file types (.png, .jpg, .gif, etc..) Linux will make the distinction between the all-capped names and the lower-case names, and since in Linux .JPG is not the same as .jpg, it looks like you don't have any files to upload.

I could be way off, though...

---

### Post by Indy452 on 2009-11-07
> **detroit/zero said:**
> Just a thought: Double check your file extensions. I have a problem with a Canon PowerShot camera - it uses all-caps extensions (e.g., .JPEG or .JPG) and on some photo-upload sites, when the upload window opens and has selection of file types (.png, .jpg, .gif, etc..) Linux will make the distinction between the all-capped names and the lower-case names, and since in Linux .JPG is not the same as .jpg, it looks like you don't have any files to upload.

I could be way off, though...

Well, you are spot on...thank you!  I noticed the Sony camera uses Capital JPG and so I changed the file name to jpg and now photobucket is recognizing the files...:D  Shows what Photobuckets support staff know.....They are trying to tell me that my version of Firefox (3.5.4) won't work with Photobucket.  Do they think that Linux is still in the dark ages?? Geezzz.  

Thanks for the tip Det/zero...!

---

### Post by Indy452 on 2009-11-07
I guess now my question is.....how do I get the camera to load jpg to my computer every time rather than JPG? Hmmmmmm.  That way I won't need to change every file name each time I load the pics.

---

### Post by jms1989 on 2009-11-07
I've been using linux for a least 4 years and I got to say the Photobucket staff knows nothing about computers. The problem is not linux, it's the image filename. On windows, it's not case sensitive but on linux it is case sensitive. 

My recommendation is to try pyrenamer. Run that every time you copy more photos to your computer. There might be a way to do a "cp /media/camera/image.JPG ~/photos/image.jpg" type deal without having to run a copy and then rename process.


sudo apt-get install pyrenamer or [apt://pyrenamer]("apt://pyrenamer")

Hope this helps, cheers.

---

### Post by ian2112 on 2009-11-08
I experienced the same problem (and solution) but the root cause was different.  It happened to me when I upgraded from 9.04 to 9.10. Same camera, only after the upgrade the photos were named in uppercase.  Weird.

The work-around I used was a nautilus script (see [https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts) for an explanation).  I'm not sure where I downloaded the script from (there were a ton of other functions bundled with it), but google something like "nautilus script lowercase" and I'm sure you'll find several options.

If you're like me, you also resize (lower) the photos before uploading to conserve on space, and upload time.  So the package of scripts I found has a 'resize' function as well.  It means I can select all the photos I just moved to computer and resize them at once.  I don't have to open each one and re-save it at a reduced size / resolution.

So... another possible work-around to the lowercase thing.

---

