---
title: "lightscribe now available for linux"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by CapnCook on 2006-10-22
[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

does anyone have a lightsrcibe disk working in kbuntu/ubuntu if so what is the brand and model.

---

### Post by Lord Illidan on 2006-10-22
I don't have one, but great news.

---

### Post by punx45 on 2006-10-22
i just installed both the lightscribe host software and the Lacie labeler software, and was able to successfully print on a disc using the HP DVD640 lightscribe drive.  and i never had to install any drivers for the drive itself.

if you are looking for a drive i got mine from geeks.com for about $40 refubished.

also note that the software is packaged as RPMs so see [here]("http://www.psychocats.net/ubuntu/installingsoftware") if you dont know how to install them.

---

### Post by CapnCook on 2006-10-22
Thanks punx 45 I am gonna go pick up a dvd dual burner later this afternoon.

---

### Post by graveson on 2006-10-22
CapnCook,
Have you managed to get this software to work.I used alien but i have some weird errors eg cpio : premature end of file

---

### Post by graveson on 2006-10-22
CapnCook,
ignore the last post. I found that the file was not downloaded correctly.The app is launching now. Now to burn some dvd's :)

---

### Post by meng on 2006-10-22
Great to hear this.

---

### Post by CapnCook on 2006-10-22
graveson I haven't been to the store to pick up a lightscribe drive yet. But glad you got the software working.

---

### Post by mcsix on 2006-10-23
This is great news for me. I had just bought a lightscribe drive about a month before I decided to intall ubuntu. I figured I would have to just without it. Now to see that it is already available is cool. I tried it out and it works perfectly. 
Thanks for the information.

---

### Post by CapnCook on 2006-10-23
mcsix your welcome. I just happened across the information while reading linux news on google.

---

### Post by jcrnan on 2006-10-23
this is nice since my hp pc inclused a lightscribe thingie. Not that I have ever used it :p

---

### Post by Roger Mudd on 2006-10-23
What are the write times for "printing" labels on CDs/DVDs with a Lightscribe drive? I have heard that it can take upwards of 30 minutes. Is this the case?

---

### Post by mcsix on 2006-10-23
It depends on the quality setting. Best quality is about 20 minutes on mine.

---

### Post by Roger Mudd on 2006-10-23
Thanks mcsix.

---

### Post by punx45 on 2006-10-23
yeah, time varies based on printing method and quality.   there are three printing styles available, one does a simple ring around the inner circumfrence of the disc, one does a larger ring, and one prints on the entire surface.  lightscribe prints like a cd writes, starting from the inside and working out, so the full surface print takes the longest at about 20 minutes at best quality.   there are three levels of quality too, the difference being the darkness.   the lowest quality is rather faint so not really worth much.   even best quality is not able to get true black unfortunately.   the plus side is the discs can be printed more than once, so if you really want to invest more time you could print best quality twice and get better black.   though i have not tried this yet and am unsure of how well the reprint lines up.   maybe someone can weigh in on that.

---

### Post by methane on 2006-10-24
Can someone tell me how I can get this to install correctly on an AMD64 system?  I've got a HP zv6000 laptop and I get this error when using alien:
> brad@Azkaban2:~/Desktop$ sudo alien -i lightscribe-1.4.113.1-linux-2.6-intel.rpm
Warning: Skipping conversion of scripts in package lightscribe: postinst
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/lightscribe
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)dh_gencontrol
[COLOR="Red"]dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)[/COLOR]
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: lightscribe-1.4.113.1: No such file or directory
brad@Azkaban2:~/Desktop$



---

### Post by Megatog615 on 2006-10-31
Does anyone have an Ubuntu picture(like maybe the icon) that could be used for lightscribe?

---

### Post by barkerben on 2006-11-04
I have found that this wont work with an AMD64 system also. Does anyone have any ideas if an ord when this is likely to change?

Cheers,

Ben

---

