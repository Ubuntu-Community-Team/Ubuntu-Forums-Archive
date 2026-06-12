---
title: "Yes it is a Sound problem"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by expatCM on 2007-07-11
SB Audigy LS.  Partially working.  Matrix module CA0106. 

So XMMS works.  MP3's can be played from the HDD.  Audacity can record from a mic and play back.

What does not work is the System Sounds and Skype.  Skype reports that "Call Failed: Problem with Audio Playback"   Quite what that message means is not clear since the Default Device is selected in the Options and I have tried all of the other items which all are referenced CA0106.

System / Preferences / Sound Preferences has three headings Sound Events, Music and Movies and Audio Conferencing. Each has a test button.  The button plays a tone for each item.

So what can I do next?

---

### Post by kvonb on 2007-07-18
Have a look through this thread, also there is a new version of Skype which I downloaded from their site, maybe give that a try :).


[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

EDIT:  I also had the problem with Skype not recording from my mic.  This thread below solved that.  Seems you have to enable the "Capture" feature in the mixer, then select it, see post #6:

[http://ubuntuforums.org/showthread.php?t=451586&highlight=record+sound+mic](http://ubuntuforums.org/showthread.php?t=451586&highlight=record+sound+mic)

---

### Post by expatCM on 2007-07-18
Thanks for your interest.  I downloaded the new version of Skype some time ago.  Actually I find it not to be too good ....   it has some strange events and also it does not appear possible to start Skype minimized, you always need manual intervention to send it to the system tray.  Best not to be too critical though since it is a beta and no doubt some of the lumps will be ironed out shortly ......

The link you mentioned is well known to me ...  indeed the content was updated and appears here - 
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by kvonb on 2007-07-18
Oh well, I tried :(

Do you also have an onboard sound card?  I got around my problems by using the onboard for Skype, and my SB live for everything else.

After enabling "capture" on both mixers, I was able to select the correct source.

---

### Post by expatCM on 2007-07-18
.....  please do not misunderstand ... it really is appreciated that you have given your suggestions.  Others will read them and be very happy that you have made them.  There seems to be a BIG problem with sound support  in Ubuntu which is not addressed. The whole area is something of a black art and the help you get is either minimal or best guess.   The blame should fall on the sound card manufacturers who are very reluctant to release proper information about their cards.  I guess if you protect your information you can also protect your pricing levels.

But there does seem to be a big need for a very complete guide to sound and how to fix it.   I have read so many sound related threads to realize that working sound is just as important as having working video.

Sorry for the rant but that is the way it is (from my perspective).


Yes, I do have on-board sound but it is defective so what I am thinking of doing is changing the motherboard and then either not bothering with the Creative card or ...   do as you suggest and mix both cards according to the need :)   By then I also hope to have worked out why I cannot save the alsamixer settings ....  now that should not be an issue but ... guess what .... it is.....

---

