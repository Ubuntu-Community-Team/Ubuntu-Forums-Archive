---
title: "Automatically scale images with GIMP ?"
date: 2010-07-14
forum: Multimedia Software
---

### Post by oygle on 2010-07-14
Hi,

Is there any method to use GIMP in batch mode, to run from the terminal, and scale all the .JPG files down by 25% ?

Thanks,

Oygle

PS  Maybe this needs to go in the scripting forum, I don't know ??

---

### Post by SteveDee on 2010-07-14
> **oygle said:**
> Hi,

Is there any method to use GIMP in batch mode, to run from the terminal, and scale all the .JPG files down by 25% ?

Thanks,

Oygle

PS  Maybe this needs to go in the scripting forum, I don't know ??

Someone has probably already written a script to do this, or you could write it yourself in Python or script-fu.

The attached script creates 2 copies of an original jpeg; one about the right size for a printed page or full web page, the other is a large thumbnail. This may give you some ideas for your own application.

---

### Post by triften on 2010-07-14
Image Magick and some perl might do the trick.

---

### Post by oygle on 2010-07-14
> **SteveDee said:**
> The attached script creates 2 copies of an original jpeg; one about the right size for a printed page or full web page, the other is a large thumbnail. This may give you some ideas for your own application.

Thanks for that. I downloaded it, and saved it in the path where the images are, then ran this from terminal

```

gimp -i -b web-images.scm

```

and the msg was "batch command experienced an execution error". Then Tried it again by parsing a filename to it, but some other error.

> **triften said:**
> Image Magick and some perl might do the trick.

I did happen to find something, don't know what language it is running ?

```

for i in `ls`; do convert -resize 648x486 -quality 100 $i resized_$i; done

```

but the images all seem ok, all scaled down to 648 x 486, which is 25% on the full size at present. I'd still prefer to use GIMP, but if this small script worsk, then it is okay.

Thanks.  :)

---

### Post by rwgale on 2010-07-14
You can add "gimp-plugin-registry" through synaptic.  Among the add-ins is
 * David's Batch Processor (1.1.9):
    A simple batch processing plugin for The Gimp - it allows
    the user to automatically perform operations (such as resize)
    on a collection of image files.

I use it to remove extra .jpg info and let .jpg files be used as Grub2 SplashImages.  Its easy to use. (access menu: gimp-->filters-->batch-->batch process)

Or you could add David's Batch Processor directly, if you don't want all the rest.

Robert

-------------------------------------------------------------------
The voices might not be real, but they have some pretty good ideas.

---

### Post by SteveDee on 2010-07-15
> **oygle said:**
> Thanks for that. I downloaded it, and saved it in the path where the images are, then ran this from terminal

```

gimp -i -b web-images.scm

```

)

My script should be added to the Gimp scripts folder which is something like: /home/steve/.gimp-2.6/scripts

The script should then appear under the script-fu menu when you run Gimp in the gui and load your target file....which I know is not what you were looking for, but this thread has thrown up many ideas for you to explore...

---

### Post by oygle on 2010-07-15
> **rwgale said:**
> You can add "gimp-plugin-registry" through synaptic.

Or you could add David's Batch Processor directly, if you don't want all the rest.

Added the gimp-plugin-registry, thanks. Just tried David's Natch Processor, wow, very impressed, lots of nice things to do 'on bulk'

> **SteveDee said:**
> My script should be added to the Gimp scripts folder which is something like: /home/steve/.gimp-2.6/scripts

The script should then appear under the script-fu menu when you run Gimp in the gui and load your target file....which I know is not what you were looking for, but this thread has thrown up many ideas for you to explore...

Okay, thanks. Yes, now it is appears under GIMP menu. Lots of ideas alright; thanks everyone for your help,

Oygle

---

