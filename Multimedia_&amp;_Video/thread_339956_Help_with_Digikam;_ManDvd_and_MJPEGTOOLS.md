---
title: "Help with Digikam; ManDvd and MJPEGTOOLS"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by granny4linux on 2007-01-16
I am at the end of my rope, been trying days to figure this problem out.
I don't have a lot of hair so I don't want to pull it out and I've already gone grey so my options are few!!! My ultimate goal is to make a SVCD.

When I try to use Digikam to make a MPEG slideshow I get the following error:

"THE COMMAND LINE IS :

images2mpg --with-gui  -f SVCD -n SECAM -d 5 -t 1 -c 000 -T /tmp/kde-suzy/kipi-mpegencoderplugin-5356/ -M /usr/bin -I /usr/bin -w "/home/suzy/mp3/Jim Brickman/Picture This/Jim Brickman - 02 - Sun, Moon & Stars.mp3" -o "/home/suzy/output.mpg" -i  "/home/suzy/Photos/scrapbook/1.jpg"  "/home/suzy/Photos/scrapbook/4.jpg"  "/home/suzy/Photos/scrapbook/7.jpg" 
-----------------------------------------------
Initialising...

Encoding image files...

Images encoding (%) : 0      [0      
   INFO: [yuvscaler] yuvscaler 1.8.0 (15-02-2004) is a general scaling utility for yuv frames
   INFO: [yuvscaler] (C) 2001-2004 Xavier Biquard <xbiquard@free.fr>, yuvscaler -h for help, or man yuvscaler
Images encoding (%) : 0      [0      
**ERROR: [yuvscaler] Could'nt read YUV4MPEG header!"


After much googling and research I found that others have had this problem too. Now  I have come to the conclusion that the problem is in MJPEGtools and that I need to downgrade to a version earlier than 1.6.3. 

I tried to follow the instructions in this post:

[http://www.ubuntuforums.org/showthread.php?t=79715&highlight=mjpegtools](http://www.ubuntuforums.org/showthread.php?t=79715&highlight=mjpegtools)

Only to find out that the Christian Merillat repositories had been moved to:
[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)  so I went there and I added this:
 "deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main"
 to my sources.list. After reloading the Synaptic packages, I selected "mjpegtools" "force version"; the only mjpegtools versions I have the option of forcing are: 1:1.8.0-04 testing or 1:1.8.0-0 Ubuntu Dapper; I am looking for a version prior to 1.6.3.

I also tried to use ManDvd to make the slideshow and came up with a similar error that also led me back to a problem with MJPEGTOOLS.

Any suggestions would be most welcomed.

---

### Post by granny4linux on 2007-01-17
Still trying to solve the problem. Today I compiled  exiv2-0.12, digikam 9.0 and digikamimageplugins9.0  and I still get the error when I try to make an mpeg slideshow with digikam.

I hate to accept defeat but I think I've exhausted my brain on this one. I refuse to go back to windows to do this project. I can go to Kodak Easy Share and have them make a dvd for me if I have to.

---

### Post by 4ebees on 2007-01-17
Hi there granny :)

Regarding the following problem:

**ERROR: [yuvscaler] Could'nt read YUV4MPEG header!"

I'm at work at the moment and cannot recall the 'fix' to the problem; however when I get home (and after the chitlins are in bed) I will look for my notes. 

This was an error I had also - and so have many other people.  I have half a notion that it was a bugfix post that lead me to the solution. I recall that I received no assistance from anyone (sadly). I suspect that few people use this option in Digikam and so there is little knowledge or awareness around it. I only persisted because I like to see things work as they should :))

Did you know that you can achieve the same goal using Kino and you have more option available and more control over the result. This is not to knock Digikam, which I love, but just to let you know that an alternative method exists that is more productive and creative, though requires more effort.

I make lots of video DVDs for the rels and use only Kubuntu Dapper and FOSS to do this (GIMP, Kino, K3B, DVDStyler) so *don't despair* :)

