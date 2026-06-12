---
title: "F Spot"
date: 2009-04-07
forum: Multimedia Software
---

### Post by 3dmatrix on 2009-04-07
I am using F Spot since a few months and find it a wonderful software to manage pictures. Though most of my pictures are taken with a digital camera but there are some which are the old style film camera stuff and were scanned and imported in to F Spot. Now as these pics usually do not have any Exif Meta data embedded in it, the problem that I face with these pics is, that they are not allowed to be edited, enlarged or 'Open with' any other application, which I can do for the other pics. If I rt click on these pics and go to 'open with' it displays 'No Application Available'. When I double click on these thumbnails they dont get enlarged. How can I solve this problem. Is there any way I cud embed a minimum basic Meta Data to avoid this trouble ? If so how ?

---

### Post by bubwitmaingay on 2009-04-07
Here's how it could be done:

Do not open it with F-Spot when you view it. Open the directory where the images were saved and right-click on the file. Then go to "Properties", click on that. When the properties window opens, click the "Open with" tab. On that tab, you will see two buttons "+Add" and "-Remove", click "+Add" and a new menu window will appear and will list all available application that you can use for viewing and editing images (such as GIMP).

If no list will appear, click the chevron (it's the standing triangle) on the side of "Use a custom command". If you don't know what command to place there, click the "browse" button, and a new directory window will open - search for the application there. Click "Open", then it will go back to the "Add Application" window, then click "+Add". Close the properties window.

Try to double-click on the file to see if it opens on your desired application.

---

### Post by 3dmatrix on 2009-04-07
If I have to do that then what is the point in using F Spot ? I need a picture manager from where I can manage all my pictures. If I have to search around the directories looking for that pic and then open it, then why use F Spot in the first place. I feel if we can 'insert' a minimum basic Exif tag in those pics then F spot will start accepting them as normal pics. I wish to know how to do that.

---

### Post by lovinglinux on 2009-04-07
The lack of Exif metadata has nothing to do with the ability to edit the file. It's just metadata. Some editors can edit image files even if they do not support Exif, which probably results in a output file without any metadata at all.

You problem could be a related to file format or data corruption. Try batch converting those files with a program like Phatch (don't override the original to be safe) and check if you can edit the converted copies on F-Spot.

Despite the fact that Exif can be edited by some applications, it is usually created by the camera. So if you need to add tags, you should use IPTC, which is another popular tagging system. Digikam can handle Exif and IPTC. A simple alternative is Picasa.

Please be aware that F-Spot can embed tags only into jpgs. Tags of any other file format is stored on a database, which means you can't read those tags with other programs and if you loose the database, you loose all tags.

---

### Post by lovinglinux on 2009-04-07
BTW, you can edit EXIF data with this tool [http://owl.phy.queensu.ca/~phil/exiftool/](http://owl.phy.queensu.ca/~phil/exiftool/). More Exif editors here [http://www.digital-photo-software-guide.com/exif-editor.html](http://www.digital-photo-software-guide.com/exif-editor.html)

---

### Post by 3dmatrix on 2009-04-08
Thanx lovinglinux, I will tryout those links.
BTW I would like to tell you that those images are not corrupt as FSpot shows them as thumbnails but is unable to edit them or hand them over to any other application to edit them, it cannot even enlarge them. I can also edit those files on Gimp if I attempt to do so without going through F Spot. So in that case what is your suggestion ? These are those files which have been scanned or whose EXIF data has been 'removed' purposely when doing a save as in Gimp.

---

### Post by lovinglinux on 2009-04-08
> **3dmatrix said:**
> Thanx lovinglinux, I will tryout those links.
BTW I would like to tell you that those images are not corrupt as FSpot shows them as thumbnails but is unable to edit them or hand them over to any other application to edit them, it cannot even enlarge them. I can also edit those files on Gimp if I attempt to do so without going through F Spot. So in that case what is your suggestion ? These are those files which have been scanned or whose EXIF data has been 'removed' purposely when doing a save as in Gimp.

I don't know if this is the case, but what I mean by corruption does not necessarily prevent the file from being thumbnailed, but can prevent a specific application to recognize the format and the corresponding editor. 

Anyways, have you checked if those files have an extension? Linux does not require extensions to read files, but maybe you saved them using a specific format and a different extension, so F-Spot could be having trouble to recognize an application to edit them. I'm just guessing, but it is possible.

Can you upload one of those images so I can test it here?

---

### Post by 3dmatrix on 2009-04-10
Attached a pic for you to check.

---

### Post by lovinglinux on 2009-04-10
> **3dmatrix said:**
> Attached a pic for you to check.

Something is wrong in your system. I can open that image with Gimp, Phatch, gThumb and others through F-Spot context menu without problems.

---

### Post by 3dmatrix on 2009-04-11
Can any one tell me what can be the problem in my system and how it could be corrected ? I have upgraded to the latest version of FSpot through synaptic but the problem remains.

---

### Post by bubwitmaingay on 2009-04-11
> **3dmatrix said:**
> If I have to do that then what is the point in using F Spot ? I need a picture manager from where I can manage all my pictures. If I have to search around the directories looking for that pic and then open it, then why use F Spot in the first place. I feel if we can 'insert' a minimum basic Exif tag in those pics then F spot will start accepting them as normal pics. I wish to know how to do that.

If you want to edit your pictures, you need to use another software. F-Spot is just to manage your pictures - in short, arranges them and all. A meta-data is not a guarantee that you can edit files.

Of course, you can edit the digital pictures in F-Spot, but if you have problems with the scanned images - that's when some other utilities have to be utilized. 8)

---

### Post by lovinglinux on 2009-04-11
> **bubwitmaingay said:**
> If you want to edit your pictures, you need to use another software. F-Spot is just to manage your pictures - in short, arranges them and all. A meta-data is not a guarantee that you can edit files.

Of course, you can edit the digital pictures in F-Spot, but if you have problems with the scanned images - that's when some other utilities have to be utilized. 8)

He doesn't want to edit with F-Spot, he wants to be able to launch an image from F-Spot using an image editor like Gimp. The problem is that he can't open some images with Gimp through the F-Spot context menu, which F-Spot should be capable of doing.

---

### Post by bubwitmaingay on 2009-04-11
Here's your picture and I was able to edit in GIMP.

---

### Post by 3dmatrix on 2009-04-11
**lovinglinux :** When i check such images' meta data from F Spots Metadata Browser then I get the following result :
[I][U]Exported Locations
The photo "file:///home/xyz/Photos/2009/04/06/Orchid-4.jpg" does not exist[/U][/I]
With others I get normal reply. Moreover, it is not only SCANNED images that create trouble (the picture attached here is NOT a scanned image) any picture whose meta data has been removed creates trouble. The attached pic was taken with my Digicam and in gimp it was 'saved as' with 'do not save exif data' option.

**bubwitmaingay :** Perhaps you have not been able to understand the problem I am referring to. Were u able to edit that pic in Gimp straight off or u were able to edit it in Gimp by opening it THROUGH Fspot ? Direct opening in Gimp is always working that is not what I am referring to in this post. I am trying to highlight a problem I am facing in FSpot. Moreover, atleast F Spot should ENLARGE the pic when a thumbnail is double clicked (as it does with all other pics) but it cannot do that for these pics on my system.

Try to see the attached images and see the context menu in both. Also see the image properties on the bottom left side of the pics. Perhaps you will be able to understand what I am referring to.

---

### Post by lovinglinux on 2009-04-12
> **3dmatrix said:**
> **lovinglinux :** When i check such images' meta data from F Spots Metadata Browser then I get the following result :
[I][U]Exported Locations
The photo "file:///home/xyz/Photos/2009/04/06/Orchid-4.jpg" does not exist[/U][/I]
With others I get normal reply. Moreover, it is not only SCANNED images that create trouble (the picture attached here is NOT a scanned image) any picture whose meta data has been removed creates trouble. The attached pic was taken with my Digicam and in gimp it was 'saved as' with 'do not save exif data' option.

Have you checked if file:///home/xyz/Photos/2009/04/06/Orchid-4.jpg really exists? Maybe you could remove the problematic images from F-Spot database and import them again.

---

### Post by glotz on 2009-04-12
May I suggest an image browser I find far superior to f-spot:

[http://gqview.sourceforge.net/](http://gqview.sourceforge.net/)

---

### Post by 3dmatrix on 2009-04-12
lovinglinux : Ofcourse it exists :) I attached that image here, from that folder. Moreover, as I said its not only THAT one image that is creating trouble. There are dozens of images that are either scanned or whose exif data has been removed are creating this trouble. You give me any image, i will import it in F Spot and it will work fine. Then i will save as that image in gimp with the exif data save turned off, and then import that image in FSpot and this new image will give this same trouble. :) Seems there is some lib file that coordinates with the exif data in images for F Spot, and some how that file is missing in my system or there is a bug in F Spot.

---

### Post by lovinglinux on 2009-04-12
> **3dmatrix said:**
> lovinglinux : Ofcourse it exists :) I attached that image here, from that folder. Moreover, as I said its not only THAT one image that is creating trouble. There are dozens of images that are either scanned or whose exif data has been removed are creating this trouble. You give me any image, i will import it in F Spot and it will work fine. Then i will save as that image in gimp with the exif data save turned off, and then import that image in FSpot and this new image will give this same trouble. :) Seems there is some lib file that coordinates with the exif data in images for F Spot, and some how that file is missing in my system or there is a bug in F Spot.

