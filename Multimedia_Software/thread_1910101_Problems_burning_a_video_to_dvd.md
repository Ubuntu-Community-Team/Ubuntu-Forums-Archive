---
title: "Problems burning a video to dvd"
date: 2012-01-16
forum: Multimedia Software
---

### Post by jockyburns on 2012-01-16
Hi I have tried burning a video to dvd using Brasero. 
 
When using Brasero it asks what sort of dvd I'm creating and I select create scvd/dvd. A window opens when I select burn telling me that all libraries are not installed. Please manually install mplex (GStreamer codecs) These are installed on my computer as the software centre tells me they are installed and so can't go any further with this. Anyone tell me what on earth I'm doing wrong??

---

### Post by cotcot on 2012-01-16
Your question is not very clear. (not clear what your source file is for instance)
Maybe a couple of things that might help you further. 
When I make a dvd I use [[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html") to make an iso to burn to the dvd with brasero. Devede is in the repositories.
Check if you have installed the gstreamer plugins 'ugly'.
If you start brasero from terminal you will probably get more precise error messages.

---

### Post by jockyburns on 2012-01-16
Ahh thanks for the reply. I'm trying to use DeVeDe to create the ISO file (I've installed all available GStreamer files too) Just tried again (2, 1/2 hr video Grrrr) right near the end when DeVeDe is creating the dvd tree structure, it gets to 99% and closes with an error message (some thing like, "unable to complete, maybe you ran out of disk space") Have tried several times now but this error I'm getting at 99% is frustrating me. 
Is there any other program out there I could try? Getting bloody fed up with DeVeDe. 
Cheers

PS I've only been using Ubuntu for about 6 months so starting a program from the terminal is really beyond me. Even if I could, any error messages would be above my level of expertise (or lack of it)

---

### Post by SeijiSensei on 2012-01-16
> **jockyburns said:**
> Just tried again (2, 1/2 hr video Grrrr) right near the end when DeVeDe is creating the dvd tree structure, it gets to 99% and closes with an error message (some thing like, "unable to complete, maybe you ran out of disk space")

Well, then, you probably are running out of space.  I wouldn't try encoding a DVD without at least 10 GB free.  The amount of space needed will depend on the bitrate and encoding method you chose along with the length of the program material.  I wouldn't be surprised to learn that DeVeDe also creates some rather large temporary files along the way.

Here's one option.  Open a Terminal in one window, then run DeVeDe in another.  While it's running, type the simple command "df" into the terminal from time to time to see how much disk space is still available.

---

### Post by jockyburns on 2012-01-16
Just ran GParted to see how much space I have on my HDD. 123.6GB unused. Surely more than enough to meet the demands of a dvd? HDD only has Ubuntu as an OS and with what I have on the HDD only 26 GB used. So I can't see it running out of space anytime soon. 
I wouldn't even know how to start devede in a terminal so that's way over my head.

Output of "df"

john@john-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152813668  23867372 121183764  17% /
none                    501216       704    500512   1% /dev
none                    507844       628    507216   1% /dev/shm
none                    507844        92    507752   1% /var/run
none                    507844         0    507844   0% /var/lock


I've just almost completed running DeVeDe. When it's creating the DVD Tree Structure, it get's to around 98-99% then the error message comes up. "Failed to create the DVD Tree Structure. Maybe you ran out of disc space"

If someone can explain to me , how a video of around 700Mb can use 120+GB of space,,, I'm all ears. 

IS there another program out there in the repo's for creating a DVD from a video on my HDD without all of this hassle? Recommendations gratefully received.

---

### Post by SeijiSensei on 2012-01-16
I did a quick search for the text of your error on Google (always a good starting point) and found [this link](http://www.rastersoft.com/programas/devede.html).  Apparently it was a bug in DeVeDe that's been resolved in the 12/31/2011 release.  You can try upgrading to this version by downloading [this .deb file]("http://www.rastersoft.com/descargas/devede_3.21.0-1~rastersoft1_all.deb"), then running "sudo dpkg -i /path/to/devede_3.21.0-1~rastersoft1_all.deb".

---

### Post by wolfen69 on 2012-01-16
To start any program via terminal, simply type the name of it.
```
devede
```
will start it. Not as hard as you thought, huh?

---

### Post by wolfen69 on 2012-01-16
> **SeijiSensei said:**
> I did a quick search for the text of your error on Google (always a good starting point) and found [this link](http://www.rastersoft.com/programas/devede.html).  Apparently it was a bug in DeVeDe that's been resolved in the 12/31/2011 release.  You can try upgrading to this version by downloading [this .deb file]("http://www.rastersoft.com/descargas/devede_3.21.0-1~rastersoft1_all.deb"), then running "sudo dpkg -i /path/to/devede_3.21.0-1~rastersoft1_all.deb".

But since the OP is a beginner, simply clicking on the .deb file will suffice.

---

### Post by jockyburns on 2012-01-17
Thanks Wolfen and Sensei for the useful links. I have tried the deb file, but get a new problem with dependecies not met ffmpeg> 4.1.72 (or something similar) I've had a look round some forums and am now completely baffled as to how to proceed (running 11.04 here) So I'm going to call it a day with DeVeDe.
 Just now need to know if there's another program out there that will create the ISO file for me. Short of putting my video on a usb stick and taking it to someone using Windoze, I'm now stumped.:confused::confused::confused:

---

### Post by tersogar on 2012-01-17
Pleased tell us if the video is mkv, mp4 ect.

---

### Post by jockyburns on 2012-01-17
The video source is .avi. When running DeVeDe, to create the ISO file it's converting it to an Mpeg format and saving it in a folder. When it reports the error about disc space  I exit the program and the folder and Mpeg of the video is there. I can't burn this to disc as it's not an ISO file (already tried)
I've looked on the internet for a solution and it seems an updated  file, (ffmpeg) is needed for DeVeDe to complete the process, but there's nothing in the repo's or anywhere else for me to download this file from. 

All I need now is an alternative program to create the ISO file so I can burn that to disc. Any help or pointers in the right direction would be very much appreciated.

---

### Post by jockyburns on 2012-01-17
Quick update folks, I've managed to install the updated ffmpeg files from the creators website Crikey who'd have thought working in the terminal was so hard?
Had to open a terminal and type in "Sudo add-apt repository ppa:jon-severinsson/ffmpeg". 
Let that download and do it's thing then "sudo apt-get update ". 
Let that blaze away. 
Finally I re-opened the deb file Sensei linked to earlier and Voila. Instead of getting the "dependencies not met message" It has allowed me to upgrade DeVeDe. 
I'm trying it now and will report back in a few hours with a hopeful success. 
If it is successful I'll mark the thread as solved and would like to say a big thanks to all who responded with very useful advice. 
I'd also like to thank my dog, who came perilously close to being shouted at , when things kept going wrong (bless him) :):)

---

### Post by jockyburns on 2012-01-17
I've successfully burned my first video on Ubuntu using DeVeDe to create the ISO file. Many thanks to all who helped. 
Cheers lads. ;););)

---

