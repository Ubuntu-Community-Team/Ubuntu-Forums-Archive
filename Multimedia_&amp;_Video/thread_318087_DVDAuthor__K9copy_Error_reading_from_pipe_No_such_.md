---
title: "DVDAuthor / K9copy Error reading from pipe: No such file or directory"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by shields on 2006-12-13
I am trying to use K9copy to separate some video I recorded on some DVD+Rs I made.

When running K9copy, I open the dvd.  It loads with the title and menus. When I try to copy the video selection from the DVD it pauses then comes back with a popup box that says:

[B]An error occurred while running DVDAuthor:
ERR: Error reading from pipe: No such file or directory
[/B]

I have qDVDAuthor installed and have noted under preferences/paths that oggdec is not found on the machine.  Not knowing how to install it, I changed oggdec to mencoder.  This eliminates the error message, but K9copy instead hangs indefinitely.:confused: 

Does anyone know how I can find oggdec and help qDVDauthor find it?  I am a REAL newbie, so please be patient as you answer.;) 

Thanks!:)

---

### Post by shields on 2006-12-14
OK -- no one knows? :( 

Can you maybe point me to a different place where I can ask this question? :confused: 

Thanks?:-k

---

### Post by fireboxtester on 2006-12-16
I hit the exact same error!  

I submitted a bug here:
[http://sourceforge.net/tracker/index.php?func=detail&atid=805544&aid=1617098&group_id=157868]("http://sourceforge.net/tracker/index.php?func=detail&atid=805544&aid=1617098&group_id=157868")

Since I have no idea what DVD author is I'm going to try [building the newer beta version from source]("https://help.ubuntu.com/community/BuildingK9CopyfromSource")

If that fails I'm going to try [DVDShrink.]("https://help.ubuntu.com/community/DVDShrink")


... of course someone could also just chime in with a DVD Author answer.  that would be cool too.....

---

### Post by shields on 2006-12-16
Thanks.  I will try to keep an eye on that thread in the bug place. :cool:   If you get any reply or a better idea, please let me know!  :)

I think that DVDAuthor is what K9COPY uses to create the ISO for burning to DVD.  However, DVDAuthor doesn't have all the encoders, etc. built in.  I have installed QDVDAuthor via the ubuntu app installer, but when I look at some of the PATHS in the SETUP, they are orange or red, indicating that the necessary tools are not on my system.  I managed to install some of them, but not all.  I am missing the following:
[I]VideoTrans: movie-to-dvd
Ogg Dec: oggdec
PMC to AIF: pcm2aif
MC TooLame: mctoolame.[/I]

I am guessing that K9COPY is asking DVDAuthor to do some work, and DVDAuthor doesn't have the right tools for the job.  Being a newbie to linux, I just don't know how to install what it needs.

---

### Post by shields on 2006-12-22
**Another observation:**
This problem does not exist when I work with DVDs not recorded on my home DVD recorder.  Though I didn't let it complete, I stuck a commercially produced DVD into my drive and it started extracting the data without problem.

I find the fact that it will not work with my personally created DVDs odd since K9COPY will let me *preview* those same DVDs.  But when extracting the data to create an ISO, it either gives me the "Error reading from pipe" error, of just hangs at 1% indefinitely.

Any thoughts?

Thanks! :)

---

### Post by adelante on 2007-05-22
I get the same error message when trying to copy scratched disks.  It authors the disk for a while, maybe 80% all looks OK, then it can't read a scratched section and gives up.  With same settings it works fine for a disk without scratches.  I still resort to DVD Decrypter (Windows) for scratched disks.  I'll try DVD Shrink which I've read is supposed to be better.

---

### Post by Dec on 2007-05-22
I dont know if it may help but i was getting the same error message wen i noticed that logs were complaining about the parentisis in the title of the movie i was trying to legaly copy ;)

Look out for parentisis or any other no standard character in the name of the movie or path to it.

Hope it helps!

---

### Post by eeried on 2007-06-26
hello,

I got the same error today on Xubuntu feisty.

I'm experimenting on ripping. I had full success with ripping one of my commercial DVD which has no DRM (but requires libdvdcss2 to be read in VLC), and I could watch the iso file on VLC: that was on Ubuntu Dapper.

Now on Xubuntu Feisty I tried to rip the same DVD and I'm getting the same error as you all got.

I gave the iso file a name without any strange characters and I'm still getting this error.

In the settings I can't see any mention of DVDauthor: the device-not-detected pane is blank.

I'll try uninstalling dvdauthor and reinstalling it but I'm doubtful.

---