### Post by kickinmhl on 2006-11-04
Just for everyones information:

I just installed this software and burned labels on a Lite-On SHM-165H6S which I bought recently at NewEgg for $32.99.  It worked perfectly.

Good luck all

---

### Post by punx45 on 2006-11-09
this software worked for me until tonight.   doesnt seem like it has anything to do with it but i installed the new nvidia drivers that were discussed today in another thread un ubuntuforums.   anyone else having some sudden trouble?

---

### Post by StefAndrew on 2006-11-10
What version are you using?  Dapper or Edgy?

---

### Post by seanUSXIII on 2006-11-13
Haha! THis is the windows killer for me!! :)

EDIT: Never mind. It segfaults on Edgy.:( Anyone know how to fix this?

---

### Post by methane on 2006-11-27
Hi,
I just got my lightscribe drive working with 64-bit Dapper Drake. How I did it follows (also including the labeler):
Download the files from LaCie to a 32-bit Dapper machine.
run alien:
 sudo alien -d lightscribe-1.4.113.1-linux-2.6-intel.rpm
 sudo alien -d 4L-1.0-r6.i586.rpm

transfer the files to the 64-bit machine.  then:
 sudo dpkg -i --force-architecture lightscribe_1.4.113.1-1_i386.deb
 sudo dpkg -i --force-architecture 4l_1.0-1_i386.deb

then, to run, as root:
 sudo $L-gui

done.!  burned one tonight just to test and it looks great.

Hardware:
HP ZV6000 laptop:
Dapper Drake
drive: TSSTcorp - CD/DVDW TS-L532M - HR08

---

### Post by MMoudry on 2007-07-27
Hmmm I am trying to do the same thing. I am trying to make the 32-bit packages run on a 64-bit feisty. Did you install any special 32 bit libraries first or did it just work out of the box?

MM

---

### Post by methane on 2007-07-27
Really, At this point I don't remember.  I will say that I don't think I had to do anything special and that I think there was enough information in the rest of the posts in this thread to get it to work for me.  I'm no technical genius when it comes to this, so I think it was pretty easy.

The only reason I even did it on the 32-bit machine was because I couldn't get the 64-bit Alien to not complain that it wasn't the right architecture.  It's possible that you run it with chroot?  I don't know anything about how to use that though.

Maybe you should describe what types of problems you're having and we can try to help.  Where do you hit an error?

---

### Post by MMoudry on 2007-07-27
Well the packages install all right by using your method, the lightscribe_1.4.136.1-0_i386.deb says something about chown lightscribelicense.rtf not found but installs itself.

However the problem is that I am not able to execute the 4L-cli, this is the output of ls -l of my /usr/4L :
-rwxr-xr-x 1 root root   60540 2006-08-10 15:20 4L-cli
-rwxr-xr-x 1 root root 6320572 2006-08-10 15:20 4L-gui
drwxr-xr-x 2 root root      31 2007-07-27 21:33 doc
-rwxr-xr-x 1 root root    2562 2006-08-10 15:20 lacie_website.sh
drwxr-xr-x 2 root root      55 2007-07-27 21:33 templates
drwxr-xr-x 2 root root     101 2007-07-27 21:33 translations

the executables are executable, however when I try to execute them with :
myuser@myhost:/usr/4L$ sudo ./4L-cli

I get :
-bash: ./4L-cli: No such file or directory

(when writing this post I noticed that there is another 4L-cli in my /usr/bin that is marked as lrwxrwxrwx... maybe it comes from there)

MM

Edit:
Oh yeah... I am running Feisty fawn server with following uname -a :
Linux myhost 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

---

### Post by david lang on 2007-08-10
is there any way to define a label from a script or command line?

I'd be interested n having my command-line burning scripts add a label to the disk, but if I would have to fire up a GUI to get the label I'll stick to leaving a pen on top of the computer.

---

### Post by bean77 on 2007-09-19
I'm having a really hard time getting this to work.

---

