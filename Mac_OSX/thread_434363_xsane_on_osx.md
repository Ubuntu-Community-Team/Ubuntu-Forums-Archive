---
title: "xsane on osx"
date: 2007-05-05
forum: Mac OSX
---

### Post by c.dric on 2007-05-05
hey guys, 

i have this great wireless networked printer/scanner from brother (MFC820C) and it works great with my linux boxes. problem is that i can't scan properly from mac computers. the mac software included with the printer is really a pile of garbage that never worked properly and the free, as in beer, softwares that i could find don't seem to work with networked scanners.

so i'm wondering if it's possible to run the xsane installed on one of the linux boxes from osx ?
and if so what is the best way to do it ? i'm a bit lost between the different solutions ... x forwarding ... vnc ... ?

if there is an how-to that i've missed please let me know ... 
i would be grateful for any advices on how to get this to work.

thanks :)

---

### Post by tgalati4 on 2007-05-06
I've got an HP network printer (Officejet 7110) and the HP Image Zone software works pretty well on a Mac powerbook G4.

You can install XDarwin on youe mac and run startx in a terminal to get an X windows environment.  Then ssh to your Ubuntu machine.  Then run gnome-panel and voila, you have a gnome desktop on your machine and you can run just about anything.

I use Desktop Manager in Tiger to get 8 desktops and one of them always has something Ubuntu-flavored running.  Of course I also have iTunes running in another to feed my various, proprietary iPods.

You can also install Fink Commander and install some deb/rpm packages that folks have thoughtfully compiled to run under Tiger.  Don't know if xsane is available, but it is a constantly-growing repository.

Then there is a growing base of Mac OS X applications that folks have converted from open source to run under the Cocoa graphics environment.  These work especially well, since they use the native graphics environment.  They tend to work better than the expensive bloatware programs that do the same thing.

You could set up a script on the Ubuntu machine to automatically take a scan from the Brother printer and put it in a shared directory then grab the file (TIFF, JPG, PDF) using a smb://ubuntumachine/shareddirectory in the Go-->Connect to Server in Finder.  Or, the script could email the file to the mac user.  How often do you need to scan images?  The more often you use it, the more effort you will spend to get a script to work properly.

In Linux there are many ways to solve problems.

So although I can't point you to a simple how-to, there are a lot of options to explore.

---

### Post by c.dric on 2007-05-06
thanks for the advices.

i already have the X server installed on that machine for OO & the Gimp ... the problem is that i'm not the one using that machine, otherwise i would have put linux on it from the start. it's the machine of someone who can barely manage osx so i can't expect that he will startx and ssh to a linux box each times he needs a scan :|

i checked fink and they have the xsane package marked as unstable ... maybe i should give it a try and see how unstable it really is.

what i'd like to get is a simple button linked to a script that connect 'automatically' to one of the linux box, launch the xsane program and export to the mac display ... i don't know if it's possible to get something that simple ?

i know a little bit of bash scripting but that doesn't work on mac right ?

---

### Post by Alfa989 on 2007-05-06
> **c.dric said:**
> thanks for the advices.
What i'd like to get is a simple button linked to a script that connect 'automatically' to one of the linux box, launch the xsane program and export to the mac display ... i don't know if it's possible to get something that simple ?

i know a little bit of bash scripting but that doesn't work on mac right ?

You should be able to make a terminal script... It uses bash... :)
Or you could give AppleScript a try...

---

### Post by rccharles on 2007-06-10
> **c.dric said:**
> hey guys, 

so i'm wondering if it's possible to run the xsane installed on one of the linux boxes from osx ?
and if so what is the best way to do it ? i'm a bit lost between the different solutions ... x forwarding ... vnc ... ?


I was able to use the TWAIN SANE Interface for MacOS X with my Umax scanner on Mac OS 10.4.9.  
See:
[http://www.ellert.se/twain-sane/](http://www.ellert.se/twain-sane/)

For the image capture software, I used hd > Applications > Image Capture.  Click on the device Pull Down and select sane even if you get an error message when you start.

I was able to scan in an image, but Image Capture wouldn't let me edit the image.

Robert

---