Additionally, if you'd like to swap ideas, techniques etc for video/image creation, I'd be more than happy to write off-post (we could always post a collection back to the forum).

Regards,

Patrick

> **granny4linux said:**
> Still trying to solve the problem. Today I compiled  exiv2-0.12, digikam 9.0 and digikamimageplugins9.0  and I still get the error when I try to make an mpeg slideshow with digikam.

I hate to accept defeat but I think I've exhausted my brain on this one. I refuse to go back to windows to do this project. I can go to Kodak Easy Share and have them make a dvd for me if I have to.

---

### Post by granny4linux on 2007-01-17
Patrick, thank you so much for some great ideas. I did not know kino would do this; can it make an SVCD or VCD? I will investigate it more tomorrow as my brain is wiped out.

I look forward to your instructions and further exchange of ideas. I am like you though, once I find out something is not working I just go nuts until I solve the problem.  good day

---

### Post by 4ebees on 2007-01-18
Okay,

I really should have posted this to numerous forums - very slack on my behalf.

The solution is this:

In Digikam, when you select the images you want to make a video slide-show out of, as you know, you choose:

tools > create mpeg slideshow.

At the top (see attached screen shot) right hand side, there is a collection of video options, starting with "Video format, type and chroma mode". It is the latter you need to change. Change this to:

420mpeg2

This should now allow you to make mpeg slideshows (which are very cool) :)

Hope this helps.

Kino can make SVCD and VCD files. Let me know how you go with that - I've only made DVDs.

Get back to me either way; I'd really like to know how you go.

Regards,

Patrick 



> **granny4linux said:**
> Patrick, thank you so much for some great ideas. I did not know kino would do this; can it make an SVCD or VCD? I will investigate it more tomorrow as my brain is wiped out.

I look forward to your instructions and further exchange of ideas. I am like you though, once I find out something is not working I just go nuts until I solve the problem.  good day

---

### Post by granny4linux on 2007-01-18
> **4ebees said:**
> Okay,

I really should have posted this to numerous forums - very slack on my behalf.

The solution is this:

In Digikam, when you select the images you want to make a video slide-show out of, as you know, you choose:

tools > create mpeg slideshow.

At the top (see attached screen shot) right hand side, there is a collection of video options, starting with "Video format, type and chroma mode". It is the latter you need to change. Change this to:

420mpeg2

This should now allow you to make mpeg slideshows (which are very cool) :)



Patrick

O.K. Patrick, I really appreciate your help. When I create an Mpeg slideshow in Digikam I do not get the dropdown menu box that is displayed on your screenshot.

I am a bit baffled, I've checked all through the settings and I can't seem to find a place to enable it. (See attached screenshot) What version of Digikam are you using? I am using it in Ubuntu Dapper 6.06, I noticed you use Kubuntu, could that make a difference?

I will check into Kino and let you know how that goes.

Thanks again for taking the time to help me out.

Good day,
Suzy

---

### Post by 4ebees on 2007-01-18
Hi Suzy,
(quick post - breakie, kids and work are all calling :))

Check your setup against mine:

I'm using Digikam 0.8.2-rc1 in Dapper.

kipi-plugins                  0.1.1-3~ach0dapper1

mjpegtools                    1.8.0-0.0ubuntu1

then get back to me.

Regards,

Patrick


> **granny4linux said:**
> O.K. Patrick, I really appreciate your help. When I create an Mpeg slideshow in Digikam I do not get the dropdown menu box that is displayed on your screenshot.

I am a bit baffled, I've checked all through the settings and I can't seem to find a place to enable it. (See attached screenshot) What version of Digikam are you using? I am using it in Ubuntu Dapper 6.06, I noticed you use Kubuntu, could that make a difference?

I will check into Kino and let you know how that goes.

Thanks again for taking the time to help me out.

Good day,
Suzy

---

### Post by granny4linux on 2007-01-18
Hi Patrick:

 I really appreciate you taking the time to help me with this; it sounds like you have a lot going on!!!

