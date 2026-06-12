---
title: "Ensoniq 1371 woes/Help Please"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by stealth_gsx1300r on 2006-05-30
I am at the end of my rope here.  I have just recently built a ubuntu box and I cannot for the life of me figure out why the sound won't work.  I come from a linux  background and have using linux for about 8 years now.  I used to consider myself linux-savvy, but have been humbled by this.  I cannot seem to get the sound working.  The right module is loaded in the kernel.  I have un-muted and turned up the volume on every option on the sound card.  I don't seem to have any errors that are being reported through the kernel, but still no sound.  When I run the live cd I get sound perfectly, but when I installed I have no such luck.  If anyone has any advice or solutions, I would really appreciate them.  I have searched all over these forums, but the problems that others had didn't seem to match up with mine.    Help please....](*,)

Edit:  It seems to only be the PCM side of things.  I can play from the CD player through the lineout perfectly fine.  I hope someone has some ideas... anyone?

---

### Post by birch on 2006-06-07
I feel your pain,  I got a Ensoniq ES1371 myself and one day (it might have been after an update ) The sound is just gone,  I mean it knows it's there but no default sound card anymore.  So yes, if anyone can help that would be great, I really don't want to go back to windows but if I don't hear some music soon, I just might.

---

### Post by stealth_gsx1300r on 2006-06-08
It looks as if you might need the OSS module.  I switched back to gentoo and couldn't get the sound there either.  I have a feeling that you have to use the alsa drivers seperately from the kernel or use the OSS 1371 module.  That was the only way I could get sound.  Something in alsa got broke I suspect because sound works fine on the livecd.  Go figure...  But, it works and I am on my way to finishing my mame machine.

---

### Post by birch on 2006-06-08
hey I reinstalled and guess what, bam ! sound! and it says there is a default sound card, and I haven't applied the updates and it is still working after a couple reboots. go figure, I just hope it doesn't happen again.

---

### Post by stimpyaw on 2007-02-05
I'm having the same problem with my Creative SoundBlaster PCI128 (CT4751) = ( Esoniq ES1371 ) sound card.  It was working for awhile and when I tested it just recently (after doing some updates) I no longer get any sound from the card.  The system see the card and I get no errors too.

$ cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xb400, irq 3

$ lspci
0000:01:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)

>birch< did you do a complete reinstall (formatting the drive) or reinstall over top?

---

### Post by Erlander on 2007-02-05
My ES1371 problems are even more puzzling.  I have onboard sound that seems to have failed so I installed an ES 1371 based card and turned the onboard off in bios.  Then I did a clean install with a reformat.  It worked!!!!!

The other night I decided to try and get the onboard going again.  So I removed the ES 1371 enabled the onboard in bios and booted up.  No Sound.

So turn off refit the ES 1371 turned off the onboard in bios and powered up.

Went to System/Preferences?Sound and clicked on Test.  My screen went black and I had to press the reset button to reboot.  Tried it again and the same except that the screen now goes black on boot up and I have to power down.

I have removed the sound card and am currently running without sound until I find a fix or get time for a fresh install.

I can't find it now but somewhere I read about conflicts between SoundBlaster Vibra 128 (ES 1371) and TNT2 video cards.  I thinks this is my problem.

Am going to replace the TNT2 in a few days so maybe a fresh install then.  Just when I have networking running nicely.

Rob

---

### Post by stimpyaw on 2007-02-06
I found in another forum a post on adding the following:

snd-ens1371

to /etc/modules it fixed my problem. so far so good. :) 2days and counting.

---

### Post by stimpyaw on 2007-02-20
I fixed my Ensoniq 1371 issue buy doing the following:

(please use do not make these changes if your not comfortable doing so)

1. You'll need to edit the &#8220;modules&#8221; file thru a terminal window.
2. Start you terminal window
3. Once at the flashing prompt type:
4. cd /etc
5. then type
6. sudo nano modules (when asked for the root password please enter it)

      #  /etc/modules: kernel modules to load at boot time.
      #
      # This file contains the names of kernel modules that should be loaded
      # at boot time, one per line. Lines beginning with "#" are ignored.

      lp
      psmouse

7. now move your blinking courser to the line just below the list line mine is &#8220;psmouse&#8221;, yours could be different. then type in &#8220;snd-ens1371&#8221;, your  modules file should look similar to mine:
               
      # /etc/modules: kernel modules to load at boot time.
      #
      # This file contains the names of kernel modules that should be loaded
      # at boot time, one per line. Lines beginning with "#" are ignored.
      
      lp
      psmouse
      snd-ens1371
          
8. To exit and save please do the following:
* Crtl-O
* You'll be asked: &#8220;File Name to Write: modules&#8221;; just hit the "enter" key.
* next you should see &#8220;[ Wrote 9 lines ]&#8221;

9. Now it Ctrl-X to exit GNU nano
10. Once that is done you should be back at &#8220;/etc$&#8221; prompt.
11. Now restart your computer. Once back in Ubuntu test your sound card.

Your sound card should work now, if you have speakers connected to your sound card you should hear the Ubuntu startup sounds. Please let me know if this works for you.

---

### Post by stimpyaw on 2007-02-20
> **stimpyaw said:**
> I found in another forum a post on adding the following:

snd-ens1371

to /etc/modules it fixed my problem. so far so good. :) 2days and counting.

2 weeks plus and still working. :)

---

### Post by fireeee on 2007-02-26
I have similar problem :sad: but snd-ens1371 did not resolve my problem. "cat /proc/asound/cards"  returns "--- no soundcards ---" and " lspci" - "00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)".I tried everything i have found on the net including reinstalling alsa driver,lib,firmware and utils with 1.0.13. And the sound is perfectly working on Knoppix 3.4 with ens1371. my volume control is red crossed and it says "No volume control GStreamer plugins and/or devices found." So I will apreceate every idea cause i cant live without my sound :guitar:  .

---

### Post by rennen01 on 2007-03-09
I  am running into the same thing.  My sound card works in XP.  I am going to try to remove the sound card and re-seat it.  Hope this works.  :crosses fingers:

---

### Post by rennen01 on 2007-03-11
Still not working.  Went through everything in the "Comprehensive Sound Problem" Thread and still not working.  I will have to keep looking.

---

### Post by nim278 on 2007-03-16
2 years, still not working ](*,)

---

### Post by rennen01 on 2007-03-17
bought a new card and voila! now i dont have to go to XP that often.

---

