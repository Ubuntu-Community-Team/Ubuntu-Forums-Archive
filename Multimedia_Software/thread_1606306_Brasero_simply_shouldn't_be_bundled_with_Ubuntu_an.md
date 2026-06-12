---
title: "Brasero simply shouldn't be bundled with Ubuntu any more."
date: 2010-10-26
forum: Multimedia Software
---

### Post by Repgahroll on 2010-10-26
Hello there.
I don't understand why Brasero was chosen as the default burning app. The fact is Brasero could NEVER burn a CD/DVD correctly on every system that i've tried - mostly Pioneer and LG writers. Sometimes it returns an error, sometimes it claims the data had been burned correctly but in fact it's corrupted. Every Ubuntu version that I install I try to use it but even after more than 20 different hardware and uncountable versions & hardware combinations, I couldn't burn even a single CD/DVD successfully. On the other side, GnomeBaker never failed to burn. It's a mature, friendly and reliable app. And I don't know if they're using the same back-end, but if they are, Brasero isn't sending the right parameters to it.
Also, not only me, but a lot of people have problems using Brasero. Some even have problems with GnomeBaker (i'm not sure if it's a software malfunction, probably not), and some of those are forced to install K3B or even the commercial Nero.
So. imho, Ubuntu should replace Brasero by GnomeBaker.

PS:
An even better solution would be a "G3B"... a K3B conversion for GTK. However, opensource developers rarely (or never) join forced. I they did, all the software would be free already, and the proprietary software for home and office use would be extinct. Too many people are working on their own projects that does pretty much the same thing with lots of flaws, an example is GnomeOffice, OpenOffice, LibreOffice, KOffice, every one has its own pros and cons, and 3 of them are in development for more than 10 years, I wonder how good the OfficeSuite would be nowadays if they'd joined forces at the beginning. The result is always the same, OpenSource means much quantity and poor quality. The only hi-quality and hi-tech opensourced programs are the ones where many developers joined efforts, like the linux kernel, iptables, grub, gnu tools, gnu compilers, etc. and it's easily noticeable that they're good because the development is centralized.
Imho, users would prefer to be free to choose between a 'reliable opensource program' and a 'proprietary one', instead of a 'proprietary program' and 'hundreds of poor-quality opensourced ones'.

---

### Post by lavinog on 2010-10-26
Are you having this issue in Maverick?
What operations are you doing that is having issues? Are you burning ISOs?

---

### Post by FNoo on 2010-11-01
I am using 10.04 and I am trying to burn the 10.10 iso. Brasero puts up a message "Please replace the disk with a supported CD or DVD".  I assume that the in-window option to write to disk is also using Brasero as the pop-up is identical and has the same message.

I used three different makes of CD-R disk, Rackard Bell, imation and Maxell, straight out of the box having removed the cellophane. 

Another thread suggested using Gnomebaker but that does not have an option for burning iso images, although it does identify the disk in the CD drive as a writable CD that is empty.

Can anyone suggest a solution?

Is there a CLI command for writing an iso to disk?

What other freely available packages support writing iso files to disk?


Thanks in advance.

---

### Post by DavePlummer on 2010-11-01
Sorry, no solution. I have experienced multiple problems with Brasero in Ubuntu 10.04 1nd 10.10. Brasero works perfectly for me with Fedora 14 Beta and Debian Squeeze. I am currently exploring the possiblity of ditching Ubuntu in favor of Debian Squeeze.

---

### Post by ezsit on 2010-11-01
I have used the Nautilus CD/DVD Creator app in Ubuntu 9.10 and 10.04 with success, and that app merely calls Brasero as the back-end burner.

However, now that I have installed 10.10, Brasero refuses to burn a CD or DVD without corrupting the entire contents of the disc. I have tried creating data CDs and DVDs from scratch by opening Brasero and choosing to create a data CD/DVD. Four attempts failed with the same result - every file on every burn was corrupted beyond any application being able to open or view the files.

Gnomebaker and Xfburn both work perfectly, except neither abides by my speed settings.

