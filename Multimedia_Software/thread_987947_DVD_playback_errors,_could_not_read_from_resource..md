---
title: "DVD playback errors, could not read from resource..."
date: 2008-11-20
forum: Multimedia Software
---

### Post by jonmark1985 on 2008-11-20
Hello my name is Jon.  I just started using Ubuntu this summer and I'm very pleased.  I am having a few issues and I haven't had any luck resolving them by myself.  They are probably very easy to fix, but I just can't seem to get it.

When I try to watch a DVD on my computer I get a window that says "Could not read from resource".

I'm using a Lite-On DVD-ROM/CD-RW IDE drive.  My mother board is Intel's D945GCLF.  I'm using Ubuntu 8.10 i386 also.

I can browse the contents on the DVD and the drive works flawlessly for any other task.

Here is the screen shot...
[IMG]http://i294.photobucket.com/albums/mm88/jon354/couldnotread.jpg[/IMG]

Here is the link to my motherboard's page
[http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm)

Please be patient as I'm very new and uneducated with Ubuntu.  Thanks for your time.

---

### Post by jonmark1985 on 2008-11-21
Can I get a bump?

---

### Post by mc4man on 2008-11-21
What version of ubuntu are you using? (8.10 - intrepid, 8.04 - hardy, 7.10 - gutsy

Do you know how to use the terminal?

Has your dvd drive ever played commercial dvds in windows?

Forget using totem movie player for dvd discs, the gstreamer version isn't well suited for good playback. (totem-gstreamer is what's installed by default in ubuntu.

---

### Post by jonmark1985 on 2008-11-21
I'm using 8.10 i386.  I also can run 64 bit, but I'm having troubles with getting connected to the internet, so at the moment I'm just running 32 bit.

I've used the terminal before, but when doing so I had to pretty much be guided through it.

I've never used windows on this computer, but I have used this drive in other computers that were running Knoppix and Xandros and got the DVD player to work.

What program do you recommend for watching DVDs?

Thank you for your reply!

---

### Post by mc4man on 2008-11-21
First to make a distinction between 2 things, there is enabling dvd playback which in most cases is pretty much trivial. Then is is quality of playback, ie. do you have sound and video, and if so are there any quality of such issues.
They are 2 separate things and need to be addressed that way.

Open up a terminal and run these commands one at a time. (copy and paste, then press enter, let the command run it's course and then do the next one

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

After that completes

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

(note: sometimes medibuntu is down, it there's any hangup in above commands wait a bit and rerun 

Then

```
sudo apt-get install libdvdcss2 vlc totem-xine libxine1-ffmpeg
```

This will give you the lib for decrypting the movies (libdvdcss2, a good player (vlc) and a totem player that works (totem-xine) and a lib that it needs (libxine1-ffmpeg and some various libs vlc needs for playback

After that is done you'll have 2 choices for playback, vlc and totem-xine.

The best thing to do now is have both set as a choice for default player (autorun upon dvd insertion.
When available as a choice you'll also be able to right click on the dvd icon -> 'open with' and pick your player from the list.

So right click on the Applications menu in upper panel -> edit menus.
On the left side highlight Preferences, on the right side ck. the box for File Management to enable it.

Close out edit menus and in upper panel click System -> Preferences -> file management -> media.

Expand the drop down for Dvd Video. Vlc should be listed, Movie Player (Xine) won't be.
Click on the 'open with other application' (blue diamond)

In the add application list look for 'Movie player (Xine)', highlight it and click add. (not 'Movie Player' or Movie Player (gstreamer')

Note :if you don't see it in list (it should be there) go one step further -> 'use a custom command' and just type in totem-xine

Movie Player (Xine) should now be set as default 'DVd Video' player (or in the unlikely event you had to type in a custom command it will say totem-xine, - same thing

I'd go ahead and put a dvd in and see what happens. (hopefully good things

If all is well you can also try vlc (either set as default in file management media or just r. click on the dvd icon -> open with and pick vlc

If movies play but there are 'quality' issues post what's happening.

If they don't play post that and we'll look for the reason why

Note: while not always needed, usually it's best if a dvd drive is set to a region, in your case region 1. No need to address now, if playback fails after doing above stuff then it's the first thing to ck.

---

### Post by jonmark1985 on 2008-11-21
Many thanks!

I now can watch DVD's and the quality is great!

---

### Post by zeifertstc on 2008-12-02
Thank you from me as well. This worked where so many others have failed. My system is probably full of crap now and I'll have to clean it out. Thank you for posting a working solution here, I appreciate it muchly.

---

### Post by violettoulli on 2009-01-03
thanks, it worked for me too.
i am new to ubuntu, and it is all like chinese to me here, so it feels like miracles when i can sort out my problems with instructions from these forums!!

thanks again,
vio x

---

### Post by The Big Chow Mein on 2009-01-22
H mc4man, thanks for the run through. Ive been having trouble with DVD playback and after going through your walk through i get this error message from xine:

'The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?'

This may be a very simple problem to solve but i don't have much experience with Linux.

Any help would be much appreciated.

(specs: AMD athlon 5000+, 8600GT, 3.2Gb ram, Philips DVD-ROM DROM6316)


UPDATE: after (for curiosities sake) taking the dvd out and putting into the second drive i have found it works fine through the second drive! Any idea why?

---

### Post by polytropos on 2009-01-23
Thanks to mc4man for the post above--that little guide worked great.  I can watch DVDs now.

---

### Post by nonsub on 2009-01-24
To mc4man.

Many thanks for the instructions above. They worked for me too!

Regards
Paul

---

### Post by victorcrane on 2009-01-29
Mc4man, many thanks for the guide, works perfectly. This has been driving me mad for months and finally i can watch dvds on the laptop again. 

Great stuff. 

:)

---

