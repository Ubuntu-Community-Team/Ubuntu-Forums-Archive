---
title: "Skipping Sound With Flash In Firefox + ALSA"
date: 2009-04-14
forum: Multimedia Software
---

### Post by HotDogBunToo on 2009-04-14
Grew tired of the issues of PulseAudio so I ran back to ALSA sound - however I was reminded of an annoyance in ALSA that I couldn't shake which is sound in Flash content skipping. I'm in Intrepid and had upgraded to Flash Player 10 but prob continues on.

Now it doesn't start off like this, I watch a few videos in Veoh, Hulu or Youtube and I'm good like gravy on potatoes.  However give it a few hours and the dreaded stuttering sound ensues when I try to play a video.  Fortunately restarting Firefox cures this ailment but it gets pretty annoying when I have several tabs open and I don't feel like having to restart & come back around to opening them all (nor do I like abruptly closing & reopening so all tabs come back up since that takes awhile).  

For a bunch of reasons Pulseaudio isn't an option even though this issue didn't occur when using that (for a ton of other reasons), so I'm pretty much wondering what's needed to get done to resolve this while using ALSA.  I installed afew packages and no luck so any help would be greatly appreciated!  ^_^

---

### Post by HotDogBunToo on 2009-04-16
C'mon... anybody?

---

### Post by HotDogBunToo on 2009-05-24
*sigh* 

Bumping again,

Searched on Google for this issue and this same topic comes up anyway lmao.

But yea... this issue is getting annoying.  Is there at least a way to at least restart flash itself without giving Firefox the pkill treatment?

---

### Post by 18th_bronzeman on 2009-06-04
Your thread is the only thread I have found on this.  I am having this EXACT same problem.  I actually can't get away with just restarting firefox. Maybe I am missing a step?  I actually have to restart the window manager.

I am tempted to install another browser to see if it is a firefox + flash issue or just a flash + ubuntu issue.  The only other thing I can think of is some type of memory leak?  Maybe I should run top in a terminal window.

Anway, keep the faith.  You are not alone!

---

### Post by nsh on 2009-12-26
i had this problem too, and i seem (fingers crossed) to have chased it away. try this:

$ sudo apt-get remove adobe-flashplugin 
$ sudo apt-get install flashplugin-nonfree

---

### Post by jensoko on 2009-12-28
I've had the same problem since I think Feisty.  I didn't know it was flash, and it happens only when I unplug my laptop and plug it back in again somewhere else.  The way I have to get around it is 

quit firefox

$ ps -ef 

(kill any firefox processes that may still be running)

$ sudo /etc/init.d/alsa-utils restart

restart firefox

It's a persistent and irritating little problem, and I keep hoping new firefox iterations will correct it.  But the fix is simple so it's not a deal-breaker.  Just annoying.

---

