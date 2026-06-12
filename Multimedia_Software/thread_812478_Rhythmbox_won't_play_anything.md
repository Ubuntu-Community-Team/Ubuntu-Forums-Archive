---
title: "Rhythmbox won't play anything"
date: 2008-05-29
forum: Multimedia Software
---

### Post by chuyler1 on 2008-05-29
I keep seeing the following message when I run Rhythmbox from the command-line:

$ rhythmbox
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing


I went to add/remove applications and added just about everything that pops up when I search for gstreamer but it still ain't working.  Any help would be appreciated!

EDIT,

So apparently the errors I see occur when Rhythmbox trys to import encrypted songs I purchased on iTunes.  I turned off the auto-detect new files in my library and now I don't see any errors.  I select a song (mp3 format) and it says it is playing but the counter never goes up and I don't hear any sound.  Sound works fine from my web browser so I'm confused as to what is going on.  There are no errors, nothing.  Rhythmbox won't even play songs off a CD in my CD-ROM drive!

---

### Post by ameseisch on 2008-06-19
Just so you know you are not alone. I am having the same problem where rhythmbox wont play files or CD's.

what happens is it just never plays. i don't think its a sound issue or codec issue. it selects the file, and in other ways acts like it is playing but the time doesn't advance or anything. very odd.

---

### Post by Pjotr123 on 2008-06-19
Apply this how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will take care of 100 % multimedia support.  :-)

---

### Post by ameseisch on 2008-06-19
Thanks, those are good resources for getting multimedia going. I will point people to those in the future. I already had all the codecs installed, but I did go ahead and install VLC and Audacious since I hadn't bothered to yet on this machine. Audacious plays files just fine. However, for some reason Rythmbox is still broke. It did change though. it now says not playing and moves through the files trying to play the next one in the list.

this seems to be a rythmbox specific issue for me. i suspected from the beginning that it wasn't a codec issue because it won't play .ogg files that i burn from a cd.

---

### Post by chuyler1 on 2008-06-19
My problem was also Rhythmbox specific.  I finally gave up.  I'm using Amarok instead and although its not perfect, it actually works and the interface is a little more robust.

---

### Post by WamBamBoozle on 2009-03-15
I got rhythmbox and others to work again by

sudo /etc/init.d/pulseaudio restart

Why pulse audio should be breaking things now is a mystery.

---

### Post by Heavenly Evil on 2009-04-24
> **WamBamBoozle said:**
> I got rhythmbox and others to work again by

sudo /etc/init.d/pulseaudio restart

Why pulse audio should be breaking things now is a mystery.

Thank you for this! It works now.

ETA: It only worked for me temporarily. My permanent fix was to go into the sound preferences and change everything from pulseaudio to alsa. I haven't had any problems since.

---

### Post by Tholley on 2009-06-05
I had the same problem also, after deleting the itunes files amd clearing the error msgs.
 
I was using Amarok 2, and it played everything, but I like the layout of Rythmbox better.
I'll try this when I get home and see if it works!

---

### Post by Tholley on 2009-06-05
> **Heavenly Evil said:**
>  
ETA: It only worked for me temporarily. My permanent fix was to go into the sound preferences and change everything from pulseaudio to alsa. I haven't had any problems since.
 
Ok... Good thing I checked back!

---

### Post by Tholley on 2009-06-05
Well, none of that is working for me. I was playing rhythmbox and it was playing ok, then hung up on a song. I then couldn't get any songs to play.  I could not even close rhythmbox. I rebooted and tried all the above and once I tried to open rhythmbox, it would not even open, it shows up at the top right like it is running, but nothing is happening and once again I cannot get it to close. I right click on the icon, and click quit... nothing, it still shows to be playing a song which it is not. 

All my music will play on amarok, but I like rb better if it would only play.

---

### Post by JFazenda on 2009-06-06
Thanks Pjotr [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

It took ages to download all the stuff missing in my installation, but ...
Rythmbox works fine now.
________________________________________________

> **Pjotr123 said:**
> Apply this how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will take care of 100 % multimedia support.  :-)

---

