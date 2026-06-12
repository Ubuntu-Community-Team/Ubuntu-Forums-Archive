---
title: "Movie Player won't run my dvd"
date: 2010-09-06
forum: Multimedia Software
---

### Post by mike0liver on 2010-09-06
I have recently installed Ubuntu 10.04, and am trying to play a DVD on my Toshiba Notebook NB100. Movie Player says it cannot find the plugins suitable to play the DVD. I have gone through procedures recommended on numerous forums to get the codecs and libdvd packages installed but I still get a notice telling me MP doesn't have the plugins.
 
Can anyone point me in the right direction, or take me through the correct procedure please? I am non-technical :-)
 
Cheers,
 
Mike

---

### Post by howefield on 2010-09-06
Have you gone through the procedure on this page ?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)


Try installing VLC, there won't be much that this application won't play.

---

### Post by mike0liver on 2010-09-06
Yes, that contains details of one of the procedures I went through but it didn't solve the problem. I'm going to check out the other installation you suggest and I'll report back - thanks for the suggestions.
 
Mike

---

### Post by mike0liver on 2010-09-06
I tried installing VLC but got the following error message: "**Package dependencies cannot be resolved. **This error could be caused by additional software packages which are missing or not installable. Alternatively, there could be a conflict between software packages which are not allowed to be installed at the same time"
 
This doesn't seem to me to be a particularly useful message. It doesn't indicate which of the possibilities is responsible (if any) nor what to do about it.
 
Is this something that is known about or is it specific to me?
 
I'm going to check on the internet to see if I can learn anything but I am now back at the start - can you offer any further help, please?
 
Mike

---

### Post by mike0liver on 2010-09-06
I have visited the VLC website and found the following information:
[SIZE=4]Ubuntu Lucid Lynx 10.04 LTS[/SIZE]
**VLC version 1.0.6 in Ubuntu 10.04 is out-of-date.** We recommend you install VLC 1.1.x manually. If you wish to install VLC 1.0.6 anyway, please refer to the instructions above for Ubuntu 10.10. Note that there will be some bugs; you are on your own.
 
I don't have Ubuntu 10.10 and my update manager has not shown it as available yet.
 
There are no instruction on how to install VLS manually. Are you able to tell me what to do on the basis of this information, please?
 
Thanks,
 
Mike

---

### Post by cchhrriiss121212 on 2010-09-06
Where did you try to install VLC from? You do not need the latest version either, 1.0.6 is fine.
Try opening synaptic package manager and check you have the following installed:
vlc
libdvdread4
libdvdnav4
libdvdcss2

---

### Post by sir_robert007 on 2010-09-06
Here's what I did to get DVD playback working on my system:

First open Synaptic Package Manager and install Ubuntu-restricted-extras. Then open up a terminal and execute the following:

sudo /usr/share/doc/libdvdread4/install-css.sh

Make sure any media players you have open are closed or you may get errors.

---

### Post by mas_sergio on 2010-09-06
_**i know you said you've gone through EVERY forum**_ but I don't know what to refer you to other than this becuase this is what got DVD playback working for me it's the **recommended** tutorial for multimedia playback and much more.

check it bro you have to do some reading to get to dvd section or use ctrl F in firefox and search dvd until you get what your looking for but theres ALOT of good stuff in there that you really shouldn't over look like codecs, disabling mouse while typing(via terminal), and much other great stuff you should really look at blah blah here's the link... my dvd won't play give me the link and shut up i know i know..

Enabling DVD playback for
Distribution: ALL VARIANTS

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Follow Directions and everything should work. You need an internet Connection for this EXCELLENT tutorial to work.

Enjoy your Movies ;)

:popcorn:

