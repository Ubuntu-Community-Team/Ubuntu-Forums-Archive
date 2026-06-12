---
title: "Ripping images  from web pages"
date: 2009-10-05
forum: Multimedia Software
---

### Post by sofasurfer on 2009-10-05
Some web pages have images that can not be saved or copied. How do they accomplish this and is there a way to rip the image from the page?

---

### Post by Lampi on 2009-10-05
> **sofasurfer said:**
> Some web pages have images that can not be saved or copied. How do they accomplish this and is there a way to rip the image from the page?
they just switched off the right click menu with some html code. you can use firefox addon live-http-headers and reload the site. it will show you what files your browser requested. Among these files will be the image - now you have the download url and can load the file directly in your browser.

---

### Post by pmlxuser on 2009-10-05
just go to the firefox folder in your home directory (assuming you are using ubuntu..

 ~/.mozilla/firefox/y7ji2hue/(somethinglikethat).default/Cache/

you will find all loaded images and you can just copy them to some other location of your liking.

---

### Post by sofasurfer on 2009-10-05
Thanks for repying guys.
The firefox addon live-http-headers has no links that take me to the image I want. I'm sure I just don't understand yet. I'll try again.

The Firefox home directory thing is a treasure chest of unknown knowledge. BUT, the images in there are only icons that just show a small part of the actual image. Can you explain further?

And, there are various "default" folders and they all seem to have a specific type of image that they are reserved for, or maybe a particular time period (based on the contents of the "bookmarks backup" folders in them). Any knowledge on this?

---

### Post by Lampi on 2009-10-05
I agree live-http-headers can be a handful if you try it for the first time.

So you might be better of with a look in your browser cache. I recommend you clean the cache first (firefox > extras > clear private data). Otherwise you will be lost completely with tons of icons and images from other sites.

Now make sure the cache is clear, I realized I had to wipe the cache manuallly in nautilius once more with a few leftovers firefox refused to remove.

Then reload firefox and the website, make sure you have mime-types visible in nautilus, then you can sort mime-types and browse the images. 

Hopefully you find the image you where looking for.

Otherwise you'll have to dig into live-http-headers to learn how to use it - it's very useful for all kinds of stuff (finding url to embedded videos for example)

---

### Post by sofasurfer on 2009-10-05
What I am seeing in my cache folder is, for instance, anywhere from 4 to 20 icons (depending on the size of the image) which would need to be stitched together to form a complete image. Apparently the image is grabbed from the internet in sections, 1 at a time, and then reassembled be the computer. Do you understand what I am saying? Is this what happens on your computer? Is manual reassembly the only way or is there another way?
Thanks for your time.

---

### Post by gordintoronto on 2009-10-05
You could always copy the window and paste it into GIMP.

---

### Post by mike67114 on 2009-10-05
have you tried simply taking a screenshot?

If you have the 'gnome-utils' package installed (through synaptic) you can go to 'Applications -> Accessories -> Take Screenshot' and open a nifty screenshot application that allows you to take screenshots of the entire screen, the open window or a selected area of your screen. 

I save Internet images by selecting the option to grab a selected area. Clicking the 'Take Screenshot' button turns your cursor into a cross hair. You then select  your image and 
select 'Save' on the pop up window that appears.

Your screenshot is saved to your default downloads folder with the name 'screenshot'. Open the downloads folder and rename, move, view or whatever with the image.

---

### Post by sofasurfer on 2009-10-05
Thanks. Will try it after work.

---