Maybe you should try to re-install Gimp. I did exactly the same thing and it works on F-Spot, even without saving the exif. So I guess your Gimp is messing with the images. You should try editing an image that works in F-Spot with another program (without saving exif) and with Gimp (preserving the exif) to see if they work.

---

### Post by 3dmatrix on 2009-04-12
But what abt the scanned images ? Even they dont work in FSpot. They have not been worked upon in Gimp. Seems a problem with FSpot. Any solution ?

---

### Post by graphius on 2009-05-08
I am having the same problem, especially with RAW images. Fspot shows them fine, and will open a larger view, but I want to edit them with an raw editor (RawTherapee) but I can't configure F-spot to send the file. I have to find out where the file is saved, then open the file in RT. That is why I was using Digikam as it showed the file structure way better than f-spot. however I prefer the way f-spot (mostly) integrates with gnome.

---

### Post by lovinglinux on 2009-05-08
> **graphius said:**
> I am having the same problem, especially with RAW images. Fspot shows them fine, and will open a larger view, but I want to edit them with an raw editor (RawTherapee) but I can't configure F-spot to send the file. I have to find out where the file is saved, then open the file in RT. That is why I was using Digikam as it showed the file structure way better than f-spot. however I prefer the way f-spot (mostly) integrates with gnome.

