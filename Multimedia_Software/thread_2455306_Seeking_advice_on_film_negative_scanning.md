---
title: "Seeking advice on film negative scanning"
date: 2020-12-17
forum: Multimedia Software
---

### Post by satimis on 2020-12-17
Hi all,

Can any folk guide me how to install Vuescan on Ubuntu 20.04 for scanning film negatives.  Pointers would be appreciated.

I shall use my old Epson Perfection 3490 Flatbed Photo Scanner as start, temporarily for testing.  I'm going to purchase Epson v800 Flatbed Photo Scanner in next few days.

What will be the alternative of Vuescan on Linux for negative scanning?  Can I run GIMP to do the job?

Please help.  Thanks in advance.

Regards

---

### Post by TheFu on 2020-12-17
I don't have 20.04 connected to any scanners. Still using 16.04 for that.

However ... 

I have a dedicated negative scanner. The driver software for it for WinXP was included. I think there is commercial software for $100 for Linux software, but I've avoided that. [https://www.hamrick.com/linux-scanner-software.html](https://www.hamrick.com/linux-scanner-software.html)  Flatbed scanners aren't usually designed for negative scanning. I had an epson flatbed with negative attachment and it didn't product nearly as good scans.  It was a huge hassle to use even for regular paper scans.

In the end, since i had many hundreds of slides and negatives to scan, I replaced the flatbed with an auto-sheet-feeding page scanner and a dedicated negative/slide scanner.  The sheet-feeding page scanner is from Brother and works with SANE and **gscan2pdf** nicely.  I'm very happy with that purchase.

---

### Post by satimis on 2020-12-18
> **TheFu said:**
> I don't have 20.04 connected to any scanners. Still using 16.04 for that.

However ... 

I have a dedicated negative scanner. The driver software for it for WinXP was included. I think there is commercial software for $100 for Linux software, but I've avoided that. [https://www.hamrick.com/linux-scanner-software.html](https://www.hamrick.com/linux-scanner-software.html)  Flatbed scanners aren't usually designed for negative scanning. I had an epson flatbed with negative attachment and it didn't product nearly as good scans.  It was a huge hassle to use even for regular paper scans.

In the end, since i had many hundreds of slides and negatives to scan, I replaced the flatbed with an auto-sheet-feeding page scanner and a dedicated negative/slide scanner.  The sheet-feeding page scanner is from Brother and works with SANE and **gscan2pdf** nicely.  I'm very happy with that purchase.
Hi,

Thanks for your advice.

I have made some searches on both flatbed scanner and digital film scanner recently.  Also I have searched the sample photos delivered by digital film scanner.  Not all samples are up to my satisfaction.

My finding is;
1. Scanning quality of a flatbed scanner is much better than a digital film scanner
2. The scanning speed of a digital film scanner is faster than a flatbed scanner.

My preliminary planning is;
1. Purchase Epson v800 or v850 flatbed photo scanner to scan my old negatives
2. If the scanning speed is NOT too slow which can satisfy me, I'll use it scanning all my old film negatives.
3. If the scanning speed is too slow in my consideration I'll purchase Kodak Scanz digital film scanner for bulk scanning all my film negatives.  Then pickup those digital files, their quality being not up to my satisfaction, and re-scan their negatives on the flatbed scanner.

I won't print the digital files but posting them on website only.  I think my film negatives are still in good condition, being stored in their folders and packed in boxes without touching.  Neither I have big size film negatives.

Now I'm busy making my old Epson Perfection 3490 flatbed photo scanner to work on Win10home VM/Guest.  It works on Ubuntu 20.04 Guest and Ubuntu 20.04 host.  The old flatbed scanner is still working but it needs to retire.  I only want to make sure I can make a flatbed scanner to work on Linux as well as Windows.

Also I have compared the features and performance of both v800 and v850. There is not much different in their specification but the price of v850 is about 35% higher.  I'm willing to pay if there is a big difference in resolution and scanning speed.

Regards

---

### Post by TheFu on 2020-12-18
I had an Epson flatbed and gave it away due to all sorts of issues and poor support.

