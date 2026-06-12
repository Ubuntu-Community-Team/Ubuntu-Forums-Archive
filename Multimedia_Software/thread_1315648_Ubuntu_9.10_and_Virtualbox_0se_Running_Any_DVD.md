---
title: "Ubuntu 9.10 and Virtualbox 0se Running Any DVD"
date: 2009-11-05
forum: Multimedia Software
---

### Post by Whiteaker on 2009-11-05
I'm not sure if this is the right forum or not so I apologize in advance.
I have Virtualbox OSE 3.08 installed and the AnyDVD 6.5.9.5  I get disk dirty or region set wrong when scanning any dvd. 

Does anyone have this working correctly? Wine won't let me use AnyDVD at all. I really don't want a dual boot XP on my computer. I have used AnyDVD and DVD Shrink to backup all my DVD's for years.

I have seen where others have said to enable passthrough on my cd rom settings in virtualbox, but when I do this Anydvd won't even start. 

Please help. I love Ubuntu!! Thank you!

---

### Post by Whiteaker on 2009-11-05
Wow no one @ all!!

---

### Post by dxxvi on 2009-11-06
If you don't care about your backup file sizes, then you don't need anydvd nor dvdshrink.

dd if=/dev/cdrom of=~/file.iso

After that you can mount your file.iso to a directory:

mkdir /tmp/somedirectory
sudo mount -o loop ~/file.iso /tmp/somedirectory

and use vlc to watch the movie in /tmp/somedirectory.

---

### Post by Whiteaker on 2009-11-06
Thank you for your reply! I appreciate it! 
:popcorn:

---

### Post by Yellowhead on 2009-11-07
FWIW, I just upgraded to 9.10 and, after discovering that vmware no longer appears to be supported, tried virtualbox as an alternative. Like you, I use anyDVD and DVDshrink to backup DVDs but I couldn't get it to work until I read your post and enabled passthrough. This seems to have done the trick :D Not sure why it didn't work for you though ...

---

### Post by Whiteaker on 2009-11-08
Glad to have helped you, but still no go for me though

---

### Post by Whiteaker on 2009-11-08
I removed Virtual box and reinstalled it. I then enabled pass through support on the CD Rom, and it works like a charm. You must do this or it will **NOT **function correctly. Hail Virtual box!! That being said I was also able to download and install K-9 Copy from Ubuntu software center and it will remove copy protection and Shrink the DVD all in one shot. Very impressive indeed.. I hope this helps others!!

---

### Post by 666f6f on 2010-04-16
It is true that you don't need [VirtualBox]("http://www.virtualbox.org")+[AnyDVD]("http://www.slysoft.com/en/anydvd.html") combination in the first place, unless you need support for BlueRay discs or you need to remove protections other than CSS. I guess K-9 is fine but if you like the command line, you may also consider the [dvdbackup]("http://dvdbackup.sourceforge.net/")+[libdvdcss]("http://www.videolan.org/developers/libdvdcss.html") combination. 

[Here]("http://forums.fedoraforum.org/showthread.php?t=65272") is a link to a post that provides a good explanation on how to use those two tools. Make sure you read the [Restricted Formats/Playing DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") wiki page to make it work under Ubuntu.

If everything is setup properly, you just have to open a terminal and type ```
dvdbackup -M
``` Could it be any simpler?

**UPDATE:** I just stumbled upon [OGMRip]("http://ogmrip.sourceforge.net/en/index.html") which seems to be light and efficient.

Off course, you need to check with your local laws to make sure usage of libdvdcss2 would be legal in your area.

---

