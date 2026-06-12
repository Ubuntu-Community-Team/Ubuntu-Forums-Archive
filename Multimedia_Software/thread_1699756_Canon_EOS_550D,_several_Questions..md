---
title: "Canon EOS 550D, several Questions."
date: 2011-03-04
forum: Multimedia Software
---

### Post by Narchie on 2011-03-04
Hi, 

I have a EOS 550D and have a few problems with it and Ubuntu.

I can not seem to get RAW images working properly, they come out as a magenta bar with only the left section of the photo. 

I have tried several fixes to this but am unable to get it working properly. Could someone offer a step-by-step solution to this?

My other problem is live shooting, can it be done? I take lots of macro photos with a long exposure time and also like to focus/align the camera and object with remote shooting as I can zoom in on the edges on the object to see if it is ligned up with the lens properly.


Thanks in advance and hope I put this under the right section.

:)

---

### Post by indytim on 2011-03-04
I suggest:

[http://photography-on-the.net/forum/]("http://photography-on-the.net/forum/")

:o

IndyTim / DataMan

---

### Post by Narchie on 2011-03-04
Thanks but a search for Ubuntu 10.10 eos 550d gave me the following result:
Sorry - no matches. Please try some different terms.

:confused:

---

### Post by tsx2424 on 2011-03-04
Try to read this:

[http://forums.dpreview.com/forums/readflat.asp?forum=1010&thread=27071716&page=1r](http://forums.dpreview.com/forums/readflat.asp?forum=1010&thread=27071716&page=1r) had 

I use Nikon camera and Never having an problem as like that.Asking the Canon or crop the magenta bar  section with photo editing software.

---

### Post by babarosa on 2011-03-04
Narchie,

I am using the Canon EOS 450D.

_Live View Shooting:_
I compiled Canon EOS Movie Record for Linux, send me a PN!

_Import RAW:_
Did you install "ufraw" respectively "gimp-ufraw"?

---

### Post by Narchie on 2011-03-07
Hi and thanks for the replies, 

babarosa, I have installed UFRAW as well as trying several other programs (dcraw, raw studio, raw therapee e.t.c.).

I'll pm you and if you like I can also upload a RAW image to the net for you to test on your system to see if it opens.


Thank you for the assistance :)

Sean

---

### Post by babarosa on 2011-03-07
Narchie,

now you know my website and there is a tool to send me a mail - go to site "Kontakt" and post your picture. I will try to open the raw file with differnet astronomical applications which I use on my xubuntu machine. If I succeed I'll let you know.

For your information, I am using ufraw v0.17, not the default 0.16!

Cheers,
Michael

---

### Post by Narchie on 2011-03-08
Hi Babarosa, 

How do I get the newer version installed?

I tried several sites that either say the package is unavailable and when I try sudo add-apt-repository ppa:pmjdebruijn/ppa it times out.

That is probably my problem here.

The .cr2 files are a bit big to email so I am uploading one to a website, I'll pm you an http link shortly.

Thank you

Sean.

---

### Post by babarosa on 2011-03-08
Here is how to add a third party repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

In launchpad you get info how to add a repo - it looks like this:
> Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:ferramroberto/gimp to your system's Software Sources. (Read about installing)
Technical details about this PPA

This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.
Display sources.list entries for:

deb [http://ppa.launchpad.net/ferramroberto/gimp/ubuntu](http://ppa.launchpad.net/ferramroberto/gimp/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ferramroberto/gimp/ubuntu](http://ppa.launchpad.net/ferramroberto/gimp/ubuntu) lucid main 

Signing key:
    1024R/3ACC3965 (What is this?) 
Fingerprint:
    3E756CF119B127D4DA40A186B725097B3ACC3965

For questions and bugs with software in this PPA please contact Ferramosca Roberto.

---

### Post by Narchie on 2011-03-10
I have added the sources but when trying to add the signing key from several keyservers ( sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 3ACC3965
 ) they just time out so Ubuntu considers these sources as untrusted.

> :~$ sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 3ACC3965
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-key --keyserver keyserver.ubuntu.com 3ACC3965
gpg: requesting key 3ACC3965 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


---

### Post by Sharpie1 on 2011-03-15
I have the same problem, and used UFRaw without any problems with .NEF images from a Nikon camera. I have recently bought the Canon 60D and I'm experiencing the same problems that Narchie is describing. i have attached a jpg that shows the original image on the left and the UFraw import window on the right. I've tried re-installing UFRAW and the Gimp plugin, the .nef files still import fine.. I'm hoping the jpg gives someone a clue as to whats going on, because godammit I had to boot up Vista for the first time in 6 months to make something work !!

Sharpie1

---

### Post by Sharpie1 on 2011-03-15
I trawled up an old post with the same issues
[http://ubuntuforums.org/showthread.php?t=1454719](http://ubuntuforums.org/showthread.php?t=1454719)
anyone got any idea ?

Sharpie1

---

### Post by Sharpie1 on 2011-03-15
Temporary fix..
got the images opening correctly in Rawstudio by installing the daily build 
version Rawstudio 1.1-snapshot3877
[http://rawstudio.org/download.php](http://rawstudio.org/download.php)
I guess ill have to learn batch processing in this new bit of software

Sharpie1

---

### Post by Narchie on 2011-03-17
Thanks for all the assistance, after a bit of [struggling]("http://ubuntuforums.org/showthread.php?p=10561862#post10561862") UFRAW is working perfectly now :) :popcorn:

---

### Post by babarosa on 2011-03-17
Narchie,

you don't know how glad I am!

Raeding the posts on [http://sourceforge.net/projects/eos-movrec/reviews/](http://sourceforge.net/projects/eos-movrec/reviews/) I am still of the opinion, the "EOS Movie Record" Software should work with your model too.

---

### Post by Narchie on 2011-03-18
Going to try it again in a bit and will get back to you.

---

### Post by Narchie on 2011-03-18
Working :D

---

### Post by avacado on 2011-07-12
I also found the magenta stripe mentioned in post 11 when I upgraded from CANON 400D to CANON 60D
I have posted - and answered a question at [https://answers.launchpad.net/ubuntu/+question/164537](https://answers.launchpad.net/ubuntu/+question/164537)
Basically the CR2 RAW format has changed and you need to instal DARKTABLE to decode to another format (at August 2011)
The bad news is DARKTABLE is not in the ubuntu repository - follow my link for instructions on how to get it on your computer
That means someone has got the code and hopefully a community contibutor will add the code to our favourite PHATCH, KRITA UFRAW etc

---

### Post by linchuan on 2011-10-12
> **babarosa said:**
> Narchie,

I am using the Canon EOS 450D.

_Live View Shooting:_
I compiled Canon EOS Movie Record for Linux, send me a PN!

_Import RAW:_
Did you install "ufraw" respectively "gimp-ufraw"?

Wow, I've been trying to compile the EOS MovRec software for quite a while now, however I am always stuck at cmake not finding my libgphoto2 (libgphoto2-2,libgphoto2-2-dev,libgphoto2-port0 are all installed!). How did you get it to work?

Do you maybe happen to have a deb package that I can directly install?

Thanks a lot!

---

### Post by babarosa on 2012-05-22
@linchuan

If you still need the deb (32bit, works fine with v12.04), send me a PM!

---

