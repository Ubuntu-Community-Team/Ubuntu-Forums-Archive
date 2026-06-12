---
title: "Best solution for scanning multiple photos with ubuntu?"
date: 2009-05-21
forum: Multimedia Software
---

### Post by SirWeazel on 2009-05-21
Let me thank anyone in advance for taking the time to read this.  Now to my problem:

I'm trying to scan multiple photos at one time using a flatbed scanner (actually an HP C4280 all in one).  With windows, i'm able to place multiple pictures on the scanner (of different sizes) and scan the pictures into seperate files. The HP software will detect the differnt photos, and name them, and save them as separte files.  So if i have 3 photos on the scanner, i will get a photo1.jpg, photo2.jpg, photo3.jpg all with one scan.  Then it prompts me if i want to scan more, I'll place more photos on the scanner, hit scan, and it continues.  I can scan several photos fairly quickly with this method.

I've searched, and read, and i might just be missing it, but i can't find a solution.  I'm very new to Linux, ubuntu, ect. and i don't yet posess the knowledge to write a "script" or something as i read somewhere once.  Also a script sound like it might not work, because my pictures change sizes, so i'll have a 4x6, 5x7, ect, scattered on the scanner and it will detect each photo separatly.

I'm 95% ready to completely wipe my computer, install ubuntu and be free from windows (i actully have vista ultimate sitting on the book shelf and i would rather try ubuntu first).  This is one of the only things holding me back, but it's kind of a big problem.

Thank you for any help you could give. - P.s. I'm using ubuntu 8.10 and plan to upgrade to 9.04, not ubuntu studio (so if that has an option, please let me know, but i didn't read about one)

---

### Post by SoFl W on 2010-10-24
Did you ever find a solution to this, I tried xsane's multi-page with my Epson all-in-one but the way it scans documents with the page feeder it ends up bending the picture and jamming.

---

### Post by Old *ix Geek on 2010-10-24
I'd LOVE to have a solution for this, too. I have an HP F4100 all-in-one, and several hundred photos of various dimensions to scan. I do not look forward to doing this manually, one at a time! :eek:

Anyone?

---

### Post by SirWeazel on 2010-11-02
I'll let you know what i ended up doing, and still continue to do.  My solution/work-flow process has its benefits/downfalls compared to how i used to do it in windows.  But overall, the process ended up being a lot quicker than how i used to do it in windows. I don't think i ever got help, so i just had to figure it out on my own.

1. i lay the photos in my flatbed scanner. i cram as many as i can, usually 3-4 pics. (sofi, i don't know how this solution would/will work for your sheet fed scanner) 
2. start xsane
3. Now for my xsane settings:
 - # pages to scan = 1
 - my target scan is selected to "save"
 - Choose the directory/file name i want my pics to be stored
 - value added to file counter = +1
 - type = JPEG
 - document feeder = flatbed
 - scan mode, resolution, dpi all depend on your scanning prefs/job at hand
4. More xsane stuff:
 - Under "window" make sure you have "show preview" and "show batch scan" checked.
5. In the "preview Window" i hit "acquire preview" (my settings are preset area=full size, rotate=000, and aspect ratio=free) depending on your needs you might need to change these, but i never had to)
6. Once you have your preview, use your mouse to box in your selection (easy to figure out, it even "kind of" zeros in on the section your trying to make), then in the top left corner hit the "+" symbol which adds the selection to batch scan.
7. Once you have the photos added to the batch scan you should see the selections added to the "batch scan window". 
8. Hit the "batch scan list" button.
 - this will scan the selected entries, and since you have the target selected as "save" it will automatically save them in the selected folder/name.
9. Once it's finished scanning, Empty the Batch list by using the blank page looking button/ "empty batch list" in the top left corner of the batch scan window.
10. Remove your pics from scanner
11. Place new pics on scanner
12. "acquire preview"
13. add batch to batch list
14. scan batch list
15. and keep the process rolling... until you have all 1000 photos scanned :)

- Notes of importance: 
Make sure your scanning to an empty directory for the collection of photos scanning. This way they are named & # in the correct order, and saves time organizing and stuff
- make sure to empty your batch list for the next set of scanned images so your selections don't get mixed.
- after i'm done scanning i like to use an app called "GPRename" to rename and date my scans.

