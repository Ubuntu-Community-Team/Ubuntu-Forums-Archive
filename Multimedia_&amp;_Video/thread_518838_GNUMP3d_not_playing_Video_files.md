---
title: "GNUMP3d not playing Video files"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by sunra350 on 2007-08-06
I've setup GNUMP3d it streams mp3's great the issue I'm having is streaming video. I've changed the default directory to my home folder via the gnump3d.conf file. I get the following error when I try to stream the video file(avi).

Error
The requested file /home/sunra/music/video/TheUnderDogsTales2007.avi couldn't be found. Please try returning to the index.
If you believe you are seeing this in error please consider reporting a bug

 Is there another section I'm supposed to edit for video streaming support?

Thanx,

--SunRA--

Resolution:

hey I got it to work in the Ubuntu repositories it doesn't have the final version GNUMP3d. I found this fix: I edited the /usr/bin/gnump3d file to include

# Strip directories for movies aswell
$file =~ s/^$ROOT\/(.*\/)*//;

-----------------
Fix Details
-----------------
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=394370;msg=10;filename=movies.diff;att=1](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=394370;msg=10;filename=movies.diff;att=1)

diff -ruN orig/gnump3d-2.9.9.9/bin/gnump3d2 gnump3d-2.9.9.9/bin/gnump3d2
--- orig/gnump3d-2.9.9.9/bin/gnump3d2	2006-11-09 13:08:32.000000000 +0100
+++ gnump3d-2.9.9.9/bin/gnump3d2	2006-11-09 13:09:24.000000000 +0100
@@ -2554,6 +2554,9 @@
 	    {
 		next if ( not $FILE_TYPES->isMovie( $file ) );
 
+		# Strip directories for movies aswell
+		$file =~ s/^$ROOT\/(.*\/)*//;
+
 		# Increase count.
 		$totalMovies += 1;

---

### Post by BigRD on 2007-08-15
I'm having the same problem so thanks for the tip.  However can you tell me where in the file to add the line - sorry for my ignorance.

R.

---

### Post by stalker145 on 2007-09-11
WOOT!!

Thanks for that research. I've been pulling my hair out over this one.

---

### Post by bensibensa on 2007-11-30
Thank you so much 

Open source will be a language one day

---

### Post by shmolf on 2007-12-03
I tried copying 

# Strip directories for movies aswell
$file =~ s/^$ROOT\/(.*\/)*//;

and

diff -ruN orig/gnump3d-2.9.9.9/bin/gnump3d2 gnump3d-2.9.9.9/bin/gnump3d2
--- orig/gnump3d-2.9.9.9/bin/gnump3d2 2006-11-09 13:08:32.000000000 +0100
+++ gnump3d-2.9.9.9/bin/gnump3d2 2006-11-09 13:09:24.000000000 +0100
@@ -2554,6 +2554,9 @@
{
next if ( not $FILE_TYPES->isMovie( $file ) );

+ # Strip directories for movies aswell
+ $file =~ s/^$ROOT\/(.*\/)*//;
+
# Increase count.
$totalMovies += 1;

at the beginning or end of the file. Not both at the same time. With the first version, nothing changes, and i can still access my site. When i copy and paste the second version, the site doesn't respond. Program error. Where should i post the information, and do i include just what sunra350 included, or what the link contains?

i am running gnump3d v2.9.9.1.

should i upgrade to v2.9.9.9 before adding the code?

thanks

---

### Post by shmolf on 2007-12-03
I resolved the issue.

Search for

		next if ( not $FILE_TYPES->isMovie( $file ) );

and it will take you the the spot.

Just below that line copy 

# Strip directories for movies aswell
		 $file =~ s/^$ROOT\/(.*\/)*//;

Save it.

Restart gnump3d by typing this in the terminal 

sudo /etc/init.d/gnump3d restart

Refresh your page.

---