[I]Recommendations:
Please in VLC enable BLEND in the right click menu(look for it i forgot in wich category it's in) while a video is playing (if thats what your going to use for DVD playback)... that should smooth out most artifacts that you WILL get during playback.[/I]

---

### Post by mike0liver on 2010-09-08
I'm sure I haven't been to _every_ forum but, as I said, I have visited numerous and followed any instructions that seemed relevant. It's quite likely I did't find and install everything I needed. However, the link you've provided looks pretty comprehensive and I'm logged into it on my Notebook so I can cut & paste relevant input for a terminal.
 
Just to be sure, shouild I do this with every item that looks relevant or are there some I should avoid?
 
One further thing, not exactly related, but when I install new software, there doesn't appear to be anywhere to call itt from (like the .exe file icons or START menu in Windows). What's the correct way to call an application in Ubuntu?
 
Thanks for your assistance on the Movie Player question.
 
Mike

---

### Post by mike0liver on 2010-09-08
Sir_Robert007 wrote: 
"First open Synaptic Package Manager and install Ubuntu-restricted-extras. Then open up a terminal and execute the following:

sudo /usr/share/doc/libdvdread4/install-css.sh

Make sure any media players you have open are closed or you may get errors."
 
This was one of the things I did on my trip around the various forums but it didn't seem to do the trick :sad: 
 
Mike

---

### Post by mike0liver on 2010-09-08
> **cchhrriiss121212 said:**
> Where did you try to install VLC from? You do not need the latest version either, 1.0.6 is fine.
Try opening synaptic package manager and check you have the following installed:
vlc
libdvdread4
libdvdnav4
libdvdcss2
 
I installed from the VLC website, which is where I got the message shown in my earlier posting (9813753). The only thing I don't recall doing is installing libdvdnav4 anywhere. Where should this file be located - I'll have a look and see if it's there?
 
Cheers,
 
Mike

---

### Post by howefield on 2010-09-08
> **mike0liver said:**
> This was one of the things I did on my trip around the various forums but it didn't seem to do the trick

Just a random thought, is this just the one awkward DVD you have, or is it all DVDs that don't play.

---

### Post by cchhrriiss121212 on 2010-09-08
> **mike0liver said:**
> I installed from the VLC website, which is where I got the message shown in my earlier posting (9813753). The only thing I don't recall doing is installing libdvdnav4 anywhere. Where should this file be located - I'll have a look and see if it's there?
 
Cheers,
 
Mike
When using Ubuntu you should not (generally speaking) install things separately from websites, what you have is a repository system that is regularly updated with all the software you need. This is so you do not get conflicting software and do not have to look around for supporting libraries etc.
You can check all installed libraries, programs and everything else using synaptic package manager in your system menu.

---

### Post by sir_robert007 on 2010-09-08
You can also try adding the Medibuntu Repository and then try installing libdvdread4, libdvdnav4 and libdvdcss2 from Synaptic.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This is the community documentation for adding and installing software from the Medibuntu repository. Hope this helps.

---

### Post by mike0liver on 2010-09-09
> **howefield said:**
> Just a random thought, is this just the one awkward DVD you have, or is it all DVDs that don't play.
 
I have tried two more commercial DVD's and one that was provided by a friend who has copied it from a commercial one. I am not sure of the legal position with the copy so have not tried playing it before.
 
My system did not recognise the presence of the two commercial DVD's in my drive but has picked up the copy. However, I still get exactly the same problems when I try to play it as I did at the outset.
 
I'd like to say here how grateful I am for all the help I'm receiving - it is much appreciated.
 
Cheers,
 
Mike

---

### Post by mike0liver on 2010-09-09
> **cchhrriiss121212 said:**
> When using Ubuntu you should not (generally speaking) install things separately from websites, what you have is a repository system that is regularly updated with all the software you need. This is so you do not get conflicting software and do not have to look around for supporting libraries etc.
You can check all installed libraries, programs and everything else using synaptic package manager in your system menu.
 
Thanks, Chris. My main problem is that I am completely unfamiliar with Linux having only used it intermittently over the past year for fairly basic computing needs (e.g. internet access, writing quick documents and storing photographs). This is the first time I've had to address more complex issues and I really don't know what I'm doing.
 
My recollection is that I was directed to the VLC website on one of the forums I visited. I think I may have to get an idiot's-guide-to-Ubuntu book and spend some time boning up on the whole thing (when I get the time ;)). Generally, when help gets technical, I have problems understanding what I'm being told.
 
Whatever the history, I still have no solution to my problem and must now hope for something to be posted here that will take me forward.
 
Cheers,
 
Mike

---

### Post by mike0liver on 2010-09-09
> **sir_robert007 said:**
> You can also try adding the Medibuntu Repository and then try installing libdvdread4, libdvdnav4 and libdvdcss2 from Synaptic.
 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
This is the community documentation for adding and installing software from the Medibuntu repository. Hope this helps.
 
I have the Medibuntu Repository installed and am hoping someone can tell me where to look to check that libdvdnav4 is installed so that I can confirm I have it.
 
I'm really floundering here and getting just a touch frustrated :( However, I'll check out the Medibuntu link you've provided and see what help I can get there - thanks.
 
Cheers,
 
Mike

---

### Post by mike0liver on 2010-09-09
I have successfully installed VLC from my Ubuntu Software Centre and it will happily play the copy DVD I mentioned but none of the commercial ones I've so far tried. I will try a few more before I give up.
 
Maybe I need to obtain some software that will copy the commercial DVD's and allow me to play them via VLC?
 
This seems to be a potentially satisfactory result if only I can get VLC to run commercial DVD's.
 
If everyone feels I have got as far as they can take me, I'd like to say "thank you" to you all. The support has been excellent.
 
Cheers,
 
Mike
 
_Later_: I have now managed to get several commercial DVDs to run in VLC - I think I'm there - thanks, guys!

---

### Post by qz9090 on 2010-12-03
Mike,
I followed the commands at the link below and was able to play commercial DVDs on 10.04 .

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

When I did this it told me that "libdvdread4" was installed already and it set the software for manual installation, so I continued with the second set of commands and was able to get Movie Player to play my DVDs. 

For me, the commercial DVDs play but they are choppy, hopefully, you will have better luck.

---

### Post by j_keiter on 2010-12-05
Mike I'm having the same problems.  I think you can verify the install of libdvdnav4 by clicking System then Administration then Synaptic Package Manager then type libdvdnav4 in the search field.  Make sure the check box is colered in.  Mine was installed but still have the problems you have.  Like you I've been installing codecs, medibuntu, turning of compositor etc.  Still not working for Monsters Inc and other store bought movies on Ubuntu 10.10.

---

### Post by j_keiter on 2010-12-05
Oh cra@!.  I may have some other problem.  Movie player cannot run a simple .avi file on my hardrive.  I have sound but no video???  Ubuntu 10.10.  I'm baffled!

---

### Post by j_keiter on 2010-12-05
Both SMPlayer and VLC play audio but no video on movie DVD Monsters Inc.  Youtube works great in firefox.

---