Digikam is by far a superior application, but not everyone needs all it's features.

---

### Post by robert shearer on 2009-06-03
> Digikam is by far a superior application, but not everyone needs all it's features. 

Yes so thought I would share this 

[http://kornelix.squarespace.com/](http://kornelix.squarespace.com/)

a nice simple editor called fotoxx.

> Fotoxx is a free open source Linux program for editing digital photos. The goal of fotoxx is to meet most photo editing needs while remaining easy to use.

Short Description:
Navigate images using a pageable thumbnail window. Change brightness and contrast, change color intensity, saturation, depth, make panoramas and HDR images, fix red-eyes, trim, rescale, rotate any angle, warp, fix perspective, sharpen, blur, remove noise. Edit within mouse-selected area. Import RAW files, **edit 16 bits/color.** Add tags to images, search by tags, dates, star-rating.

prebuilt packages here...

[http://kornelix.squarespace.com/packages/](http://kornelix.squarespace.com/packages/)

I downloaded and am using this one on Jaunty 32bit works great.

fotoxx-6.9.3-i686.deb

also recommend 'phatch'  can be installed from the repos. search in Synaptic.

---

### Post by graphius on 2009-06-03
Not to be negative, but I read through the authors description, and he sounds more like a programmer than a photographer. Not that is necessarily a bad thing, but some of the small details sound a bit out for serious work. ie it can only save tiff or jpg, VERY rudimentary colour management, etc.
However I am downloading it to give it a fair shake...

---

### Post by graphius on 2009-06-03
OK, I downloaded fotoxx, then I reread your post. You are right. As a simple editor it is ok. I wouldn't call it an organizer in the same league as f-spot or Digikam, or even RawTherapee, but if you shoot jpg snapshots it is probably good enough, especially for a 0.1 release.

---

