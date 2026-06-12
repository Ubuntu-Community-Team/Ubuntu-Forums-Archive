---
title: "Installation Ending Problem"
date: 2011-01-12
forum: Mythbuntu
---

### Post by Barry_IA on 2011-01-12
[FONT=Palatino Linotype]Hi Folks!

Attempting to do a Frontend installation  (Mythbuntu 10.10); install process appears to go fine  but at the end this occurs: Window:  Installation complete, radio button to restart.  -- Click and then get numerous lines of text , the last one says to remove installation media (I do) and [ENTER}.  I do (the one on the main keyboard) but all I get is ^\ followed by the white diamond (ALT_004).  The same result has occurred with four or five install tries on the original installation disk  and earlier this morning on a new installation disk.  (5MDSUM verified on both, ImgBurn verified on both.  Not sure if the Disk Verifier option worked or not on the first one; didn't try on the second CD.  First disk is CD RO, the new one is CD RW.)

Power Boot (hold the front panel switch four seconds) to reboot.  Unremarkable text (AFAICT!) then stops at a login prompt (displays part of the name I gave to the computer -- first few characters cutoff) with a flashing underscore cursor.  Maybe ten or so seconds later the screen goes black, the HDD LED will have some blinking activity and then stops.  Can not toggle the NumLock LED (stays off).    This has been consistent with the multiple installations.

Hardware:
    Compaq Evo-D500
        Pentium  IV, 1.800 GHz 
        1280 MB 
        20 GB HDD  (default format is ext4, on the original disk even tried ext3)
       Chipset i845 
  Video card = HIS 4650  (AGP, 1 GB, HDMI)

So, what's screwing up the installation??  What do I need to check/do??  TIA!

P.S.: With the first installation CD I'd sometimes see a message about "connecting to plymouth: connection refused".  Also have seen "*ERROR* Device busy: 1" and the text line above was "[drm:drm release]" (apparently 38 seconds into the boot/load process).  Tried with and without the Install Updates; with and without the Fluendo MP3 plugin, with and without the AMD Graphics driver -- mostly with the Open Source driver.
 
[/FONT]

---

### Post by thatguruguy on 2011-01-12
FWIW, I always had issues installing from CDs. Have you tried installing from a USB stick to see if that makes a difference?

Also, have you tried running the CD as a "liveCD" prior to installation, to see if mythbuntu runs on that system?

---

### Post by Barry_IA on 2011-01-13
> **thatguruguy said:**
> FWIW, I always had issues installing from CDs. Have you tried installing from a USB stick to see if that makes a difference?

Also, have you tried running the CD as a "liveCD" prior to installation, to see if mythbuntu runs on that system?
[FONT=Palatino Linotype]
Hi ThatGuruGuy!

Haven't done an install from a thumbdrive -- will have to see if the BIOS has the option, or will just try.  And oddly enough last night while getting ready for bed it dawned on me to try doing the Live CD install just to see if that would take. 

Will try the Live CD and see what happens.  (Hope if takes there is an option to install the 'test' options rather than going through all the steps again!)
[/FONT]

---

### Post by Barry_IA on 2011-01-13
[FONT=Palatino Linotype]Well, that didn't work.  :(    Tried the Live CD option: the "Try Mythbuntu" option.  FWIW used the second CD -- the other day wasn't certain the first CD was good so downloaded the ISO a second time, checked 5MDSUM matched, ImgBurn indicated the burn was good...  BTW this is the i386/32-bit version.  Downloaded and burned on a Windows XP machine.

First trial:  installation seems to stop and just sit there after the  "Try Mythbuntu" option.  No DVD LED activity, no HDD LED activity, no NumLock toggle (stays off).  Let sit for 3 minutes, thinking it's "thinking".  Do the hold the power switch for four second thing to power down, goes to several lines of text so thinking I should retry and wait longer.

Second trial; trying to pay a little more attention.  see the "[drm:drm]" error again (no idea what it means; half-saw it with the first trial and with the install-to-HDD trials previously -- significant??).  Screen clears (reminds me of the old DOS *CLS* command), think is see something about a GPL error but displays too quickly at the top of the screen.  Another <CLS>, then alternating between the arrow and rotating I'm working circle icon.  Eventually to the Try Mythbuntu / Install Mythbuntu screen.  Click on the Try option...    One line text something like 'failed due to unknown user id' 

9:49  Black screen (again).  This time leaving things alone to let it 'think'.  No activities noted (no LEDs flashing, no screen activity noted).

9:58  Same...NumLock stays off,  Shift Lock stays off, <CR> nothing.....

10:00 Tap the ATX Front Panel Lower Switch.  ejects the CD.
      Power down (hold switch for four seconds) -- this time no text


Will try the install via thumbdrive option in a bit.  Need to get annoyance level down. <g>  Need to figure out how to install to a thumbdrive....
[/FONT]

---

### Post by Barry_IA on 2011-01-13
[FONT=Palatino Linotype]...Catching up on some e-mail; was reminded I had tried installing Mythbuntu 10.10 on to a Pentium III, 733 MHz a couple of weeks ago.  (Was half-hoping to use some of the old computers around here!)  Believe it or not the installation went fine with it -- the problem was the hardware was too slow (even with a 1 GB video card) and the video constantly started and stopped.   Too bad can't put the two machines side-by side and connect the two!  ...Would try except for the hardware detection wouldn't come out right.

BTW, how does one make a boot/installation USB thumbdrive??  I can find the instructions for Ubuntu but the instructions tell me to "Start > Administrator > open Start-up Disk Creator" but I haven't been able to find anything like that at the Mythbuntu Desktop.

Thanks again in advance!




[/FONT]

---

### Post by Barry_IA on 2011-01-25
[FONT=Palatino Linotype]A bit of a follow-up.  Appears to be an "incompatibility" between the particular computer and Ubuntu: I installed the full Ubuntu on the machine and had the same problem with the ^\ white_diamond symbols at the end (at the 'remove installation media and hit <ENTER> text).   Not sure what I did but a few reboots later I did finally get the installation to finish and then installed MythTV.

After all that work the system ended up being unusable.  It's a P4 1.8 GHz, 1,280 MB RAM,  2 GB AGP Video Card.  Fine with those low resolution recordings (where no resolution number is displayed) but with 720 the audio and video stutter (quick start-stop-start-stop) and for 1080 it doesn't play at all: goes to some sort of a menu screen listing my name and Other.
  [/FONT]

---

### Post by nickrout on 2011-01-25
> **Barry_IA said:**
> [FONT=Palatino Linotype]A bit of a follow-up.  Appears to be an "incompatibility" between the particular computer and Ubuntu: I installed the full Ubuntu on the machine and had the same problem with the ^\ white_diamond symbols at the end (at the 'remove installation media and hit <ENTER> text).   Not sure what I did but a few reboots later I did finally get the installation to finish and then installed MythTV.

After all that work the system ended up being unusable.  It's a P4 1.8 GHz, 1,280 MB RAM,  2 GB AGP Video Card.  Fine with those low resolution recordings (where no resolution number is displayed) but with 720 the audio and video stutter (quick start-stop-start-stop) and for 1080 it doesn't play at all: goes to some sort of a menu screen listing my name and Other.
  [/FONT]

Not surprising, that machine certainly does NOT have the grunt to play HD files.

That screen is the login screen, so I am guessing playing 1080 crashes X completely, which then restarts and waits for you to log in.

Unfortunately you cannot get AGP cards that will do vdpau, so you could try a PCI vdpau capable card, or get a better box.

---

### Post by Barry_IA on 2011-01-27
> **nickrout said:**
> Not surprising, that machine certainly does NOT have the grunt to play HD files.
That screen is the login screen, so I am guessing playing 1080 crashes X completely, which then restarts and waits for you to log in.
Unfortunately you cannot get AGP cards that will do vdpau, so you could try a PCI vdpau capable card, or get a better box.

[FONT=Palatino Linotype]Hi Nickrout!

Yes, in discussing this with some Linux knowledge we figured the login screen had something to do with the video portion.

I've already ordered a replacement computer, with more 'oomph'.  So much for trying to use the old computers around here for watching HD TV!

Will keep in mind your advice on the PCI video card -- on a machine not as much of a wimp as this one! <g>  

...I'll mark this thread as solved as it appears part of the problem is a too-slow machine and the other part is the incorrect video card.  (Now to remember where that button is!)
[/FONT]

---

### Post by Barry_IA on 2011-01-27
[FONT=Palatino Linotype]Umm, I will be checking the suggestions provided by newlinux and  novellahub.  Someone with whom I correspond via e-mail also suggested iffy memory and perhaps slowing the memory timing in CMOS.  I then thought of checking with MemTest from the Live CD.  Was intending to check the system out this afternoon but other things.....  [/FONT]

---

