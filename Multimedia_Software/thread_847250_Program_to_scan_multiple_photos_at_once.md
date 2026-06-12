---
title: "Program to scan multiple photos at once?"
date: 2008-07-02
forum: Multimedia Software
---

### Post by Jackelope on 2008-07-02
I have about 1000 photos that I want to scan onto a hard drive for archiving. There's a program for Windows which will let me place several pictures on the scanner, scan them all at once, then automatically crop them into separate digital pictures. This would be a real time saver, but I can't find any equivalent for Linux. Is there a program or script for Ubuntu which would let me do this? Maybe something for Gimp? Thanks ahead of time! :)

---

### Post by SoFl W on 2011-04-06
I will bump this OLD thread because I would like to know if SANE or some other program can do this.  I am currently using the Windows program that came with the scanner/printer.

I can put five photos on the glass and the software will verify and then save five pictures with incremental file names.  Is there a linux option for this?

Possible solution found in the archives which they might remove.
> 
I'll let you know what i ended up doing, and still continue to do.  My  solution/work-flow process has its benefits/downfalls compared to how i  used to do it in windows.  But overall, the process ended up being a lot  quicker than how i used to do it in windows. I don't think i ever got  help, so i just had to figure it out on my own.

1. i lay the photos in my flatbed scanner. i cram as many as i can,  usually 3-4 pics. (sofi, i don't know how this solution would/will work  for your sheet fed scanner) 
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
5. In the "preview Window" i hit "acquire preview" (my settings are  preset area=full size, rotate=000, and aspect ratio=free) depending on  your needs you might need to change these, but i never had to)
6. Once you have your preview, use your mouse to box in your selection  (easy to figure out, it even "kind of" zeros in on the section your  trying to make), then in the top left corner hit the "+" symbol which  adds the selection to batch scan.
7. Once you have the photos added to the batch scan you should see the selections added to the "batch scan window". 
8. Hit the "batch scan list" button.
 - this will scan the selected entries, and since you have the target  selected as "save" it will automatically save them in the selected  folder/name.
9. Once it's finished scanning, Empty the Batch list by using the blank  page looking button/ "empty batch list" in the top left corner of the  batch scan window.
10. Remove your pics from scanner
11. Place new pics on scanner
12. "acquire preview"
13. add batch to batch list
14. scan batch list
15. and keep the process rolling... until you have all 1000 photos scanned :)

- Notes of importance: 
Make sure your scanning to an empty directory for the collection of  photos scanning. This way they are named & # in the correct order,  and saves time organizing and stuff
- make sure to empty your batch list for the next set of scanned images so your selections don't get mixed.
- after i'm done scanning i like to use an app called "GPRename" to rename and date my scans.

Benefits to me:
- actually is faster for me now vs how my windows hp software did it  (not at first, but now i've got it streamlined) This is because the  actual scanning of the pics is so so much faster. When your adding your  selection to the batch scan, the scanner is only scanning/processing  that section on your scanner. Under windows, i think the software  scanned the hole surface which took longer, then had to process and  detect the photos.
- I can quickly scan the section of the photo i want when i add it to  the batch list, thus saving time later editing photos. (alot of time)
  a. ex: scanning non borderless photo, with a big clunky border around  it that i actually don't need scanned. (specially when putting together  sideshows and stuff).
- don't forget to change your dpi settings depending on your project/photo in the scanner.

Cons to me:
- before i loaded photos into scanner, pushed button on scanner, it auto  selected and scanned photos. This gave me time to fold laundry while it  was scanning. (it would take a long long time for it to scan 4 photos)  Now i have to manually select what i want scanned, but at the same time  it scans so fast, i don't have time to walk away so now i just multi  task more on my computer instead of walking away from it.

At first i wasn't happy with this process, but after a couple times, its  actually saved me time, and overall been a better process.

Sorry for the long post, but just trying to detail the process i've  adapted. Not sure if this will help you out SoFI W, but maybe helps the  Geek out. My description sounds more complicated then it is... and  you'll figure that out once you scan a couple. And you can adjust it to  your needs.
[http://ubuntuforums.org/archive/index.php/t-1165797.html](http://ubuntuforums.org/archive/index.php/t-1165797.html)

I have not tried it, I am using the Windows software that  came with the scanner because I worked out a system to do it.

---

### Post by inobe on 2011-04-06
xsane has a multi page mode, see if that helps.

i think

---

### Post by SoFl W on 2011-04-07
> **inobe said:**
> xsane has a multi page mode, see if that helps.
i think

I have used it for multi-page documents, but have not tried it for putting multiple pictures on the glass, scanning the pictures, and having it save each picture to a separate file.  I will have to try it sometime.  Right now I have a method of getting it done with the Windows machine, and the windows machine is closer to the scanner.  I have thousands of old family photos and I want to do this quickly.

**Edit:**  I attempted the method in post#2 (from another thread) and it works, but there are a few more steps then the Windows software that come with the scanner/printer.  It does work and seems to work well.

---

