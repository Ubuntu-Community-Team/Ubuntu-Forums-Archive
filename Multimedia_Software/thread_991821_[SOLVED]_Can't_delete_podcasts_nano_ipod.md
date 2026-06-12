---
title: "[SOLVED] Can't delete podcasts nano ipod"
date: 2008-11-24
forum: Multimedia Software
---

### Post by Rodney9 on 2008-11-24
Hello. I can not delete podcasts from my nano ipod. 

gpodder says it has , but does nothing and gtkpod ghives the followinf error -

Could not remove the following file: '/media/Rodney’s iPod/iPod_Control/Music/F00/gtkpod516162.mp3'

Error opening /media/Rodney’s iPod/iPod_Control/Artwork/F1031_1.ithmb: Read-only file system
Error opening /media/Rodney’s iPod/iPod_Control/Artwork/F1027_1.ithmb: Read-only file system
Opening of '/media/Rodney’s iPod/iPod_Control/iTunes/iTunesDB' for writing failed (Read-only file system).

Please Help me delete some podcasts so I can listen to something new.

---

### Post by Rodney9 on 2008-11-24
Please Help

---

### Post by Rodney9 on 2008-11-25
Anyone ?

---

### Post by Rodney9 on 2008-11-25
gPodder copys to my iPod , fills it up, says it is deleting the old , but does not, than says no more room !

Amarok will not even look at the iPod, even when I show the mount.

Gtkpod see it, says it is deleting, but nothing happens.

So now I have a $300 iPod and can't use it......HELP

---

### Post by Rodney9 on 2008-11-25
> **Rodney9 said:**
> gPodder copys to my iPod , fills it up, says it is deleting the old , but does not, than says no more room !

Amarok will not even look at the iPod, even when I show the mount.

Gtkpod see it, says it is deleting, but nothing happens.

So now I have a $300 iPod and can't use it......HELP
 
I have tried Banshee as well, it also says it has deleted files, but does not.

What does work ? I can't listen to the same podcasts over and over :mad:

---

### Post by williamson389 on 2008-11-26
essentially the same thing is happening to me, sooo hopefully one of us will get some help.  the comprhensive sound walkthrough says to just manually delete the Itunes_locked  file under itunes>itunes control.
for me it doesnt change anything and keeps reapearing. it is especially bothering me because i had previously had my ipod workinng no problem in amarok, but then upgraded to 64-bit because i bought more ram.#-o

PM me if you figure it out.

---

### Post by DirtDawg on 2008-11-26
I have no definitive answers for you, but thought I would throw some ideas out there since you seem to be pretty stuck.

Have you tried using iTunes on a Windows partition yet? I ask because I wonder if the problem could be with the hard drive or formatting of your ipod, rather than the software. 

You may also try using 'sudo' to remove the files in question. For example:
```
sudo rm /media/"Rodney&#8217;s iPod"/iPod_Control/Music/F00/gtkpod516162.mp3
```
It will probably not work, and it's generally not recommended as standard practice if it does, but it may provide a more relevant error message.

And looking at the command, I also see the name of the iPod is "Rodney's iPod." I'm wondering if the apostrophe in the name of the iPod may interfere with commands. Note in the command above I wrapped the iPod name in quotes.

If you have a first generation Nano, as I do, I would use [Rockbox]("http://www.rockbox.org/"), as I do :D If you have a newer generation, however, I have read there are many compatibility issues where Linux is concerned. Your problems may stem from such issues.

---

### Post by Rodney9 on 2008-11-26
Hello, My iPod Nano is a 1st gen, so I tried to format to fat32 so I could use Rockbox.

I followed the instuctions here -

