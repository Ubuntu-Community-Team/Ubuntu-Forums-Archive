---
title: "Audacious won't play audio CDs"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by robc02 on 2008-01-06
I can't get Audacious to play Audio CDs. I am currently using Version 1.4.3 from the backports repository but had the same problem witht the earlier version on the main repository.
With the CD in the drive when launching Audacious the drive spins up but doesn't play. I have tried clicking  "Plugin Services - Add CD" but the drive just spins up and then stops.  I have installed Plugins and Plugins Extra.
Both Rythmbox and Amorok have no problems.
Audacious plays ogg files (and presumably mp3 etc) OK.

Can anyone help, please?

---

### Post by blubberblubb on 2008-01-22
Just hit the same problem and found the solution: Obviously it's a problem with the way it tries to read the CD.

I fixed it this way:

Open the audacious preference window. Go to 'plugins', then select 'CD audio plugin' and click on the 'preferences' button below. There, change the 'play mode' to 'analog' instead of 'digital audio extraction'.

Hope that helps!

---

### Post by robc02 on 2008-01-22
That's interesting. The CD Audio Plugin Configuration Window does not have an option for Analogue playback. Just Digital Adio Extraction followed by some options. I am using version 1.4.3

 I must look into this.

---

### Post by Yellow Pasque on 2008-01-22
I'm not sure, but I think the analog playback might only work if you have one of those 3-pin analog cables that connects your optical drive directly to your sound card.

---

### Post by domitianus on 2008-01-26
I had the same problem too.  I resolved by changing the name of the device directory that in my case was incorrectly set to /mnt/cdrom

---

### Post by disturbedite on 2008-01-26
i had the same "issue" as domitianus...

---

### Post by robc02 on 2008-01-27
I have the analogue lead connected but still no Analogue Playback option.

I have checked and my mount point is correct.

I am  short of time at the moment but I will look into this a bit more.

Thanks for your suggestions.

---

### Post by eeried on 2008-04-15
hello,

I have the same problem since I upgraded to Audacious 1.4.5.

There used to be a "play back" entry in the general menu, and there used to be settings for the CD plugin that enabled you to chnage to "digital" and to change the path of the CD if needed.

There's nothing like that in the new version.

I clicked on the "plugins service", and then "Add CD" but this doesn't seem to do anything: the menu remains open while you look at it like a dummy ;-)

I can't make it play a CD from Gnome either (System > Prefs > Removable drives and media).

VLC is okay to play CDs but isn't as good as the former version of audacious and I've never been able to play a CD with mplayer, I'm afraid -- I suppose the command line works better with mplayer.

---

### Post by halogentan on 2008-04-28
I went into the preferences of the cd plugin and mine was set to /mnt/cdrom/ as well.  When I changed that to /media/cdrom/ it worked fine.

---

### Post by eeried on 2008-04-28
> I went into the preferences of the cd plugin

Problem is I can find the plugins prefs but I can see an empty field next to Misc - Override default device (which is unchecked).

I'll try filling in the field with /media/cdrom (first you need to check "Override default device"

---

### Post by robc02 on 2008-05-09
I recently installed Hardy and then Audacious -  from the repository. It played my CDs straight away. Problem solved!:)

---

