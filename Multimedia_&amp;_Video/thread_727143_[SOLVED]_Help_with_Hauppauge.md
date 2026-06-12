---
title: "[SOLVED] Help with Hauppauge"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by Zeotronic on 2008-03-17
Just today, I received my Hauppauge card... its a WinTV-PVR 150 (I think...) I am trying to get it to work with TVTime, and I have to admit that I have no idea how to... I assume I have to get some drivers somewhere, and I assume the fact that I don't have them is the reason why its not working? Anyways my searches of the posts on the forum haven't helped me, so I have to ask for help in this manner.

---

### Post by Firestone on 2008-03-17
The Hauppauge cards use the [IVTV](http://ivtvdriver.org/index.php/Howto:Ubuntu) driver, but it's already included. The PVR series are hardware encoders though, and most tv viewing tools can't process that. I don't know if TVTime supports it, but I use VLC(with a PVR-250) in combo with a playlist for my viewing needs. At least you can try that your card works that way. Just start VLC, open the PVR tab and enter the frequency of a channel.

---

### Post by Zeotronic on 2008-03-17
> The Hauppauge cards use the IVTV driver, but it's already included. The PVR series are hardware encoders though, and most tv viewing tools can't process that. I don't know if TVTime supports it, but I use VLC(with a PVR-250) in combo with a playlist for my viewing needs. At least you can try that your card works that way. Just start VLC, open the PVR tab and enter the frequency of a channel.
I didn't know VLC could do that... it truly is incredibly versatile... I've messed with it, and it displays what I would expect it to for the different inputs (composite, s-video, and tuner) but I have yet to make it display anything that I'm pumping into it... I cant seem to find it... perhaps you have more information of use?

Edit:
Ok, I have composite working...

---

### Post by wolfen69 on 2008-03-17
I have a Hauppauge pvr150 card running on my gutsy box, and I get live tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool GUI desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

as far as i know, hauppauge wont work with tvtime. you can record the channel you are on by (open another terminal first) cat /dev/video0 > /tmp/name_of_video.mpg

type ctrl-c to stop recording.

---

### Post by Zeotronic on 2008-03-27
> for a cool GUI desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)
As it turns out, I have an *actual* remote, for use with the computer... I don't suppose you (or anyone else) would know how I can use that?
> I have a Hauppauge pvr150 card running on my gutsy box, and I get live tv by: (...)
Wait, do you mean *live live* or just input? Because I now know how to get input, but I notice there to be a second (or so) of delay... I had figured that since my card was hardware encoded this was impossible to get around... ... ... or do all tv cards do that regardless of encoding?

---

### Post by wolfen69 on 2008-03-27
by live tv i mean regular tv viewing. there may be a 1 sec. delay compared to a tv set.
> 
As it turns out, I have an actual remote, for use with the computer... I don't suppose you (or anyone else) would know how I can use that?
actual remotes work with mythbuntu, but not sure how to get it going with ivtv-utils.  check the ivtv forums.

---

### Post by saedelaere on 2008-04-23
Hi,

you could also try to use [this one]("http://ubuntuforums.org/showthread.php?t=763698")
If your remote control is installed properly you can use it with the program.

Regards

---

