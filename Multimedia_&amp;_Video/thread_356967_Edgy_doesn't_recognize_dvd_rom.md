---
title: "Edgy doesn't recognize dvd rom"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by tjtansey on 2007-02-09
I just installed edgy and it doesn't recognize my dvd even after I installed every patch I could find.  Any ideas?  Error msg I get is "No plug in found to handle this resource (dvd://)
Thanks

---

### Post by RomeReactor on 2007-02-09
Hi. Did you install [libdvdcss]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability")?  Are you using Totem-Xine?

---

### Post by tjtansey on 2007-02-09
Yes, I had it working fine on dapper

---

### Post by RomeReactor on 2007-02-09
Open Nautilus, got to "Computer-->media" and see what folders you have there. If you have "cdrom", open "System-->Preferences-->Removable Drives and Media", go to the second tab and write

```
totem /media/cdrom
```

on the "Command" section of "Video DVD Discs", or change to an entry you actually have there. Then try loading a dvd.

---

### Post by tjtansey on 2007-02-09
I tried that, I assume you meant the command to go in the multimedia tab.  Still nothing and when I go to media, the cdrom folder is blank

---

### Post by tjtansey on 2007-02-09
I discovered the problem I think.  I get this error when trying to install libdvdread3
"Couldn't find any package whose name or description matched "libdvdread3""
I assume this is what is causing the problem, any ideas?

---

### Post by RomeReactor on 2007-02-09
Open Synaptic, click on "Settings-->Repositories", check all the boxes on the first tab and click reload; then search for libdvdread and install it. After that

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

and

```
sudo apt-get install totem-xine
```

If you don't have it already. I found [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability") to be very useful.

---

### Post by tjtansey on 2007-02-09
I followed the guide to the letter (had to add the repositories) but I still get the same errors.  Here are the screenshots:
At this point I'm beyond aggravated

---

### Post by RomeReactor on 2007-02-09
By mistake i linked the Dapper version of Ubuntu Guide on my third post; the one on my first post leads you to the Edgy version. Did libdvdcss install correctly? Look for it in Synaptic, or

```
locate libdvdcss
```

Also try opening Totem and press **CTRL+L**; write **/dev/hdc** and see if that opens the dvd.

---

### Post by tjtansey on 2007-02-09
no dice there, I'm about to go hunting a NT cd

---

### Post by tjtansey on 2007-02-10
I have the errors down to two here they are:

---

### Post by tjtansey on 2007-02-10
Ok now I can play a few DVD's but this is the error I get on most.  xine: cannot find input plugin for MRL [dvd://]
xine: input plugin cannot open MRL [dvd://]
Any Ideas anyone?
Thanks

---

### Post by RomeReactor on 2007-02-10
Try

```
sudo apt-get install libxine-extracodecs
```

I find it very odd that you can't play DVD's with Totem-Xine...

---

### Post by tjtansey on 2007-02-10
You find it odd, I had it working fine on dapper thanks to your help, but my brother talked me into installing edgy and I'm starting to regret it.

---

### Post by TBOL3 on 2007-02-16
I'd like to add myself to this plea for help.

My player does the same thing.  Worked fine in dapper, not in edgy.  Also, the cdrom folder is empty.  The error looks like it can't find the right folder.  Also, BTW, edgy runs CDs fine, but not DVDs.  Its a CD DVD combo,  It seams as if there are no drivers for it.

---

### Post by tjtansey on 2007-02-16
What brand is your cd/dvd rom?  I almost think this is a driver issue.  I have basically given up on it.

---

### Post by TBOL3 on 2007-02-16
It came on an IBM computer, it says DISC +, it's black, but that's about all I can make out.

---

### Post by tjtansey on 2007-02-16
Well it seems to me that we are the only two people in the world that can't accomplish dvd playback.  I've been given a list of instructions as long as my arm, but nothing works.  Although  I can read data dvd's go figure

---

### Post by TBOL3 on 2007-02-16
Interesting, I can't.

I'm looking for it in the device manager, but I can't find it, even when there is a readable CD in.

---

### Post by TBOL3 on 2007-02-16
I found it, it's a Samsung CDRW/DVD SM-352F

It's also located at dev/hdc if that can help.

THANKS! :)

---

### Post by tjtansey on 2007-02-16
Now I know it has to be a hardware issue because that's the same one I have.

---

### Post by TBOL3 on 2007-02-17
So how do you play data DVDs?

---

### Post by tjtansey on 2007-02-17
It just work for data

---

### Post by TBOL3 on 2007-02-17
Was there an icon for it on the desk?  When I inserted a data DVD, I didn't find anything.

---

### Post by tjtansey on 2007-02-19
Finally found a fix for it and it seems to work.  There is a firmware update on Samsungs website.  I installed it and the player works great! The link for the download site is in the PDF that pulls up when you look for a driver download

---

### Post by TBOL3 on 2007-02-19
Can you give me your search words, I already did sevrreal searches without any luck.

Thanks.

---

### Post by tjtansey on 2007-02-19
just enter your model # in the search, it should pull right up

---

### Post by TBOL3 on 2007-02-19
I really can't find a download:(, but I think I found the page, (with the white cd player, right?)

---

### Post by tjtansey on 2007-02-20
Here's a link to the index for all the cdrw/dvd drives.
[http://www.samsung.com/support/productsupport/download/index.aspx](http://www.samsung.com/support/productsupport/download/index.aspx)

---

### Post by TBOL3 on 2007-02-21
It's a windows upgrade, what should I do?

---

### Post by tjtansey on 2007-02-21
That I'm not sure of, I am dual booting with XP.  I don't know how to do the firmware update in Linux, maybe one of the guru's can give you a hand there

---

### Post by TBOL3 on 2007-02-26
I downloadid the firmare, and started it, but it kept  saying error, can't find flash device, or something like that.

O, and I was using windows.  Did you encounter this problem?

---

### Post by tjtansey on 2007-02-26
No it ran fine for me, and everything works as it is supposed to.

---

### Post by TBOL3 on 2007-04-16
Alright, I still haven't had any luck, so I got a new DVD player.  It is still made by the same people, now it also burns DVDs.  It worked for the first day.  A few days later, I popped in a new DVD, it recognized it, but nothing could play it.  After taking it back out and putting in the same one in that I had tried the first time, it didn't even recognize that there was ANYTHING in it.  I put the second disk back in, and it no longer even recognized the presence of that disc.

---

