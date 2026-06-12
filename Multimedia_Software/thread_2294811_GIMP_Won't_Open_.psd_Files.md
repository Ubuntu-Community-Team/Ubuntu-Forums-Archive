---
title: "GIMP Won't Open .psd Files"
date: 2015-09-13
forum: Multimedia Software
---

### Post by branau on 2015-09-13
So I've got a MacBook Pro with GIMP and Photoshop CC 2015, and another laptop running Ubuntu 14.04 with GIMP as well, and I'm unable to open up psd files in GIMP on either computer. I've tried multiple psd files, and they all open just fine in photoshop, but they throw me an error message in GIMP and then don't open. I've attached a screenshot of that. Interestingly enough, if I create the psd in GIMP and then save it to my computer, I can open it no problem. That's unfortunately not going to be good enough for me though, since I am usually just receiving psd iles that I have to build from. Any ideas as to what could be causing this?

---

### Post by branau on 2015-09-13
With a different psd, I'm getting a different error message, attached below.

---

### Post by brian-mccumber on 2015-09-13
It could be that the new version of Photoshop has changed the format of the psd to something that Gimp can't read anymore. I have tons of psd's that I had made with PS cs5 when I was running Windows and Gimp has no problem opening them. The worse thing that happens is I get a font error and it falls back to system default which is understandable since I don't have the same fonts on Ubuntu as I did on Windows. But other than that I can open any of my psd's from cs5 in Gimp 2.8.

---

### Post by branau on 2015-09-13
Yeah, that would be a tough one for me too because I need to be able to grab the exact fonts used. Interestingly enough, I can open the psd's in LibreOffice, but then I just get a flat .png image and that doesn't work for me either, seeing as I need to be able to pull logos and specific images, sometimes with a transparent background

---

### Post by brian-mccumber on 2015-09-13
Well after some searching I found this article and it seems that Gimp has problems with text, some layer modes, and masks from psd. Here is the link to article in case you want to read it. They found a workaround by turning text layers to images and rasterizing certain layer modes.

[http://www.gimptalk.com/index.php?/topic/47574-error-opening-psd-file-unsupported-or-invalid-layer-height/](http://www.gimptalk.com/index.php?/topic/47574-error-opening-psd-file-unsupported-or-invalid-layer-height/)

---

### Post by branau on 2015-09-13
Hmmm, well thank you for your help. I may just have to run windows in a virtual box and then run Creative Cloud from there. I was hoping to find a way to get out of using Windows haha but my bosses are pretty strict on the pixel-perfect design of the sites we build, so I really need things to look exactly the way they do in photoshop. It's a shame Adobe hasn't ported their software to linux yet. I'm sure there are plenty of developers and designers on linux computers that would pay for the software, at least enough to make it worth their while.

---

### Post by brian-mccumber on 2015-09-13
Here is a converter I found but I did not test it because you must have the psd's in dropbox or google drive or something before it will convert them, it doesn't support uploads from the computer.

[https://cloudconvert.com/psd-to-xcf](https://cloudconvert.com/psd-to-xcf)

---

### Post by Bucky Ball on 2015-09-13
> **branau said:**
> It's a shame Adobe hasn't ported their software to linux yet.

I would not hold your breath on that, particularly a/v software.

Can you save them in a cross-platform filetype from Photoshop?

---

### Post by brian-mccumber on 2015-09-13
If you already have a copy of Photoshop just work with that from your Mac then for those particular jobs.

---

### Post by branau on 2015-09-13
> **brian-mccumber said:**
> Here is a converter I found but I did not test it because you must have the psd's in dropbox or google drive or something before it will convert them, it doesn't support uploads from the computer.

[https://cloudconvert.com/psd-to-xcf](https://cloudconvert.com/psd-to-xcf)

Thanks, that's actually a really neat tool. I'll have to test it and see how well it works. Im going to be working remotely as of Tuesday so it won't be a big deal to work from two different computers and just transfer the files between them

---

### Post by brian-mccumber on 2015-09-13
Roger that. USB drives are cheap and easy to use and share folders are a cinch to set up between computers.  I freelance dev work from home and it's great, so if you meant remotely as in working from home you're in for a treat! Most days I work all day in my pj's before I realize the day is gone and it's time to put my pj's back on.

---

### Post by branau on 2015-09-13
Yeah I've actually been testing this by file sharing between the Mac and my Ubuntu computer so I'll just do that. 

And yeah that's exactly what I'll be doing haha. I'm looking into getting a second monitor too to make things a little faster since I do a lot of multitasking.

---

### Post by brian-mccumber on 2015-09-13
Oh, if you haven't done so turn on the workspace switcher on the Ubuntu computer, it's in System Settings-->Appearance-->Behavior Tab.  Check the Enable Workspaces box, this is a great tool also. I have mine set up for 3 rows and 3 columns so I get a total of 9 different workspaces to use but I think I used Unity Tweak Tool to set more than 4 workspaces.

---

### Post by branau on 2015-09-13
> **brian-mccumber said:**
> Oh, if you haven't done so turn on the workspace switcher on the Ubuntu computer, it's in System Settings-->Appearance-->Behavior Tab.  Check the Enable Workspaces box, this is a great tool also. I have mine set up for 3 rows and 3 columns so I get a total of 9 different workspaces to use but I think I used Unity Tweak Tool to set more than 4 workspaces.

Interesting, I'll have to try that out. Is there a keyboard shortcut to move easily between the workspaces or is it like the multiple displays to where you just drag windows onto the other workspaces?

---

### Post by brian-mccumber on 2015-09-13
It puts an icon in your launcher when you enable it and there are hotkeys for it too. The hot key is superkey(windows key) + s then you can use arrow keys to move between workspaces. I don't use the hot keys tho I mainly use the icon in the launcher and select the workspace I want to use with the mouse.

---

### Post by branau on 2015-09-13
I'll have to play around with that for sure!

---

