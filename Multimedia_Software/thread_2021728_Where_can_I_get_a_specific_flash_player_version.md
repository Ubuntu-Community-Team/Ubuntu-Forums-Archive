---
title: "Where can I get a specific flash player version?"
date: 2012-07-09
forum: Multimedia Software
---

### Post by masonTen on 2012-07-09
Hi all,
I had to install flash player recently (11.2 version) and I realized that it sucks.
So i tried to install a previous version such as 10 but I couldn't find a .deb or similar on the internet.

So where can I get a specific flash player version?
Thanks

---

### Post by ron999 on 2012-07-09
> **masonTen said:**
> 
So where can I get a specific flash player version?

Hi
I (sometimes) use flash plugin v-10.1.102.64 ;)
Downloaded from here ---> [http://kb2.adobe.com/cps/142/tn_14266.html#main_Archived_Flash_Player_versions_for_developers]("http://kb2.adobe.com/cps/142/tn_14266.html#main_Archived_Flash_Player_versions_for_developers")

Download the archive that you need...
unzip it...

File is named "libflashplayer.so".

On my system I've put it in folder "/usr/lib/flashplugin-installer".
(Kept the original one in there too, just re-named it "NEWlibflashplayer.so").
Then when you re-start Firefox, it will see the replacement file instead.
:)

---

### Post by masonTen on 2012-07-09
None of the zip files had a *.so file. Are you sure about the link?

---

### Post by flemur13013 on 2012-07-09
Try this (.deb files)
[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)
(I wanted to go to 10.whatever, but there's no 64 bit version and the 32 bit wants a lot of libs).

Edit:
> None of the zip files had a *.so file. Are you sure about the link?

That redirects to the link below; it had .so files along with Mac and Win stuff for each version, you have to go down thru the archive:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Good luck!

---

### Post by ron999 on 2012-07-09
> **masonTen said:**
> Are you sure about the link?
Yes

fp_10.1.102.64_and_9.0.289.0_archive.zip
contains folder
fp_10.1.102.64_and_9.0.289.0_archive
contains folder
Flash Player 10.1.102.64
contains folder
10_1r102_64
contains archive
flashplayer10_1r102_64_linux.tar.gz
contains file
libflashplayer.so

---

### Post by DaveyG on 2012-07-10
> **ron999 said:**
> On my system I've put it in folder "/usr/lib/flashplugin-installer".

I'd also recommend (if you're using Firefox) placing libflashplayer.so in Firefox's add-ons folder (/usr/lib/firefox-addons/plugins)

---

### Post by masonTen on 2012-07-11
I assume I was blind when I didn't find the *.so file :)
Thanks for those valuable links too.

I had to replace my current version in firefox
/usr/lib/firefox-addons/plugins)
and chromium directory as well
/usr/lib/chromium-browser/

Thanks all!

---

