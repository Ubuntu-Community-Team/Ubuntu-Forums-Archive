---
title: "missing buttons in maverick"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by basilwatson on 2010-09-04
Hi there 
updated to maverick on my MSI wind u 100 ( realtek drivers ) and the minimize close buttons are missing 
tried reinstalling Emerald , but I cant seem to get then to work ,

Everything is ok in safe mode ( log out ,log back in safe mode )

How can I regain the missing buttons 

Kind regards 

Stephen

---

### Post by dino99 on 2010-09-04
into a console:

sudo dpkg-reconfigure gnome-panel

metacity --replace

---

### Post by basilwatson on 2010-09-05
Hi there

just tried that I get an error message ; invalid string constant " panel" , expected valid string constant 

Something to do with theme , emerald? anyway , i can find the answer yet so as its my net book I will reinstall 10.04 , or try the netbook edition of 10.10 

Thanks for the help Stephen

---

### Post by NosamLuap on 2010-09-05
@BasilWatson - you're not alone. I'm getting this problem too...

@dino99 - that didn't solve it for me (though I didn't get an error)

I did notice that in Google Chrome, if I choose not to "use system title bar and borders", and then choose to use them again, they appear, but only for Google Chrome - other apps still have none.

---

### Post by NosamLuap on 2010-09-05
And another thing I just noticed - icons are only missing on windows that are maximised (I'm testing this on a netbook (Not using UNR) so tend to run most things maximised).

---

### Post by basilwatson on 2010-09-05
> **NosamLuap said:**
> And another thing I just noticed - icons are only missing on windows that are maximised (I'm testing this on a netbook (Not using UNR) so tend to run most things maximised).

Me to 

but i just installed the desktop version and all the buttons are present and correct 
Except the resizing of the set up screen and a large margin on the left ( the icons sit about a centimeter from the screen edge

Well its Beta , so I expect a few teething prob

Stephen

---

### Post by NosamLuap on 2010-09-07
I found that Maximus (the UNR 'automatic maximiser') was still installed on my system (it was originally a 9.10 version of UNR, but I always booted into the regular gnome session. Upgraded to 10.04 (desktop) and then 10.10 (desktop) but it seems that Maximus was still doing something - uninstalled that, and my icons are now back :o)

---