I give up on Brasero and will use Gnomebaker from now on. But why is it failing? And if it is a Brasero specific problem, why don't we hear more about problems?

---

### Post by ezsit on 2010-11-01
> Another thread suggested using Gnomebaker but that does not have an option for burning iso images, 

Gnomebaker most certainly does burn ISO images to CD and DVD. I use that often. The command is under the Tools menu if I remember correctly. I'm not at my Ubuntu box, but look for it and it should be listed as "burn disc image" under the tools menu.

---

### Post by marl30 on 2010-11-01
Since I've been seeing a lot of complaints on here about Brasero, I haven't used it since. I've been using mainly these three instead: AcetoneISO, Gnomebaker, and K3B.

---

### Post by FNoo on 2010-11-01
> **ezsit said:**
> Gnomebaker most certainly does burn ISO images to CD and DVD. I use that often. The command is under the Tools menu if I remember correctly. I'm not at my Ubuntu box, but look for it and it should be listed as "burn disc image" under the tools menu.

I stand corrected, it does have an iso burning option. As you say it is in the tools menu list. The 'new project tools' have icons for Data DVD, Data CD and Audio CD, which led me to my first incorrect impression. I concede I was too hasty to judge and in the interim I downloaded K3B which did solved my immediate problem.

I will take another look at Gnomebaker and K3B seems like a very good package but I think I will forego trying to get Brasero to work as it has a poor reputation and not just in this thread.

Thank you for the input.

---

### Post by Odin888 on 2010-11-01
Ya I agree. Mine worked fine with 9.1 (still on one of my older systems)but now it just keeps trying to burn without summarizing and finishing.

---