Benefits to me:
- actually is faster for me now vs how my windows hp software did it (not at first, but now i've got it streamlined) This is because the actual scanning of the pics is so so much faster. When your adding your selection to the batch scan, the scanner is only scanning/processing that section on your scanner. Under windows, i think the software scanned the hole surface which took longer, then had to process and detect the photos.
- I can quickly scan the section of the photo i want when i add it to the batch list, thus saving time later editing photos. (alot of time)
  a. ex: scanning non borderless photo, with a big clunky border around it that i actually don't need scanned. (specially when putting together sideshows and stuff).
- don't forget to change your dpi settings depending on your project/photo in the scanner.

Cons to me:
- before i loaded photos into scanner, pushed button on scanner, it auto selected and scanned photos. This gave me time to fold laundry while it was scanning. (it would take a long long time for it to scan 4 photos) Now i have to manually select what i want scanned, but at the same time it scans so fast, i don't have time to walk away so now i just multi task more on my computer instead of walking away from it.

At first i wasn't happy with this process, but after a couple times, its actually saved me time, and overall been a better process.

Sorry for the long post, but just trying to detail the process i've adapted. Not sure if this will help you out SoFI W, but maybe helps the Geek out. My description sounds more complicated then it is... and you'll figure that out once you scan a couple. And you can adjust it to your needs.

---

### Post by AKADAP on 2010-11-02
Now if only I could get XSane to turn on the back light on my HP Scanjet 8200 so I could scan slides & negatives...

---

### Post by SoFl W on 2011-04-07
> **SirWeazel said:**
> I'll let you know what i ended up doing, and still continue to do.  My solution/work-flow process has its benefits/downfalls compared to how i used to do it in windows. .... <break>... 
Sorry for the long post, but just trying to detail the process i've adapted. Not sure if this will help you out SoFI W, but maybe helps the Geek out. My description sounds more complicated then it is... and you'll figure that out once you scan a couple. And you can adjust it to your needs.

Thank you SirWeazel, this process worked fine.  It took a few more  steps compared to the Windows software that came with the scanner.  The Windows software automatically selects the pictures and has the ability to rotate any selected areas a little easier.   An old Windows XP machine sits next to the scanner/printer, the process is a easier so I will use that.  I am glad you posted this information so in the future I know it will work on my Linix box.

Now off to scan about 3000 photos!

*I know this is an old post, but I wanted to thank SirWeazel, and let anyone else looking up the information that this does work.*

---

### Post by SoFl W on 2011-04-10
I am going to offer suggestion in case anyone else is scanning in a lot of old film pictures.

I suggest using many folders with a limited amount of pictures in each.  When you are looking back trough the pictures 150-250 photos is enough to look at in one sitting.  Limit the pictures to that amount in each folder.
If you are really ambitious and were organized I guess "Mary's 3rd birthday" would be good also. 
Give each picture a unique file name.  Pictures get moved around and may not be grouped where they belong.  If every picture has a unique filename you don't have to worry about name conflicts if you have to move photos to another folder.  It also helps you find that photo you moved if you moved it to the wrong folder.
I named folders "FOLDERxxx" and each image "imgxxx-yyy.ext"  xxx is the folder number yyy is the image number.

Before you begin:
Check for duplicates.  Many times you would get a second print "for free".  When pictures were view by several people and then placed into boxes, sometimes the second print didn't end up with the first print.
Look at the back of the picture.  Besides a month and year the pictures were developed you can tell which photos belong with each other.  The photo paper might have "Joe's color lab" or "Kodak - (with the catch phrase of the time)"

Go through, look at the pictures to get the order to scan before you get ready to scan.  Sometimes you can tell which order they belong in, birthday cake with candles lit, blowing out the candles, and cutting the cake.  When reviewing the pictures it is nice to have them in order.
A lot of times you had several events on one roll of film, organize the pictures by grouping the events.

When placing the pictures on the scanner because of the aspect ratio you can fit more pictures on the scanner "sideways" from the top to the bottom.  With my all-in-one scanner which had its hinges on the long side of the scanner I found it was a good idea to put the "heads to the hinges" (top of photo near the hinges) to spend less time rotating the pictures.

-----------------------
I will add more advice as I think of it.  I am currently scanning several thousand photos , and those pictures are not organized well and in several boxes.  I wish I thought of some of those things before I started.

---

### Post by mlsfit138 on 2011-06-07
Thank you Sirweazel.  I've been putting off digitally archiving my old photos for a long time because I didn't know an efficient way of doing it until you pointed it out.  Now the question is do I actually throw my old hard copies out once I've made sure to follow back up procedures.  It would be nice not to have all of that clutter.

---

### Post by Unterseeboot_234 on 2011-06-07
I had a similar assignment. My class reunion wanted to separate the yearbook photos from a single page scan into individual mug shots. I searched and searched online. I tried and almost, almost, made a program in Java to crop each image. It is harder than it looks to make a program: the white background might not be pure white; the photos were slightly different dimensions.

I did find a script for GIMP that makes multiple images from one scan and your thread here reminded me I didn't have it in my Natty updated computer. Here is the link to his last update for the script:

[COLOR="Blue"]**[http://ffaat.pointclark.net/incoming/scripts/DivideScannedImages.scm]("http://ffaat.pointclark.net/incoming/scripts/DivideScannedImages.scm")**[/COLOR]

And, the above was a working link from **[Rob A's (Im)personal Blog]("http://ffaat.pointclark.net/blog/")**

Here is the link for the discussion:

**[http://www.gimptalk.com/index.php?/topic/35713-divide-or-crop-multiple-images-from-single-scan/]("http://www.gimptalk.com/index.php?/topic/35713-divide-or-crop-multiple-images-from-single-scan/")**

The script works very well for img001.jpg, img002.jpg... The author claims it will do .png but strangely that does not work.

Anyhow, the link is to a script that brings up a GUI in GIMP. You have to play with it a bit. I'm posting this as a 'bookmark' so I can always get back to the forum that posted the code.

You save the downloaded file.scm. Show hidden files in your Home Folder, find .gimpX.x, inside that is a folder /scripts. Put it there. Fire up GIMP and you find the Menu item: Filters [ last item ]. Or, you can Menu: Filters -> Batch Tools -> Batch DivideScannedImage

---

### Post by SirWeazel on 2011-06-14
mlsfit138,

Unless you have 1000+, 100000+, 10000000000+, i would probably hold on to the photos.  Even if i had millions of photos, i would probably still keep them.  As you scan them, just put them in a box or something and store them away.  You never know what the future holds and how much space can it really take up. Just consider it an extra layer to your backup system. Backing up is a whole another topic. (onsite, offsite, fireproof, ect...)  I'm actually afriad with everything digitize, old photos will be more dificult to find hidden on some old relatives vintage computer several years from now.... Simple answer is keep the photos.

---

