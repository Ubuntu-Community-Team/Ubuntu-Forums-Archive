---
title: "Transformers 2 plays in VLC, but not in XBMC, Boxee, Totem"
date: 2010-03-03
forum: Multimedia Software
---

### Post by yebo29 on 2010-03-03
I am attempting to build my media center based on Ubuntu. Currently, I am testing between XBMC and Boxee.

I recently rented Transformers 2 for the first time, and popped it into the drive, and fired up xbmc. Xbmc saw the disk, and started the player - but no picture or sound. It plays for about 5 seconds and then returns me to the main screen.

Boxee exhibits the same exact behavior.

Totem states that it's missing plugins - but no link, no button to search for new plugins - and no workie for Transformers 2.

BUUUT: VLC will play it just fine! 

I have already installed libdvdread4 and ran the install-css.sh script successfully.

---

### Post by Yellow Pasque on 2010-03-03
> Totem states that it's missing plugins
Start Totem from the terminal. Maybe it will tell you what plugin. In general, you can get missing plugins for Totem with:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by yebo29 on 2010-03-03
Temüjin:

Thanks for your assistance!! :)

OK, I started Totem through the command-line and began playing the dvd, but no output.

I then went ahead and installed the plugins you mentioned and Totem now plays the DVD perfectly!

BUUUUT:........ XBMC and Boxee still can not play the DVD. :( 

Let me know what else I could do to troubleshoot, such as running XBMC and Boxee through CLI and posting that, or maybe I just need to logout or restart??

Just to clarify, BTW: I mentioned that Totem didn't give me any links when it stated that it had missing plugins, but it actually does give a link to a page talking about installing some plugins and more, albeit the ones you mentioned. Sorry I missed that!

---

### Post by yebo29 on 2010-03-04
I have attached boxee's log file as well as the output of dmesg.

---

### Post by Yellow Pasque on 2010-03-04
The program is segfaulting. NOt much you can do there, except try another version or report it to the developers.

---

### Post by yebo29 on 2010-03-04
Hm. What does it mean when a program "segfaults"?

And why does it happen to xbmc as well? And why only Transformers 2? 

Don't worry, Temüjin, not expecting a response to the above two questions. Just "thinking out loud"....

But I'm kinda thinking it has something to do with the encryption used on the DVD. Something that XBMC and Boxee have yet to implement, as they share the same code base, no?

---

### Post by mc4man on 2010-03-04
> But I'm kinda thinking it has something to do with the encryption used on the DVD
Not exactly the encryption but the structure protection used on the disk. 
Trans2 used a fairly decent sp scheme that it appears is causing XBMC, Boxee, ect. to try and play one or more of the bogus, intentionally borked titlesets. 

(IIRC the 'real' movie was on title 47, most of the other titles were essentially garbage, and would make for an apparent disc size that is quite impossible for dvd's - 40+GB

---

### Post by yebo29 on 2010-03-05
Ah-ha! I see. Yeah, just navigated the DVD in boxee and was able to play the other VOB's. But, as boxee is still Beta, it plays for like a second and then freezes. Then it starts again but with static, and freezes..
Tis' the nature of beta. 

Thanks for clearing that up, mc4man. I'm going to go ahead and mark this thread [SOLVED]. I'll look into reporting that segfault to the devs.

Thanks everyone for their help!

---