I'll attach a slide scanned image from the Hamrick USB scanner for your consideration. Give me a few minutes. It was scanned probably 10 yrs ago. It has 1 button, no LCD, and a 4 side/film manual feeder  Says "VuPoint" on the top. We'll see if these forums allow the "full-sized" file.  The source was a slide. Appears the forums drastically reduced the uploaded file to less than 640x480. The original was 1680x2592. In the original, there are lots of blemishes on the slide.

The scanner looks much like this: [https://www.ebay.com/p/2256200502](https://www.ebay.com/p/2256200502) , but not exactly.

---

### Post by QIII on 2020-12-18
Scanned 10 years ago, taken 55 years ago?  :)

Looks like some of our slides of my younger siblings.

---

### Post by satimis on 2020-12-22
Followings are the test results of film negatives on Epson Perfection 3490 Photo Scanner:-
(One film strip, 4/6 negatives. per each scanning)

OS - Windows 10 Home
Software - Epson Scan
Epson Perfection 3490 Photo Scanner

img005.jpg
Professional Mode
Film Type - Color Negative Film
Image Type - 24 bit color
Resolution - 1200 dpi
Target Size - Original
Preview Time + Warm up time + Scanning time = about 5 min

img009a10.jpg
Professional Mode
Film Type - Color Negative Film
Image Type - 48 bit color
Resolution - 9600 dpi
Target Size - Original
Document Size - W 1.35 H 0.87 inch
Preview Time + Warm up time + Scanning time = about 18 min

img018.jpg
Professional Mode
Film Type - Color Negative Film
Image Type - 48 bit color
Resolution - 4800 dpi
Target Size - Original
Document Size - W 1.36 H 0.85 inch
Preview Time + Warm up time + Scanning time = about 10 min
Simple manual adjustment on settings - performed

It is NOT TOO bad.  But img005.jpg and img009a10.jpg look not much difference to me.  img018.jpg looks differently after having simple manual adjustment on settings before scanning.

My preliminary conclusion on scanning old film negatives:-
If you need quality digital images/files, time and effort are unavoidalbe.  There is no simple and easy way !!! 

I can't believe my old Epson Perfection 3490 Photo Scanner still working so strong.  It can scan 48bit color and 9600 dpi resolution.

Preview scanning is ONE pass of 4/6 negatives on the film strip.  But scanning negatives is done ONE BY ONE, not collectively, then saving them on their own digital files.  That is why taking so long time on scanning film negatives.

My solution on saving time is to have 2 PCs running side-by-side, one for scanning film negative and another for daily working. During scanning negatives I continue working on my daily computer

Thanks and Regards

---

### Post by shantiq on 2020-12-23
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=287598&d=1608620367[/IMG]*Paris 1972?   can't be far off   *:mad:

---

### Post by pushbike06 on 2020-12-23
Not directly answering the question, but another way of achieving the same solution. Some ideas.
I use: 
Canon EOS500D and a light table/copy table, sourced from a hospital pathology lab. auction ($A100) 
Canon software (free),EOS Utility (camera control/settings, remote capture operation and computer display of image), on Win XP system
I am about to learn/use Darktable on Ubuntu system. Similar to Canon software.
Also use Fotoxx for image processing and Thunar for bulk file renaming.
I am constructing a light box for copying negs. then invert? image using software.

I have used this light table /copy table for Docs and legacy? color and BW prints. also to photograph physical objects.
Camera attaches to central vertical adjustable column mount. USB connection to PC. Live view of image for positioning, size, focus and lighting adjustments. Remote shutter actuation.

---

### Post by TheFu on 2020-12-24
> **pushbike06 said:**
>   Thunar for bulk file renaming.

For bulk renaming, **qmv** rocks!  
It creates 2 columns of filenames. The left is the original name. The right is the new name. Depending on your configured editor, renaming hundreds to thousands of files is very quick.  Just set the EDITOR environment variable to the editor you prefer and can do amazing things inside. Obviously, editors with column editing are handy, like vim.

---

