---
title: "lost sound when upgrading to 14.04"
date: 2014-12-20
forum: Multimedia Software
---

### Post by bal2 on 2014-12-20
I recently upgraded from Ubuntu 12.10 to 14.04, and the sound on my  computer has not worked since. Discovered on another forum that this is a  known problem. Tried a few fixes suggested, no success. One fix says it won't work yet on 14.04 but will on earlier  versions. So I'm thinking I need to uninstall 14.04 and reinstall an  earlier version. I cannot however find how to do this as yet. If anyone  could guide me as to how to uninstall/reinstall ubuntu verions or  suggest another fix I would be grateful.

 Thanks Bal

---

### Post by mörgæs on 2014-12-21
Hi, welcome to the fora.

Do you get sound in a live boot of 14.04.1?

---

### Post by Yellow Pasque on 2014-12-21
> Tried a few fixes suggested, no success.
Be more specific. What exactly did you try?
Also, give more info. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bal2 on 2015-01-02
Thanks for the welcome!

Please bear with my limited knowledge of computer terms, I'm assuming a live boot is when I turn on the computer and ubuntu loads up? If so the answer is no, I don't get any sound at that point (whereas I did before the upgrade).

---

### Post by bal2 on 2015-01-02
Fixes were as follows:

Checked the alsa mixer to ensure the sound devices are working and not muted.

Re-installed alsa and pulse audio

The next suggestion was to install ubuntu audio development team driver, but with a disclaimer that this ppa is not upgraded to 14.04 yet.

I'll have a go also with the link you suggested.

Thanks

---

### Post by Quarkrad on 2015-01-03
I believe what is meant by a live boot is - when you intalled ubuntu (usb stick or CD/DVD) you had the option to TRY ubuntu or INSTALL ubuntu.  My understanding is that booting via this method and taking the TRY option is taken as a Live Boot (you can do all sorts of things to a broken or partially broken system booting and using a Live CD - in TRY mode).  So ...  if you boot your pc with a Ubuntu 14.04 install CD/DVD in the drive, or USB stick attached, and choose the TRY option - when you get to the ubuntu desktop do you have any sound?  (I fire up firefox, go to youtube and play anything - is there any sound?).

---

### Post by bal2 on 2015-01-03
Thank you Quarkrad, when I upgraded from 12.10 to 14.04 it was downloading directly via the update manager so not from an external drive. So are you saying it would be worth reinstalling (or in fact TRYing) 14.04 from a memory stick? In which case where do I find the download for this to get it onto my memory stick? Would you say furthermore that there would be any mileage in uninstalling 14.04 and installing an earlier version if reinstalling or TRYing 14.04 doesn't help (given that I have found a few potential guides to troubleshooting sound issues on earlier versions including one by people from this forum)?

---

### Post by mörgæs on 2015-01-04
There are links for download at the top of the page.

---

### Post by bal2 on 2015-01-14
Finally got a usb stick and tried a live boot of 14.04.1, got sound on this but came with other problems e.g. screen flashing on and off, display getting distorted suddenly, or computer crashing. Was going to install 14.04.1 as it seems to have plenty of fixes for sound issues, but concerned about the problems on the live boot. Any advice on how to proceed?

Thanks all!

---

### Post by mörgæs on 2015-01-15
Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by bal2 on 2015-01-15
Please bear with me again, I've run the command as suggested and posted the text which came up in response in the Add/Edit Tags box, was that what you were meaning?

---

### Post by bal2 on 2015-01-15
And in fact now that I've tried that I get a message that I don't have permission to add tags

---

### Post by bal2 on 2015-01-15
Just to add as well the problems with display, computer crashing etc only happen on the live boot, they are not happening at all when I use the already installed version of 14.04, the one which is minus the sound.

---

### Post by Yellow Pasque on 2015-01-15
Your thread's getting kind of confusing. You should stick to trying to solve the sound issue on your current install in this thread. If you want to troubleshoot the live media issue, then I'd suggest making a new thread, and at least give some basic info on what GPU you have:
```
lspci | grep -i VGA
```

You still haven't given your audio information... [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

