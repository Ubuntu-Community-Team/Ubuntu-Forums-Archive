---
title: "nvidia drivers for 12.10"
date: 2013-02-19
forum: Multimedia Software
---

### Post by zohaib44 on 2013-02-19
i need nvidia drivers for geforce 8400 gs

---

### Post by Bucky Ball on 2013-02-19
*Thread moved to **Multimedia & Video**.*

---

### Post by kc1di on 2013-02-19
Go to system settings > Additional Drivers and install it from there. 

There was a problem for a while with the current nvidia driver. in the 295 series so I would try 310 series if it's offered.
good luck

---

### Post by zohaib44 on 2013-02-19
there is no additional drivers in system settings

---

### Post by Bucky Ball on 2013-02-19
Have you done an update? If not, do so and check Additional Drivers again.

---

### Post by zohaib44 on 2013-02-19
235mb of updates are being downloaded, it will get some time on my broadband, approximately 50 minutes, ones its done i will report back.

thank you

---

### Post by zohaib44 on 2013-02-19
nope, i have done an update but there is still no additional drivers in system settings

---

### Post by kc1di on 2013-02-19
forgot jockey-gtk did not come preinstalled with 12.10.

If I remember right you have to enable the universe repository to get it. then you can use additional driver tool.

---

### Post by zohaib44 on 2013-02-19
how can i do that?

---

### Post by kc1di on 2013-02-19
go to software center > edit tab > software sources make sure universe and multi-universe are checked.
you can also try installing the driver from the software center.

---

### Post by zohaib44 on 2013-02-19
they were already checked. now what should i do next?

---

### Post by zohaib44 on 2013-02-19
[[IMG]http://img33.imageshack.us/img33/9514/screenshotfrom201302192.png[/IMG]](http://imageshack.us/photo/my-images/33/screenshotfrom201302192.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

which nvidia driver should i download from this list?

---

### Post by kc1di on 2013-02-20
I would try the second in the list first, (experimental)
if that does not work let me know we will go from there.

---

### Post by zohaib44 on 2013-02-20
yesterday i searched on google about how to install nvidia drivers, i tried many drivers but nothing worked, today when i removed the drivers which i installed yesterday from terminal then i restared the system now there is no display, all i see is my monitors light blinking and black screen. i think i should remove 12.10 and try 12.04, or is there a way to get rid of this no display problem?

and thanks for helping mate really appreciated.

---

### Post by kc1di on 2013-02-20
At this point it may be easier to just reinstall I like 12.04 but your mileage may vary ;)

---

### Post by zohaib44 on 2013-02-20
i have installed ubuntu 12.04 
which driver should i download from this screenshot
[[IMG]http://img600.imageshack.us/img600/5274/screenshotfrom201302201.png[/IMG]](http://imageshack.us/photo/my-images/600/screenshotfrom201302201.png/)

---

### Post by kc1di on 2013-02-20
Try the third one 310 first.
It works very well for me here.

---

### Post by Bucky Ball on 2013-02-21
Try them all and see what works. The third experimental driver? Why? It might work for some but not for others. I'd go for the one you have highlighted and 12.04 LTS, yes. Experimental can be v flaky on some hardware.

PS: Incidentally, could you attach screenshots rather than putting them in the body of the post? Spare a thought for those with slow connections. They can't help or even look at this thread.

Hit 'Go Advanced' and then the paperclip icon. ;)

---

### Post by kc1di on 2013-02-21
Hi Bucky Ball,

the reason I suggested the experimental one is there was a known bug in the 295 series and ubuntu 12.04 lts gave me no end of fits here when 12.04 was released so thought I'd see if the 310 would work for the op first. 

cheers!

---

### Post by zohaib44 on 2013-02-21
i tried them all, after restarting the system i get the same old no display black screen, nothing worked so far unfortunately.

---

### Post by kc1di on 2013-02-21
> **zohaib44 said:**
> i tried them all, after restarting the system i get the same old no display black screen, nothing worked so far unfortunately.
ok I'm beginning to think you had the need to enter nomodeset in the kernel line. 
[Here is a page]("http://askubuntu.com/questions/207175/what-does-nomodeset-do") that explains it:

---

