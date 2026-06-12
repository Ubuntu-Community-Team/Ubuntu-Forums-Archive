---
title: "Gimp cropping"
date: 2019-09-23
forum: Multimedia Software
---

### Post by Robbyx on 2019-09-23
If I crop an image in gimp, zoom  and export as a jpg how do I ensure that the picture automatically  takes up all of the window's space for the picture, ie I do not want the final picture to be surrounded by a lot of black space.  I am finding that the picture needs to be zoomed in the picture viewer to get it to take up the full screen. I want it to be automatically the right size in the viewer.  What extra adjustments should  I make in gimp to the picture before it is exported to get it to automatically zoom to the full size?

---

### Post by uRock on 2019-09-23
Click **Image**, then **Scale image** to change the size of the image.

---

### Post by Dennis N on 2019-09-23
You could resize, but that gives you a fixed size. If you want automatic zoom to fit the images to any window size, that will be a function of the image viewer. gthumb and pix: **preferences > viewer > after loading images > keep previous zoom** will retain zoom setting once it's set.

Versions: gthumb 3.8.0; pix 1.6.2

---

### Post by Robbyx on 2019-09-23
Thank you both for replying so quickly.

---

### Post by Robbyx on 2019-09-23
Is there a method to work out what image size settings should be chosen? 

I am doing this to produce a picture in ebay for a sale. The item for sale currently is very small in the centre of the shot, and so I need to crop it, and scale the image so as to ensure that when anyone looks at the picture the item for sale will take up the full size of the available space.

---

### Post by SeijiSensei on 2019-09-24
Usually I just pick a specific size for all the images that corresponds to their aspect ratios, like 640x480, and scale the images to that size. If you cut the image out, then scale it up, there shouldn't be any black space.

However if the image you're describing is as small as it sounds, it might look ugly when enlarged.

If you're doing a lot of these, you might want to acquaint yourself with [Imagemagick]("https://imagemagick.org/") convert, which is a command-line tool that can manipulate images in all sorts of ways. You can use it in scripts to iterate over a bunch of images and apply needed transforms.  For instance, here's a script that rotates only images in portrait mode to landscape: [https://ubuntuforums.org/showthread.php?t=1951949&p=11814807&viewfull=1#post11814807](https://ubuntuforums.org/showthread.php?t=1951949&p=11814807&viewfull=1#post11814807)

"sudo apt install imagemagick"

---

### Post by coffeecat on 2019-09-24
From the **Art & Design** sub-forum tagline:

> Discuss various aspects of Ubuntu and Art here. Questions about using software for image editing should go in the Multimedia Software section.


*Thread moved to **Multimedia Software**.*

---

### Post by CatKiller on 2019-09-24
> **Robbyx said:**
> Is there a method to work out what image size settings should be chosen?

The crop tool shows the size of the selected box in the options dialogue, and you can set it to a specific size there as well. Use appropriate values for your use case. For example, were you cropping out an avatar for the Ubuntu Forums, you would pick 90×90 pixels.

As others have already mentioned, the way that the image is *presented* is entirely dependent on the software that's used to present it and the specific attributes of the hardware used to display it. The same 800×600 image, say, is going to be a completely different size on a 21" CRT than it would be on a 300 DPI laptop.

---

### Post by rpaco on 2019-09-27
Size the image to what size you want then crop it then  crop canvas to mage size then flatten layers. then export as whatever filetype  you need. Then save the image in the format Gimp wants in case you need to come back and start again. Also best save the original photo etc. before you start frigging with it.

---

### Post by vanadium on 2019-09-29
The setting ""Current layer only" may be active in your crop tool settings. Make sure it is unchecked: then the crop action will reduce the entire image to the cropped area, also cropping other layers if present.

---