This is what I'm using:

digikam  0.8.2~rc1-0ubuntu3

kipi-plugins 0.1+rc1-1ubuntu2

mjpegtools 1.8.0-0. 0ubuntu1

I've also tried it with digikam 9.0 and  kipi-plugins 1.3-rc1 and I get the same error and no way to choose "420 mpeg2"

Good day,

Suzy

---

### Post by 4ebees on 2007-01-19
Weird.

Okay,

Let's start from the beginning :)

I'd uninstall Digikam and the kipi-plugins etc.

Check the attached images. It has my install list of packages. Install them using Synaptic - I'm pretty sure mine is just a standard install.

It may well be that it's the kipi-plugin that's not working properly.

See if installing what I've got listed makes a difference.

Regards,

Patrick







> **granny4linux said:**
> Hi Patrick:

 I really appreciate you taking the time to help me with this; it sounds like you have a lot going on!!!

This is what I'm using:

digikam  0.8.2~rc1-0ubuntu3

kipi-plugins 0.1+rc1-1ubuntu2

mjpegtools 1.8.0-0. 0ubuntu1

I've also tried it with digikam 9.0 and  kipi-plugins 1.3-rc1 and I get the same error and no way to choose "420 mpeg2"

Good day,

Suzy

---

### Post by granny4linux on 2007-01-19
Hi Patrick:

I've re-installed the programs as you suggested. I noticed that our kipi-plugins are different; could it be my sources list? I've attached a copy.

I've also attached screenshots from my current Synaptic setup.

Thanks for your determination to help me get this fixed.

Good day,

Suzy
[ATTACH]23446[/ATTACH]

[ATTACH]23447[/ATTACH]

[ATTACH]23448[/ATTACH]

---

### Post by tanman on 2007-01-19
As I was reading this thread I never realized that Digikam had this feature. Anyway I tried it and it seems to work OK, but is there a way to add more than just one song. I was working on a friends pictures from a wedding, but the slide show is much longer than song. I looked at Kino, but not sure if I understand how everything works yet.

---

### Post by 4ebees on 2007-01-20
Hiya tanman,

I'd suggest timing the show you want to make, then taking the sound file you want to use and editing it (with Audacity - the perfect application for this) to match the length. You can certainly make the sound file longer by adding a second song or repeating a bit of the original.

Regards,

Patrick 


> **tanman said:**
> As I was reading this thread I never realized that Digikam had this feature. Anyway I tried it and it seems to work OK, but is there a way to add more than just one song. I was working on a friends pictures from a wedding, but the slide show is much longer than song. I looked at Kino, but not sure if I understand how everything works yet.

---

### Post by 4ebees on 2007-01-20
Hokely dokely,

I'd try one of the following:

[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)

and download the newest versions.

or

PM me and we can work out how to get the version I've used. I found my .deb, which means I must have downloaded and updated it - I have a feeling that I did this, which would explain why my version is newer than the one in the repos).

See how you go.

Also, attached is my repo list.

NB. For some reason I'm not getting e-mail updates about posts to this thread...dunno why, so I'm having to come and check to see what's happened. If I go 'quiet' :) just e-mail me directly.

Regards,

Patrick

PS. No probs with helping out... God knows I've sought enough help myself!!!!!!!







> **granny4linux said:**
> Hi Patrick:

I've re-installed the programs as you suggested. I noticed that our kipi-plugins are different; could it be my sources list? I've attached a copy.

I've also attached screenshots from my current Synaptic setup.

Thanks for your determination to help me get this fixed.

Good day,

Suzy
[ATTACH]23446[/ATTACH]

[ATTACH]23447[/ATTACH]

[ATTACH]23448[/ATTACH]

---

### Post by granny4linux on 2007-01-20
Success!!! Thanks Patrick for your dedication in helping me solve this problem.

In order to install kipi-plugins 1.3-rc1.1  I had to remove libkipi0, libkipi-dev libkipiexif1, exiv1, digikam8.2 and digikamimageplugins 8.0. 