### Post by honkydrum on 2010-11-22
First-time poster ('bout time I came out of my shell.....).

For what it's worth, I switched to Gnomebaker with Lucid; like most everybody else, I could not get Brasero to copy a CD or DVD. After upgrading to Maverick, I thought I'd try Brasero one more time, and lo and behold, it copies DVDs fine. I've copied four now, and they all play fine on both standalone players I have.

Haven't tried burning from an .iso yet, though.....

[Update] It's even copying and burning dual-layer DVDs without a hitch. Wow.

---

### Post by pccampos on 2010-12-01
The complains about Brasero are real. When I used to dual boot on Linux and Windows I always used Linux because the chances of a failure was less than Windows. I had 4 attempts to burn a simple mp3 cd and all failed on Brasero. It is a shame.

---

### Post by a-user on 2010-12-01
hmm interesting. i used brasero to burn my maverick image on cd. i was on lucid. i used brasero on karmic and lucid without any problems. since maverick i didn't tried it again.

---

### Post by lidex on 2010-12-02
If you know anything about open-source, you know that complaining on the forums isn't going to accomplish anything. It's about community and YOU are part of that. If something doesn't work, file a bug report and follow up on it so it will get fixed.

---

### Post by BiggoCharley on 2010-12-10
> **FNoo said:**
> I stand corrected, it does have an iso burning option. As you say it is in the tools menu list. The 'new project tools' have icons for Data DVD, Data CD and Audio CD, which led me to my first incorrect impression. I concede I was too hasty to judge and in the interim I downloaded K3B which did solved my immediate problem.

I will take another look at Gnomebaker and K3B seems like a very good package but I think I will forego trying to get Brasero to work as it has a poor reputation and not just in this thread.

Thank you for the input.
I have been fighting the brasero battle fir some time (using lucid and before that --jaunty) and did a search and found this thread. I see its a bit old but worth a try. 

I just tried to burn an iso image (linux mint 10) with Gnomebaker using the commmand under the Tools menu "burn dvd image" and it behaved just like Brasero has been doing.burned a data dvd instead. Now I'm really at a loss. Anybody else had this experience??

---

### Post by KinGnu on 2010-12-12
I could not agree more... I was having a lot of issues with brasero, and just installed GnomeBaker and worked like a charm!!! this should be taken in consideration... :D

---

### Post by svaens on 2010-12-21
Brasero is crap, and doesn't work.
Ubuntu should take better care that the software that is so tightly integrated into the system actually does its job. But again today, with Maverick, i've had to use k3b, after having given Brasero yet another change after upgrade to Maverick.

To those who say 'file a bug' 

I've done that a few times, only to be fobbed off with 'incomplete or invalid status' ....

---

### Post by sir_robert007 on 2010-12-21
Brasero in my experience has a hard time burning dual layer disks as the data becomes corrupted during the layer transition. However copying DVD's to an image file seems to work well so i use Brasero for copying disks and K3b for burning disks as k3b has better error protection than Brasero.

---

### Post by cottfcfan on 2010-12-21
I've had issues with all the OS Burners at one time or another.
Then I tried out Nero-Linux, 100% success since. You get a months trial and after that it cost around £15. But its well worth it.

---

### Post by Old_Man_Unix on 2010-12-21
> **cottfcfan said:**
> I've had issues with all the OS Burners at one time or another.
Then I tried out Nero-Linux, 100% success since. You get a months trial and after that it cost around £15. But its well worth it.
 
I do agree with this "solution". Sometimes you just have to bite the bullet and buy something, even with Linux.
 
Nero Linux is something of an illegitimate child compared to Nero Burning ROM - the Windows product - but it is still a very slick piece of work.

---

### Post by ussndmac on 2010-12-21
As many others have, I switched to Gnomebaker a while back. No problems since.

When I upgrade Ubuntu, I just delete the menu entry for Brasero.

---

### Post by haircat on 2010-12-24
You can use freeware dvd or cd burner {windows software} Imageburn

just google it to find it-- Works great under wine 1.39

haircat

---

### Post by Rasa1111 on 2010-12-24
Brasero has *always* worked great for me! 

CD's, Iso's, DVD's, , etc etc. 

 Never had a problem with it.

---

### Post by nmyrick on 2011-02-20
To those who are having trouble with Brasero.  Do you have Ubuntu Restricted Extras and libdvdcss2 installed?  If not, this may solve many of your DVD/CD and image copying issues.

Go to your synaptic package manager and enter these into the search and install them from there.

---

### Post by uRock on 2011-02-20
> **lidex said:**
> If you know anything about open-source, you know that complaining on the forums isn't going to accomplish anything. It's about community and YOU are part of that. If something doesn't work, file a bug report and follow up on it so it will get fixed.

^^^^^This^^^^^

I haven't had any issues with Brasero. It has not given me any bad recordings.

---

### Post by babarosa on 2011-02-21
Brasero coming with Ubuntu 10.04 used to have issues (in Ubuntu 10.10 I think they are solved).

If you are using (X)Ubuntu 10.04 LTS, replace brasero _and_ cdrdao (!) with these versions:
[https://launchpad.net/~renbag/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~renbag/+archive/ppa?field.series_filter=lucid)

---

### Post by blitzd on 2011-03-22
...also having a lot of issues with Brasero on 10.10. I will try GnomeBaker and see if it's any better.

First issue I ran into was at the end of a data-disc burn it said it couldn't eject, and that I should manually eject to complete - so I manually ejected, but the prompt never went away until I hit cancel - and after that it says the burn failed. Sure enough every file on the disc was corrupt, as others have had happen. I did a bit of googling on this and found that the issue was with the checksum plugins, and sure enough the next disc I went to burn was fine after I disabled both the file and checksum plugs.

Second issue was after burning a disk it would no longer recognize blank discs anymore and would only burn to an image. I'd have to exit brasero, re-open it, and then it would work.

Third was that it would randomly hang on 'getting size'. I'd have to cancel, close brasero, re-open and retry.

And, while it's not really a bug with brasero, it's still worth mentioning as the cherry on top of the whole experience - when I went to file a bug, bugzilla.gnome.org gives a 500 Internal Server Error.

So, all in all I would agree with the sentiment that Brasero shouldn't be bundled with Ubuntu anymore.

---

### Post by Yellow Pasque on 2011-03-23
I prefer xfburn for a lightweight gtk-based burner (though its interface could be more intuitive at places). Usually, I just install k3b, though.

---

