---
title: "Headphone &amp; Speaker Issue"
date: 2008-05-24
forum: Multimedia Software
---

### Post by davidkyn on 2008-05-24
Headphone & Speaker Issue:
Fronts still playing while Headphones plugged in!

Hi,
I've just re-installed Ubuntu 8.04, as my last attempts to FIX a common Headphone & speaker issue failed resulting in No Sound at all. It would seem that those of us with an Intel HDA sound card(Many Note Books) suffer with their front speakers NOT mutting when plugging in their Headphones.........................All I have done thus far to this OS is simply Updated thgouh Update Manager & nothing else!

I located a solved thread on this:
[http://ubuntuforums.org/showthread.php?t=740702](http://ubuntuforums.org/showthread.php?t=740702)
Seems simple enough to fix, so I visited the recommended site:
[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)
It says from there to go here:
[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
were I downloaded the said script...right clicked to make executable coppied it to the home folder and used his command line to run it from the terminal. So Far So Good.....after the script installed a Heap of stuff & restarted system automatically... I still have sound...that is at least something...Now I will try to test it further with Headphones!

I opened up the default music player which wanted me to install 2XGStreamer Pluggins...So I just highlighted the boxes clicked next and watched it install. ARGHHHH I dont believe it...errors already...I tried going through synaptic Packager as well but after getting more erros I finially realised it helps to make sure your connection to the internet is working when downloading....anyways, after srumbling over my own feet there I installed the Gstreamer codecs and Low & Behold I can play the mp3............

Sound Still comes out front speakers when Headphones plugged in....AARRGGHH.

OK.....it says I should do the following after installng the update:
 In you /etc/modprobe.d/alsa-base add the following line.
options snd-hda-intel probe_mask=8 model=lenovo
save and exit
reboot the machine and when you insert headphones the speakers will mute

I THINK THIS IS WERE I STUFFED UP LAST TIME AND LOST MY SOUND...ONLY BECAUSE I DID NOT KNOW HOW TO DO THIS.

Ok.....I will do this by:
sudo gedit /etc/modprobe.d/alsa-base

when the window opens I will save as first to back it up!

Ok I added the new line & saved + exit the terminal and restarted..tested system and still have the same problem with sound coming out both speakers and headphones!!

Oh well.........I did solve this problem in suse10.3 by some how changing the Kimx controll panel to allow for “switching” the headphones on & off...........after updating Alsa in Ubuntu I still have a rather Dosy looking sound controll with no options like that......???????

I think I need it to at least recognise that I have suround sound ability like it did after updating is SUSE10.3.................I want Ubuntu though....

Please I will follow anything you tell me...as long as you can spell it out that is...

Anyone??????.........what can I do:confused:

---

### Post by davidkyn on 2008-05-24
Am I suppose to configure the sound some how...?

---

### Post by smarks on 2008-05-24
yes just go to system + pref + sound and in there you can tell it where u want the sound to come out of.

---

### Post by davidkyn on 2008-05-24
Nar...just like when disabling or enabling through edit through the Master Intel (Alsa Mixer) Volume Control.......does nothing to change the problem....Mute speakers mutes headphones mute headphone mutes speakers and so forth including master as well.......

Thanks dude...can Anyone elaborate??

---

### Post by smarks on 2008-05-24
just so i understand, You went to the preferences and under the tabs you selected your headset like how mine says USB Audio like in this pic.

[http://img205.imageshack.us/my.php?image=screenshotly2.png](http://img205.imageshack.us/my.php?image=screenshotly2.png)

---

### Post by davidkyn on 2008-05-24
yea, I found that.........as a newbiew to Ubuntu and the whole linux thing I would need a little more guiding as to what I am supose to do with all those tabs and the many option within each..........

No use messing with things I dont understand...

I was more like talking about the Master Intel (Alsa Mixer) Volume Control (icon on top of desktop) before.

as for where you advised me to go.......I messed around some but to no avial as I have no idea what to do there.....????

Here is current set-up...Very Dosy looking...anyways when I mute "Fronts" Headphone mutes too & when I mute Headphone Fronts stop too? Ive tried changing all the combinations with the cinfig to the left but still same thing happens..........please refer to second screen shot!
[IMG]http://i181.photobucket.com/albums/x30/davekyn/SoundTest.png[/IMG]

[SIZE="4"][COLOR="black"][COLOR="Red"]*Note...[/COLOR][/COLOR][/SIZE]on the right side of volume controll I used file to changed the device to Realtech ALC 888... and now I dont have a headphone volume to mute??
[IMG]http://i181.photobucket.com/albums/x30/davekyn/soundtesttwo.png[/IMG]

---

### Post by davidkyn on 2008-05-25
It just does not make sense?????????Sound still comming out of speakers...why oh why
[IMG]http://i181.photobucket.com/albums/x30/davekyn/test3.png[/IMG]

---

### Post by davidkyn on 2008-05-25
[SIZE="5"]SOLVED...............it pays to keep talking to yourself:)[/SIZE]
find fix at:
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