I compiled in this order:
 libkipi 1.5			[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)		
 libkexif 2.5			[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)	
 exviv2			[http://www.exiv2.org/download.html](http://www.exiv2.org/download.html)					
 * libgpod4.0 		[http://sourceforge.net/project/showfiles.php?](http://sourceforge.net/project/showfiles.php?)				group_id=67873			
 kipi-plugins 1.3 		[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)

*(to use kipi plug-in to export to ipod) 

To install digikam 9.0 and digikamimageplugins 9.0 available at
[http://sourceforge.net/project/showfiles.php?group_id=42641](http://sourceforge.net/project/showfiles.php?group_id=42641)

sudo apt-get install build-essential
sudo apt-get build-dep digikam
(found this post helpful:
[http://kubuntuforums.net/forums/index.php?topic=12047.0](http://kubuntuforums.net/forums/index.php?topic=12047.0))

then I compiled both packages

Then I made myself a little test slideshow with mp3 file and it worked like a charm. Choosing Chroma Mode 420mpeg2 option.

I am sorry for such a wordy post and I hope I didn't leave anything out; but if someone else experiences this problem I hope this will help them resolve it.  So Patrick...you da man!!!

Good day,
Suzy

---

### Post by tanman on 2007-01-20
It is great to hear that you have it working. When I have some more time I will play around with Audacity and see how I can either make a lope or add more songs.

---

### Post by granny4linux on 2007-01-20
tanman, I've used Audacity successfully; if I can do it, I know you can too.

---

### Post by 4ebees on 2007-01-21
> **tanman said:**
> It is great to hear that you have it working. When I have some more time I will play around with Audacity and see how I can either make a lope or add more songs.

Hi Tanman.

I'd suggest you make a separate post and then PM me and I'll get back to you on the new thread :)

That way you can get the benefit of your own thread and other will be able to see the issue in the header.

Regards,

Patrick

---

### Post by 4ebees on 2007-01-21
Hey Nan :)

Good to see you got it working =D> 

Well done.

Now, another thing I'd like to mention is 'checkinstall'. 

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

It's a great package and it's in the repos (like so many other things when using Debian/Ubuntu)

When you're compiling something, first you:

./configure

Then:

make

Then:

checkinstall

It automatically creates a package specifically for your distros, so in this instance it creates a .deb for you to keep!...urm, and then install (silly me).

The beauty of this is:

1. it appears in Synaptic as an installed package.
2. can be uninstalled with Synaptic or the CLI using dpkg

I was often concerned about trying to find the bits-and-bots to remove when uninstalling a  package that was compiled from source on my machine, and then I read about this app.

My other favourite is: 

alien

this is in the repos to

This converts packages like an .rpm to a .deb - brilliant!

> **granny4linux said:**
> Success!!! Thanks Patrick for your dedication in helping me solve this problem.

Well, I'm very glad it's worked out for you Nan.

Again, well done.

I don't believe there's a problem with long descriptions of "how I did it". The more detailed the better for anyone else coming along. It's really just part of how you give something back to the community :))

Regards,

Patrick



In order to install kipi-plugins 1.3-rc1.1  I had to remove libkipi0, libkipi-dev libkipiexif1, exiv1, digikam8.2 and digikamimageplugins 8.0. 

I compiled in this order:
 libkipi 1.5			[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)		
 libkexif 2.5			[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)	
 exviv2			[http://www.exiv2.org/download.html](http://www.exiv2.org/download.html)					
 * libgpod4.0 		[http://sourceforge.net/project/showfiles.php?](http://sourceforge.net/project/showfiles.php?)				group_id=67873			
 kipi-plugins 1.3 		[http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/)

*(to use kipi plug-in to export to ipod) 

To install digikam 9.0 and digikamimageplugins 9.0 available at
[http://sourceforge.net/project/showfiles.php?group_id=42641](http://sourceforge.net/project/showfiles.php?group_id=42641)

sudo apt-get install build-essential
sudo apt-get build-dep digikam
(found this post helpful:
[http://kubuntuforums.net/forums/index.php?topic=12047.0](http://kubuntuforums.net/forums/index.php?topic=12047.0))

then I compiled both packages

Then I made myself a little test slideshow with mp3 file and it worked like a charm. Choosing Chroma Mode 420mpeg2 option.

I am sorry for such a wordy post and I hope I didn't leave anything out; but if someone else experiences this problem I hope this will help them resolve it.  So Patrick...you da man!!!

Good day,
Suzy

---

### Post by granny4linux on 2007-01-21
> **4ebees said:**
> 


Now, another thing I'd like to mention is 'checkinstall'. 

My other favourite is: 

alien

this is in the repos to

This converts packages like an .rpm to a .deb - brilliant!

Hi Patrick,

One of the benefits of problem solving is all that one learns in the process. I actually stumbled across "checkinstall" and used it for this project. I'm glad you mentioned it because I'd never heard of it before and others may benefit as well..

Alien...that's a new one for me and I will definitely check it out. Thanks for mentioning it. There is a fle I want to install for my Ipod but it was only available as an RPM.

One last thing; I'd originally thought the problem I was having with ManDvd was related to Mpegtools. After googling myself silly I found a suggestion to install the latest version of dvd-slideshow and it worked like a charm. (see screenshot) ManDvd is a really sweet program; I like it so much that I ordered a DVD burner yesterday so I can burn my slieshow to a dvd rather than an SVCD.  Good day, Suzy

app.[ATTACH]23594[/ATTACH]

---

### Post by doundounba on 2007-01-21
Hi guys...  Bit late to the party, but I just wanted to mention (since I just ran into this as well) that the original issue ("Could'nt read YUV4MPEG header") appears to be a known bug on Dapper, and there's an easier fix than manually compiling and installing a handful of stuff.  See this bug entry: [https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787]("https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787").  The fix, as per the patch attached to the bug description, is to change a single line in the file /usr/bin/images2mpg to add the switch "-S 420mpeg2" when ppmtoy4m is invoked.  This fix worked for me.  YMMV, of course.  Hope this might help someone.

---

### Post by 4ebees on 2007-01-22
Hey doundounba,

That's great. I fiddled with this for ages... I think my located solution came before this one was put up (but I could be wrong). I looked for ages for a solution.

This is so much easier. 

Thanks very much for that.

Regards,

Patrick

> **doundounba said:**
> Hi guys...  Bit late to the party, but I just wanted to mention (since I just ran into this as well) that the original issue ("Could'nt read YUV4MPEG header") appears to be a known bug on Dapper, and there's an easier fix than manually compiling and installing a handful of stuff.  See this bug entry: [https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787]("https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787").  The fix, as per the patch attached to the bug description, is to change a single line in the file /usr/bin/images2mpg to add the switch "-S 420mpeg2" when ppmtoy4m is invoked.  This fix worked for me.  YMMV, of course.  Hope this might help someone.

---

### Post by granny4linux on 2007-01-22
> **doundounba said:**
> Hi guys...  Bit late to the party, but I just wanted to mention (since I just ran into this as well) that the original issue ("Could'nt read YUV4MPEG header") appears to be a known bug on Dapper, and there's an easier fix than manually compiling and installing a handful of stuff.  See this bug entry: [https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787]("https://launchpad.net/ubuntu/+source/kipi-plugins/+bug/48787").  The fix, as per the patch attached to the bug description, is to change a single line in the file /usr/bin/images2mpg to add the switch "-S 420mpeg2" when ppmtoy4m is invoked.  This fix worked for me.  YMMV, of course.  Hope this might help someone.

Thanks doundounba, I will keep this for reference and the next person will have an easy time fixing the problem.

---

### Post by benrboone on 2008-04-16
When I tried to make a video from my pictures, I had to install mpg123 through synaptic.  It work after that.
(using hardy beta)

---

