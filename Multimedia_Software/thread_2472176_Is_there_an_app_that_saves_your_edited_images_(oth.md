---
title: "Is there an app that saves your edited images (other than shotwell)?"
date: 2022-02-20
forum: Multimedia Software
---

### Post by flyingvluvr on 2022-02-20
Because shotwell doesn’t save your edited images. Is there an app in Ubuntu 20.04 LTS that will?

Thanks for any info.

---

### Post by mIk3_08 on 2022-02-20
> **flyingvluvr said:**
> Because shotwell doesn’t save your edited images. Is there an app in Ubuntu 20.04 LTS that will?

Thanks for any info.
You can use gimp. Gimp is an image editor application software. You can install gimp via Ubuntu software or you can install via cli in terminal. 
```
sudo apt install application name
``` 
Good luck and cheers

---

### Post by Holger_Gehrke on 2022-02-20
Or you just might take a look at the manual at [shotwell.org]("http://shotwell-project.org/doc/html/index.html"). You'll find that Shotwell stores your pictures as they originally are and stores all changes separately in a database. If you want your pictures in the edited form in another program you'll have to export them by having Shotwell and a file manager open and dragging the pictures from shotwell into a folder in the file manager. You'll then get a form in which you can select to export either unmodified or current picture. This is done because most digital cameras store pictures in the lossy JPEG format. Each time you change a picture and save it in jpeg you loose a bit more. By not repeatedly saving the pictures after every edit Shotwell keeps the original quality of the image.

Holger

---

### Post by TheFu on 2022-02-20
I use tools from the ImageMagick suite. They can do almost anything. The manpage is fairly complete, but there are so many wizard-skill level things that people have complete websites [http://www.fmwconcepts.com/imagemagick/index.php](http://www.fmwconcepts.com/imagemagick/index.php) just for creating different effects for images using the suite.
> NAME
       ImageMagick  -  is a free software suite for the creation, modification
       and display of bitmap images.
...
SEE ALSO
       convert-im6.q16(1), identify-im6.q16(1), composite-im6.q16(1), montage-
       im6.q16(1), compare-im6.q16(1), display-im6.q16(1), animate-im6.q16(1),
       import-im6.q16(1), conjure-im6.q16(1), quantize(5), miff(4)

Obviously, ImageMagick isn't for everyone, but there are times when I need to process 500 images and doing that with a GUI would take forever. No thanks. ImageMagick to the rescue.  gthumb is another.

---

### Post by flyingvluvr on 2022-02-20
Thanks for the replies, guys.  Right now I’m checking out Gthumb. If that doesn’t work out, I’ll try GIMP.

---

### Post by flyingvluvr on 2022-02-20
Okay, I installed GIMP, but the Editor is pretty confusing. So what I do is Edit an image in Shotwell (which is a very good editor, better than Gthumb), but I made GIMP my External Editor, and Export the image from there. That seems to work okay.

---

### Post by flyingvluvr on 2022-02-20
> **Holger_Gehrke said:**
> Or you just might take a look at the manual at [shotwell.org]("http://shotwell-project.org/doc/html/index.html"). You'll find that Shotwell stores your pictures as they originally are and stores all changes separately in a database. If you want your pictures in the edited form in another program you'll have to export them by having Shotwell and a file manager open and dragging the pictures from shotwell into a folder in the file manager. You'll then get a form in which you can select to export either unmodified or current picture. This is done because most digital cameras store pictures in the lossy JPEG format. Each time you change a picture and save it in jpeg you loose a bit more. By not repeatedly saving the pictures after every edit Shotwell keeps the original quality of the image.

Holger

Thanks for the info, Holger, that's what I ended up doing.

---

