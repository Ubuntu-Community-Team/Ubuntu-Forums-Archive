---
title: "Help installing Logitech Music Anywhere?"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by sookoon on 2007-06-11
Hello, all. 

I need help / instructions on how to install Logitech Music Anywhere

I'm using Feisty on a Latitude D620, and don't know where to start

---

### Post by tedemang on 2007-09-14
I'd like to ask about this also, since I moved my PC away from my stereo.

Ubuntu Feisty and Gutsy do detect it quite well, from looking at the Hardware Information app anyway.

Has anyone else tried the Logitech Music Anywhere USB/Bluetooth Wireless?

---

### Post by Rumo on 2007-10-12
Yeah, I just bought it and it works great! So here's how to do it:

1) The remote should work out of the box - just connect the usb-adapter to the remote station (press the connect button) and you should be able to skip between songs in amarok or almost any other music player...

2) The easiest way to setup the wireless music part is actually quite well explained in the amarok manual (under 'alsa' the 'usb-audio' part). So here's what you need to do:

create .asoundrc in your home directory (~/,asoundrc) or alternatively /etc/asoundrc with the following content:

```
pcm.intel8x0 {
    type plug
    slave.pcm "hw:0"
}
ctl.intel8x0 {
    type hw
    card 0
}
pcm.usb-audio {
    type plug
    slave.pcm "hw:1"
}
ctl.usb-audio {
    type hw
    card 1
}
```
Btw, you probably only need the usb-audio-lines. Now open amarok and change 'Outplug plugin' (->'Settings' ->'Engine') from 'auto' to 'alsa'. Then enter 'usb-audio' as the stereo device. Now everything should work fine.

This should work with any other player - at least if it allows to manually change the audio device (so no rhythmbox afaik).

---

### Post by drjson on 2007-10-14
I have this working with MPD using a similar method to the above post.  At first I would get no sound output even though it was defined, but after creating the asound.conf file, things began working for me.  Now I just need to figure out a way to bind the remote keys.

I have a slightly different setup in that I was planning on just sticking this computer off in some adjacent room to my stereo since I was using it as a fileserver anyway.  Then I figured I could use it as a audio player for my music collection with the Music Anywhere system since I didn't like using it on my main desktop.  So I got it all setup with MPD/Pitchfork/icecast/samba/scrobbling/etc, but about the only thing I can't figure out is how to get those remote keys bound to a command.  

The usb-hid device shows up and is listed under /dev/input/event2 for me.  And I've tried to use just about every suggestion on [on this page](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Finding_raw_scan_codes_-_USB_keyboards) for finding a scan code and somehow binding it.  But the problem is that I just did a LAMP server install and am uncertain if it'd even be possible to do an 'arbitrary' bind to a command even with X, without having an interactive x session.  I know the event is getting to the OS because I can wake up the terminal by pushing a button on the remote, but I just need to find a way to hook onto it.

running cat /dev/input/event2 in a terminal and then pushing buttons definitely spits out some information, just not sure how to get that to do what I need it to do.

---

### Post by drjson on 2007-10-14
sigh... just when you think you've tried everything and ask for help, you go back to the beginning and find your answer.

I was able to use the utility listed on the MPD website and get the remote to work with MPD now.  Utility in question is [empcd](http://unfix.org/projects/empcd/).  Problem solved.

---

### Post by trginter on 2007-10-24
I still can't get the Logitech Wireless Music system to work.  Any ideas?

---

### Post by drjson on 2007-10-25
What player are you using?  

First thing you can do is make sure the card is listed when you do:
sudo asoundconfig list

---

### Post by angelsneverdie on 2007-12-13
alright, i'm using amarok and followed your instructions (i think) and can't get it to work.  first of all, do i just copy the code you provided and save it as assoundrc.conf?  sorry, i'm very much still learning.  when i make the changes to amarok in the settings, the player grays out for a long time and then i finally get this message: Audio output unavailable; the device is busy.
xine parameters: 

note that there is nothing after "xine parameters:"

i'm running gutsy

any ideas what i'm doing wrong?

---

### Post by angelsneverdie on 2007-12-14
I've just tried again, and now it doesn't grey out like it did before, it just runs through the playlist track names (quickly, without playing) and then gives me the error. . . i don't know if this sheds any light on the situation.

---

### Post by angelsneverdie on 2007-12-15
i've been reading many forums trying to figure this out and still no luck.. does anyone have any ideas?  hate to think i just spent the money on this thing and won't be able to use it with ubuntu!

---

### Post by badlydrawn on 2008-01-17
For amarok i found the easiest way to get it working is to insert plughw:Tra as the stereo output device. Hope this helps.

---

