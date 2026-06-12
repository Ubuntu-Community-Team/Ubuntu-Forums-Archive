---
title: "Autokey and GIMP"
date: 2013-06-27
forum: Multimedia Software
---

### Post by silbar on 2013-06-27
Greetings,

I have about a thousand JPEG images that I want to resize from 300 x 300 pixels/inch to 72 x 72 pixels/inch.  Hoping to do this  efficiently, I installed Autokey to be able to do this after taking the *.jpg file into GIMP.  

Manually, I can do the resize in GIMP with the following keystrokes:

<alt>+i 
# opens the image pulldown menu
s
# selects the Scale Image option and opens that window
<tab><tab><tab><tab>
# tabs down to the X resolution slot
72
# changes both X and Y resolutions from 300 x 300 to 72 x 72
<tab><tab><tab><tab><tab><tab><tab><tab>
# tabs down to highlight the Scale button
<enter>
# does the rescaling, and the scaling window disappears
<ctrl>+s
# now starts to save the modified GIMP window with the *.jpg image[INDENT]
<enter>
# completes the save


It would seem that all these keystrokes could be automated with a Autokey phrase.

Unfortunately, I cannot get Autokey to go beyond the first line.  The "<alt>+i" does open the pulldown menu, but the following "s" does not bring up the scaling window.  Nor would a second line consisting of six <down>'s and an <enter>.  So, I am stuck.

I have also tried to do this with a Autokey python script rather than an Autokey phrase.  In this case, I put in a "time.sleep(2)" after the "keyboard.send_keys("<alt>+i")" command, but here too I cannot proceed past getting the pulldown menu.

Perhaps one way to work around this problem is if there is a way to directly bring up the scaling window with a keyboard command.  Does any GIMPer  know how to do that?

Richard Silbar

---

### Post by Cheesemill on 2013-06-27
This is the perfect example of when to use the terminal instead of a GUI program. First of all install imagemagick if you don't already have it...
```
sudo apt-get install imagemagick
```
This will let you use the convert command to resize your images, for example...
```
convert -resize 75x75 image.jpg resized_image.jpg
```
will resize image.jpg to 75x75 and save the result as resized_image.jpg


If you want to do this on all jpg files in a directory then you could use the following command...
```
for i in *.jpg; do convert -resize 75x75 "$i" resized_"$i"; done
```

---

### Post by silbar on 2013-06-27
Thanks, Cheesemill,

After I posted, I started looking around elsewhere in the forum and did find out about imagemagick's convert.  However, in looking at its man page, I found there were a gazillion options, none of which was obviously meant for what I wanted to do.  Cheesemill has now pointed me at -resize as the way to go.  Which I will proceed to use (later this afternoon).  Nonetheless, I'm still curious about how one could make Autokey work with a pulldown menu.

RRS

---

### Post by silbar on 2013-06-27
Oops!

Following Cheesemill's -resize suggestion, I find it doesn't do what I wanted to do to the resolution. After
```
convert -resize 72x72 Church.jpg CChurch.jpg 
```
I find that it converts a 360 by 251 pixels image at 300x300 resolution into size 72x50 at 300x300 (still).

So, -resize is not the right convert option.  Which option does handle resolution?

RRS

---

### Post by silbar on 2013-06-27
Okay!  After a Google search on "imagemagick convert resolution to dpi", I found, by a person nicknamed Draradel,

[http://www.imagemagick.org/discourse-server/viewtopic.php?f=2&t=18241](http://www.imagemagick.org/discourse-server/viewtopic.php?f=2&t=18241)

So, the following DOES work properly:

```
convert -units pixelsperinch Church.jpg -density 72 CChurch.jpg 
```

turning a 360 by 251 pixels image at 300x300 resolution into size 360 by 251 at 72x72.

Now about to proceed converting in batch mode.

RRS

---

### Post by Cheesemill on 2013-06-27
You beat me to it, I was just going to post back about the -density switch :cool:

---