[http://www.rockbox.org/tw...ain/IpodConversionToFAT32](http://www.rockbox.org/tw...ain/IpodConversionToFAT32)

however I get the following error

$ sudo mformat -t 2428 -h 255 -s 63 -S 4 -M 2048 -F a:
mformat: Can't open /dev/sdd3s2: No such file or directory

doesn't matter if it is mounted or unmounted.

even though mount shows - /dev/sdd3 on /media/Rodney&#8217;s iPod type hfsplus (rw,nosuid,nodev,uhelper=hal)

What can I do ? I do not have windows or mac only Ubuntu 64bit 8.10

Should I use /media/Rodney&#8217;s iPod instead of /dev/sdd3
if so, do I put the /etc/mtools.conf in drive a: file="/media/Rodney&#8217;s iPods2"

Rodney.

---

### Post by DirtDawg on 2008-11-27
> **Rodney9 said:**
> Hello, My iPod Nano is a 1st gen, so I tried to format to fat32 so I could use Rockbox.

I followed the instuctions here -

[http://www.rockbox.org/tw...ain/IpodConversionToFAT32](http://www.rockbox.org/tw...ain/IpodConversionToFAT32)

however I get the following error

$ sudo mformat -t 2428 -h 255 -s 63 -S 4 -M 2048 -F a:
mformat: Can't open /dev/sdd3s2: No such file or directory

doesn't matter if it is mounted or unmounted.

even though mount shows - /dev/sdd3 on /media/Rodney&#8217;s iPod type hfsplus (rw,nosuid,nodev,uhelper=hal)

What can I do ? I do not have windows or mac only Ubuntu 64bit 8.10

Should I use /media/Rodney&#8217;s iPod instead of /dev/sdd3
if so, do I put the /etc/mtools.conf in drive a: file="/media/Rodney&#8217;s iPods2"

Rodney.
Please be cautious reformatting. Unfortunately, the link you provided doesn't work. I looked for it on the rockbox site, but cannot find it. I have always reformatted from Windows, so I am not familiar with the process on Ubuntu, but if I could look at the same instructions, I think I can help.

With Rockbox, you will not need a special interface like iTunes or gtkpod to transfer music. You simply transfer the files from the iPod to the computer as you would any other files.

EDIT: I just want to mention, if you have a friend or family member who runs Windows and has iTunes, and who would allow you to use their computer, reformatting is very simple. There's a Restore button under the Summary tab in iTunes that will do the trick. Then you can plug the reformatted iPod back into your Linux box and run the Rockbox installer. In other words, if you have the access, use it.

---

### Post by Rodney9 on 2008-11-28
> With Rockbox, you will not need a special interface like iTunes or gtkpod to transfer music. You simply transfer the files from the iPod to the computer as you would any other files.

Well I got Rockbox installed but I can not copy files or create folders. If I right click on the desktop icon and select properties it says under Permissions " The Permissions of "RODNEYSIPOD" could not be dertimed "

I did try ~$ sudo chown $USER:$USER /media/RODNEYSIPOD
$ sudo chmod -R 750 /media/RODNEYSIPOD
from the hints [http://ubuntuforums.org/showthread.php?t=982560](http://ubuntuforums.org/showthread.php?t=982560)

But still can not copy.

What is going on ?

---

### Post by DirtDawg on 2008-11-28
> **Rodney9 said:**
> Well I got Rockbox installed but I can not copy files or create folders. If I right click on the desktop icon and select properties it says under Permissions " The Permissions of "RODNEYSIPOD" could not be dertimed "

I did try ~$ sudo chown $USER:$USER /media/RODNEYSIPOD
$ sudo chmod -R 750 /media/RODNEYSIPOD
from the hints [http://ubuntuforums.org/showthread.php?t=982560](http://ubuntuforums.org/showthread.php?t=982560)

But still can not copy.

What is going on ?
Hey, sorry i can't help today. I don't have any experience with your situation, but I will try to look at these things tomorrow. Nice work getting Rockbox installed. If we can figure out this permissions problem, you'll find it enhances your Nano greatly. Sorry things aren't running as smoothly as you'd like.

Quickly, I looked up "ubuntu permission could not be determined" in google and found a few links. [Here's one]("http://ge.ubuntuforums.com/showthread.php?t=820744") about permissions on an external HD, not sure it applies to your situation. Like I said I'll try to look again tomorrow. Good luck.

---

### Post by Rodney9 on 2008-11-29
Thanks for your help.

It is awfully strange though, today I plugged it in , it auto mounted and let me copy a folder to it, but when I tried a second file it said "Error opening file '/media/RODNEYSIPOD/cabbiev2.cfg': Read-only file system" 
I tried unmounted and unplugging then plugging back in , auto mount, but still would not let me copy.

When I use $ sudo chown -R $rodney. /media/RODNEYSIPOD

I get many, many lines saying similar to this one -

chown: changing group of `/media/RODNEYSIPOD': Read-only 
file system

but does not fix my problem.

Am I correct in thinking this "Read-only file system" is my problem.

Rodney.

---

### Post by Rodney9 on 2008-11-29
> Originally Posted by vanadium View Post
Before proceeding with anything else, you need to check the file system. In MS Windows, you would have used the venerable "chkdsk a: /f", in linux there is the dosfsck program that allows to check and repair fat volumes. Only continue troubleshooting after you have made sure that the file system is healthy.from vanadium [http://ubuntuforums.org/showthread.php?p=6276824#post6276824](http://ubuntuforums.org/showthread.php?p=6276824#post6276824) Post No.6

I used - dosfsck -a /dev/sdd2 

and now it is worked perfectly.

Thankyou Everybody for your ideas and help.

Rodney

---

### Post by DirtDawg on 2008-11-30
Excellent! Congratulations and nice work. I was just coming in to check on things and start looking for solutions. Please mark this thread as [SOLVED] using the option in 'Thread tools' on the upper right.

I think you'll find Rockbox enhances your Nano quite a bit. I'll give you some unsolicited ideas here. To play all your music (lets assume all your music is in a folder called 'Music'), click and hold down the select button while the Music folder is highlighted and choose one of the 'enter folder as playlist' options. This will queue up all the songs in your Music folder. This may sound obvious, but it took me awhile to figure out :D I use this as a replacement for Apples 'play all' and prefer this method over messing with the Database feature.

The other thing is you can now play movies/film on your nano. The trick is the video needs to be an mpeg, and it needs to be converted to a very specific size to play. I have worked out a way to convert video to work specifically for the Nano. First, you must install mencoder, if you haven't already. You may also need ffmpeg. I cannot remember, but if you have installed all the codecs for internet and movie viewing, you likely already have it.
```
sudo apt-get install mencoder
```
Then, run this command and replace "/path/to/your/old_video.extention" and "/path/to/your/new_video.mpeg" with the appropriate paths.
```
mencoder "/path/to/your/old_video.extension/" -o "/path/to/your/new_video.mpeg" -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=100 -vf scale,harddup -ofps 25 -zoom -xy 176
```
Note this command is for converting different file types (ie: .avi files) into mpegs as well as reformatting existing mpegs for playing on your Nano. If you find the quality of the new video is too small, replace the value after "vbitrate=100" to a higher number than 100. Just remember the higher that number, the larger the final filesize will be.

Lastly, you can now help improve your battery life by dimming the backlight. Adjust through "Settings> GeneralSettings> Display> LCDSettings> Brightness". I usually keep mine between 4 and 6. Why Apple didn't include this kind of functionality is beyond me. I suspect it was to drive people to their more expensive models.

Okay, enough unsolicited blathering. I'm just trying to make up for the fact that I didn't know how to fix your original problem :D Really though, if you have any more questions about Rockbox on the Nano, don't hesitate to private message me. I've been working with Rockbox on Nano for about 2 years now and, although the initial transition can take getting used to, the payoffs are huge.

And again, nice work. You're obviously a very self-reliant person :KS

---

