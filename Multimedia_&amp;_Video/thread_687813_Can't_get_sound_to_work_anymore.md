---
title: "Can't get sound to work anymore"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by poofyyoda on 2008-02-04
I recently installed Ubuntu 7.10 on my HP Compaq Presario v6000, and it went well.  The sound worked great, but after I got my motherboard replaced by HP when the wireless died(6 days before the warranty went!), I can't get sound to work anymore.  The replacement motherboard is the same, and everything works well in windows (have dual boot setup).  

When I do *lspci* in terminal it tells me that the audio device is:
Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Not sure what to do next, any help would be appreciated.

---

### Post by nullfactor on 2008-02-04
My sound is the Intel HD sound, but I had the same problem of non-functional audio.  What worked for me is the following:

1)  Reboot computer.

2)  While the computer is rebooting, the GRUB menu will appear briefly.  When it does, it will tell you to press ESC to go to the boot menu.  Do so (press ESC).

3)  In the boot menu, highlight the kernel you're booting from (most likely the first option).

4)  Press "E" to edit.

5)  Highlight the option you wish to edit (second option on my computer...).  Press "E" to edit.

6)  At the end of the boot command, type the following:  ACPI=off

7)  Press <ENTER>

8)  Press "B" to boot.

9)  Hope for the best.

If this does not help, reboot the computer as normal (without editing anything) and let me know.  I have an alternate way to do the above that we'll try.

Good luck!

---

### Post by poofyyoda on 2008-02-04
I tried what you said, but there's still nothing, so I suppose lets try your alternative then.

---

### Post by poofyyoda on 2008-02-05
Well I've scoured these forums for ages and tried many things, but  nothing  at all works to restore my sound. 

I was thinking about reloading fresh, so I booted live, but there wasn't even sound on that, when there was originally, so I doubt the effectiveness of that.  So I can't comprehend the difference between the two motherboards(and soundcards) in the laptop, for some reason it seems there is no support for this one.  Major suckage, which means the dreaded windows again until Hardy gives me another chance..

---

### Post by easilydistrac on 2008-02-05
I have a brand new HP Pavilion dv9000 laptop and my sound also fails to work for some reason.  When I test I either hear nothing or receive a message stating "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available."

---

### Post by poofyyoda on 2008-02-05
Yeah, I get no sound from the test buttons, but if I press the sound capture test button I get 
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat".  The others have the status bar move back and forth stating its testing but nothing comes out.

---

### Post by easilydistrac on 2008-02-06
That's identical to me.

I'm dual booting with Vista, and my sound works fine there.

Also, despite the fact that the computer is not muted, the physical mute button (which changes colors when activated) says that the computer is muted.

lspci tells me my audio device is: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by WFGeppetto on 2008-02-07
um, bump

I have feisty fawn, and my sound stopped working after I rebooted after an update session.  When ubuntu loads, my sound is muted, but if I unmute it, and turn it up, even the gain, i still get nothing.  It worked fine for a while, and the only things I know of that I have done are a blacklist edit (but that was for wireless, and it seems fine, just have to redo the ndiswrapper thing), and I let the update thing run, and install everything.  I haven't changed my system any more than that since install, not even custom background, and I lost sound.

Please big coffee cups, come answer this one.

---

### Post by sluckz on 2008-02-07
**_easilydistrac_**

this is the easy way ICH8 
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

i have used this as recently as today works fine.  i m just new and not sure what backports fully entails and i really didnt like doing updates and finding a crapload of "updates" from my backports source.  im sure theres a way to blacklist anything else but really i 'd way rather be going forward than backwards anywaz

this is (my opinion) a much better way.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

i just finished that last way.  works like a champ.  i m running the latest alsa 1.0.16 compiled on my very own machine ; -)

if you go that last way i had to use the troubleshooting tip at the very end of the doc.


>  [ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_add
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_new
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates

i got error messages like that.  just read below it and that worked for me.

on my dv6000
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by easilydistrac on 2008-02-07
Thanks so much!  Did the first fix and it worked like a charm!

---

### Post by poofyyoda on 2008-02-11
YES! Finally I got sound.  
Over the last few days I've been through almost every 'no sound' thread, but nothing at all done anything.  In my desperation, I decided to try the live discs of all the previous Ubuntus.  
7.04 and 7.10 did not produce anything, but my good old 6.10 did.  So I was jubilant, and about to install that on my system.  But I restarted first and magically my 7.10 current install had sound!
I have no idea what happened and why the other live sessions didn't work but I'm glad I kept all my other ubuntu's!

Out of curiosity ,If anyone knows why it started again, I'd be glad to hear about it.

---

### Post by poofyyoda on 2008-02-11
Ok, so I happen to have a strange problem, but I'm sure some genius will know the answer...
It appears my 6.10 disc is 'holy'.  If I restart my computer and get into ubuntu again, the sound goes away, but if I load up immediately after I live sessioned with my edgy disc, it works but only until I restart.  So any help to resolve this would be great.  I don't really feel like worshipping my edgy disc and using it everytime I want to use sound.  Please help.

---

