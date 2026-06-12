---
title: "Logitech Z-10 display"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by aliyanage on 2007-03-11
Hi all,

I just bought myself some Logitech Z-10 speakers and saw that when playing music over amarok first of all it doesn't recognize the usb connection meaning it doest play the music over the speakers when using usb, where as the normal cable works fine.

Also once I would get the usb thing working... I've heard that there are issues with displaying song tracks on the logitech display... did anyone already make  any experiences with this? Or does someone already have a solution?

thanks for your help in advance
aliyanage

---

### Post by haopeng on 2007-07-20
i got the same problem. no sound when playing mp3 in xmms or gxine. But I can control the volumn of the z10 speaker through volumn controller. And in system->preference->sound, it shows that z10 speaker is detected and I clicked on "sound test " it played "beep" sound for me. Is there anyone have this working?

---

### Post by haopeng on 2007-07-21
finally the speaker works for me using USB connection! it's ubuntu does not set USB speaker as default sound device. just set the default sound card like this 

# get <card-name> for your usb sound card
$ asoundconf list
# set defaul sound card
$ asoundconf set-default-card <card-name>.

Just follow this thread
[http://ubuntuforums.org/showthread.php?p=3014683](http://ubuntuforums.org/showthread.php?p=3014683)

Also found some threads about g15daemon to enable LCD display which said to be working for z10 as well.
[http://forums.logitech.com/rss/message?board.id=stereo_20&message.id=429](http://forums.logitech.com/rss/message?board.id=stereo_20&message.id=429)


And I followed this thread to install all packages required for g15daemon 
[http://ubuntuforums.org/showthread.php?t=267118&page=29](http://ubuntuforums.org/showthread.php?t=267118&page=29)

And the LCD displayed the time for me now. yay!or me using USB connection! it's ubuntu does not set USB speaker as default sound device. just set the default sound card like this

# get <card-name> for your usb sound card
$ asoundconf list
# set defaul sound card
$ asoundconf set-default-card 

Looks like there's also plugins for xmms to display song names in LCD which I found here, I'll have a try and see how it goes
[http://sourceforge.net/project/showfiles.php?group_id=172261](http://sourceforge.net/project/showfiles.php?group_id=172261)

---

