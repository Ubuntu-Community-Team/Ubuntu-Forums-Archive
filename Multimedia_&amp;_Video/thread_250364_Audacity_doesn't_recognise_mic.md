---
title: "Audacity doesn't recognise mic"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Aurora on 2006-09-04
Hi,

I'm trying to record live guitar/vocals with an old iMac G3 333MHz running Dapper. I have Audacity, a mixer, and a decent recording mic. The mixer out is plugged into the iMac's mic jack, and the headphones are plugged in to the iMac's headphone jack. I can hear the mic in the headphones, but I just get a flat line when I record.  Where the input source menu should be there's just a blank rectangle.  When I open edit> preferences> audio I/O, the recording device is listed as /dev/dsp. What do I need to change to get Audacity to record from the external mic input?

Thanks,

Paul in Seattle

---

### Post by aanderson on 2006-09-04
I have a similar problem. Audacity doesnt recognize
ANY sound interfaces. I get an error notice on start,
and the preferences->audio just shows a blank box for
recording and playback.

A temp fix is to kill esd (sudo killall -9 esd) which
fixes everything, but that disables system sounds as 
well.

There are supposed to be tools like esddsp which are
mentioned in man esd, which set up a pipe for /dev/dsp
into esd by running 'esddsp audacity' or something like
that, but ubuntu doesnt seem to have the esd tools 
available.

Others don't seem to have exactly this problem so there
must be a more elegant solution, but I don't know what 
it is.

:-k

---

### Post by aanderson on 2006-09-04
Ok, esddsp is in the package 'esound-clients'.

if you install it and set up a launcher icon with 'esddsp audacity' as
the command, audacity will work without stopping esd.

---

### Post by Aurora on 2006-09-04
Thanks for your response.  When I launch esddsp, I get the error:

There was an error initializing the audio i/o layer.
You will not be able to play or record audio.

Error: Host error

I then tried the killall -9 esd command, and I still have that blank box.

Are you using a PPC computer too?  Macs are weird; what works under Linux on Intel architecture often fails on a Mac--expecially when it comes to multimedia. I would get another computer, but I have a deadline today to submit a rough demo and I won't have time to shop carefully.

Any other ideas?

--Paul

---

