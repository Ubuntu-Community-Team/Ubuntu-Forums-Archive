---
title: "How to keep digital photos"
date: 2020-12-20
forum: Multimedia Software
---

### Post by satimis on 2020-12-20
Hi all,

Keeping digital photos for sharing there are 2 ways:-

1. Digital Album
2. Website (I don't expect uploading my digital photo to website)

There are digital albums from Open Source, FREE to Download and FREE to Use.
Example: 5 Powerful Photo Album Software To Manage Digital Photos 2020
[https://fliphtml5.com/learning-center/5-powerful-photo-album-software-to-manage-digital-photos/](https://fliphtml5.com/learning-center/5-powerful-photo-album-software-to-manage-digital-photos/)

Which of them shall I try?

Is there a 3rd way sharing photos?  Please advise.

Thanks

Regards

---

### Post by TheFu on 2020-12-20
Only trust dirctory structures if you don't want to be disappointed.
Ensure you have 3 copies of anything you don't want to lose too.

Use yyyy/mm-Event/ for the directories. If you want to capture more metadata about each photo, create a text index fle lke n the 1980s that is easily indexed by search tools - **recoll** is one. There are 20 others. Many image files can can hold text nformation in headers too. This is a little harder.

Avoid any tool that only stores metadata nsde teir own DBMS. That's usually a 1-way process, so we end up filling a DB, but in 3 yrs when our needs change, that data is lost.

I've been burned a few times, if it isn't clear.  My collection is small, with just 28,500 images from travels, life, family. But  can find photos based on some large categories easily. Annals, plants, foods, humans, mountains, sea, stars, weather,  location, date, etc.

---

### Post by satimis on 2020-12-20
Thanks for your advice.

That is for home storage.  But how to share the phones with friends?

If I store the photos in photo albums I can send a copy of that album to my friends

Regards

---

### Post by TheFu on 2020-12-20
I have multiple websites.  Depending on the person I wish to share with ... 
[LIST]
[*]Event Specific websites - I'll send a PM with a link. Don't remember if the site is still public or not.
[*]Nextcloud - family has accounts on my NC site.
[*]Or I use wormhole and they can grab a tgz file full of everything.
[/LIST]

---

### Post by satimis on 2020-12-21
I think finally I have to make use of Internet.

I can create slide shows from photos for sharing, running OpenShot or similar application.  But the video files created are quite large in size.  I have to upload them to YouTube, Dailymotion etc for sharing.  Otherwise I have to save the video files on CD/DVD for sharing.

I have my own website but still I need to upload the video files to YouTube otherwise the broadcasting speed is very slow.

Regards

---

### Post by TheFu on 2020-12-21
If you create videos of photos, be certain to reduce the FPS to 10 fps or lower. No need for 30 or 60 fps just to show images. If you don't care about transitions, 1 fps should be fine.
Heck, you could make a self contained script + images that displays a slideshow fairly easily in a website.  I played around with a JS webapp that did that by customizing each file to be loaded for X seconds.  It wasn't general purpose.  Something like tiddlywiki could probably be used.

---

### Post by SeijiSensei on 2020-12-21
The easiest method I've found for creating slide shows is to make an animated GIF. Typically I use the GIMP for this, opening the first photo normally, then using "Open as Layers" and selecting the remaining photos. It's easiest to have the files ordered appropriately beforehand, but you can move around the layers in the GIMP document if you want. Choose Export, enter a .gif extension, and choose animation and loop forever. Specify a reasonable time for each frame to be on screen like 5000 ms. 

You can also do this from the command prompt with [Imagemagick convert]("https://webinista.com/updates/how-to-create-animated-gifs-imagemagick/").

I don't know about loss of quality but I don't see much decline if any. I've typically done this with ordinary personal photos where high fidelity isn't really the issue.

---

### Post by Holger_Gehrke on 2020-12-21
@SeijiSensei: This is one of the rare occasions I have to disagree with you. GIF is limited to 256 colours so you either get horrible colour-banding or catastrophic dithering. GIF should never be used for photographs and animated GIF should only be used for simple animations; even cartoons often have more than 256 colours.

Holger

---

### Post by SeijiSensei on 2020-12-21
Thanks!

Well, it looks like the only decent solution is creating a movie from the still images using something like [ffmpeg]("https://video.stackexchange.com/questions/7903/how-to-losslessly-encode-a-jpg-image-sequence-to-a-video-in-ffmpeg").

---

### Post by satimis on 2020-12-22
I think finally I have to make use of Internet.

I can create slide shows from photos for sharing, running OpenShot or similar application.  But the video files created are quite large in size.  I have to upload them to YouTube, Dailymotion etc for sharing.  Otherwise I have to save the video files on CD/DVD for sharing.

I have my own website but still I need to upload the video files to YouTube otherwise the broadcasting speed is very slow.

Regards

---

### Post by satimis on 2020-12-22
> **SeijiSensei said:**
> The easiest method I've found for creating slide shows is to make an animated GIF. Typically I use the GIMP for this, opening the first photo normally, then using "Open as Layers" and selecting the remaining photos. It's easiest to have the files ordered appropriately beforehand, but you can move around the layers in the GIMP document if you want. Choose Export, enter a .gif extension, and choose animation and loop forever. Specify a reasonable time for each frame to be on screen like 5000 ms. 

You can also do this from the command prompt with [Imagemagick convert]("https://webinista.com/updates/how-to-create-animated-gifs-imagemagick/").

I don't know about loss of quality but I don't see much decline if any. I've typically done this with ordinary personal photos where high fidelity isn't really the issue.
Hi,

Thanks for your advice.

The reason for me running OpenShot to create slide show are;
1. I can add background music
2. I can add narration
3. I can add fade-in, fade-out etc.
4. I can add sub-title
5. etc.

Regards

---

