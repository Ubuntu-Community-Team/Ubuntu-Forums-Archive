---
title: "Amazon mp3 downloader conflict"
date: 2010-06-29
forum: Multimedia Software
---

### Post by varga49 on 2010-06-29
While trying to install the amazon mp3 downloader  I got this package installer message : "Error: Dependency is not satisfiable: libboost-filesystem1.34.1" 

Amazons ubuntu version of this downloader is for the 9.04 version and not the10,04 LTS which I am using. 
any help?
Thanks in advance

---

### Post by projectbronco on 2010-06-29
I know this isn't what you are asking, but you don't even have to use the downloader. You can just download the music using your browser. It is still high quality (256) and you can send it to whatever folder you want.

---

### Post by bark50 on 2010-06-29
This doesn't exactly address your problem either, but here's an article about a replacement downloader for Amazon's music store:  [http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html]("http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html")

And if you're a Banshee user, there's an alternate downloader coming down the pike soon:  [http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html]("http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html")

I haven't tried either of them, so I can't vouch for them.

---

### Post by varga49 on 2010-06-30
> **projectbronco said:**
> I know this isn't what you are asking, but you don't even have to use the downloader. You can just download the music using your browser. It is still high quality (256) and you can send it to whatever folder you want.
Thanks ..amazon won't let me download an entire album without using their downloader...I can always order the cd...but !!!

---

### Post by varga49 on 2010-06-30
> **bark50 said:**
> This doesn't exactly address your problem either, but here's an article about a replacement downloader for Amazon's music store:  [http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html]("http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html")

And if you're a Banshee user, there's an alternate downloader coming down the pike soon:  [http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html]("http://www.omgubuntu.co.uk/2010/06/amazon-mp3-download-extension-for.html")

I haven't tried either of them, so I can't vouch for them.
Thanks I'll check it out!

---

### Post by Yellow Pasque on 2010-06-30
You should be able to install the prerequisite boost packages by downloading them from the ubuntu packages site. You can have multiple versions of boost installed.

---

### Post by dzmijewski on 2010-07-07
I had the same error and ended up having to install the  following packages to get Amazon mp3 installed

libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb
libicu40_4.0.1-2ubuntu2_i386.deb
libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb

---

### Post by Lambchopper on 2010-07-08
> **dzmijewski said:**
> I had the same error and ended up having to install the  following packages to get Amazon mp3 installed

libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb
libicu40_4.0.1-2ubuntu2_i386.deb
libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb
libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb


This worked for me.  Incidentally, I found the LIBBOOST files [here]("https://launchpad.net/ubuntu/+source/boost/1.34.1-16ubuntu1/+build/1037118") towards the bottom of the page

and

I found the LIBICU file [here]("http://packages.ubuntu.com/karmic/i386/libicu40/download")

You'll need to install the LIBICU file before the LIBBOOST-REGEX file.  After you install those, then install the Amazon Deb package and it works.

The Lamb

---

### Post by daqron on 2010-07-09
Ah, my daily reminder that Linux isn't ready for casual users yet. The Amazon downloader doesn't work at all in 10.04. I installed the libboost libraries from the Software Center but they are all version 1.40.0 and that's evidently not what the Amazon software wants. Shouldn't the Package Installer resolve these dependencies?

---

### Post by ubugrrl on 2010-07-10
As someone mentioned above, get [pymazon]("http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html") ... easy to install (and i'm an unbuntu noob) and works great!

---

### Post by cinger on 2010-07-15
I am having trouble locating these packages necessary for the amazon album app via aptitude and KPackageKit.  I know a previous post listed the web addresses of the .debs, but I wanted to learn how to use aptitude and/or KPackageKit to download packages through a manager instead of via the web.  Apt-get install is about as complex a task as I've done previously.  I launched aptitude, hit \, entered libboost-filesystem, libboost-filesystem1.40.0 is listed, libboost-filesystem1.34.1 is not listed.  Selecting libboost-filesystem1.40.0 I receive 

```
-- libboost-system1.40.0 (>= 1.40.0-1) (UNSATISFIED)
--- libc6 (>= 2.3.6-6~)
--- libgcc1 (>= 1:4.1.1)
--- libstdc++6 (>= 4.1.1)

```Do I need to try and install those listed files first?  I am on a fresh install of Ubuntu 10.04.  
Thanks for any assistance.

---

### Post by Yellow Pasque on 2010-07-15
> **cinger said:**
> I am having trouble locating these packages necessary for the amazon album app via aptitude and KPackageKit.  I know a previous post listed the web addresses of the .debs, but I wanted to learn how to use aptitude and/or KPackageKit to download packages through a manager instead of via the web.  Apt-get install is about as complex a task as I've done previously.  I launched aptitude, hit \, entered libboost-filesystem, libboost-filesystem1.40.0 is listed, libboost-filesystem1.34.1 is not listed.  Selecting libboost-filesystem1.40.0 I receive 

```
-- libboost-system1.40.0 (>= 1.40.0-1) (UNSATISFIED)
--- libc6 (>= 2.3.6-6~)
--- libgcc1 (>= 1:4.1.1)
--- libstdc++6 (>= 4.1.1)

```Do I need to try and install those listed files first?  I am on a fresh install of Ubuntu 10.04.  
Thanks for any assistance.
Because amazonmp3 is a closed-source program in need of an update, you have to download some of the prerequisites manually, as lambchopper did above. Then you can install them using dpkg -i

---

### Post by cinger on 2010-07-15
Okay, thanks for the response.

---

### Post by Seagarz on 2010-08-06
lambchopper method worked perfect  !!! Thanks for all the great info, LOVE the forums. 

Found this thread also which might work a bit quicker though..

[http://ubuntuforums.org/showthread.php?t=1478214&highlight=amazon+mp3+downloader](http://ubuntuforums.org/showthread.php?t=1478214&highlight=amazon+mp3+downloader)

---

### Post by Wharf Rat on 2010-10-27
> **ubugrrl said:**
> As someone mentioned above, get [pymazon]("http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html") ... easy to install (and i'm an unbuntu noob) and works great!

Oh yeah!!!  Great Product.

---

### Post by MDM72 on 2010-11-29
I don't know if this is a good idea or not, but I figured out a way to get the Package Installer to auto-magically download and install all the dependencies by adding the Karmic package URLs to my apt sources.

After making a backup copy, I added the following three lines to /etc/apt/sources.list file:
```
[B]#  hack added to pull older (Karmic 9.10) packages 
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe[/B]

```After saving the file, I then ran the following command in a Terminal to refresh the package lists:
```
sudo apt-get update

```Then I re-opened the amazonmp3.deb file and this is what the Window  looked like:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176939&stc=1&d=1291057402[/IMG]

I then clicked Install Package, and the Amazonmp3 package and all dependencies were automatically installed.

One thing to point out here -- updating the sources.list file means that, **for better or worse**, these Karmic package sources will be available for everything, not just the Amazonmp3 package.  This is why I'm not sure if this is a good idea or not.

---

### Post by Yellow Pasque on 2010-11-29
^That's a terrible idea.

---

### Post by anechoic on 2011-04-06
ditto on pymazon - downloaded and works great (and you don't have to do the Linux dep dance) -- one annoying thing though: it downloads all the files scattered into one directory - not politely into a named directory as it should

---

### Post by MorayJ on 2011-07-21
Seems like Banshee has an amazon downloader built in now, so if you go that route it works.

Probably keen that we do so they get a referral :-)

Moray

---

### Post by aerobeing on 2011-07-30
Thank you to those, who suggested pymazon. It's simple, easy to use, and does just what it's supposed to. :D

---

