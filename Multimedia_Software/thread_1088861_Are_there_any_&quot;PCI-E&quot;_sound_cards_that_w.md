---
title: "Are there any &quot;PCI-E&quot; sound cards that *will* work?"
date: 2009-03-06
forum: Multimedia Software
---

### Post by ssiegler on 2009-03-06
Are there any "PCI-E" sound cards that will work with Ubuntu 8.10 (or better)?

I made the mistake of believing that Creative's release of drivers (to support the Sound Blaster Titianium PCI-E card on Linux) was the same as having working drivers for the card/os. I see that this has been in the alsa queue forever, and that people claim to have this working (I'm skeptical, since they didnt post the steps to make it happen -- they post the threads that "contain" the magic code).

My options are: 
1) Revert to windows.
2) Live without sound.
3) Wait for the Alsa group.
4) Buy another card that does work.

Im running a Dell PowerEdge T300, 2.6.27-11-generic, 8.10, if that makes any difference.

Thanks!

Stuart

---

### Post by ssiegler on 2009-05-08
The Creative Titanium XFi/PCI-E works with Jaunty!

(You still need to make/install the Creative Drivers by hand, this is not too hard, even for someone new to Ubuntu (There are many threads that have the steps but Its basically:  
1) download the [XFiDrv_Linux_Public_US_1.00.tar.gz ]("http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17927&prodName=PCI+Express+X-Fi+Titanium")
from [http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17927&prodName=PCI+Express+X-Fi+Titanium](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17927&prodName=PCI+Express+X-Fi+Titanium)

2) untar it  (you should be able to double click on it)

3) open a terminal window, and cd to the folder created 

There is a readme that says:
1) Goto source directory (Youre already there)
2) Execute make command as root
   make
   make install

4) Reboot.

Stuart

---

