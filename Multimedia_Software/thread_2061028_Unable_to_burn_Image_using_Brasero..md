---
title: "Unable to burn Image using Brasero."
date: 2012-09-21
forum: Multimedia Software
---

### Post by FahadMKS on 2012-09-21
Hi,

I tried to burn ISO image using Brasero. But after completing the Image Check Sum error, the medium is getting ejected and  an error occurs. I am trying to burn a Linux image.
A screen Shot of the error is attached below so as to know about the error better.
Please do help us with the issue as soon as possible.

---

### Post by Cheesemill on 2012-09-21
Try using a different application.

My personal favourite is [xfburn]("apt://xfburn").

---

### Post by acefromspace on 2012-09-21
Try K3b (I never liked Brasero)
Choose Burn Image (or just browse for your iso image and click it... should bring up the burn image anyway) Does your file have extension .iso ? Linux may not care, but I think the burner program does.

---

### Post by FahadMKS on 2012-09-21
Hi, Cheesebil,

I have tried Xfburn and the issue still remains. And I have checked on with the extension and its .iso.

PLease  Please .. anybody help me out with the issue.

---

### Post by Cheesemill on 2012-09-21
'Tracking servo failure' sounds like your drive is on it's way out.

Do you have another OS you can boot from to try with (either a Windows dual-boot or a Live USB)?

---

### Post by acefromspace on 2012-09-21
Just to be sure: you are choosing burn image, not data dvd?
Also, I'm getting fed up with dvd drives in general. Many times they need to be opened and clean the spindle, check for crud on slider bars, ect. What drive do you have? Some are known to have issues (like mine... optiarc) Will the drive burn data dvd?

---

### Post by pakguru on 2012-09-24
I have had issues trying to burn iso images to CD using Brasero – it usually tells me that the blank CD is not big enough (-when it actually is). The best solution I have found is to use GnomeBaker ( -downloadable from Ubuntu software centre).
 How to burn iso to CD in Gnomebaker:  
 Open GnomeBaker but IGNORE the three option boxes: Data DVD/Data CD/Audio CD in the 'Create New Project' part in the lower, 'Welcome' part of the screen. Instead, go to the top menu bar and select 'Tools' and then click the 'Burn CD' option...things are straightforward from then on.

---

### Post by buckyaustin on 2012-10-15
You would be better off running this in terminal, in the newer distro's press [ctrl] + [alt] + [t] or older [alt]+[f2] type "gnome-terminal". This will open terminal, then type sudo apt-get update && sudo apt-get upgrade. Then sudo apt-get dist-upgrade. This is to eliminate that you have out of date software. 

Buy a new DVD, use a dvd as it is far too big to be told there isn't enough space. Also a new DVD means there is no possiblity of it being at all scratched or used before.

Then try Brasero, or any other software. If it still doesn't work, then you are looking at more of hardware problem than software. 

Also try another OS this will test if your OS is the problem. Give us back your results. Look forward to get a reply from you.

---

### Post by evilsoup on 2012-10-15
For ripping DVDs or creating ISOs, I've always found Brasero to work fine; but for actually burning them, it's a piece of junk.

As others have suggested, [xfburn]("apt://xfburn") works much better; of the programs I've used, though, the best for burning DVDs has to be [IMGburn]("http://www.imgburn.com/"). It's a Windows program, but runs flawlessly in [WINE]("apt://wine"). I've found it's the only thing that can utilise my external DVD writer's full write speed.

---

