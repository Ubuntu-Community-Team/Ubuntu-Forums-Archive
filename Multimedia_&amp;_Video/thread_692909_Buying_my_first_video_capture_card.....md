---
title: "Buying my first video capture card...."
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by arsenic23 on 2008-02-10
Alright, I've never been interested in any form of video capture before, but right now I'm designing my new PC and have begun to develope a need for a good capture card.  I've done alot of reading on the subject of video capture and editing in linux over the last couple days, so I think I'm starting to get a vague idea as to what I need.  Unfortunatley alot of the things I'm reading are skipping over details that are important to me and talking about things I just couldn't care about.  Also alot of the best writen data seems to be a little out of date.  So I'm hoping some of you guys and gals out there with decent experience capturing video in linux could share your experience with a few things.

Here's what I want too do (in order of importance):
**1**.)  I want to be able to flawlessly capture my old 80's cartoon VHS tapes.  Perferably I'd like to capture them too .dv files to compress after the fact.  I'm more then likely going to be saving them as ogg or mp4 files in the end.

**2**.) I'd like to be able to do the same with analog TV signals.  It whouldn't bother me if I had to run this through a box or VCR first to turn it into component or Svideo.

**3**.) I'd like to be able to capture in HD, but not nessisarily from the TV. ( cameras and stuff )

**4**.) I may want to use MythTV sometime in the not foreseeable future.

**5**.) I may want to view HDtv sometime in the unforeseeable future.

**6**.) I'm not oposed to buying a non-HD card now and purchasing one later and using it as a second card.


The first thing I noticed when I started looking for linux capture card reviews and opinions, was that alot of people seemed to recomend cards with Philips chipsets.  I particularly saw quite a few people claiming that the Philips SAA7130 was THE card.  Unfortunatlely alot of this information was a little old.

I also saw alot of people saying great things about the HD5500 from [http://pchdtv.com/](http://pchdtv.com/) .  Unfortunately all they wanted to talk about was using it for HDtv, so I'm not too sure it would be terribly usefull to me since 99% of what I'm going to be doing, at least at first, is not going to be HD.

So, any help, pointers, sugestions, or experience you all could share would be terribly appriciated.

---

### Post by Thingymebob on 2008-03-03
Don't want to hijack your thread, but I'm in the same position and it looks like it may need a bump. I'm also needing to capture some old VHS stuff and am looking for something suitable. I'll be using a laptop so ideally this needs to be a USB device. I've managed to work out that just about everything for sale on Ebay is not going to work. I'm currently looking at the terratec grabster usb and the hauppage usb live devices if I can find a UK seller of them. Has anyone had any succes with either of these devices.

---

### Post by eldragon on 2008-03-03
for analogue tv, ive used the saa 7130 with no problems at all, only deal is that you have to run the audio signal throught your line in. ive had 2 of these, one old flyvideo 2000 which worked great, when it died, i bought a pinnacle pctv 10 expecting to have similar or even better quality. this was not the case. there is a small lag between channel change, and quality isnt as good.

they usually come with composite and svideo, cable in, 

for HD cameras, i dont think you will need a capture card, since most come with a digital link to a pc (firewire??)

if HDtv is what you need, i cannot help :(

---

### Post by arsenic23 on 2008-03-18
There is a terrible lack of information on this subject.

I just noticed that when searching google for "purchasing a video capture card for linux", this thread is the 8th result.

---

### Post by ToySouljah on 2008-03-19
> **arsenic23 said:**
> There is a terrible lack of information on this subject.

I just noticed that when searching google for "purchasing a video capture card for linux", this thread is the 8th result.

lol...it's number one now.  I'm looking for the same info  :)

---

### Post by xzero1 on 2008-03-19
[http://linuxtv.org/v4lwiki/index.php/Main_Page]("http://linuxtv.org/v4lwiki/index.php/Main_Page")

---

### Post by arsenic23 on 2008-03-20
> **xzero1 said:**
> [http://linuxtv.org/v4lwiki/index.php/Main_Page]("http://linuxtv.org/v4lwiki/index.php/Main_Page")

This is kinda helpfull - thank you very much.

---

### Post by arsenic23 on 2008-04-26
Just in case anyone is interested I ended up buying an Hauppauge WinTV PVR-150 MCE.  Seems to work perfect in both Vista Ultimate and Hardy.  ( The iamge quality is a little on the rough side, not too bad though. )

---

### Post by killernurd on 2008-04-29
I can't seem to get mine to work... my composite input is severely distorted; it jams the entire image up into the top third of the picture window. Is there a setting I need to fiddle with to fix that, or did I get a bad card?

---

### Post by wesley_of_course on 2008-04-29
> **arsenic23 said:**
> Just in case anyone is interested I ended up buying an Hauppauge WinTV PVR-150 MCE.  Seems to work perfect in both Vista Ultimate and Hardy.  ( The iamge quality is a little on the rough side, not too bad though. )

        I had the same ?'s and had been surf'in and reading threads which were older and some newer.  I had decided on the same card but was curious about Mythtv ?  Is this what you set it up with or is it needed ?    No remote ?  Curious
  about this . Thanks for the thread.

---

### Post by arsenic23 on 2008-04-29
> **wesley_of_course said:**
> I had the same ?'s and had been surf'in and reading threads which were older and some newer.  I had decided on the same card but was curious about Mythtv ?  Is this what you set it up with or is it needed ?    No remote ?  Curious
  about this . Thanks for the thread.

I haven't setup Mythtv, and don't have any intention of doing so right now, I got the card just for converting my old VHS tapes to files.  I'm still setting the machine up right now, so I haven't gotten to that yet, and I didn't buy a card with a remote, as I've only used a wireless mouse for a remote for years.  All I'm doing with the card is watching a little TV in mplayer and ripping shows from my VCR, both using the coax input.

So the only ways I've used the card are the following:
```
mplayer -vf pp=lb /dev/video0 -ni
```and
```
cat /dev/video0 > file.mpg
```

I've been changing the channels directly with the driver using:
```
ivtv-tuner -c 44
``` 44 being the channel I use the most.

I was told I could open it directly with vlc as well, but that doesn't seem to work right and I'm too busy fiddling with other stuff right now to care.

---

### Post by wesley_of_course on 2008-04-30
Thanks for the the info Arsenic23. Much appreciated .

---

